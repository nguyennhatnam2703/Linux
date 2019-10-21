# Mục lục

+ [1. Mục đích ](#1)
+ [2. Crontab là gì?](#2)
+ [3. Cơ chế làm việc và cách sử dụng Crontab](#3)
+ [4. Cài đặt Crontab](#4)
+ [5. Cấu trúc của Crontab ](#5)
+ [6. Một số ví dụ về crontab](#6)

<a name = '1'></a>

# 1.Mục đích 
 
 - Tất cả những tác vụ cần thực hiện tự động vào một thời điểm nào đó thì đều có thể làm tự động. Linux có một cơ chế lập lịch để thực hiện các tác vụ tự động gọi là Cron.
 - Khái niệm cron trong Linux cũng tương tự như Alarm trong Android, hay Task Schedule trên Window vậy.
 - Một số ứng dụng của Crontab:
   + Lập lịch sao lưu cơ sở dữ liệu tự động
   + bật/tắt các phần mềm nào đó cụ thể để tiết kiệm bộ nhớ
   + Gửi email thống kê cho khách hàng mỗi tuần

<a name = '2'></a>

 # 2.Crontab là gì?
 - Cron là cách để tạo và thực hiện các tác vụ theo một lịch trình định kì ở chế độ nền.Cron là một chương trình deamon, tức là nó được chạy ngầm mãi mãi một khi nó được khởi động lên. 
 - Cronjob là các lệnh thực thi hành động đặt trước vào thời điểm nhất định. Crontab là nơi lưu trữ các cronjob

<a name = '3'></a>

 # 3.Cơ chế làm việc và cách sử dụng Crontab 
 
 - Một crontab là một tệp văn bản đơn giản chứa danh sách các lệnh có nghĩa và được chạy tại các thời điểm được chỉ định. Nó được chỉnh sửa bằng lệnh crontab.
 - Các lệnh trong file crontab được kiểm tra bởi trình cron daemon và thực thi chúng trong nền hệ thống.
 - Để đảm bảo hệ thống kiểm soát tốt lịch trình thì file crontab không thể được chỉnh sửa bởi bất kỳ ứng dụng file editor nào.Chỉ duy nhất nhất lệnh crontab là có thể sửa nó
 - Một số lệnh thường dùng:
   + `crontab -e`: tạo hoặc chỉnh sửa file crontab
   + `crontab -l`: hiển thị file crontab 
   + `crontab -r`: xóa file crontab
   + `cd /etc/cron.d` : Nếu crobtab được register bằng system cron
 - Mỗi người dùng (bao gồm cả root) đều có một tệp crontab.
 - Cron daemon kiểm tra tệp crontab của người dùng bất kể người dùng có thực sự đăng nhập vào hệ thống hay không.
 
 <a name = '4'></a>
 
 # 4.Cài đặt Crontab
 
 - Trên Ubuntu/Debian:
   `sudo apt-get install cron`
   
 - Trên CentOS/Red Hat Linux:
   `yum install cronie`  
   
 - Kiểm tra cài đặt:
   + ![]( /image/cdcrontab.PNG)
  
  <a name = '5'></a>
  
  # 5.Cấu trúc của Crontab 
  
  - Một lệnh crobtab thường gồm 3 phần:
    + Trường thời gian: gồm 5 chỉ số thời gian để xác định một lịch trình.
    + Trường user-name: Xác định tài khoản nào được phép chạy crontab này. Nếu không chỉ định sẽ sử dụng user mặc định đã register           crontab.
    + Tác vụ cần thực thi: tác vụ này có thể là một lệnh hoặc nhiều lệnh. Nếu có nhiều lệnh sẽ cách nhau bởi dấu chấm phẩy.
    + ![]( /image/timecrontab.png)
    
    + Nếu tất cả đều là dấu * thì mỗi phút command sẽ được thực hiện 1 lần
    + Bất kì trường thời gian nào nếu bạn để là * thì có nghĩa trường đó sẽ chạy every ~(Every minute, every day …)
    
    <a name = '6'></a>
    
  # 6.Một số ví dụ về crontab
    - 5 0 * * * /root/backup.sh: có nghĩa là đoạn script:/root/bachup.sh sẽ được thực thi vào 0h 5 phút hằng ngày
    - 1 2 3 * *  :đoạn cript sẽ được thực thi vào 2h 1 phút của ngày 3 hàng tháng
    - 4 5 6 7 *: đoanh sript sẽ được thực thi vào lúc 5 giờ 4 phút ngày 6 tháng 7 hằng năm
