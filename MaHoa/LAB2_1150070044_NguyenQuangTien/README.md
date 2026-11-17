# LAB 2 – MÃ HÓA ĐỐI XỨNG HIỆN ĐẠI

## 1. Thông tin sinh viên
- **Họ và tên:** Nguyễn Quang Tiến
- **Mã số sinh viên:** 1150070044
- **Lớp:** 11TTMT
- **Học phần:** An toàn và Bảo mật thông tin

## 2. Tên bài thực hành
LAB 2 – Mã hóa đối xứng hiện đại.

## 3. Nội dung thực hiện
- Bài 2.1: Mã hóa và giải mã DES.
- Bài 2.2: Mã hóa và giải mã TripleDES.
- Bài 2.3: Mã hóa AES, đăng ký và đăng nhập tài khoản, kết nối SQL Server.
- Bài 2.4: Mã hóa RC4.
- Bài 2.5: Mã hóa Twofish.
- Bài 2.6: Mã hóa AES-CTR và AES-CBC bằng Python.
- Xây dựng giao diện chương trình bằng Java Swing.
- Sử dụng Microsoft SQL Server để quản lý tài khoản và lịch sử thao tác.

## 4. Công cụ sử dụng
- Visual Studio Code
- Java JDK 17 hoặc 21
- Apache Maven
- Microsoft SQL Server và SSMS
- Python 3

## 5. Kết quả thực hiện
- Chương trình mã hóa và giải mã: Chưa cập nhật kết quả kiểm thử.
- Kết nối SQL Server: Chưa cập nhật kết quả kiểm thử.
- Chức năng đăng ký, đăng nhập: Chưa cập nhật kết quả kiểm thử.
- Các chức năng lưu và mở file: Chưa cập nhật kết quả kiểm thử.

## 6. Hướng dẫn chạy chương trình
1. Mở thư mục project bằng Visual Studio Code.
2. Kiểm tra JDK và Maven đã được cài đặt.
3. Chạy các script trong thư mục `sql` bằng SQL Server Management Studio.
4. Mở Terminal tại thư mục chứa `pom.xml`.
5. Chạy các lệnh:

```bash
mvn clean compile
mvn exec:java
```

6. Trong ứng dụng, mở chức năng kết nối SQL Server, nhập thông tin kết nối và kiểm tra.
7. Chọn từng thuật toán để thực hiện mã hóa, giải mã và kiểm thử.

## 7. Lưu ý
- Cần chạy SQL Server trước khi sử dụng chức năng đăng nhập và lưu lịch sử.
- Kiểm tra đúng cổng SQL Server theo cấu hình của bài thực hành (14333).
- Không đưa mật khẩu thật hoặc thông tin bí mật lên GitHub.
- Cập nhật phần kết quả thực hiện sau khi đã chạy và kiểm thử chương trình.
