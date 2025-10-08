**Introduction to Software Engineering – PTIT**

---

## Thông tin sinh viên

- **Họ tên:** Đoàn Ngọc Thành  
- **MSSV:** K23DTCN560  
- **Lớp:** D23TXCN10-K  
- **Github:** [doanngocthanh](https://github.com/doanngocthanh)

---

## Đề tài: Hệ thống Trích xuất Thông tin bằng OCR

### Mục tiêu dự án

Phát triển hệ thống web tự động trích xuất thông tin (Họ tên, Ngày sinh, Số CMND/CCCD, Quê quán,...) từ ảnh giấy tờ tùy thân (CMND, CCCD, Hộ chiếu) và lưu kết quả vào CSDL.

### Phạm vi

- Nhận diện & xử lý:  
    - CMND 9 số  
    - CCCD 12 số (mặt trước)  
    - Hộ chiếu (trang thông tin chính)  
- Ngôn ngữ: Tiếng Việt

### Stakeholders

- **Người dùng:** Trích xuất dữ liệu từ giấy tờ cá nhân  
- **Quản trị viên:** Quản lý tài khoản, theo dõi lịch sử  
- **Kỹ sư phát triển:** Xây dựng, bảo trì hệ thống

### Giả định & Giới hạn

- Ảnh đầu vào rõ nét, giấy tờ hợp lệ  
- Không xử lý ảnh quá mờ, giấy tờ hết hạn hoặc ngoài CMND/CCCD/Hộ chiếu

---

## Yêu cầu hệ thống

### Chức năng

- Đăng ký/Đăng nhập/Đăng xuất
- Tải lên ảnh giấy tờ (JPG, PNG)
- Xử lý OCR, trích xuất thông tin
- Hiển thị kết quả, cho phép sửa/xác nhận
- Lưu kết quả vào CSDL
- Quản trị viên xem, tìm kiếm, thống kê lịch sử

### Phi chức năng

- **Hiệu năng:** Xử lý OCR ≤ 5 giây  
- **Bảo mật:** Dữ liệu cá nhân được mã hóa  
- **Khả năng sử dụng:** Giao diện trực quan  
- **Độ tin cậy:** Tỷ lệ trích xuất đúng ≥ 90%

---

## Sơ đồ & Mô hình

- **Use Case:**  
    - Người dùng: Đăng nhập, Tải ảnh, Xử lý OCR, Sửa/Lưu kết quả, Xem lịch sử  
    - Quản trị viên: Quản lý người dùng, lịch sử

- **Activity:**  
    1. Tải ảnh → Kiểm tra định dạng → Xử lý OCR → Hiển thị kết quả → Sửa/Xác nhận → Lưu

- **Class:**  
    - User (ID, Username, Password, Role)  
    - DocumentImage (ID, UserID, Path, Status)  
    - OCRResult (ID, ImageID, FullName, DoB, IDNumber, ExtractedDate, ConfidenceScore, RawJson)

---

## Kế hoạch dự án

| Giai đoạn                | Thời gian   | Công việc chính                                  |
|--------------------------|-------------|--------------------------------------------------|
| Khởi tạo/Yêu cầu         | 1 tuần      | Định nghĩa dự án, Viết SRS                       |
| Phân tích/Thiết kế       | 1.5 tuần    | Vẽ UML, Thiết kế CSDL, UI                        |
| Phát triển/Cài đặt       | 4 tuần      | Thiết lập MVC, Upload, OCR, Quản trị              |
| Kiểm thử/Triển khai      | 1.5 tuần    | Unit Test, Kiểm thử hệ thống, Triển khai          |

### Gantt Chart

| Công việc                | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|-------------------------|---|---|---|---|---|---|---|---|
| Khởi tạo/Yêu cầu        | X |   |   |   |   |   |   |   |
| Phân tích/Thiết kế      | X | X |   |   |   |   |   |   |
| Phát triển/Cài đặt      |   | X | X | X | X |   |   |   |
| Kiểm thử/Triển khai     |   |   |   |   | X | X |   |   |

---

## Quản lý rủi ro

| Rủi ro                | Mức độ | Kế hoạch giảm thiểu           |
|-----------------------|--------|-------------------------------|
| Chất lượng ảnh thấp   | Cao    | Hướng dẫn người dùng, cảnh báo|
| Lỗi OCR               | Trung  | Sử dụng nhiều thư viện, kiểm thử|
| Bảo mật dữ liệu       | Cao    | Mã hóa, phân quyền truy cập   |

---

## Thiết kế UI & Database

- **UI:**  
    - Trang Upload: Kéo/thả ảnh, nút "Tải lên", "Xử lý"
    - Trang Kết quả: Form dữ liệu, nút "Sửa", "Lưu"
    - Trang Quản trị: Danh sách người dùng, lịch sử

- **Database:**  
    - Thiết kế bảng theo ERD, trường dữ liệu phù hợp thông tin trích xuất

---

## Công nghệ & Triển khai

- **Framework:** FastAPI, YoloV8, VietOCR
- **Upload:** Tải ảnh lên server, lưu metadata
- **OCR:** Tích hợp thư viện OCR, trích xuất dữ liệu
- **Testing:** Unit Test upload, OCR, lưu dữ liệu
- **Quản lý lỗi:** GitHub Issues
- **Triển khai:** Demo: 

