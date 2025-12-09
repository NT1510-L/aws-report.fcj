---
title: "Sử dụng AWS FIS để kiểm tra khả năng chịu lỗi của Cassandra tự quản lý"
date: "2025-06-25"
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# Sử dụng AWS FIS để kiểm tra khả năng chịu lỗi của Cassandra tự quản lý

**Tác giả:** Hans Nesbitt và Lwanga Phillip | **Ngày đăng:** 25 tháng 6, 2025 | **Chủ đề:** Amazon EC2, AWS Fault Injection Service (FIS), Database, Resilience

## Giới thiệu

Các sự cố ngừng hoạt động của cơ sở dữ liệu có thể gây tác động nghiêm trọng đến ứng dụng và hoạt động kinh doanh của bạn. Đối với các nhóm đang vận hành cụm Apache Cassandra tự quản lý, các sự cố bất ngờ như lỗi nút hoặc vấn đề bộ nhớ có thể dẫn đến giảm hiệu năng dịch vụ, mất nhất quán dữ liệu hoặc thậm chí ngừng hệ thống hoàn toàn.

Vậy làm thế nào để bạn đảm bảo cụm Cassandra của mình vẫn hoạt động ổn định khi sự cố xảy ra?

AWS Fault Injection Service (AWS FIS) là một dịch vụ được quản lý cho phép bạn thực hiện các thí nghiệm tiêm lỗi (fault injection) trên khối lượng công việc của mình trong AWS. Tiêm lỗi dựa trên các nguyên tắc của chaos engineering, trong đó bạn cố tình tạo ra các sự cố có kiểm soát để quan sát cách ứng dụng phản ứng, từ đó cải thiện độ tin cậy và hiệu năng của hệ thống.

Cassandra là một cơ sở dữ liệu NoSQL phổ biến, có hiệu năng cao. AWS cung cấp nhiều cách để chạy Cassandra trên nền tảng của mình — từ Amazon Keyspaces (for Apache Cassandra), một dịch vụ cơ sở dữ liệu serverless, có khả năng mở rộng và sẵn sàng cao, đến việc tự triển khai Cassandra trên Amazon EC2.

Trong bài viết này, chúng ta sẽ cùng xem cách sử dụng AWS FIS để tạo một thí nghiệm chaos nhằm kiểm tra khả năng chịu lỗi của cụm Cassandra tự quản lý chạy trên Amazon EC2. Thí nghiệm này giúp bạn hiểu rõ khả năng ứng dụng tự động kết nối lại với các nút khỏe mạnh trong trường hợp có sự cố.

## Tổng quan giải pháp

Giả sử bạn là thành viên trong một nhóm chịu trách nhiệm kiểm tra độ ổn định của ứng dụng. Trước đây, một sự cố bộ nhớ đã phát hiện ra lỗi cấu hình trong cơ chế retry và backoff của ứng dụng. Bây giờ, nhóm cần xác nhận rằng phiên bản mới đã cải thiện khả năng chịu lỗi của thành phần này.

Như minh họa dưới đây, nhóm có một cụm Cassandra gồm sáu nút, phân bố trên ba Availability Zone trong cùng một vùng AWS. Cụm có Replication Factor (RF) = 3, nghĩa là dữ liệu sẽ được lưu trên ba nút khác nhau. Do đặc tính của Cassandra, mọi nút đều có thể xử lý yêu cầu đọc/ghi. Do đó, việc mất một nút không nên ảnh hưởng đến tính khả dụng của dịch vụ, vì ít nhất hai bản sao dữ liệu vẫn tồn tại.

## Giả thuyết thí nghiệm

Trong cụm Cassandra 6 nút với RF = 3, việc gián đoạn một nút sẽ không ảnh hưởng đến tính khả dụng. Một phản hồi thành công yêu cầu hai trong ba bản sao phản hồi. Cụm vẫn đảm bảo tính nhất quán dữ liệu trên năm nút còn lại, và độ trễ p99 dưới 100 ms.

Khi một nút bị gián đoạn, các yêu cầu từ client có thể vẫn được xử lý thành công bởi hai nút còn lại. Dữ liệu vẫn khả dụng vì có hai bản sao đầy đủ tồn tại.

