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

NC1: Thêm ô tìm kiếm liên hệ theo tên hoặc số điện thoại.

NC2: Thêm hiệu ứng Hero cho ảnh đại diện khi mở màn hình Chi tiết.

Cách chạy

Chạy flutter pub get, sau đó chạy flutter run. Có thể dùng flutter analyze để kiểm tra lỗi.
