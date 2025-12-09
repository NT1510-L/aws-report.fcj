---
title: "Worklog Tuần 5"
date: "2025-09-09"
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 5:

* Kết nối, làm quen với các thành viên trong First Cloud Journey.
* Hiểu dịch vụ AWS cơ bản, cách dùng console & CLI.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Chuẩn bị <br>&emsp;+ Tạo S3 Bucket <br>&emsp;+ Tạo EC2 cho Storage Gateway | 10/06/2025| 10/06/2025      | < https://000024.awsstudygroup.com/> |
| 3   | - Sử dụng AWS Storage Gateway <br>&emsp;+ Tạo Storage Gateway <br>&emsp;+ Tạo File Shares <br>&emsp;+ Mount File shares trên máy On-premises <br> - Dọn dẹp tài nguyên | 10/07/2025 | 10/07/2025     | < https://000024.awsstudygroup.com/> |
| 4   | - Giới thiệu <br> - Chuẩn bị <br>&emsp;+ Tạo môi trường <br>&emsp;+ Tạo SSD Multi-AZ file system <br>&emsp;+ Tạo HDD Multi-AZ file system <br> - Tạo file shares mới | 10/08/2025 | 10/08/2025      | < https://000025.awsstudygroup.com/> |
| 5   | - Kiểm tra hiệu năng <br> - Giám sát hiệu năng <br> - Kích hoạt data deduplication <br> - Kích hoạt shadow copies <br> - Quản lý phiên người dùng và file đang mở <br> - Kích hoạt user storage quotas <br> - Kích hoạt Continuous Access share | 10/09/2025 | 10/09/2025      | < https://000025.awsstudygroup.com/> |
| 6   | - Mở rộng throughput capacity <br> - Mở rộng storage capacity <br> - Xóa môi trường <br> - Sử dụng AWS CLI (tham khảo) | 10/10/2025 | 10/10/2025      | < https://000025.awsstudygroup.com/> |


### Kết quả đạt được tuần 5:

* Triển khai thành công các giải pháp AWS Storage Gateway:
  * Tạo và cấu hình S3 buckets cho backend của storage gateway
  * Thiết lập EC2 instances làm storage gateway appliances
  * Triển khai và cấu hình dịch vụ AWS Storage Gateway
  * Tạo và quản lý file shares cho hybrid cloud storage
  * Mount thành công file shares trên máy on-premises
  * Thực hiện thủ tục dọn dẹp tài nguyên hoàn chỉnh

* Nắm vững quản lý và vận hành AWS file system:
  * Tạo môi trường test toàn diện cho file systems
  * Triển khai cả SSD và HDD Multi-AZ file systems
  * Cấu hình và quản lý file shares mới trên các loại storage khác nhau
  * Thực hiện kiểm tra và giám sát hiệu năng của file systems
  * Triển khai các tính năng nâng cao bao gồm data deduplication và shadow copies

* Có chuyên môn về các tính năng quản lý storage doanh nghiệp:
  * Quản lý phiên người dùng và giám sát file đang mở
  * Cấu hình user storage quotas để quản lý tài nguyên
  * Kích hoạt Continuous Access shares cho tính khả dụng cao
  * Mở rộng động throughput và storage capacity một cách linh hoạt
  * Thực hiện xóa môi trường và dọn dẹp có kiểm soát

* Phát triển kỹ năng thành thạo AWS CLI cho dịch vụ storage:
  * Sử dụng AWS CLI cho lệnh quản lý storage gateway
  * Thực thi các thao tác file system qua giao diện dòng lệnh
  * Tự động hóa các tác vụ mở rộng và cấu hình storage
  * Triển khai script giám sát và quản lý

* Có kinh nghiệm thực tế với kiến trúc hybrid cloud storage:
  * Tích hợp hệ thống on-premises với AWS cloud storage
  * Cấu hình luồng dữ liệu liền mạch giữa môi trường local và cloud
  * Triển khai các giải pháp storage cấp doanh nghiệp với dịch vụ AWS
  * Tối ưu hóa hiệu năng và hiệu quả chi phí storage trên hạ tầng hybrid

* Nắm vững các tính năng storage nâng cao thiết yếu cho môi trường doanh nghiệp bao gồm chiến lược backup, tối ưu hóa hiệu năng và kiến trúc storage có thể mở rộng.
