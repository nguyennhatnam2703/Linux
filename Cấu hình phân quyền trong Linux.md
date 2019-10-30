# Cấu hình phân quyền trong Linux
 
 - Tại sao phải phân quyền trong Linux ?
   + Phân quyền truy xuất đến các tài nguyên Server Linux là một vấn đề quan trọng. Phân quyền giúp tăng mức độ an toàn, đảm bảo đúng trách nhiệm – quyền hạn của từng user khi sử dụng tài nguyên trên Server
 
 # 1. Quyền truy xuất
 - Quyền truy xuất trên thư mục và tập tin được trình bày khi thực hiện lệnh `ls -l`
 
   ![]( /image/ls-l.PNG)
   + Cột thứ nhất là quyền áp dụng đối với thư mục, ký tự d chỉ đây là thư mục.
   + Cột thứ 2 là các số nguyên chỉ liên kết tới thư mục.
   + Cột thứ 3,4 là chủ sở hữu và nhóm sở hữu thư mục
   + Cột 5 chỉ dung lượng của thư mục (byte).
   + Cột 6,7,8 chỉ thời gian tạo.
   + Cột 9 chỉ tên thư mục.
 - Các loại quyền truy xuất:  
   + Read(r) :Đối với một file thì Read chính là quyền xem nội dung file đó còn đối với một folder thì Read chính là quyền xem các file      trong folder đó.
   + Write(w):Đối với một file thì Write cho phép thêm,sửa nội dung file còn đối với một folder thì Write cho phép thêm xóa một subfolder hay một file trong folder đó.
   + Execute(e):Cho phép thực thi chương trình,đối với thư mục thì Execute cho phép chuyển vào thư mục bằng lệnh cd
   + Deny (-): không có quyền làm một thao tác gì trên file hay thư mục
 - Kiểu file:
 
   |Ký tự| Ý nghĩa|
   |-----|--------|
   |-|Tập tin thông thường|
   |b|Tập tin đặc biệt block|
   |c|Tập tin ký tự đặc biệt|
   |d|Thư mục|
   |l|Tập tin liên kết|
   
- Quyền truy xuất gồm ba nhóm:
  + Quyền của người sở hữu(u): Là người tạo ra thư mục/file hoặc người được gán quyền sở hữu
  + Quyền của nhóm sở hữu (g): Là nhóm người sử dụng được gán quyền
  + Quyền của người dùng khác: Là những người không thuộc hai nhóm trên

# 2.Biểu diễn quyền truy xuất

## 2.1: Bằng chữ:

- Trong cách biểu diễn này,các quyền được biểu diễn bằng ký tự
  + r:read
  + w: write
  + e:thực thi
  + -:không có quyền
  + rwx: có toàn quyền
  + rw-: chỉ có quyền đọc và ghi
  + r--: chỉ có quyền đọc
  + ---: không có quyền gì
- Quyền hạn trên một file sẽ gồm cả ba nhóm quyền nên danh sách sẽ gồm 9 ký tự.Ví dụ
  + rwxrw---- :Người sở hữu có toàn quyền,các user cùng nhóm có quyền đọc và ghi,các user khác không có quyền gì.
  + rw-r-----:Người sở hữu có quyền đọc và ghi,các user cùng nhóm có quyền đọc,các user khác không có quyền gì.
  + rwx-w-r--:Người sở hữu có toàn quyền,các user cùng nhóm có quyền ghi,các user khác có quyền đọc.

## 2.2 Bằng số:

- Trong cách biểu diễn này,các quyền được biểu diễn bằng số
   
  | Số | Quyền |
  |----|-------|
  |4|Đọc
  |2|Ghi|
  |1|Thực thi|
  |0|Không có quyền|
