# Nhom4_BaoCaoCuoiKy

## 1. Giới thiệu đề tài
Dự án tập trung xây dựng hệ thống **phân tích hành vi khách hàng, khuyến nghị sản phẩm thông minh và giao diện người dùng** trên bộ dữ liệu **Brazilian E-Commerce Public Dataset by Olist**. Hệ thống được triển khai bằng **Python, Pandas và Scikit-learn**, theo hướng end-to-end từ khảo sát dữ liệu, tiền xử lý, tạo đặc trưng, chuẩn bị dữ liệu cho các bài toán học máy, đến tích hợp kết quả vào giao diện trực quan.

Mục tiêu của dự án không chỉ dừng ở phân tích dữ liệu mô tả (EDA), mà còn hướng tới việc xây dựng nền tảng dữ liệu phù hợp cho các nhóm bài toán chính:
- **Classification**: dự đoán mức độ hài lòng/đánh giá của khách hàng
- **Regression**: dự đoán giá trị đơn hàng hoặc các biến định lượng liên quan
- **Clustering**: phân khúc khách hàng dựa trên hành vi mua sắm
- **Recommendation**: gợi ý sản phẩm dựa trên dữ liệu đánh giá/giao dịch
- **Association Rules**: khai phá luật kết hợp và xu hướng mua sắm

---

## 2. Mục tiêu chính của dự án
Dự án được xây dựng với các mục tiêu cụ thể sau:

1. Khảo sát và hiểu cấu trúc bộ dữ liệu Olist gồm 9 bảng CSV có quan hệ với nhau.
2. Thực hiện **EDA** để nhận diện đặc điểm dữ liệu, quan hệ giữa các bảng, giá trị thiếu, độ phủ liên kết và các xu hướng mua sắm.
3. Xây dựng quy trình **tiền xử lý dữ liệu** theo hướng có hệ thống:
   - merge các bảng liên quan
   - xử lý missing values
   - chuẩn hóa kiểu dữ liệu
   - tạo đặc trưng phục vụ mô hình
4. Chuẩn bị dữ liệu cho các bài toán:
   - classification
   - regression
   - clustering
   - recommendation
   - association rules
5. Xây dựng **preprocessing pipeline** bằng Scikit-learn với:
   - `ColumnTransformer`
   - `StandardScaler`
   - `OneHotEncoder`
   - `TfidfVectorizer`
6. Chuẩn bị nền tảng để tích hợp mô hình vào giao diện **Streamlit Web UI**.

---

## 3. Bộ dữ liệu sử dụng
Dự án sử dụng bộ dữ liệu:

**Brazilian E-Commerce Public Dataset by Olist**
Link:https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce
Bộ dữ liệu gồm 9 file CSV chính:

- `olist_customers_dataset.csv`
- `olist_geolocation_dataset.csv`
- `olist_order_items_dataset.csv`
- `olist_order_payments_dataset.csv`
- `olist_order_reviews_dataset.csv`
- `olist_orders_dataset.csv`
- `olist_products_dataset.csv`
- `olist_sellers_dataset.csv`
- `product_category_name_translation.csv`

### Vai trò của từng bảng
- **orders**: bảng trung tâm, chứa thông tin đơn hàng và các mốc thời gian
- **customers**: thông tin khách hàng
- **order_items**: chi tiết sản phẩm trong từng đơn hàng
- **order_payments**: thông tin thanh toán
- **order_reviews**: đánh giá của khách hàng
- **products**: thông tin sản phẩm
- **sellers**: thông tin người bán
- **geolocation**: dữ liệu vị trí địa lý
- **category_translation**: bảng dịch tên danh mục từ tiếng Bồ Đào Nha sang tiếng Anh

### Ghi chú
Do dữ liệu có cấu trúc **nhiều bảng quan hệ**, hệ thống không phân tích từng bảng riêng lẻ mà tiến hành tổng hợp dữ liệu về mức **đơn hàng** và **khách hàng** để phục vụ EDA và machine learning.

---

## 4. Kiến trúc hệ thống tổng thể
Pipeline của dự án được thiết kế theo hướng:

1. **Raw CSV Files (9 files)**
2. **Pandas DataFrame (Load and Validate)**
3. **Join / Merge Relevant Tables + Data Cleaning**
   - `pd.merge`
   - aggregation
   - null handling
   - duplicate check
   - type casting
4. **Feature Engineering**
   - RFM
   - `delivery_time_days`
   - payment features
   - review features
   - text features
5. **Master Dataset / Task-specific Datasets**
6. **Train / Test Split for Supervised Tasks**
7. **Scikit-learn Preprocessing Pipeline**
   - `ColumnTransformer`
   - `StandardScaler`
   - `OneHotEncoder`
   - `TfidfVectorizer`
   - optional feature selection (`SelectKBest`)
   - target encoding if needed
8. **5 Model / Analysis Groups**
   - Classification
   - Regression
   - Clustering
   - Recommendation
   - Association Rules
9. **Training / Evaluation**
   - `GridSearchCV`
   - metrics
   - model comparison
10. **Save / Load Trained Models and Export Outputs**
    - models: `joblib`, `pickle`
    - outputs/data: `csv`, `parquet`
11. **Streamlit Web UI (Deployment Layer)**
    - Dashboard
    - Customer Analysis
    - Prediction
    - Recommendation

---

## 5. Nội dung hiện có trong repository
Repository hiện lưu trữ các thành phần chính phục vụ cho quá trình thực hiện đồ án, bao gồm notebook khảo sát dữ liệu, file cấu hình thư viện và dữ liệu đầu vào.

### File chính
- `Nhom4_bctd_Tuan1.ipynb`  
  Notebook chính dùng để:
  - đọc dữ liệu
  - EDA
  - kiểm tra missing values
  - khảo sát quan hệ giữa các bảng
  - tạo `orders_base`
  - chuẩn bị RFM
  - chuẩn bị dữ liệu cho preprocessing pipeline

- `requirements.txt`  
  Danh sách các thư viện cần thiết để tái lập môi trường làm việc.

### Dataset
Các file CSV Olist được sử dụng làm đầu vào cho notebook.  
Trường hợp repository không chứa toàn bộ dataset, cần đặt các file CSV đúng thư mục làm việc trước khi chạy notebook.

---

## 6. Cấu trúc thư mục gợi ý
Cấu trúc repository có thể được tổ chức như sau:

```text
Nhom4_BaoCaoCuoiKy/
│
├── Nhom4_bctd_Tuan1.ipynb
├── requirements.txt
├── README.md
│
├── olist_customers_dataset.csv
├── olist_geolocation_dataset.csv
├── olist_order_items_dataset.csv
├── olist_order_payments_dataset.csv
├── olist_order_reviews_dataset.csv
├── olist_orders_dataset.csv
├── olist_products_dataset.csv
├── olist_sellers_dataset.csv
├── product_category_name_translation.csv
│
├── outputs/
│   ├── eda_summary.png
│   ├── correlation_heatmap.png
│   └── ...
│
└── app.py / streamlit.py   (nếu đã có giao diện)
