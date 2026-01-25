##  Các Khái Niệm & Thuật Ngữ Cốt Lõi (n8n)

**Các khái niệm cốt lõi** của n8n là nền tảng để hiểu trước khi xây dựng các tự động hóa mạnh mẽ.  
Chúng bao gồm: **workflows, nodes, triggers, actions, data flow, và JSON basics**.

Hãy coi đây như "ngữ pháp" của tự động hóa — một khi bạn học nó, bạn có thể tạo thành bất kỳ câu nào (workflow).

---

### 🧭 Workflows — Bức Tranh Lớn

Một **workflow** giống như một **công thức** hoặc **kế hoạch dự án**.  
Đó là toàn bộ tập hợp các hướng dẫn cho n8n *phải làm gì, theo thứ tự nào, và dưới những điều kiện nào.*

- **Phép Loại Suy (Chuyên Nghiệp):** Một quy trình "Quản Lý Khách Hàng Tiềm Năng" — trigger khi form được gửi, làm giàu với dữ liệu API, gửi email chào mừng, sau đó thêm vào CRM.  
- **Phép Loại Suy (Cá Nhân):** Quy Trình "Sáng Hôm Nay" của bạn — trigger khi bạn thức dậy, sau đó đánh răng → pha cà phê → kiểm tra lịch.

✅ **Ý Chính:** Một workflow = một tự động hóa hoàn chỉnh.

---

### 🧩 Nodes — Các Khối Xây Dựng

Một **node** là một **bước** trong workflow của bạn. Mỗi node có một công việc cụ thể.

- **Phép Loại Suy:** Trong một nhà máy, mỗi công nhân là một node — người này sơn, người kia kiểm tra chất lượng, người còn lại đóng gói hộp.  
- **Ví Dụ Chuyên Nghiệp:** Node Gmail Send → Gửi email cảm ơn.  
- **Ví Dụ Cá Nhân:** Node Calendar Create → Thêm "Ăn tối với bạn" lúc 8 tối.

✅ **Quy ước đặt tên:** Luôn sử dụng *Động từ + Đối tượng* (ví dụ: "Send Email", "Fetch Orders").

---

### 🔔 Triggers — Cách Workflows Bắt Đầu

Triggers cho n8n biết **khi nào** để chạy workflow của bạn.

- **Manual Trigger:** Giống như nhấn nút *play* khi kiểm tra.  
- **Schedule Trigger:** Giống như một báo thức — chạy vào những thời gian cụ thể.  
- **Webhook Trigger:** Giống như chuông cửa — một dịch vụ bên ngoài "gọi" để khởi động workflow.  
- **App Triggers:** Gmail (email mới), Telegram (tin nhắn mới), Airtable (bản ghi mới).  

✅ **Phép Loại Suy:** Một trigger là "chuông cửa" bắt đầu workflow.

---

### ⚡ Actions — Thực Hiện Công Việc

Actions là những **nhiệm vụ** xảy ra sau khi trigger kích hoạt.

- **Ví Dụ Chuyên Nghiệp:** Sau khi form được gửi, gửi cảnh báo Slack.  
- **Ví Dụ Cá Nhân:** Sau khi nhận tin nhắn Telegram, kiểm tra Google Calendar và trả lời với tính khả dụng.  

✅ **Phép Loại Suy:** Trigger là báo thức reo, action là bạn **pha cà phê**.

---

### 🔄 Data Flow — Nhiên Liệu của Workflows

Dữ liệu di chuyển qua các nodes như **chiếc gậy trong cuộc đua tiếp sức** hoặc **một kiện hàng trên băng chuyền**.  
Mỗi node nhận dữ liệu đầu vào (thường là JSON), xử lý nó, và chuyển đầu ra cho node tiếp theo.

Ví dụ mục JSON:
```json
{
  "name": "Priya",
  "email": "priya@acme.com"
}
```

Các biểu thức phổ biến:
- `{{$json["email"]}}` → email của mục hiện tại  
- `{{$node["Lookup"].json["id"]}}` → lấy ID từ node trước đó  

✅ **Phép Loại Suy:** Dữ liệu là **gậy chạy** được truyền giữa các vận động viên (nodes).

---

### 📜 JSON Basics — Bản Thiết Kế

Workflows được lưu trữ và chia sẻ dưới dạng **tệp JSON** — bản thiết kế tự động hóa của bạn.

- **Phép Loại Suy:** Bản thiết kế ngôi nhà, hoặc thẻ công thức với mọi chi tiết được viết rõ ràng.  
- **Trường Hợp Sử Dụng:** Xuất workflows để chia sẻ với đồng nghiệp, nhập workflows sẵn sàng từ mẫu, hoặc gỡ lỗi cấu trúc.  

Ví dụ workflow JSON đơn giản hóa:
```json
{
  "name": "My Workflow",
  "nodes": [
    { "name": "Webhook Trigger", "type": "webhook" },
    { "name": "Gmail Send", "type": "gmail" }
  ],
  "connections": {
    "Webhook Trigger": ["Gmail Send"]
  }
}
```

---

### 🧠 Tóm Tắt Phép Loại Suy

- **Workflow = Công thức / Kế hoạch dự án**  
- **Node = Công nhân trong nhà máy / Bước trong công thức**  
- **Trigger = Chuông cửa hoặc Báo thức**  
- **Action = Bước nấu ăn / Gửi Email**  
- **Data Flow = Gậy chạy tiếp sức / Dòng chảy kiện hàng**  
- **JSON = Bản thiết kế hoặc Thẻ công thức**

---

### ✅ Bảng Tóm Tắt

| Khái Niệm   | Nó là gì                          | Phép Loại Suy                  | Ví Dụ (Chuyên Nghiệp)             | Ví Dụ (Cá Nhân)                   |
|-------------|-----------------------------------|--------------------------------|---------------------------------------|--------------------------------------|
| Workflow    | Tự động hóa hoàn chỉnh             | Công thức / Kế hoạch dự án     | Quy trình khách hàng: form → làm giàu dữ liệu → email | Quy trình sáng: thức dậy → cà phê    |
| Node        | Một bước duy nhất                 | Công nhân trong nhà máy / Bước công thức| Gmail Send → email cảm ơn         | Calendar Create → sự kiện ăn tối     |
| Trigger     | Bộ khởi động workflow             | Chuông cửa / Báo thức          | Webhook: gửi form mới              | Telegram Trigger: bạn gửi tin nhắn  |
| Action      | Công việc thực hiện sau trigger   | Bước nấu ăn                    | Gửi cảnh báo Slack sau điền form    | Trả lời Telegram với lịch của bạn   |
| Data Flow   | Thông tin di chuyển giữa các nodes| Gậy tiếp sức / Dòng kiện hàng  | ID Khách hàng → lấy chi tiết        | "7 giờ tối xem phim" → tạo sự kiện  |
| JSON        | Định dạng bản thiết kế workflow   | Bản thiết kế / Thẻ công thức   | Xuất workflow dưới dạng JSON        | Nhập workflow sẵn sàng              |

---

### 🔗 Kết Nối Với Tôi

Tò mò về cách xây dựng các hệ thống AI có thể tự cải thiện?

📺 **YouTube** → [@tech.mayankagg](https://www.youtube.com/@tech.mayankagg)  
💼 **LinkedIn** → [Mayank Agarwal](https://www.linkedin.com/in/mayank953/)  
📸 **Instagram** → [@tech.mayankagg](https://www.instagram.com/tech.mayankagg/)

---

*Được chia sẻ bởi Mayank Agarwal – Xây dựng tự động hóa tự nhận thức với n8n + AI.*
