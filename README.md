# Tìm hiểu EmberJS

## 1. Định nghĩa
- Ember.js là một mã nguồn mở JavaScript phía client khuôn khổ cho việc phát triển các ứng dụng web và sử dụng các cấu trúc mô hình MVC (Model-View-Controller).
## 2. Thuận lợi khi sử dụng EmberJS
- Mã nguồn mở. 
- Linh hoạt, có thể tăng hiệu năng của ứng dụng mà không cần phải load lại cả trang. 
- Sử dụng các thư viện tương tự như HTML. 
- Ứng dụng dùng Ember.js có kích cỡ nhỏ hơn dùng các thư viện khác. 
- Các thuộc tính ràng buộc được hỗ trợ đầy đủ, ví dụ khi đã tạo tạo liên kết giữa 2 thuộc tính, 1 cái thay đổi, cái còn lại được update theo thành giá trị mới. 
## 3. Cài đặt môi trường Ember.js
 Có 2 cách để cài đặt cấu hình Ember.js: 
- Tải các thư viện JavaScript. 
- Sử dụng CDN (Content Delivery Network). Trong đó CDN là một hệ thống máy chủ trên toàn cầu (số lượng tùy theo mỗi nhà cung cấp dịch vụ) làm nhiệm vụ lưu bản sao của các nội dung tĩnh bên trong website, sau đó phân tán nó ra nhiều máy chủ khác (được gọi là PoP – Points of Presence) và từ các PoP đó nó sẽ gửi tới cho người dùng khi họ truy cập vào website. Khi một tập tin được phân phối bởi CDN, người dùng truy cập vào nó thì PoP phân phối gần nhất so với người dùng sẽ trả nội dung về cho người dùng xem. 
## 4. Kiến trúc Ember.js
Kiến trúc của Ember.js về cơ bản bao gồm các thành phần: 
- Template 
- Route 
- Model 
- View 
- Controller 

Trong đó: 
- Template: Mô tả các giao diện người dùng của ứng dụng. Ember.js cung cấp thư viện Handlebar template để xây dựng các ứng dụng front-end, giống như HTML thông thường. Có thể trực tiếp nhúng templates vào các thẻ HTML. Mỗi template được hỗ trợ bởi một model, và các template tự động cập nhật nếu các model thay đổi. 
- Route: Một route là một đối tượng mà nó sẽ làm cho template hiển thị thông tin theo model quy định. Các router dịch một URL vào một loạt các template lồng nhau, mỗi template được hỗ trợ bởi một model. Nếu templates hoặc models thay đổi do người dùng thay đổi, Ember tự động cập nhật URL trên thanh URL của trình duyệt. Điều này có nghĩa rằng, vào thời điểm bất kỳ, người dùng có thể chia sẻ các URL của ứng dụng. Khi ai đó nhấp chuột vào liên kết, họ đang xem nội dung tương tự như người chia sẻ đã thấy. 
- Model: Model là một đối tượng được lưu trong persistent state. Template có trách nhiệm hiển thị các mô hình cho người dùng bằng cách biến nó thành HTML. Các model và route được liên kết với nhau bởi vì model thực hiện các route bằng cách đi qua như là đối số mỗi khi route được gọi đến. 
- View: Xử lý sự kiện người dùng và cập nhật DOM. 
- Controller: Controller quản lý logic hiển thị của model và cũng kiểm soát các hoạt động giữa các route, model, và view. Nó lấy model từ route và tạo ra các kết nối giữa các view, model, and template. Ember.js tự động sinh ra controller.


# Cài đặt TaskApp đơn giản

- Cài đặt Ember CLI
Nhập vào command line:
```sh
$ npm install -g ember-cli
```
Lúc này, Ember command đã được cài đặt trong console. Kiểm tra lại bằng cách:
```sh
$ ember -v
```
Ta sẽ nhận được trên màn hình như sau:
```sh
version: 2.12.1
node: 6.10.2
os: win32 x64
```

- Tạo ứng dụng
Khởi tạo ứng dụng mới: 
```sh
$ ember new my_app
```
Chuyển đến đường dẫn của ứng dụng vừa tạo:
```sh
$ cd my_app
```
- Khởi chạy ứng dụng
Ứng dụng cơ bản đã được thiết lập để có thể chạy được trên trình duyệt. Nhập vào terminal:
```sh
$ ember server
```
Mở trình duyệt vào vao địa chỉ http://localhost:4200 để truy cập.
