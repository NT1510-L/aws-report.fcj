   ---
title: "Nâng cấp Amazon RDS với AWS Graviton4: Kết quả benchmark"
date: "2025-06-27"
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# Nâng cấp Amazon RDS với AWS Graviton4: Kết quả benchmark

**Tác giả:** Angel Duenas | **Ngày đăng:** 27 tháng 6 năm 2025 | **Chủ đề:** Amazon RDS, Graviton, RDS for PostgreSQL, Technical How-to

## Giới thiệu

Vào tháng 11 năm 2024, AWS đã giới thiệu thế hệ tiếp theo của bộ vi xử lý ARM tùy chỉnh – **AWS Graviton4**, mang lại hiệu suất và hiệu quả năng lượng vượt trội cho Amazon Relational Database Service (Amazon RDS) với các engine PostgreSQL, MySQL, MariaDB và Amazon Aurora (tương thích với cả PostgreSQL và MySQL).

Được xây dựng trên hệ thống AWS Nitro và sử dụng bộ nhớ DDR5 mới nhất, Graviton4 cung cấp:

- **Hiệu suất tăng tới 40%**
- **Hiệu quả chi phí trên hiệu năng tăng tới 29%** so với thế hệ Graviton3

Ra mắt cùng thời điểm là các họ instance M8g và R8g, với kích thước lớn nhất lên đến 48xlarge, cung cấp tối đa 192 vCPU. Những cải tiến này cho phép khách hàng xử lý khối lượng công việc nặng hơn, đồng thời tối ưu chi phí.

Trong bài viết này, chúng ta sẽ tập trung vào **Amazon RDS for PostgreSQL**, và so sánh hiệu năng giữa Graviton4 với các thế hệ Graviton3 và Graviton2. Các phép benchmark được sử dụng để đánh giá throughput (lưu lượng xử lý), latency (độ trễ) và hiệu năng trên chi phí, minh họa rõ ưu thế của Graviton4 cho các workload cơ sở dữ liệu hiện đại.

## Thiết lập benchmark

Chúng tôi sử dụng công cụ **Sysbench** – một công cụ benchmark đa luồng – để so sánh hiệu suất giữa:

- Graviton2 (m6g)
- Graviton3 (m7g)
- Graviton4 (m8g)

Thử nghiệm được tiến hành trên Amazon RDS trong khu vực us-east-1, với mô hình triển khai một Availability Zone nhằm giảm độ trễ. Một instance Amazon EC2 m7g.4xlarge được dùng để chạy Sysbench, đảm bảo không bị giới hạn bởi CPU, bộ nhớ, hoặc băng thông mạng, phản ánh chính xác tải thực tế.

### Phiên bản cơ sở dữ liệu và cấu hình instance

Chúng tôi thực hiện thử nghiệm trên Amazon RDS for PostgreSQL phiên bản 16.3, sử dụng ba loại instance để so sánh ba thế hệ Graviton:

| Instance class | Processor | vCPUs | Memory (GiB) | EBS Bandwidth (Gbps) | Network (Gbps) |
| --- | --- | --- | --- | --- | --- |
| db.m6g.xlarge | Graviton2 | 4 | 16 | Up to 4.75 | Up to 10 |
| db.m7g.xlarge | Graviton3 | 4 | 16 | Up to 10 | Up to 12.5 |
| db.m8g.xlarge | Graviton4 | 4 | 16 | Up to 10 | Up to 12.5 |

Để đảm bảo kết quả chính xác và nhất quán, chúng tôi điều chỉnh như sau:

- **Storage:** Sử dụng Amazon EBS io2 với 10.000 IOPS và dung lượng 200 GB, tránh nghẽn cổ chai lưu trữ.
- **Độ trễ:** Tất cả thử nghiệm đều thực hiện trong cùng một Availability Zone với instance EC2.

Cấu hình này giúp đánh giá khách quan hiệu năng mà Graviton4 mang lại cho các workload của Amazon RDS.

## Tái tạo môi trường benchmark

Để đơn giản hóa việc triển khai, chúng tôi đã tạo một mẫu AWS CloudFormation tự động hóa việc tạo toàn bộ môi trường thử nghiệm, bao gồm cơ sở dữ liệu RDS cho PostgreSQL, phiên bản EC2 và các cấu hình cần thiết. **Tải xuống mẫu.**

### Ngăn xếp CloudFormation thiết lập:

- Một phiên bản RDS DB chạy PostgreSQL 16.3
- Một phiên bản EC2 được cấu hình sẵn với Sysbench để chạy các bài kiểm tra
- Cấu hình mạng phù hợp để cho phép kết nối liền mạch giữa các phiên bản

