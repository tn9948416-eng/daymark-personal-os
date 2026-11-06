# DAYMARK 2.1 — Personal Operating System

DAYMARK là ứng dụng web quản lý cá nhân có game hóa, thiết kế mobile-first để chạy trên máy tính và iPhone dưới dạng PWA.

## Điểm mới trong 2.1

- **AI Life Coach:** phân tích cục bộ công việc, thói quen, mục tiêu và thời gian tập trung; gợi ý 1–3 bước tiếp theo. Có thể chia sẻ bản tóm tắt sang ChatGPT khi người dùng chủ động chọn. Chưa tích hợp API mô hình AI hoặc gửi dữ liệu ngầm.
- **Life RPG:** XP, level, xu ảo, nhiệm vụ ngày, cây kỹ năng, huy hiệu và cửa hàng phần thưởng không dùng tiền thật.
- **Second Brain:** tạo/sửa/xóa ghi chú, thư mục, tags, ghim, tìm kiếm và sao chép.
- **Smart Analytics:** biểu đồ tập trung 7 ngày, tỷ lệ check-in thói quen, hoạt động theo lĩnh vực và tiến độ mục tiêu.
- **Pomodoro bền hơn:** dùng mốc thời gian thực, có lưu trạng thái bắt đầu/tạm dừng để giảm sai lệch khi Safari đưa ứng dụng xuống nền.
- **PWA nâng cấp:** manifest, icon PNG cho iOS, service worker có phiên bản, cache offline và giao diện điều hướng ngang trên màn hình nhỏ.
- Giữ khả năng đọc dữ liệu `daymark-v1` từ phiên bản trước; dữ liệu mới lưu ở `daymark-v2`.

## Chạy trên máy tính

1. Giải nén thư mục `DAYMARK-Personal-OS.zip`.
2. Mở thư mục `stride-life-os` bằng VS Code.
3. Cài extension **Live Server**.
4. Nhấp chuột phải `index.html` → **Open with Live Server**.

Có thể dùng Python nếu đã cài:

```bash
python -m http.server 5500
```

Sau đó mở `http://localhost:5500`.

## Cài DAYMARK lên iPhone

Để cài ổn định từ iPhone, DAYMARK cần được đăng lên một địa chỉ **HTTPS**. Địa chỉ Live Server `localhost` trên máy tính không phải địa chỉ mà iPhone có thể truy cập từ xa.

### Đăng miễn phí bằng GitHub Pages

1. Đăng nhập GitHub và tạo repository mới, ví dụ `daymark-app`.
2. Mở thư mục `stride-life-os` trên máy tính. Tải **các file bên trong thư mục này** lên thư mục gốc của repository, không tải thư mục backup hoặc file ZIP.
3. Trên repository GitHub, mở **Settings → Pages**.
4. Trong **Build and deployment**, chọn **Deploy from a branch**.
5. Chọn branch `main`, thư mục `/(root)`, rồi nhấn **Save**.
6. Chờ GitHub Pages triển khai và mở đường dẫn website được cung cấp trong phần Pages. Bật **Enforce HTTPS** nếu tùy chọn xuất hiện.
7. Trên iPhone, mở đường dẫn HTTPS đó bằng **Safari**.
8. Nhấn **Share / Chia sẻ** → **Add to Home Screen / Thêm vào Màn hình chính**. Bật **Open as Web App / Mở dưới dạng ứng dụng** nếu tùy chọn xuất hiện, rồi nhấn **Add / Thêm**.
9. Mở biểu tượng DAYMARK trên Home Screen. Hãy mở app khi có Internet ít nhất một lần để tải bộ vỏ ứng dụng và cache offline.

Hướng dẫn chính thức: [GitHub Pages — cấu hình nguồn triển khai](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site) · [Apple — biến website thành ứng dụng trên iPhone](https://support.apple.com/guide/iphone/open-as-web-app-iphea86e5236/ios).

**Lưu ý:** với GitHub Free, GitHub Pages thường cần repository public. Mã nguồn website sẽ công khai trên Internet. Không đưa file backup JSON, mật khẩu, hoặc dữ liệu cá nhân lên repository. Dữ liệu người dùng của DAYMARK được lưu trong bộ nhớ trình duyệt, không nằm trong các file website.

## Dùng dữ liệu trên máy tính và iPhone

DAYMARK **chưa có đồng bộ đám mây tự động**. Trình duyệt trên máy tính và iPhone có bộ nhớ riêng:

1. Trên thiết bị cũ, vào **Cài đặt → Xuất dữ liệu (.json)**.
2. Chuyển file JSON sang thiết bị mới bằng một cách riêng tư (ví dụ iCloud Drive, cáp hoặc dịch vụ lưu trữ cá nhân).
3. Trên thiết bị mới, vào **Cài đặt → Nhập dữ liệu từ file**.

Không tải file backup cá nhân lên repository GitHub công khai.

## Dữ liệu và quyền riêng tư

- Công việc, mục tiêu, thói quen, ghi chú, nhật ký, XP và lịch sử tập trung lưu bằng `localStorage` trên từng trình duyệt.
- Ứng dụng không có tài khoản, backend hoặc đồng bộ nhiều thiết bị trong bản này.
- AI Coach sử dụng gợi ý theo quy tắc ở ngay trên thiết bị; không gọi mô hình AI ẩn. Chức năng chia sẻ chỉ chạy khi người dùng bấm nút và chọn ứng dụng đích.
- Service worker cache giao diện để hỗ trợ mở lại khi offline sau lần tải đầu tiên. Những tính năng cần mạng hoặc AI bên ngoài không hoạt động offline.
- Xóa dữ liệu website hoặc xóa app khỏi iPhone có thể làm mất dữ liệu cục bộ chưa sao lưu. Hãy xuất JSON định kỳ.

## Tệp chính

- `index.html` — giao diện và logic ứng dụng.
- `manifest.webmanifest` — cấu hình PWA.
- `sw.js` — service worker và cache offline.
- `icon.svg`, `icon-180.png`, `icon-192.png`, `icon-512.png` — biểu tượng ứng dụng.
- `.nojekyll` — giúp GitHub Pages phục vụ các file tĩnh đúng cách.
