---
title: "Blog 1"
date: "2025-06-26"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---
# Chạy đua với thời gian: SRO Motorsports đã cắt giảm 83% thời gian kiểm tra bằng AWS như thế nào

**Tác giả:** Ryan Kiel và Steven Miller | **Ngày đăng:** 26 tháng 6 năm 2025 | **Chủ đề:** Amazon EC2, Amazon QuickSight, Amazon Simple Storage Service (S3), Analytics, AWS Lambda, Compute, Customer Solutions, Data Science & Analytics for Media, Industries, Media & Entertainment, Storage

## Giới thiệu

Trong thế giới tốc độ cao của đua xe, sự chính xác và công bằng là điều không thể thỏa hiệp. SRO Motorsports America (SRO), tổ chức đứng sau giải GT World Challenge America, đã hợp tác với Amazon Web Services (AWS) Professional Services để cách mạng hóa cách kiểm tra tuân thủ của xe đua — biến một quy trình thủ công 90 phút thành hệ thống tự động chỉ mất chưa đến 15 phút. Sự hợp tác này không chỉ hợp lý hóa hoạt động của giải đua mà còn đặt nền móng cho việc áp dụng Balance of Performance (BoP) dựa trên dữ liệu trong tương lai bằng machine learning.

## Cho phép độ chính xác theo dõi với AWS Cloud

Quy trình kiểm tra kỹ thuật đảm bảo rằng mỗi chiếc xe đua — dù là Toyota, BMW, Hyundai hay Acura — đều tuân thủ nghiêm ngặt các quy định kỹ thuật về thi đấu và an toàn. Trước khi làm việc với AWS, các nhân viên kỹ thuật của SRO mất tới 90 phút để xử lý thủ công dữ liệu xe được ghi lại từ các hệ thống gắn trên xe, tạo ra nút thắt trong vận hành trong những ngày cuối tuần đua vốn đã căng thẳng và gấp rút.

Hệ thống kiểm tra kỹ thuật mới được AWS hỗ trợ đã tự động hóa việc xử lý dữ liệu xe thông qua một pipeline xử lý dữ liệu tinh vi, thực hiện 102 lần kiểm tra tuân thủ khác nhau. Các vấn đề tiềm ẩn được đánh dấu thông qua dashboard trực quan, giúp các nhân viên kỹ thuật có thể nhanh chóng phát hiện vi phạm.

> "Làm việc với AWS đã thay đổi hoàn toàn cách chúng tôi tiếp cận việc tuân thủ kỹ thuật trong giải Touring Car," – Greg Gill, Chủ tịch kiêm CEO của SRO Motorsports America. "Những gì trước đây là một quy trình thủ công, tốn thời gian, giờ đây đã trở nên hợp lý, chính xác và dựa trên dữ liệu — cho phép đội ngũ kỹ thuật tập trung vào điều quan trọng nhất: sự công bằng trong thi đấu và trải nghiệm đua xe tuyệt vời."

Đằng sau sự thay đổi này là một kiến trúc AWS Cloud mạnh mẽ, được thiết kế để đảm bảo độ tin cậy, khả năng mở rộng và hiệu suất, đặc biệt quan trọng trong môi trường đầy thách thức của một ngày đua:

1. **Thiết bị Edge Trackside:** Hệ thống bắt đầu từ thiết bị edge trackside, thu thập dữ liệu từ xe đua.
2. **Amazon S3:** Dữ liệu được đưa vào Amazon S3, kích hoạt pipeline xử lý tự động.
3. **Amazon EC2:** EC2 xử lý các tác vụ chuyển đổi file chuyên biệt.
4. **AWS Lambda:** Lambda phân tích dữ liệu đã giải mã theo quy định kỹ thuật.
5. **Amazon QuickSight:** Cuối cùng, QuickSight hiển thị dashboard tương tác để nhân viên kỹ thuật sử dụng.

Cải tiến này đã được chứng minh trong điều kiện thực tế tại Sebring International Raceway, nơi hệ thống xử lý dữ liệu từ nhiều xe với tốc độ và độ chính xác chưa từng có. Nhờ vậy, nhân viên kỹ thuật có thể tập trung phân tích chuyên sâu thay vì chỉ xử lý dữ liệu lặp lại.

