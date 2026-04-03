 

IV. CÂU HỎI BẮT BUỘC
1. So sánh sự khác biệt về lưu lượng dữ liệu (Payload) giữa REST API và GraphQL trong bài làm:

Trong quá trình thực hiện, sự khác biệt về Payload thể hiện rất rõ rệt:

Với REST API (Over-fetching): Khi gọi một Endpoint sản phẩm thông thường, server sẽ trả về toàn bộ các trường dữ liệu mặc định (hàng chục trường như: mô tả chi tiết, cấu hình thuế, cân nặng, kích thước, trạng thái kho...). Điều này tạo ra một lượng dữ liệu thừa lớn, gây lãng phí băng thông và tăng thời gian phản hồi của hệ thống.

Với GraphQL (Cấu trúc tối ưu): Em chỉ yêu cầu các trường cụ thể phục vụ giao diện Card như name, price, và sku. Server Bagisto chỉ đóng gói đúng các trường này vào file JSON trả về. Kết quả là dung lượng Payload giảm xuống mức tối thiểu, giúp ứng dụng Frontend load dữ liệu cực nhanh và giảm tải cho đường truyền mạng.

2. Thay đổi giá của một sản phẩm qua Headless API: Query hay Mutation?

Em sẽ sử dụng hành động Mutation.

Giải thích: * Trong GraphQL, Query được thiết kế riêng cho các hành động đọc (Read) dữ liệu, tức là chỉ lấy thông tin về mà không làm thay đổi trạng thái của hệ thống trên Server.

Ngược lại, Mutation là loại hành động dùng để thực hiện các thay đổi dữ liệu (Write/Update/Delete) trên Server. Việc thay đổi giá sản phẩm là một hành động cập nhật cơ sở dữ liệu, do đó bắt buộc phải dùng Mutation. Sử dụng Mutation cũng giúp hệ thống thực hiện các bước kiểm tra (Validation) và đảm bảo tính toàn vẹn của dữ liệu trước khi ghi đè giá mới vào hệ thống Bagisto.
