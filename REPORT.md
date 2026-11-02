# Đinh Bộ Lĩnh Lv1 — cung đối xứng, kiếm 200px và mép cổ áo

Mốc đầu vào: `760fdd9b849acaa3999bdf2f3df0f254f2830ba3`. Không dùng Git để lấy nguồn hay đổi phiên bản trong quá trình sửa; Git chỉ dùng để đẩy kết quả. Chỉ đọc hai thư mục nguồn đã được chỉ định để tham khảo hình và bảng số. Gói không chứa ảnh, mã hoặc tên sản phẩm tham khảo.

**Bảo toàn: 284 PNG đối chiếu SHA256, 0 thay đổi.** Toàn bộ 33 mảnh nhân vật (raw, mặt nạ, hai cỡ: 132 file), 120 khung tay không và 32 khung lộn của các biến thể còn lại giữ nguyên từng byte. Màu, nét, tỷ lệ và bốn kiểu lộn không vẽ lại. Các PNG lộn của tay không đã nằm trong nhóm 120, không đếm trùng.

## Vũ khí và cách ghép

- Kiếm: chiều dài toàn bộ theo trục, gồm đốc, **200.109px**, chia chiều cao chuẩn 256px = **0.78168**. Bao alpha >127: **176×101px**. Nén theo trục quanh chuôi, giữ độ rộng vuông góc lưỡi; lưỡi vẫn to bản. Không nhầm chiều rộng bao với chiều dài chéo của kiếm.

- Cung: bao **170×258px**, chuẩn quy đổi 170.015×257.954px. Hai cánh cong đều có chiều dài bằng nhau **175.167px/cánh**, tay cầm tại đúng giữa cung; hai đầu uốn ngược nhẹ. Dây màu kem đậm, dày **3.2px** ở cỡ 256. Script kiểm tra lại độc lập độ dài hai cánh và điểm giữa từ đường nét SVG xuất.

- Tọa độ cơ sở: `x=cx+(dx+pdx)*4*256/131`, `y=cy+(-dy+pdy)*4*256/131`, gốc khung `(320,444)`. Khung 12 dùng ô vũ khí `[1,-9,49]`; khung 21 dùng `[1,-10,46]`. Độ lệch hai loại vũ khí lần lượt `[-4,27]` và `[-10,9]`. Không xoay vũ khí khi ghép.

- Ngoại lệ theo yêu cầu mới: kiếm 12/21 và nắm tay được đưa lên ngực, tại `[151,133]` trong tọa độ thân (phải cổ 23px, dưới cổ 29px). Khung 12 dịch **(-62.325,-66.307)px**, khung 21 dịch **(-62.325,-74.123)px** so với vị trí bảng số. Không ghi nhầm hai khung này là giữ nguyên tọa độ gốc. Tay còn lại giơ lên được giữ từ thân gốc.

- Thứ tự: chân/thân → vũ khí → ngón tay. Với cung, lớp đầu gốc được đặt trên cung; toàn bộ pixel đầu đục đối chiếu chính xác với ảnh gốc ở mọi khung có cung, nên cánh cung/dây không phủ lên mặt. Cung đứng 00/01 có đáy y=427/419, chân y=452/444.

- Vũ khí chỉ hiện 00–07,12,21. Có đủ 30 khung × 3 biến thể × 2 hướng × 2 cỡ = **360 PNG**; các khung không được mang vũ khí đối chiếu pixel với tay không.

## Mép cổ áo và lớp tay cầm

Không sửa mảnh thân gốc. Tách lại alpha các lớp tay cầm đã tạo bằng công cụ ảnh: loại dấu màu, chuôi tạm và mẩu áo lọt vào lớp tay; lấy vùng da nắm tay liên thông cùng viền mực thay cho mặt nạ tròn chứa cả cổ áo. Vùng cổ áo được phục hồi trực tiếp từ raster gốc, tránh ghép các đốm tròn nhỏ tạo răng cưa. Script xác nhận các pixel vùng cổ được bảo vệ khớp chính xác. Đã xem tờ phóng to các khung 00,03,07,12,21 cho cả kiếm và cung.

