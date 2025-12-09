---
title: "Nhật ký công việc tuần 11"
date: "2025-09-09"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---
{{% notice warning %}} 
⚠️ **Lưu ý:** Thông tin sau đây chỉ mang tính tham khảo. Vui lòng **không sao chép nguyên văn** cho báo cáo của bạn, bao gồm cả cảnh báo này.
{{% /notice %}}


### Mục tiêu tuần 11:

* Kết nối và làm quen với các thành viên của First Cloud Journey.
* Hiểu các dịch vụ AWS cơ bản, cách sử dụng console & CLI.

### Các nhiệm vụ cần thực hiện trong tuần này:
| Ngày | Nhiệm vụ                                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   |  - AWS Glue & Amazon Athena: <br>&emsp; + Giới thiệu AWS Glue & Amazon Athena <br>&emsp; + Chuẩn bị (Chuẩn bị database, Xây dựng database, Kiểm tra Database) <br>&emsp; + Phân tích hiệu suất chi phí và sử dụng (Dữ liệu trong bảng, Chi phí, Tagging và phân bổ chi phí, Sử dụng) <br>&emsp; + Dọn dẹp tài nguyên | 11/17/2025 | 11/17/2025      | <https://000040.awsstudygroup.com/> |
| 3   |  - Amazon DynamoDB Fundamentals: <br>&emsp; + Giới thiệu (Core Components, Primary Key, Secondary Index, Naming Rules và Data Types, Read Consistency, Read/Write Capacity Mode) <br>&emsp; + Chuẩn bị và thực hành AWS Management Console <br>&emsp; + Các thao tác thực hành (Tạo access key, Tạo bảng, Ghi/Đọc/Cập nhật dữ liệu, Truy vấn dữ liệu) <br>&emsp; + Tính năng nâng cao (Tạo Global Secondary Index, Truy vấn GSI) | 11/18/2025 | 11/18/2025      | <https://000060.awsstudygroup.com/> |
| 4   |  - DynamoDB Advanced Operations: <br>&emsp; + AWS CloudShell Operations (Tạo bảng, Ghi/Đọc/Cập nhật/Truy vấn dữ liệu, Tạo và truy vấn GSI) <br>&emsp; + AWS SDK Integration (Cấu hình AWS CLI, Python và DynamoDB) <br>&emsp; + Comprehensive SDK Operations (Tạo/Ghi/Đọc/Cập nhật/Xóa dữ liệu, Load sample data, Query/Scan operations) <br>&emsp; + Quản lý tài nguyên (Xóa bảng, Dọn dẹp tài nguyên) | 11/19/2025 | 11/19/2025      | <https://000060.awsstudygroup.com/> |
| 5   |  - AWS DataBrew Data Preparation: <br>&emsp; + Chuẩn bị (Tạo Cloud9 Instance, Download Dataset, Kiểm tra encoding, Upload Dataset lên S3) <br>&emsp; + Data Preparation với DataBrew (Thiết lập DataBrew, Data Profiling) <br>&emsp; + Data Transformation (Clean & Transform Data, Chuẩn bị Next Table, Upload cleaned dataset) | 11/20/2025 | 11/20/2025     | <https://000070.awsstudygroup.com/> |
| 6   |  - Data Ingestion & Querying: <br>&emsp; + Data Ingestion với AWS Glue (Cấu hình roles, Tạo Data Catalog, Transform sang Parquet, Tạo New Data Catalog, Xác minh Schema) <br>&emsp; + Query với Athena (Cài đặt Athena, Các thao tác query cơ bản, Join 2 bảng cho phân tích phức tạp) | 11/21/2025 | 11/21/2025      | <https://000070.awsstudygroup.com/> |


### Thành tựu tuần 11:

* **Thành thạo hệ sinh thái và dịch vụ phân tích dữ liệu AWS toàn diện:**
  * AWS Glue cho các thao tác ETL (Extract, Transform, Load)
  * Amazon Athena cho phân tích truy vấn tương tác serverless
  * AWS DataBrew cho chuẩn bị và chuyển đổi dữ liệu trực quan
  * DynamoDB cho các thao tác và quản lý cơ sở dữ liệu NoSQL
  * Các mẫu tích hợp giữa các dịch vụ phân tích

* **Triển khai quy trình phân tích dữ liệu hoàn chỉnh:**
  * Các quy trình chuẩn bị, xây dựng và xác minh cơ sở dữ liệu
  * Chiến lược phân tích và tối ưu hóa chi phí cho dịch vụ dữ liệu
  * Tagging và phân bổ chi phí cho quản lý tài nguyên
  * Phân tích hiệu suất và giám sát mẫu sử dụng

* **Đạt được chuyên môn về DynamoDB fundamentals và advanced operations:**
  * Core components, primary keys và secondary indexes
  * Các mô hình read consistency và cấu hình capacity mode
  * Các thao tác dựa trên Console, CloudShell và SDK
  * Tạo và truy vấn Global Secondary Index
  * Các thao tác CRUD toàn diện và quản lý dữ liệu

* **Phát triển thành thạo trong chuẩn bị và chuyển đổi dữ liệu:**
  * Thiết lập và quản lý môi trường phát triển Cloud9
  * Xử lý dataset, xác minh encoding và tích hợp S3
  * DataBrew visual data profiling và đánh giá chất lượng
  * Quy trình làm sạch, chuyển đổi và chuẩn bị dữ liệu
  * Xử lý và tối ưu hóa dữ liệu đa định dạng

* **Xây dựng khả năng data ingestion và querying end-to-end:**
  * Cấu hình AWS Glue role và quản lý Data Catalog
  * Chuyển đổi dữ liệu sang định dạng Parquet cho tối ưu hóa analytics
  * Xác minh schema và quản lý metadata
  * Thiết lập Athena và các thao tác truy vấn tương tác
  * Các truy vấn phân tích phức tạp bao gồm multi-table joins

* **Áp dụng best practices data engineering cấp doanh nghiệp:**
  * Chiến lược lưu trữ và xử lý dữ liệu hiệu quả về chi phí
  * Tối ưu hóa hiệu suất cho các thao tác dữ liệu quy mô lớn
  * Tích hợp nhiều dịch vụ AWS trong quy trình làm việc gắn kết
  * Dọn dẹp tài nguyên và quản lý cho môi trường production
  * Resource cleanup and management for production environments
