# Video: Hướng dẫn Crawl4AI Dữ liệu Web hiệu quả (tích hợp n8n đơn giản)
crawlAI: Open source llm-friendly. Web crawler & scraper

mỗi video mang lại thông điệp gì? -> crawl thông tin data của trang web
nôi dung chính ra sao?

giải thích & ví dụ cụ thể với các công nghệ?
những điều còn thắc mắc?
tổng kết & lưu ý?
nguồn tài nguyên?

# Introduction
Trong video này, mình giới thiệu Crawl4AI - một bộ công cụ crawl dữ liệu web mã nguồn mở (open-source) cực kỳ mạnh mẽ và linh hoạt, giúp bạn tự động hóa hoàn toàn quá trình này. Đặc biệt, video tập trung hướng dẫn cách tích hợp và sử dụng Crawl4AI ngay trong workflow n8n quen thuộc của bạn!

Chúng ta sẽ cùng tìm hiểu và thực hành qua các ví dụ cụ thể:
1️⃣ Crawl dữ liệu cơ bản từ một URL duy nhất.
2️⃣ Sử dụng sức mạnh của LLM (Large Language Models) để tự động trích xuất (extract) dữ liệu crawl được thành dạng có cấu trúc (structured output).
3️⃣ Kỹ thuật crawl nâng cao: Xử lý nhiều URL đồng thời, tôn trọng `robots.txt`, quản lý tốc độ với `semaphore` và `rate limit`.
4️⃣ Sử dụng `profile` để tùy chỉnh quá trình crawl cho các trang web phức tạp.
5️⃣ Cách tích hợp và gọi Crawl4AI trực tiếp từ trong workflow n8n của bạn.

Video này hoàn hảo cho những ai đang dùng n8n, các nhà phát triển, data engineer, hoặc bất kỳ ai muốn tự động hóa việc thu thập dữ liệu web một cách hiệu quả để phục vụ cho các dự án AI, RAG, hay phân tích dữ liệu.


Tóm tắt nội dung?tiêu đề của từng phần hướng dẫn?
- Giới thiệu tầm quan trọng của dữ liệu và giới thiệu crawl data
- Chuẩn bị cài đặt
🔗 Liên kết hữu ích:
    Link tải uv: https://docs.astral.sh/uv/
    Link tải examples: https://github.com/draphonix/storage/tree/main/012_crawl4ai
    ```bash
    install uv # thư viện quản lý python
    uv env -p 3.11
    uv pip install - r requirements.txt
    playwright install
    ```
- Demo 1: Crawl simple URL.
- Demo 2: Extract structured data bằng LLM
- Demo 3: Crawl nhiều URLs (Semaphore, RateLimit, Robots.txt)
- Demo 4: Crawl dữ liệu với Profile
- Demo 5: Các sử dụng Crawl4AI trong n8n
- Tổng kết và lưu ý?

