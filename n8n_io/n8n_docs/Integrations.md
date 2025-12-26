**Integrations trong n8n** chính là **linh hồn** của automation.
Hiểu đuunsg Integrations → bạn **kết nối được mọi hệ thống** (AI, API, DB, SaaS) mà **không cần viết backend riêng**.

Mình sẽ hướng dẫn từ **tư duy → cấu trúc → cách dùng → best practice**, đúng kiểu làm **project thật**.

# Integrations trong n8n là gì?
**Integration = kết nối n8n với hệ thống bên ngoà** để:
- Lấy dữ liệu
- Gửi dữ liệu
- Đồng bộ
- Điều khoản hành vi hệ thống khác

👉 Mỗi Integration thường tương ứng với **1 node hoặc 1 nhóm node**

## 1. Các nhóm Integrations chính trong n8n
n8n chia integrations theo **4 nhóm lớn**:
```bash
Trigger integrations
Action integrations
Generic integration
Custom integration
```
## 2. Trigger Integration (nhận sự kiện bên ngoài)
**Dùng để: Khởi động workflow**
Ví dụ:
| Integration          | Khi nào chạy  |
| -------------------- | ------------- |
| Webhook              | API gọi vào   |
| Telegram Trigger     | Có tin nhắn   |
| Google Drive Trigger | File mới      |
| Notion Trigger       | Page thay đổi |
| Stripe Trigger       | Thanh toán    |

📌 **Trigger integration = event-driven**

Ví dụ thực tế: `Khi có đơn hành từ Stripe → xử lý tự động`

## 3. Action Integrations (thực hiện hành động)
**Dùng để: Làm gì đó**
Ví dụ:
| Integration   | Hành động |
| ------------- | --------- |
| Google Sheets | Ghi / đọc |
| Telegram      | Gửi tin   |
| Slack         | Notify    |
| Notion        | Tạo page  |
| Email         | Gửi mail  |

📌 Action integration **không tự chạy**, phải được trigger trước

## 4. Generic Integrations (xương sống - dùng nhiều nhất)
**HTTP Request (Quan trọng nhất)** → `Kết nối với bất kì API nào trên đời`
Dùng cho:
- REST API
- AI API (Gemini, OpenAI)
- Tiktok API
- SerpAPI

📌 Nếu **n8n chưa có node riêng → dùng HTTP Request**

**Ví dụ HTTP Request**
```json
POST https://api.example.com/orders
Headers:
Authorization: Bearer xxx
Body:
{
  "order_id": {{$json.id}}
}
```

**Webhook**
Biến workflow thành **API endpoint**
📌 Webhook = integration ngược (bên ngoài gọi n8n)

## 5. Custom / Advanced Integrations
**Database**
- PostgreSQL
- MySQL
- MongoDB
- Redis

Dùng khi:
- Lưu trạng thái
- Làm memory cho AI Agent
- Audit dữ liệu

**AI / LLM Integrations**
- OpenAI
- Gemini
- HuggingFace
- Local LLM (Qua HTTP)

📌 Rất hợp với use case của bạn (AI Agent + n8n)

## 6. Credentials (trái tim của Integrations)
**Credential là gì?** → Là nơi lưu **API Key / token / auth**
Ví dụ:
- OAuth2
- API Key
- Basic Auth
- Service Account
📌 **Credential dùng chung cho nhiều workflow**

## 7. Dòng dữ liệu trong Integration
**Integration nhận gì?**
```json
Input: items[]
```
**Integration trả gì?**
```json
Output: JSON / Binary
```
📌 Luôn kiểm tra **Output của Integration node**

## 8. Pattern tích hợp phổ biến (rất hay dùng)
**Pattern 1: Webhook → API → Notify**
```nginx
Webhook → HTTP Request → Telegram
```
**Pattern 2: Cron → Fetch → Store**
```nginx
Cron → HTTP Request → DB
```
**Pattern 3: AI Agent**
```scss
Webhook → LLM → Tool (API/DB) → Response
```

## 9. Lỗi thường gặp khi dùng Integrations
- Sai credential
- Token hết hạn
- Sai HTTP Method
- Sai JSON Path
- API trả format khác dự đoán
👉 90% fix bằng Executions

## 10. Tối ưu Integration 
**Performance**
- Hạn chế node HTTP không cần thiết
- Batch request nếu có thể

**Stability**
- Retry on fail
- Error workflow
- Timeout hợp lý

**Security**
- Header auth
- Webhook secret
- IP allowlist (nếu có)

1️⃣2️⃣ Tóm tắt cực ngắn
**Integrations = cách n8n nói chuyện với thế giới**
**Node native → nhanh**
**HTTP Request → vạn năng**
**Credential → sống còn**