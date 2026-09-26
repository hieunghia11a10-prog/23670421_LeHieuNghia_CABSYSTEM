# CAB System – Test Cases theo Business Process

Bộ này gồm 12 Business Process × 20 Test Case = **240 Test Case**.
Phạm vi bám theo README đã hiệu đính: Customer, Driver, Driver Matching, Trip Execution, Trip Tracking, Trip History, **Vận hành/Phân quyền (Operator–Admin)** và **Hủy chuyến**.

---

## BP-01 – Đăng ký tài khoản khách hàng

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP01-001 | BP-01 – Đăng ký tài khoản khách hàng | Đăng ký với thông tin hợp lệ | Tài khoản chưa tồn tại | 1. Mở màn hình đăng ký 2. Nhập đầy đủ thông tin 3. Nhấn Đăng ký | Thông tin khách hàng hợp lệ | Tạo tài khoản thành công; trạng thái tài khoản được thiết lập theo rule | Medium |
| TC-BP01-002 | BP-01 – Đăng ký tài khoản khách hàng | Đăng ký với email đã tồn tại | Đã có tài khoản dùng email tương ứng | 1. Nhập thông tin 2. Nhấn Đăng ký | Email: user01@example.com | Không tạo tài khoản; hiển thị lỗi email đã tồn tại | Medium |
| TC-BP01-003 | BP-01 – Đăng ký tài khoản khách hàng | Đăng ký với username đã tồn tại | Đã có username tương ứng | 1. Nhập thông tin 2. Nhấn Đăng ký | Username: user01 | Không tạo tài khoản; thông báo username đã tồn tại | Medium |
| TC-BP01-004 | BP-01 – Đăng ký tài khoản khách hàng | Bỏ trống username | Đang ở màn hình đăng ký | 1. Bỏ trống username 2. Nhập các trường khác 3. Đăng ký | Username: empty | Hiển thị lỗi bắt buộc nhập username | Medium |
| TC-BP01-005 | BP-01 – Đăng ký tài khoản khách hàng | Bỏ trống password | Đang ở màn hình đăng ký | 1. Nhập username 2. Bỏ trống password 3. Đăng ký | Password: empty | Hiển thị lỗi bắt buộc nhập password | Medium |
| TC-BP01-006 | BP-01 – Đăng ký tài khoản khách hàng | Bỏ trống trường bắt buộc | Đang ở màn hình đăng ký | 1. Bỏ trống một trường bắt buộc 2. Đăng ký | Một trường bắt buộc: empty | Không tạo tài khoản; hiển thị validation | Medium |
| TC-BP01-007 | BP-01 – Đăng ký tài khoản khách hàng | Password không đạt quy tắc | Quy tắc password đã được định nghĩa | 1. Nhập password không hợp lệ 2. Đăng ký | Password: 123 | Từ chối dữ liệu và hiển thị lỗi password | Medium |
| TC-BP01-008 | BP-01 – Đăng ký tài khoản khách hàng | Email sai định dạng | Đang ở màn hình đăng ký | 1. Nhập email sai định dạng 2. Đăng ký | Email: user@@example | Hiển thị lỗi định dạng email | High |
| TC-BP01-009 | BP-01 – Đăng ký tài khoản khách hàng | Số điện thoại sai định dạng | Quy tắc số điện thoại đã xác định | 1. Nhập số điện thoại sai 2. Đăng ký | Phone: abc123 | Hiển thị lỗi số điện thoại | High |
| TC-BP01-010 | BP-01 – Đăng ký tài khoản khách hàng | Username chứa ký tự không hợp lệ | Đang ở màn hình đăng ký | 1. Nhập username có ký tự không cho phép 2. Đăng ký | Username: user@@@ | Từ chối username và hiển thị lỗi | High |
| TC-BP01-011 | BP-01 – Đăng ký tài khoản khách hàng | Hai mật khẩu không khớp | Có trường xác nhận password | 1. Nhập password 2. Nhập confirm password khác 3. Đăng ký | Password: Password@123; Confirm: Password@321 | Không tạo tài khoản; hiển thị lỗi không khớp | Medium |
| TC-BP01-012 | BP-01 – Đăng ký tài khoản khách hàng | Khoảng trắng ở đầu/cuối dữ liệu | Đang ở màn hình đăng ký | 1. Nhập dữ liệu có khoảng trắng đầu/cuối 2. Đăng ký | Username: " user01 " | Xử lý khoảng trắng đúng theo Business Rule | Medium |
| TC-BP01-013 | BP-01 – Đăng ký tài khoản khách hàng | Username quá dài | Giới hạn độ dài username đã xác định | 1. Nhập username vượt giới hạn 2. Đăng ký | Username: chuỗi vượt max length | Từ chối hoặc validation theo rule | Medium |
| TC-BP01-014 | BP-01 – Đăng ký tài khoản khách hàng | Password vượt giới hạn | Giới hạn độ dài password đã xác định | 1. Nhập password vượt giới hạn 2. Đăng ký | Password: chuỗi vượt max length | Từ chối hoặc validation theo rule | Medium |
| TC-BP01-015 | BP-01 – Đăng ký tài khoản khách hàng | Đăng ký nhiều lần với cùng dữ liệu | Tài khoản chưa tồn tại trước lần đầu | 1. Đăng ký lần 1 2. Đăng ký lại cùng dữ liệu | Cùng username/email | Lần đầu thành công; lần sau không tạo bản ghi trùng | Medium |
| TC-BP01-016 | BP-01 – Đăng ký tài khoản khách hàng | Kiểm tra password không hiển thị plaintext | Đang ở màn hình đăng ký | 1. Click ô password 2. Nhập password | Password: Password@123 | Password được mask | Medium |
| TC-BP01-017 | BP-01 – Đăng ký tài khoản khách hàng | Request thiếu username | API đăng ký đang hoạt động | 1. Gửi request 2. Bỏ trường username | {password: Password@123} | API trả lỗi validation; không tạo tài khoản | High |
| TC-BP01-018 | BP-01 – Đăng ký tài khoản khách hàng | Request thiếu password | API đăng ký đang hoạt động | 1. Gửi request 2. Bỏ trường password | {username: user01} | API trả lỗi validation; không tạo tài khoản | High |
| TC-BP01-019 | BP-01 – Đăng ký tài khoản khách hàng | Request có dữ liệu không hợp lệ | API đăng ký đang hoạt động | 1. Gửi request với dữ liệu sai | username: @@; password: 123 | API trả response lỗi phù hợp | High |
| TC-BP01-020 | BP-01 – Đăng ký tài khoản khách hàng | Không trả password trong response | Đăng ký thành công | 1. Gửi request hợp lệ 2. Kiểm tra response | Thông tin hợp lệ | Response không chứa password hoặc thông tin nhạy cảm | Medium |

