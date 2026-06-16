# Jenny Pixel Studio — 3D Storyboard / Previz Studio

Công cụ dựng **storyboard 3D / previz** chạy hoàn toàn trong trình duyệt, đóng gói trong một file HTML duy nhất ([`jenny-pixel-studio.html`](jenny-pixel-studio.html)). Dùng [three.js](https://threejs.org/) (nạp từ CDN) để dàn cảnh model, camera, tư thế và chụp shot.

— *by Tran Duc Vien*

> 📖 **Hướng dẫn chi tiết từng chức năng** (kho model, máy quay, AI, API, storyboard…): [HUONG-DAN-CHUC-NANG.md](HUONG-DAN-CHUC-NANG.md)

## Tính năng

- **Không cần internet:** thư viện model, camera, tư thế, monitor, chụp shot.
- **Cần API key + mạng** (3 tính năng AI): dàn cảnh, dựng từ ảnh, tạo vật thể.
- Lưu project & API key trong `localStorage` của trình duyệt; xuất/nhập cảnh ra file `.json`.

## Cách mở app

Mở trực tiếp file `jenny-pixel-studio.html` bằng **Firefox** (cho phép lưu trữ offline), hoặc chạy qua localhost để dùng tốt trên Chrome:

```
python -m http.server 8080
```

rồi mở http://localhost:8080/jenny-pixel-studio.html

> Xem hướng dẫn chi tiết tại [HUONG-DAN-MO-APP.md](HUONG-DAN-MO-APP.md).

## API key

App **không** chứa API key sẵn. Khi cần dùng tính năng AI, người dùng tự nhập key qua nút trên thanh công cụ; key chỉ lưu cục bộ trong trình duyệt (`localStorage`).
