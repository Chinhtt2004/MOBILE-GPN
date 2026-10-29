# Hiện trạng trên hệ thống

**Trạng thái:** Draft – gửi PM review\n**Người thực hiện:** TTS BA Tướng Thị Chình\n**Ngày cập nhật:** 21/10/2026\n**Người review:** PM\n**Deadline và link docs.gopany.tech:** Chờ xác nhận

## 1. Business Context & Objectives

### 1.1. Bối cảnh theo đầu việc PM

* iOS đang ẩn chức năng tạo workspace do từng bị Apple reject theo mục 3.1.1.
* Người dùng chưa có workspace bị kẹt ở màn "Bạn chưa có Workspace nào".
* Android đã có luồng tạo nhưng sử dụng design cũ.
* Design cũ có bước Cá nhân/Đội nhóm/Doanh nghiệp nhìn giống chọn gói; có nhắc lời mời nhưng thiếu điểm truy cập rõ ràng trong luồng PM phản ánh.
* Màn danh sách thiếu nút tạo mới; thiếu loading/lỗi.

### 1.2. Mục tiêu

* Người dùng đủ điều kiện có thể tạo workspace trên iOS.
* Đồng bộ luồng tạo theo design mới trên iOS và Android.
* Làm rõ đường đi cho người chưa có workspace và người được mời/thêm vào workspace.
* Bổ sung trạng thái loading, lỗi, rỗng và thao tác thử lại.

### 1.3. Quy ước và nguồn

* **FACT – anh Chiến:** thông tin được Chình chuyển lại từ anh Chiến.
* **Theo tài liệu:** logic trong Workspace ver 2.1.xlsx bản web;
* **Đề xuất:** nội dung draft để PM review, chưa là quyết định đã chốt.
* **QUESTION:** nội dung cần làm rõ, tập trung tại mục 10.

Nguồn: đầu việc PM, phản hồi anh Chiến do Chình cung cấp, hai sheet UserStory(US)_Workspace ver 2.1 và MTDL.Workspace ver 2.1.

## 2. Kết quả làm rõ mô hình workspace

### 2.1. Mô hình và ảnh hưởng

| Nội dung | Kết quả | Nguồn |
|----------|---------|-------|
| Cá nhân/Đội nhóm/Doanh nghiệp | Là các option lựa chọn; mục đích phân loại chưa được giải thích rõ. Không ghi nhận khác biệt chức năng theo lựa chọn này. | Anh Chiến |
| Dữ liệu mẫu | Hiện không có dữ liệu mẫu theo mô hình. | Anh Chiến |
| Tính năng, quyền, số thành viên, dung lượng | Không phụ thuộc lựa chọn mô hình; các giới hạn/quyền lợi này theo gói dịch vụ. | Anh Chiến |
| Bỏ bước chọn mô hình | Không ảnh hưởng; không cần thay đổi xử lý phía hệ thống. | Anh Chiến |
| Workspace hiện có | Không bị ảnh hưởng khi bỏ bước chọn. | Anh Chiến |
| Quyền người tạo | "Admin hệ thống"; cần làm rõ tên và phạm vi quyền chính xác. | Anh Chiến |
| Quyền ở nhiều workspace | Độc lập theo từng workspace. | Anh Chiến |
| Information | Mỗi workspace có hồ sơ riêng của tài khoản. | Anh Chiến |

**Nhận định BA:** Có cơ sở đề xuất bỏ bước chọn mô hình trong luồng tạo. Điều này không thay đổi gói dịch vụ theo thông tin hiện có.

### 2.2. Nguyên tắc tạo và tham gia

| Nội dung | Kết quả |
|----------|---------|
| Người được tạo | Mọi tài khoản đều có thể tạo workspace riêng. |
| Giới hạn tạo | Một tài khoản được tạo một workspace của riêng mình và làm admin. |
| Tham gia workspace khác | Có thể là thành viên nhiều workspace khác. |
| Đã tham gia nhưng chưa tạo workspace riêng | Vẫn được tạo workspace riêng. |
| Xoá workspace | Hiện chưa có chức năng xoá workspace. Không đặt quy tắc "lượt tạo lại" khi chưa có nghiệp vụ này. |
| Chống gửi tạo lặp | Nút tạo được disable trong khi tạo; nếu tiếp tục gọi API thì các lần sau báo lỗi. |

### 2.3. Tên workspace

