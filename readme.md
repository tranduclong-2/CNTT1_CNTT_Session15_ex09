# BÀI 9: THIẾT KẾ HỆ THỐNG LƯU TRỮ VÀ PHÂN QUYỀN CHO DỰ ÁN CAMPUSPAY
## PHẦN 1: PHÂN TÍCH BÀI TOÁN (I/O)
### 1. Xác định đầu vào và đầu ra
Đầu vào:
- 4 nhóm người dùng: Ban Kỹ thuật, Ban Thiết kế, Ban Kinh doanh và Nhà đầu tư.
- Các loại tài liệu: Code, thiết kế, kế hoạch kinh doanh, slide thuyết trình và dữ liệu bảo mật.
- Yêu cầu: Lưu trữ an toàn, phân quyền hợp lý và tránh rò rỉ dữ liệu.
Đầu ra:
- Một hệ thống thư mục Google Drive rõ ràng.
- Bảng phân quyền cho từng nhóm.
- Có thể kiểm soát người xem, người chỉnh sửa và người tải tài liệu.
### 2. Cấu trúc thư mục Google Drive
```CampusPay/
│
|_ 01_Code/
│   └── Code, API, tài liệu kỹ thuật 
│
├── 02_Design/
│   └── Hình ảnh, UI, UX
│
├── 03_Business/
│   └── Business Plan, thông tin đối tác
│
├── 04_Shared/
│   └── Slide Pitch, tài liệu chung
│
└── 05_Private/
    └── API Keys, thông tin khách hàng
```

Mỗi thư mục chứa tài liệu riêng của từng nhóm để dễ quản lý và tránh nhầm lẫn.
### 3. Các bước thiết lập
1. Tạo thư mục chính CampusPay trên Google Drive.
2. Tạo các thư mục con theo từng nhóm tài liệu.
3. Đưa tài liệu vào đúng thư mục.
4. Thêm thành viên vào thư mục tương ứng.
5. Cấp quyền Viewer hoặc Editor phù hợp.
6. Đặt chế độ Restricted cho tài liệu quan trọng.
7. Chia sẻ tài liệu cho nhà đầu tư trong 14 ngày.
8. Kiểm tra quyền truy cập và thu hồi khi có thành viên nghỉ việc.

## PHẦN 2: TRIỂN KHAI VÀ CHỐNG LỖI
### 4. Bảng phân quyền
Loại tài liệu	Ban KT	Ban TK	Ban KD	Nhà đầu tư	Ghi chú bảo mật
Code, API	Editor	Không quyền	Không quyền	Không quyền	Chỉ Ban KT
Thiết kế UI/UX	Viewer	Editor	Không quyền	Không quyền	Chỉ Ban TK sửa
Business Plan	Viewer	Không quyền	Editor	Viewer	Không cho sửa
Slide Pitch	Viewer	Viewer	Editor	Viewer	Được tải PDF
API Keys, dữ liệu khách hàng	Không quyền	Không quyền	Không quyền	Không quyền	Chỉ người được phép

### 5. Trả lời 3 bẫy dữ liệu
Bẫy 1: Ban Kỹ thuật được xem Business Plan nhưng không được sửa.
- Cấp quyền: Viewer.
- Không cấp quyền Editor.
- Lý do: Ban Kỹ thuật chỉ cần đọc để hiểu dự án, không cần chỉnh sửa.
Bẫy 2: Nhà đầu tư muốn tải Slide Pitch về máy.
- Cấp quyền: Viewer.
- Cho phép tải xuống bản PDF.
- Không cấp quyền Editor.
- Không cần tắt Viewers can download, print, and copy vì nhà đầu tư cần tải tài liệu để thuyết trình.
Bẫy 3: Thành viên nghỉ việc.
 Xóa quyền truy cập Google Drive của thành viên.
- Xóa thành viên khỏi các nhóm được chia sẻ.
- Kiểm tra và thu hồi các quyền truy cập riêng lẻ.
- Nếu là tài khoản của công ty, khóa tài khoản khi cần thiết.
KẾT LUẬN
Việc sử dụng Google Drive và phân quyền hợp lý giúp CampusPay lưu trữ tài liệu an toàn, tránh rò rỉ thông tin và giúp các thành viên làm việc hiệu quả hơn. Mỗi người chỉ được truy cập những tài liệu cần thiết cho công việc của mình.
4. Nếu tài khoản thuộc quyền quản lý của tổ chức, vô hiệu hóa tài khoản khi cần thiết.
5. Kiểm tra lại để đảm bảo thành viên không còn quyền truy cập.

KẾT LUẬN
Hệ thống Google Drive của CampusPay được thiết kế theo nguyên tắc Least Privilege, giúp mỗi thành viên chỉ truy cập tài liệu cần thiết. Việc phân quyền rõ ràng, sử dụng Restricted, quản lý Version History và đặt thời hạn truy cập cho nhà đầu tư giúp bảo vệ dữ liệu và nâng cao hiệu quả cộng .