Kiếm 12/21 tái sử dụng ảnh tay cầm đã tạo `kiem_02`, đăng ký ở ngực; các lớp còn lại dùng ảnh tay cầm đã có cùng khóa. Không tạo hình người bằng SVG, vector hoặc hình khối. Các biến đổi/mặt nạ chỉ xử lý raster ảnh đã tạo, không vẽ RGB cơ thể mới.

## Số đo từng khung có vũ khí

Góc tính từ +x, y hướng xuống: kiếm từ chuôi về mũi; cung từ đầu dưới lên đầu trên. Góc/bao được đo trên **asset đầy đủ trước che khuất**, rồi kiểm tra riêng pixel vũ khí còn nhìn thấy trong ảnh ghép và pixel đầu. Không đo sai trục vì đầu che mất một phần cung. Bao dùng alpha >127. Sai lệch tay–chuôi tính cả làm tròn độc lập gốc hai lớp; cỡ 128 ghi theo hệ tọa độ thu nhỏ. Tỷ lệ kiếm dùng chiều cao chuẩn 256/128px, không dùng chiều cao bao cả vũ khí hay dáng đang nhảy.

Có **80 phép kiểm**, 0 lỗi. Bảng dưới ghi cả hai cỡ cho từng hướng. Đầy đủ tọa độ, độ dịch và tỷ lệ khớp pixel nằm ở `tools/weapon_audit.json`.

| Khung | Loại | Hướng | Góc 256 / 128 (°) | Góc hướng dẫn (°) | Bao 256 / 128 (px) | Dài kiếm / cao người 256 / 128 | Lệch tay–chuôi 256 / 128 (px) | Tay bọc chuôi |
|---|---|---|---:|---:|---|---:|---:|---|
| 00 | kiem | phai | 153.711 / 153.869 | 152.182 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.661 / 0.330 | Có |
| 00 | kiem | trai | 26.289 / 26.131 | 27.818 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.661 / 0.330 | Có |
| 01 | kiem | phai | 153.711 / 153.869 | 152.182 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.661 / 0.330 | Có |
| 01 | kiem | trai | 26.289 / 26.131 | 27.818 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.661 / 0.330 | Có |
| 02 | kiem | phai | 153.711 / 153.869 | 152.182 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.299 / 0.150 | Có |
| 02 | kiem | trai | 26.289 / 26.131 | 27.818 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.299 / 0.150 | Có |
| 03 | kiem | phai | 153.711 / 153.869 | 152.182 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.285 / 0.143 | Có |
| 03 | kiem | trai | 26.289 / 26.131 | 27.818 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.285 / 0.143 | Có |
| 04 | kiem | phai | 153.711 / 153.869 | 152.182 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.597 / 0.299 | Có |
| 04 | kiem | trai | 26.289 / 26.131 | 27.818 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.597 / 0.299 | Có |
| 05 | kiem | phai | 153.711 / 153.869 | 152.182 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.295 / 0.147 | Có |
| 05 | kiem | trai | 26.289 / 26.131 | 27.818 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.295 / 0.147 | Có |
| 06 | kiem | phai | 153.711 / 153.869 | 152.182 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.597 / 0.299 | Có |
| 06 | kiem | trai | 26.289 / 26.131 | 27.818 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.597 / 0.299 | Có |
| 07 | kiem | phai | 153.711 / 153.869 | 152.182 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.410 / 0.205 | Có |
| 07 | kiem | trai | 26.289 / 26.131 | 27.818 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.410 / 0.205 | Có |
| 12 | kiem | phai | 153.711 / 153.869 | 152.182 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.540 / 0.270 | Có |
| 12 | kiem | trai | 26.289 / 26.131 | 27.818 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.540 / 0.270 | Có |
| 21 | kiem | phai | 153.711 / 153.869 | 152.182 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.920 / 0.460 | Có |
| 21 | kiem | trai | 26.289 / 26.131 | 27.818 | 176×101 / 89×50 | 0.7817 / 0.7840 | 0.920 / 0.460 | Có |
| 00 | cung | phai | -64.314 / -64.230 | -63.182 | 170×258 / 85×129 | — | 0.490 / 0.245 | Có |
| 00 | cung | trai | -115.686 / -115.770 | -116.818 | 170×258 / 85×129 | — | 0.490 / 0.245 | Có |
| 01 | cung | phai | -64.314 / -64.230 | -63.182 | 170×258 / 85×129 | — | 0.490 / 0.245 | Có |
| 01 | cung | trai | -115.686 / -115.770 | -116.818 | 170×258 / 85×129 | — | 0.490 / 0.245 | Có |
| 02 | cung | phai | -64.314 / -64.230 | -63.182 | 170×258 / 85×129 | — | 0.551 / 0.275 | Có |
| 02 | cung | trai | -115.686 / -115.770 | -116.818 | 170×258 / 85×129 | — | 0.551 / 0.275 | Có |
| 03 | cung | phai | -64.314 / -64.230 | -63.182 | 170×258 / 85×129 | — | 0.201 / 0.100 | Có |
| 03 | cung | trai | -115.686 / -115.770 | -116.818 | 170×258 / 85×129 | — | 0.201 / 0.100 | Có |
| 04 | cung | phai | -64.314 / -64.230 | -63.182 | 170×258 / 85×129 | — | 0.436 / 0.218 | Có |
| 04 | cung | trai | -115.686 / -115.770 | -116.818 | 170×258 / 85×129 | — | 0.436 / 0.218 | Có |
| 05 | cung | phai | -64.314 / -64.230 | -63.182 | 170×258 / 85×129 | — | 0.437 / 0.219 | Có |
| 05 | cung | trai | -115.686 / -115.770 | -116.818 | 170×258 / 85×129 | — | 0.437 / 0.219 | Có |
| 06 | cung | phai | -64.314 / -64.230 | -63.182 | 170×258 / 85×129 | — | 0.436 / 0.218 | Có |
| 06 | cung | trai | -115.686 / -115.770 | -116.818 | 170×258 / 85×129 | — | 0.436 / 0.218 | Có |
| 07 | cung | phai | -64.314 / -64.230 | -63.182 | 170×258 / 85×129 | — | 0.669 / 0.335 | Có |
| 07 | cung | trai | -115.686 / -115.770 | -116.818 | 170×258 / 85×129 | — | 0.669 / 0.335 | Có |
| 12 | cung | phai | -64.314 / -64.230 | -63.182 | 170×258 / 85×129 | — | 0.992 / 0.496 | Có |
| 12 | cung | trai | -115.686 / -115.770 | -116.818 | 170×258 / 85×129 | — | 0.992 / 0.496 | Có |
| 21 | cung | phai | -64.314 / -64.230 | -63.182 | 170×258 / 85×129 | — | 0.216 / 0.108 | Có |
| 21 | cung | trai | -115.686 / -115.770 | -116.818 | 170×258 / 85×129 | — | 0.216 / 0.108 | Có |

