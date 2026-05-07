# RISK REGISTER (3 RISKS CỐT LÕI)
*Giả định Burn Rate = 250 triệu VNĐ/tháng. 1 tháng runway = 250 triệu VNĐ.*

| # | Type | Risk Scenario (If - Then - Leading to) | Likelihood (1-5) | Impact (Runway lost) | Score |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | **Vendor** | **If** Anthropic đột ngột siết Rate Limit cho tier hiện tại (như từng làm) khiến hệ thống quét 5,000 files bị nghẽn,<br>**Then** toàn bộ app sập trong 2 ngày, phải đền bù SLA cho 1,000 paying users,<br>**Leading to** mất 125 triệu VNĐ doanh thu và chi phí engineering chuyển đổi sang OpenAI = **0.5 tháng runway.** | 4 | 1 | **4** (Accept/ Watch) |
| 2 | **Customer-facing** | **If** Agent 3 (Click-to-Explain) ảo giác (hallucinate) và giải thích sai logic của một file `auth.ts` bảo mật,<br>**Then** Developer tin lời AI, viết code có lỗ hổng và bị hack database,<br>**Leading to** khách hàng kiện đòi bồi thường thiệt hại và hủy gói = 1 tỷ VNĐ = **4 tháng runway.** | 3 | 4 | **12** (Mitigate) |
| 3 | **Founder-bandwidth** | **If** Tech Founder (người duy nhất nắm logic AST Parser) bị ốm nằm viện 1 tuần đúng lúc Github update cấu trúc GraphQL API,<br>**Then** tính năng quét repo chết cứng, team không ai biết sửa,<br>**Leading to** 30% user rời bỏ sang tool đối thủ (Churn) = 750 triệu VNĐ = **3 tháng runway.** | 3 | 3 | **9** (Mitigate) |
