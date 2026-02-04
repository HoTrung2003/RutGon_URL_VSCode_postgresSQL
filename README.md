# Rút Gọn URL -- VS Code & PostgreSQL

## Giới thiệu

Dự án **Rút gọn URL** được xây dựng bằng **VS Code**, sử dụng
**PostgreSQL** làm cơ sở dữ liệu.\
Ứng dụng giúp chuyển các URL dài thành các URL rút gọn có mã ngẫu nhiên,
dễ chia sẻ, dễ quản lý.

## Công nghệ sử dụng

-   Ngôn ngữ lập trình: **JavaScript / Node.js** 
-   IDE: **Visual Studio Code**
-   Cơ sở dữ liệu: **PostgreSQL**
-   Thư viện/Framework liên quan :
    -   ExpressJS 
    -   pg / prisma 
    -   Các thư viện hỗ trợ sinh mã ngẫu nhiên

## Chức năng chính

-   Rút gọn URL dài thành URL có mã ngắn.
-   Tự động chuyển hướng khi truy cập URL rút gọn.
-   Lưu trữ URL gốc và URL rút gọn trong PostgreSQL.
-   Thống kê số lượt truy cập .
-   API tạo URL rút gọn .

## Cấu trúc thư mục (tham khảo)

    /project
    │── src/
    │   ├── controllers/
    │   ├── routes/
    │   ├── models/
    │   ├── database/
    │   └── app.js
    │── package.json
    │── README.md

## Cấu hình cơ sở dữ liệu

1.  Cài đặt PostgreSQL.
2.  Tạo database:

``` sql
CREATE DATABASE shorturl_db;
```

3.  Tạo bảng:

``` sql
CREATE TABLE urls (
    id SERIAL PRIMARY KEY,
    original_url TEXT NOT NULL,
    short_code VARCHAR(20) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Chạy dự án

### 1. Cài đặt package

    npm install

### 2. Cấu hình biến môi trường

Tạo file `.env`:

    DATABASE_URL=postgres://user:password@localhost:5432/shorturl_db
    PORT=3000

### 3. Chạy server

    npm start

## API Endpoints (nếu applicable)

  Method   Endpoint         Mô tả
  -------- ---------------- --------------------------
  POST     `/api/shorten`   Tạo URL rút gọn
  GET      `/:shortCode`    Chuyển hướng đến URL gốc

## Ghi chú

-   Bạn có thể mở rộng thêm chức năng bảo mật, thống kê, giao diện UI.
-   Xem code chi tiết trong repo GitHub.

## Tác giả

**HoTrung2003**\
GitHub: https://github.com/HoTrung2003