## BP-02 – Đăng nhập khách hàng

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP02-001 | BP-02 – Đăng nhập khách hàng | Đăng nhập thành công | Tài khoản Active | 1. Mở Login 2. Nhập username/password 3. Login | user01 / Password@123 | Đăng nhập thành công; tạo phiên/token | Medium |
| TC-BP02-002 | BP-02 – Đăng nhập khách hàng | Username không tồn tại | Hệ thống hoạt động | 1. Nhập username không tồn tại 2. Login | unknown01 / Password@123 | Đăng nhập thất bại | High |
| TC-BP02-003 | BP-02 – Đăng nhập khách hàng | Password sai | Username tồn tại và Active | 1. Nhập username đúng 2. Nhập password sai 3. Login | user01 / Wrong@123 | Không tạo token | High |
| TC-BP02-004 | BP-02 – Đăng nhập khách hàng | Username để trống | Đang ở Login | 1. Bỏ trống username 2. Nhập password 3. Login | empty / Password@123 | Hiển thị lỗi username | Medium |
| TC-BP02-005 | BP-02 – Đăng nhập khách hàng | Password để trống | Đang ở Login | 1. Nhập username 2. Bỏ trống password 3. Login | user01 / empty | Hiển thị lỗi password | Medium |
| TC-BP02-006 | BP-02 – Đăng nhập khách hàng | Cả hai để trống | Đang ở Login | 1. Không nhập dữ liệu 2. Login | empty / empty | Hiển thị validation | Medium |
| TC-BP02-007 | BP-02 – Đăng nhập khách hàng | Username sai định dạng | Quy tắc username đã xác định | 1. Nhập username sai 2. Login | user@@@ / Password@123 | Từ chối dữ liệu | High |
| TC-BP02-008 | BP-02 – Đăng nhập khách hàng | Password sai định dạng | Quy tắc password đã xác định | 1. Nhập password sai 2. Login | user01 / 123 | Từ chối dữ liệu | High |
| TC-BP02-009 | BP-02 – Đăng nhập khách hàng | Tài khoản Locked | Tài khoản Locked | 1. Nhập thông tin đúng 2. Login | locked01 / Password@123 | Đăng nhập thất bại; thông báo tài khoản bị khóa | High |
| TC-BP02-010 | BP-02 – Đăng nhập khách hàng | Tài khoản Inactive | Tài khoản Inactive | 1. Nhập thông tin đúng 2. Login | inactive01 / Password@123 | Đăng nhập thất bại | High |
| TC-BP02-011 | BP-02 – Đăng nhập khách hàng | Username khác hoa thường | Rule case đã xác định | 1. Nhập username khác case 2. Login | User01 / Password@123 | Xử lý đúng theo rule case | Medium |
| TC-BP02-012 | BP-02 – Đăng nhập khách hàng | Password khác hoa thường | Tài khoản Active | 1. Nhập password khác case 2. Login | user01 / password@123 | Thất bại nếu password case-sensitive | Medium |
| TC-BP02-013 | BP-02 – Đăng nhập khách hàng | Password có khoảng trắng | Tài khoản Active | 1. Nhập password có khoảng trắng 2. Login | user01 / " Password@123" | Xử lý đúng theo rule | Medium |
| TC-BP02-014 | BP-02 – Đăng nhập khách hàng | Password được mask | Đang ở Login | 1. Click password 2. Nhập password | Password@123 | Password không hiển thị plaintext | Medium |
| TC-BP02-015 | BP-02 – Đăng nhập khách hàng | Đăng nhập và truy cập chức năng được cấp quyền | Tài khoản có quyền | 1. Login 2. Mở chức năng yêu cầu authentication | user01 / Password@123 | Truy cập được chức năng được cấp | High |
| TC-BP02-016 | BP-02 – Đăng nhập khách hàng | Đăng nhập sai nhiều lần | Có cơ chế bảo vệ đăng nhập | 1. Nhập password sai lặp lại | user01 / Wrong@123 | Áp dụng cơ chế khóa/giới hạn theo rule | High |
| TC-BP02-017 | BP-02 – Đăng nhập khách hàng | Request thiếu username | API Login hoạt động | 1. Gửi request 2. Bỏ username | {password: Password@123} | API trả validation error | High |
| TC-BP02-018 | BP-02 – Đăng nhập khách hàng | Request thiếu password | API Login hoạt động | 1. Gửi request 2. Bỏ password | {username: user01} | API trả validation error | High |
| TC-BP02-019 | BP-02 – Đăng nhập khách hàng | Request credential không hợp lệ | API Login hoạt động | 1. Gửi request sai | unknown / wrong | API trả lỗi; không tạo token | High |
| TC-BP02-020 | BP-02 – Đăng nhập khách hàng | Response không trả password | Login thành công | 1. Login 2. Kiểm tra response | user01 / Password@123 | Response không chứa password | Medium |

## BP-03 – Cập nhật thông tin khách hàng

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP03-001 | BP-03 – Cập nhật thông tin khách hàng | Xem thông tin cá nhân | Khách hàng đã đăng nhập | 1. Mở hồ sơ | user01 | Hiển thị đúng thông tin tài khoản | Medium |
| TC-BP03-002 | BP-03 – Cập nhật thông tin khách hàng | Cập nhật tên hợp lệ | Đã đăng nhập | 1. Mở hồ sơ 2. Sửa tên 3. Lưu | Name: Nguyễn Văn A | Cập nhật thành công | Medium |
| TC-BP03-003 | BP-03 – Cập nhật thông tin khách hàng | Cập nhật số điện thoại hợp lệ | Đã đăng nhập | 1. Sửa phone 2. Lưu | Phone: 0901234567 | Cập nhật thành công | Medium |
| TC-BP03-004 | BP-03 – Cập nhật thông tin khách hàng | Cập nhật email hợp lệ | Đã đăng nhập | 1. Sửa email 2. Lưu | Email: new@example.com | Cập nhật thành công | Medium |
| TC-BP03-005 | BP-03 – Cập nhật thông tin khách hàng | Email đã tồn tại | Email khác đã được dùng | 1. Sửa email 2. Lưu | Email: existing@example.com | Không cập nhật; báo email đã tồn tại | Medium |
| TC-BP03-006 | BP-03 – Cập nhật thông tin khách hàng | Số điện thoại sai định dạng | Đã đăng nhập | 1. Nhập phone sai 2. Lưu | Phone: abc | Hiển thị validation | High |
| TC-BP03-007 | BP-03 – Cập nhật thông tin khách hàng | Tên để trống | Trường tên bắt buộc | 1. Xóa tên 2. Lưu | Name: empty | Không cập nhật; báo lỗi | Medium |
| TC-BP03-008 | BP-03 – Cập nhật thông tin khách hàng | Email sai định dạng | Đã đăng nhập | 1. Nhập email sai 2. Lưu | Email: user@@ | Hiển thị validation | High |
| TC-BP03-009 | BP-03 – Cập nhật thông tin khách hàng | Thông tin không thay đổi | Đã đăng nhập | 1. Mở hồ sơ 2. Lưu nguyên dữ liệu | Dữ liệu hiện tại | Hệ thống xử lý ổn định, không tạo dữ liệu dư thừa | Medium |
| TC-BP03-010 | BP-03 – Cập nhật thông tin khách hàng | Dữ liệu có khoảng trắng | Đã đăng nhập | 1. Nhập dữ liệu có khoảng trắng 2. Lưu | Name: " Nguyen A " | Xử lý theo rule chuẩn hóa dữ liệu | Medium |
| TC-BP03-011 | BP-03 – Cập nhật thông tin khách hàng | Tên quá dài | Giới hạn tên đã xác định | 1. Nhập tên vượt max 2. Lưu | Chuỗi vượt max length | Validation phù hợp | Medium |
| TC-BP03-012 | BP-03 – Cập nhật thông tin khách hàng | Phone trùng tài khoản khác | Đã đăng nhập | 1. Nhập phone đã tồn tại 2. Lưu | 0909999999 | Không cập nhật nếu phone phải unique | Medium |
| TC-BP03-013 | BP-03 – Cập nhật thông tin khách hàng | Request thiếu trường bắt buộc | API update hoạt động | 1. Gửi request thiếu field | {name: Nguyen A} | API xử lý theo schema; trả lỗi nếu field bắt buộc | High |
| TC-BP03-014 | BP-03 – Cập nhật thông tin khách hàng | User chưa xác thực | Không có token | 1. Gửi request update | Authorization: absent | API từ chối truy cập | High |
| TC-BP03-015 | BP-03 – Cập nhật thông tin khách hàng | Token hết hạn | Token expired | 1. Gửi request update | Expired token | API yêu cầu đăng nhập lại | High |
| TC-BP03-016 | BP-03 – Cập nhật thông tin khách hàng | Cập nhật thành công và lấy lại hồ sơ | Đã cập nhật | 1. Update 2. Get profile | Name: Nguyen A | Thông tin mới được trả về | Medium |
| TC-BP03-017 | BP-03 – Cập nhật thông tin khách hàng | Không cập nhật thông tin của user khác | Đã đăng nhập user01 | 1. Gửi request tới user02 | Target: user02 | Bị từ chối do quyền truy cập | Medium |
| TC-BP03-018 | BP-03 – Cập nhật thông tin khách hàng | Response không chứa dữ liệu nhạy cảm | Update thành công | 1. Kiểm tra response | User profile | Không trả password/thông tin nhạy cảm | Medium |
| TC-BP03-019 | BP-03 – Cập nhật thông tin khách hàng | Hai request cập nhật liên tiếp | Đã đăng nhập | 1. Gửi update A 2. Gửi update B | Name A → Name B | Trạng thái cuối cùng nhất quán | Medium |
| TC-BP03-020 | BP-03 – Cập nhật thông tin khách hàng | Lỗi hệ thống khi lưu | DB/service tạm lỗi | 1. Cập nhật 2. Lưu | Valid profile | Thông báo lỗi; không làm sai dữ liệu hiện có | High |

