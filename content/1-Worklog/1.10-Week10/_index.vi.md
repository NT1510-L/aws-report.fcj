---
title: "Nhật ký công việc tuần 10"
date: "2025-09-09"
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
{{% notice warning %}} 
⚠️ **Lưu ý:** Thông tin sau đây chỉ mang tính tham khảo. Vui lòng **không sao chép nguyên văn** cho báo cáo của bạn, bao gồm cả cảnh báo này.
{{% /notice %}}


### Mục tiêu tuần 10:

* Kết nối và làm quen với các thành viên của First Cloud Journey.
* Hiểu các dịch vụ AWS cơ bản, cách sử dụng console & CLI.

### Các nhiệm vụ cần thực hiện trong tuần này:
| Ngày | Nhiệm vụ                                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - DynamoDB Hands-on Labs: <br>&emsp; + Bắt đầu với DynamoDB <br>&emsp; + Tạo bảng DynamoDB và tải dữ liệu mẫu <br>&emsp; + Khám phá DynamoDB với CLI (Read, Query, Scan, Insert/Update, Delete) <br>&emsp; + Làm việc với Transactions và Global Secondary Indexes <br>&emsp; + Khám phá DynamoDB Console (Xem, Query, Scan, Sửa đổi dữ liệu) <br>&emsp; + Triển khai Backups (Point-In-Time Recovery, On-Demand, Scheduled) <br>&emsp; + Relational Modeling & Migration với DMS <br>&emsp; + Cấu hình môi trường MySQL và migration DynamoDB <br>&emsp; + Dọn dẹp tài nguyên | 11/10/2025 | 11/10/2025      | <https://000039.awsstudygroup.com/> |
| 3   | - **LBED: Generative AI với DynamoDB zero-ETL tới OpenSearch integration và Amazon Bedrock:** <br>&emsp; + Bắt đầu - Lấy & Xem xét mã nguồn <br>&emsp; + Cấu hình dịch vụ (OpenSearch Service Permissions, Kích hoạt Amazon Bedrock Models, Tải dữ liệu DynamoDB) <br>&emsp; + Cấu hình Integrations và tạo zero-ETL Pipeline <br>&emsp; + Query và Kết luận <br>- **LADV: Advanced Design Patterns cho Amazon DynamoDB:** <br>&emsp; + Bắt đầu (Systems Manager Console, Python/AWS CLI, boto3, workshop files) <br>&emsp; + Bài tập 1: DynamoDB Capacity Units và Partitioning <br>&emsp; + Bài tập 2: Sequential và Parallel Table Scans <br>&emsp; + Bài tập 3: Global Secondary Index Write Sharding <br>&emsp; + Bài tập 4: Global Secondary Index Key Overloading <br>&emsp; + Bài tập 5: Sparse Global Secondary Indexes <br>&emsp; + Bài tập 6: Composite Keys <br>&emsp; + Bài tập 7: Adjacency Lists <br>&emsp; + Bài tập 8: DynamoDB Streams và AWS Lambda <br>- **LCDC: Change Data Capture cho Amazon DynamoDB:** <br>&emsp; + Bắt đầu (Cloud9, EC2 Instance) <br>&emsp; + Tổng quan kịch bản (Tạo bảng DynamoDB, Tải dữ liệu mẫu) <br>&emsp; + Change Data Capture sử dụng DynamoDB Streams <br>&emsp; + Change Data Capture sử dụng Kinesis Data Streams <br>&emsp; + Tóm tắt và Dọn dẹp | 11/11/2025 | 11/11/2025      | <https://000039.awsstudygroup.com/> |
| 4   | - **LMR: Xây dựng và triển khai ứng dụng Serverless toàn cầu với Amazon DynamoDB:** <br>&emsp; + Bắt đầu <br>&emsp; + Module 1: Triển khai tài nguyên backend <br>&emsp; + Module 2: Khám phá Global Tables <br>&emsp; + Module 3: Tương tác với Globalflix Interface <br>&emsp; + Chủ đề thảo luận Global Tables <br>&emsp; + Tóm tắt và Dọn dẹp <br>- **LEDA: Xây dựng kiến trúc hướng sự kiện Serverless với DynamoDB:** <br>&emsp; + Bắt đầu và Tổng quan <br>&emsp; + Tùy chọn - Pipeline Deep Dive <br>&emsp; + Lab 1: Kết nối pipeline (StateLambda, MapLambda trigger, ReduceLambda) <br>&emsp; + Lab 2: Đảm bảo fault tolerance và exactly once processing <br>&emsp; + Tóm tắt: Kết luận | 11/12/2025 | 11/12/2025      | <https://000039.awsstudygroup.com/> |
| 5   | - **LGME: Mô hình hóa dữ liệu Game Player với Amazon DynamoDB:** <br>&emsp; + Bắt đầu <br>&emsp; + Lập kế hoạch mô hình dữ liệu (Best Practices, Entity-Relationship Diagram, Access Patterns) <br>&emsp; + Sử dụng cốt lõi: hồ sơ người dùng và games (Thiết kế primary key, Truy xuất item collections) <br>&emsp; + Tạo bảng và bulk-load dữ liệu <br>&emsp; + Tìm games đang mở (Mô hình sparse GSI, Tạo sparse GSI, Query và Scan sparse GSI) | 11/13/2025 | 11/13/2025      | <https://000039.awsstudygroup.com/> |
| 6   | - **LGME Tiếp tục: Các thao tác Game nâng cao:** <br>&emsp; + Tham gia và đóng games (Thêm users vào game, Bắt đầu game) <br>&emsp; + Xem games đã qua (Thêm inverted index, Truy xuất games cho user) <br>&emsp; + Tóm tắt & Dọn dẹp <br>- **LDC: Thử thách thiết kế:** <br>&emsp; + Kịch bản Retail Cart với References <br>&emsp; + Kịch bản Bank Payments với References <br>&emsp; + NoSQL Design: Tài liệu tham khảo | 11/14/2025 | 11/14/2025      | <https://000039.awsstudygroup.com/> |


