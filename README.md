# ClaudeClaw — Hướng dẫn cài đặt

Bản thử **1.11.0** cho **Mac Apple Silicon** (M1, M2, M3, M4…). Bộ cài được tải công khai từ repository này; repository mã nguồn ứng dụng vẫn private.

[Trang tải bản phát hành](https://github.com/hoanghd218/claudeclaw-downloads/releases/tag/v1.11.0-preview.1)

## 1. Chuẩn bị

- Mac dùng chip Apple Silicon; bản này chưa hỗ trợ Mac Intel hoặc Windows.
- Cài **Node.js 22 trở lên** từ [nodejs.org](https://nodejs.org/en/download), sau đó mở lại Terminal.
- Internet để tải runtime khoảng **446 MB** và dùng dịch vụ AI.
- Tài khoản AI/API của bạn và bot Telegram riêng. Chi phí API do tài khoản của bạn chịu.

Kiểm tra trong Terminal:

```sh
node --version
npm --version
```

## 2. Chạy một lệnh để mở trình cài

Không cần tải ZIP thủ công, clone repository hoặc đăng nhập GitHub. Dán lệnh này vào Terminal:

```sh
npx --yes --package=https://github.com/hoanghd218/claudeclaw-downloads/releases/download/v1.11.0-preview.1/claudeclaw-local-installer-0.2.0.tgz claudeclaw-install
```

npx tải CLI rồi mở trang cài đặt trên trình duyệt. Manifest và public key tin cậy đã được chọn sẵn. **Giữ Terminal mở trong lúc dùng trình cài.** Nếu trình duyệt không tự mở, dùng URL được in trong Terminal; URL có token quản lý, không chia sẻ.

### Nếu máy đã chạy một ClaudeClaw khác

Dùng thư mục dữ liệu riêng để thử:

```sh
npx --yes --package=https://github.com/hoanghd218/claudeclaw-downloads/releases/download/v1.11.0-preview.1/claudeclaw-local-installer-0.2.0.tgz claudeclaw-install gui --home "$HOME/ClaudeClaw-Pilot"
```

Chọn **cổng 32550** nếu cổng 3141 đang dùng và **bot Telegram riêng**. Luôn giữ cùng `--home` cho các lệnh của instance thử.

## 3. Cài đặt và cấu hình lần đầu

1. Bấm **Cài đặt**. Trình cài tải runtime, kiểm tra chữ ký/hash và kiểm tra SQLite. Chờ thông báo thành công.
2. Trong **Thiết lập lần đầu**, nhập tên của bạn.
3. Nhập bot token riêng và Telegram chat ID của bạn. Có thể tạo bot bằng [@BotFather](https://t.me/BotFather).
4. Chọn **Claude** hoặc **OpenAI / Codex**. Nhập API key riêng; chỉ để trống nếu đã đăng nhập CLI tương ứng bằng đúng user trên máy. Preview chưa tự đăng nhập OAuth cho bạn.
5. Chọn cổng dashboard: mặc định **3141**, hoặc **32550** khi thử song song.
6. Bấm **Lưu cấu hình → Khởi động → Mở dashboard**.
7. Gửi một tin nhắn thử và kiểm tra phản hồi trước khi giao công việc thật.

Máy phải bật, không sleep và có mạng khi dùng AI. Sau khi khởi động, ứng dụng chạy độc lập với Terminal; preview chưa tự khởi động khi login/reboot.

## 4. Mở lại, kiểm tra và dừng

Mở lại trình quản lý bằng cùng lệnh ở bước 2. Sau reboot, bấm **Khởi động** rồi **Mở dashboard**.

Hoặc dùng các lệnh dưới đây cho instance mặc định:

```sh
# Xem trạng thái
npx --yes --package=https://github.com/hoanghd218/claudeclaw-downloads/releases/download/v1.11.0-preview.1/claudeclaw-local-installer-0.2.0.tgz claudeclaw-install status

# Kiểm tra runtime và database (sau khi đã cài)
npx --yes --package=https://github.com/hoanghd218/claudeclaw-downloads/releases/download/v1.11.0-preview.1/claudeclaw-local-installer-0.2.0.tgz claudeclaw-install doctor

# Dừng ứng dụng
npx --yes --package=https://github.com/hoanghd218/claudeclaw-downloads/releases/download/v1.11.0-preview.1/claudeclaw-local-installer-0.2.0.tgz claudeclaw-install stop
```

Nếu dùng instance thử, thêm `--home "$HOME/ClaudeClaw-Pilot"` cuối mỗi lệnh trên.

## 5. Dữ liệu và nâng cấp

- Home mặc định: `~/Library/Application Support/ClaudeClaw/`.
- Home thử trong hướng dẫn: `~/ClaudeClaw-Pilot/`.
- Dữ liệu không nằm trong cache npm/npx. Không xóa home nếu còn cần hội thoại, cấu hình hoặc tài liệu.
- Bản này dành cho **cài pilot mới**. Không dùng để nâng cấp deployment cũ khi chưa kiểm tra khóa ký đã ghim và phiên bản ứng dụng.
- Nâng cấp ứng dụng qua trình quản lý với manifest mới được xác nhận; `npm update` chỉ cập nhật CLI, không nâng cấp ứng dụng.

## Gặp lỗi

| Tình huống | Cách xử lý |
| --- | --- |
| `node` / `npx` không tìm thấy | Cài Node.js 22+ và mở Terminal mới |
| Báo chưa có runtime cho nền tảng | Hiện chỉ có macOS arm64; không ép dùng ZIP Mac cho Windows hoặc Mac Intel |
| Trình duyệt không tự mở | Mở URL localhost in trong Terminal |
| Cổng dashboard đang dùng | Chọn cổng khác, ví dụ 32550 |
| Không phản hồi AI/Telegram | Kiểm tra tài khoản AI/API, bot riêng và chat ID; xem trạng thái/log |
| Cài bị gián đoạn | Mở lại trình cài và xem trạng thái; nếu báo cần recovery, dùng nút phục hồi trước khi khởi động |

Khi gửi lỗi để hỗ trợ, che API key, bot token và URL quản lý có token. Không gửi backup chứa credentials.

## Phạm vi preview

Đã kiểm thử npx tải package từ GitHub public, cài signed runtime vào home riêng, SQLite probe và doctor. Chưa xác minh hội thoại AI/Telegram bằng tài khoản khách.

Chưa kèm skills cá nhân, voice/Python, War Room hoặc browser WhatsApp. Windows chưa có runtime trong release hiện tại. JavaScript ứng dụng đã làm rối và bỏ source map; vẫn có thể phân tích ngược. Chưa có mã kích hoạt hoặc giới hạn số máy.

CLI version **0.2.0**, ứng dụng version **1.11.0**. Không có khóa ký riêng, dữ liệu khách hoặc source TypeScript gốc của ứng dụng trong repository public và release assets.
