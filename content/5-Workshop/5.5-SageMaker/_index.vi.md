---
title : "Huấn luyện và quản lý mô hình"
date :  2026-07-30 
weight : 5
chapter : false
pre : " <b> 5.5 </b> "
---

### Cốt lõi của MLOps: Amazon SageMaker

Trong bài thực hành này, chúng ta sẽ tiến hành quá trình tính toán nặng nhất của dự án: Huấn luyện thuật toán XGBoost. Việc chạy trên Amazon SageMaker giúp chúng ta dễ dàng mở rộng tài nguyên tính toán (scale compute) và tự động hóa toàn bộ việc dò tìm siêu tham số, cũng như quản lý phiên bản mô hình.

Đặc biệt, để giải quyết bài toán mất cân bằng nhãn của dữ liệu SCADA công nghiệp, chúng ta sẽ cấu hình tham số `scale_pos_weight` trực tiếp vào luồng huấn luyện.

---

### 1. Khởi tạo Kịch bản Huấn luyện (Training Job)

Chúng ta sử dụng thư viện `sagemaker` (Python SDK) tại máy cục bộ để định nghĩa một **Estimator**. Estimator này sẽ báo cho AWS biết cần thuê loại máy chủ ảo (EC2) nào, lấy dữ liệu ở đâu và thuật toán cần chạy là gì.

Tạo một tệp Jupyter Notebook hoặc script Python trên máy cục bộ và chạy đoạn mã cấu hình sau:

```python
import sagemaker
from sagemaker.xgboost.estimator import XGBoost

# Lấy execution role đã thiết lập
role = 'arn:aws:iam::<ACCOUNT_ID>:role/SageMaker-SCADA-ExecutionRole'

# Cấu hình XGBoost Estimator
xgb_estimator = XGBoost(
    entry_point='train.py', # Script chứa mã nguồn huấn luyện của nhóm
    role=role,
    instance_count=1,
    instance_type='ml.m5.large', # Máy chủ dùng để training
    framework_version='1.3-1',
    output_path='s3://scada-mlops-project-bucket-2026/model-artifacts/', # Nơi lưu model.tar.gz
    hyperparameters={
        'objective': 'binary:logistic',
        'eval_metric': 'aucpr', # Tối ưu hóa trên diện tích dưới đường cong PR (Precision-Recall)
        'scale_pos_weight': '99', # Bù trừ cho dữ liệu lỗi SCADA hiếm gặp
        'num_round': '100'
    }
)

# Kích hoạt quá trình huấn luyện với dữ liệu từ S3
xgb_estimator.fit({'train': 's3://scada-mlops-project-bucket-2026/processed-data/train.csv',
                   'validation': 's3://scada-mlops-project-bucket-2026/processed-data/validation.csv'})

```

---

### 2. Tối ưu hóa Siêu tham số tự động (HPO)

Thay vì thử nghiệm các tham số (`max_depth`, `eta`, `subsample`...) bằng tay, chúng ta sẽ thiết lập **Hyperparameter Tuning Job**. SageMaker sẽ tự động sinh ra nhiều Training Jobs song song hoặc nối tiếp để tìm ra tổ hợp tham số cho ra chỉ số F1-Score (hoặc AUCPR) cao nhất.

![image](/images/5-Workshop/5.4-SageMaker/HPO.png)

---

### 3. Đăng ký Mô hình (Model Registry)

Sau khi HPO hoàn tất và mô hình được đánh giá thông qua tập kiểm thử (Test set), các chỉ số (Metrics) thu được sẽ lưu vào tệp `evaluation.json`. Mô hình tốt nhất (Best Model) cùng với các metrics này sẽ được tự động đẩy vào **SageMaker Model Registry**.

Model Registry hoạt động như một kho lưu trữ trung tâm dành cho việc lập phiên bản (versioning) của mô hình.

**Cơ chế Phê duyệt (Approval Workflow):**
Khi một phiên bản mô hình mới được đăng ký thành công vào nhóm mô hình (Model Package Group), trạng thái mặc định của nó sẽ là **PendingManualApproval**. Nó chưa thể được đưa vào sản xuất (Deploy to Endpoint) ngay lập tức.

Kỹ sư MLOps (hoặc Quản lý dự án) cần truy cập vào giao diện, đánh giá file kết quả và chuyển trạng thái sang **Approved** (Phê duyệt) để hoàn tất vòng đời.

![Model Registry](/images/5-Workshop/5.4-SageMaker/Model_Registry.png)

{{% notice success %}}
**Hoàn tất Huấn luyện:**
Đến bước này, bạn đã tự động hóa thành công luồng huấn luyện, đánh giá và lập phiên bản. Trong bài lab tiếp theo, chúng ta sẽ đi sâu vào việc thiết lập các Policy (IAM Role) bảo mật ở hậu trường để đảm bảo toàn bộ quá trình trên được diễn ra thông suốt.
{{% /notice %}}
