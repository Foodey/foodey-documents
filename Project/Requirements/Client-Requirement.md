## Client Requirement

Một chủ đầu tư muốn triển khai một hệ thống bán đồ ăn trực tuyến (Online Food-selling System: “Foodey”) tương tự như các sàn thương mại điện tử về F&B như hiện nay (ShopeeFood, Now, GrabFood,...) với mong muốn có thể hợp tác mở rộng quy mô kinh doanh với các chuỗi nhà hàng hiện có cũng như tạo một sàn thương mại cho các nhà hàng nhỏ lẻ.

Hệ thống hoạt động như sau:

- Quản trị viên của hệ thống (System Admin) sẽ là người quản lý tất cả hoạt động diễn ra trên trang web.
- Chủ nhà hàng (Shop Owner) – có thể là các ông chủ của chuỗi nhà hàng như Highlands Coffee, The Coffee House, Phúc Long,… hoặc những cửa hàng buôn bán nhỏ lẻ như các quán hủ tiếu, cơm tấm bình dân,… – là những người có quyền đăng ký trở thành người dùng với vai trò SO với điều kiện phải thoả mãn các chính sách về pháp lý để có thể được chấp thuận và duyệt thông qua bộ phận SA.
- Thực khách (Customer) là những người có thể đăng ký hoặc không đăng ký tài khoản để đặt đồ ăn thông qua hệ thống. Điều kiện với những người dùng không đăng ký tài khoản là phải để lại các thông tin như Tên, Số điện thoại, Địa chỉ giao hàng.
- Người giao hàng (Shipper) có trách nhiệm đảm bảo việc giao hàng thực phẩm từ nhà hàng đến khách hàng diễn ra một cách trơn tru và đúng thời gian. Vai trò chính của DD nhận giao các đơn hàn mà Cm đã đặt ở các cửa hàng của SO.

### Functional Requirements

Mỗi người dùng có thể:

- Đăng ký/đăng nhập
- Lấy lại mật khẩu đã quên
- Chỉnh sửa thông tin tài khoản

#### Customer

- Các chức năng chính:
- Xem danh sách các cửa hàng
- Tra cứu các cửa hàng
- Xem danh sách các món ăn
- Tra cứu các món ăn
- Xem thông tin món ăn
- Thêm món ăn vào giỏ hàng
- Chỉnh sửa số lượng/Xoá món ăn trong giỏ hàng
- CRUD thông tin giao hàng
- Áp dụng phương thức thanh toán
- Áp dụng các mã giảm giá
- Đặt hàng
- Huỷ đơn hàng
- Theo dõi trạng thái đơn hàng
- Liên hệ với Show Owner thông qua hotline
- Đánh giá đơn hàng
- Xem lịch sử mua hàng
- CRUD danh sách yêu thích
- Đánh giá cửa hàng, shipper

#### Shop Owner

- Đăng ký thông tin cửa hàng trên sàn Foodey
- CRUD thông tin cửa hàng
- CRUD các món ăn của cửa hàng
- CRUD các mã giảm giá
- Hiển thị danh sách món ăn khi nhấn vào xem menu của cửa hàng
- Điều chỉnh trạng thái đơn đặt hàng và hiển thị cho Customer
- Theo dõi tình trạng đơn hàng của Customer
- Liên hệ với Customer thông qua số điện thoại
- Theo dõi các đánh giá từ Customer
- Xem báo cáo doanh thu và lợi nhuận theo tháng/quý/năm

**NOTE**: Nếu là một chuỗi nhà hàng,

- Đăng ký nhiều cửa hàng trên sàn Foodey.
- Hiển thị danh sách chi nhánh các cửa hàng đã đăng ký
- CRUD thông tin các chi nhánh

#### Shipper

- Đăng ký thông tin cá nhân và phương tiện sử dụng để giao hàng trên sàn Foodey
- Nhận được đơn đặt hàng của khách hàng trong phạm vi bán kính 5km
- Lựa chọn chấp thuận hoặc từ chối nhận đơn hàng
- Xem thông tin địa chỉ nhà hàng cũng như thông tin chi tiết đơn hàng mà Customer đã đặt ở nhà hàng đó
- Xem thông tin địa chỉ và số điện thoại của khách hàng để liên lạc giao hàng
- Ứng dụng hiển thị một bản đồ chỉ dẫn tới địa chỉ của nhà hàng cũng như đến địa chỉ giao hàng của Customer.

#### System Admin

- Tương tác với Shop Owner
- Tương tác với Shipper
- Xác thực thông tin đăng ký của các cửa hàng
- Xác thực thông tin đăng ký của các Shipper
- Lập danh sách các cửa hàng đã đăng ký thành công
- Tra cứu cửa hàng
- Tra cứu các Shipper
- Xem lợi nhuận kiếm được từ tiền hoa hồng của các cửa hàng và shipper