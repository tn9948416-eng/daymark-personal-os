# Cài DAYMARK lên iPhone

DAYMARK là một PWA (ứng dụng web có thể thêm vào Màn hình chính). Không cần cài qua App Store, nhưng cần có một URL HTTPS để iPhone mở được.

## 1. Đưa ứng dụng lên HTTPS bằng GitHub Pages

1. Đăng nhập GitHub và tạo repository mới tên `daymark-app`.
2. Mở thư mục `stride-life-os` trên máy tính.
3. Đưa **toàn bộ các file bên trong** thư mục đó lên thư mục gốc của repository: `index.html`, `manifest.webmanifest`, `sw.js`, các file icon, `.nojekyll` và `README.md`.
4. Mở repository → **Settings** → **Pages**.
5. Trong mục **Build and deployment**, chọn **Deploy from a branch**.
6. Chọn branch `main`, thư mục `/(root)`, rồi nhấn **Save**.
7. Sau khi GitHub Pages báo website đã được xuất bản, mở URL đó. Bật **Enforce HTTPS** nếu tùy chọn có sẵn.

Tài liệu chính thức: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

## 2. Thêm vào Home Screen

1. Trên iPhone, mở **Safari**.
2. Nhập URL HTTPS của DAYMARK.
3. Nhấn **Share / Chia sẻ**.
4. Chọn **Add to Home Screen / Thêm vào Màn hình chính**. Nếu chưa thấy, kéo xuống cuối bảng chia sẻ và tìm trong Edit Actions.
5. Bật **Open as Web App / Mở dưới dạng ứng dụng** nếu tùy chọn xuất hiện.
6. Nhấn **Add / Thêm**.
7. Mở biểu tượng DAYMARK mới xuất hiện trên Home Screen.

Tài liệu chính thức của Apple: https://support.apple.com/guide/iphone/open-as-web-app-iphea86e5236/ios

## 3. Chuyển dữ liệu từ máy tính sang iPhone

Dữ liệu trên máy tính và iPhone được lưu riêng trong từng trình duyệt. Để chuyển dữ liệu:

1. Máy tính: DAYMARK → Cài đặt → Xuất dữ liệu.
2. Chuyển file JSON riêng tư sang iPhone (ví dụ iCloud Drive hoặc cáp kết nối).
3. iPhone: DAYMARK → Cài đặt → Nhập dữ liệu từ file.

Không tải file backup chứa dữ liệu cá nhân lên repository công khai. GitHub Pages public site có thể xem được trên Internet.
