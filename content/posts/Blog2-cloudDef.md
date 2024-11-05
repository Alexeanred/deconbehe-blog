+++
title = 'Bài 2: Cloud computing: Basic definitions'
date = 2024-09-22T17:23:41+07:00
draft = false
+++

# Một số khái niệm cơ bản
## HA (High Availability)
![Pic2](https://www.techtarget.com/rms/onlineimages/cloud_computing-availability_sla.png)
* HA thường được đo bởi phần trăm thời gian hoạt động.
* Tính sẵn sàng cao nói đến khả năng tránh sự cố, loại bỏ các SPOF (Single-point-of-failure).
* Single Point of Failure là một thành phần duy nhất của một hệ thống mà khi bị lỗi sẽ làm toàn bộ hệ thống ngừng hoạt động. Ví dụ: 1 server duy nhất, 1 storage duy nhất, 1 nguồn điện, 1 đường truyền mạng. 
* 1 hệ thống có thể tiếp tục hoạt động khi có 1 thành phần bị lỗi, ko bị downtime, mất dữ liệu và khôi phục liền sau đó.
* 1 số yếu tố của 1 hệ thống HA tốt:
    * Redundancy: khả năng dự phòng - khả năng có nhiều thành phần giống hệt nhau được sao lưu sẵn sàng trong hệ thống, khi một thành phần chính bị lỗi, một thành phần dự phòng sẽ tiếp quản ngay lập tức mà không làm gián đoạn dịch vụ.
    * Monitoring: khả năng giám sát - quá trình theo dõi sức khỏe các thành phần trong hệ thống.
    * Failover: khả năng chuyển đổi dự phòng - tự động chuyển đổi từ thành phần gặp sự cố sang thành phần dự phòng trong trường hợp có lỗi.
    * Failback: khả năng khôi phục - quá trình chuyển ngược lại từ thành phần dự phòng về thành phần chính sau khi thành phần chính đã được khắc phục lỗi. Failback đảm bảo rằng hệ thống sẽ không phụ thuộc vào thành phần dự phòng lâu dài, và có thể trở lại trạng thái tối ưu khi thành phần chính đã sẵn sàng.
### SLA (Service Level Agreement)
* SLA, hay Service Level Agreement, là một thỏa thuận dịch vụ giữa nhà cung cấp dịch vụ (như dịch vụ cloud, phần mềm, viễn thông) và khách hàng. Thỏa thuận này xác định các cam kết về mức độ dịch vụ mà nhà cung cấp phải đảm bảo, như thời gian hoạt động (uptime), độ trễ (latency), tốc độ phản hồi, và các điều khoản hỗ trợ kỹ thuật. SLA cũng thường quy định các biện pháp xử phạt (penalty) hoặc bồi thường nếu nhà cung cấp không đạt được mức cam kết.
## Agility (Khả năng linh hoạt)
* Agility đề cập đến khả năng của một hệ thống hoặc tổ chức có thể nhanh chóng thích ứng và thay đổi theo nhu cầu kinh doanh mới, điều chỉnh tài nguyên và dịch vụ một cách linh hoạt mà không cần thời gian hoặc chi phí lớn.

## Scalability (khả năng mở rộng)
* Scalability là khả năng của hệ thống có thể mở rộng để đáp ứng khối lượng công việc tăng cao bằng cách tăng tài nguyên (ví dụ: CPU, RAM, lưu trữ). Scalability có thể theo chiều dọc (vertical scaling) (tăng cường tài nguyên trên một instance) hoặc theo chiều ngang (horizontal scaling) (thêm nhiều instance vào hệ thống).

## Elasticity
* Elasticity là khả năng của hệ thống tự động mở rộng và thu hẹp tài nguyên dựa trên nhu cầu thực tế của khối lượng công việc. Không chỉ mở rộng khi cần, mà còn có khả năng giải phóng tài nguyên khi nhu cầu giảm xuống để tối ưu hóa chi phí.

## Fault Tolerance (Khả năng chịu lỗi)
*  Fault tolerance là khả năng của hệ thống tiếp tục hoạt động chính xác ngay cả khi một hoặc nhiều thành phần trong hệ thống gặp sự cố. Các thành phần dự phòng được sử dụng để tránh gián đoạn dịch vụ.

## Resilience (Khả năng phục hồi)
* Resilience là khả năng của hệ thống có thể phục hồi sau sự cố và tiếp tục hoạt động mà không bị mất dữ liệu hoặc ảnh hưởng nghiêm trọng đến hiệu suất.

## Disaster recovery 
* Disaster recovery là quá trình lập kế hoạch và triển khai các biện pháp để khôi phục lại hệ thống sau các thảm họa lớn (như hỏng hạ tầng, thiên tai, hoặc mất điện) nhằm đảm bảo dịch vụ không bị gián đoạn hoặc giảm thiểu thời gian gián đoạn.

## Sustainability
* Sustainability (bền vững) trong điện toán đám mây là việc thiết kế và vận hành các khối lượng công việc (workload) trên đám mây sao cho giảm thiểu các tác động tiêu cực đến môi trường, đặc biệt là tiêu thụ năng lượng và phát thải carbon. Điều này bao gồm việc hiểu và giảm thiểu tài nguyên mà các dịch vụ đám mây sử dụng, chẳng hạn như điện và phần cứng, trong suốt vòng đời của một khối lượng công việc. Thực hành này phù hợp với phát triển bền vững, đảm bảo rằng các hoạt động hiện tại không làm ảnh hưởng đến khả năng của các thế hệ tương lai trong việc đáp ứng nhu cầu của họ. Trong điện toán đám mây, trách nhiệm về bền vững được chia sẻ giữa nhà cung cấp đám mây và khách hàng sử dụng dịch vụ.