### Thành tựu tuần 10:

* **Thành thạo các khái niệm cơ bản và nâng cao toàn diện của Amazon DynamoDB:**
  * Nguyên lý cơ sở dữ liệu NoSQL và kiến trúc DynamoDB
  * Tạo bảng, mô hình hóa dữ liệu và thiết kế primary key
  * Các thao tác CLI và Console (CRUD, Query, Scan, Transactions)
  * Chiến lược sao lưu (Point-In-Time Recovery, On-Demand, Scheduled)
  * Migration cơ sở dữ liệu từ hệ thống quan hệ sử dụng DMS

* **Triển khai các mẫu thiết kế nâng cao và kỹ thuật tối ưu hóa DynamoDB:**
  * Global Secondary Indexes (GSI) bao gồm sparse, write sharding và key overloading
  * Composite keys cho các mẫu truy vấn phức tạp
  * Adjacency lists cho mối quan hệ dữ liệu phân cấp
  * Capacity units, phân vùng và tối ưu hóa hiệu suất
  * Sequential và parallel table scans

* **Xây dựng giải pháp xử lý dữ liệu thời gian thực và tích hợp:**
  * DynamoDB Streams cho change data capture
  * Tích hợp Kinesis Data Streams cho xử lý khối lượng lớn
  * Các hàm Lambda cho kiến trúc hướng sự kiện
  * Tích hợp Zero-ETL với OpenSearch và Amazon Bedrock cho ứng dụng AI

* **Phát triển ứng dụng serverless với phân phối toàn cầu:**
  * Global Tables cho triển khai đa vùng
  * Kiến trúc serverless hướng sự kiện với khả năng chịu lỗi
  * Các mẫu xử lý exactly-once và idempotency
  * Triển khai ứng dụng serverless toàn cầu (Globalflix)

* **Áp dụng DynamoDB vào các kịch bản thực tế:**
  * Mô hình hóa dữ liệu game player với hệ thống matchmaking
  * Các mẫu dữ liệu retail cart và e-commerce
  * Hệ thống thanh toán ngân hàng và dịch vụ tài chính
  * Inverted indexes nâng cao cho truy vấn phức tạp

* **Đạt được chuyên môn trong các thử thách thiết kế NoSQL cấp doanh nghiệp:**
  * Best practices mô hình hóa dữ liệu cho hệ thống NoSQL
  * Tối ưu hóa hiệu suất và quản lý chi phí
  * Các mẫu tích hợp với các dịch vụ AWS khác
  * Thử thách thiết kế cho ứng dụng bán lẻ và tài chính
