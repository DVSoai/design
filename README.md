# Đinh Bộ Lĩnh Lv1 — vẽ mới toàn bộ theo cấu trúc khung gốc

[Tải ZIP mới](https://github.com/DVSoai/design/raw/main/dbl_lv1.zip) · [REPORT](REPORT.md) · [SHA256](dbl_lv1.zip.sha256)

32 mảnh có hình nhân vật được vẽ mới bằng công cụ tạo ảnh, qua 36 lần gọi. Không dùng lại các mảnh nhân vật bản trước. Ô 22 là canvas trống 4×4 như cấu trúc ban đầu.

Có đủ **30 khung × 3 biến thể × 2 hướng × 2 cỡ = 360 PNG**. Thư mục `parts/native/` trong ZIP giữ nguyên kích thước canvas/khung bao và tên số từng ảnh để thay trực tiếp, gồm 262/283; có thêm bản tỷ lệ 256/128. Ghép bằng bảng số gốc, không bù vị trí riêng hoặc thêm lớp tay cầm.

Đầu/thân/chân khung đứng có bao 83×76 / 82×43 / 58×31px; toàn người 87×131px. Các tư thế khác giữ kích thước riêng theo bảng gốc. Vũ khí ở trước thân; vùng đầu được bảo vệ để tránh che mặt.

## Xem ảnh mới

- [Tỷ lệ gốc minh họa bằng hình mới](preview/ty_le_goc.png)
- [Đủ 33 slot mảnh](preview/parts_33.png)
- [16 thân, cùng tỷ lệ](preview/tay_dong_bo.png)
- [Bốn dáng lộn mới](preview/lon_4.png)
- [Tay không — 30 khung](preview/tay_khong_30.png)
- [Kiếm — 30 khung](preview/kiem_30.png)
- [Cung — 30 khung](preview/cung_30.png)
- [Vũ khí phóng 2×](preview/vu_khi_zoom.png)
- [Tổng hợp hai hướng](preview/sheet_30_khung.png)
- [Chạy](preview/anim_chay.gif) · [Nhảy/lộn](preview/anim_nhay.gif)

Đã kiểm tra canvas, bao hình, tọa độ, ảnh lật, nguồn tạo ảnh và ZIP CRC; đã xem ảnh ghép để so dáng/khớp. **Chưa chạy thử trong client thực tế.** Khung bao trùng nhau không có nghĩa đường viền ảnh vẽ mới trùng từng pixel. REPORT có số lần tạo từng mảnh và output script nguyên văn. Mọi ảnh tham khảo bên ngoài đều không nằm trong ZIP hoặc repo kết quả.
