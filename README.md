## I. Lý thuyết

### 1. API là gì, API testing là gì, bao gồm các thành phần nào, phân biệt với GUI testing

API là viết tắt của Giao diện lập trình ứng dung (Application Programming Interface). API là trung gian phần mềm cho phép hai ứng dụng giao tiếp với nhau, có thể sử dụng cho web-based system, operating system, database system, computer hardware, or software library

ở dạng đơn giản nhất, API là giao diện cho phép một úng dụng giao tiêp với ứng dụng khác thông qua các lệnh đơn giản và các lệnh này được gửi định dạng mà dữ liệu được truy xuất thông qua API có thể khác với API SOAP hoặc REST

API testing là một phương pháp kiểm thử phần mềm bao gồm kiểm tra trực tiếp giao giện lập trình ứng dụng (API) mà không tác động tới client. Test API còn là một phần của kiểm thử tích hợp nhằm xác định các API có đáp ứng kỳ vọng về chức năng, độ tin cậy, hiệu suất và bảo mật không  

Testing Restful API bao gồm các khía cạnh
* Chức năng
* Tin cậy
* Hiệu năng
* Bảo mật

Phân biệt API testing và GUI testing

API testing phù hợp hơn cho test automation và test liên tục (đặc biệt trong Agile và DevOps) so với GUI testing. Bởi vì:

Độ phức tạp của hệ thống: GUI testing không thể xác minh đầy đủ các fuctional path và API / service liên quan đến kiến trúc đa nhiệm. API được coi là giao diện ổn định nhất cho hệ thống được test.

Các chu kỳ release ngắn với các vòng phản hồi nhanh: Các nhóm Agile và DevOps làm việc với các vòng lặp ngắn (short iterations) và các vòng phản hồi nhanh (fast feedback loops) thấy rằng GUI testing  yêu cầu làm lại đáng kể để theo kịp sự thay đổi thường xuyên. Testing ở lớp API ít hơn và dễ bảo trì hơn.

Vì những lý do này, chúng ta nên tăng API testing và giảm sự phụ thuộc vào GUI testing. API testing được khuyến nghị cho phần lớn các automation test và thử nghiệm càng nhiều càng tốt. GUI testing sau đó được dành riêng để xác thực các trường hợp ở system level, mobile testing, và usability testing.

### 2. Restful API là gì, một số tiêu chuẩn khi test Restful API

Restful API là phần lõi cua hầu hết ứng dụng hiện tại, Rest API cung cấp cách thức để các hệ thống giao tiếp với nhau trên môi trường web 

Tiêu chí khi test Restful API 
- Các API sẽ được cung cấp cho một tài nguyên vd: users, products
- Danh sách các API cần cung cấp  list users, read user, tạo user, 
- Chuẩn method của API: GET, POST, PUT, DELETE
- Quy ước đặt path của các API:  /users, /users/:id
- Format đầu vào của các API:

  * API GET list users: truyền query params: /users?page=1&limit=20
  * API GET 1 user: truyền path variable: /users/100
  * API POST 1 user: truyền request body:  /users
  * API PUT 1 user: truyền request body:  /users
  * API DELETE 1 user: truyền path variable: /users/100

- Chuẩn các status code:
  * 2xx: thành công
  * 3xx: chuyển hướng
  * 4xx: lỗi của người dùng
  * 5xx: lỗi của server


- Chuẩn kết quả đầu ra của các API

  * Status code valid
  * API GET list users: trả ra list + phân trang + status code 200
  * API GET 1 user: trả về 1 user + status code 200
  * API POST 1 user: trả về 1 user sau khi tạo + status code 201 Created
  * API PUT 1 user: trả về 1 user sau khi update + status code 200 
  * API DELETE 1 user: không trả về cái gì hết + status code 200



### 3. Phân biệt query params, path variable, request body trong một Restful API request, cho ví dụ (có thể dùng postman)

* Query params:

Là các tham số được truyền vào URL sau dấu ?. Dùng để truyền các thông tin bổ sung cho API, ví dụ như bộ lọc, phân trang, sắp xếp.

Ví dụ: /api/users?page=2

*  Path variable:

 Path variable là một phần trong đường dẫn URL, ví dụ GET /users/123/info thì 123 là path variable.

* Request body:

Request method PUT, POST mới có request body, đây là nơi chứa data chính để gửi lên. Thường thì request body sẽ ở dạng JSON hoặc form-data, khi vào controller sẽ được tự động parse ra thành Object 

* Json là gì, cho ví dụ

JavaScript Object Notation (thường được viết tắt là JSON) là một kiểu dữ liệu mở trong JavaScript. Kiểu dữ liệu này bao gồm chủ yếu là văn bản, có thể đọc được theo dạng cặp "thuộc tính - giá trị". Về cấu trúc, nó mô tả một vật thể bằng cách bọc những vật thể con trong vật thể lớn hơn trong dấu ngoặc nhọn ({ }). JSON là một kiểu dữ liệu trung gian, chủ yếu được dùng để vận chuyển thông tin giữa các thành phần của một chương trình

Ví dụ: 
{
    "data": {
        
        "id": 2,
        "email": "janet.weaver@reqres.in",
        "first_name": "Janet",
        "last_name": "Weaver",
        "avatar": "https://reqres.in/img/faces/2-image.jpg"
    },
    "support": {
        "url": "https://reqres.in/#support-heading",
        "text": "To keep ReqRes free, contributions towards server costs are appreciated!"
    }

## 2. Thực hành
- Cài đặt phần mềm postman

