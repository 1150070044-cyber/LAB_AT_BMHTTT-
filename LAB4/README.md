# LAB 4 - KHẢO SÁT VÀ ĐÁNH GIÁ BỀ MẶT MẠNG BẰNG NMAP

## Thông tin sinh viên

- Họ và tên: Nguyễn Quang Tiến
- Mã số sinh viên: 1150070044
- Lớp: 11_TTMT

## Tên bài Lab

LAB 4 - Khảo sát và đánh giá bề mặt mạng bằng Nmap

## Môi trường thực hành

- VMware Workstation
- Kali Linux
- Windows Server 2025
- Mạng Host-Only
- Kali Linux: 192.168.11.128
- Windows Server 2025: 192.168.11.129

## Nội dung đã thực hiện

- Cấu hình mạng Host-Only giữa Kali Linux và Windows Server 2025.
- Kiểm tra địa chỉ IP của hai máy.
- Kiểm tra kết nối bằng ping.
- Phát hiện host đang hoạt động bằng Nmap.
- TCP Connect Scan (-sT).
- SYN Scan (-sS).
- FIN Scan (-sF).
- Xmas Scan (-sX).
- NULL Scan (-sN).
- ACK Scan (-sA).
- UDP Scan.
- Nhận diện dịch vụ và phiên bản bằng -sV.
- Nhận diện hệ điều hành bằng -O.
- Aggressive Scan bằng -A.
- Kiểm tra giao thức SMB bằng NSE.
- Kiểm tra MS17-010.
- Xuất kết quả quét ra file.
- Thực hiện Before/After Hardening bằng Windows Firewall.

## Kết quả thực hiện

- Kali Linux và Windows Server 2025 kết nối thành công trong mạng Host-Only.
- Phát hiện Windows Server tại địa chỉ 192.168.11.129.
- Phát hiện dịch vụ Microsoft HTTPAPI trên cổng 5985/tcp.
- Cổng SMB 445/tcp được kiểm tra bằng NSE.
- NSE smb-protocols phát hiện các dialect SMB:
  - SMB 2.0.2
  - SMB 2.1
  - SMB 3.0
  - SMB 3.0.2
  - SMB 3.1.1
- Sau khi hardening, cổng SMB 445 không còn ở trạng thái open.
- Số cổng open giảm từ 2 xuống 1.

## Before / After Hardening

### Before

- 445/tcp: open
- 5985/tcp: open
- 998 cổng filtered

### After

- 5985/tcp: open
- 999 cổng filtered
- 445/tcp không còn truy cập được từ Kali.

## Lưu ý khi chạy lại

1. Khởi động Kali Linux và Windows Server 2025.
2. Đặt hai máy trong cùng mạng VMware Host-Only.
3. Kiểm tra lại địa chỉ IP vì DHCP có thể cấp IP khác.
4. Chỉ thực hiện quét trên các máy ảo thuộc môi trường Lab.
5. Khi kiểm tra SMB, bảo đảm dịch vụ SMB đang chạy và firewall được cấu hình phù hợp.
