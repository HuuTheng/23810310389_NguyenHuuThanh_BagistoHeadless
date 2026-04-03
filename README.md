Dưới đây là nội dung trả lời ngắn gọn, đúng trọng tâm kỹ thuật để em đưa vào báo cáo:

### 1. So sánh sự khác biệt về lưu lượng dữ liệu (Payload)
Trong bài làm của em, sự khác biệt thể hiện rõ qua hai khía cạnh:
* **REST API (Over-fetching):** Khi gọi endpoint sản phẩm, hệ thống trả về toàn bộ cấu trúc dữ liệu (hàng chục trường như mô tả, cấu hình thuế, tồn kho...). Điều này làm tăng kích thước Payload không cần thiết, gây lãng phí băng thông và làm chậm tốc độ tải trang.
* **GraphQL (Cấu trúc tối ưu):** Em chỉ yêu cầu các trường cụ thể như `name`, `price`. Server chỉ đóng gói đúng các trường này vào JSON. Kết quả là Payload cực kỳ nhẹ, giúp giảm độ trễ mạng và cải thiện hiệu năng ứng dụng Frontend đáng kể.

### 2. Thay đổi giá sản phẩm: Query hay Mutation?
Em sẽ sử dụng **Mutation**.

* Trong GraphQL, **Query** chỉ được dùng cho các hành động **đọc** (Read) và lấy dữ liệu mà không làm thay đổi trạng thái của hệ thống.
* **Mutation** là loại hành động bắt buộc khi muốn **thay đổi** (Write/Update) dữ liệu trên server, bao gồm thêm mới, xóa hoặc cập nhật thông tin như giá sản phẩm. Việc dùng Mutation giúp đảm bảo tính nhất quán của dữ liệu và cho phép Server thực hiện các logic kiểm tra (Validation) trước khi ghi đè giá mới vào Database.
