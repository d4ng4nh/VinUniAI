**Dự án:** RepoMap3D - AI 3D Architecture Map cho Github Repo

| Trường | Mô tả chi tiết |
| :--- | :--- |
| **Tình huống** | Developer dùng RepoMap3D (phiên bản Web App) để dán link Github nhằm phân tích và đọc hiểu kiến trúc của một dự án mã nguồn mở khổng lồ trước khi viết code. |
| **Ai là người dùng chính?** | Developers (Junior/Mid-level) và Tech Lead đang trong quá trình Onboarding vào dự án mới. |
| **Dấu hiệu bị kẹt** | Trong tuần đầu tiên, lượng người dùng dán link Github rất cao (hiệu ứng "Wow" với bản đồ 3D). Nhưng sang tuần thứ 2, họ xem xong bản đồ rồi tắt Web, quay lại VS Code để code chay và mò mẫm lỗi thủ công. Tính năng "Click-to-Explain" sinh ra giá trị lớn nhất lại bị bỏ xó. |
| **Vì sao bạn nghĩ nó bị kẹt?** | (1) Kẹt ở lăng kính **Workflow**: Bắt Dev chuyển qua lại (context switching) giữa IDE làm việc (VS Code) và Trình duyệt Web gây ra lực cản (friction) lớn. <br>(2) Kẹt ở lăng kính **Metrics**: Chỉ số "Số lượng link dán" chỉ đo được sự tò mò (Activation), không chứng minh được AI đã đi vào quy trình làm việc thường ngày (Normalization). |