## BP-04 – Tạo yêu cầu đặt xe

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP04-001 | BP-04 – Tạo yêu cầu đặt xe | Tạo booking đầy đủ thông tin | Đã đăng nhập | 1. Nhập điểm đón 2. Nhập điểm đến 3. Chọn loại xe 4. Gửi | A → B; Sedan | Booking được tạo thành công | Medium |
| TC-BP04-002 | BP-04 – Tạo yêu cầu đặt xe | Thiếu điểm đón | Đã đăng nhập | 1. Bỏ trống pickup 2. Gửi | Pickup: empty | Không tạo booking | Medium |
| TC-BP04-003 | BP-04 – Tạo yêu cầu đặt xe | Thiếu điểm đến | Đã đăng nhập | 1. Bỏ trống destination 2. Gửi | Destination: empty | Không tạo booking | Medium |
| TC-BP04-004 | BP-04 – Tạo yêu cầu đặt xe | Chưa chọn loại xe | Đã đăng nhập | 1. Nhập A/B 2. Không chọn xe 3. Gửi | Vehicle type: empty | Không tạo booking | Medium |
| TC-BP04-005 | BP-04 – Tạo yêu cầu đặt xe | Điểm đón không hợp lệ | Đã đăng nhập | 1. Nhập pickup sai 2. Gửi | Pickup: invalid | Hiển thị lỗi | High |
| TC-BP04-006 | BP-04 – Tạo yêu cầu đặt xe | Điểm đến không hợp lệ | Đã đăng nhập | 1. Nhập destination sai 2. Gửi | Destination: invalid | Hiển thị lỗi | High |
| TC-BP04-007 | BP-04 – Tạo yêu cầu đặt xe | Pickup trùng destination | Rule khoảng cách đã xác định | 1. Nhập cùng địa điểm 2. Gửi | A → A | Từ chối nếu business rule không cho phép | Medium |
| TC-BP04-008 | BP-04 – Tạo yêu cầu đặt xe | Chọn loại xe không tồn tại | Đã đăng nhập | 1. Chọn loại xe không tồn tại 2. Gửi | Vehicle: unknown | Không tạo booking | High |
| TC-BP04-009 | BP-04 – Tạo yêu cầu đặt xe | Tạo nhiều booking liên tiếp | Đã đăng nhập | 1. Tạo booking 1 2. Tạo booking 2 | A→B; C→D | Xử lý theo rule booking đang hoạt động (BRL-06/tối đa 1 chuyến mở) | Medium |
| TC-BP04-010 | BP-04 – Tạo yêu cầu đặt xe | Tạo booking khi chưa login | Không có token | 1. Gửi request booking | Authorization: absent | API từ chối | High |
| TC-BP04-011 | BP-04 – Tạo yêu cầu đặt xe | Token hết hạn khi tạo booking | Token expired | 1. Gửi request | Expired token | API yêu cầu authentication lại | High |
| TC-BP04-012 | BP-04 – Tạo yêu cầu đặt xe | Request thiếu pickup | API booking hoạt động | 1. POST request thiếu pickup | {destination: B, vehicleType: Sedan} | Validation error | High |
| TC-BP04-013 | BP-04 – Tạo yêu cầu đặt xe | Request thiếu destination | API booking hoạt động | 1. POST request thiếu destination | {pickup: A, vehicleType: Sedan} | Validation error | High |
| TC-BP04-014 | BP-04 – Tạo yêu cầu đặt xe | Request thiếu vehicle type | API booking hoạt động | 1. POST request thiếu vehicle | {pickup: A, destination: B} | Validation error | High |
| TC-BP04-015 | BP-04 – Tạo yêu cầu đặt xe | Request chứa dữ liệu không hợp lệ | API hoạt động | 1. POST dữ liệu sai | pickup: null | API trả lỗi phù hợp | High |
| TC-BP04-016 | BP-04 – Tạo yêu cầu đặt xe | Booking được tạo với trạng thái ban đầu | Dữ liệu hợp lệ | 1. Tạo booking 2. Kiểm tra response | A→B; Sedan | Booking có trạng thái khởi tạo SEARCHING | Medium |
| TC-BP04-017 | BP-04 – Tạo yêu cầu đặt xe | Booking gắn đúng customer | Customer đã login | 1. Tạo booking 2. Kiểm tra dữ liệu | user01 | Booking thuộc đúng customer | Medium |
| TC-BP04-018 | BP-04 – Tạo yêu cầu đặt xe | Không gửi thông tin nhạy cảm dư thừa | Đã login | 1. Tạo booking 2. Kiểm tra request/response | Booking data | Không chứa dữ liệu nhạy cảm không cần thiết | Medium |
| TC-BP04-019 | BP-04 – Tạo yêu cầu đặt xe | Lỗi hệ thống khi tạo booking | DB/service lỗi | 1. Gửi booking hợp lệ | A→B; Sedan | Thông báo lỗi; không tạo booking nửa chừng | High |
| TC-BP04-020 | BP-04 – Tạo yêu cầu đặt xe | Sau tạo booking hệ thống tiếp nhận yêu cầu | Tạo booking thành công | 1. Tạo booking 2. Kiểm tra trạng thái | A→B; Sedan | Booking được đưa vào luồng tìm tài xế | Medium |

## BP-05 – Đăng nhập và quản lý tài xế

