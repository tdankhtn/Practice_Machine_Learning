# Travel Insurance Prediction

## Mục lục
- [Giới thiệu](#giới-thiệu)
- [Mô tả tập dữ liệu](#mô-tả-tập-dữ-liệu)
- [Cài đặt](#cài-đặt)
- [Phân tích dữ liệu](#phân-tích-dữ-liệu)
- [Kỹ thuật Feature Engineering](#kỹ-thuật-feature-engineering)
- [Huấn luyện và Đánh giá mô hình](#huấn-luyện-và-đánh-giá-mô-hình)
- [Kết quả](#kết-quả)

## Giới thiệu
Notebook này thực hiện một nhiệm vụ phân loại nhằm dự đoán việc mua bảo hiểm du lịch của khách hàng. Mục tiêu chính là dự đoán "Tỷ lệ rời bỏ khách hàng" (Churn rate), một chỉ số marketing mô tả số lượng khách hàng rời bỏ doanh nghiệp trong một khoảng thời gian cụ thể. Mỗi người dùng được gán một giá trị dự đoán ước tính trạng thái rời bỏ của họ dựa trên các thuộc tính được cung cấp.

## Mô tả tập dữ liệu
Tập dữ liệu chứa các thuộc tính sau, dùng để dự đoán việc khách hàng có mua bảo hiểm du lịch hay không:
- **Age**: Tuổi của khách hàng.
- **Employment Type**: Lĩnh vực mà khách hàng làm việc (ví dụ: Khu vực Chính phủ, Khu vực Tư nhân/Tự kinh doanh).
- **GraduateOrNot**: Khách hàng có phải là sinh viên tốt nghiệp đại học hay không.
- **AnnualIncome**: Thu nhập hàng năm của khách hàng bằng Rupee Ấn Độ (làm tròn đến 50 nghìn Rupee gần nhất).
- **FamilyMembers**: Số thành viên trong gia đình của khách hàng.
- **ChronicDiseases**: Khách hàng có mắc bất kỳ bệnh mãn tính hoặc tình trạng nào như tiểu đường/huyết áp cao hoặc hen suyễn, v.v. hay không (1 nếu có, 0 nếu không).
- **FrequentFlyer**: Dữ liệu phái sinh dựa trên lịch sử đặt vé máy bay của khách hàng ít nhất 4 lần khác nhau trong 2 năm qua (2017-2019).
- **EverTravelledAbroad**: Khách hàng đã từng đi du lịch nước ngoài chưa (không nhất thiết phải sử dụng dịch vụ của công ty).
- **TravelInsurance**: Khách hàng có mua gói bảo hiểm du lịch trong đợt ưu đãi giới thiệu được tổ chức vào năm 2019 hay không (biến mục tiêu: 1 nếu có, 0 nếu không).

## Cài đặt
Để chạy notebook này, bạn cần cài đặt các thư viện Python sau:
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn` (sklearn)
- `imblearn` (cho SMOTE)
- `ydata-profiling` (để phân tích dữ liệu)

Có thể cài đặt chúng bằng pip:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn imblearn ydata-profiling.

## Phân tích dữ liệu
- Xác định các cột số và cột phân loại.
- Kiểm tra các giá trị thiếu trong mỗi cột.
- Hiển thị tóm tắt thống kê cơ bản của các cột số để hiểu phân phối dữ liệu.
- Sử dụng ydata-profiling để tạo báo cáo chi tiết về dữ liệu, bao gồm thống kê, cảnh báo.

## Kỹ thuật Feature Engineering
Để chuẩn bị dữ liệu cho mô hình học máy, các bước kỹ thuật feature engineering được áp dụng:
- Các cột phân loại được chuyển đổi thành mã số.
- Kỹ thuật Oversampling SMOTE được áp dụng để cân bằng tập dữ liệu, giúp xử lý các trường hợp dữ liệu không cân bằng.

## Huấn luyện và Đánh giá mô hình
Dự án sử dụng các mô hình học máy sau:
- Random Forest Classifier: Một mô hình cây quyết định ensemble.
- Logistic Regression: Một mô hình phân loại tuyến tính.
Cả hai mô hình đều được huấn luyện bằng GridSearchCV để tìm ra các siêu tham số tốt nhất, đảm bảo hiệu suất tối ưu. Các siêu tham số được tìm kiếm bao gồm:
- Random Forest: n_estimators, max_depth, min_samples_split, min_samples_leaf, max_features, bootstrap.
- Logistic Regression: C (hệ số nghịch đảo của cường độ điều hòa), penalty (l1 hoặc l2), solver (lbfgs, liblinear, v.v.).

Các mô hình được đánh giá dựa trên các chỉ số hiệu suất như accuracy_score, precision_score, recall_score và f1_score, đặc biệt là f1_weighted cho GridSearchCV.

Kết quả
- Mô hình Random Forest tốt nhất đã tìm thấy các tham số tối ưu như max_depth=10, max_features='log2', min_samples_leaf=2, n_estimators=10.
- Mô hình Logistic Regression tốt nhất đã tìm thấy C=10, penalty='l2' và solver='lbfgs'.
Notebook thực hiện việc chia dữ liệu thành tập huấn luyện và tập kiểm tra (tỷ lệ 80/20) sau khi áp dụng SMOTE.
- Kích thước tập huấn luyện: (2043, 8)
- Kích thước tập kiểm tra: (511, 8)

Chi tiết về hiệu suất của từng mô hình (ví dụ: độ chính xác, độ nhạy, F1-score) được tính toán sau khi huấn luyện mô hình.
