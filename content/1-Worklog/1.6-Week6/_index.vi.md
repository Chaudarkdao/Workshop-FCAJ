---
title: "Worklog Tuần 6"
date: 2026-07-25
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Kết nối, làm quen với các thành viên trong First Cloud AI Journey.
* Hiểu dịch vụ AWS cơ bản, cách dùng console & CLI.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Đóng gói và đăng kí mô hình vào SageMaker Model Registry <br> - Thiết lập model versioning                                                                                          | 20/07/2026   | 20/07/2026      |
| 3   | - Triển khai mô hình lên SageMaker Endpoint <br> -  Tích hợp API Gateway +Lambda để expost Rest API                                   | 21/07/2026   | 21/07/2026      | 
| 4   | - Thiết lập monitoring với SageMaker Model Monitor và CloudWatch <br> - Phát hiện data drift| 22/07/2026   | 22/07/2026      |
| 5   | - Tự động hóa toàn bộ pipeline với SageMaker Pipelines                  | 23/07/2026   | 23/07/2026      |
| 6   | - Hoàn chỉnh, Tổng hợp, viết báo cáo                                                                                      | 24/07/2026   | 24/07/2026      |


### Kết quả đạt được tuần 6:

* Đóng gói và đăng ký mô hình vào SageMaker Model Registry:
  * Đóng gói mô hình đã chọn thành công dưới dạng model artifact (model.tar.gz).
  * Đăng ký mô hình vào SageMaker Model Registry để quản lý tập trung.
  * Thiết lập model versioning để theo dõi các phiên bản khác nhau của mô hình.
  * Gán metadata và tags cho mô hình để dễ dàng truy xuất và quản lý.

* Triển khai mô hình lên SageMaker Endpoint:
  * Tạo thành công SageMaker Endpoint để phục vụ dự đoán theo thời gian thực (real-time inference).
  * Cấu hình instance type phù hợp với yêu cầu về hiệu năng và chi phí.
  * Kiểm thử endpoint với dữ liệu mẫu để đảm bảo hoạt động chính xác.

* Tích hợp API Gateway + Lambda để expose REST API:
  * Xây dựng và triển khai AWS Lambda function để xử lý request từ client.
  * Tích hợp Lambda với SageMaker Endpoint để gọi model inference.
  * Tạo REST API trên API Gateway để expose endpoint ra bên ngoài.
  * Cấu hình CORS, authentication và các cài đặt bảo mật cần thiết.
  * Kiểm tra API hoạt động với các công cụ như Postman hoặc curl.

* Thiết lập monitoring với SageMaker Model Monitor và CloudWatch:
  * Cấu hình SageMaker Model Monitor để theo dõi chất lượng dự đoán.
  * Thiết lập phát hiện data drift để phát hiện sự thay đổi trong phân phối dữ liệu đầu vào.
  * Tạo CloudWatch Alarms để cảnh báo khi có sự cố bất thường.
  * Xây dựng dashboard giám sát để theo dõi các metrics quan trọng.

* Tự động hóa toàn bộ pipeline với SageMaker Pipelines:
  * Xây dựng pipeline tự động hóa quy trình Machine Learning từ preprocessing đến deploy.
  * Tích hợp các bước: data loading, preprocessing, training, evaluation, model registration.
  * Cấu hình pipeline triggers để tự động chạy khi có dữ liệu mới.

* Hoàn chỉnh và tổng hợp dự án:
  * Viết báo cáo tổng kết quá trình thực hiện project.
  * Tổng hợp các kết quả đạt được, bài học kinh nghiệm và hướng phát triển trong tương lai.
  * Chuẩn bị tài liệu hướng dẫn sử dụng và vận hành hệ thống.
  * Hoàn thành tất cả công việc đúng tiến độ.