> Test case ở đây giả định tài khoản tài xế đã tồn tại. Luồng *tạo* tài khoản tài xế (tự đăng ký hoặc do Nhân viên vận hành tạo) được kiểm thử ở **BP-11**.

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP05-001 | BP-05 – Đăng nhập và quản lý tài xế | Driver đăng nhập hợp lệ | Driver Active | 1. Login 2. Nhập credential | driver01 / Password@123 | Đăng nhập thành công | Medium |
| TC-BP05-002 | BP-05 – Đăng nhập và quản lý tài xế | Driver password sai | Driver tồn tại | 1. Nhập password sai | driver01 / Wrong@123 | Login thất bại | High |
| TC-BP05-003 | BP-05 – Đăng nhập và quản lý tài xế | Driver bị khóa | Driver Locked | 1. Login | locked-driver / Password@123 | Login thất bại | High |
| TC-BP05-004 | BP-05 – Đăng nhập và quản lý tài xế | Xem hồ sơ driver | Driver đã login | 1. Mở profile | driver01 | Hiển thị đúng hồ sơ | Medium |
| TC-BP05-005 | BP-05 – Đăng nhập và quản lý tài xế | Cập nhật hồ sơ hợp lệ | Driver đã login | 1. Sửa hồ sơ 2. Lưu | Name/phone hợp lệ | Cập nhật thành công | Medium |
| TC-BP05-006 | BP-05 – Đăng nhập và quản lý tài xế | Cập nhật phone sai | Driver đã login | 1. Nhập phone sai 2. Lưu | Phone: abc | Validation error | High |
| TC-BP05-007 | BP-05 – Đăng nhập và quản lý tài xế | Quản lý phương tiện hợp lệ | Driver có quyền | 1. Mở vehicle 2. Cập nhật | Biển số và loại xe hợp lệ | Thông tin xe được lưu | Medium |
| TC-BP05-008 | BP-05 – Đăng nhập và quản lý tài xế | Biển số xe trùng | Đã có vehicle cùng biển số | 1. Nhập biển số trùng 2. Lưu | Plate: 51A-12345 | Không tạo/cập nhật trùng | Medium |
| TC-BP05-009 | BP-05 – Đăng nhập và quản lý tài xế | Loại xe không hợp lệ | Danh mục loại xe đã định nghĩa | 1. Chọn loại xe không tồn tại | Vehicle type: unknown | Từ chối dữ liệu | High |
| TC-BP05-010 | BP-05 – Đăng nhập và quản lý tài xế | Bật trạng thái AVAILABLE | Driver đủ điều kiện (có xe hợp lệ) | 1. Chuyển status AVAILABLE | Status: AVAILABLE | Driver sẵn sàng nhận chuyến | Medium |
| TC-BP05-011 | BP-05 – Đăng nhập và quản lý tài xế | Tắt trạng thái AVAILABLE | Driver đang AVAILABLE | 1. Chuyển UNAVAILABLE | Status: UNAVAILABLE | Driver không được tìm cho booking mới | Medium |
| TC-BP05-012 | BP-05 – Đăng nhập và quản lý tài xế | Đổi trạng thái khi đang có chuyến | Driver đang phục vụ chuyến (BUSY) | 1. Thử chuyển UNAVAILABLE | Status: UNAVAILABLE | Từ chối hoặc xử lý theo BRL-07; không làm sai trip | Medium |
| TC-BP05-013 | BP-05 – Đăng nhập và quản lý tài xế | Driver chưa xác thực cập nhật profile | Không có token | 1. Gửi update | Authorization: absent | API từ chối | High |
| TC-BP05-014 | BP-05 – Đăng nhập và quản lý tài xế | Driver cập nhật profile của driver khác | Driver01 login | 1. Gửi target driver02 | Target: driver02 | Từ chối do quyền | Medium |
| TC-BP05-015 | BP-05 – Đăng nhập và quản lý tài xế | Request vehicle thiếu biển số | API vehicle hoạt động | 1. POST thiếu plate | {type: Sedan} | Validation error | High |
| TC-BP05-016 | BP-05 – Đăng nhập và quản lý tài xế | Request vehicle thiếu loại xe | API vehicle hoạt động | 1. POST thiếu type | {plate: 51A-12345} | Validation error | High |
| TC-BP05-017 | BP-05 – Đăng nhập và quản lý tài xế | Response không chứa password | Login thành công | 1. Kiểm tra response | driver01 credential | Không trả password | Medium |
| TC-BP05-018 | BP-05 – Đăng nhập và quản lý tài xế | Token hết hạn | Expired token | 1. Cập nhật profile | Expired token | Yêu cầu authentication lại | High |
| TC-BP05-019 | BP-05 – Đăng nhập và quản lý tài xế | Hai driver cùng cập nhật trạng thái | Hai request đồng thời | 1. Gửi AVAILABLE/UNAVAILABLE | Concurrent requests | Trạng thái cuối nhất quán | Medium |
| TC-BP05-020 | BP-05 – Đăng nhập và quản lý tài xế | Lỗi lưu vehicle | DB/service lỗi | 1. Cập nhật vehicle | Valid vehicle | Thông báo lỗi; không lưu dữ liệu dở dang | High |

## BP-06 – Tìm tài xế phù hợp

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP06-001 | BP-06 – Tìm tài xế phù hợp | Có driver AVAILABLE phù hợp | Có driver cùng loại xe | 1. Tạo booking 2. Kích hoạt matching | Sedan; Driver01 AVAILABLE | Tìm được driver phù hợp | Medium |
| TC-BP06-002 | BP-06 – Tìm tài xế phù hợp | Không có driver AVAILABLE | Không có driver sẵn sàng | 1. Tạo booking 2. Matching | Sedan | Không phân công driver; trạng thái NO_DRIVER_FOUND | Medium |
| TC-BP06-003 | BP-06 – Tìm tài xế phù hợp | Có driver nhưng sai loại xe | Driver AVAILABLE nhưng loại xe khác | 1. Matching | Customer chọn SUV; Driver Sedan | Không chọn driver sai loại | High |
| TC-BP06-004 | BP-06 – Tìm tài xế phù hợp | Driver AVAILABLE đúng loại xe | Driver đủ điều kiện | 1. Matching | Sedan; Driver01 Sedan | Driver được đưa vào danh sách phù hợp | Medium |
| TC-BP06-005 | BP-06 – Tìm tài xế phù hợp | Driver UNAVAILABLE bị loại | Driver đang UNAVAILABLE | 1. Matching | Driver01 UNAVAILABLE | Không gửi request cho driver | Medium |
| TC-BP06-006 | BP-06 – Tìm tài xế phù hợp | Nhiều driver phù hợp | Có nhiều driver AVAILABLE | 1. Matching | Driver01/02/03 Sedan | Hệ thống chọn một driver theo rule MVP | Medium |
| TC-BP06-007 | BP-06 – Tìm tài xế phù hợp | Driver gần/xa khi MVP chưa tối ưu | Có nhiều driver phù hợp | 1. Matching | Nhiều vị trí | Không yêu cầu thuật toán tối ưu ngoài phạm vi MVP (B4.4/B4.5) | High |
| TC-BP06-008 | BP-06 – Tìm tài xế phù hợp | Driver không có vehicle hợp lệ | Driver profile có vấn đề vehicle | 1. Matching | Vehicle invalid | Không chọn driver không đủ điều kiện | High |
| TC-BP06-009 | BP-06 – Tìm tài xế phù hợp | Booking thiếu loại xe | Booking invalid | 1. Chạy matching | Vehicle type: empty | Matching không thực hiện thành công | High |
| TC-BP06-010 | BP-06 – Tìm tài xế phù hợp | Booking không tồn tại | ID booking không hợp lệ | 1. Gọi matching | Booking ID: unknown | API trả lỗi không tìm thấy | High |
| TC-BP06-011 | BP-06 – Tìm tài xế phù hợp | Booking đã được assign | Booking đã có driver | 1. Matching lại | Booking assigned | Không phân công thêm driver | Medium |
| TC-BP06-012 | BP-06 – Tìm tài xế phù hợp | Booking đã completed | Trip completed | 1. Matching | Completed booking | Không tìm driver mới | Medium |
| TC-BP06-013 | BP-06 – Tìm tài xế phù hợp | Driver đã có trip active | Driver đang bận (BUSY) | 1. Matching | Driver BUSY | Không chọn driver cho booking mới | Medium |
| TC-BP06-014 | BP-06 – Tìm tài xế phù hợp | Driver vừa chuyển UNAVAILABLE | Trạng thái thay đổi trước matching | 1. Matching | Driver UNAVAILABLE | Không gửi request | Medium |
| TC-BP06-015 | BP-06 – Tìm tài xế phù hợp | Hai booking cùng tìm một driver | Có một driver phù hợp | 1. Chạy matching đồng thời | Booking A/B | Không phân công cùng driver trái rule (BRL-06) | Medium |
| TC-BP06-016 | BP-06 – Tìm tài xế phù hợp | Matching thất bại do service lỗi | Matching service lỗi | 1. Tạo booking 2. Matching | Valid booking | Thông báo lỗi; booking không bị mất | Medium |
| TC-BP06-017 | BP-06 – Tìm tài xế phù hợp | Không tiết lộ dữ liệu driver không cần thiết | Matching thành công | 1. Kiểm tra response | Driver data | Chỉ trả thông tin cần thiết | Medium |
| TC-BP06-018 | BP-06 – Tìm tài xế phù hợp | Không tìm thấy driver sau nhiều lần | Các driver đều không phù hợp | 1. Matching | No suitable driver | Trả trạng thái NO_DRIVER_FOUND | Medium |
| TC-BP06-019 | BP-06 – Tìm tài xế phù hợp | Driver đủ điều kiện được đưa vào dispatch | Có driver phù hợp | 1. Matching 2. Kiểm tra request | Driver01 | Request được gửi tới driver phù hợp | Medium |
| TC-BP06-020 | BP-06 – Tìm tài xế phù hợp | Matching gắn đúng booking | Có booking hợp lệ | 1. Matching 2. Kiểm tra ID | Booking B001 | Kết quả matching thuộc đúng booking | Medium |

