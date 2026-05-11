**Dự án:** RepoMap3D (Bản đồ kiến trúc 3D cho Github)

### PHẦN A — Thách Thức Và Phạm Vi Sản Phẩm
*   **Thách thức áp dụng AI:** Hiện ứng "Wow" ban đầu không chuyển hóa thành sự gắn bó (Adoption). User xem bản đồ 3D cho vui rồi thoát, không dùng AI để hỗ trợ gỡ rối logic code trong công việc hàng ngày.
*   **Sản phẩm AI:** RepoMap3D (Đang là nền tảng Web độc lập).
*   **Người dùng chính:** Developers đang onboarding dự án mã nguồn mở.
*   **Quy trình chính (Workflows):** 
    1. *Đọc hiểu kiến trúc tổng thể (Onboarding):* Paste link -> AI vẽ map -> Dev nắm luồng đi.
    2. *Trace lỗi / Đọc logic (Code Navigation):* Click vào hàm khó trên map -> AI giải thích logic -> Dev lấy insight để viết code tiếp.

### PHẦN B — Chẩn Đoán Nguyên Nhân Gốc
*   **Lăng kính (Lens):** Quy trình công việc (Workflow) & ADKAR (Ability/Friction).
*   **Chẩn đoán:** Giải pháp tách rời trên nền tảng Web đi ngược lại luồng làm việc thực tế của Dev (vốn chỉ ở trên VS Code hoặc Terminal). Việc phải "ra khỏi IDE để hỏi AI" tạo rào cản quá lớn.
*   **Bài học từ Case Study:** Rút bài học từ KPMG/JPMorgan (Dashboard đo usage bị tối ưu sai) và IBM Watson (Model giỏi nhưng không khớp với workflow thực tế của bác sĩ sẽ bị khai tử).

### PHẦN C — Giải Pháp Và Lộ Trình 30/60/90 ngày
*   **Giải pháp (Tactics):**
    *   *Move 3 (Cut the red tape):* Giảm friction bằng cách biến RepoMap3D thành **VS Code Extension**, đặt ngay cạnh editor của Dev thay vì Web App.
    *   *Move 5 (Prioritize high-impact tasks):* Bỏ tập trung vào vẽ 3D lấp lánh, tập trung vào text-based tree-map và "Click-to-Explain" ngay trong IDE.
*   **Lộ trình (Roadmap):**
    *   **0-30 ngày:** Pilot bản VS Code Extension cho 1 team nội bộ (5 devs).
    *   **31-60 ngày:** Theo dõi chỉ số Time-to-first-commit (TTFC) của team pilot so với team không dùng.
    *   **61-90 ngày:** Nếu TTFC giảm > 40%, rollout toàn công ty.

### PHẦN D — Dashboard Đo ROI Của Sản Phẩm (Đã sửa V2)
| Thang đo | Chỉ số thực tế sẽ đo | Nguồn dữ liệu |
| :--- | :--- | :--- |
| **Activation** | Tỷ lệ Dev install VS Code Extension & Authenticate. | VS Code Marketplace Analytics |
| **Engagement** | Số lần dùng "Click-to-Explain" trong phiên làm việc. | Extension Telemetry |
| **Productivity** | **Thời gian Time-to-first-commit (TTFC).** (Từ 14 ngày -> <3 ngày) | Jira / Github Commit Logs |
| **Quality / Trust** | Tỷ lệ code do AI suggest KHÔNG bị revert/sửa lại khi Review PR. | Github Pull Request Data |
| **Value (ROI)** | Số giờ kỹ sư tiết kiệm được / tháng x Lương trung bình. | CFO Report |

### PHẦN E — Rủi Ro Từ Red-Team & Phần Sửa Đổi
| Vai trò Red-Team | Rủi ro bị chất vấn (Bản V1) | Nhóm sửa gì ở V2 |
| :--- | :--- | :--- |
| **CFO** | "Chỉ số *Số lượt dán link Github* không chứng minh ra tiền. Paste nhiều có khi do tool chậm hoặc load lỗi." | **Sửa V2:** Bỏ chỉ số Usage (lượt dán link). Thay bằng chỉ số Outcome là **Time-to-first-commit**. |
| **Người dùng** | "Bắt tôi mở Chrome dán link lúc đang code là ép uổng, context switching rất mệt mỏi." | **Sửa V2:** Pivot sản phẩm từ Web App sang VS Code Extension (Tích hợp workflow). |
| **Risk / Legal** | "Nếu AI giải thích auth logic sai, Dev code theo bị hack thì ai chịu?" | **Sửa V2:** Thêm chỉ số Quality (Tỷ lệ PR bị reject) làm chốt chặn. |

### PHẦN F — Memo Quyết Định (Decision Memo)
1.  **Quyết định:** Đề xuất **PIVOT (Đổi hướng)** giao diện từ Web App sang IDE Extension để bám sát Workflow.
2.  **Chỉ số mạnh nhất bảo vệ quyết định:** Time-to-first-commit (TTFC) - Đây là chỉ số đo lường hiệu suất (Productivity) thực tế nhất báo cáo được cho CFO.
3.  **Giả định yếu nhất trong V1:** Tưởng rằng "giao diện 3D đẹp" là đủ động lực (Desire) để Dev thay đổi thói quen làm việc hàng ngày.
4.  **Việc cần làm trước khi Scale:** Đóng băng việc code Web, tung bản Extension tinh gọn để test với 1 nhóm 5 người dùng thử.
