**Bảng điểm RICE (5 tính năng cốt lõi)**
*(Giả định: R = Reach (User/tháng), I = Impact (0.25-3), C = Confidence (%), E = Effort (Person-month))*.

| Tính năng | Mô tả từ Demo | Reach | Impact | Confidence | Effort | RICE Score |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **1. Fast Repo Scanner (Agent 1)** | Paste link là quét được ngôn ngữ, đếm file không cần signup. | 1000 | 3 | 100% | 1 | **3000** |
| **2. Call-Graph Extractor (Agent 2)** | Đọc từng file, tìm ra hàm nào gọi hàm nào để tạo mạng lưới liên kết. | 800 | 3 | 80% | 2 | **960** |
| **3. 3D Architecture Renderer** | Gom cụm file và vẽ bản đồ 3D trực quan phân chia các tầng (UI, Logic, DB). | 800 | 3 | 60% | 3 | **480** |
| **4. Click-to-Explain (Agent 3)** | Click vào 1 khối (vd: API), AI tóm tắt bằng "tiếng người" chức năng của khối đó. | 500 | 2 | 80% | 1 | **800** |
| **5. Github PR Auto-Reviewer** | Tính năng mở rộng: Tự động review code khi có Pull Request mới. | 100 | 1 | 50% | 4 | **12.5** |

**Ma trận 2x2 Value-Effort**:
*   **Quick Wins (Làm ngay):** Fast Repo Scanner (Agent 1), Click-to-Explain (Agent 3) - Thấy ngay "Aha moment" trong 3 phút.
*   **Strategic Bets (Đầu tư dài hạn làm moat):** Call-Graph Extractor, 3D Architecture Renderer.
*   **Fill-ins (Làm khi rảnh):** Không có trong scope hiện tại.
*   **Non-starters (Bỏ thẳng):** Github PR Auto-Reviewer (Lệch focus khám phá mã nguồn, tốn nguồn lực).