Thí nghiệm sẽ xác định tài nguyên mục tiêu bằng cách dùng tag, như mô tả trong các phần sau.

## Điều kiện tiên quyết

Trước khi chạy thí nghiệm, hãy đảm bảo rằng bạn đã:

- Cấu hình AWS Identity and Access Management (IAM) với quyền cần thiết.
- Có hệ thống giám sát (monitoring) để theo dõi cụm Cassandra.
- Có kế hoạch khôi phục (rollback) nếu thí nghiệm gây ra sự cố.

## Cấu hình thí nghiệm

Để định vị các tài nguyên trong cụm, ta sẽ sử dụng tag AWS. Ví dụ: các EC2 instance trong cụm được gắn tag:

- **Cluster-Name:** Cassandra-Cluster1
- **Chaos-Ready:** True

### Các bước cấu hình AWS FIS

1. Truy cập AWS FIS Console, chọn **Create experiment template**.
2. Nhập tên, mô tả, chọn tài khoản AWS chứa tài nguyên, sau đó nhấn **Next**.
3. Với **Target method**, chọn **Resource tags, filters and parameters**, rồi thêm các tag ở trên.
4. Sử dụng chế độ **COUNT(1)** để chỉ chọn một instance.

```json
"targets": {
   "Instances-Target-1": { 
      "resourceType": "aws:ec2:instance", 
      "resourceTags": { 
           "Chaos-Ready": "True", 
           "Cluster-Name": "Cassandra-Cluster1" 
      }, 
      "selectionMode": "COUNT(1)" 
     }
}
```

**Giải thích:**
- **resourceType:** chỉ định mục tiêu là EC2 instance.
- **resourceTags:** xác định instance có tag tương ứng.
- **selectionMode:** chọn ngẫu nhiên một instance phù hợp.

Tiếp theo, trong phần **Action**, đặt **actionId** là **aws:ssm:send-command**. Điền các tham số: Document ARN, Document parameters, Document version và Duration. Sử dụng tài liệu **AWSFIS-Run-Memory-Stress**, công cụ này sẽ tạo tải bộ nhớ trên instance bằng stress-ng, mô phỏng tình huống rò rỉ bộ nhớ.

```json
"actions": {                  
    "Cassandra-Node-Mem-Stress": { 
        "actionId": "aws:ssm:send-command", 
        "parameters": {  
             "documentArn": "arn:aws:ssm:us-west-2::document/AWSFIS-Run-Memory-Stress", 
             "documentParameters": "{
                \"Percent\":\"100\", 
                \"DurationSeconds\":\"900\", 
                \"InstallDependencies\":\"True\"
             }",  
             "duration": "PT15M" }, 
        "targets": { 
            "Instances": "Instances-Target-1" 
         } 
    } 
}
```

**Giải thích:**
- **actionId:** sử dụng Systems Manager để thực thi lệnh.
- **documentParameters:** tạo tải 100% bộ nhớ trong 900 giây (15 phút).
- **duration:** đảm bảo thí nghiệm dừng sau 15 phút.

Sau khi cấu hình, bạn có thể bắt đầu thí nghiệm từ AWS FIS Console hoặc AWS CLI. Trong suốt quá trình, hãy giám sát hiệu năng ứng dụng và cụm Cassandra.

## Tiến hành thử nghiệm

Bạn có thể thực thi thí nghiệm bằng Console, CLI hoặc API. Sau khi khởi chạy, AWS FIS sẽ lọc các instance theo tag, chọn mục tiêu và bắt đầu tạo lỗi.

Khi một nút bị ảnh hưởng, hiệu năng đọc/ghi sẽ bắt đầu giảm hoặc tạm ngừng.

## Giám sát

Giám sát là yếu tố cốt lõi của chaos engineering — bạn phải quan sát rõ tác động của lỗi. Nên đảm bảo hệ thống đang chịu tải ổn định trước khi thử nghiệm.

