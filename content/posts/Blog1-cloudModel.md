+++
title = 'Bài 1: Cloud Computing: 3 Types of Cloud'
date = 2024-05-31T16:48:18+07:00
+++

# Một số khái niệm cơ bản
## Cloud model
![Pic1](https://home-cdn.reolink.us/wp-content/uploads/2023/07/310126431690766803.2436.jpg)
### 1. Public Cloud
* Là do 1 Cloud Service Provider cung cấp, dùng server của người khác chạy workloads của mình.
* Đảm bảo đủ dùng về mặt compute, memory, network, storage.
* Fast deployments, avoid overprovisioning.
* Ví dụ: AWS, GCP, Azure.
### 2. Private Cloud
* Là 1 company tự set up data center, insfrastructure của họ để tự quản lý services và resources của họ.
* Secure, controlled.
* 1 lựa chọn là hợp tác với CSP. Họ sẽ cung cấp tài nguyên phần cứng.
    * **fully dedicated hardware**: Nhà cung cấp cung cấp các máy chủ và thiết bị mạng chỉ dành riêng cho một doanh nghiệp duy nhất. Tương tự như tự mua.
    * **shared hardware**: Các tài nguyên phần cứng được chia sẻ giữa nhiều doanh nghiệp khác nhau. Giúp giảm chi phí, hạn chế bảo mât hơn.
* **Đám mây riêng ảo (Virtual Private Clouds - VPC)**: triển khai trên phần cứng chung của nhà cung cấp dịch vụ đám mây. 

### 3. Hybrid cloud
* Combination - kết hợp cả public và private cloud
* Ví dụ: lưu data khách hàng ở private, lưu email hay shared documents ở public. Hay tận dụng computing power trên public cloud để deploy resources. Hay chuyển all resources lên public cloud, chỉ lưu 1 số ít ở private.

* **Colocation data center**: là data center cho các công ty thuê để đặt máy chủ giúp tiết kiệm chi phí.
