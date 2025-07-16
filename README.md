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
pip install pandas numpy matplotlib seaborn scikit-learn imblearn ydata-profiling
