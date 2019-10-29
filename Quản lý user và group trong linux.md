# Mục lục.
 
 - [ 1.Quản lý user ](#1)
 
 - [1.1 Giới thiệu ](#1.1)
 
 - [1.2 file /etc/passwd](#1.2)
 
 - [1.3 fule /etc/shadown](#1.3)
 
 - [ 2.Quản trị group](#2)
 
 - [ 2.1.Lệnh Groupadd](#2.1)
 
 - [2.2.Lệnh Groupmod](#2.2)
 
 - [2.3.Lệnh Groupdel](#2.3)
 
 
 
 
 # Quản lý User và Group trong Linux
 
 <a name="1"><a>
 # 1.Quản lý User
 
 <a name="1.1"><a>
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
  
 <a name="1.2"><a> 
 ## 1.2:file /etc/passwd
 - là file văn bản chứa các thông tin các tài khoản User trên máy.Các user có thể đọc tập tin này nhưng chỉ có `User root` có quyền thay đổi.
 - dùng lệnh `cat /etc/passwd` để xem nội dung file:
   + ![]( /image/etc.passwd1.PNG)
   
   + ![]( /image/etc.passwd2.PNG)
   + Cột thứ nhất là tên người dùng:giaovien1,giaovien2,sinhvien1,....
   + Cột thứ hai chỉ ra mật khẩu đã được mã hóa và lưu ở tập tin shadown
   + Cột thứ 3  User ID là định định danh duy nhất của người dùng
   + Cột thứ 4 Group ID là định danh nhóm người dùng chỉ rõ người dùng thuộc nhóm nào.
   + Cột thứ 5 thư mục home của người dùng
   + Cột thứ 6 đường dẫn của dòng lệnh

<a name="1.3"><a>
 ## 1.3:file /etc/shadow
 - là file văn bản chứa các thông tin mật khẩu của các user trên máy.Chỉ có root mới có quyền đọc tập tin này.User root có quyền reset mật khẩu bất cứ user nào trên  máy.
 - sử dụng `cat /etc/shadown` :
   + ![]( /image/shadown1.PNG)
   
   + ![]( /image/shadown2.PNG)
   + cột thứ 1 tên người sử dụng.
   + Cột thứ 2:Mật khẩu đã được mã hóa. Để trống – không có mật khẩu, Dấu “*” – tài khoản bị tạm ngưng (disable). 
   + Cột thứ 3:Số ngày kể từ lần cuối thay đổi mật khẩu 
   + Cột thứ 4:Số ngày trước khi có thể thay đổi mật khẩu, giá trị 0 có nghĩa có thể thay đổi bất kỳ lúc nào. 
   + Cột thứ 5:Số ngày mật khẩu có giá trị. 99999 có ý nghĩa mật khẩu có giá trị vô thời hạn
   + Cột thứ 6:Số ngày cảnh báo user trước khi mật khẩu hết hạn 
   + Cột thứ 7:Số ngày sau khi mật khẩu hết hạn tài khoản sẽ bị xóa. Thường có giá trị 7 (một tuần). 
   + Cột thứ 8:Số ngày kể từ khi tài khoản bị khóa 
   
  <a name="1.4"><a> 
 ## 1.4 Các lệnh quản lý user
 - a,Lệnh Useradd:Tạo tài khoản 
 - `useradd [options] login_name`
 - options:
   + -c: comment, tạo bí danh. 
   + -u: set user ID. Mặc định sẽ lấy số ID tiếp theo để gán cho user.   
   + -d: chỉ định thư mục home. 
   + -g: chỉ định nhóm chính. 
   + -G: chỉ định nhóm phụ (nhóm mở rộng). 
   + -s: chỉ định shell cho user sử dụng.
   + Ví dụ: tạo user sinhvien1 thuộc group sinhvien
   + `useradđ sinhvien1 -g sinhvien`
    ![]( /image/useradd.PNG)  
 - b,Lệnh usermod: Sửa thông tin tài khoản 
 - `usermod [options] login_name`
   - options:
    + -c: comment, tạo bí danh. 
    +  -l -d: thay đổi thư mục home. 
    + -g: chỉ định nhóm chính.
    + -G: chỉ định nhóm phụ (nhóm mở rộng). 
    + -s: chỉ định shell cho user sử dụng.
    + -L: Lock account  
 - c,Lệnh userdel: Xóa tài khoản user 
 -   `userdel [option] login_name`
    + option: -r: xóa thư mục home của user 
     + Ví dụ: xóa user sinhvien 3: `userdel sinhvien3`  
 - d,Lệnh chage: Dùng để thiết lập các chính sách (policy) cho user. 
 -   `chage [options] login_name`
 -  option:
    + -l : xem chính sách của 1 user
    + -E: thiết lập ngày hết hạn cho account. Vd: chage -E 6/30/2014 a1
    + - I: thiết lập số ngày bị khóa sau khi hết hạn mật khẩu 
    + -m: thiết lập số ngày tối thiểu được phép thay đổi password
    + -M: thiết lập số ngày tối đa được phép thay đổi password
    + -W: Thiết lập số ngày cảnh báo trước khi hết hạn mật khẩu. 
    + ví dụ: ` chage -E 10-10-2030 -I 15 -m 3 -M 90 -W 10 giaovien1 `
    + Lệnh trên sẽ thiết lập user giaovien1 có ngày hết hạn là 10-10-2030 user sẽ bị khóa 15 ngày sau khi hết hạn mật khẩu.User giaovien      1 có tối thiểu 3 ngày được phép thay đổi mật khẩu và có tối đa 90 được phép thay mật khẩu,hệ thống sẽ báo 10 ngày trước khi hết hạn      mật khẩu.

<a name="2"><a>
  # 2. Quản trị Group
  - Nhóm là tập hợp của nhiều user. Mỗi nhóm có tên duy nhất, và có một mã định danh duy nhất (gid). Khi tạo một user (không dùng option   -g) thì mặc định một group được tạo ra. 
<a name="2.1"><a>
  ## 2.1:Lệnh groupadd
  - Lệnh tạo nhóm `groupadd [options] tên_group`
  - options: -g Định nghĩa nhóm với mã nhóm GID
  - vd: Tạo nhóm sv1: `groupadd sv1`
 
 <a name="2.2"><a>
  ## 2.2: Lệnh groupmod-Sửa thông tin nhóm
  - Lệnh sửa `groupmod [options] group`
  - options: 
    + -g sửa mã nhóm thành GID
    + -n group_name sửa tên group
  - ví dụ: sửa tên group sv1 thành svien1 `groupmod -n svien1 sv1 `
 
 <a name="2.3"><a>
  ## 2.3: Lệnh groupdel- xóa group
  - Cấu trúc lệnh: `groupdel [option] group
  - ví dụ: xóa group hoctap `groupdel hoctap`
  
  # Mục lục
  [1] Giáo trình quản trị hệ thống Linux LPI 1 của Newstar.
  [2] https://support.maxserver.com/767313--H%C6%B0%E1%BB%9Bng-d%E1%BA%ABn-qu%E1%BA%A3n-l%C3%BD-User-v%C3%A0-Group-tr%C3%AAn-Linux
    
    
  
 
