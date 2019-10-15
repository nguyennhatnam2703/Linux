# Tìm hiểu về systemd để quản lý service trong linux
 
 # Mục lục 
 
  - [1. Khái niệm](#1) 
 
  - [2. Vai trò của System trong hệ thống](#2)
 
  - [3.Tạo service với hệ thống](#3)
  
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
    
    + `

  
  
  
  
 
 