## Tờ kiểm 16 thân

`preview/tay_dong_bo.png`: đủ thân **5–12,14–21**, dùng cùng vùng cắt và tỷ lệ 1.6×, không phóng từng thân theo kích thước riêng. Không cắt mất tay cao của thân 12/20. Số dưới ảnh là số đo ở cỡ nguồn 256px; diện tích da ghi theo dáng. `preview/vu_khi_zoom.png`: 00,03,07,12,21 × kiếm/cung, cùng vùng cắt, phóng đúng 2×.

Các số đo tay được giữ nguyên từ bản đầu vào. Ngưỡng ±12% áp cho độ dày trung bình hai bắp tay đo được theo lựa chọn đã chốt; diện tích da không dùng để loại dáng. **Thân 16 có giữa bắp tay bị che: N/A, không coi là phép đo đạt.** Đây là giới hạn đã có, không vẽ lại mảnh được yêu cầu giữ nguyên.

| Thân | Hai bên (px) | Trung bình (px) | Lệch thân 8 (%) | Diện tích da (px²) | Kết quả |
|---|---:|---:|---:|---:|---|
| 5 | 21.83 / 11.00 | 16.42 | -6.86 | 2764 | Đạt |
| 6 | 20.67 / 15.83 | 18.25 | +3.55 | 2212 | Đạt |
| 7 | 19.42 / 12.92 | 16.17 | -8.27 | 2546 | Đạt |
| 8 | 18.42 / 16.83 | 17.62 | +0.00 | 2828 | Đạt |
| 9 | 18.75 / 13.42 | 16.08 | -8.75 | 2593 | Đạt |
| 10 | 18.50 / 17.33 | 17.92 | +1.65 | 1994 | Đạt |
| 11 | 21.17 / 15.42 | 18.29 | +3.78 | 2321 | Đạt |
| 12 | 21.17 / 18.08 | 19.62 | +11.35 | 3100 | Đạt |
| 14 | 14.25 / 21.33 | 17.79 | +0.95 | 2363 | Đạt |
| 15 | 23.08 / 12.42 | 17.75 | +0.71 | 1977 | Đạt |
| 16 | 9.08 / 13.42 | N/A | N/A | 2203 | N/A — che khuất |
| 17 | 13.92 / 17.50 | 15.71 | -10.87 | 1716 | Đạt |
| 18 | 18.50 / 15.92 | 17.21 | -2.36 | 2730 | Đạt |
| 19 | 18.50 / 15.75 | 17.12 | -2.84 | 2442 | Đạt |
| 20 | 18.75 / 19.25 | 19.00 | +7.80 | 3008 | Đạt |
| 21 | 17.42 / 15.00 | 16.21 | -8.04 | 2590 | Đạt |

