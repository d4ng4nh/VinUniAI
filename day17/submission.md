
## 1. MVP Boundary Sheet

**Mục tiêu:** Ranh giới rõ ràng để kiểm chứng giả định cốt lõi với chi phí rẻ nhất.

| Phân loại | Tính năng | Giải thích (Lý do chọn) |
| :--- | :--- | :--- |
| **In-Scope**<br>*(Bắt buộc phải có)* | 1. Input GitHub Repo URL<br>2. Phân tích cấu trúc thư mục & Tóm tắt kiến trúc tổng quan<br>3. Q&A cơ bản về luồng code (Data flow) trong repo | Đây là cốt lõi để test xem người dùng có thực sự nhận được giá trị từ việc AI "đọc hộ" repo hay không. |
| **Out-of-Scope**<br>*(Tốt nhưng chưa cần)* | 1. Tích hợp trực tiếp thành Extension trên VSCode/IntelliJ<br>2. Phân tích và so sánh nhiều repo cùng lúc (Multi-repo analysis)<br>3. Vẽ sơ đồ UML tự động (Auto-diagramming) | Có thì tốt, nhưng tốn nhiều thời gian phát triển và không giải quyết giả định cốt lõi ban đầu của MVP. |
| **Non-Goals**<br>*(Ranh giới đỏ)* | 1. Viết code tự động để sửa bug (Auto-fixing)<br>2. Công cụ quét lỗ hổng bảo mật chuyên sâu (SAST/DAST) | CodebaseCompass là công cụ "la bàn" để học và hiểu repo, không phải là một AI Copilot để gõ code hay một scanner bảo mật thay thế con người. |

---

## 2. PRD Skeleton (Bộ khung yêu cầu sản phẩm)

**Mục tiêu:** Đồng bộ ngôn ngữ giữa Product, Engineering và AI Model.

### A. Standard Components

* **Problem Statement:** Việc đọc hiểu một repository mới, không có tài liệu (undocumented) hoặc code rác (spaghetti code) khiến các lập trình viên mới (newbies) hoặc người tham gia dự án tốn hàng tuần chỉ để hiểu luồng đi của dữ liệu.
* **Target User:** Software Engineers (đặc biệt là Junior/Mid-level) mới join vào dự án, hoặc những người muốn học hỏi từ các Open-source repo trên GitHub.
* **User Story #1:** As a *lập trình viên mới onboarding*, I want *nhập link GitHub vào CodebaseCompass* so that *tôi có thể đọc được bản tóm tắt kiến trúc và các module chính chỉ trong 5 phút*.
* **User Story #2:** As a *người học code*, I want *hỏi AI về cách một API cụ thể hoạt động trong repo* so that *tôi hiểu được luồng xử lý mà không cần dò từng file bằng tay*.

### B. AI-Specific Components

* **Model Selection:** LLM có Context Window cực lớn (ví dụ: GPT-4o với 1M-2M tokens) để có thể nạp toàn bộ cấu trúc mã nguồn của một repo cỡ trung bình vào ngữ cảnh (context) mà không bị "rớt chữ".
* **Data Source:** Public GitHub Repositories (thông qua GitHub API để clone text files). Đối với MVP, giới hạn các file `.py`, `.js`, `.ts`, `.go`, `.java` và bỏ qua các file binary/media.
* **Fallback UX (Thiết kế khi AI ngáo):**
    * **Quản trị kỳ vọng:** Khi mới load repo, hiện dòng chữ: *"AI đang phân tích repo. Kết quả có thể bỏ sót các logic ẩn, hãy luôn đối chiếu với mã nguồn gốc."*
    * **Xử lý giới hạn:** Khi repo quá lớn (vượt Context Window), hệ thống không được crash. Hiện thông báo: *"Repo quá lớn. Vui lòng chọn 1-3 thư mục cốt lõi (ví dụ: /src, /api) để AI tập trung phân tích."*
    * **Mất tự tin:** Nếu người dùng hỏi một đoạn code AI không tìm thấy, AI phải trả lời *"Không tìm thấy định nghĩa function này trong các file text đã quét"* thay vì bịa ra (hallucinate) một luồng code ảo.

---

## 3. Hypothesis & PMF Scorecard

**Mục tiêu:** Đưa ra con số đo lường sự thành công thay vì cảm giác mơ hồ.

| Thành phần | Chi tiết cho CodebaseCompass |
| :--- | :--- |
| **Riskiest Assumption** | Lập trình viên sẽ tin tưởng và dựa vào tóm tắt của AI để học về repo, thay vì thói quen truyền thống là tự clone code về máy và mò mẫm trên IDE của họ. |
| **Hypothesis** | Chúng tôi tin rằng tính năng Q&A trực tiếp trên mã nguồn sẽ giúp lập trình viên mới đạt được sự hiểu biết về luồng dữ liệu (Data flow) nhanh gấp 3 lần bình thường. |
| **Aha Moment** | Khoảnh khắc người dùng copy một hàm cực kỳ phức tạp/khó hiểu trong repo và CodebaseCompass giải thích chính xác nó được gọi từ đâu đến đâu bằng ngôn ngữ tự nhiên, giúp họ "sáng mắt ra" ngay lập tức. |
| **PMF Signal** | **Actionable Metric:** Một user phân tích thành công ít nhất **≥ 3** repo khác nhau trong tuần đầu tiên trải nghiệm.<br><br>**Retention:** Tỷ lệ D7 Retention (quay lại sau 7 ngày) **> 20%**. |