> "Việc giảm 83% thời gian kiểm tra kỹ thuật cực kỳ có giá trị đối với vận hành giải đua," Gill chia sẻ. "Những gì trước đây mất 90 phút, giờ đây đội kỹ thuật chỉ cần chưa đến 15 phút. Hiệu quả này không chỉ cải thiện trải nghiệm cho các đội đua mà còn cho phép chúng tôi phân bổ nguồn lực để nâng cao các khía cạnh khác của cuối tuần đua."

## Machine Learning thúc đẩy sự công bằng trong thi đấu

Trong các giải đua đa thương hiệu, những nhà sản xuất khác nhau mang đến các xe có đặc điểm kỹ thuật vốn dĩ khác nhau. Hệ thống BoP (Balance of Performance) là công cụ cân bằng để đảm bảo sự công bằng. BoP có thể bao gồm việc thêm ballast (trọng lượng), hạn chế công suất động cơ hoặc điều chỉnh khí động học. Điều này tạo ra một sân chơi công bằng, nơi kỹ năng của tay đua mới là yếu tố quyết định, chứ không phải sự khác biệt của nhà sản xuất.

SRO Motorsports và AWS đã phát triển một cách tiếp cận machine learning (ML) tiên tiến cho BoP, hứa hẹn cách mạng hóa khía cạnh quan trọng này của đua xe. AWS Professional Services đã xây dựng và huấn luyện các mô hình ML nâng cao, có khả năng dự đoán thời gian vòng đua dựa trên kỹ năng tay đua, đặc điểm đường đua, thông số khí động học và ballast hiệu suất.

> "Khả năng BoP dựa trên machine learning mà chúng tôi xây dựng với AWS chính là tương lai của đua xe thể thao," Gill nói. "Chúng tôi hình dung một thế giới nơi dữ liệu thời gian thực thúc đẩy sự công bằng trong thi đấu giữa các loại xe khác nhau, nâng cao trải nghiệm đua xe Touring Car cho cả tay đua và người hâm mộ. Đây mới chỉ là khởi đầu cho việc chúng tôi sử dụng công nghệ AWS để tái định hình thể thao đua xe."

### Lộ trình triển khai BoP dựa trên dữ liệu

Lộ trình triển khai BoP hoàn toàn dựa trên dữ liệu bao gồm:

- Mở rộng thử nghiệm với nhiều biến thể ballast
- Tinh chỉnh mô hình ML
- Triển khai theo từng giai đoạn

Bắt đầu từ việc ML model chỉ cung cấp tư vấn bên cạnh phương pháp truyền thống, SRO dự định trong tương lai sẽ cho phép điều chỉnh BoP real-time trong giải Touring Car.

## Từ cờ kết thúc đến chiến thắng kỹ thuật số

Bằng việc tự động hóa kiểm tra kỹ thuật và đặt nền móng cho BoP dựa trên dữ liệu, SRO Motorsports đã tự khẳng định ở tuyến đầu đổi mới trong môn đua xe thể thao:

- **Giá trị ngay lập tức:** Giảm 83% thời gian kiểm tra kỹ thuật mang lại giá trị ngay lập tức hôm nay.
- **Tầm nhìn dài hạn:** Tầm nhìn dài hạn về BoP dựa trên dữ liệu hứa hẹn sẽ thay đổi cách mà người hâm mộ, các đội đua và tay đua trải nghiệm môn thể thao này trong tương lai.
- **Tương lai cạnh tranh:** Với các đổi mới trong tương lai dựa trên nền tảng vững chắc, SRO hy vọng sẽ mang đến những giải đua cạnh tranh và cân bằng nhất cho người hâm mộ toàn cầu.

## Thông tin tác giả

**Ryan Kiel** – Senior Solutions Architect tại AWS. Là một phần của AWS for Sports, anh hỗ trợ các giải đấu và câu lạc bộ trong hành trình cloud trên AWS bằng cách tận dụng best practices và công nghệ mới nhất.

**Steven Miller** – Principal Consultant tại AWS Professional Services. Anh đam mê data science và data engineering trong ngành ô tô và motorsports, làm việc trực tiếp với khách hàng để mang đến các giải pháp mang tính bước ngoặt.

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
