---
title: "Xóa SageMaker Endpoints"
date: 2026-07-30
weight: 1
chapter: false
pre: " <b> 5.9.1 </b> "
---

SageMaker Endpoint là tài nguyên tiêu tốn nhiều chi phí nhất vì luôn duy trì máy chủ (EC2) chạy 24/7 chờ phục vụ dự đoán.

Mặc dù trọng tâm của dự án này là tự động hóa luồng Huấn luyện (Training) và Quản lý phiên bản (Model Registry), nhưng nếu trong quá trình thực hành bạn có thử nghiệm triển khai (Deploy) mô hình ra Endpoint để dự đoán thử (Inference), bạn **phải xóa nó ngay lập tức**. 

## Bước 1: Đi đến phần Inference

1. Truy cập giao diện **SageMaker Console**.
2. Ở menu bên trái, tìm mục **Inference**, sau đó chọn **Endpoints**.

## Bước 2: Xóa Endpoint

1. Chọn Endpoint đang chạy của dự án SCADA (ví dụ: `scada-xgboost-endpoint`) và nhấn **Delete**.
2. Xác nhận thao tác xóa và chờ đến khi Endpoint biến mất khỏi danh sách.

>![Figure 1](/images/5-Workshop/5.10/delete-endpoint/endpoints.png)

## Bước 3: Xóa các cấu hình liên quan

Tiếp tục vào mục **Endpoint configurations** và **Models** (trong phần Inference) để xóa các cấu hình liên quan.