## Tự soát 30 khung

Có/Không theo kiểm tra pixel/neo và phép đo đã mô tả; cột tay ghi số đo, riêng khung lộn giữ nguyên và thân 16 ghi N/A. Bảng này không thay thế tờ phóng to để duyệt hình.

| Khung | Đầu–cổ | Cỡ áo | Da | Hai chân | Dáng tay | Tay cầm | Hiện vũ khí | Tay cùng cỡ: TB px / diện tích px² |
|---|---|---|---|---|---|---|---|---|
| 00 | Có | Có | Có | Có | Có | Có | Có | 16.42 / 2764 |
| 01 | Có | Có | Có | Có | Có | Có | Có | 16.42 / 2764 |
| 02 | Có | Có | Có | Có | Có | Có | Có | 18.25 / 2212 |
| 03 | Có | Có | Có | Có | Có | Có | Có | 16.17 / 2546 |
| 04 | Có | Có | Có | Có | Có | Có | Có | 17.62 / 2828 |
| 05 | Có | Có | Có | Có | Có | Có | Có | 16.08 / 2593 |
| 06 | Có | Có | Có | Có | Có | Có | Có | 17.92 / 1994 |
| 07 | Có | Có | Có | Có | Có | Có | Có | 18.29 / 2321 |
| 08 | Có | Có | Có | Có | Có | Có | Có | Lộn giữ nguyên |
| 09 | Có | Có | Có | Có | Có | Có | Có | Lộn giữ nguyên |
| 10 | Có | Có | Có | Có | Có | Có | Có | Lộn giữ nguyên |
| 11 | Có | Có | Có | Có | Có | Có | Có | Lộn giữ nguyên |
| 12 | Có | Có | Có | Có | Có | Có | Có | 19.62 / 3100 |
| 13 | Có | Có | Có | Có | Có | Có | Có | 17.79 / 2363 |
| 14 | Có | Có | Có | Có | Có | Có | Có | 17.75 / 1977 |
| 15 | Có | Có | Có | Có | Có | Có | Có | N/A (che khuất) / 2203 |
| 16 | Có | Có | Có | Có | Có | Có | Có | 15.71 / 1716 |
| 17 | Có | Có | Có | Có | Có | Có | Có | 17.21 / 2730 |
| 18 | Có | Có | Có | Có | Có | Có | Có | 17.12 / 2442 |
| 19 | Có | Có | Có | Có | Có | Có | Có | 19.00 / 3008 |
| 20 | Có | Có | Có | Có | Có | Có | Có | 16.21 / 2590 |
| 21 | Có | Có | Có | Có | Có | Có | Có | 19.62 / 3100 |
| 22 | Có | Có | Có | Có | Có | Có | Có | 17.79 / 2363 |
| 23 | Có | Có | Có | Có | Có | Có | Có | 17.75 / 1977 |
| 24 | Có | Có | Có | Có | Có | Có | Có | N/A (che khuất) / 2203 |
| 25 | Có | Có | Có | Có | Có | Có | Có | 15.71 / 1716 |
| 26 | Có | Có | Có | Có | Có | Có | Có | 17.21 / 2730 |
| 27 | Có | Có | Có | Có | Có | Có | Có | 17.12 / 2442 |
| 28 | Có | Có | Có | Có | Có | Có | Có | 19.00 / 3008 |
| 29 | Có | Có | Có | Có | Có | Có | Có | 16.21 / 2590 |

