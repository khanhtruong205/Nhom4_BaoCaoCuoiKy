# Nhom4_BaoCaoCuoiKy

## Giới thiệu
Dự án xây dựng hệ thống phân tích hành vi khách hàng, khuyến nghị sản phẩm thông minh và giao diện người dùng trên bộ dữ liệu Brazilian E-Commerce (Olist). Nhóm sử dụng Python, Pandas và Scikit-learn để thực hiện EDA, tiền xử lý dữ liệu, tạo đặc trưng và chuẩn bị cho các bài toán học máy.

## Dataset
Bộ dữ liệu sử dụng: Brazilian E-Commerce Public Dataset by Olist.
Link: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce
Các file chính gồm:
- `olist_customers_dataset.csv`
- `olist_orders_dataset.csv`
- `olist_order_items_dataset.csv`
- `olist_order_payments_dataset.csv`
- `olist_order_reviews_dataset.csv`
- `olist_products_dataset.csv`
- `olist_sellers_dataset.csv`
- `olist_geolocation_dataset.csv`
- `product_category_name_translation.csv`

## File chính trong repo
- `Nhom4_bctd_Tuan1.ipynb`: notebook khảo sát dữ liệu và tiền xử lý bước đầu
- `requirements.txt`: danh sách thư viện cần cài đặt
- `app.py` hoặc `streamlit.py`: giao diện Streamlit (nếu có)

## Công nghệ sử dụng
- Python 3.x
- Pandas
- NumPy
- Scikit-learn
- Matplotlib / Seaborn / Plotly
- Streamlit
- scikit-surprise
- mlxtend

## Cách chạy
### 1. Tạo môi trường ảo
```bash
python -m venv .venv
