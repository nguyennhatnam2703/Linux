# Cấu trúc thư mục trong Linux
 
 # Mục lục
 
 # 1.Hệ thống file trong Linux
  
 - Trong hệ thống Linux, tất cả đều được cấu hình và coi như là file. Không chỉ bao gồm file text, ảnh, các chương trình biên dịch mà còn   cả các thư mục, phân vùng và drive thiết bị phần cứng đều được hệ thống nhìn nhận như một file. 
 
 - Tất cả các file và thư mục đều xuất hiện trong thư mục root, kể cả khi các thư mục còn lại được lưu trong các thiết bị vật lý khác nhau    (trên ổ cứng khác, hoặc trên ổ cứng của máy tính khác)
 
 
 
 # 2.Cấu trúc thư mục trong Linux
 
 - Cấu trúc cơ bản của:
 
 ![](https://camo.githubusercontent.com/bd567bd1fe568d2ab5c1e3f059a85a8d8f484dd7/687474703a2f2f696d6775722e636f6d2f6b647135594f4a2e6a7067)
 
- **2.1: / - Root**
  -  Là thư mục root.Đúng với tên gọi của mình: nút gốc (root) đây là nơi bắt đầu của tất cả các file và thư mục. Chỉ có root user mới có quyền ghi trong thư  mục này.
  
 - **2.2: /bin - Chương trình của người dùng** 
   + Thư mục này chứa các chương trình thực thi. Các chương trình chung của Linux được sử dụng bởi tất cả người dùng được lưu ở đây. Ví dụ như: ps, ls, ping...
 
 - **2.3: /boot - Các file khởi động**
   + Trong thư mục bao gồm tất cả các file cần thiết để khởi động hệ thống được lưu tại đây.Ví dụ: các tệp của trình tải khởi động GRUB và các nhân Linux của bạn được lưu trữ ở đây. 
 - **2.4: /dev - Các file thiết bị**
   + Các phân vùng ổ cứng, thiết bị ngoại vi như USB, ổ đĩa cắm ngoài, hay bất cứ thiết bị nào gắn kèm vào hệ thống đều được lưu ở đây.
 
 - **2.5: /etc - Các file cấu hình**
   +  Thư mục này chứa các file cấu hình của các chương trình, đồng thời nó còn chứa các shell script dùng để khởi động hoặc tắt các chương trình khác
   
 - **2.6: /home - Thư mục người của dùng**
   +   Thư mục này chứa tất cả các file cá nhân của từng người dùng. Ví dụ: /home/john, /home/marie
     
 - **2.7: /lib - Thư viện hệ thống**
   +   Chứa thư viện chia sẻ được dùng bởi các tiến trình, các lệnh boot, lệnh hệ thống như trong /bin và /sbin. 
 
 - **2.8: /Media**
    + Thư mục tạm này chứa các thiết bị như CdRom /media/cdrom. floppy /media/floopy hay các phân vùng đĩa cứng /media/Data (hiểu như là ổ D:/Data trong Windows)
   
 - **2.9: /opt - Các ứng dụng phụ tùy chọn**
   +  Thư mục /opt chứa các ứng dụng thêm vào từ các nhà cung cấp độc lập khác. Các ứng dụng này có thể được cài ở /opt hoặc một thư mục con của /opt

- **2.10: /proc - Thông tin về các tiến trình**
  +  Thư mục proc lưu các thông tin về quá trình xử lí của hệ thống.Ví dụ như: /proc/cpuinfo cung cấp cho ta thông số kỹ thuật của CPU.

- **2.11: /root**
  +  Là thư mục dành riêng cho người dùng quản trị hệ thống.

- **2.12:/sbin - Chương trình hệ thống**
   + Cũng giống như /bin, /sbinn cũng chứa các chương trình thực thi, nhưng chúng là những chương trình của admin, dành cho việc bảo trì hệ thống. Ví dụ như: reboot, fdisk, iptables...
  
- **2.13: /srv - Dữ liệu dịch vụ** 
  + Thư mục chứa các dữ liệu liên quan đến các dịch vụ chạy trên hệ thống như ssh, mysql, mongose ...
  
- **2.14: /tmp - Tệp tạm thời**
   + Lưu lại các tập tin được tạo ra tạm thời bởi người dùng. Nó sẽ được xóa đi khi hệ thống được khởi động lại.

- **2.15: /usr - Chương trình của người dùng**
  + Chứa các tập tin của những ứng dụng chính được cài đặt cho mọi người dùng. Chứa các thư viện, file thực thi, tài liệu hướng dẫn và mã nguồn cho chương trình chạy ở level 2 (write) ở hệ thống.Trong đó:
 - - usr/bin chứa các file thực thi của người dùng.
 - - /usr/sbin chứa các file thực thi của hệ thống.
 - - /usr/lib chứa các thư viện cho các chương trình trong /usr/bin và /usr/sbin.

 ![](https://www.howtogeek.com/wp-content/uploads/2012/06/image358.png)

  
 
- **2.16: /var - File về biến của chương trình**
  +   Thông tin về các biến của hệ thống được lưu trong thư mục này. Như thông tin về log file: /var/log, các gói và cơ sở dữ liệu       /var/lib...
  
- **2.17: /lib64**
  + Tương như như lib nhưng dành cho 64bit
  
- **2.18: /etc**
  + Chứa file cấu hình hệ thống và ứng dụng. 

 
 # Mục lục
 [1] https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/
 
 [2]https://quantrimang.com/cau-truc-cay-thu-muc-trong-linux-84056
