# Jenny Pixel Studio — Hướng dẫn chi tiết các chức năng

Công cụ dựng **storyboard / previz 3D** ngay trong trình duyệt. Bạn dàn khối 3D (người, xe, nhà, đồ vật…), đặt góc máy như máy quay thật, rồi **chụp shot** hoặc xuất **storyboard có nhãn + depth/edge map** để đưa cho AI tạo ảnh (GPT-Image, Nano Banana, ControlNet…) ra hình đúng góc.

> Chưa biết cách mở app để lưu được offline? Xem [HUONG-DAN-MO-APP.md](HUONG-DAN-MO-APP.md).

---

## Mục lục

1. [Bố cục màn hình](#1-bố-cục-màn-hình)
2. [Thanh công cụ trên cùng](#2-thanh-công-cụ-trên-cùng)
3. [Cột trái — Kho model](#3-cột-trái--kho-model)
4. [Vùng giữa — Viewport & công cụ](#4-vùng-giữa--viewport--công-cụ)
5. [Cột phải — các bảng điều khiển](#5-cột-phải--các-bảng-điều-khiển)
6. [Vật thể đang chọn (Inspector)](#6-vật-thể-đang-chọn-inspector)
7. [Chụp shot & Storyboard cho AI Image](#7-chụp-shot--storyboard-cho-ai-image)
8. [API & các tính năng AI (chi tiết)](#8-api--các-tính-năng-ai-chi-tiết)
9. [Project & lưu trữ](#9-project--lưu-trữ)
10. [Phím tắt](#10-phím-tắt)
11. [Quy trình gợi ý](#11-quy-trình-gợi-ý)

---

## 1. Bố cục màn hình

| Khu vực | Vai trò |
|---|---|
| **Thanh trên** | Undo/Redo, lưới sàn, project, xuất/nhập, chụp shot, storyboard |
| **Cột trái** | Kho model dựng sẵn, chia theo nhóm + ô tìm kiếm |
| **Vùng giữa (Viewport)** | Cảnh 3D, công cụ thao tác, màn hình xem trước (monitor) |
| **Cột phải** | AI dàn cảnh, tạo vật thể, máy quay, góc máy, chỉnh vật thể, danh sách shot |

Hai cột bên có thể **thu gọn** bằng nút mũi tên ở mép, hoặc ẩn cả hai bằng phím `~` / `Tab` để xem cảnh toàn màn hình.

---

## 2. Thanh công cụ trên cùng

| Nút | Chức năng |
|---|---|
| **Hoàn tác / Làm lại** | Undo (`Ctrl+Z`) / Redo (`Ctrl+Shift+Z`) |
| **Full** | Ẩn hai panel, xem cảnh toàn màn hình (`~` hoặc `Tab`) |
| **Hướng dẫn** | Mở bảng hướng dẫn nhanh + phím tắt (phím `?`) |
| **API Key** | Nhập key để dùng tính năng AI — xem [mục 8](#8-api--các-tính-năng-ai-chi-tiết) |
| **Lưới sàn** | Bật/tắt lưới mặt đất |
| **Xóa cảnh** | Xóa toàn bộ vật thể trong cảnh hiện tại |
| **Project** | Quản lý project lưu trong trình duyệt — xem [mục 9](#9-project--lưu-trữ) |
| **Xuất** | Lưu cảnh ra file `.json` (sao lưu / chép sang máy khác) |
| **Nhập** | Mở lại một file `.json` đã xuất |
| **Chụp shot** | Chụp khung hình hiện tại vào danh sách shot |
| **Storyboard** | Xuất ảnh previz có nhãn + depth/edge map + prompt cho AI image |

---

## 3. Cột trái — Kho model

Bấm vào một model là nó **xuất hiện ngay trong cảnh**. Gõ vào ô tìm kiếm (phím tắt `/`) để lọc nhanh, ví dụ "ghế", "xe", "súng".

Các nhóm có sẵn:

- **Người & Động vật** — nhân vật có khung xương (gập tư thế được)
- **Tư thế nhân vật** — đặt nhanh người ở các dáng dựng sẵn
- **Xe cộ**, **Quân sự**, **Vũ khí (đạo cụ)**
- **Kiến trúc**, **Đồ vật / Đô thị**
- **Nội thất** — Phòng khách · Bếp · Ngủ & Bàn ghế
- **Thiên nhiên**
- **Khối cơ bản** — hộp, trụ, cầu, nón… để tự ghép

---

## 4. Vùng giữa — Viewport & công cụ

### Thanh công cụ trong cảnh

| Công cụ | Phím | Tác dụng |
|---|---|---|
| **Orbit** | `Q` | Xoay camera quanh cảnh (chuột trái kéo) |
| **Di chuyển** | `G` | Kéo vật thể trên mặt đất; **giữ `Alt`** khi kéo để nâng lên / hạ xuống |
| **Xoay** | `E` | Xoay vật thể đang chọn |
| **Tỉ lệ** | `R` | Phóng to / thu nhỏ vật thể |
| **Monitor** | `M` | Bật/tắt màn hình xem trước (khung hình thật của "máy quay") |

### Điều khiển chuột

- **Chuột trái kéo** — xoay camera (Orbit)
- **Lăn chuột** — zoom
- **Chuột phải kéo** — lia (pan)
- **Bấm vật thể** — chọn để chỉnh
- **Shift + bấm** — chọn thêm nhiều vật, di chuyển/xoay cả nhóm (cần ở chế độ Orbit)

### Monitor & khung ngắm

**Monitor** (góc dưới viewport) hiển thị đúng khung hình camera sẽ chụp, kèm tiêu cự và lưới 1/3 — dùng để canh bố cục. Có thể bật **Khung 1/3 & safe area** ở bảng Máy quay để hiện đường gióng ngay trên cảnh.

---

## 5. Cột phải — các bảng điều khiển

### 5.1. AI dàn cảnh / bối cảnh
Dựng **cả một bối cảnh** (đường phố, căn phòng, nhiều vật) bằng AI:
- **Từ chữ:** mô tả cảnh → bấm *"AI dựng cảnh từ chữ"*. Có sẵn các gợi ý bấm nhanh.
- **Từ ảnh:** thả ảnh bối cảnh tham chiếu → *"AI phân tích & dựng bối cảnh"*. AI ước lượng bố cục thô (nhà/cây/xe thành khối) đủ để blocking góc máy. Có tùy chọn dán ảnh đầu làm background đối chiếu.

> Mục này dựng **bối cảnh**. Muốn tạo **một nhân vật có khớp** thì dùng mục 5.2.

### 5.2. AI tạo vật thể mới
- **Từ chữ:** gõ tên vật chưa có trong kho (vd "lò vi sóng", "xe máy") → *"AI lắp khối tạo vật thể"*. AI ghép 3–12 khối cơ bản thành vật, đặt vào cảnh, chỉnh như vật thường.
- **★ Tạo nhân vật có khớp từ ảnh:** thả ảnh **một nhân vật** → AI chọn khung xương khớp nhất (gà/người/chibi…), set tỉ lệ & màu. Kết quả **gập được tư thế** (tay/chân/thân) trong Inspector.

### 5.3. 🎭 Nhân vật từ ảnh (billboard)
Thả ảnh nhân vật (PNG nền trong) → app dán lên một tấm phẳng **luôn xoay về camera**. Đặt tên (Việt + Anh cho AI), chỉnh chiều cao. Di chuyển/scale/nâng cao như vật thường — để nhân vật "bay" giữa khung cảnh. Đây là cách giữ **đúng hình nhân vật thật** trong previz.

### 5.4. Background 2D
Tải ảnh nền (concept art, ảnh thật…). Hai kiểu: **Phông phẳng** (dán cố định sau cảnh) hoặc **Mặt phẳng 3D** (đặt trong không gian). Chỉnh **độ mờ, khoảng cách, kích thước**.

### 5.5. Máy quay
Mô phỏng máy quay thật:

| Thông số | Ý nghĩa |
|---|---|
| **Tiêu cự** (14–200mm) | Góc rộng ↔ tele. Có preset 18/24/35/50/70/85/135/200 kèm gợi ý dùng |
| **Khẩu độ** (f-stop) | Độ xóa phông (bokeh) |
| **Kiểu lens** | Thường · Anamorphic · Vintage |
| **Méo wide** | Lens < 40mm cong nhẹ ở mép như thật (tắt được để khung sạch) |
| **Cao độ máy** | Đặt máy cao/thấp (0.1–12m) |
| **Khung hình** | 2.39:1 · 1.85 · 16:9 · 1:1 |
| **Khung 1/3 & safe area** | Bật đường gióng bố cục |

### 5.6. Góc máy nhanh
Bấm để camera nhảy về góc dựng sẵn: **Chính diện, 3/4, Hông, Trên cao, Thấp, Bird's eye**. Chọn vật thể trước thì camera sẽ quay quanh vật đó.

### 5.7. Shot đã chụp
Danh sách thu nhỏ các khung đã chụp. Bấm để tải về làm tham chiếu storyboard.

---

## 6. Vật thể đang chọn (Inspector)

Khi chọn một vật, cột phải hiện đầy đủ điều khiển:

- **Tên** + **Tên tiếng Anh cho AI** (giúp AI hiểu đúng vật khi xuất storyboard)
- **Xoay** 3 trục: ngang (Y), ngả tới/sau (X), nghiêng trái/phải (Z)
- **Độ cao** (lên/xuống), **Tỉ lệ**
- **Màu khối** + bảng màu nhanh
- **Texture 2D** — dán ảnh thật lên khối (tải file hoặc dán URL). Hai chế độ: **Bọc vật thể** hoặc **Decal billboard** (tấm dán luôn hướng camera, chỉnh cỡ & cao thấp). *Mẹo: khối thô khó nhận ra → dán ảnh thật lên để AI hiểu ngay.*

**Với nhân vật có khung xương**, có thêm:
- **Chiều cao, độ mập, tỉ lệ chân, bề ngang vai**
- **Tư thế dựng sẵn:** Đứng · Ngồi ghế · Ngồi lái xe · Nằm · Ngồi xổm · Quỳ · Giơ tay · Chỉ tay · Chạy
- **Khớp tinh chỉnh:** cúi/ngả thân, gập hông, gập gối, đưa tay, gập khuỷu
- **Chỉnh phụ kiện** (mắt/mỏ/tóc/mũ/áo): vị trí 3 chiều, kích thước, màu riêng
- **Màu theo bộ phận:** cả người / đầu / thân / tay / chân

> Mẹo: **nháy đúp** vào bất kỳ thanh trượt nào để đưa về mặc định. Phím `Del` xóa vật đang chọn.

---

## 7. Chụp shot & Storyboard cho AI Image

**Chụp shot** lưu khung hình hiện tại vào danh sách bên phải.

**Storyboard** (nút cam trên thanh trên) mở bảng xuất bộ tài liệu cho AI tạo ảnh:

| Đầu ra | Dùng để |
|---|---|
| **Ảnh có nhãn** (Việt+Anh) | Cho GPT-Image / Nano Banana hiểu mỗi khối là gì |
| **Ảnh sạch** | Bản không nhãn |
| **Depth map** | Khóa góc + chiều sâu (đưa vào ControlNet Depth) |
| **Edge map** | Khóa hình khối (ControlNet Canny) |
| **Prompt mô tả** | Copy dán kèm ảnh. Có nút **"✨ AI viết prompt điện ảnh"** (cần API key) |

> Depth/Edge map là tín hiệu **mạnh nhất** để khóa góc máy: đưa vào ControlNet trên Replicate/ComfyUI → giữ góc gần như 100%, tự do đổi phong cách.

---

## 8. API & các tính năng AI (chi tiết)

### Những tính năng nào cần API?
Chỉ **3 nhóm tính năng AI** cần API key + mạng:
1. **AI dàn cảnh / dựng bối cảnh** (từ chữ và từ ảnh) — mục 5.1
2. **AI tạo vật thể / nhân vật có khớp từ ảnh** — mục 5.2
3. **AI viết prompt điện ảnh** trong bảng Storyboard — mục 7

Mọi thứ còn lại (kho model, camera, tư thế, monitor, chụp shot, depth/edge map) **chạy offline, không cần key**.

### Dùng model nào?
Ô **"Model AI"** ở đầu mục 5.1 áp dụng cho *tất cả* tính năng AI:

| Model | Đặc điểm |
|---|---|
| **Haiku 4.5** | Nhanh, rẻ nhất |
| **Sonnet 4.6** | Cân bằng — **nên dùng** (mặc định) |
| **Opus 4.7** | Mạnh nhất, đắt nhất |

### Cách lấy API key (Claude API)
App gọi **thẳng tới Claude API của Anthropic** bằng key của *chính bạn*:

1. Vào **console.anthropic.com**, đăng ký / đăng nhập (tài khoản này **khác** tài khoản Claude.ai thường).
2. Vào **Billing**, thêm thẻ và nạp một ít credit. API tính tiền **theo lượng dùng** — dựng vài cảnh rất rẻ.
3. Vào **Settings → API Keys → Create Key**, đặt tên rồi **copy ngay** (key chỉ hiện một lần, dạng `sk-ant-...`).
4. Trong app, bấm **API Key** trên thanh trên, dán key vào, bấm **Lưu**.

### Key được lưu ở đâu? Có an toàn không?
- Key lưu trong **localStorage của trình duyệt máy bạn** (khóa `previz_api_key`), **không** nằm trong file `.json` xuất ra và **không** được đẩy lên GitHub.
- Khi gọi AI, key chỉ được gửi tới **api.anthropic.com**, không đi đâu khác.
- **Đừng** chia sẻ trình duyệt / máy đã lưu key cho người khác dùng.

### Mỗi người bạn cần key riêng
Khi bạn gửi link cho bạn bè dùng, **mỗi người phải tự nhập key của họ** — chi phí AI tính vào tài khoản Anthropic của từng người. Key chỉ nằm trong trình duyệt của họ, bạn không thấy và không bị tính tiền hộ.

### Lưu ý khi chạy offline (mở file `file://`)
Mở app bằng cách nhấp đúp trên **Chrome** sẽ bị chặn lưu lâu dài → key dùng được trong phiên nhưng lần sau phải nhập lại. Muốn nhớ vĩnh viễn: dùng **Firefox**, chạy qua **localhost**, hoặc mở qua link **GitHub Pages** (web thật, lưu được). Xem [HUONG-DAN-MO-APP.md](HUONG-DAN-MO-APP.md).

### Khi báo lỗi
- *"API key sai hoặc hết hạn"* → key nhập sai hoặc đã thu hồi (HTTP 401).
- *"Không kết nối được tới API"* → mất mạng, hoặc chưa nhập key khi chạy offline.
- Hết credit trong tài khoản Anthropic → vào Billing nạp thêm.

---

## 9. Project & lưu trữ

- **Project:** bấm **Project** → tạo project mới; app **tự lưu** vào trình duyệt mỗi khi bạn chỉnh (hiện "✓ Đã lưu"). Mở lại lần sau là còn nguyên (nếu trình duyệt cho lưu — xem mục offline ở trên).
- **Xuất / Nhập `.json`:** sao lưu chắc chắn nhất, không phụ thuộc trình duyệt; chép sang máy nào cũng mở lại được.

---

## 10. Phím tắt

| Phím | Tác dụng |
|---|---|
| `Q` / `G` / `E` / `R` | Orbit / Di chuyển / Xoay / Tỉ lệ |
| `Alt` (khi kéo `G`) | Nâng lên / hạ xuống |
| `M` | Bật/tắt monitor |
| `~` / `Tab` | Toàn màn hình (ẩn 2 panel) |
| `/` | Nhảy tới ô tìm kiếm model |
| `?` | Mở bảng hướng dẫn |
| `Del` | Xóa vật đang chọn |
| `Ctrl+Z` / `Ctrl+Shift+Z` | Hoàn tác / Làm lại |
| **Nháy đúp thanh trượt** | Đưa về mặc định |

---

## 11. Quy trình gợi ý

1. **Thêm chủ thể** — bấm model cột trái, hoặc dùng AI dàn cảnh / dựng từ ảnh.
2. **Sắp đặt** — dùng Di chuyển / Xoay / Tỉ lệ, chỉnh tư thế nhân vật trong Inspector.
3. **Đặt máy quay** — xoay camera, chọn tiêu cự / khẩu độ / cao độ / góc máy nhanh; canh bố cục bằng monitor + khung 1/3.
4. **Chụp shot** — lưu các khung ưng ý.
5. **Storyboard** — xuất ảnh có nhãn + depth/edge map + prompt, đưa cho AI tạo ảnh ra hình điện ảnh đúng góc.
6. **Lưu việc** — tạo Project (tự lưu) hoặc Xuất `.json` để sao lưu.

---

— *Jenny Pixel Studio · 3D Storyboard Studio · by Tran Duc Vien*
