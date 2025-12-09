---
title: "Worklog Tuần 7"
date: "2025-09-09"
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
{{% notice warning %}} 
⚠️ **Lưu ý:** Thông tin sau đây chỉ mang tính chất tham khảo. Xin **không sao chép nguyên văn** cho báo cáo của bạn, bao gồm cả cảnh báo này.
{{% /notice %}}


### Mục tiêu Tuần 7:

* Kết nối và làm quen với các thành viên của First Cloud Journey.
* Hiểu về các dịch vụ AWS cơ bản, cách sử dụng console & CLI.

### Các công việc cần thực hiện trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   |  - VPC & EC2 Setup: <br>&emsp; + Giới thiệu về networking concepts <br>&emsp; + Tạo VPC (Virtual Private Cloud) <br>&emsp; + Cấu hình Security Group <br>&emsp; + Khởi chạy EC2 instance trong VPC <br>&emsp; + Cấu hình incoming Web-hooks cho Slack <br>&emsp; + Tạo tags cho EC2 instance | 10/20/2025 | 10/20/2025     | <https://000022.awsstudygroup.com/> |
| 3   |  - Lambda Functions: <br>&emsp; + Tạo Role cho Lambda function <br>&emsp; + Tạo Lambda Function cho automation <br>&emsp; + Triển khai function stop instance <br>&emsp; + Triển khai function start instance <br>&emsp; + Kiểm tra kết quả và testing <br>&emsp; + Dọn dẹp resources | 10/21/2025 | 10/21/2025      | <https://000022.awsstudygroup.com/> |
| 4   |  - AWS Tags Management: <br>&emsp; + Giới thiệu về AWS resource tagging <br>&emsp; + Sử dụng tags trong AWS Console <br>&emsp; + Tạo EC2 Instance với tags <br>&emsp; + Quản lý tags trong AWS Resources <br>&emsp; + Best practices cho tagging strategy | 10/22/2025 | 10/22/2025      | <https://000027.awsstudygroup.com/> |
| 5   |  - Advanced Tags & Resource Groups: <br>&emsp; + Filter resources theo tag <br>&emsp; + Sử dụng tags với AWS CLI <br>&emsp; + Tạo Resource Group <br>&emsp; + Quản lý resources thông qua Resource Groups <br>&emsp; + Dọn dẹp resources | 10/23/2025 | 10/23/2025      | <https://000027.awsstudygroup.com/> |
| 6   |  - IAM Policies & Role Management: <br>&emsp; + Giới thiệu về IAM security <br>&emsp; + Tạo IAM user <br>&emsp; + Tạo IAM Policy <br>&emsp; + Tạo IAM Role <br>&emsp; + Switch Roles và kiểm tra policy <br>&emsp; + Test EC2 access ở Tokyo và North Virginia regions <br>&emsp; + Tạo EC2 instances với qualified tags <br>&emsp; + Edit resource tags trên EC2 instances <br>&emsp; + Xác minh policy và dọn dẹp resources | 10/24/2025 | 10/24/2025      | <https://000028.awsstudygroup.com/> |


### Thành tựu Tuần 7:

* Triển khai thành công AWS networking và compute infrastructure (Lab 22):
  * Tạo và cấu hình VPC (Virtual Private Cloud) với kiến trúc mạng phù hợp
  * Thiết lập Security Groups với các quy tắc truy cập thích hợp
  * Khởi chạy EC2 instances trong môi trường VPC
  * Cấu hình incoming Web-hooks cho tích hợp Slack
  * Áp dụng các chiến lược tagging phù hợp cho EC2 instances

* Nắm vững AWS Lambda serverless automation:
  * Tạo IAM roles cho Lambda functions với quyền phù hợp
  * Phát triển Lambda functions cho tự động hóa EC2 instance
  * Triển khai function để stop EC2 instances tự động
  * Triển khai function để start EC2 instances theo yêu cầu
  * Test automation workflows và xác minh kết quả
  * Thực hiện thủ tục dọn dẹp tài nguyên toàn diện

* Có chuyên môn về AWS resource tagging và tổ chức (Lab 27):
  * Hiểu AWS resource tagging fundamentals và best practices
  * Tạo EC2 instances với strategic tag implementation
  * Quản lý tags trên nhiều AWS resources hiệu quả
  * Filter và tìm kiếm resources sử dụng tag-based queries
  * Sử dụng AWS CLI cho các thao tác quản lý tag nâng cao

* Phát triển kỹ năng thành thạo với AWS Resource Groups:
  * Tạo Resource Groups để tổ chức resources logic
  * Quản lý các tập hợp AWS resources liên quan hiệu quả
  * Triển khai các chiến lược resource grouping cho hiệu quả vận hành
  * Tối ưu hóa quản lý resources thông qua centralized grouping

* Nắm vững advanced IAM security và access control (Lab 28):
  * Tạo IAM users với các yêu cầu permission cụ thể
  * Phát triển custom IAM policies cho granular access control
  * Tạo và cấu hình IAM roles cho cross-service access
  * Triển khai role switching cho các scenarios truy cập khác nhau
  * Test multi-region access control (Tokyo và North Virginia)
  * Tạo EC2 instances với qualified tag requirements
  * Edit và quản lý resource tags để tuân thủ policy
  * Xác minh tính hiệu quả của policy thông qua testing toàn diện

* Có kỹ năng toàn diện về AWS security, automation và resource management kết hợp networking, compute services, serverless functions và các cơ chế access control nâng cao.
