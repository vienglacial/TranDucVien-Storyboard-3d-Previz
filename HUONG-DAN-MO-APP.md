# Jenny Pixel Studio — Cách mở app để LƯU ĐƯỢC offline

Bạn đang mở file `jenny-pixel-studio.html` bằng cách nhấp đúp (kiểu `file://`) trên **Chrome**.
Khi đó Chrome **chặn bộ nhớ lưu trữ** (localStorage) vì lý do bảo mật — nên Project và API key
không nhớ được giữa các lần mở. Đây là giới hạn của trình duyệt, không phải app hỏng.

Dưới đây là 3 cách khắc phục, xếp từ dễ tới chắc chắn nhất.

---

## Cách 1 — Dùng Firefox (dễ nhất, làm 10 giây)

Firefox **cho phép** lưu trữ với file mở trực tiếp.

1. Cài Firefox nếu chưa có.
2. Nhấp chuột phải vào file `jenny-pixel-studio.html` → **Open with** → **Firefox**.
   (hoặc kéo thả file vào cửa sổ Firefox)
3. Xong. Project tự lưu, API key nhớ luôn, không phải làm gì thêm.

---

## Cách 2 — Chạy qua localhost bằng Python (chắc chắn nhất, chạy tốt trên cả Chrome)

Cách này biến thư mục thành một "trang web nội bộ", trình duyệt sẽ cho lưu trữ đầy đủ.
Cần có Python trên máy (đa số máy Windows mới đã có; nếu chưa, tải tại python.org và nhớ tích "Add to PATH").

### Trên Windows:

1. Mở **thư mục chứa file** `jenny-pixel-studio.html`.
   Trong ví dụ của bạn là: `G:\My Drive\Studio Jenny\App Storyboard\`
2. Bấm vào **thanh địa chỉ của thư mục** (chỗ hiện đường dẫn), gõ `cmd` rồi Enter.
   → Cửa sổ Command Prompt mở ra ngay tại thư mục đó.
3. Gõ lệnh sau rồi Enter:

   ```
   python -m http.server 8080
   ```

   (Nếu báo không tìm thấy python, thử `py -m http.server 8080`)

4. Mở trình duyệt, vào địa chỉ:

   ```
   http://localhost:8080/jenny-pixel-studio.html
   ```

5. Giờ Project và API key lưu vĩnh viễn. Khi làm xong, quay lại cửa sổ đen bấm `Ctrl + C` để tắt server.

> Mẹo: lần sau chỉ cần lặp lại bước 2–4. Có thể tạo một file `.bat` chứa 2 dòng:
> ```
> python -m http.server 8080
> ```
> để bấm phát chạy luôn.

---

## Cách 3 — Vẫn dùng Chrome file:// nhưng lưu thủ công

Nếu không muốn cài gì, bạn vẫn dùng app bình thường trên Chrome, chỉ là phải tự lưu:

- **Trong lúc làm:** mọi thứ chạy ngon (thêm model, camera, tư thế, chụp shot, AI...).
  API key sau khi nhập sẽ dùng được tới khi đóng tab.
- **Trước khi đóng:** bấm nút **Xuất** trên thanh trên → tải về file `.json`.
- **Lần sau mở lại:** bấm **Nhập** → chọn file `.json` đó để tiếp tục.

Cách này hơi thủ công nhưng an toàn tuyệt đối: cảnh của bạn nằm trong file `.json`,
không phụ thuộc trình duyệt, chép sang máy nào cũng mở lại được.

---

## Tóm tắt nhanh

| Nhu cầu | Nên dùng |
|---|---|
| Nhanh gọn, không cài đặt | **Firefox** (Cách 1) |
| Chuyên nghiệp, dùng Chrome, nhớ vĩnh viễn | **localhost** (Cách 2) |
| Không cài gì, chấp nhận lưu tay | **Xuất/Nhập .json** (Cách 3) |

Dù chọn cách nào, các tính năng **không cần internet** vẫn chạy: thư viện model,
camera, tư thế, monitor, chụp shot. Chỉ 3 tính năng **AI** (dàn cảnh, dựng từ ảnh,
tạo vật thể) là cần API key + mạng.

— Jenny Pixel Studio · by Tran Duc Vien
