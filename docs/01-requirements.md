# Tài liệu Yêu cầu Hệ thống (Requirements Specification)
## Dự án: Quản lý Câu lạc bộ (là Nhiệm vụ 1)

---

## 1. Danh sách Actor (Danh sách tác nhân)

* **Admin (Quản trị viên hệ thống):**
  Quản trị toàn bộ hệ thống, quản lý tài khoản người dùng, phân quyền và giám sát hoạt động của tất cả các câu lạc bộ. Ranh giới quyền hạn bao phủ toàn bộ dữ liệu hệ thống nhưng không trực tiếp can thiệp vào các hoạt động nghiệp vụ nội bộ của từng CLB ngoại trừ khi xử lý vi phạm hoặc cấu hình chung.

* **Chủ nhiệm CLB:**
  Quản lý toàn bộ thông tin, thành viên, sự kiện và tài chính trong phạm vi câu lạc bộ mà mình phụ trách. Ranh giới quyền hạn tuyệt đối không được truy cập hay can thiệp vào dữ liệu hoặc hoạt động của các CLB khác trên hệ thống.

* **Thành viên:**
  Người tham gia vào các hoạt động của CLB, có quyền gửi đơn gia nhập, đăng ký tham gia sự kiện, theo dõi điểm danh và xem các thông báo/báo cáo công khai. Ranh giới quyền hạn chỉ dừng lại ở các thao tác cá nhân và xem thông tin được cho phép, không có quyền quản lý hay chỉnh sửa dữ liệu chung.

---

## 2. Phân loại phạm vi (Scope Classification)

| Nghiệp vụ | Mức | Lý do |
| :--- | :--- | :--- |
| **Quản lý CLB** | Bắt buộc | Là dữ liệu gốc, các chức năng khác phụ thuộc vào. |
| **Quản lý thành viên** | Bắt buộc | Cần thiết để xác định danh tính và vai trò người dùng trong từng CLB, thiếu nó hệ thống không thể hoạt động. |
| **Đơn gia nhập** | Bắt buộc | Là quy trình đầu vào để tiếp nhận thành viên mới, thiếu nó hệ thống không thể phát triển số lượng người dùng. |
| **Quản lý sự kiện** | Bắt buộc | Hoạt động cốt lõi của CLB; thiếu nó hệ thống mất đi mục tiêu kết nối và tổ chức hoạt động. |
| **Đăng ký sự kiện** | Bắt buộc | Dùng để ghi nhận nhu cầu tham gia của thành viên, là cơ sở để ban tổ chức chuẩn bị và điểm danh. |
| **Điểm danh** | Bắt buộc | Xác nhận sự tham gia thực tế của thành viên tại sự kiện, quyết định tính chính xác của dữ liệu hoạt động. |
| **Thu chi** | Mở rộng | Hỗ trợ quản lý quỹ và tài chính minh bạch, tuy nhiên hệ thống vẫn có thể vận hành các hoạt động cơ bản nếu thiếu phần này. |
| **Thống kê** | Mở rộng | Phục vụ việc tổng hợp báo cáo và đánh giá hiệu quả, có thể thực hiện thủ công hoặc bổ sung nâng cấp ở giai đoạn sau. |
