# URL Shortener - Frontend (Vue 3 + Vite)

Đây là phần **frontend** của ứng dụng rút gọn URL, được xây dựng bằng **Vue 3 + Vite**.

## 📌 1. Cài đặt Frontend

### 1️⃣ **Clone project**
```sh
git clone https://github.com/Kamito69/TestFe.git
cd TestFe
```

### 2️⃣ Cài đặt dependencies
```sh
npm install
```

### 3️⃣ Cấu hình môi trường
Tạo file `.env` từ `.env.example` và chỉnh sửa URL API backend:
```sh
cp .env.example .env
```
Chỉnh sửa file `.env`:
```env
VITE_API_BASE_URL=http://127.0.0.1:8000/api
```

### 4️⃣ Chạy ứng dụng
```sh
npm run dev
```
Ứng dụng sẽ chạy tại: [http://localhost:5173](http://localhost:5173)

## 📌 2. Build & Deploy
Nếu muốn build ứng dụng để deploy lên production, chạy lệnh:
```sh
npm run build
```
Sau khi build xong, thư mục `dist/` sẽ chứa các file sẵn sàng để deploy.

## 📌 3. Các tính năng chính
- Nhập URL gốc để tạo URL rút gọn.
- Hiển thị danh sách các URL đã rút gọn.
- Click vào URL rút gọn để chuyển hướng.


