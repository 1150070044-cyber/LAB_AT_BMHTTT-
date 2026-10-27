LAB8 - LOCAL DNS ATTACK

1. Thông tin sinh viên

Họ và tên: Nguyễn Quang Tiến

Mã số sinh viên: 1150070044

Môn học: An toàn và Bảo mật Hệ thống Thông tin

Tên bài thực hành: Local DNS Attack - DNS Spoofing và DNS Cache Poisoning

2. Mục tiêu bài thực hành

Tìm hiểu nguyên lý hoạt động của hệ thống DNS.

Cấu hình DNS Server sử dụng BIND9 trên Ubuntu Server.

Tìm hiểu các hình thức tấn công DNS Spoofing và DNS Cache Poisoning.

Sử dụng Kali Linux để mô phỏng tấn công trong mạng ảo cô lập.

Sử dụng Wireshark để quan sát và phân tích các gói tin DNS.

Tìm hiểu các biện pháp phòng chống và khôi phục hệ thống DNS.

3. Môi trường thực hành

VirtualBox: Tạo và quản lý máy ảo.

pfSense: Quản lý mạng và thiết lập Firewall.

Ubuntu Server 24.04: Cấu hình DNS Server BIND9.

Ubuntu Desktop: Máy Victim.

Kali Linux: Máy mô phỏng tấn công.

Wireshark: Phân tích lưu lượng mạng.

Scapy: Công cụ tạo và xử lý gói tin.

Địa chỉ IP trong mô hình:

pfSense DNSLAB: 10.9.0.1

DNS Server: 10.9.0.10

Victim: 10.9.0.100

Attacker Kali: 10.9.0.200

DMZ Web: 172.16.6.10

AUTH-DNS: 172.16.6.20

4. Nội dung thực hành

Task 1: Thay đổi Hosts File

Tìm hiểu chức năng của file /etc/hosts.

Mô phỏng việc thay đổi địa chỉ IP ánh xạ với tên miền.

Kiểm tra sự khác biệt giữa kết quả phân giải tên miền thông qua file hosts và DNS Server.

Task 2: Direct DNS Spoofing

Quan sát các truy vấn DNS từ máy Victim.

Tìm hiểu cơ chế giả mạo phản hồi DNS.

Sử dụng Wireshark để phân tích gói tin DNS hợp lệ và gói tin giả mạo.

Kiểm tra sự thay đổi kết quả phân giải tên miền trên máy Victim.

Task 3: DNS Cache Poisoning

Tìm hiểu cơ chế lưu trữ bộ nhớ đệm DNS.

Mô phỏng việc đưa bản ghi DNS giả vào cache trong môi trường thử nghiệm.

Quan sát ảnh hưởng của bản ghi giả đến quá trình phân giải tên miền.

Kiểm tra và khôi phục bộ nhớ đệm DNS sau thử nghiệm.

5. Kết quả thực hiện

Các kết quả cần kiểm tra trong bài thực hành:

DNS Server hoạt động và phân giải tên miền hợp lệ.

Kết quả DNS ban đầu trả về địa chỉ 172.16.6.10.

Task 1: File hosts chuyển hướng tên miền đến 10.9.0.200.

Task 2: Quan sát phản hồi DNS giả và kiểm tra kết quả trên Victim.

Task 3: Kiểm tra bản ghi DNS giả trong bộ nhớ đệm BIND9.

Sau khi khôi phục, DNS trả về địa chỉ hợp lệ 172.16.6.10.
