---
title: "Worklog Tuần 2"
date: "2025-09-15"
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 2:

* Kết nối, làm quen với các thành viên trong First Cloud Journey.
* Hiểu dịch vụ AWS cơ bản, cách dùng console & CLI.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Giới thiệu <br> - Chuẩn bị <br>&emsp;+ Tạo cặp khóa (Key Pair) <br>&emsp;+ Khởi tạo mẫu CloudFormation <br>&emsp;+ Cấu hình Security Group <br> - Kết nối tới RDGW <br> - Triển khai Microsoft AD <br> - Thiết lập DNS <br>&emsp;+ Tạo Route 53 Outbound Endpoint <br>&emsp;+ Tạo Route 53 Resolver Rules <br>&emsp;+ Tạo Route 53 Inbound Endpoints <br>&emsp;+ Kiểm tra kết quả <br> - Dọn dẹp tài nguyên | 15/09/2025 | 15/09/2025 | < https://000010.awsstudygroup.com/> |
| 3   | - Giới thiệu <br> - Yêu cầu chuẩn bị <br>&emsp;+ Khởi tạo mẫu CloudFormation <br>&emsp;+ Tạo Security Group <br>&emsp;+ Tạo EC2 Instance <br> - Cập nhật Network ACL <br> - VPC Peering <br> - Bảng định tuyến (Route Tables) <br> - DNS giữa các VPC Peering <br> - Dọn dẹp tài nguyên | 16/09/2025 | 16/09/2025 | < https://000019.awsstudygroup.com/> |
| 4   | - Giới thiệu <br> - Chuẩn bị <br>&emsp;+ Tạo cặp khóa (Key Pair) <br>&emsp;+ Khởi tạo mẫu CloudFormation <br> - Tạo Transit Gateway <br> - Tạo Transit Gateway Attachments <br> - Tạo Transit Gateway Route Tables <br> - Thêm Transit Gateway Routes vào bảng định tuyến VPC <br> - Dọn dẹp tài nguyên | 17/09/2025 | 17/09/2025 | < https://000020.awsstudygroup.com/> |
| 5   | - Giới thiệu <br> - Chuẩn bị <br>&emsp;+ Tạo S3 Bucket <br>&emsp;+ Triển khai hạ tầng <br> - Tạo kế hoạch sao lưu (Backup plan) <br> - Thiết lập thông báo <br> - Kiểm tra khôi phục (Test Restore) <br> - Dọn dẹp tài nguyên | 18/09/2025 | 18/09/2025 | https://000013.awsstudygroup.com/> |
| 6  | - Chuẩn bị <br>&emsp;+ Tạo S3 Bucket <br>&emsp;+ Tạo EC2 cho Storage Gateway <br> - Sử dụng AWS Storage Gateway <br>&emsp;+ Tạo Storage Gateway <br>&emsp;+ Tạo File Shares <br>&emsp;+ Mount File Shares lên máy On-premises <br> - Dọn dẹp tài nguyên | 19/09/2025 | 19/09/2025 | <https://000024.awsstudygroup.com/> |


### Dưới đây là **“Thành tựu Tuần 2”** được viết ngắn gọn, xuống dòng rõ ràng, phù hợp để đưa vào **báo cáo thực tập AWS** 👇

---

### **Thành tựu Tuần 2**

* Hiểu và triển khai **Microsoft Active Directory (AD)** trên AWS, bao gồm tạo Key Pair, CloudFormation Stack và cấu hình Security Group.

* Thiết lập **DNS nội bộ với Amazon Route 53**, tạo và kiểm tra Outbound Endpoint, Resolver Rules và Inbound Endpoints để đảm bảo phân giải tên miền chính xác giữa các mạng.

* Thực hành **VPC Peering** giữa các mạng VPC, cập nhật Network ACL và Route Tables để cho phép kết nối liên vùng an toàn.

* Cấu hình **DNS Resolution** giữa các VPC đã peering, đảm bảo các máy chủ có thể giao tiếp thông suốt qua tên miền nội bộ.

* Tạo và quản lý **AWS Transit Gateway**, cấu hình Attachments và Route Tables để kết nối nhiều VPC trong cùng hệ thống mạng trung tâm.

* Triển khai và kiểm thử **AWS Backup**, tạo kế hoạch sao lưu (Backup Plan), thiết lập thông báo, và thực hiện kiểm tra khôi phục (Test Restore) thành công.

* Làm quen với **AWS Storage Gateway**, cấu hình File Gateway, tạo File Share và kết nối thành công với máy On-premises.

* Rèn luyện kỹ năng triển khai, giám sát, và dọn dẹp tài nguyên hạ tầng AWS theo quy trình chuyên nghiệp. 