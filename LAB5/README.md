# LAB 5 - CẤU HÌNH FIREWALL PFSENSE

## Thông tin sinh viên
- Họ và tên: Nguyễn Quang Tiến
- Mã số sinh viên: 1150070044

## Tên bài Lab
Thực hành cấu hình Firewall pfSense và kiểm soát truy cập giữa LAN, Internet và DMZ.

## Nội dung đã thực hiện
- Cài đặt và cấu hình pfSense.
- Cấu hình WAN, LAN và DMZ.
- Cấu hình Domain Controller.
- Cấu hình máy LAN-Test.
- Cấu hình máy DMZ-Web.

### Tình huống 1
Chặn ICMP nhưng vẫn cho phép DNS và HTTP/HTTPS.

### Tình huống 2
Chỉ cho phép Domain Controller 10.0.0.2 truy cập Internet và chặn các host LAN còn lại.

### Tình huống 3
Cô lập DMZ khỏi LAN nhưng vẫn cho phép DMZ truy cập Internet và phân giải DNS.

## Kết quả thực hiện
- ICMP bị chặn nhưng DNS và HTTPS vẫn hoạt động.
- Domain Controller 10.0.0.2 truy cập Internet thành công.
- LAN-Test 10.0.0.3 bị chặn truy cập Internet.
- DMZ-Web bị chặn truy cập vào LAN.
- DMZ-Web vẫn truy cập Internet và phân giải DNS thành công.

## Thông số mạng
- pfSense LAN: 10.0.0.1/8
- Domain Controller: 10.0.0.2/8
- LAN-Test: 10.0.0.3/8
- pfSense DMZ: 172.16.0.1/16
- DMZ-Web: 172.16.0.2/16

## File nộp
- Bao_cao_pfSense_Tinh_huong_1_den_3.docx
- README.md

## Lưu ý
Sau khi thay đổi Firewall Rule cần Apply Changes và Reset States trước khi kiểm thử để tránh các state cũ ảnh hưởng đến kết quả.
