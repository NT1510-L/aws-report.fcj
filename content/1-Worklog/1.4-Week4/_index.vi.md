---
title: "Worklog Tuần 4"
date: "2025-08-14"
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 4:

* Kết nối, làm quen với các thành viên trong First Cloud Journey.
* Hiểu dịch vụ AWS cơ bản, cách dùng console & CLI.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Chuẩn bị <br>&emsp;+ Tạo S3 Bucket <br>&emsp;+ Tải dữ liệu <br> - Kích hoạt tính năng static website <br>&emsp;- Cấu hình public access block <br>&emsp;- Cấu hình public objects <br> - Kiểm tra website | 09/29/2025 | 09/29/2025      | < https://000013.awsstudygroup.com/> |
| 3   | - Thiết lập thông báo <br> - Kiểm tra khôi phục <br> - Dọn dẹp tài nguyên | 09/30/2025 | 09/30/2025     | < https://000013.awsstudygroup.com/> |
| 4   | - VMWare Workstation <br> - Import máy ảo vào AWS <br>&emsp;+ Xuất máy ảo từ On-premises <br>&emsp;+ Tải máy ảo lên AWS <br>&emsp;+ Import máy ảo vào AWS <br>&emsp;+ Triển khai Instance từ AMI | 10/01/2025 | 10/01/2025     | < https://000014.awsstudygroup.com/> |
| 5   | - Xuất instance từ AWS <br>&emsp;+ Thiết lập S3 bucket ACL <br>&emsp;+ Xuất máy ảo từ Instance <br>&emsp;+ Xuất máy ảo từ AMI <br> - Video tham khảo <br> - Dọn dẹp tài nguyên trên AWS | 10/02/2025 | 10/02/2025     | < https://000014.awsstudygroup.com/> |
| 6   | - Ôn tập và thực hành các hoạt động trong tuần <br>&emsp;+ Ôn tập thiết lập S3 static website <br>&emsp;+ Thực hành quy trình import/export VM <br>&emsp;+ Ôn tập thủ tục backup và restore <br> - Củng cố kiến thức và khắc phục sự cố | 10/03/2025 | 10/03/2025 | |



### Kết quả đạt được tuần 4:

* Đã tạo và cấu hình thành công S3 buckets cho static website hosting:
  * Cấu hình bucket policies để truy cập công khai
  * Tải lên các file website và tài nguyên
  * Kích hoạt tính năng static website hosting
  * Cấu hình public access blocks phù hợp
  * Kiểm tra chức năng và khả năng truy cập website

* Nắm vững các thao tác backup và restore trên S3:
  * Thiết lập thông báo backup
  * Thực hiện các thủ tục kiểm tra backup
  * Khôi phục dữ liệu từ backup thành công
  * Thực hiện thủ tục dọn dẹp tài nguyên đúng cách

* Có kinh nghiệm thực tế với việc migration VM sang AWS:
  * Thiết lập môi trường VMware Workstation
  * Xuất máy ảo từ hạ tầng on-premises
  * Tải file VM lên AWS S3 storage
  * Import VM thành công sử dụng AWS VM Import/Export service
  * Triển khai EC2 instances từ AMI đã import

* Học được quy trình migration ngược từ AWS:
  * Cấu hình S3 bucket ACLs để export VM
  * Xuất running instances về định dạng VM
  * Xuất AMIs thành file VM có thể tải về
  * Thực hiện dọn dẹp tài nguyên hoàn chỉnh trên AWS

* Phát triển thành thạo các dịch vụ AWS storage và compute:
  * Quản lý và cấu hình S3 bucket
  * Triển khai và quản lý EC2 instance
  * Tạo và thao tác AMI
  * Quy trình migration VM đa nền tảng

* Có được kỹ năng thực tế trong chiến lược cloud migration và thủ tục backup/restore cần thiết cho môi trường doanh nghiệp.
