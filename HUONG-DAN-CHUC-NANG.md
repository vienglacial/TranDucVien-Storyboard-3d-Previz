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

> **Giao diện mới (09/2026):** cột **trái = KHO** (mọi thứ để *thêm* vào cảnh, nhấn màu hổ phách),
> cột **phải = CHỈNH** (cái đang chọn, nhấn màu xanh trời) và chia **4 tab**: `Vật thể` · `Camera` · `AI` · `Shot`.
> Chọn một vật thể là tự nhảy sang tab Vật thể; bấm Chụp shot là nhảy sang tab Shot.
> Công cụ Orbit / Di chuyển / Xoay / Tỉ lệ nằm ở **dock dưới viewport**. Số đo và phím tắt dùng font mono, chữ còn lại dùng Be Vietnam Pro.


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
| **Màn hình** | Nhiều góc nhìn & nhiều màn hình: bật **4 góc nhìn** (`V`), mở **cửa sổ phụ** (Màn hình máy quay / 4 góc nhìn), **Bố cục 2 / 3 màn hình** — xem [Nhiều màn hình](#nhiều-màn-hình-2--3-màn) |
| **Full** | Ẩn hai panel, xem cảnh toàn màn hình (`~` hoặc `Tab`) |
| **Hướng dẫn** | Mở bảng hướng dẫn nhanh + phím tắt (phím `?` / `H`); nút **⌨ Tùy chỉnh phím tắt** trong bảng để tự gán phím — xem [mục 10](#10-phím-tắt) |
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

- **Gánh xiếc nửa đêm · Khối bối cảnh** — *Thung lũng rạp xiếc* khổng lồ dựng theo bản đồ tổng thể + mặt cắt (1 px bản đồ = 0.15 m: đáy thung lũng ~207 × 167 m, lều Ø30 m; Pipo = Coppa = 1 m). Gốc = tâm lều trên đáy thung lũng (y=0), bắc = −Z, đông = +X. Cao độ: đáy 0 · trần sương 28–34 m · gờ đá = mặt rừng +36 m · vách đá cao + vành thung lũng +51 m. Có đủ đường vô (A rừng chết → B màn dây leo → C hầm đom đóm → D quầy vé → E cổng rèm → 1 loa kèn trên ngay sau rèm → 2 ống kèn xoắn 2,5 vòng quanh cây trụ → 3 loa dưới → 4 hồ banh), đường ra (R1 cửa xoay một chiều → R2 cầu thang zig-zag bám vách → R3 trạm lối ra có băng rôn EXIT → R4 gờ dẫn ngược về cổng soát vé), thang máy tơ M của Madame, lều mạng nhện, đường ray hạt đậu phộng + tàu, đu quay, bập bênh, nhà ma + hầm khu vui chơi, hồ nước chanh + thác, quầy hàng, cây kẹo bông; 23 bookmark góc máy. *Trần sương* là bộ phận riêng đang **tắt** (như bản đồ) — bật lên khi quay từ gờ nhìn ra biển mây hoặc từ đáy nhìn lên. *Ánh sáng phép thuật* là đèn chỉ chiếu trong lòng thung lũng, gờ đá và rừng vẫn là đêm thật (tắt bộ phận này nếu muốn cả cảnh tối). Lấy lẻ được: lều mạng nhện, đu quay nhỏ, nhà ma, bập bênh, quầy vé, cây kẹo bông
- **Titanic · Khối bối cảnh** — *Titanic + biển + tảng băng* (tỉ lệ thật 269 m, 12 bookmark góc máy) và *Tảng băng trôi (riêng)*. Mực nước y=0, mũi tàu hướng +Z, mạn phải = -X. Sàn đi lại được: boong mũi ~16 m (Rose & Jack đứng ở mũi, dang tay "I'm flying" — ẩn/tách được), boong giếng 12.6 m, tầng B 17.9 m, boong xuồng cứu sinh 20.8 m, ụ quan sát 29 m. Thả nhân vật lên tàu rồi bấm `End` để rơi đúng xuống mặt boong. Tảng băng là bộ phận riêng, kéo đi tuỳ cảnh
- **Người & Động vật** — nhân vật có khung xương (gập tư thế được)
- **Tư thế nhân vật** — đặt nhanh người ở các dáng dựng sẵn
- **Xe cộ**, **Quân sự**, **Vũ khí (đạo cụ)**
- **Máy bay · Khoang hành khách** — ghế economy có tay vịn (đơn / hàng 3 ghế), ghế có sẵn hành khách, và **Khoang máy bay** trọn bộ: 5 hàng ghế 3+3, lối đi giữa, cửa sổ, ngăn hành lý, trần đèn. Bản *Khoang + hành khách* có sẵn người ngồi (bỏ trống ~1/4 ghế cho tự nhiên). Mỗi dãy 3 ghế là một vật thể riêng → bấm chọn dãy để xóa / di chuyển / xoay từng dãy; vỏ khoang là vật thể riêng. Chọn một dãy rồi bấm **Tách hành khách** trong Inspector (hoặc *Tách toàn bộ … trong cảnh*) để mỗi người thành một vật thể riêng — sau đó bấm từng người và nhấn `Del` để chừa ghế trống. Muốn thêm người trở lại thì dùng model **Khách ngồi (rời)**. Khi thêm khoang, camera tự nhảy vào đầu lối đi. Vỏ khoang chỉ vẽ mặt trong nên xoay camera ra ngoài vẫn nhìn xuyên vào được; đặt camera trong lối đi (cao ~1.2–1.4m) để lấy góc máy như phim.
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
| **Di chuyển** | `W` | Hiện **gizmo trục X/Y/Z**: kéo mũi tên để dời theo đúng 1 trục. Kéo thân vật vẫn trượt trên mặt đất như cũ; **giữ `Alt`** khi kéo thân vật để nâng lên / hạ xuống |
| **Xoay** | `E` | Gizmo **3 vòng xoay** X/Y/Z (+ vòng ngoài xoay theo hướng nhìn). Kéo thân vật vẫn xoay ngang như cũ |
| **Tỉ lệ** | `R` | Gizmo **hộp tỉ lệ**: kéo hộp nào vật cũng phóng **đều** (app lưu một hệ số tỉ lệ) |
| **Thế giới / Cục bộ** | `X` | (hiện khi đang W/E/R) trục gizmo cố định theo thế giới hay xoay theo hướng của vật |
| **Bắt bước** | giữ `Ctrl` | (hiện khi đang W/E/R) kéo trục nhảy theo lưới **0.25 m · 15° · 0.1×**. Bật nút này = luôn bắt bước; giữ `Ctrl` khi kéo = đảo tạm |
| **Monitor** | `M` | Bật/tắt màn hình xem trước (khung hình thật của "máy quay") |
| **4 góc** | `V` | Chia viewport thành 4 ô: **Trên · Phối cảnh · Trước · Phải** |

> Viewport hẹp (laptop, hai panel đang mở) thì thanh công cụ tự bỏ chữ phím tắt, hẹp nữa thì chỉ còn icon — rê chuột lên nút vẫn thấy tên.
>
> Phím trong bảng là **phím mặc định** — đổi được hết (phím `K`), xem [Tùy chỉnh phím tắt](#tùy-chỉnh-phím-tắt-tự-gán-phím). Nhãn phím trên nút và tooltip tự đổi theo.

### Gizmo trục X / Y / Z (như các app 3D)

Chọn một vật rồi bấm **W / E / R**: ngay tại vật hiện tay cầm 3 trục — **X đỏ**, **Y xanh lá** (lên–xuống), **Z xanh dương** — cùng màu với 2 đường trục đỏ/xanh trên lưới sàn.

- **Di chuyển (W):** kéo **mũi tên** = dời theo 1 trục; kéo **ô vuông nhỏ** giữa 2 trục = dời trong mặt phẳng đó (ô vuông xanh lá = trượt trên mặt sàn XZ).
- **Xoay (E):** kéo **vòng** đỏ / xanh lá / xanh dương = xoay quanh trục đó; vòng ngoài cùng = xoay theo hướng nhìn của camera. Đây là cách nhanh nhất để nghiêng / lật vật (trước đây chỉ có thanh trượt trục X/Z).
- **Tỉ lệ (R):** kéo hộp bất kỳ = phóng to / thu nhỏ đều cả vật.
- Khi đang kéo, góc trên viewport hiện **số đo** (dời bao nhiêu mét theo trục nào, xoay bao nhiêu độ, tỉ lệ bao nhiêu lần); panel phải cập nhật theo.
- **Chọn nhiều vật** (Shift+bấm ở Orbit) rồi kéo gizmo: cả nhóm dời / xoay quanh vật chính / phóng cùng nhau.
- Gizmo chỉ là **công cụ làm việc**: không lọt vào ảnh **Chụp shot**, **Storyboard**, **monitor** hay **video cú máy**.
- Đang ở W / E / R vẫn **lia bằng chuột phải** và **lăn để zoom** được; muốn xoay camera thì về **Q**.
- Mỗi lần thả chuột là một bước **Ctrl+Z** hoàn tác.

### 4 góc nhìn (phím V)

Như các app 3D: viewport chia 4 ô — **TRÊN** (nhìn thẳng xuống, bắc ở trên), **PHỐI CẢNH** (chính là **camera chụp**, có gizmo, chọn/kéo vật như thường), **TRƯỚC** (nhìn từ +Z) và **PHẢI** (nhìn từ +X). Ba ô Trên/Trước/Phải là hình chiếu **trực giao** (không phối cảnh) nên canh khoảng cách, thẳng hàng, độ cao rất dễ.

- Trong ô Trên / Trước / Phải: **lăn** = zoom về chỗ con trỏ (Shift = bước tinh) · **chuột phải / giữa kéo** = lia · **bấm** = chọn vật (Shift = chọn thêm) · **kéo vật** = dời / xoay / tỉ lệ ngay trong mặt phẳng ô đó (theo công cụ W / E / R đang chọn; giữ `Ctrl` = bắt bước) · **nháy đúp** = lấy chỗ đó làm tâm ô.
- **Phím F** = khung vừa vật đang chọn ở cả camera chính lẫn 3 ô trực giao.
- **Đường màu cam** trong các ô trực giao = tầm nhìn của camera chụp (hình chóp ống kính + tam giác chỉ đỉnh khung + dấu + là tâm xoay) → nhìn từ trên xuống thấy ngay máy đang đặt ở đâu, chĩa đi đâu.
- Ô trực giao **bỏ sương mù** và **ẩn vòm trời / sao / trăng** của các khối bối cảnh lớn (nhìn từ ngoài vòm sẽ che hết cảnh).
- Chụp shot / Storyboard / monitor vẫn ra **một khung camera chụp** như bình thường.
- Để nhẹ máy: ô phối cảnh vẽ mỗi khung hình, 3 ô trực giao vẽ luân phiên (ô đang thao tác thì vẽ liên tục).

### Nhiều màn hình (2 – 3 màn)

Bấm nút **Màn hình** trên thanh trên cùng:

| Mục | Tác dụng |
|---|---|
| **4 góc nhìn trong khung chính** | Như phím `V` |
| **Cửa sổ: Màn hình máy quay** | Cửa sổ riêng chỉ hiện **khung chụp sạch** (đúng tỉ lệ khung, viền đen, không gizmo) + tiêu cự — kéo sang màn hình khác làm "màn hình đạo diễn" |
| **Cửa sổ: 4 góc nhìn** | Cửa sổ riêng 4 ô Trên / **Phối cảnh tự do** / Trước / Phải. Ô phối cảnh ở đây xoay tự do (chuột trái xoay, phải lia, lăn zoom, nháy đúp lấy tâm) và **không đụng camera chụp** |
| **Bố cục 2 màn hình** | Màn 1: app · Màn 2: Màn hình máy quay |
| **Bố cục 3 màn hình** | Màn 1: app · Màn 2: 4 góc nhìn · Màn 3: Màn hình máy quay |
| **Đóng các cửa sổ phụ** | Đóng hết cửa sổ phụ |

- **Chrome / Edge:** lần đầu bấm *Bố cục 2/3 màn hình*, trình duyệt hỏi quyền **"Quản lý cửa sổ trên tất cả màn hình"** → **Cho phép** để app tự đặt mỗi cửa sổ lên đúng màn hình (sắp theo thứ tự trái → phải). Trình duyệt khác: cửa sổ vẫn mở, bạn kéo tay sang màn kia.
- Trình duyệt chỉ cho **mở 1 cửa sổ mỗi lần bấm**: nếu app báo, bấm lại *Bố cục 3 màn hình* để mở cửa sổ còn lại. Nếu bị chặn popup: bấm biểu tượng chặn trên thanh địa chỉ → **Luôn cho phép**.
- Mỗi cửa sổ phụ có nút **⛶ Toàn màn hình** (hoặc F11) và **⇄ Đổi** (máy quay ⇄ 4 góc).
- Cửa sổ phụ chạy **trực tiếp cùng cảnh**: chọn / kéo vật ở màn nào cũng cập nhật mọi màn. Các phím tắt (W/E/R/Q, Del, Ctrl+Z, G, T, End…) gõ ở cửa sổ phụ vẫn tác dụng lên app. Nút **Màn hình** hiện số cửa sổ phụ đang mở.
- Đóng / tải lại app chính thì các cửa sổ phụ cũng đóng theo.

### Điều khiển chuột

- **Chuột trái kéo** — xoay camera (Orbit)
- **Lăn chuột** — zoom **về phía điểm đang trỏ**, nên ngắm chi tiết nhỏ trong cảnh lớn vẫn tới được
- **Shift + lăn** — zoom bước tinh (3%/nấc) để canh khung chính xác
- **Ctrl/Alt + lăn** — zoom bước thô (30%/nấc) để nhảy nhanh giữa hai cỡ cảnh
- **Bấm đúp vào đâu** — lấy đúng chỗ đó làm **tâm xoay**, camera tự lại gần. Đây là cách nhanh nhất để soi một chi tiết trong set lớn
- **Phím F** — lấp đầy khung bằng vật đang chọn; không chọn gì thì khung vừa toàn cảnh
- **Lăn tiếp khi đã sát tường** — camera **đi xuyên qua** tường/vỏ khối để vào trong (phòng bida, khoang máy bay)
- **Mũi tên ↑↓←→** — đi bộ tới/lùi/ngang; **PageUp/PageDown** — lên/xuống; giữ **Shift** để bước nhỏ
- **Chuột phải kéo** — lia (pan), tốc độ tự co theo độ xa gần
- **Bấm vật thể** — chọn để chỉnh
- **Shift + bấm** — chọn thêm nhiều vật, di chuyển/xoay cả nhóm (cần ở chế độ Orbit)
- **Bấm vật nhỏ khi zoom xa** — không cần trúng từng pixel: bấm lệch khoảng 15 px quanh một người/đạo cụ tí hon vẫn chọn được nó chứ không dính khối nền bên dưới
- **Lens góc rộng (< 30mm)** — ảnh bị méo barrel; bấm/kéo/zoom theo con trỏ đã tính theo ảnh méo nên bấm đúng chỗ thấy trên màn hình
- **Phím T** — ẩn/hiện chữ chú thích previz của các khối bối cảnh
- **Nâng lên / hạ xuống** — chọn vật, bấm **W** (Di chuyển) rồi **giữ Alt và kéo chuột lên/xuống**; hoặc gõ thẳng số vào ô **Độ cao** ở panel phải (vd `-6` để xuống đáy hố nhân sư)
- **Phím End** (hoặc nút **⤓ Thả xuống bề mặt**) — đặt vật xuống đúng mặt nền ngay bên dưới: đáy hố, mặt dốc, mặt bục, sàn phòng
- **Tách nhiều tầng** — tách khối bối cảnh ra bộ phận, chọn một bộ phận rồi **tách tiếp** thành từng mảnh, cứ thế cho tới khi không còn chia được. Vật nào còn từ 2 phần con trở lên thì panel phải hiện bảng **Tách tiếp**; dòng nào còn chia nhỏ được sẽ ghi số mảnh
- **Phím G** — gộp các vật đang chọn thành **một khối** (di chuyển/xoay/tỉ lệ/lưu như một vật); **Shift+G** — tách khối đang chọn ra lại
- Khi chọn nhiều vật (Shift+bấm), các thanh trượt Xoay / Độ cao / Tỉ lệ ở panel phải áp cho **cả nhóm**

> Tầm zoom được giới hạn theo cỡ cảnh: gần nhất 0.25 m (soi được bảng PET, chùm chà là),
> xa nhất vừa đủ ôm trọn set mà không bay ra ngoài vòm trời.

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

### 5.5b. Cú máy — xuất video tham chiếu

Tab **Camera** → mục **Cú máy**:

1. Xoay camera tới **góc đầu** → bấm **Đặt** ở dòng **A**. Tới **góc cuối** → **Đặt** ở dòng **B**. (Bấm bookmark theo timecode rồi Đặt cũng được.)
2. Chọn **Thời lượng** (giây), **Đường đi** (*Thẳng* = dolly/track/crane · *Vòng cung* = lượn quanh chủ thể), **Nhịp** (*Đều · Êm · Tăng tốc · Giảm tốc*), **fps** 24/25/30.
3. **▶ Xem thử** chạy ngay trong viewport. **⏺ Xuất video** ra file **.mp4** vào thư mục *Tải về*.

- Tiêu cự nội suy theo: A ở 24mm, B ở 85mm là ra một cú zoom kết hợp dolly.
- Đường bay (A xanh → B đỏ, chấm vàng mỗi giây) chỉ hiện khi đang mở tab Camera, không dính vào ảnh chụp hay video.
- Video đúng khung hình đang chọn (1.85, 2.39, 16:9, 9:16…), rộng tối đa 1920 px, và **đúng số giây** dù máy render chậm (dựng từng khung một).
- ↺ đưa camera về A hoặc B để chỉnh; ⇄ đảo chiều cú máy. Cú máy lưu cùng project.

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
- **Tư thế dựng sẵn:** Đứng · Ngồi ghế · Ngồi ghế máy bay (ngả lưng nhẹ, cẳng tay đặt lên tay vịn; nhân vật *Ngồi máy bay* trong kho sinh ra đúng độ cao để thả lên ghế máy bay) · Ngồi lái xe · Nằm · Ngồi xổm · Quỳ · Giơ tay · Chỉ tay · Chạy
- **Nhân vật chính ★ Pipo · Buro · Coppa · Pharaoh hà mã** cũng có khung xương: dùng chung dropdown Tư thế + các thanh gập khớp (thân/hông/gối/tay/khuỷu). Dáng đứng = đúng mẫu thiết kế; quỳ/xổm/chạy/nằm tự chạm sàn, ngồi ghế giữ độ cao để thả lên ghế. Gậy của hà mã đi theo bàn tay. Project cũ có sẵn các nhân vật này cũng tự có khớp khi mở lại
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

Đây là **phím mặc định**. Mọi phím đều đổi được theo ý bạn — xem [Tùy chỉnh phím tắt](#tùy-chỉnh-phím-tắt-tự-gán-phím) ngay bên dưới.

| Phím (mặc định) | Tác dụng |
|---|---|
| `Q` / `W` / `E` / `R` | Orbit / Di chuyển / Xoay / Tỉ lệ (W/E/R hiện gizmo trục X/Y/Z) |
| `X` | Trục gizmo: Thế giới ⇄ Cục bộ |
| `F` | Khung vừa vật đang chọn (không chọn = toàn cảnh; ở 4 góc: cả 3 ô trực giao cùng ôm vật) |
| `V` | Bật/tắt 4 góc nhìn |
| `M` | Bật/tắt monitor |
| `T` | Ẩn/hiện chữ previz |
| `` ` `` / `~` / `Tab` | Toàn màn hình (ẩn 2 panel) |
| `↑` `↓` `←` `→` | Đi tới / lùi / sang trái / sang phải (giữ `Shift` = bước nhỏ) |
| `PgUp` / `PgDn` | Lên cao / xuống thấp (giữ `Shift` = bước nhỏ) |
| `Ctrl+Z` | Hoàn tác |
| `Ctrl+Shift+Z` / `Ctrl+Y` | Làm lại |
| `Del` / `Backspace` | Xóa vật đang chọn |
| `G` / `Ctrl+G` | Gộp các vật đang chọn thành một khối |
| `Shift+G` | Tách khối đang chọn ra bộ phận |
| `End` | Thả vật xuống bề mặt bên dưới |
| `/` | Nhảy tới ô tìm kiếm model |
| `?` / `H` | Mở bảng hướng dẫn |
| `K` | Mở bảng **Tùy chỉnh phím tắt** |
| `Esc` *(cố định)* | Lùi một bước: đóng bảng → thoát ô nhập → bỏ chọn |
| giữ `Ctrl` khi kéo trục *(cố định)* | Bắt bước 0.25 m · 15° · 0.1× |
| giữ `Alt` khi kéo `W` *(cố định)* | Nâng lên / hạ xuống |
| **Nháy đúp thanh trượt** | Đưa về mặc định |

### Tùy chỉnh phím tắt (tự gán phím)

Mở bảng bằng phím **`K`**, hoặc nút **Hướng dẫn (?)** → **⌨ Tùy chỉnh phím tắt**.

- **Đổi phím:** bấm vào phím đang gán (ví dụ `W`) → bảng chờ "bấm phím…" → bấm phím / tổ hợp mới (giữ `Ctrl`, `Alt`, `Shift` nếu muốn; trên Mac `Ctrl` = `⌘`). `Esc` để huỷ.
- **Thêm phím:** bấm **+** ở cuối dòng — mỗi thao tác có tối đa 3 phím.
- **Gỡ phím:** rê chuột lên phím rồi bấm **✕**. Thao tác không còn phím hiện "chưa gán".
- **↺** ở cuối dòng = đưa thao tác đó về phím mặc định; **↺ Tất cả về mặc định** ở chân bảng = đưa toàn bộ về như cũ.
- **Phím trùng:** gán một phím đang thuộc thao tác khác thì phím đó **tự chuyển** sang thao tác mới, bảng báo đã gỡ khỏi thao tác nào (dòng đó nháy màu cam).
- **Không gán được:** `Esc` và các phím trình duyệt giữ (`Ctrl+W/T/N`, `Ctrl+Tab`, `F5` / `Ctrl+R`, `F11`, `F12`, `Ctrl+L`, `Alt+F4`, phóng to/thu nhỏ trang `Ctrl` `+` / `−` / `0`).
- **Thao tác chưa có phím sẵn** để bạn tự gán: Chụp shot, Storyboard, Xuất `.json`, Mở bảng Project, Lưới sàn, Bật/tắt Bắt bước, Cửa sổ phụ (máy quay / 4 góc), Bố cục 2 / 3 màn hình, Đóng các cửa sổ phụ.
- Ô **Tìm** ở đầu bảng lọc theo tên thao tác hoặc tên phím (vd `xoay`, `chụp`, `Ctrl`).
- Phím đi camera (mặc định mũi tên, PgUp/PgDn) đổi sang phím khác vẫn giữ **Shift = bước nhỏ**. Giữ phím lâu thì chỉ đi camera và hoàn tác/làm lại lặp lại; các phím bật/tắt (4 góc, monitor, toàn màn hình…) không nhấp nháy.
- Đang gõ chữ trong ô nhập thì phím tắt không chạy. Vừa kéo thanh trượt xong thì phím chữ vẫn chạy ngay; mũi tên / PgUp / PgDn / Home / End lúc đó là của thanh trượt.
- Bộ phím **lưu trong trình duyệt** (mỗi trình duyệt / máy một bộ). Muốn mang sang máy khác: **⤓ Xuất file** → sang máy kia mở bảng → **⤒ Nhập file**.
- Nhãn phím trên các nút, tooltip, thông báo, nút trong Inspector và bảng Hướng dẫn **tự đổi theo** phím bạn gán. Phím gõ ở **cửa sổ phụ** (màn hình 2–3) cũng dùng đúng bộ phím đã đổi.

---

## 11. Quy trình gợi ý

1. **Thêm chủ thể** — bấm model cột trái, hoặc dùng AI dàn cảnh / dựng từ ảnh.
2. **Sắp đặt** — dùng Di chuyển / Xoay / Tỉ lệ (kéo trục gizmo X/Y/Z cho chính xác), bật **4 góc nhìn** (`V`) để canh từ trên xuống / chính diện / bên hông; chỉnh tư thế nhân vật trong Inspector.
3. **Đặt máy quay** — xoay camera, chọn tiêu cự / khẩu độ / cao độ / góc máy nhanh; canh bố cục bằng monitor + khung 1/3.
4. **Chụp shot** — lưu các khung ưng ý.
5. **Storyboard** — xuất ảnh có nhãn + depth/edge map + prompt, đưa cho AI tạo ảnh ra hình điện ảnh đúng góc.
6. **Lưu việc** — tạo Project (tự lưu) hoặc Xuất `.json` để sao lưu.

---

— *Jenny Pixel Studio · 3D Storyboard Studio · by Tran Duc Vien*
