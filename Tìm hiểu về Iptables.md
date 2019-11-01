# Tìm hiểu về Iptables
 
 # 1.Giới thiệu về Iptables
 - Mục đích ra đời: 
   + Sử dụng tường lửa (firewall) là điều hầu như bắt buộc phải làm khi bạn sử dụng máy chủ để chống lại các tấn công bất hợp pháp bằng cách tự thiết lập các quy tắc chặn truy cập cửa riêng mình.
   + Trong các bản phân phối của Linux như Centos,Ubuntu,... đều có tích hợp công cụ tường lửa Iptables.
 - Iptables do Netfilter Organiztion viết ra để tăng tính bảo mật trên Linux
 - Iptables có các tính năng như :
   + Tích hợp tốt với kernel của Linux
   + Có khả năng phân tích packet hiệu quả.
   + Lọc packet dựa vào địa chỉ MAC và một số cờ hiệu trong TCP Header.
   + Cung cấp chi tiết các tùy chọn để ghi nhận sự kiện vào hệ thống.
   + Cung cấp kỹ thuật NAT
   + Có khả năng ngăn chặn một số cơ chế tấn công theo kiểu DOS.
 - Iptables có thể đọc,thay đổi,chuyển hướng hoặc hủy các gói tin đi tới dựa trên các tables,chain,rules.
 - Mỗi table sẽ có  nhiều chain trong chain chứa nhiều rules khác nhau quyết định cách thức xử lí gói tin ( dựa trên giao thúc,địa chỉ ip nguồn,ip đích,...)
 - Có nhiều phiên bản Iptables khác nhau cho các giao thức khác nhau như: iptables(ipv4), ip6tables(ipv6),arptable(ARP),ebtables (Ethernet frame)
 
 # 2.Sử dụng Iptables
  
 ## 2.1: Các bảng trong Iptables
 *Iptables gồm có năm bảng với mục đích xử lí và các thứ tự khác nhau.*
 - `Filter table`:table này nhằm quyết định liệu gói tin có được chuyển đến địa chỉ đích hay không.Filter tables có ba nguyên tắc cơ bản để thiết lập các nguyên tắc lọc gói:
   + FOWARD CHAIN:  lọc gói khi đến các server khác
   + Input chain: lọc gói tin khi đến server
   + Output chain:lọc gói khi ra khỏi server
 
 - `NAT tables` :gồn hai loại
   + Pre-routing chain: thay đổi địa chỉ đến của gói dữ liệu khi cần thiết.
   + Post-routing chain: thay đổi địa chỉ nguồn của gói dữ liệu khi cần thiết.
   
 - `Mangle Table`:
   + Bảng mangle dùng để điều chỉnh một số trường trong IP header như TTL (Time to Live), TOS (Type of Serivce) dùng để quản lý chât lượng dịch vụ (Quality of Serivce)… hoặc dùng để đánh dấu các gói tin để xử lý thêm trong các bảng khác.
   
 - `Raw Table`:
   + iptables sẽ lưu lại trạng thái kết nối của các gói tin, tính năng này cho phép iptables xem các gói tin rời rạc là một kết nối, một session chung để dễ dàng quản lý. 
   + Với raw table ta có thể bật/tắt tính năng theo dõi này đối với một số gói tin nhất định, các gói tin được đánh dấu NOTRACK sẽ không được ghi lại trong bảng connection tracking nữa.
   
 - `Security table`:
   + Bảng security dùng để đánh dấu policy của SELinux lên các gói tin, các dấu này sẽ ảnh hưởng đến cách thức xử lý của SELinux hoặc của các máy khác trong hệ thống có áp dụng SELinux. 
   + Bảng này có thể đánh dấu theo từng gói tin hoặc theo từng kết nối.
   
- ## 2.2:Các chain trong tables
- Giới thiệu các chain
  + `INPUT`:Lọc gói đi đến firewall. Ví dụ một user cần kết nối SSH và máy chủ, iptables sẽ xét xem IP và port của user này có phù hợp với một rule trong chain INPUT hay ko.
  + `OUTPUT`:Lọc gói tin đi ra firewall.Ví dụ như khi ta truy cập google.com, chain này sẽ kiểm tra xem có rules nào liên quan tới http, https và google.com hay không trước khi quyết định cho phép hoặc chặn kết nối.
  + `FORWARD`:Chain này được dùng cho các kết nối chuyển tiếp sang một máy chủ khác 
  + `PREROUTING`:Header của gói tin sẽ được chỉnh sửa tại đây trước khi việc routing được diễn ra.
  + `POSTROUTING`:Header của gói tin sẽ được chỉnh sửa tại đây sau khi việc routing được diễn ra.
- Bảng chain có trong từng table:

| Tables/Chain | PREROUTING | INPUT | FORWARD | OUTPUT | POSTROUTING |
|--------------|------------|-------|---------|--------|-------------|
|raw|x| | |x| |
|mangle|x|x|x|x|x|
|nat(DNAT)|x| | |x| |
|filter| |x|x|x| |
|security| |x|x|x| |
|nat(SNAT)| |x| | |x|
   