## BP-07 – Tiếp nhận và phân công chuyến

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP07-001 | BP-07 – Tiếp nhận và phân công chuyến | Driver ACCEPT booking | Booking đang tìm driver | 1. Driver nhận request 2. ACCEPT | Booking B001; Driver01 | Driver được phân công | High |
| TC-BP07-002 | BP-07 – Tiếp nhận và phân công chuyến | Driver REJECT booking | Booking đang tìm driver | 1. Driver nhận request 2. REJECT | B001; Driver01 | Hệ thống tiếp tục tìm driver khác | High |
| TC-BP07-003 | BP-07 – Tiếp nhận và phân công chuyến | Driver không phản hồi | Có timeout rule | 1. Gửi request 2. Không phản hồi đến timeout | B001; Driver01 | Request hết hạn; tìm driver khác | Medium |
| TC-BP07-004 | BP-07 – Tiếp nhận và phân công chuyến | Driver thứ hai ACCEPT | Driver đầu reject | 1. Driver01 REJECT 2. Driver02 ACCEPT | B001; Driver02 | Driver02 được phân công | High |
| TC-BP07-005 | BP-07 – Tiếp nhận và phân công chuyến | Tất cả driver REJECT | Có nhiều driver | 1. Tất cả reject | B001 | Thông báo không tìm được driver | High |
| TC-BP07-006 | BP-07 – Tiếp nhận và phân công chuyến | Không còn driver sau timeout | Tất cả timeout | 1. Chờ hết timeout | B001 | Thông báo khách hàng | Medium |
| TC-BP07-007 | BP-07 – Tiếp nhận và phân công chuyến | Hai driver cùng ACCEPT | Hai request đồng thời | 1. Driver01 ACCEPT 2. Driver02 ACCEPT | B001 | Chỉ một driver được phân công | High |
| TC-BP07-008 | BP-07 – Tiếp nhận và phân công chuyến | Driver ACCEPT sau khi booking đã assign | Booking đã assigned | 1. Driver khác ACCEPT | B001 | Không thay đổi driver đã assign | High |
| TC-BP07-009 | BP-07 – Tiếp nhận và phân công chuyến | Driver REJECT sau khi đã ACCEPT | Booking đã assigned | 1. Driver gửi reject | B001 | Không làm mất assignment hợp lệ | High |
| TC-BP07-010 | BP-07 – Tiếp nhận và phân công chuyến | Booking đã cancelled/closed nhận ACCEPT | Booking không còn active | 1. Driver ACCEPT | B001 closed | Không phân công | High |
| TC-BP07-011 | BP-07 – Tiếp nhận và phân công chuyến | Driver không thuộc danh sách matching | Driver không được gửi request | 1. Gửi ACCEPT trực tiếp | Driver99 | API từ chối | Medium |
| TC-BP07-012 | BP-07 – Tiếp nhận và phân công chuyến | Request ACCEPT thiếu booking ID | API response hoạt động | 1. POST thiếu bookingId | {driverId: D01} | Validation error | High |
| TC-BP07-013 | BP-07 – Tiếp nhận và phân công chuyến | Request REJECT thiếu reason nếu reason bắt buộc | Rule reason đã xác định | 1. REJECT không reason | booking B001 | Validation error nếu rule yêu cầu; nếu không bắt buộc thì vẫn REJECT thành công | High |
| TC-BP07-014 | BP-07 – Tiếp nhận và phân công chuyến | Driver không xác thực | Không có token | 1. ACCEPT request | Authorization: absent | API từ chối | Medium |
| TC-BP07-015 | BP-07 – Tiếp nhận và phân công chuyến | Token driver hết hạn | Expired token | 1. ACCEPT | Expired token | API yêu cầu login | High |
| TC-BP07-016 | BP-07 – Tiếp nhận và phân công chuyến | Assignment ghi nhận đúng driver | Driver ACCEPT thành công | 1. ACCEPT 2. Kiểm tra booking | B001/D01 | Booking lưu đúng driver | Medium |
| TC-BP07-017 | BP-07 – Tiếp nhận và phân công chuyến | Thông báo customer khi driver nhận | Driver ACCEPT | 1. ACCEPT 2. Kiểm tra notification | B001 | Customer nhận thông báo theo rule | Medium |
| TC-BP07-018 | BP-07 – Tiếp nhận và phân công chuyến | Thông báo driver khi có booking | Driver phù hợp | 1. Matching 2. Kiểm tra notification | B001 | Driver nhận thông báo | Medium |
| TC-BP07-019 | BP-07 – Tiếp nhận và phân công chuyến | Lỗi notification không làm mất assignment | Notification service lỗi | 1. Driver ACCEPT | B001 | Assignment vẫn thành công | High |
| TC-BP07-020 | BP-07 – Tiếp nhận và phân công chuyến | Lỗi transaction khi assignment | DB/service lỗi | 1. Driver ACCEPT | B001 | Không tạo assignment dở dang | High |

