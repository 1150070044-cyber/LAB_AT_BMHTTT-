# LAB 3 - MÃ HÓA KHÓA CÔNG KHAI

## THÔNG TIN SINH VIÊN

- **Họ và tên:** Nguyễn Quang Tiến
- **MSSV:** 1150070044
- **Lớp:** 11TTMT
- **Môn học:** An toàn và bảo mật thông tin
- **Bài thực hành:** LAB 3 - Mã hóa khóa công khai

## 1. GIỚI THIỆU

Bài thực hành LAB 3 được xây dựng bằng ngôn ngữ Java, sử dụng Visual Studio Code, Maven và Microsoft SQL Server.

Chương trình minh họa các thuật toán mã hóa khóa công khai, hệ mã lai và chữ ký số. Đồng thời, ứng dụng có chức năng lưu lịch sử thao tác vào SQL Server.

## 2. NỘI DUNG THỰC HIỆN

### Bài 3.1 - RSA Console

- Sinh khóa RSA 2048 bit và 3072 bit.
- Mã hóa văn bản bằng RSA OAEP SHA-256.
- Giải mã và kiểm tra kết quả.
- Đo thời gian sinh khóa, mã hóa và giải mã.

**Kết quả:** Roundtrip PASS với cả hai kích thước khóa.

### Bài 3.2 - RSA Swing

- Xây dựng giao diện Java Swing.
- Sinh cặp khóa Public Key và Private Key.
- Mã hóa văn bản HELLO RSA.
- Giải mã và khôi phục văn bản ban đầu.

**Kết quả:** Mã hóa và giải mã thành công.

### Bài 3.3 - ECC

- Sử dụng đường cong P-256.
- Kết hợp ECDH, HKDF-SHA256 và AES-GCM.
- Mã hóa và giải mã văn bản HELLO ECC.
- Kiểm tra giải mã bằng khóa không phù hợp.

**Kết quả:** Đúng khóa giải mã thành công; sai khóa giải mã thất bại.

### Bài 3.4 - Hệ mã lai RSA + AES

- Sử dụng RSA-OAEP để bảo vệ khóa AES.
- Sử dụng AES-256-GCM để mã hóa văn bản dài.
- Giải mã và khôi phục dữ liệu.
- Kiểm tra trường hợp bản mã bị chỉnh sửa.

**Kết quả:** Giải mã đúng văn bản dài; phát hiện bản mã bị thay đổi.

### Bài 3.5 - Chữ ký số ECDSA

- Sinh cặp khóa ECDSA P-256.
- Ký thông điệp THONG DIEP A.
- Xác minh chữ ký số.
- Thay đổi thông điệp để kiểm tra tính toàn vẹn.

**Kết quả:**
- Thông điệp gốc: VALID.
- Thông điệp bị thay đổi: INVALID.

## 3. KẾT NỐI SQL SERVER

Ứng dụng kết nối Microsoft SQL Server để lưu lịch sử mã hóa, giải mã, ký và xác minh.

**Thông tin cơ sở dữ liệu:**

- Server: 127.0.0.1
- Port: 1433
- Database: LAB3_MaHoaKhoaCongKhai
- Bảng: dbo.History

Các trường dữ liệu:

- Id
- CreatedAt
- Algorithm
- Operation
- InputLength
- Success

**Kết quả:** Kết nối SQL Server thành công và ghi nhận được lịch sử thao tác.

## 4. CÔNG NGHỆ SỬ DỤNG

- Java 17
- Java Swing
- Apache Maven
- Visual Studio Code
- Microsoft SQL Server
- SQL Server Management Studio (SSMS)
- Microsoft JDBC Driver
