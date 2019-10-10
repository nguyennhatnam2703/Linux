
# Tìm hiểu về lịch sử hình thành,phát triển của Linux.

# Mục lục

- [1. Nguồn gốc ra đời](#1)

- [2. Quá trình phát triển](#2)

- [3. Các loại nhân hệ điều hành](#3)

- [3.1:Kernel là gì](#3.1)





<a name="1"><a>
# 1. Nguồn gốc của LINUX.

Linux ra đời năm 1991 được viết bởi Torvalds. Hệ điều hành MINIX chính là nguồn cảm hứng cho Torvalds viết LINUX.Nói về MINIX thì MINIX là hệ điều hành kiểu UNIX được thiết kế bởi giáo sư Andrew S.Tanenbaum với mục đích giáo dục.

Ban đầu Linux kernel được phát triển trên môi trường MINIX.Sau đó khi LINUX đã trưởng thành  thì việc phát triền Linux diễn ra ngay trên hệ thống Linux.Các ứng dụng GNU thay thế dần các thành phần của MINIX.

<a name="2"></a>
# 2.Quá trình phát triển

-  Tháng 4/1991,Linus Torvalds bắt tay vào việc viết những dòng lệnh đầu tiên của Linux.
- Tháng 8/1991,Torvalds gửi đi thông điệp về sự ra đời của Linux.
-  Tháng 9/1991,phiên bản Linux 0.01 ,phiên bản đầu tiên được Torvalds công bố
- Tháng 10,phiên bản Linux 0.02 được công bố
- Năm 1992, Torvalds phát hành Linux dưới dạng mã nguồn mở của giấy phép GPL cho phép tất cả mọi người có quyền dowload về để mã nguồn để cùng phát triển.
- Năm 1993,Slackware là hệ điều hành đầu tiên phát triển dựa trên mã nguồn Linux ra đời.
- Ngày 14/3/1994,ra mắt phiên bản Linux 1.0 với 176.250 dòng lệnh.
- Ngày 3/11/1994,Red hat Linux phiên bản 1.0 được ra mắt.Đây là một trong những hệ điều hành được thương mại hóa đầu tiên dựa trên Linux.
- Năm 1995,ra mắt phiên bản Linux 1.2 với 319.950 dòng lệnh.
- Năm 1996, hình ảnh chim cánh cụt được chọn để làm biểu tưởng chính thức của Linux.

![image](https://upload.wikimedia.org/wikipedia/commons/thumb/3/35/Tux.svg/800px-Tux.svg.png)

- Năm 1998, Linux bắt đầu được các tập đoàn công nghẹ quan tâm và đầu tư để phái triển như IBM,Orcale,Compaq.

-Năm 2004,phát hành hai phiên bản Ubuntu, Centos.

- Năm 2007,các hãng sản xuất máy tính như Hp,ASUS,Dell,..bắt đầu bán ra các sản phẩm laptop được cài đặt sẵn Linux.

- Hiệm nay Linux được sư dụng rộng rãi trên toàn thế giới,trên các máy tính các nhân,các máy chủ,thiết bị di động,....
<a name="3"></a>
# 3.Kernel

<a name="3.1"></a>
## 3.1.Kernel là gì? 

- Kernel là thành phần cốt lõi của một hệ điều hành.Sử dụng giao tiếp giữa quá trình và các call system, nó hoạt động như một cầu nối giữu các ứng dụng và xử lí dữ liệu được thực hiện ở cấp độ phần cứng. 
- Khi một hệ điều hành được tải vào bộ nhớ,kernel sẽ tải trước và lưu lại trong bộ nhớ cho đến khi hệ điều hành được tắt lại.Kernel chịu trách nhiệm cho các tác vụ cấp thấp như quản lí bộ nhớ,quản lí đĩa,quản lí tác vụ

<a name="3.2"></a>
## 3.2.Vai trò kernel 

- Nhân cung cấp và quản lí tài nguyên máy tính cho phép các chương trình khác chạy và sử dụng tài nguyên này.

- Nhân thiết lập không gian địa chỉ bộ nhớ cho các ứng dụng,tải các tệp có mã ứng dụng vào bộ nhớ

<a name="3.3"></a>
## 3.3.Cấu trúc và quy ước số hiệu phiên bản của nhân Linux

 Phiên bản nhân Linux bao gồm ba nhóm số được tạch bằng dấu chấm.Ví dụ:2.4.26
 
 - Số thứ nhât: 2 là số hiệu phiên bản chính
 - Số thứ hai: 4 là chỉ định cho tình trạng phiên bản. Nếu số này là số chẵn, nó chỉ định cho phiên bản ổn định (stable), có thể dùng      cho môi trường production. Nếu số này là số lẻ, nó chỉ định cho phiên bản không ổn định, nó thường dùng trong môi trường đang phát      triển (development). Các kernel thuộc dạng này thường có nhiều bugs và không ổn định. Nếu dùng các phiên bản này để tìm bugs và thông    báo cho nhóm phát triển Linux kernel thì đây là điều rất tốt. Không nên dùng phiên bản development cho môi trường production.
 
 - Số thứ ba: 26 là chỉ định cho số hiệu phát hành của một phiên bản Linux kernel. Một phiên bản ổn định của một Linux kernel có thể có    nhiều số hiệu phát hành khác nhau.
 <a name="4"></a>
 ## 4.Protection Rings
 
 <a name="4.1"></a>
 ## 4.1.Các khái niệm cơ bản:
 - Trong khoa học máy tính, Protection Rings là cơ chế nhằm bảo vệ dữ liệu và chức năng của một chương trình tránh khỏi nguy cơ lỗi hoặc bị truy cập trái phép bởi các chương trình khác.
 - Một Protection Ring là một mức độ (mode/level/layer) truy cập tài nguyên hệ thống. Số lượng Ring tùy thuộc vào kiến trúc CPU và hệ điều hành chạy trên kiến trúc đó có khả năng hỗ trợ bao nhiêu Ring.
 - Các Ring được sắp xếp có thứ bậc, từ mức có nhiều đặc quyền nhất  đến mức có ít đặc quyền nhất.
 
 ![](https://manthang.files.wordpress.com/2010/10/protection-rings.jpg)
 <a name="4.2"></a>
 ## 4.2. Kernel mode
 - Kernel mode là môt cơ chế hoạt động của CPU.
 - Nếu 1 chương trình hoạt động trong Kernel Mode thì nó sẽ có thể nắm quyền sử dụng mọi tài nguyên hệ thống như: sử dụng được tất cả     các chỉ lệnh CPU, truy cập tới mọi vùng nhớ trong RAM…
 
 <a name="4.3"></a>
 ## 4.3. User mode
 - User mode là một cơ chế hoạt động của CPU.
 - Các chương trình nằm trong User Mode thì ít có đặc quyền truy cập tới tài nguyên hệ thống như: số lượng các chỉ lệnh CPU được sử dụng    bị giới hạn, bị cấm truy cập tới vùng nhớ được cấp phát cho Kernel và các chương trình khác…
 - Tất cả các phần mềm ứng dụng lớp người dùng (thuộc untrusted software) khi mới được khởi chạy đều được đưa vào vùng User Mode.
 
 <a name="5"></a>
 ## 5.Linux distribution.
 
<a name="5.1"></a> 
 ## 5.1. Khái niệm
 
 - Linux distribution là một hệ điều hành được tạo bởi tâp hợp nhiều phần mềm dựa trên hạt nhân Linux và thường có một hệ thống quản lí gói tin
 - Linux distribution bao gồm bao gồm linux kernel , GNU tool and libraries , thêm một số software , documentation , window system ( phổ biến nhất là X Window System) , desktop environment .
 
 <a name="5.2"></a>
 ## 5.2. Các bản phân phôí phổ biến

<a name="5.2.1"></a>
 ## 5.2.1:Debian
 
 <a name="5.2.1.1"></a>
 ## a, Giới thiệu
 - Debian là một bản phân phối phi thương mại và là một trong những bản phân phối ra đời sớm nhất
 - Hiện tại các hệ thống Debian sử dụng nhân Linux hoặc nhân FreeBSD.
 - Là phần mềm tự do.
 - Có rất nhiều distribution dựa trên Debian như Ubuntu ,Astra-Linux ,Collax, Cumulus Linux ,Damn Small Linux ,Debian JP ,DoudouLinux . 
 <a name="5.2.1.2"></a>
 ## b, Hệ điều hành Ubuntu
 - Ubuntu là tên một hệ điều hành máy tính,được ra đời vào năm 2004.
 - Hệ điều hành Ubuntu phát triển dựa trên Debian GNU/Linux và được sản xuất bởi Canonical Ltd.
 
 
 
 
 
 
 
 
 
 


## Tài liệu

[1] https://wikihoidap.org/kernel-la-gi

[2] https://vi.wikipedia.org/wiki/Linux

[3] https://manthang.wordpress.com/2010/10/30/co-che-protection-rings-trong-bao-mat-may-tinh/

[4] https://vi.wikipedia.org/wiki/B%E1%BA%A3n_ph%C3%A2n_ph%E1%BB%91i_Linux
 
[5] https://www.debian.org/intro/about.vi.html
