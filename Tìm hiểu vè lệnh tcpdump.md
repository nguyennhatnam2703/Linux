# Tìm hiểu về lệnh tcpdump trên Linux
 
 ## Tcpdump là gì?
 - Tcpdump là phần mềm bắt gói tin trong mạng làm việc hầu hết trên các phiên bản hệ điều hành unix/linux.Tcpdump cho phép bắt và lưu lại những gói tin bắt được,từ đó chúng ta có thể sử dụng để phân tích
 
 ## Tcpdump tồn tạo dưới hình thức nào?
 - TCPDUMP xuất ra màn hình nội dung các gói tin (chạy trên card mạng mà máy chủ đang lắng nghe) phù hợp với biểu thức logic chọn lọc mà khách hàng nhập vào.
 - Với từng loại tùy chọn khác nhau khách hàng có thể xuất những mô tả về gói tin này ra một file “pcap” để phân tích sau, và có thể đọc nội dung của file “pcap” đó với option –r của lệnh tcpdump
 - Trong trường hợp không có tùy chọn, lệnh tcpdump sẽ tiếp tục chạy cho đến khi nào nó nhận được một tín hiệu ngắt từ phía khách hàng
 - Sau khi kết thúc việc bắt các gói tin, tcpdump sẽ báo cáo các cột sau:
  + Packet capture: số lượng gói tin bắt được và xử lý.
  + Packet received by filter: số lượng gói tin được nhận bởi bộ lọc.
  + Packet dropped by kernel: số lượng packet đã bị dropped bởi cơ chế bắt gói tin của hệ điều hành.
  
  ## Một số vai trò của Tcpdump
  - Nhìn thấy được các bản tin DUMP trên terminal
  - Bắt các bản tin và lưu vào định dạng PCAP (có thể đọc được bởi Wireshark)
  - Tạo được các bộ lọc Filter để bắt các bản tin cần thiết, ví dụ: http, ftp, ssh, …
  - Có thể nhìn được trực tiếp các bản tin điều khiển hệ thống Linux
  -...
  
  ## Định dang chung của một dòng tcpdump
  
  - `time-stamp src > dst: flags data-seqno ack window urgent options`
  - Time-stamp: hiển thị thời gian gói tin được capture.
  - Src và dst: hiển thị địa IP của người gởi và người nhận.
  - Cờ Flag thì bao gồm các giá trị sau:
    + S(SYN): Được sử dụng trong quá trình bắt tay của giao thức TCP.
    + .(ACK): Được sử dụng để thông báo cho bên gửi biết là gói tin đã nhận được dữ liệu thành công.
    + F(FIN): Được sử dụng để đóng kết nối TCP.
    + P(PUSH): Thường được đặt ở cuối để đánh dấu việc truyền dữ liệu.
    + R(RST): Được sử dụng khi muốn thiết lập lại đường truyền.
  
  - Data-sqeno: Số sequence number của gói dữ liệu hiện tại.
  - ACK: Mô tả số sequence number tiếp theo của gói tin do bên gởi truyền
  - Window: Vùng nhớ đệm có sẵn theo hướng khác trên kết nối này.
  - Urgent: Cho biết có dữ liệu khẩn cấp trong gói tin
 
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
   + ![]( /image/tcmdump-d.PNG)
 
 - b.bắt gói tin trên interface `tcpdump -i <interface>
   + ví dụ bắt 10 gói tin trên card ens33 `tcpdump -c 10 -i ens33`
   + ![](/image/tcpmdump-iens33.PNG)
   
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


