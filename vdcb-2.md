## [Vận dụng cơ bản 2] Khắc phục lỗi rò rỉ dữ liệu mật khi chat với AI công cộng
### BƯỚC 1: CHỈ RA CÁC THÔNG TIN NHẠY CẢM TRONG HIỆN TRƯỜNG GIẢ
Trong đoạn mã nguồn được cung cấp:
def connect_database(): 
    db_password = 'rikkei_secret_password_2026' 
    api_key = 'google_gemini_api_abc123' 
    print('Đang kết nối...')

Hai biến số chứa thông tin cực kỳ nguy hiểm nếu bị rò rỉ ra ngoài gồm:
1. `db_password` ('rikkei_secret_password_2026'): Mật khẩu kết nối cơ sở dữ liệu thực tế của hệ thống. Nếu lộ, kẻ tấn công có thể truy cập, đánh cắp hoặc phá hoại toàn bộ dữ liệu database.
2. `api_key` ('google_gemini_api_abc123'): Khóa truy cập API của dịch vụ (Google Gemini). Nếu lộ, kẻ xấu có thể lợi dụng key này để gọi API trái phép, gây tổn thất tài chính hoặc chiếm quyền dịch vụ.

### BƯỚC 2: LÀM SẠCH CODE VÀ VIẾT PROMPT AN TOÀN GỬI CHO AI

**1. Đoạn code đã được làm sạch (Masked Code):**
```python
def connect_database(): 
    db_password = '[kkk]' 
    api_key = '[kkkk]' 
    print('Đang kết nối...')
   ```
   
**2. Câu lệnh Prompt an toàn gửi kèm cho AI:** "Bạn là một chuyên gia bảo mật và lập trình viên cao cấp. Tôi có đoạn mã Python kết nối cơ sở dữ liệu dưới đây. Các thông tin nhạy cảm đã được ẩn đi bằng các placeholder. Hãy xem xét đoạn code này và tư vấn giúp tôi các phương án tối ưu hóa, tuân thủ các thực hành bảo mật tốt nhất để bảo vệ thông tin cấu hình thay vì viết cứng trong mã nguồn:
def connect_database(): 
    db_password = '[YOUR_DATABASE_PASSWORD]' 
    api_key = '[YOUR_API_KEY]' 
    print('Đang kết nối...')