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


