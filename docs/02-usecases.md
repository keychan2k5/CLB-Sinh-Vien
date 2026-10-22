# Tài liệu Use Case (Use Case Specification)

## Phần 2A: Danh sách Use Case

| Mã | Tên Use Case | Actor | Nghiệp vụ |
| :--- | :--- | :--- | :--- |
| **UC01** | Đăng ký tài khoản | Khách | Xác thực & Tài khoản |
| **UC02** | Đăng nhập hệ thống | Khách / Thành viên / Chủ nhiệm / Admin | Xác thực & Tài khoản |
| **UC03** | Tạo câu lạc bộ | Admin | Quản lý CLB |
| **UC04** | Cập nhật thông tin CLB | Chủ nhiệm CLB | Quản lý CLB |
| **UC05** | Phân quyền / Xóa thành viên | Chủ nhiệm CLB | Quản lý thành viên |
| **UC06** | Xem danh sách thành viên | Chủ nhiệm CLB / Thành viên | Quản lý thành viên |
| **UC07** | Gửi đơn gia nhập CLB | Thành viên | Đơn gia nhập |
| **UC08** | Duyệt đơn gia nhập | Chủ nhiệm CLB | Đơn gia nhập |
| **UC09** | Tạo sự kiện mới | Chủ nhiệm CLB | Quản lý sự kiện |
| **UC10** | Cập nhật / Hủy sự kiện | Chủ nhiệm CLB | Quản lý sự kiện |
| **UC11** | Xem danh sách sự kiện | Thành viên / Chủ nhiệm CLB | Quản lý sự kiện |
| **UC12** | Đăng ký sự kiện | Thành viên | Đăng ký sự kiện |
| **UC13** | Hủy đăng ký sự kiện | Thành viên | Đăng ký sự kiện |
| **UC14** | Điểm danh thành viên sự kiện | Chủ nhiệm CLB | Điểm danh |
| **UC15** | Xem lịch sử điểm danh | Thành viên / Chủ nhiệm CLB | Điểm danh |

---

## Phần 2B: Mô tả chi tiết 3 Use Case

### UC08 – Duyệt đơn gia nhập
- **Actor:** Chủ nhiệm CLB
- **Điều kiện trước:** Chủ nhiệm đã đăng nhập; có ít nhất 1 đơn gia nhập ở trạng thái "Chờ duyệt" trong CLB do mình quản lý.
- **Luồng chính:**
  1. Chủ nhiệm CLB mở trang "Quản lý đơn gia nhập".
  2. Hệ thống hiển thị danh sách đơn gia nhập đang ở trạng thái "Chờ duyệt".
  3. Chủ nhiệm chọn một đơn và bấm "Duyệt" hoặc "Từ chối".
  4. Nếu chọn "Duyệt": Hệ thống đổi trạng thái đơn thành "Đã chấp nhận" và thêm người dùng vào danh sách thành viên CLB.
  5. Nếu chọn "Từ chối": Hệ thống đổi trạng thái đơn thành "Đã từ chối".
  6. Hệ thống hiển thị thông báo kết quả thành công.
- **Luồng thay thế / lỗi:**
  - 3a. Đơn đã được xử lý bởi người khác trước đó → Hệ thống báo lỗi "Đơn gia nhập không còn tồn tại hoặc đã được xử lý".
  - 3b. Tài khoản người gửi đơn bị xóa hoặc khóa → Hệ thống báo lỗi "Tài khoản không hợp lệ" và hủy đơn.
- **Kết quả (điều kiện sau):** Trạng thái đơn được cập nhật; người dùng trở thành thành viên chính thức nếu được duyệt.

---

### UC12 – Đăng ký sự kiện
- **Actor:** Thành viên (Đã đăng nhập)
- **Điều kiện trước:** Đã đăng nhập; là thành viên chính thức của CLB tổ chức sự kiện; sự kiện đang mở đăng ký.
- **Luồng chính:**
  1. Thành viên mở trang chi tiết sự kiện.
  2. Hệ thống hiển thị thông tin sự kiện, số chỗ còn lại và nút "Đăng ký tham gia".
  3. Thành viên bấm nút "Đăng ký tham gia" và xác nhận.
  4. Hệ thống ghi nhận đăng ký thành công và giảm số chỗ còn lại của sự kiện đi 1.
  5. Hệ thống thông báo "Đăng ký tham gia sự kiện thành công".
