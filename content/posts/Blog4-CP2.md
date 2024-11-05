+++
title = 'Bài 4: AWS Card Clash Cloud Practitioner 2: Regions and Zones'
date = 2024-09-29T16:29:11+07:00
draft = false
+++

![architecture-picture](/deconbehe-blog/images/arch.png)

# Mục Đích
* Thông qua bài blog này, ta sẽ tìm hiểu một số khái niệm về networking trong AWS như VPC, subnet, các zones như local zone, wavelengths zone, outposts zone.
* Đồng thời ta sẽ thực hành tạo custom VPC, subnet, tạo EC2 instance, tạo resources như EC2 instance trong local zone.
# Khái Niệm
### VPC (Virtual Private Cloud)
* VPC là một môi trường mạng ảo cho phép bạn triển khai các tài nguyên của mình trên đám mây AWS một cách bảo mật và có thể kiểm soát hoàn toàn. Với VPC, bạn có thể tự do cấu hình không gian địa chỉ IP, subnets, bảng định tuyến, và cài đặt bảo mật nhằm đáp ứng các yêu cầu cụ thể của tổ chức.
* Mỗi VPC có thể chứa nhiều subnets và có thể được kết nối với Internet thông qua Internet Gateway hoặc VPN Gateway nếu cần.
### Subnet
* Subnet là một phân đoạn của VPC với không gian địa chỉ IP con của VPC đó, giúp tách biệt tài nguyên của bạn vào các nhóm nhỏ để kiểm soát lưu lượng mạng và bảo mật tốt hơn.
* Có thể thiết lập public subnets (cho phép kết nối Internet) hoặc private subnets (chỉ có thể truy cập từ bên trong mạng VPC hoặc qua VPN).
### Local Zone
* Local Zones là các khu vực tính toán có độ trễ thấp đặt gần các khu vực địa lý nhất định. Điều này giúp giảm độ trễ cho các ứng dụng đòi hỏi thời gian phản hồi nhanh và độ trễ thấp, như các ứng dụng về gaming, AR/VR, và truyền thông trực tiếp.
* Local Zones mở rộng khả năng của AWS đến gần người dùng hơn mà vẫn giữ các tài nguyên nằm trong khu vực kiểm soát của bạn.
### Wavelengths Zone
* Wavelength Zones là các vùng đặc biệt được xây dựng hợp tác giữa AWS và các nhà cung cấp dịch vụ viễn thông, cho phép chạy các ứng dụng yêu cầu độ trễ thấp trên mạng 5G. Những ứng dụng này sẽ tận dụng được hạ tầng viễn thông ở gần người dùng cuối.
* Các tài nguyên trong Wavelength Zones có thể kết nối trực tiếp với các mạng 5G, giúp tối ưu cho các dịch vụ truyền tải video, AR/VR, và IoT.
### Outposts Zone
* AWS Outposts cho phép bạn triển khai cơ sở hạ tầng AWS tại trung tâm dữ liệu của mình với tính nhất quán về API và khả năng tương thích với các dịch vụ AWS. Outposts giúp giữ các ứng dụng yêu cầu độ trễ cực thấp và cần xử lý dữ liệu tại chỗ mà không cần gửi đến các vùng của AWS.
* Outposts Zones là các khu vực mạng riêng biệt giúp đưa dịch vụ của AWS đến những vị trí mà bạn không thể triển khai VPC hoặc không muốn sử dụng dịch vụ hoàn toàn trên đám mây.
# Thực Hành
## Tạo EC2 instance trong custom VPC
* Các bước: 
    1. Tạo custom VPC.
    2. Tạo subnet trong VPC đó.
    3. Tạo internet gateway cho VPC.
    4. Attach igw vào route table. 
    5. Associate subnet với route table. 
    6. Tạo ec2 instance.
* Đầu tiên, ta tạo custom VPC:
    * Chọn VPC only.
    * Điền tên VPC như: **myVPC**.
    * Điền IPv4 CIDR như: **10.0.0.0/16**.
    * Chọn nút: **Create VPC**.
![alt](/deconbehe-blog/images/vpc1.png)
* Sau khi tạo VPC xong, ta tạo subnet:
    * Chọn VPC vừa tạo.
    * Điền tên subnet như: **myVPC-subnet01**
    * Chọn AZ cho subnet.
    * Điền IPv4 subnet CIDR block như: **10.0.0.0/24**
    * Chọn nút: **Create subnet**
![alt](/deconbehe-blog/images/subnet1.png)
* Vì ta muốn các resources bên trong VPC có thể kết nối Internet nên ta tạo một internet gateway:
    * Chọn mục **Internet gateways** trong VPC.
    * Điền tên igw như: **myVPC-igw**.
    * Chọn **Create internet gateway**.
![alt](/deconbehe-blog/images/igw.png)
* Sau khi tạo xong igw, ta attach to VPC:
    * Chọn VPC.
    * Chọn nút: **Attach internet gateway**.
![alt](/deconbehe-blog/images/igw2.png)
* Sau đó, ta thêm 1 route vào route table của VPCL
    * Trong rtb có 2 vị trí để điền là target và destination:
        * Destination điền: **0.0.0.0/0**
        * Target chọn igw đã tạo.
<img src="/deconbehe-blog/images/image.png" alt="Mô tả ảnh" style="width:600px; height:400px;">
![Resize](/deconbehe-blog/images/rtb1.png?width=800px)
* Cuối cùng, ta liên kết subnet với route table:
![alt](/deconbehe-blog/images/rtb4.png)
* Tiếp theo ta tạo 1 security group để allow internet truy cập vào instance:
    * Chọn **Type** là HTTP và source: **0.0.0.0/0**.
    * Nếu application chạy ở port khác như 8080 thì ta chọn Type là Custom TCP và source **0.0.0.0/0**.
![alt](/deconbehe-blog/images/sg10.png)
* Tạo EC2 instance như cấu hình dưới đây:
![alt](/deconbehe-blog/images/ec21.png)
* Nếu đã lỡ tạo ec2 instance trước thì vào Actions chọn Security chọn change security group:
![alt](/deconbehe-blog/images/sg2.png)
* Nếu ec2 instance không có Public IPv4 DNS, ta vào **Edit VPC settings** để check vào box **Enable DNS hostnames**.
![alt](/deconbehe-blog/images/hostname1.png)

## Tạo EC2 instance trong local zone
* Đầu tiên ta search trên thanh tìm kiếm local zone, chọn AWS local zones:
    * Sau đó ta chọn Actions -> Manage Zone group và enable 1 local zone.
![alt](/deconbehe-blog/images/localzone0.png)
* Tiếp theo, ta tạo subnet trong local zone đó:
    * Lưu ý: IPv4 CIDR block phải khác với subnet đã tạo trên của AZ
![alt](/deconbehe-blog/images/localzone1.png)
* Tạo ec2 instance như hình dưới:
    * Lưu ý: Chọn subnet của local Zone đã tạo.
![alt](/deconbehe-blog/images/localzone2.png)
* Lưu ý: Ở local zone không có tất cả các instance types như ở region. Như dưới đây là phải chọn c6i.large do nó không có t2.micro.
![alt](/deconbehe-blog/images/localzone3.png)
* Ta vào thử 2 web chạy ở 2 zones khác nhau:
![alt](/deconbehe-blog/images/localzone4.png)
* Lưu ý: Nếu IAM user chỉ có quyền tạo resources trên những region nhất định như us-east-1 và muốn tạo resources ở local zone từ region đó thì phải request quyền để dùng được.