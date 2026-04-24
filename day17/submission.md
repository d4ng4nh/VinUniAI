

## 1. MVP Boundary Sheet

**Mục tiêu:** Ranh giới rõ ràng để kiểm chứng giả định cốt lõi với chi phí rẻ nhất và tránh các rủi ro kỹ thuật (latency, cost).

| Phân loại | Tính năng | Giải thích (Lý do chọn) |
| :--- | :--- | :--- |
| **In-Scope**<br>*(Bắt buộc phải có)* | 1. Input GitHub Repo URL (giới hạn size repo < 50MB hoặc < 500 files).<br>2. Xuất sơ đồ cây (Tree-view) và tóm tắt vai trò của các thư mục lõi.<br>3. Q&A tĩnh trên 1 file cụ thể hoặc nhóm file (≤ 3 files) do user chủ động khoanh vùng. | Giải quyết đúng "nỗi đau" tìm đường trong repo lạ. Giới hạn dung lượng và số lượng file giúp hệ thống phản hồi nhanh (< 10 giây) và kiểm soát chi phí API ở mức tối thiểu. |
| **Out-of-Scope**<br>*(Tốt nhưng chưa cần)* | 1. Q&A truy vết luồng dữ liệu (Data flow) tự động xuyên suốt toàn bộ repo.<br>2. Tích hợp trực tiếp thành Extension trên IDE.<br>3. Vẽ sơ đồ UML tự động (Auto-diagramming). | Q&A Data flow toàn cục đòi hỏi xây dựng hệ thống RAG phức tạp hoặc AST, làm chậm tiến độ MVP. Hãy để user tự khoanh vùng file cần phân tích trước. |
| **Non-Goals**<br>*(Ranh giới đỏ)* | 1. Viết code tự động để sửa bug (Auto-fixing).<br>2. Công cụ quét lỗ hổng bảo mật chuyên sâu (SAST/DAST). | CodebaseCompass là "la bàn" định hướng kiến trúc, không phải AI Copilot để code hộ hay Security Scanner. |

---

## 2. PRD Skeleton (Bộ khung yêu cầu sản phẩm)

**Mục tiêu:** Đồng bộ ngôn ngữ giữa Product, Engineering và thiết lập luồng xử lý AI thực tế.

### A. Standard Components

* **Problem Statement:** Việc đọc hiểu một repository mới, không có tài liệu khiến các lập trình viên tốn hàng tuần chỉ để rà soát xem tính năng A được đặt ở thư mục nào và các file liên kết tĩnh ra sao.
* **Target User:** Software Engineers (Junior/Mid-level) mới onboard vào dự án, hoặc người tự học qua Open-source.
* **User Story #1:** As a *lập trình viên mới*, I want *hệ thống tóm tắt mục đích của các thư mục chính (ví dụ: `src/utils` dùng để làm gì)* so that *tôi biết nên bắt đầu đọc từ đâu thay vì mở từng file.*
* **User Story #2:** As a *người tìm hiểu code*, I want *chọn file `auth.controller.ts` và hỏi AI về logic của file này* so that *tôi hiểu cách file này hoạt động độc lập trước khi tự ghép nối nó vào hệ thống.*

### B. AI-Specific Components

* **AI Architecture (Pipeline 2 bước thay vì nhồi nhét Context):**
    * *Bước 1 (Mapping):* Dùng API của GitHub lấy cấu trúc cây thư mục và file `README.md`. Đưa vào LLM (tốc độ cao, chi phí rẻ như GPT-4o-mini) để phân loại và tóm tắt kiến trúc.
    * *Bước 2 (On-demand Q&A):* Chỉ khi user click chọn cụ thể 1 file (hoặc paste đoạn code), hệ thống mới trích xuất nội dung text của file đó và đưa vào LLM (tốc độ cao) để giải thích logic cục bộ.
* **Fallback UX (Thiết kế quản trị rủi ro AI):**
    * **Giới hạn dung lượng:** Nếu user nhập link repo quá lớn (như repo lõi của Linux), hiện thông báo: *"Repo vượt quá 500 files. Để đảm bảo tốc độ, vui lòng điền đường dẫn đến một thư mục con cụ thể (Ví dụ: `github.com/torvalds/linux/tree/master/kernel`)."*
    * **Cảnh báo "Dependency Hell":** Khi AI giải thích một file có gọi API từ bên ngoài, luôn kèm theo disclaimer: *"Lưu ý: File này phụ thuộc vào thư viện `axios` và service `PaymentGateway`. AI hiện chỉ phân tích logic tĩnh nội bộ trong file này."*
    * **Chống Hallucination:** Prompt kỹ thuật phải ép model trả lời *"Tôi không tìm thấy thông tin này trong cấu trúc thư mục hiện tại"* nếu user hỏi về một module không tồn tại, tuyệt đối không tự bịa tên file.

---

## 3. Hypothesis & PMF Scorecard

**Mục tiêu:** Đo lường sự tham gia sâu (Deep engagement) và giá trị ứng dụng thực tế.

| Thành phần | Chi tiết cho CodebaseCompass |
| :--- | :--- |
| **Riskiest Assumption** | User sẽ tin tưởng dùng bản tóm tắt kiến trúc của AI làm "bản đồ" để điều hướng trong IDE của họ, thay vì phớt lờ nó và tự dùng tính năng Search/Find in Files truyền thống. |
| **Hypothesis** | Chúng tôi tin rằng việc bóc tách và giải thích kiến trúc thư mục bằng ngôn ngữ tự nhiên sẽ giúp giảm 50% thời gian user tìm ra đúng file chứa logic cần sửa. |
| **Aha Moment** | Khoảnh khắc user đặt câu hỏi khái quát về dự án (Ví dụ: *"Tôi muốn đổi logic tính thuế ở giỏ hàng thì tìm ở đâu?"*) và AI chỉ ra đích danh đường dẫn file chính xác (Ví dụ: *"Bạn hãy kiểm tra hàm `calculateTax()` trong `src/services/checkout.ts`"*). |
| **PMF Signal** | **1. Conversation Depth (Độ sâu hội thoại):** ≥ 30% user có từ **4 lượt hỏi-đáp (turns)** trở lên trên *cùng một repo* (chứng tỏ họ thực sự dùng tool để đào sâu nghiên cứu, không phải test dạo).<br><br>**2. Actionable Rate (Tỷ lệ ứng dụng):** ≥ 20% session kết thúc bằng việc user thực hiện thao tác **Copy to Clipboard** câu trả lời của AI hoặc bấm nút **Export Architecture Note** (chứng tỏ kết quả đầu ra đủ chất lượng để họ dùng cho công việc thật).<br><br>**3. Retention:** Tỷ lệ D7 Retention **> 20%**. |