## BP-08 – Thực hiện chuyến

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP08-001 | BP-08 – Thực hiện chuyến | Driver cập nhật ARRIVING | Driver đã assigned | 1. Mở trip 2. Chuyển ARRIVING | Trip T001 | Trạng thái ARRIVING | Medium |
| TC-BP08-002 | BP-08 – Thực hiện chuyến | Driver cập nhật ARRIVED | Trip ARRIVING | 1. Chuyển ARRIVED | Trip T001 | Trạng thái ARRIVED | Medium |
| TC-BP08-003 | BP-08 – Thực hiện chuyến | Driver cập nhật IN_PROGRESS | Trip ARRIVED | 1. Chuyển IN_PROGRESS | Trip T001 | Trạng thái IN_PROGRESS | Medium |
| TC-BP08-004 | BP-08 – Thực hiện chuyến | Driver cập nhật COMPLETED | Trip IN_PROGRESS | 1. Chuyển COMPLETED | Trip T001 | Trip hoàn thành | High |
| TC-BP08-005 | BP-08 – Thực hiện chuyến | Cập nhật sai thứ tự ASSIGNED → COMPLETED | Trip chưa thực hiện | 1. Gửi COMPLETED | Trip T001 | Từ chối chuyển trạng thái (BRL-11) | High |
| TC-BP08-006 | BP-08 – Thực hiện chuyến | ARRIVED → ARRIVING | Trip đã ARRIVED | 1. Gửi ARRIVING | Trip T001 | Từ chối lùi trạng thái | Medium |
| TC-BP08-007 | BP-08 – Thực hiện chuyến | COMPLETED → IN_PROGRESS | Trip đã completed | 1. Gửi IN_PROGRESS | Trip T001 | Không cho quay lại trạng thái | High |
| TC-BP08-008 | BP-08 – Thực hiện chuyến | Driver cập nhật trip của driver khác | Driver01 login; trip thuộc D02 | 1. Gửi update | Trip T002 | Từ chối quyền (BRL-10) | Medium |
| TC-BP08-009 | BP-08 – Thực hiện chuyến | Customer không được tự cập nhật trip | Customer login | 1. Gửi update status | Trip T001 | Từ chối | Medium |
| TC-BP08-010 | BP-08 – Thực hiện chuyến | Trip không tồn tại | ID không tồn tại | 1. Gửi update | Trip: unknown | 404/Not Found phù hợp | High |
| TC-BP08-011 | BP-08 – Thực hiện chuyến | Driver chưa assigned cập nhật trip | Booking chưa assign | 1. Gửi ARRIVING | Trip T001 | Từ chối | High |
| TC-BP08-012 | BP-08 – Thực hiện chuyến | Cập nhật trạng thái nhiều lần (retry) | Trip IN_PROGRESS | 1. Gửi cùng status nhiều lần | IN_PROGRESS | Xử lý idempotent; không tạo bản ghi trùng | Medium |
| TC-BP08-013 | BP-08 – Thực hiện chuyến | Cập nhật vị trí khi đang trip | Trip active | 1. Gửi GPS | Lat/Lng hợp lệ | Vị trí được ghi nhận | Medium |
| TC-BP08-014 | BP-08 – Thực hiện chuyến | Vị trí không hợp lệ | Trip active | 1. Gửi GPS sai | Lat: abc; Lng: xyz | Validation error | High |
| TC-BP08-015 | BP-08 – Thực hiện chuyến | Mất GPS | Trip active | 1. Gửi request không có GPS | Location unavailable | Xử lý theo policy; không làm crash trip | Medium |
| TC-BP08-016 | BP-08 – Thực hiện chuyến | Mất kết nối khi cập nhật trạng thái | Trip active | 1. Gửi request nhưng network fail | Valid status | Client có thể retry; server không tạo trạng thái sai | Medium |
| TC-BP08-017 | BP-08 – Thực hiện chuyến | Hai update trạng thái đồng thời | Trip active | 1. Gửi 2 trạng thái đồng thời | ARRIVED/IN_PROGRESS | State cuối nhất quán theo rule | Medium |
| TC-BP08-018 | BP-08 – Thực hiện chuyến | Hoàn thành trip và ghi nhận thời điểm | Trip IN_PROGRESS | 1. COMPLETED 2. Kiểm tra dữ liệu | Trip T001 | Lưu trạng thái và timestamp | Medium |
| TC-BP08-019 | BP-08 – Thực hiện chuyến | Thông báo customer khi trip hoàn thành | Trip completed | 1. COMPLETED 2. Kiểm tra notification | T001 | Customer nhận thông báo | Medium |
| TC-BP08-020 | BP-08 – Thực hiện chuyến | Lỗi notification khi hoàn thành | Notification service lỗi | 1. COMPLETED | T001 | Trip vẫn COMPLETED | High |

## BP-09 – Theo dõi chuyến

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP09-001 | BP-09 – Theo dõi chuyến | Customer xem trạng thái booking | Booking active | 1. Mở booking | B001 | Hiển thị trạng thái hiện tại | Medium |
| TC-BP09-002 | BP-09 – Theo dõi chuyến | Customer xem driver được phân công | Booking assigned | 1. Mở booking | B001 | Hiển thị driver được phân công | Medium |
| TC-BP09-003 | BP-09 – Theo dõi chuyến | Customer theo dõi ARRIVING | Trip ARRIVING | 1. Refresh tracking | T001 | Hiển thị ARRIVING | Medium |
| TC-BP09-004 | BP-09 – Theo dõi chuyến | Customer theo dõi ARRIVED | Trip ARRIVED | 1. Refresh tracking | T001 | Hiển thị ARRIVED | Medium |
| TC-BP09-005 | BP-09 – Theo dõi chuyến | Customer theo dõi IN_PROGRESS | Trip IN_PROGRESS | 1. Refresh tracking | T001 | Hiển thị IN_PROGRESS | Medium |
| TC-BP09-006 | BP-09 – Theo dõi chuyến | Customer theo dõi COMPLETED | Trip completed | 1. Mở trip | T001 | Hiển thị COMPLETED | High |
| TC-BP09-007 | BP-09 – Theo dõi chuyến | Customer xem booking của người khác | Đã login user01 | 1. Gọi booking user02 | B002 | Từ chối truy cập | Medium |
| TC-BP09-008 | BP-09 – Theo dõi chuyến | Customer chưa login xem tracking | Không có token | 1. Gọi tracking API | B001 | API yêu cầu authentication | High |
| TC-BP09-009 | BP-09 – Theo dõi chuyến | Token hết hạn | Expired token | 1. Gọi tracking | B001 | Yêu cầu login lại | High |
| TC-BP09-010 | BP-09 – Theo dõi chuyến | Booking không tồn tại | ID unknown | 1. Gọi tracking | B999 | Not Found | High |
| TC-BP09-011 | BP-09 – Theo dõi chuyến | Driver chưa assign | Booking searching | 1. Xem tracking | B001 | Hiển thị đang tìm driver; chưa có driver | High |
| TC-BP09-012 | BP-09 – Theo dõi chuyến | Driver mới được assign | Booking assigned | 1. Refresh tracking | B001 | Thông tin driver được cập nhật | Medium |
| TC-BP09-013 | BP-09 – Theo dõi chuyến | Trạng thái cập nhật theo thời gian | Trip đang thay đổi | 1. Gọi tracking nhiều lần | T001 | Trả trạng thái mới nhất | Medium |
| TC-BP09-014 | BP-09 – Theo dõi chuyến | Vị trí driver hợp lệ | Trip active | 1. Mở tracking | GPS valid | Hiển thị vị trí theo dữ liệu hệ thống | Medium |
| TC-BP09-015 | BP-09 – Theo dõi chuyến | Vị trí driver unavailable | GPS unavailable | 1. Mở tracking | GPS unavailable | Thông báo vị trí không khả dụng | Medium |
| TC-BP09-016 | BP-09 – Theo dõi chuyến | Tracking không hiển thị dữ liệu nhạy cảm | Trip active | 1. Kiểm tra response | T001 | Chỉ hiển thị dữ liệu cần thiết | Medium |
| TC-BP09-017 | BP-09 – Theo dõi chuyến | Nhiều customer tracking đồng thời | Nhiều request | 1. Mở tracking đồng thời | T001 | Hệ thống trả dữ liệu ổn định | Medium |
| TC-BP09-018 | BP-09 – Theo dõi chuyến | Tracking sau khi trip completed | Trip completed | 1. Mở tracking | T001 | Hiển thị trạng thái cuối | Medium |
| TC-BP09-019 | BP-09 – Theo dõi chuyến | Thông báo driver nhận chuyến | Driver ACCEPT | 1. Kiểm tra customer | B001 | Customer được cập nhật | Medium |
| TC-BP09-020 | BP-09 – Theo dõi chuyến | Lỗi service tracking | Tracking service lỗi | 1. Gọi API | B001 | Thông báo lỗi phù hợp; không làm mất trip | High |

