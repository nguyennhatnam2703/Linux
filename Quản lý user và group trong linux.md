# Quản lý User và Group trong Linux
 
 # 1.Quản lý User
 
 ## 1.1 Giới thiệu
 
 - User là gì ?
   + User là một thuật ngữ chuyên dụng được sử dụng trong ngành công nghệ thông tin. User được dùng để thể hiện tài khoản của người dùng trong máy tính. User giúp bạn bảo mật thông tin máy tính của bạn. User được sử dụng để login, gán quyền,... 
 - có hai loại User:
   + `User hệ thống`: dùng để thực thi các module, script cần thiết phục vụ cho HĐH. 
   + `User người dùng`: là những tài khoản để login để sử dụng HĐH. 
 - `User root` :
   + là tài khoản quan trọng nhất.Nó được tạo khi cài đặt Linux
   + tài khoản này không thể xóa đi hoặc đôi tên
   + chỉ nên thực hiện tài khoản User root khi thực hiện việc quản trị hệ thống.
 - Các đặc điểm của User:
   + Tên mỗi user là duy nhất, chỉ có thể đặt tên chữ thường, chữ hoa. 
   + Mỗi user có một mã định danh duy nhất (uid). 
   + Mỗi user có thể thuộc về nhiều nhóm. 
   + Tài khoản superuser có uid = gid = 0. 
   
 ## 1.2:file /etc/passwd
 - là file văn bản chứa các thông tin các tài khoản User trên máy.Các user có thể đọc tập tin này nhưng chỉ có `User root` có quyền thay đổi.
 - dùng lệnh `cat /etc/passwd` để xem nội dung file:
   + ![]( /image/etc.passwd1.PNG)
   + ![]( /image/etc.passwd2/PNG)
   + Cột thứ nhất là tên người dùng:giaovien1,giaovien2,sinhvien1,....
   + Cột thứ hai chỉ ra mật khẩu đã được mã hóa và lưu ở tập tin shadown
   + Cột thứ 3  User ID là định định danh duy nhất của người dùng
   + Cột thứ 4 Group ID là định danh nhóm người dùng chỉ rõ người dùng thuộc nhóm nào.
   + Cột thứ 5 thư mục home của người dùng
   + Cột thứ 6 đường dẫn của dòng lệnh
   
 ## 1.3:file /etc/shadow
 - là file văn bản chứa các thông tin mật khẩu của các user trên máy.Chỉ có root mới có quyền đọc tập tin này.User root có quyền reset mật khẩu bất cứ user nào trên  máy.
 - sử dụng `cat /etc/shadown` :
   + ![]( /image/shadown1.PNG)
   + ![]( /image/shadown2/PNG)
   + cột thứ 1 tên người sử dụng.
