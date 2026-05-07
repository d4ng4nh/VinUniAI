# INCIDENT PLAYBOOK (FOUNDER ALWAYS-ON-CALL)
*Tình huống: 9:00 sáng Thứ Hai, một Developer đăng lên X/Twitter: "Tránh xa RepoMap3D! Tool này vừa âm thầm gửi file chứa database password trong Private Repo của công ty tôi lên OpenAI public API!". Bài viết đạt 500 retweets.*

### 1. VERIFY (0-5 phút)
*   **Action:** Tech Founder lập tức truy cập **Helicone Dashboard**. Filter theo `user_id` của khách hàng đó (hoặc Github URL).
*   **Check:** Kiểm tra log raw input gửi đi xem file password đó có thực sự bị lọt qua bộ lọc (Sanitizer) không, và endpoint LLM gọi đến là Public hay Enterprise.

### 2. STOP THE BLEEDING (5-15 phút)
*   **Quyết định:** **SOFT KILL** (Chuyển sang rule-based / degraded mode).
*   **Action:** Lập tức đổi biến môi trường `ALLOW_PRIVATE_REPOS=false` trên Vercel. 
*   **Lý do:** Tắt ngay lập tức khả năng quét Private Repos để bảo vệ các khách hàng B2B khác khỏi rủi ro rò rỉ. Tuy nhiên, tính năng quét Public Repos (mã nguồn mở) vẫn hoạt động bình thường, không làm sập 100% app (Tránh Hard kill).

### 3. COMMUNICATE (15-30 phút)
**A. Customer Comm (DM trực tiếp cho user tố cáo trên X):**
> Subject: From [Tên Founder], CEO RepoMap3D re: your Private Repo data
> 
> Hi [Tên khách hàng],
> This is [Tên Founder]. I personally checked our Helicone logs after seeing your tweet. 
> What happened: Cảnh báo của bạn đúng, file config của bạn đã bị parser đọc do lỗi bộ lọc extension. 
> What I'm doing: Tôi đã tắt toàn bộ tính năng quét Private Repo của toàn hệ thống và đích thân xóa request log đó trên server.
> Making it right: Tôi đã hoàn tiền $200 cho gói Enterprise của bạn ngay hôm nay -- no forms required. 
> Calling in 24h: Số điện thoại trực tiếp của tôi là 09xx.xxx.xxx, bạn có thể gọi tôi bất cứ lúc nào. 
> -- [Tên Founder], CEO

**B. Public Tweet (< 280 ký tự):**
> "Sáng nay, RepoMap3D gặp sự cố bộ lọc khi quét Private Repos, gây rủi ro lộ file config. Đích thân tôi đã TẮT tính năng Private Repo để vá lỗi và rà soát log. Dữ liệu của các bạn là sinh mạng của chúng tôi. Update chi tiết và post-mortem sẽ có trong 4h tới. - [Tên Founder]"
