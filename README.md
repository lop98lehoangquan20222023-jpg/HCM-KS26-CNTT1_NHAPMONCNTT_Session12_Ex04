# BÁO CÁO TỔNG QUAN: EMR & XỬ LÝ DỮ LIỆU Y TẾ

---

## Phần 1. Phân tích: Yêu cầu Chức năng vs. Phi chức năng (Bảo mật)

* **Yêu cầu Chức năng (LÀM CÁI GÌ):** Các tính năng nghiệp vụ trực tiếp phục vụ người dùng.
  * *Ví dụ:* Đăng ký khám, kê đơn thuốc, tạo bệnh án, tra cứu lịch sử bệnh.
* **Yêu cầu Phi chức năng - Bảo mật (LÀM NHƯ THẾ NÀO):** Các tiêu chuẩn đảm bảo an toàn và vận hành hệ thống.
  * *Ví dụ:* 
    * **Mã hóa:** Bảo vệ dữ liệu bằng mã hóa AES-256 (lưu trữ) và TLS 1.3 (truyền tải).
    * **Phân quyền (RBAC):** Bác sĩ chỉ xem được bệnh án thuộc chuyên khoa; Lễ tân chỉ xem thông tin hành chính.
    * **Nhật ký (Audit Log):** Ghi vết 100% lượt truy cập, sửa, xóa bệnh án.

---

## Phần 2. Triển khai: Hệ thống Clinic-Cloud & Xử lý Dữ liệu Excel

### 1. Khắc phục lỗi "AutoFilter" bị đứt đoạn do ô trống
* **Nguyên nhân:** Excel dừng bộ lọc tự động khi gặp các hàng bị rỗng toàn bộ hoặc đứt đoạn.
* **Giải pháp:**
  1. **Chuyển sang dạng Bảng (`Ctrl + T`):** Nhấn `Ctrl + T` để biến vùng dữ liệu thành *Excel Table*. Tính năng này tự động khóa toàn bộ phạm vi dữ liệu, không bị ngắt quãng dù có ô trống.
  2. **Chuẩn hóa dữ liệu:** Điền giá trị `N/A` hoặc `Chưa cập nhật` vào các ô trống thay vì để trắng.

### 2. Vẽ biểu đồ Donut Chart tối giản (Số liệu dịch bệnh)
* **Bước 1:** Chuẩn bị dữ liệu 2 cột: *Tên nhóm bệnh* và *Số lượng ca*.
* **Bước 2:** Chọn Insert > Chart > Donut Chart.
* **Bước 3 (Tối giản):**
  * Xóa bỏ đường lưới (Gridlines) và chú thích không cần thiết.
  * Chỉnh độ rộng lỗ tròn (Hole Size) về **50% - 60%**.
  * Chèn tổng số ca bệnh vào chính giữa vòng tròn.

---

## Phần 3. Kiểm thử: Khắc phục lỗi định dạng Heading Styles

Khi đoạn văn bị dán nhầm thành tiêu đề (Heading) khiến Mục lục tự động bị sai:

* **Thao tác:** Bôi đen đoạn văn bị lỗi $\rightarrow$ Nhấn **`Ctrl + Shift + N`**.
* **Kết quả:** Đưa văn bản về lại kiểu **Normal** ban đầu và loại bỏ khỏi Mục lục.