| Nội dung | Quy định đã có |
|----------|----------------|
| Độ dài tối đa | 100 ký tự; đối chiếu câu trả lời "100" với giới hạn tối đa trong file. |
| Ký tự    | Cho phép tiếng Việt có/không dấu, hoa/thường, số, khoảng trắng, ký tự đặc biệt và emoji. |
| Trùng tên | Cho phép.      |
| Thông báo vượt giới hạn theo file | "Tên workspace không được vượt quá 100 ký tự". |

Bắt buộc nhập, độ dài tối thiểu, cách xử lý khoảng trắng và cách đếm emoji còn cần xác nhận.

### 2.4. Thêm thành viên và lời mời

| Nội dung | Kết quả đã xác nhận |
|----------|---------------------|
| Nơi thêm/mời | Màn Nhân sự và Sơ đồ tổ chức. |
| Mời từ Sơ đồ tổ chức | Phải chấp nhận thì mới tạo nhân sự mới. |
| Kênh mời | Email; có link để chấp nhận. |
| Thao tác qua link | Có thể chấp nhận; không từ chối được qua link theo anh Chiến. |
| Thao tác tại màn chọn workspace | Có thể chấp nhận/từ chối. |
| Quyền thực hiện | Tạo nhân sự.        |
| Danh sách lời mời đã đề cập | Dành cho người nhận; đã có dữ liệu. |
| Người chưa có workspace | Xem/chấp nhận qua link hoặc màn chọn workspace. |
| Trạng thái | Có từ chối, hết hạn, thu hồi. |
| Quyền người tham gia | Theo quyền chức vụ được gán. |
| Thời hạn theo file | 24 giờ; chờ đối chiếu thực tế. |

## 3. Nhóm người dùng và tình huống

Phân nhóm theo trạng thái tài khoản, workspace và lời mời để xác định điều hướng. Một người dùng có thể thuộc nhiều nhóm. Phần này tổng hợp từ hai sheet; thông tin anh Chiến và Chình bổ sung được ghi rõ nguồn. Không phân tích chi tiết nghiệp vụ khoá tài khoản/nghỉ việc trong scope này.

### 3.1. Đăng nhập và tạo workspace

| STT | Nhóm người dùng | Tình huống | Cách xử lý và nguồn |
|-----|-----------------|------------|---------------------|
| 1   | Người chưa có workspace | Đăng nhập thành công, chưa có workspace và không có lời mời | Theo file: hiển thị màn khởi tạo để tạo workspace. |
| 2   | Người có một workspace | Có một workspace, không có lời mời mới | Theo file và anh Chiến: vào thẳng workspace. |
| 3   | Người có nhiều workspace | Có từ hai workspace trở lên | Theo file và anh Chiến: hiển thị danh sách chọn workspace. |
| 4   | Người đang sử dụng muốn tạo workspace riêng | Đã là thành viên workspace khác nhưng chưa tạo workspace riêng | File: thực hiện qua workspace switcher, không ở login flow. Anh Chiến: vẫn được tạo workspace riêng. |

### 3.2. Được thêm hoặc mời tham gia workspace

| STT | Nhóm người dùng | Tình huống | Cách xử lý và nguồn |
|-----|-----------------|------------|---------------------|
| 5   | Người được mời, đã có tài khoản | Mở link mời hợp lệ bằng đúng tài khoản nhận | File: xác nhận tham gia, bổ sung workspace vào tài khoản hiện có; không gửi mật khẩu mới. Điều hướng sau tham gia cần thống nhất giữa các nhánh. |
| 6   | Người được mời, chưa có tài khoản | Mở link mời tiêu chuẩn hợp lệ | File: tạo mật khẩu/tài khoản → đăng nhập → vào thẳng workspace được mời lần đầu. Cần đối chiếu hành vi thực tế. |
| 7   | Người được kích hoạt nhanh | Chưa có tài khoản, được HCNS kích hoạt nhanh | File: nhận email chứa thông tin đăng nhập và chức vụ → đăng nhập → vào workspace được mời. |
| 8   | Người được mời từ Sơ đồ tổ chức | Có lời mời tham gia workspace | Anh Chiến: phải chấp nhận thì mới tạo nhân sự mới; quyền theo chức vụ được gán. |
| 9   | Người được mời từ màn Nhân sự | Nhân sự được tạo rồi gửi lời mời | Cần xác nhận: có bắt buộc chấp nhận không, thời điểm cấp quyền truy cập và điều hướng. |

