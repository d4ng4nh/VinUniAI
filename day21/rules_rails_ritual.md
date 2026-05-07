# 3 R's CHO RISK LỚN NHẤT CỦA REPOMAP3D
**Risk lớn nhất:** Rò rỉ mã nguồn (Data Leakage) hoặc vô tình dùng mã nguồn Private Repo của khách hàng để train public model của AI Vendor.

### R1 — RULES (1-trang Notion, Founder viết)
*   **Cấm cụ thể:** KHÔNG BAO GIỜ được gửi mã nguồn Private Repo của khách hàng qua public API (OpenAI/Anthropic tier thường) có lưu log training.
*   **Được làm gì:** DÙNG Anthropic Console tier Claude for Work (Zero Data Retention) hoặc OpenAI Enterprise API (Data không được train). Cost API có thể cao hơn nhưng bắt buộc.
*   **Hậu quả vi phạm:** Vi phạm lần 1 -> Founder (CEO) họp 1-1 cảnh cáo và rà soát lại toàn bộ log. Tái phạm lần 2 -> Buộc thôi việc ngay lập tức.
*   **Update:** Cập nhật qua [Link Notion: RepoMap3D Security Guidelines].

### R2 — RAILS (Stack $0 - $500/tháng, tự động chặn)
1.  **Helicone (Paid tier - $50/tháng):** Làm proxy đứng giữa app và LLM để log toàn bộ 100% LLM prompts/responses, thiết lập rule tự động sanitize (che) các biến môi trường hoặc API Keys vô tình nằm trong code của khách hàng trước khi gửi cho LLM.
2.  **Github App Permissions ($0):** Thiết lập quyền của RepoMap3D Github App là "Strictly Read-Only" (Tuyệt đối không có quyền Write) để AI không thể tự ý sửa code của khách.
3.  **git-secrets ($0):** Cài đặt pre-commit hooks chặn toàn bộ nhân viên push các file config chứa API Key thật lên Github.
*Tổng Cost: $50/tháng (Hoàn toàn nằm trong budget < $500/tháng của startup).*

### R3 — RITUAL (Hành vi team)
*   **Friday 30' Risk Review:** Chiều Thứ Sáu hàng tuần (16:00), Tech Founder và Lead Dev dành đúng 30 phút mở dashboard Helicone. 
*   **Question bắt buộc:** *"Tuần qua có request nào từ Private Repo bị filter báo đỏ là chứa API Key/PII không? Có request nào gọi nhầm sang endpoint public của LLM provider không?"*