Sau khi các tài nguyên đã được triển khai bằng mẫu CloudFormation, hãy sử dụng URL Trình quản lý Phiên từ các đầu ra của mẫu để kết nối với phiên bản EC2 và làm theo các bước trong các phần tiếp theo để chuẩn bị và thực hiện bài kiểm tra hiệu suất.

Mặc dù bài viết này tập trung vào Amazon RDS cho PostgreSQL, mẫu CloudFormation cũng hỗ trợ MySQL và MariaDB. Bạn có thể dễ dàng chạy cùng một quy trình đánh giá chuẩn cho các công cụ này bằng cách chọn tùy chọn phù hợp khi khởi chạy ngăn xếp.

## Chuẩn bị thử nghiệm

Lệnh prepare trong Sysbench sẽ tạo và điền dữ liệu vào các bảng sbtest1 và sbtest2, mỗi bảng có 2 triệu bản ghi, với các cột được đánh chỉ mục để mô phỏng môi trường giao dịch thực tế.

- **Số bảng:** 2
- **Dữ liệu:** 2.000.000 bản ghi mỗi bảng
- **Script:** oltp_read_write.lua

```bash
sysbench /usr/sysbench/src/lua/oltp_read_write.lua \
--pgsql-host=<pgsql-host> --db-driver=pgsql --pgsql-user=postgres \
--pgsql-password='<pgsql-password>' --pgsql-port=5432 --pgsql-db=sbtest \
--tables=2 --table-size=2000000 prepare
```

## Chạy benchmark

Lệnh run sẽ khởi động thử nghiệm, chạy các truy vấn OLTP đọc/ghi hỗn hợp trên các bảng đã chuẩn bị.

- **Thời lượng:** 30 phút (1800 giây)
- **Đồng thời:** 100 luồng (threads)
- **Báo cáo:** mỗi 10 giây
- **Workload:** oltp_read_write.lua

```bash
sysbench /usr/sysbench/src/lua/oltp_read_write.lua --threads=100 \
--time=1800 --report-interval=10 --pgsql-host=<host> --db-driver=pgsql \
--pgsql-user=postgres --pgsql-password='<password>' \
--pgsql-port=5432 --pgsql-db=sbtest --tables=2 \
--table-size=2000000 run
```

## Kết quả hiệu năng

Trong các thử nghiệm của chúng tôi, các phiên bản dựa trên AWS Graviton4 (m8g) cho thấy sự cải thiện hiệu suất đáng kể và nhất quán so với Graviton3 (m7g) và Graviton2 (m6g) đối với Amazon RDS chạy khối lượng công việc PostgreSQL.

Khi so sánh số truy vấn mỗi giây (QPS), các phiên bản m8g vượt trội hơn cả hai thế hệ trước, như thể hiện trong hình sau.

- **m8g tăng 23%** số truy vấn/giây so với m7g.
- **So với m6g, m8g tăng 41%**.
- **m7g vượt m6g 15%**.

## Độ trễ (Latency)

Các bài kiểm tra độ trễ cho thấy xu hướng cải thiện tương tự với Graviton4. Trong bối cảnh các bài kiểm tra chuẩn của chúng tôi, độ trễ phản ánh thời gian từ đầu đến cuối mà máy khách Sysbench ghi nhận được cho mỗi truy vấn, bao gồm cả thời gian xử lý cơ sở dữ liệu và bất kỳ độ trễ mạng nào giữa máy khách và cơ sở dữ liệu. Sysbench báo cáo độ trễ là thời gian phản hồi trung bình cho mỗi truy vấn tính bằng mili giây. Kết quả chứng minh rằng các phiên bản dựa trên Graviton4 liên tục giảm thời gian phản hồi truy vấn so với cả phiên bản dựa trên Graviton3 và Graviton2, cho thấy hiệu quả được cải thiện trong việc xử lý khối lượng công việc cơ sở dữ liệu:

- **m8g giảm 19%** độ trễ so với m7g.
- **So với m6g, m8g giảm 29%**.
- **m7g cải thiện 13%** so với m6g.

## Phân tích hiệu năng trên chi phí

Các instance Graviton4 có giá thấp hơn một chút so với Graviton3, giúp tăng hiệu năng trên mỗi đô-la. Bảng sau tóm tắt chi phí hàng tháng và theo giờ (tại khu vực N. Virginia):

| Instance type | Monthly (USD) | Hourly (USD) |
| --- | --- | --- |
| db.m6g.xlarge (Graviton2) | 232.14 | 0.322 |
| db.m7g.xlarge (Graviton3) | 246.01 | 0.342 |
| db.m8g.xlarge (Graviton4) | 245.28 | 0.341 |

- **m8g xử lý nhiều hơn 23%** truy vấn mỗi đô-la so với m7g, và **34% so với m6g**.
- **m7g hơn m6g 9%**.

