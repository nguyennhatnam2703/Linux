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
   
 ## 2.2:Các chain trong tables
 
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

## 2.3 Các Rule trong chain
- Các rule là tập điều kiện và hành động tương ứng để xử lý gói tin.Mỗi chain sẽ chứa rất nhiều rule, gói tin được xử lý trong một chain sẽ được so với lần lượt từng rule trong chain này.
- Cơ chế kiểm tra gói tin dựa trên rule vô cùng linh hoạt và có thể dễ dàng mở rộng thêm nhờ các extension của IPtables có sẵn trên hệ thống.
-  Rule có thể dựa trên protocol, địa chỉ nguồn/đích, port nguồn/đích, card mạng, header gói tin, trạng thái kết nối…
- Mỗi rule sẽ đươc gắn một hành động để xử lý gói tin, hành động này có thể là:
  + `ACCEPT`: gói tin sẽ được chuyển tiếp sang bảng kế tiếp.
  + `DROP`: gói tin/kết nối sẽ bị hủy, hệ thống sẽ không thực thi bất kỳ lệnh nào khác.
  + `REJECT`: gói tin sẽ bị hủy, hệ thống sẽ gởi lại 1 gói tin báo lỗi ICMP – Destination port unreachable
  + `LOG`: gói tin khớp với rule sẽ được ghi log lại.
  + `REDIRECT`: chuyển hướng gói tin sang một proxy khác.
  + `MIRROR`: hoán đổi địa chỉ IP nguồn, đích của gói tin trước khi gởi gói tin này đi.
  + `QUEUE`: chuyển gói tin tới chương trình của người dùng qua một module của kernel.
  
## 2.4 Các trạng thái kết nối

- Vai trò:Các trạng thái kết nối giúp người quản trị tạo ra những rule cụ thể và an toàn hơn cho hệ thống.
- Đây là những trạng thái mà hệ thống theo dõi tình trạng của các kết nối:
  + NEW: Khi có một gói tin mới được gởi tới và không nằm trong bất kỳ connection nào hiện có, hệ thống sẽ khởi tạo một kết nối mới và gắn nhãn NEW cho kết nối này. Nhãn này dùng cho cả TCP và UDP.
  + ESTABLISHED: Kết nối được chuyển từ trạng thái NEW sang ESTABLISHED khi máy chủ nhận được phản hồi từ bên kia.
  + RELATED: Gói tin được gửi tới không thuộc về một kết nối hiện có nhưng có liên quan đến một kết nối đang có trên hệ thống. Đây có thể là một kết nối phụ hỗ trợ cho kết nối chính. ví dụ như giao thức FTP có kết nối chính dùng để chuyển lệnh và kết nối phụ dùng để truyền dữ liệu.
  + INVALID: Gói tin được đánh dấu INVALID khi gói tin này không có bất cứ quan hệ gì với các kết nối đang có sẵn, không thích hợp để khởi tạo một kết nối mới hoặc đơn giản là không thể xác định được gói tin này, không tìm được kết quả trong bảng định tuyến. 
  + UNTRACKED: Gói tin có thể được gắn hãn UNTRACKED nếu gói tin này đi qua bảng raw và được xác định là không cần theo dõi gói này trong bảng connection tracking.
  + SNAT: Trạng thái này được gán cho các gói tin mà địa chỉ nguồn đã bị NAT, được dùng bởi hệ thống connection tracking để biết khi nào cần thay đổi lại địa chỉ cho các gói tin trả về.
  + DNAT: Trạng thái này được gán cho các gói tin mà địa chỉ đích đã bị NAT, được dùng bởi hệ thống connection tracking để biết khi nào cần thay đổi lại địa chỉ cho các gói tin gởi đi.
  
 # 3. Cấu hình Iptable cơ bản:
 
 - `iptables -t [table] [command] [match] [target] `
 
 - Các lệnh cơ bản của Iptable:
 
 | Option | Mô tả |
 |--------|-------|
 |-A chain rule|Thêm một rule vào chain|
 |-D chain rule|Xóa một rule khỏi chain|
 |-F [chain]|Xóa tất cả các rule thuộc một chain (hoặc mọi chain)|
 |-I chain index rule|Chèn rule mới vào chain tại vị trí có giá trị là index|
 |-L [chain]|Liệt kêt toàn bộ rule của một chain (hoặc mọi chain)|
 |-P chain target|Đặt policy mặc định cho chain đó|
 |-R chain index rule|Thay một rule của chain tại ví trí có giá trị là index|
 |-S [chain]|Liệt kê nội dung chi tiết của các rule thuộc một chain (hoặc mọi chain)|
 |-t table|Chọn table để áp rule|
 
 - Các cờ cấu hình cơ bản:
 
 |option | Mô tả |
 |-------|-------|
 |-d address | Địa chỉ đích |
 |-g chain| chuyển sang một chain mới|
 |-i name|nhập interface|
 |-j target|Hành động sẽ làm khi gói tin khớp rule (tức là khớp toàn bộ các điều kiện của 1 rule)|
 |-o name|Interface xuất|
 |-p protocol|Giao thức: tcp, udp, icmp, ftp, dns…|
 |-s address|Địa chỉ nguồn|
 |–dport|Port đích|
 |–sport|Port nguồn|
 |!|Phủ định một mệnh đề|
 |–state|Khớp với một tập các trạng thái của kết nối (ESTABLISHED, RELATED….)|
 |–string|Khớp với một chuỗi của dữ liệu ở tần ứng dụng (layer 7 – application layer)|
 
 - Target:
 |Target| Ý nghĩa|
 |------|--------|
 |ACCEPT|Cho phép chain thông qua rules|
 |DROP|Không cho phép chain thông qua rules|
 |REJECT|Làm việc giống DROP nhưng có gửi lại gói tin error message|
 |RETURN|Packet sẽ không traverse ở chain hiện tại. Nếu nó là subchain thì nó sẽ quay lại superior chain. Nếu nó là main chain thì policy sẽ được áp dụng.|
 |REDIRECT|Rewrite lại địa chỉ của gói tin|
 
 # Tham khảo:
 
 - [1] https://tech.bizflycloud.vn/tim-hieu-ve-iptables-phan-1-660.htm
 - [2] https://viblo.asia/p/network-tim-hieu-ve-iptables-n7prv348RKod
 - [3] https://cloudcraft.info/gioi-thieu-ve-iptables/
 
   
