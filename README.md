# Thổ Địa Dĩ An

Website review địa điểm, ăn uống, cà phê, vui chơi và đời sống sinh viên tại Dĩ An, Đông Hòa và khu Làng Đại học. Dự án được xây dựng bằng Jekyll, dùng theme Chirpy và triển khai qua GitHub Pages.

Cập nhật gần nhất: 2026-06-02.

## Tổng quan

- Domain cấu hình: `https://thodiadian.com`
- Ngôn ngữ: `vi-VN`
- Múi giờ: `Asia/Ho_Chi_Minh`
- Theme: `jekyll-theme-chirpy`
- Nội dung hiện có: 52 bài viết Markdown trong `_posts`
- Nhóm nội dung chính: Cà phê, Ẩm thực, Địa điểm, Giải trí, Trà sữa, Thể thao
- Công cụ SEO đang cấu hình: Google Search Console, Google Analytics 4, sitemap mặc định của Jekyll/Chirpy, PWA cache

## Cấu trúc thư mục

- `_posts/`: bài viết đã xuất bản. Tên file theo dạng `YYYY-MM-DD-ten-bai-viet.md`.
- `_tabs/`: các trang điều hướng như danh mục, thẻ, lưu trữ và giới thiệu.
- `_includes/`: các include tùy chỉnh, gồm `category-posts.html`, `related-posts.html` và `head.html`.
- `_plugins/`: plugin Jekyll tùy chỉnh. `posts-lastmod-hook.rb` tự gắn `last_modified_at` từ lịch sử Git.
- `_data/`: dữ liệu liên hệ, chia sẻ mạng xã hội và locale tiếng Việt.
- `assets/`: CSS override, avatar, logo và favicon.
- `tools/`: script chạy local và build/test production.
- `.github/workflows/pages-deploy.yml`: GitHub Actions build, kiểm tra HTML và deploy GitHub Pages.
- `strategy.json`: chiến lược SEO và quy tắc vận hành nội dung.
- `_config.yml`: cấu hình chính của site, SEO meta, analytics, PWA, pagination và permalink.

## Cài đặt local

Yêu cầu:

- Ruby 3.x
- Bundler
- Git

Cài dependencies:

```bash
bundle install
```

Chạy website local:

```bash
bundle exec jekyll s -l -H 127.0.0.1
```

Hoặc dùng script có sẵn:

```bash
bash tools/run.sh
```

Trên Windows, nếu không dùng Git Bash hoặc WSL thì chạy trực tiếp lệnh `bundle exec jekyll s -l -H 127.0.0.1` trong PowerShell.

## Build và kiểm tra

Build production:

```bash
JEKYLL_ENV=production bundle exec jekyll b
```

Build và chạy `html-proofer`:

```bash
bash tools/test.sh
```

GitHub Actions cũng chạy build production và `html-proofer` trước khi deploy.

## Quy trình viết bài

Tạo file mới trong `_posts/` với slug không dấu, chữ thường, phân tách bằng dấu gạch ngang:

```text
YYYY-MM-DD-review-ten-dia-diem-di-an.md
```

Front matter nên có đủ các trường sau:

```yaml
---
layout: post
title: "Review Tên Địa Điểm Dĩ An - mô tả ngắn"
date: 2026-06-02 08:00:00 +0700
categories: [Review, Cà phê]
tags: [cafe di an, check in di an]
description: "Mô tả 120-160 ký tự, có từ khóa chính và lý do người đọc nên bấm vào."
image:
  path: https://res.cloudinary.com/.../w_1000,q_auto,f_auto/...
  alt: "Mô tả ảnh rõ ràng, có ngữ cảnh địa điểm"
---
```

Checklist trước khi xuất bản:

- Tiêu đề có từ khóa địa phương như `Dĩ An`, `Làng Đại học`, `Đông Hòa` hoặc tên địa điểm.
- `description` không để placeholder và không quá chung chung.
- Ảnh đại diện có `path` và `alt`; ưu tiên URL Cloudinary có `q_auto` và `f_auto`.
- Bài có thông tin thực tế: địa chỉ, giờ mở cửa, giá tham khảo, ưu/nhược điểm và Google Maps nếu có.
- Cuối bài thêm `{% include category-posts.html %}` để tăng liên kết nội bộ theo chủ đề.
- Tag dùng thống nhất theo các cụm hiện có: `cafe di an`, `quan an di an`, `an vat di an`, `tra sua di an`, `check in di an`, `du lich di an`, `lang dai hoc di an`.

## SEO và đo lường

- Sitemap production: `https://thodiadian.com/sitemap.xml`
- Robots: `robots.txt` đang cho phép crawl toàn site.
- Google Analytics 4 được khai báo trong `_config.yml`.
- Google Search Console verification được khai báo trong `_config.yml`.
- Các bài nên ưu tiên từ khóa long-tail có ý định tìm kiếm rõ: review, địa chỉ, giá, giờ mở cửa, quán gần Làng Đại học, quán học bài, ăn vặt sinh viên.

Mỗi tuần nên kiểm tra:

- Bài mới đã index chưa trên Google Search Console.
- Từ khóa nào có impression cao nhưng CTR thấp để sửa title/description.
- Bài nào có traffic tốt để thêm liên kết nội bộ sang bài mới.
- Link ngoài, ảnh Cloudinary và Google Maps còn hoạt động không.

## Triển khai

Workflow deploy chạy khi push lên `main` hoặc `master`, trừ các thay đổi chỉ liên quan đến `.gitignore`, `README.md` hoặc `LICENSE`.

Quy trình thông thường:

```bash
git add .
git commit -m "Add new local review post"
git push origin main
```

Sau khi push, kiểm tra tab Actions của GitHub để đảm bảo job `Build and Deploy` hoàn tất.

## Ghi chú bảo trì

- Không đổi permalink `/posts/:title/` nếu chưa có kế hoạch redirect, vì thay đổi này có thể làm mất URL đã index.
- Hạn chế tạo category/tag mới trùng nghĩa; ưu tiên chuẩn hóa theo `strategy.json`.
- File README bị loại khỏi build và thay đổi README không kích hoạt deploy.
- Nếu sửa `_includes/head.html`, `_config.yml` hoặc CSS theme, cần build lại trước khi push vì đây là các phần ảnh hưởng toàn site.