Như vậy, **Graviton4 cung cấp hiệu năng/chi phí tốt nhất** cho Amazon RDS for PostgreSQL trong các thử nghiệm này.

## Dọn dẹp môi trường

Sau khi hoàn tất thử nghiệm và lưu kết quả, hãy xóa stack CloudFormation để tránh phát sinh chi phí. Việc này sẽ tự động xóa RDS instance, EC2 instance, và các cấu hình liên quan.

## Kết luận

Đối với người dùng Amazon RDS, các instance dựa trên Graviton4 là lựa chọn hấp dẫn để chạy workload cơ sở dữ liệu quan hệ.

Trong các thử nghiệm của chúng tôi:

- **Graviton4 tăng 41% throughput** so với Graviton2,
- **Tăng 23%** so với Graviton3,
- **Cải thiện 34% hiệu năng/chi phí** so với Graviton2,
- **Và 23%** so với Graviton3.

Kết quả thực tế có thể thay đổi tùy theo workload, nhưng như đã công bố, Graviton4 mang lại tới **40% hiệu năng cao hơn** và **29% hiệu quả chi phí** hơn so với Graviton3.

### Hỗ trợ Graviton4:

**Các dịch vụ RDS hỗ trợ:**
- Amazon RDS for PostgreSQL, MySQL, MariaDB

**Phiên bản PostgreSQL:** 17.1+, 16.1+, 15.2+, 14.5+, 13.8+  
**MySQL:** 8.0.32+  
**MariaDB:** 11.4.3+, 10.11.7+, 10.6.13+, 10.5.20+, 10.4.29+

**Khả dụng tại các khu vực:**
- US East (N. Virginia, Ohio)
- US West (Oregon)
- Europe (Frankfurt, Ireland)
- AWS GovCloud (US-West)