## Nguồn tạo ảnh và số lần gọi

**Lần sửa hiện tại: 0 lần gọi tạo ảnh mới**, vì yêu cầu giữ nguyên mọi mảnh nhân vật và tay đã đồng bộ. Mọi mảnh đều có nguồn ảnh và lịch sử gọi công cụ từ các bản trước; không có mảnh nhân vật dựng bằng mã. Có 18 nguồn tay cầm đã tạo trước đó, không tạo lại; việc tái sử dụng donor được ghi trong JSON mỗi lớp. Các prompt nguyên văn và log tạo ảnh trước đây vẫn giữ trong `prompts/` và `tools/logs/`.

| Mảnh | Tổng lần tạo ảnh đã ghi nhận | Lần sửa hiện tại |
|---|---:|---:|
| 01 | 1 | 0 — giữ nguyên |
| 02 | 1 | 0 — giữ nguyên |
| 03 | 1 | 0 — giữ nguyên |
| 04 | 1 | 0 — giữ nguyên |
| 05 | 2 | 0 — giữ nguyên |
| 06 | 1 | 0 — giữ nguyên |
| 07 | 1 | 0 — giữ nguyên |
| 08 | 1 | 0 — giữ nguyên |
| 09 | 1 | 0 — giữ nguyên |
| 10 | 2 | 0 — giữ nguyên |
| 11 | 1 | 0 — giữ nguyên |
| 12 | 2 | 0 — giữ nguyên |
| 14 | 2 | 0 — giữ nguyên |
| 15 | 3 | 0 — giữ nguyên |
| 16 | 1 | 0 — giữ nguyên |
| 17 | 2 | 0 — giữ nguyên |
| 18 | 2 | 0 — giữ nguyên |
| 19 | 2 | 0 — giữ nguyên |
| 20 | 1 | 0 — giữ nguyên |
| 21 | 2 | 0 — giữ nguyên |
| 22 | 1 | 0 — giữ nguyên |
| 23 | 1 | 0 — giữ nguyên |
| 24 | 1 | 0 — giữ nguyên |
| 25 | 1 | 0 — giữ nguyên |
| 26 | 1 | 0 — giữ nguyên |
| 27 | 1 | 0 — giữ nguyên |
| 28 | 1 | 0 — giữ nguyên |
| 29 | 1 | 0 — giữ nguyên |
| 30 | 1 | 0 — giữ nguyên |
| 31 | 1 | 0 — giữ nguyên |
| 32 | 1 | 0 — giữ nguyên |
| 33 | 1 | 0 — giữ nguyên |
| 35 | 1 | 0 — giữ nguyên |

## Output nguyên văn các script trong lần sửa này

Các log cũ giữ làm lịch sử; các log có tiền tố `revision3_` dưới đây là kết quả hiện tại.

### revision3_weapons.txt
```text
WEAPON kiem: bbox=[176, 101]; angle=153.711; reference=152.182; delta=1.529; rotation=0
WEAPON cung: bbox=[170, 258]; angle=-64.314; reference=-63.182; delta=1.132; rotation=0
SWORD axial length=200.109px; height=256px; ratio=0.78168; thickness retained.
BOW equal limbs=175.167px / 175.167px; grip arc fraction=0.5; string=3.2px.
```

