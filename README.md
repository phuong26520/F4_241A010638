Lab F4 - Điều hướng đa màn hình trong Flutter - Danh bạ mini

Thông tin sinh viên: Nguyễn Hoài Phương - MSSV 241A010638 - Lớp LTTTBDD - Môn INT4211 Lập trình trên các thiết bị di động - Tuần 8. Project f4_danhba tạo bằng lệnh flutter create, ngôn ngữ Dart theo Material 3, Flutter 3.47.3.

Mô tả ngắn gọn

App Danh bạ mini gồm các màn hình điều hướng qua ngăn xếp của Navigator: màn hình Danh sách liên hệ ContactListPage, màn hình Chi tiết ContactDetailPage, màn hình Thêm hoặc Sửa liên hệ ContactEditPage, màn hình Giới thiệu AboutPage dùng named route và màn hình Tìm kiếm ContactSearchPage phục vụ bài nâng cao. Model Contact khai báo bất biến với các trường final và hàm copyWith; kết quả trả về từ Chi tiết được gói trong DetailResult cùng enum DetailAction. Màn hình Thêm/Sửa dùng PopScope với canPop và onPopInvokedWithResult để chặn thao tác Back khi còn thay đổi chưa lưu và hiển thị hộp thoại xác nhận Bỏ thay đổi?.

Cấu trúc thư mục chính

lib/main.dart chứa toàn bộ ứng dụng gồm MyApp, Contact, DetailResult, ContactListPage, ContactDetailPage, ContactEditPage, AboutPage và ContactSearchPage
test/widget_test.dart chứa widget test kiểm tra điều hướng giữa các màn hình
pubspec.yaml khai báo tên package f4_danhba và các dependency mặc định

Các chức năng đã hoàn thành theo thang điểm

Ba màn hình chính chạy đúng, điều hướng bằng Navigator.push kèm MaterialPageRoute và quay lại bằng Navigator.pop, title của MaterialApp là F4_241A010638. Truyền dữ liệu sang màn hình con bằng tham số constructor với model Contact bất biến. Nhận kết quả trả về bằng await Navigator.push có kiểu tường minh, xử lý đủ hai dòng phòng thủ kiểm tra null và mounted trước khi gọi setState và showSnackBar. PopScope chặn thoát khi cờ _daSua bật và hỏi người dùng qua AlertDialog Bỏ thay đổi?. Màn hình Giới thiệu mở bằng Navigator.pushNamed qua route /about khai báo trong MaterialApp.routes, hiển thị họ tên Nguyễn Hoài Phương và MSSV 241A010638. Hai bài nâng cao NC1 và NC2 đã làm.

Bài nâng cao đã thực hiện

NC1 - Thêm màn hình Tìm kiếm và trả về liên hệ được chọn. Tạo thêm ContactSearchPage nhận danh sách liên hệ qua constructor, có ô TextField lọc trực tiếp theo họ tên hoặc số điện thoại khi người dùng gõ. Bấm vào một dòng kết quả sẽ gọi Navigator.pop(context, contact) để trả đối tượng Contact đã chọn về màn hình trước. Trên AppBar của ContactListPage thêm nút biểu tượng kính lúp gọi hàm _timKiem, dùng final chon = await Navigator.push<Contact>(...) để chờ kết quả; sau khi kiểm tra chon != null và mounted thì tìm vị trí của liên hệ đó trong danh bạ và mở thẳng màn hình Chi tiết tương ứng.

NC2 - Dùng Hero để ảnh đại diện bay mượt từ Danh sách sang Chi tiết. Bọc CircleAvatar chữ cái đầu tên ở từng ListTile của ContactListPage trong widget Hero với tag là số điện thoại của liên hệ. Ở đầu màn hình ContactDetailPage thêm một CircleAvatar cỡ lớn hơn có radius 36 cũng bọc trong Hero với cùng tag là contact.dienThoai. Khi mở Chi tiết hoặc bấm Back quay về Danh sách, Flutter tự nhận diện hai Hero cùng tag ở hai route và diễn hoạt ảnh đại diện phóng to hoặc thu nhỏ bay mượt giữa hai màn hình.

Cách chạy và kiểm thử

Cần Flutter 3.35 trở lên. Mở thư mục project rồi chạy flutter pub get, flutter analyze và flutter run trên máy ảo Android, Windows hoặc Chrome. Kiểm thử bảy kịch bản trong hướng dẫn cùng hai chức năng nâng cao Tìm kiếm và hiệu ứng Hero.