## BP-10 – Lưu lịch sử chuyến

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP10-001 | BP-10 – Lưu lịch sử chuyến | Trip completed được lưu lịch sử | Trip COMPLETED | 1. Hoàn thành trip 2. Mở history | T001 | Trip xuất hiện trong lịch sử | Medium |
| TC-BP10-002 | BP-10 – Lưu lịch sử chuyến | Trip chưa completed không nằm lịch sử hoàn thành | Trip IN_PROGRESS | 1. Mở history | T002 | Không hiển thị trong completed history | High |
| TC-BP10-003 | BP-10 – Lưu lịch sử chuyến | Customer xem lịch sử của mình | Đã login | 1. Mở history | user01 | Chỉ hiển thị chuyến của user01 | Medium |
| TC-BP10-004 | BP-10 – Lưu lịch sử chuyến | Customer xem lịch sử người khác | Đã login user01 | 1. Gọi history user02 | user02 | Từ chối truy cập | Medium |
| TC-BP10-005 | BP-10 – Lưu lịch sử chuyến | Không có lịch sử | Customer chưa có completed trip | 1. Mở history | user03 | Hiển thị danh sách rỗng phù hợp | Medium |
| TC-BP10-006 | BP-10 – Lưu lịch sử chuyến | Nhiều trip completed | Có nhiều trip | 1. Mở history | T001,T002,T003 | Hiển thị đầy đủ theo rule | Medium |
| TC-BP10-007 | BP-10 – Lưu lịch sử chuyến | Lịch sử chứa đúng thông tin trip | Trip completed | 1. Mở history 2. Kiểm tra detail | T001 | Thông tin khớp trip gốc | Medium |
| TC-BP10-008 | BP-10 – Lưu lịch sử chuyến | Lịch sử giữ đúng driver | Trip completed | 1. Kiểm tra history | T001/D01 | Driver đúng | Medium |
| TC-BP10-009 | BP-10 – Lưu lịch sử chuyến | Lịch sử giữ đúng điểm đón | Trip completed | 1. Kiểm tra history | A→B | Pickup đúng | Medium |
| TC-BP10-010 | BP-10 – Lưu lịch sử chuyến | Lịch sử giữ đúng điểm đến | Trip completed | 1. Kiểm tra history | A→B | Destination đúng | Medium |
| TC-BP10-011 | BP-10 – Lưu lịch sử chuyến | Lịch sử giữ timestamp | Trip completed | 1. Kiểm tra thời gian | T001 | Thời gian hoàn thành được lưu | Medium |
| TC-BP10-012 | BP-10 – Lưu lịch sử chuyến | Trip complete nhưng lỗi lưu history | History service/DB lỗi | 1. Complete trip | T001 | Hệ thống xử lý lỗi và không mất trạng thái trip; retry theo policy | Medium |
| TC-BP10-013 | BP-10 – Lưu lịch sử chuyến | Gọi history khi chưa login | Không có token | 1. GET history | Authorization: absent | API từ chối | High |
| TC-BP10-014 | BP-10 – Lưu lịch sử chuyến | Token history hết hạn | Expired token | 1. GET history | Expired token | Yêu cầu authentication | High |
| TC-BP10-015 | BP-10 – Lưu lịch sử chuyến | Pagination lịch sử | Có nhiều records và API hỗ trợ pagination | 1. Gọi page 1/page 2 | page=1,size=10 | Trả đúng phân trang | Medium |
| TC-BP10-016 | BP-10 – Lưu lịch sử chuyến | Sắp xếp lịch sử | Có nhiều trip | 1. Mở history | T001,T002 | Thứ tự theo rule được áp dụng (mới nhất trước) | Medium |
| TC-BP10-017 | BP-10 – Lưu lịch sử chuyến | History không chứa password | Có completed trip | 1. Kiểm tra response | History response | Không chứa password | Medium |
| TC-BP10-018 | BP-10 – Lưu lịch sử chuyến | History không sửa được trip gốc | Customer chỉ xem history | 1. Thử thay đổi record | T001 | Không cho chỉnh sửa nếu không có quyền | Medium |
| TC-BP10-019 | BP-10 – Lưu lịch sử chuyến | Trip hoàn thành một lần chỉ tạo một history record | Trip T001 | 1. Gửi complete/retry | T001 | Không tạo bản ghi lịch sử trùng | Medium |
| TC-BP10-020 | BP-10 – Lưu lịch sử chuyến | History phản ánh dữ liệu sau completion | Trip vừa completed | 1. Complete 2. Get history | T001 | History cập nhật đúng trip vừa hoàn thành | Medium |

## BP-11 – Vận hành & Phân quyền (Operator – Admin) *(mới)*

*Đóng khoảng trống BRL-14, BRL-16, NFR-10 (audit) trong README đã hiệu đính. Không test báo cáo doanh thu (BO-12) vì đây là tính năng ngoài MVP.*

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP11-001 | BP-11 – Vận hành & Phân quyền | Operator đăng nhập hợp lệ | Tài khoản Operator Active | 1. Login | operator01 / Password@123 | Đăng nhập thành công; token gắn role OPERATOR | Medium |
| TC-BP11-002 | BP-11 – Vận hành & Phân quyền | Admin đăng nhập hợp lệ | Tài khoản Admin Active | 1. Login | admin01 / Password@123 | Đăng nhập thành công; token gắn role ADMIN | Medium |
| TC-BP11-003 | BP-11 – Vận hành & Phân quyền | Operator tạo tài khoản tài xế | Operator đã login | 1. Nhập thông tin tài xế 2. Tạo | Tài xế hợp lệ | Tài khoản tài xế được tạo, trạng thái ACTIVE | High |
| TC-BP11-004 | BP-11 – Vận hành & Phân quyền | Operator tạo tài xế thiếu thông tin bắt buộc | Operator đã login | 1. Bỏ trống trường bắt buộc 2. Tạo | Phone: empty | Validation error; không tạo tài khoản | Medium |
| TC-BP11-005 | BP-11 – Vận hành & Phân quyền | Operator thêm phương tiện cho tài xế | Tài xế đã tồn tại | 1. Nhập biển số, loại xe 2. Lưu | Plate: 51A-11111 | Phương tiện được gắn đúng tài xế | Medium |
| TC-BP11-006 | BP-11 – Vận hành & Phân quyền | Operator xem danh sách khách hàng | Operator đã login | 1. Mở danh sách khách hàng | — | Hiển thị danh sách, không lộ password | Medium |
| TC-BP11-007 | BP-11 – Vận hành & Phân quyền | Operator xem danh sách tài xế và trạng thái sẵn sàng | Operator đã login | 1. Mở danh sách tài xế | — | Hiển thị đúng availability từng tài xế | Medium |
| TC-BP11-008 | BP-11 – Vận hành & Phân quyền | Operator xem danh sách chuyến đang diễn ra | Có chuyến ASSIGNED/IN_PROGRESS | 1. Lọc theo trạng thái | status=IN_PROGRESS | Chỉ trả đúng các chuyến ở trạng thái lọc | Medium |
| TC-BP11-009 | BP-11 – Vận hành & Phân quyền | Operator hỗ trợ hủy một chuyến bị lỗi | Chuyến đang SEARCHING/ASSIGNED | 1. Chọn chuyến 2. Hủy | Trip T001 | Chuyến chuyển CANCELLED; tài xế (nếu có) được giải phóng | High |
| TC-BP11-010 | BP-11 – Vận hành & Phân quyền | **Operator cố khóa tài khoản khách hàng → bị từ chối** | Operator đã login (không phải Admin) | 1. Gửi yêu cầu khóa tài khoản | Customer C01 | 403 Forbidden; tài khoản KHÔNG bị khóa (BRL-16) | High |
| TC-BP11-011 | BP-11 – Vận hành & Phân quyền | **Operator cố khóa tài khoản tài xế → bị từ chối** | Operator đã login | 1. Gửi yêu cầu khóa tài khoản | Driver D01 | 403 Forbidden; tài khoản KHÔNG bị khóa (BRL-16) | High |
| TC-BP11-012 | BP-11 – Vận hành & Phân quyền | Admin khóa tài khoản khách hàng vi phạm | Admin đã login | 1. Khóa tài khoản | Customer C01 | Tài khoản chuyển LOCKED; khách hàng không đăng nhập được | High |
| TC-BP11-013 | BP-11 – Vận hành & Phân quyền | Admin mở khóa tài khoản | Tài khoản đang LOCKED | 1. Mở khóa | Customer C01 | Tài khoản chuyển ACTIVE; đăng nhập lại được | Medium |
| TC-BP11-014 | BP-11 – Vận hành & Phân quyền | Admin khóa tài khoản tài xế đang BUSY | Tài xế đang phục vụ chuyến | 1. Khóa tài khoản | Driver D01 (BUSY) | Tài khoản bị khóa; chuyến đang chạy không bị hủy đột ngột (xử lý theo rule) | High |
| TC-BP11-015 | BP-11 – Vận hành & Phân quyền | Customer/Driver không truy cập được API vận hành | Customer/Driver đã login | 1. Gọi API danh sách khách hàng/tài xế | Token customer hoặc driver | 403 Forbidden | High |
| TC-BP11-016 | BP-11 – Vận hành & Phân quyền | Truy cập API vận hành khi chưa đăng nhập | Không có token | 1. Gọi API operator | Authorization: absent | 401 Unauthorized | High |
| TC-BP11-017 | BP-11 – Vận hành & Phân quyền | Token Operator hết hạn | Expired token | 1. Gọi API operator | Expired token | Yêu cầu đăng nhập lại | Medium |
| TC-BP11-018 | BP-11 – Vận hành & Phân quyền | Đăng nhập/đăng nhập thất bại được ghi audit log | Có audit log | 1. Login thành công 2. Login sai | user01 | Cả hai lượt đều có bản ghi log (LOGIN_SUCCESS/LOGIN_FAILED) | High |
| TC-BP11-019 | BP-11 – Vận hành & Phân quyền | Thao tác khóa/mở khóa tài khoản được ghi audit log | Admin thực hiện khóa tài khoản | 1. Khóa tài khoản 2. Kiểm tra log | Customer C01 | Log ghi rõ actor = Admin, hành động, thời gian (BRL-15) | High |
| TC-BP11-020 | BP-11 – Vận hành & Phân quyền | Audit log không hiển thị cho Operator | Operator đã login | 1. Gọi API xem audit log | Token operator | 403 Forbidden (chỉ Admin xem được) | Medium |

