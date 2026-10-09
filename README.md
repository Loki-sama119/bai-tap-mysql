# Thực hành: Xóa cơ sở dữ liệu trong MySQL Workbench

## Mục tiêu
Thực hành **hai cách xóa cơ sở dữ liệu (CSDL)**: (1) thao tác trên giao diện đồ họa (GUI) của MySQL Workbench và (2) thực thi câu lệnh SQL.

> **Lưu ý:** Thực hành chỉ sử dụng các cơ sở dữ liệu thử nghiệm `bt_xoa_gui` và `bt_xoa_sql`, không thao tác trên cơ sở dữ liệu dự án hay cơ sở dữ liệu hệ thống.

## 1. Xóa CSDL bằng giao diện MySQL Workbench (GUI)

1. Mở MySQL Workbench, đăng nhập vào kết nối `Localhost`.
2. Trong khung **SCHEMAS**, làm mới danh sách và tìm CSDL thử nghiệm `bt_xoa_gui`.
3. Nhấp chuột phải vào `bt_xoa_gui` và chọn lệnh **Drop Schema** trong menu ngữ cảnh.
4. Hộp thoại **Confirmation** hiện ra, hỏi có muốn xóa schema `bt_xoa_gui` không. Ảnh dưới đây ghi lại thao tác GUI **trước khi xác nhận xóa**:

![Hộp thoại xác nhận Drop bt_xoa_gui trong MySQL Workbench](images/01_gui_xac_nhan_xoa.png)

5. Nhấn nút **Drop bt_xoa_gui** để xác nhận. Workbench hiển thị thông báo `The object bt_xoa_gui has been dropped successfully.` (ở góc dưới bên phải ảnh):

![Thông báo xóa bt_xoa_gui thành công](images/02_gui_xoa_thanh_cong.png)

6. Làm mới danh sách SCHEMAS và thực thi `SHOW DATABASES;` để kiểm tra. CSDL `bt_xoa_gui` không còn trong danh sách:

![Danh sách cơ sở dữ liệu sau khi xóa](images/03_kiem_tra_sau_xoa.png)

**Kết quả:** Đã xóa CSDL thử nghiệm `bt_xoa_gui` thông qua giao diện đồ họa Workbench, có ảnh xác nhận thao tác và ảnh kết quả.

## 2. Xóa CSDL bằng câu lệnh SQL

Mở SQL Editor và thực thi:

```sql
DROP DATABASE IF EXISTS bt_xoa_sql;
SHOW DATABASES;
```

- `DROP DATABASE IF EXISTS`: xóa CSDL nếu tồn tại, không phát sinh lỗi nếu CSDL đã bị xóa.
- `SHOW DATABASES;`: kiểm tra lại danh sách CSDL.

![SQL xóa CSDL và danh sách kiểm tra](images/04_sql_xoa_csdl.png)

**File mã nguồn:** [xoa_csdl_bang_sql.sql](xoa_csdl_bang_sql.sql).

## 3. Chuẩn bị thực hành

Tạo hai CSDL thử nghiệm bằng file [chuan_bi_csdl_thuc_hanh.sql](chuan_bi_csdl_thuc_hanh.sql).

## Kết luận
Đã thực hành **xóa CSDL bằng giao diện GUI** và **xóa CSDL bằng câu lệnh SQL**, kèm ảnh chụp màn hình minh chứng cho phần GUI và file SQL cho phần dòng lệnh.
