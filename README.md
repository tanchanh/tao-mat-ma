# Tạo Và Đánh Giá Mật Mã (Password Generator & Evaluator)

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Offline Ready](https://img.shields.io/badge/Offline-Ready-0d9488?style=for-the-badge)
![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

Ứng dụng web Single-Page tinh gọn, bảo mật cao giúp **sinh mật mã ngẫu nhiên chuẩn mã hoá** và **đánh giá độ mạnh của mật mã theo thời gian thực** (Real-time Live Validation).

Được xây dựng hoàn toàn bằng **HTML/CSS/JavaScript thuần (Vanilla)** trong một tập tin duy nhất, không sử dụng thư viện ngoài, không tải phông chữ từ xa và có thể khởi chạy tức thì offline 100%.

---

## 🌟 Tính Năng Nổi Bật

- **Kiến trúc Hợp nhất (All-in-One UX):** Không chia tab phức tạp. Ô mật mã trung tâm đóng vai trò kép: vừa là nơi hiển thị kết quả sinh mã, vừa cho phép người dùng click vào gõ tay, dán hoặc tinh chỉnh mật khẩu cá nhân.
- **Chuẩn mật mã ngẫu nhiên (CSPRNG):** Sử dụng `crypto.getRandomValues()` kết hợp giải thuật **Rejection Sampling** để triệt tiêu hoàn toàn sai số Modulo Bias, đảm bảo tính ngẫu nhiên tuyệt đối theo chuẩn bảo mật.
- **Xáo trộn vị trí đồng đều:** Áp dụng thuật toán **Fisher-Yates Shuffle** $O(n)$ giúp các nhóm ký tự bắt buộc không bị cố định ở đầu chuỗi.
- **Đánh giá độ mạnh thông minh:** Chấm điểm dựa trên sự kết hợp giữa độ dài chuỗi và độ đa dạng nhóm ký tự. Hỗ trợ tốt cho các cụm mật khẩu dài (Passphrase), ngăn chặn chuỗi lặp đơn điệu đạt điểm ảo.
- **Cơ chế sao chép đa nền tảng:** Tích hợp đồng thời Modern Clipboard API và phương thức dự phòng `execCommand('copy')` giúp nút Sao chép hoạt động trơn tru ngay cả trên môi trường `file://` nội bộ.
- **Trải nghiệm hiển thị cao cấp:**
  - Phông chữ mật mã to **`2rem`** chuẩn Monospace, căn giữa hoàn hảo.
  - Hệ thống biểu tượng vector thuần **`<svg>`** sắc nét, chống giật/nhấp nháy giao diện.
  - Bố cục co giãn linh hoạt (Mobile-first Responsive), nút bấm đạt chuẩn cảm ứng ($\ge 44\text{px}$).

---

## 📐 Quy Tắc & Giải Thuật Kỹ Thuật

### 1. Quy tắc sinh mật mã (Password Generation)
* **Độ dài tuỳ chọn:** Từ `4` đến `128` ký tự (mặc định: `16`).
* **4 nhóm ký tự hỗ trợ:**
  * Chữ hoa (`A-Z` - 26 ký tự)
  * Chữ thường (`a-z` - 26 ký tự)
  * Chữ số (`0-9` - 10 ký tự)
  * Ký hiệu đặc biệt (`!@#$%^&*()-_=+[]{};:,.?` - 24 ký tự)
* **Ràng buộc an toàn:** Luôn đảm bảo mỗi nhóm được chọn xuất hiện ít nhất 1 ký tự trong chuỗi kết quả. Tự động khoá chống bỏ chọn toàn bộ nhóm ký tự.

### 2. Tiêu chí đánh giá độ mạnh (Password Strength)
Gọi $L$ là độ dài chuỗi và $V$ là số nhóm ký tự có mặt ($0 \le V \le 4$):

| Mức độ | Tỉ lệ | Điều kiện áp dụng |
| :--- | :---: | :--- |
| **Rất mạnh** | `100%` | ($L \ge 20$ VÀ $V \ge 2$) **HOẶC** ($L \ge 16$ VÀ $V = 4$) |
| **Mạnh** | `75%` | ($L \ge 14$ VÀ $V \ge 3$) **HOẶC** ($L \ge 12$ VÀ $V = 4$) |
| **Trung bình** | `50%` | $L \ge 10$ VÀ $V \ge 2$ |
| **Yếu** | `25%` | Các trường hợp còn lại ($L > 0$) |
| **Trống** | `0%` | Ô mật mã rỗng ($L = 0$) |

---

## 🚀 Hướng Dẫn Sử Dụng & Khởi Chạy

Không cần cài đặt Node.js, Webpack hay cấu hình máy chủ Web phức tạp:

### Cách 1: Tải về và mở trực tiếp
1. Tải tập tin `index.html` về máy tính hoặc điện thoại.
2. Nhấp đúp vào tập tin `index.html` để mở ngay bằng bất kỳ trình duyệt web nào (Google Chrome, Microsoft Edge, Safari, Firefox...).

### Cách 2: Clone qua Git
```bash
# Sao chép kho lưu trữ
git clone https://github.com/<tai-khoan-cua-ban>/tao-va-danh-gia-mat-ma.git

# Mở thư mục
cd tao-va-danh-gia-mat-ma

# Chạy trực tiếp trên trình duyệt
open index.html # Trên macOS
# hoặc
start index.html # Trên Windows
```

---

## 🛠️ Công Nghệ Xây Dựng

* **Ngôn ngữ:** Vanilla HTML5, Modern CSS, Vanilla JavaScript (ES6+).
* **CSS Architecture:** Flexbox, CSS Grid, CSS Custom Properties (`:root` variables), tối giản bảng màu 4 màu chủ đạo.
* **Security & Web APIs:** Web Crypto API (`crypto.getRandomValues`), Async Clipboard API.
* **Zero Dependency:** 100% mã nguồn tự thân, kích thước siêu nhẹ (~15KB).

---

## 👤 Tác Giả

* **Tác giả:** **Dương Tấn Chánh**
* **Chuyên mục:** Ứng dụng web Single-Page / Lập trình Front-end hiệu năng cao.

---

## 📄 Giấy Phép (License)

Dự án được phân phối dưới giấy phép **MIT License**. Bạn được toàn quyền sử dụng, chỉnh sửa và tích hợp vào các dự án cá nhân hoặc thương mại.