### revision3_grips.txt
```text
GRIP kiem_00: side=right; fingers_wrap=True; raster_displacement=[17.07095190724968, -6.757933289237627]; image_calls=1
GRIP kiem_02: side=right; fingers_wrap=True; raster_displacement=[8.40456197041226, -15.604159490696816]; image_calls=2
GRIP kiem_03: side=right; fingers_wrap=True; raster_displacement=[-6.735449946110322, 9.27240572702081]; image_calls=1
GRIP kiem_04: side=right; fingers_wrap=True; raster_displacement=[-35.195360118403926, -13.60646764270254]; image_calls=1
GRIP kiem_05: side=right; fingers_wrap=True; raster_displacement=[-7.10473131604877, -10.420988043979975]; image_calls=1
GRIP kiem_06: side=right; fingers_wrap=True; raster_displacement=[2.1178251733473132, -6.687700596878301]; image_calls=1
GRIP kiem_07: side=right; fingers_wrap=True; raster_displacement=[0.9125768436855992, -5.995755668410311]; image_calls=1
GRIP kiem_12: side=right; fingers_wrap=True; raster_displacement=[8.613816556491656, 4.0739476180818315]; image_calls=2
GRIP kiem_21: side=right; fingers_wrap=True; raster_displacement=[8.613816556491656, 4.0739476180818315]; image_calls=2
GRIP cung_00: side=right; fingers_wrap=True; raster_displacement=[-13.18086960241564, 8.940756646946596]; image_calls=1
GRIP cung_02: side=left; fingers_wrap=True; raster_displacement=[2.766341602932073, -16.976070468171173]; image_calls=1
GRIP cung_03: side=left; fingers_wrap=True; raster_displacement=[36.059037797383354, 9.907416658416963]; image_calls=1
GRIP cung_04: side=left; fingers_wrap=True; raster_displacement=[2.776701966948849, 1.9440031627584347]; image_calls=1
GRIP cung_05: side=left; fingers_wrap=True; raster_displacement=[4.361705436734539, 0.9953832361752291]; image_calls=1
GRIP cung_06: side=left; fingers_wrap=True; raster_displacement=[7.670673263140117, 4.0490829340442644]; image_calls=1
GRIP cung_07: side=right; fingers_wrap=True; raster_displacement=[-31.14013222772485, 1.5443575744563702]; image_calls=1
GRIP cung_12: side=right; fingers_wrap=True; raster_displacement=[-12.899742786270224, 56.55778328333176]; image_calls=1
GRIP cung_21: side=right; fingers_wrap=True; raster_displacement=[-9.162981297033951, 50.28077990136745]; image_calls=1
GRIP LAYERS: original unarmed character pieces left unchanged; frame 01 reuses frame 00 relative pose. Colored markers removed.
```

### revision3_assemble.txt
```text
ASSEMBLE: 30 frames × 3 variants × 2 directions × 2 scales = 360 transparent frame PNGs.
Weapons visible ONLY at frames 0–7, 12, 21; all other armed-variant frames are identical to unarmed.
Roll frames 8–11 use four independently image-generated full-body sprites; ZERO character rotation applied.
Runtime weapon rotation: ZERO. Table positions retained except explicit chest registration for sword 12/21.
Layer order: legs/body, weapon ABOVE torso, extracted raster fingers; bow under original head to protect face.
Standing frame alpha height: 256px; standing display exports: exactly 256px and 128px tall.
Clipped frame count: 0
Saved both-direction sheet, 3 preview boards, run GIF (5 frames), jump GIF (8 frames).
```

### revision3_previews.txt
```text
PREVIEW: tay_dong_bo.png = all 16 torsos 5–12,14–21; common crop / 1.6x scale; per-side thickness, mean, delta and skin area.
PREVIEW: vu_khi_zoom.png = frames 00,03,07,12,21 × sword/bow; common crop / exactly 2x scale.
```

### revision3_preservation.txt
```text
PRESERVATION: 284 protected PNG files compared to baseline; unauthorized pixel/file changes=0.
Baseline 760fdd9: ALL 33 character parts (raw, masks, 256/128), ALL unarmed exports and ALL roll exports remain byte-identical.
```

