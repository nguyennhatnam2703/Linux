# Tìm hiểu về systemd để quản lý service trong linux
 
 # Mục lục 
 
  - [1. Khái niệm](#1) 
 
  - [2. Vai trò của System trong hệ thống](#2)
 
 
  
  # 1.Khái niệm
  
  - Systemd là 1 công cụ (System Tool) của Linux được phát triển bởi nhóm Red Hat.
  
  - Nó bao gồm nhiều tính năng, bao gồm một hệ thống bootstrapping được sử dụng để khởi động và quản lý các tiến trình (processes) trong     hệ  thống. 
  
  - Nó hiện là hệ thống khởi tạo mặc định trên hầu hết các bản phân phối Linux. 
  
  - Một số dịch vụ (services) phổ biến như SSH, Apache đều đang sử dụng systemd để khởi động và quản lý dịch vụ.
  
  # 2.Vai trò của Systemd trong hệ thống
  
  ## 2.1:Khởi tạo hệ thống
  
  - Systemd cung cấp một chương trình đặc biệt là /sbin/init và nó sẽ là chương trình đầu tiên được khởi động trong hệ thống (PID = 1)
  
  - Khi hoạt động, /sbin/init sẽ giữ vai trò kích hoạt các file cấu hình cần thiết cho hệ thống, và các chương trình này sẽ tiếp nối để hoàn tất công đoạn khởi tạo.
  
  ## 2.2:Các thành phần của Systemd
  
  - Về cơ bản thì systemd tương đương với một chương trình quản lý hệ thống và các dịch vụ trong Linux. Nó cung cấp một số các tiện ích như sau:
    + `systemctl` dùng để quản lý trạng thái của các dịch vụ hệ thống (bắt đầu, kết thúc, khởi động lại hoặc kiểm tra trạng thái hiện tại)
    
    + `journald` dùng để quản lý nhật ký hoạt động của hệ thống (hay còn gọi là ghi log)
    
    + `logind` dùng để quản lý và theo dõi việc đăng nhập/đăng xuất của người dùng
    
    + `networkd` dùng để quản lý các kết nối mạng thông qua các cấu hình mạng
    
    + `timedated` dùng để quản lý thời gian hệ thống hoặc thời gian mạng
    
    + `udev` dùng để quản lý các thiết bị và firmware
    
 ## 2.3.Unit file
 - Tất cả các chương trình được quản lý bởi systemd đều được thực thi dưới dạng daemon hay background bên dưới nền và được cấu hình thành 1 file configuration gọi là unit file. 
 - Các unit file này sẽ bao gồm 12 loại:`
   + service (các file quản lý hoạt động của 1 số chương trình)
   
   + socket (quản lý các kết nối)
   
   + device (quản lý thiết bị)
   
   + mount (gắn thiết bị)
   
   + automount (tự đống gắn thiết bị)
   
   + swap (vùng không gian bộ nhớ trên đĩa cứng)
   
   + target (quản lý tạo liên kết)
   
   + path (quản lý các đường dẫn)
   
   + timer (dùng cho cron-job để lập lịch)
   
   + snapshot (sao lưu)
   
   + slice (dùng cho quản lý tiến trình)
   
   + scope (quy định không gian hoạt động)
   
  ## 2.4:Service 
  - Service sẽ được khởi động khi bật máy và luôn chạy ở chế độ nền (daemon hoặc background)
  
  - Các service thường sẽ được cấu hình trong các file riêng biệt và được quản lý thông qua câu lệnh systemctl.
  
  - Ta có thể sử dụng câu lệnh sau để xem các service đã được kích hoạt bởi hệ thống: systemctl list-units | grep -e '.service' hoặc      systemctl -t service
  
  - Bộ ba tùy chọn quen thuộc của systemctl sẽ dùng khi muốn bật/tắt một service:
  
    + `start`: bật service
    
    + `stop`: tắt service
    
    + `restart`: tắt service rồi bật lại
    
    +  Ba tùy chọn trên sẽ được sử dụng khi hệ thống đang hoạt động, tuy nhiên systemctl cũng cung cấp 2 tùy chọn khác để điều khiển           việc hoạt động của service từ lúc khởi động hệ thống
    
    + `enable`: service sẽ được khởi động cùng hệ thống
    
    + `disable`: service sẽ không được khởi động cùng hệ thống
    
    # Tham khao
    - [1] https://viblo.asia/p/tim-hieu-va-van-dung-systemd-de-quan-ly-he-thong-linux-phan-co-ban-WAyK8kN65xX#_service-6
   
   

  
  
  
  
 
 
