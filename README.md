# DashShell — PowerShell Overlay Monitor

Ứng dụng Windows dạng overlay luôn nổi trên desktop: dashboard CPU / RAM / nhiệt độ / mạng realtime, **PowerShell
terminal thật** nhiều tab, ghi chú, theo dõi hạn mức Claude Code / Codex / Antigravity và báo qua Telegram khi agent
AI chạy xong.

Repo này chỉ chứa **bản cài đặt**.

## ⬇️ Tải về

**[Tải bản mới nhất](https://github.com/1995mars/dashshell-releases/releases/latest)** → trong mục *Assets*, chọn một
trong ba file:

| File | Dùng khi |
|---|---|
| `PowerShell-Overlay-Monitor_<phiên bản>_x64-setup.exe` | **Khuyến nghị** — bộ cài thường, có shortcut Start menu |
| `PowerShell-Overlay-Monitor_<phiên bản>_x64_en-US.msi` | Cài hàng loạt / qua chính sách công ty |
| `powershell-overlay-monitor.exe` | Bản portable, chạy luôn không cần cài |

## Yêu cầu hệ thống

- Windows 10 / 11, 64-bit.
- WebView2 Runtime (Windows 11 có sẵn; bộ cài tự tải nếu thiếu).
- Tuỳ chọn: PowerShell 7 (`winget install Microsoft.PowerShell`) — không có thì dùng Windows PowerShell 5.1.

## Tính năng

- **Dashboard realtime:** CPU (%, GHz, biểu đồ), RAM, nhiệt độ CPU / GPU NVIDIA / SSD, upload/download mạng.
- **Terminal PowerShell thật** (ConPTY): nhiều tab, màu ANSI, tiếng Việt, gợi ý lệnh kiểu VS Code.
- **Overlay:** luôn nổi, click-through (chuột xuyên qua), chỉnh độ trong suốt, nền Glass / Acrylic / Mica.
- **Hạn mức AI:** Claude Code (nhiều tài khoản), Codex, Antigravity — cùng số liệu với lệnh `/usage`.
- **Báo khi agent xong việc:** toast Windows + Telegram khi Claude Code / Codex / Antigravity xong lượt hoặc chờ xác
  nhận; điều khiển terminal từ Telegram (tuỳ chọn).
- Ghi chú, giá vàng trong nước / thế giới, hẹn giờ bật máy từ Sleep, thu xuống khay hệ thống.

## Cài đặt

1. Chạy file `..._x64-setup.exe` vừa tải.
2. Nếu Windows hiện **"Windows protected your PC"** (SmartScreen): bấm **More info → Run anyway**. Cảnh báo này xuất
   hiện vì bộ cài chưa có chứng chỉ ký mã thương mại.
3. Làm theo trình cài đặt, rồi mở **PowerShell Overlay Monitor** từ Start menu.

Bấm **X** chỉ thu app xuống khay hệ thống; muốn thoát hẳn: chuột phải icon ở khay → **Thoát**.

## Báo Telegram khi agent AI xong việc (tuỳ chọn)

1. Tạo bot bằng [@BotFather](https://t.me/BotFather) (`/newbot`), copy bot token.
2. Trong app: **Settings → Telegram** → dán token → **Lưu** → nhắn một tin bất kỳ cho bot → bấm **Lấy** chat ID →
   **Gửi thử**.
3. Bấm **Đồng bộ Claude / Codex / AGY** để agent chạy ở terminal bất kỳ (kể cả khi app tắt) cũng báo khi xong task.
   Bật **Luôn gửi khi agent xong task** nếu muốn nhận tin cả lúc đang xem app.

Bot token lưu trong Windows Credential Manager của máy bạn, không gửi đi đâu ngoài Telegram.

## Xử lý sự cố

| Vấn đề | Cách xử lý |
|---|---|
| Nhiệt độ CPU hiện `--` | Mainboard không có ACPI thermal zone. Kiểm tra: `Get-CimInstance Win32_PerfFormattedData_Counters_ThermalZoneInformation`. |
| Nhiệt độ SSD hiện `--` | Cần chạy app bằng **Run as Administrator**; một số ổ NVMe không hỗ trợ. |
| Bật click-through xong không bấm được app | Chuột phải icon ở khay → *Bật/Tắt Click-through*. |
| "An Application Control policy has blocked this file" | Smart App Control đang chặn file chưa ký: tắt trong Windows Security → App & browser control. |
| Terminal không mở | Đặt đường dẫn shell trong Settings → Terminal. |

## Gỡ cài đặt

**Settings → Apps → Installed apps → PowerShell Overlay Monitor → Uninstall.** Bản portable thì chỉ cần xoá file exe.