### Tham khảo thêm:
- [Amazon RDS Pricing Page](https://aws.amazon.com/rds/pricing/)
- [Amazon RDS Documentation](https://docs.aws.amazon.com/rds/)

## Về tác giả

**Angel Duenas** – Angel là Technical Account Manager tại AWS, chuyên về Amazon RDS và Aurora. Anh hỗ trợ khách hàng tối ưu workload trên AWS bằng thực hành tốt nhất (best practices) và giải pháp sáng tạo. Angel có nền tảng kỹ thuật vững vàng về các hệ quản trị cơ sở dữ liệu quan hệ và phi quan hệ.

Các data lake có thể giúp các bệnh viện và cơ sở y tế chuyển dữ liệu thành những thông tin chi tiết về doanh nghiệp và duy trì hoạt động kinh doanh liên tục, đồng thời bảo vệ quyền riêng tư của bệnh nhân. **Data lake** là một kho lưu trữ tập trung, được quản lý và bảo mật để lưu trữ tất cả dữ liệu của bạn, cả ở dạng ban đầu và đã xử lý để phân tích. data lake cho phép bạn chia nhỏ các kho chứa dữ liệu và kết hợp các loại phân tích khác nhau để có được thông tin chi tiết và đưa ra các quyết định kinh doanh tốt hơn.

Bài đăng trên blog này là một phần của loạt bài lớn hơn về việc bắt đầu cài đặt data lake dành cho lĩnh vực y tế. Trong bài đăng blog cuối cùng của tôi trong loạt bài, *“Bắt đầu với data lake dành cho lĩnh vực y tế: Đào sâu vào Amazon Cognito”*, tôi tập trung vào các chi tiết cụ thể của việc sử dụng Amazon Cognito và Attribute Based Access Control (ABAC) để xác thực và ủy quyền người dùng trong giải pháp data lake y tế. Trong blog này, tôi trình bày chi tiết cách giải pháp đã phát triển ở cấp độ cơ bản, bao gồm các quyết định thiết kế mà tôi đã đưa ra và các tính năng bổ sung được sử dụng. Bạn có thể truy cập các code samples cho giải pháp tại Git repo này để tham khảo.

---

## Hướng dẫn kiến trúc

Thay đổi chính kể từ lần trình bày cuối cùng của kiến trúc tổng thể là việc tách dịch vụ đơn lẻ thành một tập hợp các dịch vụ nhỏ để cải thiện khả năng bảo trì và tính linh hoạt. Việc tích hợp một lượng lớn dữ liệu y tế khác nhau thường yêu cầu các trình kết nối chuyên biệt cho từng định dạng; bằng cách giữ chúng được đóng gói riêng biệt với microservices, chúng ta có thể thêm, xóa và sửa đổi từng trình kết nối mà không ảnh hưởng đến những kết nối khác. Các microservices được kết nối rời thông qua tin nhắn publish/subscribe tập trung trong cái mà tôi gọi là “pub/sub hub”.

Giải pháp này đại diện cho những gì tôi sẽ coi là một lần lặp nước rút hợp lý khác từ last post của tôi. Phạm vi vẫn được giới hạn trong việc nhập và phân tích cú pháp đơn giản của các **HL7v2 messages** được định dạng theo **Quy tắc mã hóa 7 (ER7)** thông qua giao diện REST.

**Kiến trúc giải pháp bây giờ như sau:**

> *Hình 1. Kiến trúc tổng thể; những ô màu thể hiện những dịch vụ riêng biệt.*

---

Mặc dù thuật ngữ *microservices* có một số sự mơ hồ cố hữu, một số đặc điểm là chung:  
- Chúng nhỏ, tự chủ, kết hợp rời rạc  
- Có thể tái sử dụng, giao tiếp thông qua giao diện được xác định rõ  
- Chuyên biệt để giải quyết một việc  
- Thường được triển khai trong **event-driven architecture**

Khi xác định vị trí tạo ranh giới giữa các microservices, cần cân nhắc:  
- **Nội tại**: công nghệ được sử dụng, hiệu suất, độ tin cậy, khả năng mở rộng  
- **Bên ngoài**: chức năng phụ thuộc, tần suất thay đổi, khả năng tái sử dụng  
- **Con người**: quyền sở hữu nhóm, quản lý *cognitive load*

---

## Lựa chọn công nghệ và phạm vi giao tiếp

| Phạm vi giao tiếp                        | Các công nghệ / mô hình cần xem xét                                                        |
| ---------------------------------------- | ------------------------------------------------------------------------------------------ |
| Trong một microservice                   | Amazon Simple Queue Service (Amazon SQS), AWS Step Functions                               |
| Giữa các microservices trong một dịch vụ | AWS CloudFormation cross-stack references, Amazon Simple Notification Service (Amazon SNS) |
| Giữa các dịch vụ                         | Amazon EventBridge, AWS Cloud Map, Amazon API Gateway                                      |

---

## The pub/sub hub

Việc sử dụng kiến trúc **hub-and-spoke** (hay message broker) hoạt động tốt với một số lượng nhỏ các microservices liên quan chặt chẽ.  
- Mỗi microservice chỉ phụ thuộc vào *hub*  
- Kết nối giữa các microservice chỉ giới hạn ở nội dung của message được xuất  
- Giảm số lượng synchronous calls vì pub/sub là *push* không đồng bộ một chiều

Nhược điểm: cần **phối hợp và giám sát** để tránh microservice xử lý nhầm message.

---

## Core microservice

Cung cấp dữ liệu nền tảng và lớp truyền thông, gồm:  
- **Amazon S3** bucket cho dữ liệu  
- **Amazon DynamoDB** cho danh mục dữ liệu  
- **AWS Lambda** để ghi message vào data lake và danh mục  
- **Amazon SNS** topic làm *hub*  
- **Amazon S3** bucket cho artifacts như mã Lambda

> Chỉ cho phép truy cập ghi gián tiếp vào data lake qua hàm Lambda → đảm bảo nhất quán.

---

## Front door microservice

- Cung cấp API Gateway để tương tác REST bên ngoài  
- Xác thực & ủy quyền dựa trên **OIDC** thông qua **Amazon Cognito**  
- Cơ chế *deduplication* tự quản lý bằng DynamoDB thay vì SNS FIFO vì:
  1. SNS deduplication TTL chỉ 5 phút
  2. SNS FIFO yêu cầu SQS FIFO
  3. Chủ động báo cho sender biết message là bản sao

---

## Staging ER7 microservice

- Lambda “trigger” đăng ký với pub/sub hub, lọc message theo attribute  
- Step Functions Express Workflow để chuyển ER7 → JSON  
- Hai Lambda:
  1. Sửa format ER7 (newline, carriage return)
  2. Parsing logic  
- Kết quả hoặc lỗi được đẩy lại vào pub/sub hub

---

## Tính năng mới trong giải pháp

### 1. AWS CloudFormation cross-stack references
Ví dụ *outputs* trong core microservice:
```yaml
Outputs:
  Bucket:
    Value: !Ref Bucket
    Export:
      Name: !Sub ${AWS::StackName}-Bucket
  ArtifactBucket:
    Value: !Ref ArtifactBucket
    Export:
      Name: !Sub ${AWS::StackName}-ArtifactBucket
  Topic:
    Value: !Ref Topic
    Export:
      Name: !Sub ${AWS::StackName}-Topic
  Catalog:
    Value: !Ref Catalog
    Export:
      Name: !Sub ${AWS::StackName}-Catalog
  CatalogArn:
    Value: !GetAtt Catalog.Arn
    Export:
      Name: !Sub ${AWS::StackName}-CatalogArn