**Các chỉ số quan trọng cần theo dõi:**
- **Hiệu năng ứng dụng:** độ trễ (p99, p95, p50), tỷ lệ lỗi, throughput.
- **Trạng thái cụm Cassandra:** node status, latency đọc/ghi, consistency level.
- **Hạ tầng:** CPU, bộ nhớ, và kết nối mạng.

Bạn có thể dùng Amazon CloudWatch để:
- Tạo dashboard tổng hợp EC2 và ứng dụng.
- Cài đặt cảnh báo (alarms) khi vượt ngưỡng.
- Phân tích log thời gian thực bằng CloudWatch Logs Insights.
- So sánh hiệu năng giữa các node bằng Metrics Explorer.
- Và tích hợp AWS FIS + CloudWatch để tự động dừng thí nghiệm nếu vi phạm điều kiện an toàn.

## Kết nối Cassandra

Trong Cassandra, connection pooling giúp ứng dụng duy trì nhiều kết nối song song đến các node khác nhau trong cụm. Khi một node ngừng phản hồi, ứng dụng có thể chuyển sang node khác nhanh chóng, giảm thời gian failover và duy trì hiệu năng ổn định.

**Để triển khai hiệu quả connection pooling:**
- Cấu hình kích thước pool dựa trên số lượng yêu cầu đồng thời.
- Dùng load balancing policies phù hợp.
- Giám sát mức sử dụng pool, quản lý vòng đời kết nối, và áp dụng exponential backoff.

Nhờ connection pooling, khi node bị lỗi, các server có thể chuyển kết nối sang node khác, như minh họa bên dưới.

Sau khi node bị lỗi khôi phục, nó sẽ trở lại với dữ liệu cũ. Để đảm bảo tính nhất quán, cần chạy quá trình repair để đồng bộ dữ liệu bị thay đổi trong thời gian downtime.

- Nếu **downtime < 3 giờ** (mặc định hinted handoff window), Cassandra sẽ tự động xử lý qua hinted handoff.
- Nếu **downtime > 3 giờ**, cần bootstrapping hoặc repair thủ công.

Sau khi hoàn tất, node được đưa trở lại connection pool, và ứng dụng có thể dần chuyển traffic về node đó.

## Kết luận

Kiểm tra khả năng chịu lỗi của hệ thống phân tán như Cassandra là bước thiết yếu để duy trì độ tin cậy trong môi trường production.

Sử dụng AWS FIS, bạn có thể mô phỏng lỗi từng phần (như lỗi bộ nhớ) để xác minh hành vi hệ thống. Thí nghiệm giúp kiểm tra cơ chế retry của ứng dụng, đồng thời cung cấp thông tin giá trị về cách Cassandra phản ứng khi bị stress.

Chaos engineering không phải là hoạt động làm một lần, mà là quy trình lặp lại liên tục, giúp nhóm kỹ thuật xây dựng hệ thống bền vững hơn. Với công cụ như AWS FIS, doanh nghiệp có thể xác thực và cải tiến kiến trúc hệ thống để phục vụ khách hàng tốt hơn.

## Tài nguyên tham khảo

- [AWS FIS sample repository](https://github.com/aws-samples/aws-fault-injection-service-samples)
- [Best Practices for Running Apache Cassandra on Amazon EC2](https://docs.aws.amazon.com/ec2/latest/userguide/cassandra-best-practices.html)
- [Retry with backoff pattern](https://docs.aws.amazon.com/architecture/latest/reliability-pillar/retry-pattern.html)

## Thông tin tác giả

**Hans Nesbitt**  
Senior Solutions Architect tại AWS (California). Làm việc với khách hàng khắp Bắc Mỹ để xây dựng kiến trúc cloud có khả năng mở rộng và linh hoạt. Ngoài công việc, anh yêu thích nấu ăn, chơi guitar và dành thời gian cho gia đình.

**Lwanga Phillip**  
Senior Solutions Architect tại AWS Strategic Accounts. Hỗ trợ khách hàng doanh nghiệp triển khai hiệu quả dịch vụ AWS cho migration & modernization. Ngoài công việc, anh thích leo núi và du lịch cùng gia đình.

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
