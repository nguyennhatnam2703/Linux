# Tìm hiểu về lệnh Netstat trong Linux để kiểm tra kết nối
 
 # 1.Giới thiệu
 
 - Lệnh netstat trên linux là một lệnh nằm trong số các tập lệnh để giám sát hệ thống trên linux.
 - netstat giám sát cả chiều in và chiều out kết nối vào server, hoặc các tuyến đường route, trạng thái của card mạng.
 - lệnh netstat rất hữu dụng trong việc giải quyết các vấn đề về sự cố liên quan đến network như là lượng connect kết nối, traffic, tốc     độ, trạng thái của từng port, Ip …
 
 # 2.Các lệnh nestart
 - Lệnh 1.Kiểm tra các cổng kết nối `netstart -a`
 ![]( /image/netstart -a.PNG)
 
 - Lệnh 2.Kiểm tra các cổng kết nối đang sử dụng TCP `netstart -at`
  ![]( /image/net-at.PNG)
  
  - Lệnh 3.Kiểm tra các cổng kết nối đang sử dung UDP `netstart -au`
   ![] (/image/net-au.PNG)
   
  - Lệnh 4:Kiểm tra các port đang ở trạng thái listening ` netstart -l`
   ![]( /image/net-l.PNG)
   
  - Lệnh 5:Kiểm tra các port đang listen sử dụng TCP `netstart -lt`
    ![]( /image/net-lt.PNG)
    
  - Lệnh 6:Kiểm tra các port đang listen sử dụng UDP `netstart -lu`
  
  - Lệnh 7:Kiểm tra các port đang lắng nghe sử dụng dịch vụ gì `netstart -pnlt`
    ![]( /image/net-pnlt.PNG)
    
  - Lệnh 8:Hiển thị bảng định tuyến `netstart -rn`
    ![]( /image/net-rn.PNG)
  
  - Lệnh 9:Hiển thị thông tin IP: `netstart -ie`
    ![]( /image/net-ie.PNG)
    
  - Lệnh 10:Hiển thị tên Serviec và PID `netstart -tp`
     ![]( /image/net-tp.PNG)
  
