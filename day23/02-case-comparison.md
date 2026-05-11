# Bảng So Sánh Case Thành Công / Thất Bại (Bài 2)

Dưới đây là phần phân tích so sánh giữa 1 case thành công và 1 case thất bại/cảnh báo khi triển khai AI, dựa trên tài liệu tham khảo của chương trình.

| Trường | Case thành công: Morgan Stanley | Case thất bại/cảnh báo: KPMG |
| :--- | :--- | :--- |
| **Case** | Morgan Stanley triển khai AI Assistant cho tư vấn viên quản lý tài sản (Wealth Management). | KPMG ra mắt Dashboard theo dõi nhân viên tư vấn sử dụng AI và trao thưởng. |
| **AI được dùng trong quy trình nào?** | Tìm kiếm và truy xuất thông tin từ kho tri thức nội bộ khổng lồ để tư vấn cho khách hàng. | Các tác vụ văn phòng và tư vấn hàng ngày của nhân viên (không quy định cụ thể quy trình). |
| **Họ đo chỉ số gì?** | Các chỉ số về chất lượng và độ an toàn (Trust/Quality) thông qua vòng phản hồi của chuyên gia và hệ thống compliance. | Tần suất sử dụng, số lượng prompt và thời gian mở công cụ AI (Usage metrics). |
| **Chỉ số đó chứng minh được gì?** | Chứng minh được hệ thống an toàn, output đáng tin cậy để sử dụng trong một ngành rủi ro cực cao (Tài chính). | Chứng minh được nhân viên có mở tool và có tương tác với tool. |
| **Chỉ số đó chưa chứng minh được gì?** | Chưa chứng minh được tác động cuối cùng đến business như: khách hàng ở lại nhiều hơn không (retention), doanh thu tăng không. | Chưa chứng minh được chất lượng công việc có tốt lên không, hay thời gian xử lý công việc có thực sự giảm không. |
| **Thiếu chỉ số nào?** | Business Value: Cost per task, Client retention rate, Revenue lift. | Productivity & Quality: Cycle time (thời gian hoàn thành task), Tỷ lệ lỗi, Outcome quality. |
| **Bài học cho dashboard nhóm** | Phải đo lường/thiết kế chỉ số "Trust" và "Quality" trước khi triển khai rộng. Không thể hy sinh sự chính xác vì tốc độ. | Không bao giờ dùng usage (lượt dùng, số prompt) làm KPI hay điều kiện thưởng, vì user sẽ "chạy số" (spam prompt) thay vì tạo ra giá trị thực. |

**1 bài học nhóm sẽ áp dụng ngay:**  

> Nhóm sẽ không sử dụng các Active Users, Prompt Count hay Login Count làm chỉ số đo lường thành công (vì dễ dẫn đến bẫy chạy số như KPMG). Thay vào đó, nhóm sẽ đo lường **Tỷ lệ xử lý công việc nhanh hơn (Productivity)** bắt buộc đi kèm với **Tỷ lệ không sai sót (Quality)**.
