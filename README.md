# reel-doc-3d-digi — skill Claude Code tự edit video dọc (Reels / TikTok / Shorts), màu chữ theo logo thương hiệu

Bản tuỳ biến từ [claude-skill-edit-reel](https://github.com/tranbahuy1205-dotcom/claude-skill-edit-reel) (giấy phép MIT). Giữ nguyên toàn bộ tính năng của bản gốc, thêm **bộ màu thương hiệu tự chọn theo tên file video**.

## Màu chữ theo tên file

| Tên file video | Bộ màu | Chữ dùng màu gì |
|---|---|---|
| có **`DH`** (vd. `Reel DH 01.mp4`, `dh_02.mp4`) | `dh` | dải chuyển sắc của logo: tím than → xanh dương → xanh ngọc → xanh non → vàng → cam |
| có **`Digi`** (vd. `Duyen Digi 01.mp4`) | `digi` | màu logo **+ màu đỏ #E3202B** |
| không có hai chữ trên | `goc` | trắng – đen – vàng #FFC400 như bản gốc |

Có cả `DH` lẫn `Digi` thì dùng `digi`. Muốn ép bộ màu cho một video, thêm `THEME = "dh"` (hoặc `"digi"`, `"goc"`) vào `du_an.py`.

![Xem trước 3 bộ màu](mau-chu/_xem-truoc.png)

Chi tiết từng kiểu chữ:
- **Chữ mảnh** (`*`, Playfair nghiêng): tô dải màu logo, gạch chân dải màu logo.
- **Chữ dày** (`!`, Inter Black): chữ đen trên hộp dải màu logo. Video Digi xen kẽ hộp logo và **hộp đỏ chữ trắng**.
- **Chữ nhấn** (`^`, mới thêm): Inter Black không hộp, bật nảy. DH: dải màu logo; Digi: **đỏ**; gốc: vàng.
- **Chữ to sau đầu**: trắng / dải màu logo (Digi thêm đỏ) xen kẽ.
- **Khối 3D minh hoạ**: màu nhấn đổi sang vàng của logo #FAD016.

Mã màu nằm trong `scripts/mau_thuong_hieu.py`. Sửa ở đó rồi chạy `scripts/thu_mau_chu.py` để xem trước, không cần video.

## Tính năng giữ từ bản gốc

- **Cắt:** bỏ khoảng lặng, ậm ừ, câu vấp; câu nói nhiều lần thì giữ lần trôi chảy nhất. Tăng tốc nhẹ ×1,1–1,2.
- **Hình:** chỉnh màu, làm mịn da, tách phông bằng RobustVideoMatting. Nền xen kẽ: phông thật, nền tối, chữ to sau đầu.
- **Chữ:** hiện theo từng cụm, 2 font (Inter Tight + Playfair nghiêng).
- **Minh hoạ khối 3D:** thư viện 25+ mẫu, Claude tự vẽ thêm mẫu mới khi cần.
- **Cảnh quay / ảnh của bạn:** 8 kiểu đặt cảnh (toàn màn hình, chia đôi, thẻ 3D, khung điện thoại, polaroid, nhãn dán, bong bóng mặt, dồn cảnh).
- **Âm thanh:** hiệu ứng tự tổng hợp, nhạc nền −15 dB, cân âm −14 LUFS.
- **Xuất file:** 1080×1920, có bản nháp 720p.

## Cài đặt

Làm theo **[HUONG-DAN-CAI-DAT.md](HUONG-DAN-CAI-DAT.md)** (Windows, viết cho người không rành máy).

Cần có: Claude Code, Python 3.10–3.12, ffmpeg, RAM từ 16 GB.

## Dùng

1. Đặt tên file video theo quy ước ở trên (`DH` / `Digi`).
2. Kéo video quay dọc vào Claude Code và nói "edit video này". Claude báo bộ màu đã chọn.
3. Claude dựng bản nháp 720p, bạn duyệt xong thì ra bản chính 1080×1920.

## Giấy phép

- Mã: **MIT** (xem [LICENSE](LICENSE)), giữ nguyên ghi công tác giả bản gốc.
- Phần bên thứ ba tải riêng khi cài: font Inter Tight, Playfair Display (SIL OFL); mô hình RobustVideoMatting (GPL-3.0); rembg / u2net.
- Skill **không kèm nhạc**. Nhạc nền là của bạn, tự chịu trách nhiệm bản quyền.
