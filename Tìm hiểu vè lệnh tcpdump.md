# Tìm hiểu về lệnh tcpdump trên Linux
 
 ## Giới thiệu về tcpdump
 - Tcpdump là là công cụ được phát triển để phân tích gói dữ liệu mạng trên dòng lệnh.Nó cho phép người dùng chặn và hiển thị các gói tin được truyền đi hoặc nhận được trên mạng máy tính mà nó tham gia.
 
 ## Sử dụng tcpdump
 
 - Các tùy chọn thường sử dụng trong `tcpdump`
   + -c: chỉ số lượng gói cần bắt.
   + -i: bắt lưu lượng một giao diện cụ thể.
   + -t :cung cấp đầu ra dấu thời gian có thể đọc được.
   + -S :in số thứ tự tuyệt đối
   + -D:Hiển thị các giao diện mạng có sẵn.
   + -w:Ghi lại thông tin các gói tin bắt được
   
 - Một vài lệnh cơ bản:
 
 - a.xem các interface đang hoạt động `tcpdump -D`
   + ![]( /image/tcpdump-d.PNG)
 
 - b.bắt gói tin trên interface `tcpdump -i <interface>
   + ví dụ bắt 10 gói tin trên card ens33 `tcpdump -c 10 -i ens33`
   ![](/image/tcpdump-iens33.PNG)
   
 - c.chỉ bắt gói tin TCP `tcpdump -c 10 -i ens33 tcp`
   + ![](/image/tcpdump-tcp.PNG)
 - d.chỉ bắt gói tin ngoài tcp `tcpdump -c 10 -i ens33 not tco`
   + ![]( /image/tcpdump-nottcp.PNG)
 - e. bắt gói tin theo port `tcpdump -c 10 -i ens33 port`
   ![](/image/tcpdump-port.PNG)
 - f. bắt các gói arp qua card ens33 `tcpdump -c -10 -i ens33 arp`
   ![]( /image/tcpdump-arp.PNG)
   
# Tham khảo
[1] https://blogd.net/linux/vi-du-ve-su-dung-lenh-tcpdump/#7-b%E1%BA%AFt-c%C3%A1c-g%C3%B3i-v%C3%A0-ghi-v%C3%A0o-m%E1%BB%99t-t%E1%BB%87p

[2] https://www.tcpdump.org/manpages/tcpdump.1.html


