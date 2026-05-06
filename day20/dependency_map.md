**Bản đồ Rủi ro và Đường găng (Critical Path)**

**A. 3 External Dependencies & Plan B:**
1.  **Github API Rate Limit:** Quét repo 5,000 file rất dễ bị chặn API.
    *   *Worst-case:* App sập vì Github chặn IP.
    *   *Plan B:* Yêu cầu user tự nhập Personal Access Token (PAT) nếu repo quá lớn. *Cost:* Làm giảm trải nghiệm frictionless.
2.  **LLM Context Window & Token Cost (OpenAI/Anthropic):** Gom cụm hàng ngàn file sẽ đốt token khổng lồ.
    *   *Worst-case:* Vượt budget token hoặc dính Rate Limit của LLM provider.
    *   *Plan B:* Agent 1 và 2 chỉ trích xuất Abstract Syntax Tree (AST) bằng code Python thuần (Rule-based), chỉ dùng LLM ở Agent 3 để gen text "tiếng người". *Cost:* Tốn 2 tuần dev lại luồng AST.
3.  **Thư viện Render 3D (WebGL/Three.js):**
    *   *Worst-case:* Render 3D map trên trình duyệt của máy yếu bị crash.
    *   *Plan B:* Tự động fallback sang giao diện 2D Map nếu detect FPS của trình duyệt rớt xuống dưới 30. *Cost:* Trải nghiệm kém "wow" hơn.

**B. Critical Path (Đường găng cho cột NOW):**
(1) Setup luồng kéo data từ Github API (không signup) -> **(2) Build Agent 1 (Quét ngôn ngữ/file) -> (3) Build Agent 2 (Trích xuất liên kết) -> (4) Build Agent 3 (Tóm tắt text)** -> (5) Render UI tương tác Click-to-Explain -> (6) Launch Demo.