### 3.3. Xử lý lời mời khi đang sử dụng

| STT | Nhóm người dùng | Tình huống | Cách xử lý và nguồn |
|-----|-----------------|------------|---------------------|
| 10  | Người chưa có workspace nhưng có lời mời | Đăng nhập và có lời mời đang chờ | Anh Chiến: xem/chấp nhận qua link hoặc màn chọn workspace; đăng nhập có danh sách lời mời. Cần xác minh từng nền tảng. |
| 11  | Người đã có workspace và có lời mời mới | Đăng nhập với workspace hiện có và lời mời chưa xử lý | Anh Chiến: hiển thị màn chọn workspace. File có mô tả popup trong workspace hiện tại; cần làm rõ thời điểm áp dụng. |
| 12  | Người đang ở workspace khác | Đang ở A, mở lời mời B | File: popup xác nhận; đồng ý thì tham gia/chuyển sang B. Cách từ chối cần đối chiếu xác nhận mới. |
| 13  | Người có nhiều lời mời | Có nhiều lời mời hợp lệ | File: xử lý lần lượt từ mới đến cũ, bỏ qua lời mời không còn hiệu lực. |
| 14  | Người chưa xử lý lời mời | Tải lại trang hoặc đóng ứng dụng khi chưa chọn hành động | File: hiển thị lại xác nhận nếu lời mời còn hiệu lực; không tự động tham gia. |
| 15  | Người đăng nhập sai tài khoản nhận lời mời | Đang dùng email A nhưng lời mời gửi email B | File: thông báo rõ hai email/người mời; cho đăng nhập email B hoặc ở lại. |
| 16  | Người mở lời mời không còn hiệu lực | Hết hạn, thu hồi, workspace không tồn tại hoặc lời mời đã xử lý | File: không cho tham gia, không tạo workspace; thông báo không khả dụng. Thời hạn được ghi là 24 giờ, chờ đối chiếu thực tế. |

Theo anh Chiến: link chỉ hỗ trợ chấp nhận; tại màn chọn workspace có chấp nhận/từ chối. Không mặc định áp dụng rule trong file rằng từ chối popup làm link mất hiệu lực cho mọi giao diện khi chưa xác nhận.

### 3.4. Chuyển hoặc mất quyền truy cập workspace

| STT | Nhóm người dùng | Tình huống | Cách xử lý và nguồn |
|-----|-----------------|------------|---------------------|
| 17  | Người có nhiều workspace | Chuyển workspace khi đang làm việc | File: mở danh sách, chọn workspace khác, cảnh báo dữ liệu chưa lưu; không cần đăng xuất. |
| 18  | Người chọn workspace không còn truy cập được | Workspace không hợp lệ/quyền truy cập bị thu hồi | File: tại màn chọn báo lỗi và cho chọn lại; khi đang chuyển thì báo lỗi và giữ workspace hiện tại nếu vẫn có quyền. Trường hợp workspace hiện tại cũng mất quyền cần làm rõ. |
| 19  | Người bị xoá khỏi workspace, còn một workspace | Còn một workspace có thể truy cập | Anh Chiến: vào workspace còn lại. Thời điểm áp dụng khi đang sử dụng cần xác nhận. |
| 20  | Người bị xoá khỏi workspace, còn nhiều workspace | Còn từ hai workspace có thể truy cập | Anh Chiến: hiển thị danh sách, không có workspace đã bị xoá khỏi. |
| 21  | Người không còn workspace | Bị xoá khỏi workspace cuối cùng | Anh Chiến: hiện nút tạo workspace. Cần xác nhận trường hợp không đủ điều kiện tạo. |
| 22  | Người bị chặn quyền truy cập | Người có quyền khoá tài khoản hoặc chuyển nhân sự sang Nghỉ việc | Chình bổ sung: không được truy cập workspace tương ứng. Chỉ ghi nhận điều kiện truy cập, không mở rộng chức năng khoá/nghỉ việc. |
| 23  | Người đã tạo workspace riêng nhưng không còn workspace truy cập được | Không còn điểm vào sử dụng | Chưa có kết luận; hiện chưa có chức năng xoá workspace. Không tự quy định lượt tạo lại. |

workspace hiện tại nếu đã đầy vẫn có thể mời được ở hồ sơ nhân sự nếu người được mời sẽ hiển thị lời mời lúc chấp nhận sẽ hiển thị thông báo