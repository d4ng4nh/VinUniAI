# HỒ SƠ CHỨNG CỨ BẢO VỆ FOUNDER

**1. Đối chiếu 5 loại hồ sơ:**
| # | Loại hồ sơ | Tình trạng | Cập nhật khi | Mục đích bảo vệ |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Nhật ký kiểm thử claim AI | ✗ (Xây dựng tuần tới) | Mỗi feature mới + hằng quý | Chống Điều 198 (Vụ Kera) |
| 2 | Hồ sơ rà soát điều khoản vendor | ✗ (Xây dựng tuần tới) | Hằng quý + khi vendor đổi | Chống rủi ro nhà cung cấp |
| 3 | Nhật ký giám sát giao dịch bất thường | ✓ (Đã có Helicone log) | Hằng tuần | Chống Điều 324 (Vụ Pips) |
| 4 | DPIA / CTIA đã nộp | ✗ (Nộp trong 60 ngày tới) | 1 lần + khi đổi luồng dữ liệu| Tuân thủ PDPL Điều 30 |
| 5 | Phê duyệt nội dung marketing | ✗ (Áp dụng ngay) | Trước mỗi đợt launch | Chống Điều 198 |

**2. TOP 1 Ưu tiên thực hiện ngay:**
- **Loại hồ sơ:** DPIA / CTIA (Đánh giá tác động chuyển dữ liệu ra nước ngoài).
- **Lý do:** Sản phẩm của chúng ta đẩy trực tiếp source code và thông tin dev sang máy chủ API tại Mỹ. Vi phạm PDPL Điều 30 (Vụ CIC) sẽ dẫn đến mức phạt lên tới 10 lần doanh thu. Đây là rủi ro hiện hữu cao nhất.

**3. Hành động 1 tuần (Cho TOP 1):**
- **Người chịu trách nhiệm:** Tech Founder.
- **Tần suất cập nhật:** 1 lần ngay bây giờ, và cập nhật mỗi khi thêm Vendor LLM mới.
- **Template tài liệu (Draft):**
  - *Luồng dữ liệu (Data Flow):* Browser (VN) -> Vercel Server -> Helicone Proxy -> Anthropic/OpenAI API (US).
  - *Biện pháp bảo vệ:* Dùng Enterprise API (Zero Data Retention), Helicone sanitize API keys/PII trước khi đẩy đi.
