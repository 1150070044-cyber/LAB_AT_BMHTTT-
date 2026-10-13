# LAB 6 - PFSENSE, ACTIVE DIRECTORY VÀ ACCESS POLICIES

## Thông tin sinh viên
- Họ và tên: Nguyễn Quang Tiến
- Mã số sinh viên: 1150070044

## Tên bài Lab
LAB 6 - Cấu hình pfSense, Active Directory, LDAP, Captive Portal và Access Policies

## 1. Mô hình LAB

Mô hình LAB gồm:

- pfSense-LAB6 với 4 interface:
  - WAN
  - MGMT
  - LAN
  - DMZ

- Máy thật quản trị:
  - IP: 192.168.56.1/24
  - Dùng để truy cập WebGUI pfSense

- pfSense MGMT:
  - IP: 192.168.56.254/24

- pfSense LAN:
  - IP: 10.6.0.1/24

- Domain Controller DC01:
  - IP: 10.6.0.10/24
  - Gateway: 10.6.0.1
  - DNS: 10.6.0.10
  - Domain: lab6.test

- Client-A:
  - IP: 10.6.0.21/24
  - DNS: 10.6.0.10

- Client-B:
  - IP: 10.6.0.22/24
  - DNS: 10.6.0.10

- pfSense DMZ:
  - IP: 172.16.6.1/24

- DMZ-WEB:
  - IP chính: 172.16.6.10/24
  - Gateway: 172.16.6.1
  - IP mô phỏng website: 172.16.6.20, 172.16.6.30, 172.16.6.40

## 2. Nội dung đã thực hiện

### 2.1. Dựng pfSense-LAB6
- Tạo máy ảo pfSense riêng cho LAB6.
- Cấu hình 4 card mạng WAN, MGMT, LAN và DMZ.
- Cấu hình địa chỉ IP tĩnh cho MGMT, LAN và DMZ.
- Truy cập WebGUI pfSense thông qua mạng MGMT.

### 2.2. Active Directory và DNS
- Cấu hình Windows Server làm Domain Controller.
- Cài đặt AD DS và DNS.
- Tạo forest/domain:
  - lab6.test
- Tạo OU:
  - LAB6-Users
- Tạo các tài khoản:
  - sv_a
  - sv_b
  - svc_pfsense_ldap

### 2.3. LDAP Authentication
- Thêm LDAP Authentication Server trên pfSense.
- Kết nối pfSense với Active Directory.
- Kiểm thử xác thực tài khoản sv_a và sv_b bằng Diagnostics → Authentication.

### 2.4. Captive Portal
- Tạo Captive Portal Zone trên LAN.
- Cấu hình nguồn xác thực sử dụng LDAP/Active Directory.
- Kiểm thử đăng nhập bằng tài khoản domain.

### 2.5. Alias

Tạo các Alias phục vụ firewall policy:

- CLIENT_A = 10.6.0.21
- CLIENT_B = 10.6.0.22
- POLICY_CLIENTS = Client-A + Client-B

Các website mô phỏng:

- GENERAL_SITE = 172.16.6.10
- JOB_SITE = 172.16.6.20
- SOCIAL_SITE = 172.16.6.30
- RESTRICTED_SITE = 172.16.6.40

Alias port:

- WEB_PORTS = 80, 443

### 2.6. Schedule

Tạo các Schedule:

- LUNCH_WINDOW:
  - 11:30–13:00
  - Thứ 2 đến Thứ 6

- WORK_HOURS:
  - 08:00–17:00
  - Thứ 2 đến Thứ 6

- TEST_NOW:
  - Dùng tạm thời để kiểm thử schedule tại thời điểm thực hành

## 3. Các kịch bản đã thực hiện

### Kịch bản 1 - Client-A bị chặn JOB_SITE

Firewall Rule:

1. Block
   - Source: CLIENT_A
   - Destination: JOB_SITE
   - Protocol/Port: TCP/80
   - Bật logging

2. Pass
   - Source: CLIENT_A
   - Destination: GENERAL_SITE
   - Protocol/Port: TCP/80

Kiểm thử:

- Client-A truy cập:
  - http://172.16.6.10 → thành công
  - http://172.16.6.20 → bị chặn

Firewall Log phải ghi nhận:

- Source: 10.6.0.21
- Destination: 172.16.6.20
- Action: Block

### Kịch bản 2 - Chặn RESTRICTED_SITE cho Client-A và Client-B

Firewall Rule:

1. Block
   - Source: POLICY_CLIENTS
   - Destination: RESTRICTED_SITE
   - Protocol/Port: TCP/80
   - Bật logging

2. Pass
   - Source: POLICY_CLIENTS
   - Destination: GENERAL_SITE
   - Protocol/Port: TCP/80

Kiểm thử:

- Client-A:
  - 172.16.6.40 → bị chặn
  - 172.16.6.10 → truy cập được

- Client-B:
  - 172.16.6.40 → bị chặn
  - 172.16.6.10 → truy cập được

### Kịch bản 3 - Client-B chỉ được SOCIAL_SITE trong giờ nghỉ

Firewall Rule:

1. Pass
   - Source: CLIENT_B
   - Destination: SOCIAL_SITE
   - Schedule: LUNCH_WINDOW

2. Block
   - Source: CLIENT_B
   - Destination: SOCIAL_SITE
   - Schedule: Always

Kiểm thử:

- Trong thời gian Schedule active:
  - Client-B truy cập 172.16.6.30 → thành công

- Ngoài thời gian Schedule:
  - Client-B truy cập 172.16.6.30 → bị chặn

Trong lúc thực hành có thể dùng TEST_NOW để kiểm tra ngay, sau đó đổi lại LUNCH_WINDOW.

### Kịch bản 4 - Chỉ cho HTTP/HTTPS trong giờ hành chính

Firewall Rule:

1. Pass
   - Source: POLICY_CLIENTS
   - Destination: Any
   - Port: WEB_PORTS
   - Schedule: WORK_HOURS

2. Block
   - Source: POLICY_CLIENTS
   - Destination: Any
   - Schedule: Always

Kiểm thử:

Trong WORK_HOURS:

- HTTP/HTTPS → được phép
- Ping hoặc các dịch vụ khác → bị chặn

Ngoài WORK_HOURS:

- Rule Pass không còn active
- Rule Block phía dưới xử lý lưu lượng

### Kịch bản 5 - Cô lập DMZ khỏi LAN nhưng cho LAN truy cập website cần thiết

Rule trên interface DMZ:

- Action: Block
- Source: DMZ net
- Destination: LAN net

Mục đích:
- Không cho máy trong DMZ chủ động khởi tạo kết nối vào LAN.

Rule trên interface LAN:

- Action: Pass
- Source: POLICY_CLIENTS
- Destination: GENERAL_SITE

Kiểm thử:

- Client-A → 172.16.6.10
  - Kết quả: Pass

- DMZ-WEB → 10.6.0.10
  - Kết quả: Block

Lưu ý:
Không dùng traffic phản hồi của kết nối do LAN khởi tạo để kết luận, vì pfSense là stateful firewall.

## 4. Kết quả

- pfSense-LAB6 hoạt động với 4 interface WAN, MGMT, LAN và DMZ.
- Máy thật quản trị truy cập được WebGUI qua MGMT.
- Active Directory và DNS hoạt động.
- pfSense xác thực được user domain qua LDAP.
- Captive Portal hoạt động với user Active Directory.
- Alias và Schedule được cấu hình thành công.
- Hoàn thành các Kịch bản 1 đến Kịch bản 5.
- Các policy hoạt động đúng theo Source, Destination, Port và Schedule.
- Firewall Log được sử dụng để kiểm chứng các rule Block.

## 5. Lưu ý khi kiểm thử

- Firewall rule trên pfSense xử lý từ trên xuống dưới theo nguyên tắc first-match.
- Sau khi thay đổi rule quan trọng cần:
  - Apply Changes
  - Tạo kết nối mới
  - Reset States khi cần
- Các IP client và server được cấu hình tĩnh để dễ kiểm tra policy.
- Cần kiểm tra đúng interface khi tạo firewall rule.
- Cần bật logging trên các rule Block quan trọng.
