Lab F4 - Điều hướng đa màn hình trong Flutter - Danh bạ mini

Thông tin sinh viên: Nguyễn Hoài Phương - MSSV 241A010638 - Lớp LTTTBDD - Môn INT4211.

Mô tả ngắn gọn

App Danh bạ mini có các màn hình Danh sách, Chi tiết, Thêm/Sửa và Giới thiệu. App dùng Navigator.push để mở màn hình mới, Navigator.pop để quay lại, truyền dữ liệu qua constructor và trả kết quả về màn hình trước. Màn hình Thêm/Sửa có PopScope để hỏi lại khi còn dữ liệu chưa lưu.

Cấu trúc chính

lib/main.dart: mã nguồn chính của ứng dụng.
test/widget_test.dart: kiểm tra một số thao tác điều hướng.
pubspec.yaml: thông tin project và các thư viện dùng trong bài.

Các chức năng đã làm

- Hiển thị danh sách liên hệ.
- Mở màn hình Chi tiết bằng Navigator.push.
- Sửa, xóa và thêm liên hệ.
- Trả kết quả từ màn hình con về màn hình danh sách.
- Xử lý trường hợp bấm Back không có kết quả.
- Hiển thị hộp thoại khi quay lại lúc chưa lưu.
- Màn hình Giới thiệu mở bằng named route.

Bài nâng cao đã làm

NC1 - Tìm kiếm liên hệ

Bài yêu cầu thêm một màn hình tìm kiếm và trả liên hệ được chọn về màn hình danh sách. Mình tạo ContactSearchPage, truyền danh sách liên hệ vào màn hình này bằng constructor. Trong màn hình tìm kiếm có TextField; mỗi lần nhập, onChanged cập nhật từ khóa rồi lọc danh sách theo họ tên hoặc số điện thoại. Kết quả được hiển thị bằng các ListTile.

Khi bấm một liên hệ, ContactSearchPage dùng Navigator.pop(context, contact) để trả liên hệ đã chọn về màn hình trước. Ở ContactListPage, hàm _timKiem dùng await Navigator.push<Contact>(...) để chờ kết quả. Nếu kết quả khác null và màn hình vẫn còn hoạt động, chương trình tìm vị trí liên hệ trong danh sách rồi mở màn hình Chi tiết của liên hệ đó.

NC2 - Hiệu ứng Hero cho ảnh đại diện

Bài yêu cầu tạo hiệu ứng ảnh đại diện chuyển từ màn hình Danh sách sang màn hình Chi tiết. Ở mỗi dòng trong ContactListPage, CircleAvatar được đặt bên trong Hero với tag là số điện thoại của liên hệ. Ở ContactDetailPage cũng có một CircleAvatar đặt trong Hero và dùng đúng tag đó.

Khi hai Hero ở hai màn hình có cùng tag, Flutter tự tạo hiệu ứng chuyển ảnh đại diện khi mở Chi tiết và khi bấm Back quay lại. Số điện thoại được dùng làm tag vì mỗi liên hệ có một giá trị riêng.

Cách chạy

Chạy flutter pub get, sau đó chạy flutter run. Có thể dùng flutter analyze để kiểm tra lỗi.
