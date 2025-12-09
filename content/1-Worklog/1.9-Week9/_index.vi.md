---
title: "Worklog Tuần 9"
date: "2025-09-09"
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---
{{% notice warning %}} 
⚠️ **Lưu ý:** Thông tin sau đây chỉ mang tính chất tham khảo. Xin **không sao chép nguyên văn** cho báo cáo của bạn, bao gồm cả cảnh báo này.
{{% /notice %}}


### Mục tiêu Tuần 9:

* Kết nối và làm quen với các thành viên của First Cloud Journey.
* Hiểu về các dịch vụ AWS cơ bản, cách sử dụng console & CLI.

### Các công việc cần thực hiện trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - **Lab 48 - EC2, S3 & IAM Integration:** <br>&emsp; + Chuẩn bị và thiết lập môi trường <br>&emsp; + Tạo EC2 Instance để testing <br>&emsp; + Tạo S3 bucket cho storage <br>&emsp; + Generate IAM user và access key <br>&emsp; + Sử dụng access key cho authentication <br>&emsp; + Tạo IAM role cho EC2 <br>&emsp; + Sử dụng IAM role trên EC2 <br>&emsp; + Dọn dẹp resources | 11/03/2025 | 11/03/2025       | <https://000048.awsstudygroup.com/> |
| 3   | - **Lab 05 - VPC & RDS Infrastructure:** <br>&emsp; + Giới thiệu về VPC và RDS concepts <br>&emsp; + Các bước prerequisite và planning <br>&emsp; + Tạo VPC cho database environment <br>&emsp; + Tạo EC2 Security Group <br>&emsp; + Tạo RDS Security Group <br>&emsp; + Tạo DB Subnet Group | 11/04/2025 | 11/04/2025      | <https://000005.awsstudygroup.com/> |
| 4   | - **Lab 05 - EC2 & RDS Deployment:** <br>&emsp; + Tạo EC2 instance trong VPC <br>&emsp; + Tạo RDS database instance <br>&emsp; + Application deployment trên EC2 <br>&emsp; + Database connectivity testing <br>&emsp; + Backup và restore procedures <br>&emsp; + Dọn dẹp resources và environment | 11/05/2025 | 11/05/2025      | <https://000005.awsstudygroup.com/> |
| 5   | - **Lab 43 - AWS Database Migration Service:** <br>&emsp; + Getting started với DMS <br>&emsp; + Select DMS source database <br>&emsp; + Select DMS target database <br>&emsp; + Cấu hình serverless replication <br>&emsp; + Monitor DMS migrations <br>&emsp; + Troubleshoot migrations với AWS DMS <br>&emsp; + Environment cleanup | 11/06/2025 | 11/06/2025       | <https://000043.awsstudygroup.com/> |
| 6   | - **Lab 35 - Data Analytics Pipeline:** <br>&emsp; + Giới thiệu về data analytics services <br>&emsp; + Tạo IAM Role và Policy <br>&emsp; + Tạo S3 Bucket cho data storage <br>&emsp; + Tạo Kinesis Delivery Stream <br>&emsp; + Generate sample data <br>&emsp; + Tạo Glue Crawler cho data catalog <br>&emsp; + Thực hiện data transformation <br>&emsp; + Analysis với Athena <br>&emsp; + Visualize với QuickSight <br>&emsp; + Dọn dẹp resources | 11/07/2025 | 11/07/2025       | <https://000035.awsstudygroup.com/> |


### Thành tựu Tuần 9:

* Triển khai thành công comprehensive EC2, S3 và IAM integration (Lab 48):
  * Thiết lập complete AWS environment với proper preparation procedures
  * Tạo và cấu hình EC2 instances cho testing và development
  * Thiết lập S3 buckets cho secure storage solutions
  * Generate IAM users và access keys cho authentication
  * Triển khai access key-based authentication mechanisms
  * Tạo và cấu hình IAM roles cho EC2 instances
  * Áp dụng IAM roles to EC2 cho secure service interactions
  * Thực hiện comprehensive resource cleanup và management

* Nắm vững VPC networking và RDS database infrastructure (Lab 05):
  * Có hiểu biết sâu về VPC và RDS architectural concepts
  * Thực thi prerequisite steps và infrastructure planning
  * Tạo VPC environments được tối ưu hóa cho database workloads
  * Cấu hình EC2 và RDS Security Groups với proper access rules
  * Thiết lập DB Subnet Groups cho multi-AZ deployments
  * Deploy EC2 instances trong VPC environments
  * Tạo và cấu hình RDS database instances

* Phát triển chuyên môn về application deployment và database management:
  * Triển khai thành công applications trên EC2 infrastructure
  * Thực hiện comprehensive database connectivity testing
  * Triển khai backup và restore procedures cho data protection
  * Quản lý complete environment cleanup và resource optimization

* Có kỹ năng thành thạo AWS Database Migration Service (Lab 43):
  * Nắm vững DMS fundamentals và migration concepts
  * Cấu hình DMS source database connections
  * Thiết lập DMS target database environments
  * Triển khai serverless replication cho scalable migrations
  * Monitor DMS migration processes và performance
  * Troubleshoot complex migration issues với AWS DMS tools
  * Áp dụng proper environment cleanup procedures

* Xây dựng thành công end-to-end data analytics pipeline (Lab 35):
  * Hiểu comprehensive data analytics service architecture
  * Tạo IAM roles và policies cho data services
  * Thiết lập S3 buckets cho scalable data storage
  * Triển khai Kinesis Delivery Streams cho real-time data ingestion
  * Generate và quản lý sample data cho testing
  * Tạo AWS Glue Crawlers cho automated data catalog management
  * Thực hiện advanced data transformation processes
  * Thực hiện sophisticated analysis sử dụng Amazon Athena
  * Xây dựng interactive visualizations với Amazon QuickSight
  * Duy trì proper resource management và cleanup

* Có chuyên môn toàn diện về AWS infrastructure, database services, migration tools và data analytics platforms kết hợp compute, storage, networking, database và analytics services cho enterprise-level solutions.
