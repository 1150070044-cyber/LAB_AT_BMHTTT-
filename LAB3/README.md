Họ và tên sinh viên : Nguyễn Quang Tiến 
Mã số sinh viên   : 1150070044
Tên bài Lab       :LAB 3 NHẬN DIỆN VÀ ỨNG PHÓ CÁC MỐI ĐE DỌA ĐẾN AN TOÀN THÔNG TIN 
Nội dung đã thực hiện :
- Cấu hình máy ảo Windows Server 2025 và mạng Host-only.
- Kiểm tra phiên bản hệ điều hành và phiên bản các công cụ.
- Kiểm tra trạng thái Microsoft Defender và Windows Firewall.
- Kiểm thử Defender bằng file EICAR và xác nhận phát hiện thành công.
- Bật Audit Logon Success/Failure.
- Tạo tài khoản lab3user và kiểm tra các sự kiện 4624, 4625, 4648.
- Thực hiện đổi mật khẩu và xác minh mật khẩu cũ không còn hợp lệ.
- Cài đặt Sysmon và kiểm tra Event ID 1, Event ID 13.
- Tạo Run key LAB3_Run_Demo và Scheduled Task LAB3_Persistence_Demo.
- Kiểm tra persistence bằng Autoruns.
- Xác định tiến trình Python HTTP server bằng Process Explorer.
- Bắt lưu lượng HTTP plaintext bằng Wireshark.
- Bắt lưu lượng HTTPS/TLS trên port 443 và so sánh với HTTP.
Kết quả thực hiện
- Microsoft Defender hoạt động và phát hiện EICAR thành công.
- Windows Firewall được bật trên các profile Domain, Private và Public.
- Event Viewer ghi nhận được các sự kiện đăng nhập thành công và thất bại.
- Sysmon ghi nhận được Process Create và Registry modification.
- Autoruns phát hiện được Run key LAB3_Run_Demo.
- Process Explorer xác định đúng tiến trình Python chạy HTTP server trên 127.0.0.1:8080.
- Wireshark quan sát được dữ liệu HTTP ở dạng plaintext.
- Lưu lượng HTTPS sử dụng TLS 1.3 và không hiển thị query string ở dạng plaintext.

Các lưu ý cần thiết để giảng viên có thể kiểm tra hoặc chạy lại bài  làm.
- Môi trường thực hành: Windows Server 2025 Standard Evaluation.
- Mạng mặc định của LAB3 sử dụng Host-only.
- NAT chỉ được sử dụng tạm thời khi cần tải công cụ hoặc tạo traffic HTTPS.
- HTTP server chỉ bind tại 127.0.0.1:8080.
- Tài khoản lab3user chỉ được tạo phục vụ bài thực hành.
- EICAR chỉ là chuỗi kiểm thử antivirus, không phải malware thực tế.
- Không lưu mật khẩu hoặc credential thật trong repository.
