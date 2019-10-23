# Mục Lục

# 1.Khái niệm về log

- Ví dụ:Trong hệ thống mạng doanh nghiệp có một máy chủ chứa dữ liệu quan trọng.Server này hoạt động 24/24,khi dữ liệu bị mất thì để điều ra xử lý hay tìm nguyên nhân khắc phục thì `log` sẽ giúp làm việc này.

- Log ghi lại liên tục các thông báo về hoạt động của cả hệ thống hoặc của các dịch vụ được triển khai trên hệ thống và file tương ứng
- Log file thường là các file văn bản thông thường dưới dạng “clear text” 
- Các file log có thể nói cho bạn bất cứ thứ gì bạn cần biết, để giải quyết các rắc rối mà bạn gặp phải miễn là bạn biết ứng dụng nào, tiến trình nào được ghi vào log nào cụ thể.
- Trong hầu hết hệ thống Linux thì /var/log là nơi lưu lại tất cả các log.
 ![]()
 
# 2.Syslog 

## 2.1:Giới thiệu về Syslog

- Syslog là một giao thức client/server là giao thức dùng để chuyển log và thông điệp đến máy nhận log

- Máy nhận log thường được gọi là syslogd, syslog daemon hoặc syslog server.

- Syslog có thể gửi qua UDP hoặc TCP. Các dữ liệu được gửi dạng cleartext. Syslog dùng cổng 514.

- Ban đầu Internet Engineering Task Forec (IETF) đưa ra chuẩn syslog trong RFC 5424.

- Sau đó IETF đã ban hành RFC 3195 (Đảm bảo tin cậy cho syslog) và RFC 6587 (Truyền tải thông báo syslog qua TCP).

- Trong chuẩn syslog, mỗi thông báo đều được dán nhãn và được gán các mức độ nghiêm trọng khác nhau

## Nguồn sinh ra log

| code | Nguồn tạo log | Ý nghĩa |
|------|--------------|---------|
|0|kernel|Những log mà kernel sinh ra|
|1|user|Log ghi lại cấp độ người dùng|
|2|mail|Log của hệ thống mail|
|3|daemon|Log của các tiến trình trên hệ thống|
|4|auth|Log của quá trình đăng nhập hoặc xác thực|
|5|syslog|Log từ chương trình syslogd|
|6|lpr|Log từ quá trình in ấn|
|7|news|Thông tin từ hệ thống|
|8|uucp|Log UUCP subsystem|
|9||Clock deamon|
|10|authpriv|Quá trình đăng nhập hoặc xác thực hệ thống|
|11|ftp|Log của FTP deamon|
|12||Log từ dịch vụ NTP của các subserver|
|13||Kiểm tra đăng nhập|
|14||Log cảnh báo hệ thống|
|15|cron|Log từ clock daemon|
|16-23|local 0-7|Log dự trữ cho sử dụng nội bộ|

## Mức độ cảnh báo

| code | Mức độ cảnh báo | Ý nghĩa |
|------|-----------------|---------|
|0|emerg|Thông báo tình trạng khẩn cấp|
|1|alert|Hệ thống cần can thiệp ngay|
|2|Crit|Tình trạng nguy kịch|
|3|error|Thông báo lỗi từ hệ thống|
|4|warn|Mức cảnh báo đối với hệ thống|
|5|notice|Chú ý đối với hệ thống|
|6|info|Thông tin hệ thống|
|7|debug|Quá trình kiểm tra hệ thống|

## Định dạng chung của một gói tin Syslog
- Gồm ba phần PRI,header và MSG

- `PRI`:Phần PRI hay Priority là một số được đặt trong ngoặc nhọn, thể hiện cơ sở sinh ra log hoặc mức độ nghiêm trọng, là một số gồm 8 bit:
   + 3 bit đầu tiên thể hiện cho tính nghiêm trọng của thông báo.
   + 5 bit còn lại đại diện cho sơ sở sinh ra thông báo.
   
- `Header`.Gồm các phần chính sau:
   + Time stamp - Thời gian mà thông báo được tạo ra. Thời gian này được lấy từ thời gian hệ thống
   + Hostname hoặc IP
   
- `MSG`:Chứa một số thông tin về quá trình tạo ra thông điệp đó.MSG gồm hai phần:
   + Tag field:tên chương trình tạo ra thông báo.
   + Contend field:chứa các chi tiết của thông báo
   
## Rsyslog
- Rsyslog là gì:
  + Rsyslog dùng để chuyển tiếp các log message đến một địa chỉ trên mạng 
  + Nó thực hiện giao thức syslog cơ bản, đặc biệt là sử dụng TCP cho việc truyền tải log từ client tới server.
  + Hiện nay rsyslog là phần mềm được cài đặt sẵn trên hầu hết hệ thống Unix và các bản phân phối của Linux như : Fedora, openSUSE,    Debian, Ubuntu, Red Hat Enterprise Linux, FreeBSD…
  
## 3.Rotating log file:

  3.1: Vai trò roate
  
 - vai trò là quản lí log file trên hệ thống,bao gồm xoay vòng file log, di chuyển, nén, gửi tự động… 
 - Rotate (xoay vòng) ở đây có thể hiểu là tiến trình xử lý file log cũ theo quy định trước đó (xóa/nén/move) đồng thời tạo ra file log mới.
 - Khi một file log được roate,file log cũ thường được sao chép vào file log có ngày rotate trong đó
 - Theo mặc định, bốn tệp nhật ký cũ được lưu giữ trên hệ thống. Các tập tin cũ hơn thời gian đó sẽ tự động bị xóa khỏi hệ thống.
 - Các cài đặt mặc định của Roate được lưu ở tệp /etc/logrotate.conf 
 
 3.2: Cấu hình roate
 - Các cài đặt mặc định của Roate được lưu ở tệp /etc/logrotate.conf 
 - Thông tn cấu hình log file của từng ứng dụng cụ thể lưu tại `/etc/logrotate.d/` 
 
 3.2.1:Lựa chọn Log file được rotate
 - Bạn có thể chỉ định cụ thể một hay nhiều file log với đường dẫn tuyệt đối của file log đó, phân biệt danh sách các log file cụ thể bằng khoảng trắng. Ví dụ:
  + /home/*/logs/mysql*.log
  
3.2.2:Roate theo thời gian
- Có 4 giá trị cấu hình tương ứng với khoảng thời gian log file sẽ được rotate:
  +Daily: mỗi ngày
  +Weekly: mỗi đầu tuần
  +Monthly: mỗi đầu tháng
  +Yearly: mỗi năm

3.2.3:Roate theo dung lượng thời gian
- Cấu hình rotate dựa theo dung lượng file luôn được ưu tiên cao hơn rotate dựa vào thời gian. 
- Khi đó, nếu 1 file log được rotate theo cấu hình dung lượng file quy định thì thời gian rotate sẽ được khởi động lại mới.

3.2.4: Rotate theo số lượng Log file
- Quy định số lượng log file cũ đã được giữ lại sau khi rotate. \
 Ví dụ:Ví dụ: rotate7 giữ lại 7 file log cũ. Trường hợp đã có đủ 7 file log cũ thì file cũ nhất sẽ bị xóa đi để chứa file log mới được tạo
 
## journald
 - Là một daemon (chạy background trên hệ thống), một bộ phận của systemd, là một system service thực hiện việc thu thập và lưu trữ dữ liệu logging.
 - Mặc định log sẽ được chứa trong /run/log/journal/



  
## Answer the question:
 -1.which file is used to configure rsyslog? ( file nào dùng để cấu hình rsyslog): /etc/
 





