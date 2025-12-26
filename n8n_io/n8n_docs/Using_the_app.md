# Các khái niệm cơ bản

# Workflow components trong n8n
Một workflow n8n được cấu thành từ **6 thành phần cốt lõi**:
```bash
Trigger → Nodes → Connections → Data → Executions → Settings
```
## 1. Trigger (điểm khởi động)
**Trigger quyết định khi nào workflow chạy**
Các loại Trigger chính
| Trigger         | Dùng khi                           |
| --------------- | ---------------------------------- |
| Manual Trigger  | Test                               |
| Webhook Trigger | Nhận HTTP request                  |
| Cron            | Chạy theo lịch                     |
| App Trigger     | Sự kiện từ app (Telegram, Google…) |
| Error Trigger   | Bắt lỗi workflow khác              |

**📌 Workflow bắt buộc phải có Trigger**

**Lỗi hay gặp**:
- Nhầm Manual Trigger là production
- Workflow Active nhưng trigger không hợp lệ

## 2. Nodes (các bước xử lý)
**Node là gì?** → `Node = 1 hành động cụ thể`
Ví dụ:
- HTTP Request → gọi API
- Set → chỉnh JSON
- IF → rẽ nhánh
- AI / Gemini → xử lý LLM
- Database → lưu dữ liệu

**Nhóm node theo chức năng**
- Data:
    - Set
    - Merge
    - Split In Batches
- Logic:
    - IF
    - Switch
    - Wait
    - Loop
- Integration:
    - HTTP Request
    - Google Sheets
    - Telegram
    - DB
- Code:
    - Function
    - Code
    - Expression

**Lỗi hay gặp**
- Không hiểu input/output của node
- Dùng Code node quá sớm

## 3. Connections (Kết nối)
**Connections là gì?** → `Là đường dẫn **dòng dữ liệu**`
- Dữ liệu **chảy từ trái → phải**
- Có thể tách nhánh (IF)
- Có thể gộp (Merge)

**📌 Không có connection → node không chạy**

**Lỗi hay gặp**
- Node kkhoong nối vào trigger
- Hiểm lầm thứ tự chạy

## 4. Data (items & JSON)
**Cách n8n xử lý data**
- Workflow xử lý **items[]**
- Mỗi item là 1 JSON

Ví dụ:
```json
[
    {"email": "a@gmail.com"},
    {"email": "b@gmail.com"}
]
```
→ node chạy **2 lần**

**Truy cập dữ liệu**
```javascript
{{$json.email}}
{{$node["Webhook"].json.body.name}}
{{$now}}
```
📌 Hiểu data = hiểu workflow

**Lỗi hay gặp**
- Sai path JSON
- Nhầm array thành object

## 5. Executions (lịch sử chạy)
**Executions lưu**:
- Input
- Output
- Error
- Thời điểm chạy
📌 Đây là **debug center**

**Execution types**
| Loại       | Khi nào      |
| ---------- | ------------ |
| Manual     | Test         |
| Production | Trigger thật |
| Error      | Workflow lỗi |

**Lỗi hạy gặp**
- Không xem execution
- Xem sai node lỗi

## 6. Workflow Settings (cấu hình workflow)
Những setting quan trọng

| Setting           | Ý nghĩa               |
| ----------------- | --------------------- |
| Active / Inactive | Publish workflow      |
| Timeout           | Giới hạn thời gian    |
| Error Workflow    | Bắt lỗi               |
| Retry on fail     | Chạy lại              |
| Execution order   | Sequential / Parallel |

**Lỗi hay gặp**
- Không set error workflow
- Timeout không đủ

## Các components phối hợp
Ví dụ diễn giải:
```bash
Khi Webhook nhận request →
Set chuẩn hóa dữ liệu →
IF kiểm tra điều kiện →
HTTP Request gọi API →
Telegram gửi thông báo →
Lưu Execution
```