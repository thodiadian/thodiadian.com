# Đồ án SEO: Thổ Địa Dĩ An - Làng Đại Học

Dự án tối ưu hóa công cụ tìm kiếm (SEO) cho ngách Review Ẩm thực, Cà phê và Đời sống sinh viên tại khu vực Dĩ An và Làng Đại học.

## 1. Cấu trúc thư mục đồ án
- `/docs`: Chứa báo cáo cuối kỳ và hướng dẫn sử dụng.
- `/analysis`: Chứa dữ liệu phân tích từ khóa, backlink, traffic.
- `/content`: Chứa bản nháp nội dung đã tối ưu hóa On-page.
- `/presentation`: Chứa slide thuyết trình bảo vệ đồ án.
- `strategy.json`: File khai báo chiến lược SEO tổng thể.

## 2. Hướng dẫn cài đặt Website (Dành cho thành viên nhóm)
Website được xây dựng dựa trên nền tảng GitHub Pages và Jekyll Static Site Generator.
- **Bước 1:** Viết bài trên định dạng Markdown (`.md`).
- **Bước 2:** Đặt file bài viết vào thư mục `_posts` với cú pháp tên: `YYYY-MM-DD-ten-bai-viet.md`.
- **Bước 3:** Push code lên nhánh `main`, GitHub Action sẽ tự động deploy trang web.

## 3. Hướng dẫn sử dụng các SEO Tools trong dự án
- **Google Search Console:** Dùng để submit sitemap (tại `_site/sitemap.xml`) và theo dõi hiệu suất index.
- **Google Analytics 4:** Mã Tracking ID đã được gắn trong file `_config.yml` để đo lường Traffic và Dwell Time.
- **Ahrefs / Keyword Planner:** Được sử dụng để phân tích và lập danh sách từ khóa đuôi dài (Long-tail keywords) có độ cạnh tranh thấp tại địa phương.
- **PageSpeed Insights:** Dùng để kiểm tra và tối ưu Core Web Vitals định kỳ sau mỗi lần cập nhật nội dung.
