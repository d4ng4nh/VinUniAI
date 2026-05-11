# AI COMPLIANCE AUDIT REPORT

**VI PHẠM 1: Lừa dối khách hàng qua Marketing (Thổi phồng tính năng)**
- **Luật áp dụng:** Bộ luật Hình sự VN
- **Điều:** Điều 198 (Tội lừa dối khách hàng)
- **Bằng chứng trong sản phẩm:** Landing page ghi *"Chính xác 100% cho mọi repo"*, *"Tự động phân tích hàng triệu file"*.
- **Pattern khớp với:** Vụ kẹo Kera (11/2025) - Thổi phồng công dụng không có chứng cứ.
- **Hành động sửa:** 
  1. Gỡ bỏ các từ "100%", "tuyệt đối", "hàng triệu" trên Landing Page và Pitch Deck.
  2. Public bảng đo lường Benchmark chất lượng RAGAS thực tế.
  3. Bắt buộc Founder ký duyệt nội dung Marketing mới.
- **Deadline:** Xử lý ngay lập tức trước khi Launch.

**VI PHẠM 2: Chuyển dữ liệu cá nhân ra nước ngoài trái phép**
- **Luật áp dụng:** Luật Bảo vệ Dữ liệu Cá nhân (PDPL)
- **Điều:** Điều 30 (Chuyển dữ liệu cá nhân ra nước ngoài)
- **Bằng chứng trong sản phẩm:** Backend gửi IP, Email user và source code qua Anthropic/OpenAI API tại Mỹ nhưng chưa làm CTIA.
- **Pattern khớp với:** Vụ rò rỉ CIC (Phạt 10x doanh thu).
- **Hành động sửa:** 
  1. Soạn thảo và nộp hồ sơ CTIA cho Bộ Công an.
  2. Bổ sung checkbox đồng ý (Consent) vào luồng Onboarding.
  3. Cập nhật Privacy Policy nêu rõ dữ liệu được xử lý bởi LLM provider ở nước ngoài.
- **Deadline:** Nộp hồ sơ trước 1/1/2026.

**VI PHẠM 3: Đồng lõa hỗ trợ tội phạm/Rửa tiền qua nền tảng**
- **Luật áp dụng:** Bộ luật Hình sự VN
- **Điều:** Điều 324 (Tội rửa tiền)
- **Bằng chứng trong sản phẩm:** Hệ thống phân tích mọi URL Github dán vào mà không kiểm duyệt rủi ro (Hacker có thể dán repo chứa mã độc/scam để nhờ AI hoàn thiện code).
- **Pattern khớp với:** Vụ Mr Pips (Shark Bình bị truy tố vì xử lý giao dịch cho tổ chức phạm pháp dù đã có dấu hiệu cảnh báo).
- **Hành động sửa:** 
  1. Dùng Guardrails block các repo thuộc danh sách blacklist hoặc có dấu hiệu malware.
  2. Thiết lập Rule Audit Log hằng tuần ghi nhận các URL bất thường.
  3. Tắt server/từ chối dịch vụ (Soft kill) ngay với các request lạm dụng.
- **Deadline:** Xây dựng cơ chế Report & Block trong Sprint tới.

**VI PHẠM 4: Chưa minh bạch hệ thống AI sinh nội dung**
- **Luật áp dụng:** Luật AI Việt Nam
- **Điều:** Điều 9 (Tầng rủi ro AI) & Nghĩa vụ Tầng Trung bình
- **Bằng chứng trong sản phẩm:** Agent Click-to-Explain sinh ra nội dung text giải thích code nhưng giao diện không ghi chú rõ đây là do AI tạo ra.
- **Pattern khớp với:** Quy định bắt buộc minh bạch AI.
- **Hành động sửa:** 
  1. Thêm watermark/nhãn *"AI-generated explanation"* trên các cửa sổ tóm tắt.
  2. Nộp thông báo hệ thống AI tầng trung bình cho Bộ KH&CN.
  3. Thêm nút Report/Feedback cho người dùng nếu AI giải thích sai.
- **Deadline:** Trước 1/3/2026.

**VI PHẠM 5: Vi phạm quyền xóa dữ liệu (Right to be Forgotten)**
- **Luật áp dụng:** EU AI Act & GDPR & PDPL
- **Điều:** Quyền xóa dữ liệu cá nhân
- **Bằng chứng trong sản phẩm:** User dán link phân tích, hệ thống lưu cache bản đồ 3D nhưng UI không có nút "Xóa lịch sử và dữ liệu của tôi".
- **Pattern khớp với:** Các vụ phạt vi phạm GDPR cơ bản ở Châu Âu.
- **Hành động sửa:** 
  1. Xây dựng API endpoint Hard Delete dữ liệu liên quan đến session/user ID.
  2. Bổ sung nút "Delete My Data" rõ ràng trong màn hình Dashboard.
  3. Cấu hình TTL tự hủy Redis cache sau 30 ngày.
- **Deadline:** Trước khi nhận User Pilot đầu tiên.

**VI PHẠM 6: Rủi ro bản quyền mã nguồn**
- **Luật áp dụng:** Luật Sở hữu trí tuệ
- **Điều:** Bản quyền và Giấy phép (Licenses)
- **Bằng chứng trong sản phẩm:** AI có thể copy code mang giấy phép GPL/Copyleft vào đoạn tóm tắt mà không cite nguồn.
- **Pattern khớp với:** Các vụ kiện Github Copilot.
- **Hành động sửa:** Cấu hình System Prompt ép LLM phải trích dẫn (cite) đường dẫn file gốc khi giải thích.
- **Deadline:** Áp dụng ngay.

**VI PHẠM 7: Ảo giác AI gây thiệt hại kinh tế (Hallucination)**
- **Luật áp dụng:** Luật Dân sự & Thương mại
- **Điều:** Bồi thường thiệt hại
- **Bằng chứng trong sản phẩm:** Không có điều khoản miễn trừ trách nhiệm pháp lý khi Dev làm theo hướng dẫn sai của AI và gây lỗi bảo mật cho công ty họ.
- **Pattern khớp với:** Vụ Air Canada (Chatbot bịa policy làm công ty phải đền tiền).
- **Hành động sửa:** Thêm Disclaimer rõ ràng vào ToS: *"Công cụ chỉ mang tính tham khảo. Người dùng hoàn toàn chịu trách nhiệm khi đưa code vào môi trường Production"*.
- **Deadline:** Áp dụng ngay.