### revision3_audit.txt
```text
BOW SVG AUDIT: limbs=175.1561/175.1561px; difference=0.00006px; grip-midpoint error=0.00005px; string=3.2px.
STANDING 00: bow_bottom=427; feet_bottom=452; PASS=True
STANDING 01: bow_bottom=419; feet_bottom=444; PASS=True
WEAPON AUDIT: 80 checks; complete asset geometry + final rendered pixels.
kiem 00: angle=153.711; reference=152.182; bbox=[176, 101]; axial_length=200.1091650348241; ratio=0.7816764259172816; hand-hilt=0.661px; wrap=True; collar=True; head_match=None; shift=[0.0, 0.0]; PASS=True
kiem 01: angle=153.711; reference=152.182; bbox=[176, 101]; axial_length=200.1091650348241; ratio=0.7816764259172816; hand-hilt=0.661px; wrap=True; collar=True; head_match=None; shift=[0.0, 0.0]; PASS=True
kiem 02: angle=153.711; reference=152.182; bbox=[176, 101]; axial_length=200.1091650348241; ratio=0.7816764259172816; hand-hilt=0.299px; wrap=True; collar=True; head_match=None; shift=[0.0, 0.0]; PASS=True
kiem 03: angle=153.711; reference=152.182; bbox=[176, 101]; axial_length=200.1091650348241; ratio=0.7816764259172816; hand-hilt=0.285px; wrap=True; collar=True; head_match=None; shift=[0.0, 0.0]; PASS=True
kiem 04: angle=153.711; reference=152.182; bbox=[176, 101]; axial_length=200.1091650348241; ratio=0.7816764259172816; hand-hilt=0.597px; wrap=True; collar=True; head_match=None; shift=[0.0, 0.0]; PASS=True
kiem 05: angle=153.711; reference=152.182; bbox=[176, 101]; axial_length=200.1091650348241; ratio=0.7816764259172816; hand-hilt=0.295px; wrap=True; collar=True; head_match=None; shift=[0.0, 0.0]; PASS=True
kiem 06: angle=153.711; reference=152.182; bbox=[176, 101]; axial_length=200.1091650348241; ratio=0.7816764259172816; hand-hilt=0.597px; wrap=True; collar=True; head_match=None; shift=[0.0, 0.0]; PASS=True
kiem 07: angle=153.711; reference=152.182; bbox=[176, 101]; axial_length=200.1091650348241; ratio=0.7816764259172816; hand-hilt=0.410px; wrap=True; collar=True; head_match=None; shift=[0.0, 0.0]; PASS=True
kiem 12: angle=153.711; reference=152.182; bbox=[176, 101]; axial_length=200.1091650348241; ratio=0.7816764259172816; hand-hilt=0.540px; wrap=True; collar=True; head_match=None; shift=[-62.32509655895879, -66.30662571564883]; PASS=True
kiem 21: angle=153.711; reference=152.182; bbox=[176, 101]; axial_length=200.1091650348241; ratio=0.7816764259172816; hand-hilt=0.920px; wrap=True; collar=True; head_match=None; shift=[-62.325096558958734, -74.12341960877859]; PASS=True
cung 00: angle=-64.314; reference=-63.182; bbox=[170, 258]; axial_length=None; ratio=None; hand-hilt=0.490px; wrap=True; collar=True; head_match=1.0; shift=[0.0, 0.0]; PASS=True
cung 01: angle=-64.314; reference=-63.182; bbox=[170, 258]; axial_length=None; ratio=None; hand-hilt=0.490px; wrap=True; collar=True; head_match=1.0; shift=[0.0, 5.684341886080802e-14]; PASS=True
cung 02: angle=-64.314; reference=-63.182; bbox=[170, 258]; axial_length=None; ratio=None; hand-hilt=0.551px; wrap=True; collar=True; head_match=1.0; shift=[0.0, 0.0]; PASS=True
cung 03: angle=-64.314; reference=-63.182; bbox=[170, 258]; axial_length=None; ratio=None; hand-hilt=0.201px; wrap=True; collar=True; head_match=1.0; shift=[0.0, 0.0]; PASS=True
cung 04: angle=-64.314; reference=-63.182; bbox=[170, 258]; axial_length=None; ratio=None; hand-hilt=0.436px; wrap=True; collar=True; head_match=1.0; shift=[0.0, 0.0]; PASS=True
cung 05: angle=-64.314; reference=-63.182; bbox=[170, 258]; axial_length=None; ratio=None; hand-hilt=0.437px; wrap=True; collar=True; head_match=1.0; shift=[0.0, 0.0]; PASS=True
cung 06: angle=-64.314; reference=-63.182; bbox=[170, 258]; axial_length=None; ratio=None; hand-hilt=0.436px; wrap=True; collar=True; head_match=1.0; shift=[0.0, 0.0]; PASS=True
cung 07: angle=-64.314; reference=-63.182; bbox=[170, 258]; axial_length=None; ratio=None; hand-hilt=0.669px; wrap=True; collar=True; head_match=1.0; shift=[0.0, 0.0]; PASS=True
cung 12: angle=-64.314; reference=-63.182; bbox=[170, 258]; axial_length=None; ratio=None; hand-hilt=0.992px; wrap=True; collar=True; head_match=1.0; shift=[0.0, 0.0]; PASS=True
cung 21: angle=-64.314; reference=-63.182; bbox=[170, 258]; axial_length=None; ratio=None; hand-hilt=0.216px; wrap=True; collar=True; head_match=1.0; shift=[0.0, 5.684341886080802e-14]; PASS=True
WEAPON AUDIT FAILURES: 0
```

