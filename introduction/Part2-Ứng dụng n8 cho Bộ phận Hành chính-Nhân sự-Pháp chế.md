# 1. GỬI THÔNG BÁO SINH NHẬT TỰ ĐỘNG

**Workflow**
1. Tạo schedule trigger để chạy hàng ngày từ thứ 2 đến chủ nhật
2. Dùng HTTP request để kết nối với Base HRM và lấy thông tin ngày sinh, tháng sinh của nhân viên (Hoặc có nếu dùng file google sheet thì dùng node google sheet để lấy thông tin trên file đó)
3. Dùng JavaScript để lấy danh sách những người có sinh nhật hôm nay
4. Dùng node send email dể gửi email Chúc mừng sinh nhật