- **Luồng thay thế / lỗi:**
  - 3a. Sự kiện đã hết chỗ → Hệ thống báo lỗi "Sự kiện đã hết số lượng đăng ký cho phép", không tạo bản ghi mới.
  - 3b. Thành viên đã đăng ký sự kiện này trước đó → Hệ thống báo lỗi "Bạn đã đăng ký sự kiện này rồi" và ẩn nút đăng ký.
- **Kết quả (điều kiện sau):** Tạo 1 bản ghi đăng ký sự kiện; số chỗ còn trống giảm đi 1.

---

### UC14 – Điểm danh thành viên sự kiện
- **Actor:** Chủ nhiệm CLB
- **Điều kiện trước:** Chủ nhiệm đã đăng nhập; sự kiện đang hoặc đã diễn ra.
- **Luồng chính:**
  1. Chủ nhiệm chọn sự kiện và vào trang "Điểm danh".
  2. Hệ thống hiển thị danh sách thành viên đã đăng ký sự kiện này.
  3. Chủ nhiệm chọn trạng thái "Có mặt" hoặc "Vắng mặt" cho từng người.
  4. Chủ nhiệm bấm nút "Lưu điểm danh".
  5. Hệ thống cập nhật trạng thái và thời gian điểm danh vào cơ sở dữ liệu.
- **Luồng thay thế / lỗi:**
  - 3a. Chưa có ai đăng ký sự kiện → Hệ thống thông báo "Chưa có thành viên đăng ký" và không cho phép điểm danh.
  - 3b. Mất kết nối mạng khi lưu → Hệ thống báo lỗi "Lưu thất bại, vui lòng kiểm tra kết nối" và giữ nguyên thông tin trên màn hình để lưu lại.
- **Kết quả (điều kiện sau):** Dữ liệu điểm danh của sự kiện được lưu thành công.


# Use Cases

## Admin
1. **Quản lý người dùng**
   - Tạo, sửa, xóa tài khoản người dùng.
   - Gán vai trò (Admin, Chủ nhiệm, Thành viên).
2. **Quản lý toàn bộ câu lạc bộ**
   - Tạo, sửa, xóa CLB bất kỳ.
   - Xem báo cáo tổng quan toàn hệ thống (thu chi, số lượng thành viên, sự kiện).
3. **Quản lý sao lưu & khôi phục dữ liệu**
   - Thực hiện backup MySQL hàng ngày.
   - Khôi phục dữ liệu khi cần.

## Chủ nhiệm CLB
1. **Quản lý CLB của mình**
   - Tạo, sửa, xóa thông tin CLB.
   - Quản lý danh sách thành viên, duyệt đơn xin gia nhập.
2. **Quản lý sự kiện**
   - Tạo, sửa, xóa sự kiện thuộc CLB.
   - Mở/đóng đăng ký, giới hạn số người tham gia.
3. **Điểm danh & thu chi**
   - Ghi nhận điểm danh cho thành viên trong sự kiện.
   - Nhập, sửa, xóa giao dịch thu/chi liên quan tới CLB.
4. **Báo cáo**
   - Xem báo cáo thống kê thành viên, sự kiện, thu chi cho CLB.

## Thành viên
1. **Đăng ký gia nhập CLB**
   - Gửi đơn xin gia nhập.
   - Xem trạng thái đơn (đang chờ, được duyệt, bị từ chối).
2. **Tham gia sự kiện**
   - Đăng ký tham gia sự kiện khi còn mở.
   - Hủy đăng ký nếu chưa đóng.
3. **Điểm danh**
   - Xem danh sách điểm danh của mình cho các sự kiện đã tham gia.
4. **Quản lý hồ sơ cá nhân**
   - Cập nhật thông tin cá nhân, đổi mật khẩu.
5. **Xem báo cáo cá nhân**
   - Xem lịch sử tham gia sự kiện và giao dịch tài chính cá nhân.