### revision3_validate.txt
```text
VALIDATE: 33 image-generated character parts; ZERO parts with 0 image-tool calls.
Inherited image-tool invocations (no new character generation in this revision): torso=7, additional grip layers=20.
Character SVG count: 0. Weapon SVG count: 2. Four roll source images have different SHA256 hashes.
Frame PNG count: 360; both directions and scales present. GIF frame counts: 5 / 8.
Weapon visibility: only 00–07, 12, 21; forbidden frames compared byte-for-byte to unarmed pixels.
frame neck size skin feet arms grip visibility bounds mirror image_tool | biceps_mean_px skin_area_px2 arm_size_result
00 YES YES YES YES YES YES YES YES YES YES | 16.416666666666664 2764 PASS
01 YES YES YES YES YES YES YES YES YES YES | 16.416666666666664 2764 PASS
02 YES YES YES YES YES YES YES YES YES YES | 18.25 2212 PASS
03 YES YES YES YES YES YES YES YES YES YES | 16.166666666666668 2546 PASS
04 YES YES YES YES YES YES YES YES YES YES | 17.625 2828 PASS
05 YES YES YES YES YES YES YES YES YES YES | 16.083333333333332 2593 PASS
06 YES YES YES YES YES YES YES YES YES YES | 17.916666666666664 1994 PASS
07 YES YES YES YES YES YES YES YES YES YES | 18.291666666666668 2321 PASS
08 YES YES YES YES YES YES YES YES YES YES | ROLL_PRESERVED
09 YES YES YES YES YES YES YES YES YES YES | ROLL_PRESERVED
10 YES YES YES YES YES YES YES YES YES YES | ROLL_PRESERVED
11 YES YES YES YES YES YES YES YES YES YES | ROLL_PRESERVED
12 YES YES YES YES YES YES YES YES YES YES | 19.625 3100 PASS
13 YES YES YES YES YES YES YES YES YES YES | 17.791666666666664 2363 PASS
14 YES YES YES YES YES YES YES YES YES YES | 17.75 1977 PASS
15 YES YES YES YES YES YES YES YES YES YES | None 2203 NOT_MEASURABLE_OCCLUDED
16 YES YES YES YES YES YES YES YES YES YES | 15.708333333333332 1716 PASS
17 YES YES YES YES YES YES YES YES YES YES | 17.208333333333332 2730 PASS
18 YES YES YES YES YES YES YES YES YES YES | 17.125 2442 PASS
19 YES YES YES YES YES YES YES YES YES YES | 19.0 3008 PASS
20 YES YES YES YES YES YES YES YES YES YES | 16.208333333333336 2590 PASS
21 YES YES YES YES YES YES YES YES YES YES | 19.625 3100 PASS
22 YES YES YES YES YES YES YES YES YES YES | 17.791666666666664 2363 PASS
23 YES YES YES YES YES YES YES YES YES YES | 17.75 1977 PASS
24 YES YES YES YES YES YES YES YES YES YES | None 2203 NOT_MEASURABLE_OCCLUDED
25 YES YES YES YES YES YES YES YES YES YES | 15.708333333333332 1716 PASS
26 YES YES YES YES YES YES YES YES YES YES | 17.208333333333332 2730 PASS
27 YES YES YES YES YES YES YES YES YES YES | 17.125 2442 PASS
28 YES YES YES YES YES YES YES YES YES YES | 19.0 3008 PASS
29 YES YES YES YES YES YES YES YES YES YES | 16.208333333333336 2590 PASS
ARM MIDPOINT NOT MEASURABLE: [16] (covered by forearm/wrist wrap; preserved original, not a passing thickness result).
FAILURES: 0
```

### revision3_package.txt
```text
PACKAGE: 786 files; 360 frame PNGs; 33 main character rasters; 18 image-generated grip sources; 2 weapon SVGs; ZIP CRC PASS.
Reference-image comparison boards excluded. One occluded biceps midpoint (torso 16) remains explicitly N/A in the report.
```
