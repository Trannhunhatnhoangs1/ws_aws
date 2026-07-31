---
title: "Xóa tài nguyên Amazon S3"
date: 2026-07-30
weight: 3
chapter: false
pre: " <b> 5.9.3 </b> "
---

Amazon S3 tính phí dựa trên dung lượng dữ liệu bạn lưu trữ (gồm dữ liệu thô, dữ liệu sau xử lý và file trọng số mô hình). AWS cũng thiết lập cơ chế an toàn: bạn không thể xóa một Bucket nếu bên trong vẫn còn dữ liệu.

## Bước 1: Làm trống Bucket (Empty)

1. Truy cập **S3 Console**, tìm đến bucket của dự án (ví dụ: `scada-mlops-project-bucket-2026`).
2. Chọn bucket đó và nhấn nút **Empty** (Làm trống).
3. AWS sẽ yêu cầu bạn gõ chữ `permanently delete` để xác nhận việc xóa toàn bộ dữ liệu CSV và các file `model.tar.gz`.

>![Figure 1](/images/5-Workshop/5.10/delete-s3/bucket.png)
>![Figure 2](/images/5-Workshop/5.10/delete-s3/files.png)

## Bước 2: Xóa hoàn toàn Bucket (Delete)

Sau khi Empty thành công, quay lại danh sách Buckets, chọn lại bucket dự án và nhấn **Delete** để xóa hoàn toàn vùng chứa này.
