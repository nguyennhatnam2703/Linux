


# SSH là gì?
- SSH là chữ viết tắt của Secure Shell, tạm dịch là "môi trường an toàn" SSH được hiểu đơn giản là giao thức kết nối giữa máy chủ và máy khách được bảo mật một cách an toàn.
- SSH có sử dụng cơ chế mã hoá đủ mạnh nhằm ngăn chặn các hiện tượng nghe trộm , đánh cắp thông tin trên đường truyền . Các giao thức trước đây như rlogin , telnet không hỗ trợ mã hóa .
- SSH hoạt động ở tầng Application trong mô hình TCP/IP
- Các công cụ SSH phổ biến hiện nay: PuTTY, OpenSSH, Bitvise SSH,Xshell,..
- Cách hoạt động của SSH:
  +Định danh host - xác định định danh của hệ thống tham gia phiên làm việc SSH.
  +Mã hoá - thiết lập kênh làm việc mã hoá.
  +Chứng thực - xác thực người sử dụng có quyền đăng nhập hệ thống

# Thực hiện
- Bật server Ubuntu ở VM

- Mở Xshell lên và tiến hành điền thông tin máy chủ
 + Đặt tên cho máy chủ ảo
 
 + Điền địa chỉ IP máy chủ ảo
 
 + Chon Port number

- ![]( /image/ssh1_2.PNG )

  + Nhập User name và Pass máy chủ ảo

- ![]( /image/sshpass_2.PNG)

- Connect vào Ubuntu Server

- ![]( /image/sshubuntu.PNG)




