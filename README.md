# BÀI THỰC HÀNH – QUẢN LÝ ĐƠN ĐẶT HÀNG

## 1. Mục tiêu
Xây dựng sơ đồ thực thể–liên kết (ERD) cho quy trình **đặt hàng** và **giao hàng**. Theo bước 5 của đề, hai thực thể “Đơn vị đặt hàng” và “Đơn vị khách hàng” được gộp thành **ĐƠN VỊ KHÁCH**.

## 2. Sơ đồ ERD hoàn chỉnh

![Sơ đồ ERD quản lý đơn đặt hàng](images/ERD_QuanLyDonDatHang.png)

[Xem ảnh SVG độ nét cao](images/ERD_QuanLyDonDatHang.svg)

## 3. Các thực thể và thuộc tính

| Thực thể | Thuộc tính |
|---|---|
| Đơn vị khách | **MaDV (PK)**, TenDV, DiaChi, DienThoai |
| Người đặt | **MaND (PK)**, HoTenND, MaDV (FK) |
| Người nhận | **MaNN (PK)**, HoTenNN, MaDV (FK) |
| Người giao | **MaNG (PK)**, HoTenNG |
| Nơi giao | **MaNoiGiao (PK)**, TenNoiGiao |
| Hàng | **MaHang (PK)**, TenHang, DonViTinh, MoTaHang |
| Đơn đặt hàng | **SoDH (PK)**, NgayDat, MaDV (FK), MaND (FK) |
| Chi tiết đơn hàng | **(SoDH, MaHang) (PK kép)**, SoLuong |
| Phiếu giao hàng | **SoPG (PK)**, NgayGiao, SoDH (FK), MaNoiGiao (FK), MaNN (FK), MaNG (FK) |
| Chi tiết phiếu giao | **(SoPG, MaHang) (PK kép)**, SoLuong, DonGia, ThanhTien (giá trị tính toán) |

## 4. Các quan hệ chính

- Một **đơn vị khách** có nhiều **người đặt**, **người nhận** và nhiều **đơn đặt hàng** (1–N).
- Một **người đặt** có thể lập nhiều **đơn đặt hàng** (1–N).
- Một **đơn đặt hàng** gồm nhiều **chi tiết đơn hàng**; một **mặt hàng** có thể xuất hiện trong nhiều đơn (N–M được tách bằng bảng chi tiết).
- Một **đơn đặt hàng** có thể có nhiều **phiếu giao hàng** (để hỗ trợ giao nhiều đợt).
- Một **phiếu giao hàng** có nhiều **chi tiết phiếu giao**; một **mặt hàng** có thể xuất hiện trên nhiều phiếu (N–M được tách bằng bảng chi tiết).
- Mỗi **phiếu giao hàng** ghi nhận một **nơi giao**, một **người nhận**, một **người giao** (mỗi người/địa điểm có thể gắn với nhiều phiếu).

## 5. Chuẩn hóa và lựa chọn thiết kế

- Gộp “Đơn vị đặt hàng” và “Đơn vị khách hàng” thành **Đơn vị khách** vì cùng mô tả một tổ chức khách hàng, tránh lặp tên và địa chỉ.
- Hai quan hệ nhiều–nhiều giữa **Đơn hàng–Hàng** và **Phiếu giao–Hàng** được chuyển thành thực thể liên kết chứa số lượng, đơn giá.
- **ThanhTien = SoLuong × DonGia** là thuộc tính dẫn xuất, có thể tính trong truy vấn thay vì lưu vật lý.
- Giả định thiết kế: một đơn hàng có thể giao nhiều lần và mỗi dòng chi tiết chỉ ghi một mặt hàng trên một đơn/phiếu. Đây là các giả định bổ sung để hoàn thiện ERD vì đề bài không xác định rõ bội số giao từng đợt.

## 6. Cách xem và nộp

Mở `images/ERD_QuanLyDonDatHang.png` để xem sơ đồ; tệp `.svg` cho phép phóng to không vỡ nét. Tải toàn bộ nội dung **bên trong** thư mục này lên một repository GitHub công khai, giữ nguyên đường dẫn `images/` để hình hiện trực tiếp trong README. Sau đó nộp đường dẫn trang chính repository lên CodeGym.

**Ghi chú:** Đây là sơ đồ được dựng từ mô tả đề bài, không phải ảnh chụp thao tác trên MySQL Workbench.
