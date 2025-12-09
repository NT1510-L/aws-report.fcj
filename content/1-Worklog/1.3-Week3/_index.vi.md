---
title: "Nhật ký Tuần 3"
date: "2025-09-22"
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---
{{% notice warning %}} 
⚠️ **Lưu ý:** Thông tin sau chỉ dùng để tham khảo. Vui lòng **không sao chép nguyên văn** vào báo cáo thực tập của bạn, kể cả phần cảnh báo này.
{{% /notice %}}


### Mục tiêu Tuần 3:

* Kết nối và làm quen với các thành viên của First Cloud Journey.
* Hiểu các dịch vụ cơ bản của AWS và cách sử dụng giao diện quản lý (Console) & CLI.

### Các nhiệm vụ thực hiện trong tuần:
| Ngày | Nhiệm vụ                                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Chuẩn bị <br>&emsp;+ Tạo S3 Bucket <br>&emsp;+ Tải dữ liệu <br> - Bật tính năng trang web tĩnh trên S3 <br>&emsp;+ Cấu hình Public Access Block <br>&emsp;+ Cấu hình các đối tượng công khai <br> - Kiểm tra website | 09/22/2025 | 09/22/2025      | <https://000057.awsstudygroup.com/> |
| 3   | - Chuẩn bị <br>&emsp;+ Tìm hiểu về AWS và các loại dịch vụ <br>&emsp;&emsp;+ Compute <br>&emsp;&emsp;+ Storage <br>&emsp;&emsp;+ Networking <br>&emsp;&emsp;+ Database <br>&emsp;&emsp;+ ... <br> - Tăng tốc trang web tĩnh bằng CloudFront <br>&emsp;+ Chặn toàn bộ truy cập công khai (S3) <br>&emsp;+ Cấu hình Amazon CloudFront <br>&emsp;+ Kiểm tra phân phối qua CloudFront <br>  | 09/23/2025 | 09/23/2025      | <https://000057.awsstudygroup.com/> |
| 4   | - Phiên bản Bucket (Bucket Versioning) <br>&emsp;+ Di chuyển đối tượng <br>&emsp;+ Thiết lập sao chép đối tượng đa vùng (Replication - multi-Region) <br> - Dọn dẹp tài nguyên <br>  | 09/24/2025 | 09/24/2025      | <https://000057.awsstudygroup.com/> |
| 5   | - **Thực hành:** Triển khai và quản lý EC2 với lưu trữ EBS <br>&emsp;- Triển khai EC2, kết nối SSH và gắn EBS                                                                                     | 09/24/2025 | 08/15/2025      | <https://000057.awsstudygroup.com/> |
| 6   | - **Thực hành:** Lab thực hành: Triển khai EC2 và quản lý EBS                                                                                       | 09/25/2025 | 08/15/2025      | <https://000057.awsstudygroup.com/> |


### Thành tựu Tuần 3:

* Có kinh nghiệm thực hành với tính năng lưu trữ trang web tĩnh trên S3, bao gồm:
  * Tạo và cấu hình S3 Bucket
  * Tải dữ liệu trang web
  * Bật chức năng hosting trang web tĩnh
  * Cấu hình Public Access Block
  * Thiết lập quyền đọc công khai cho các đối tượng (khi cần)

* Học cách tăng tốc phân phối nội dung bằng Amazon CloudFront:
  * Chặn toàn bộ truy cập công khai ở lớp S3
  * Tạo và cấu hình CloudFront distribution
  * Kiểm tra phân phối nội dung qua URL CloudFront

* Thực hành các tính năng quản lý S3 nâng cao, bao gồm:
  * Bật Bucket Versioning
  * Di chuyển và tổ chức các đối tượng
  * Thiết lập Replication đối tượng đa vùng (Multi-Region Replication)

* Hoàn thành quy trình triển khai EC2 đầy đủ, bao gồm:
  * Khởi tạo EC2 với cấu hình phù hợp
  * Lựa chọn AMI, loại instance, key pair và cấu hình mạng
  * Xác minh truy cập hệ thống và thực hiện các thao tác Linux cơ bản

* Nâng cao hiểu biết về cách tích hợp giữa dịch vụ tính toán và lưu trữ:

  * Tương tác giữa EC2 và EBS trong cùng AZ
  * Các quy trình làm việc thực tế cho quản trị hệ thống

* Đã tạo và cấu hình AWS Free Tier account thành công.

* Làm quen với AWS Management Console và biết cách tìm, truy cập, sử dụng dịch vụ từ giao diện web.

* Cài đặt và cấu hình AWS CLI trên máy tính bao gồm:
  * Access Key
  * Secret Key
  * Region mặc định
  * ...

* Sử dụng AWS CLI để thực hiện các thao tác cơ bản như:

  * Kiểm tra thông tin tài khoản & cấu hình
  * Lấy danh sách region
  * Xem dịch vụ EC2
  * Tạo và quản lý key pair
  * Kiểm tra thông tin dịch vụ đang chạy
  * ...

* Có khả năng kết nối giữa giao diện web và CLI để quản lý tài nguyên AWS song song.
* ...


