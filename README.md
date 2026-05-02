# 💊 Quản Lý Danh Mục Thuốc – BVĐN

Hệ thống quản lý danh mục thuốc đấu thầu 2021–2025, chạy hoàn toàn trên trình duyệt (không cần server).

## 🚀 Deploy lên GitHub Pages

1. Tạo repo mới trên GitHub (ví dụ: `danh-muc-thuoc`)
2. Upload **toàn bộ** các file trong thư mục này vào repo
3. Vào **Settings → Pages → Source**: chọn `main` branch, thư mục `/root`
4. Save → Truy cập tại: `https://<username>.github.io/<repo-name>/`

## 📁 Cấu trúc file

```
├── index.html        ← Giao diện chính
├── style.css         ← CSS toàn bộ
├── app.js            ← Logic JavaScript
├── manifest.json     ← Thông tin số lượng chunk
├── data_0.json       ← Dữ liệu chunk 1 (~250KB)
├── data_1.json       ← Dữ liệu chunk 2
├── ...
└── data_9.json       ← Dữ liệu chunk cuối
```

> ⚠️ **Quan trọng**: Phải upload ĐỦ tất cả file `data_*.json` — thiếu 1 file sẽ lỗi.

## ✨ Tính năng

### 📋 Tab Danh mục
- Hiển thị **toàn bộ thuốc còn hiệu lực** mặc định
- **Ẩn/hiện cột** tuỳ chọn — click từng cột
- **Tìm kiếm** theo QĐTT / Tên thuốc / Hoạt chất
- **Lọc** theo nguồn ban hành: SYT hoặc BVĐN
- **Bật/tắt** hiển thị thuốc hết hiệu lực (row tô đỏ)
- **Sắp xếp** theo cột, phân trang 50–500 dòng/trang
- Badge trạng thái: ✅ Còn HH / ⚠️ Sắp hết / ⏰ Hết HH
- **Xuất Excel** theo bộ lọc hiện tại

### 📊 Tab Phân bổ
- Theo dõi số lượng nhập kho theo tháng
- Nhập tay hoặc nạp file Excel nhập hàng
- Tính tự động: **Còn lại = SL phân bổ − Tổng nhập**
- Thanh progress % cảnh báo màu khi > 80%
- **Xuất Excel** để lưu và nạp lại lần sau

### 📤 Tab Nạp dữ liệu
- Nạp thêm file Excel danh mục mới (merge tự động)
- Lưu/khôi phục từ localStorage trình duyệt
- Xuất/nạp JSON backup

## 📋 Format file nhập kho (Tab Phân bổ)

| Cột A | Cột B | Cột C | Cột D |
|-------|-------|-------|-------|
| QĐTT | Tên thuốc | SL nhập | Tháng (YYYY-MM) |

## 🛠️ Nạp thêm dữ liệu mới

Upload file Excel danh mục mới qua **Tab "Nạp dữ liệu"** — app sẽ:
- Cộng thêm mục mới vào danh sách
- Cập nhật mục đã có (trùng QĐTT + STT)
