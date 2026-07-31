---
title: "Xóa SageMaker Model Registry"
date: 2026-07-30
weight: 2
chapter: false
pre: " <b> 5.9.2 </b> "
---

Để giữ cho không gian làm việc gọn gàng và không tốn phí lưu trữ siêu dữ liệu (metadata), bạn nên xóa các Model Groups không còn sử dụng.

## Bước 1: Điều hướng đến Model Registry

Trong **SageMaker Console**, điều hướng đến **Models** → **Model Registry**.

## Bước 2: Xóa các phiên bản (Model versions)

1. Tìm **Model Package Group** của dự án SCADA.
2. Bạn cần nhấp vào Group đó, chọn tất cả các phiên bản (Model versions) bên trong và xóa chúng trước.

## Bước 3: Xóa Model Package Group

Cuối cùng, sau khi đã xóa hết các phiên bản, hãy xóa chính Model Package Group.