## BP-12 – Hủy chuyến (Cancel Trip) *(mới)*

*Đóng khoảng trống về luồng hủy chuyến (BR-Q07/Q08) — chỉ kiểm thử cơ chế hủy; chính sách phí hủy vẫn là câu hỏi mở (BR-Q08), không test ở đây.*

| Test Case ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP12-001 | BP-12 – Hủy chuyến | Khách hàng hủy khi đang SEARCHING | Trip SEARCHING | 1. Mở chuyến 2. Hủy | Trip T001 | Trip chuyển CANCELLED | Medium |
| TC-BP12-002 | BP-12 – Hủy chuyến | Khách hàng hủy khi đã ASSIGNED | Trip ASSIGNED | 1. Hủy | Trip T001 | Trip chuyển CANCELLED; tài xế được giải phóng về AVAILABLE | High |
| TC-BP12-003 | BP-12 – Hủy chuyến | Khách hàng hủy khi ARRIVING | Trip ARRIVING | 1. Hủy | Trip T001 | Trip chuyển CANCELLED | Medium |
| TC-BP12-004 | BP-12 – Hủy chuyến | Khách hàng hủy khi ARRIVED | Trip ARRIVED | 1. Hủy | Trip T001 | Trip chuyển CANCELLED | Medium |
| TC-BP12-005 | BP-12 – Hủy chuyến | Khách hàng không hủy được khi IN_PROGRESS | Trip IN_PROGRESS | 1. Thử hủy | Trip T001 | Từ chối; trip giữ nguyên IN_PROGRESS | High |
| TC-BP12-006 | BP-12 – Hủy chuyến | Khách hàng không hủy được chuyến đã COMPLETED | Trip COMPLETED | 1. Thử hủy | Trip T001 | Từ chối | Medium |
| TC-BP12-007 | BP-12 – Hủy chuyến | Khách hàng không hủy được chuyến đã CANCELLED | Trip CANCELLED | 1. Thử hủy lại | Trip T001 | Từ chối; không đổi trạng thái | Medium |
| TC-BP12-008 | BP-12 – Hủy chuyến | Khách hàng không hủy được chuyến của người khác | Trip thuộc customer02 | 1. Customer01 gửi hủy | Trip T002 | 403 Forbidden | High |
| TC-BP12-009 | BP-12 – Hủy chuyến | Tài xế không tự hủy chuyến của khách | Trip ASSIGNED | 1. Driver gửi hủy | Trip T001 | 403 Forbidden (driver dùng REJECT/không nhận, không dùng cancel) | Medium |
| TC-BP12-010 | BP-12 – Hủy chuyến | Hủy chuyến khi chưa đăng nhập | Không có token | 1. Gửi hủy | Authorization: absent | 401 Unauthorized | High |
| TC-BP12-011 | BP-12 – Hủy chuyến | Hủy chuyến không tồn tại | Trip ID unknown | 1. Gửi hủy | Trip: unknown | 404 Not Found | High |
| TC-BP12-012 | BP-12 – Hủy chuyến | Hủy chuyến giải phóng tài xế khỏi lời mời đang chờ | Trip SEARCHING, đang chờ driver phản hồi | 1. Khách hủy trước khi driver phản hồi | Trip T001 | Lời mời đang chờ (PENDING) bị hủy; driver không còn nhận được yêu cầu này | High |
| TC-BP12-013 | BP-12 – Hủy chuyến | Tài xế nhận được thông báo khi khách hủy chuyến đã ASSIGNED | Trip ASSIGNED | 1. Khách hủy 2. Kiểm tra notification tài xế | Trip T001 | Tài xế nhận thông báo hủy | Medium |
| TC-BP12-014 | BP-12 – Hủy chuyến | Sau khi hủy, khách hàng đặt lại chuyến mới | Trip vừa CANCELLED | 1. Tạo booking mới | A→B; Sedan | Tạo booking mới thành công (không còn bị chặn bởi "1 chuyến mở") | Medium |
| TC-BP12-015 | BP-12 – Hủy chuyến | Operator hủy chuyến hộ khách khi có sự cố | Trip ASSIGNED, khách báo lỗi qua tổng đài | 1. Operator mở chuyến 2. Hủy | Trip T001 | Trip chuyển CANCELLED; ghi nhận actor = Operator | High |
| TC-BP12-016 | BP-12 – Hủy chuyến | Hai yêu cầu hủy gửi đồng thời | Trip ASSIGNED | 1. Gửi 2 request hủy cùng lúc | Trip T001 | Trip chỉ chuyển CANCELLED một lần; không lỗi trạng thái | Medium |
| TC-BP12-017 | BP-12 – Hủy chuyến | Hủy chuyến được ghi vào lịch sử trạng thái | Trip đã hủy | 1. Kiểm tra status history | Trip T001 | Có bản ghi CANCELLED kèm thời gian và actor | Medium |
| TC-BP12-018 | BP-12 – Hủy chuyến | Chuyến đã hủy không xuất hiện trong lịch sử "đã hoàn thành" | Trip CANCELLED | 1. Mở history (status=COMPLETED) | Trip T001 | Không hiển thị trong danh sách chuyến hoàn thành | Medium |
| TC-BP12-019 | BP-12 – Hủy chuyến | Lỗi hệ thống khi hủy | DB/service lỗi | 1. Gửi hủy | Trip T001 | Thông báo lỗi; trạng thái trip không bị đổi nửa chừng | High |
| TC-BP12-020 | BP-12 – Hủy chuyến | Response hủy không chứa dữ liệu nhạy cảm | Hủy thành công | 1. Kiểm tra response | Trip T001 | Không chứa password/thông tin thanh toán | Medium |
