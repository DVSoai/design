# Đinh Bộ Lĩnh Lv1 — vẽ mới toàn bộ, dùng cấu trúc khung gốc
Theo yêu cầu mới, toàn bộ mảnh có hình nhân vật đã được tạo mới bằng công cụ ảnh; không giữ lại đầu/thân/chân/lộn từ bản trước. Giữ kích thước canvas, khung bao, số ảnh, bảng tư thế và độ lệch mảnh của cấu trúc gốc. Chỉ thay diện mạo, tóc, mặt và trang phục. Không dựng hình người bằng SVG/vector/code; hai vũ khí dùng SVG tự vẽ.
Có **32 mảnh nhân vật mới**, qua **36 lần gọi công cụ tạo ảnh**: 3 đầu, 16 thân, 9 chân và 4 dáng lộn. Mảnh 22 là ô điều khiển trong suốt 4×4, không có nhân vật để vẽ; ghi N/A thay vì tạo thêm chân làm sai cấu trúc. `tools/freshness.json` xác nhận 32 ảnh raw đều khác bản trước, không tái sử dụng ảnh nhân vật cũ.
## Đã xem và đo những gì
Đã mở trực tiếp ảnh mảnh gốc, phóng lớn để xem dáng, và ghép các mảnh tham khảo bằng bảng số để so với hình mới ở cùng tỷ lệ. Sau đó đối chiếu thêm tờ mảnh/tờ ghép người dùng gửi. **Chưa chạy client để chụp màn hình thực tế.** Các tờ đối chiếu có hình bên ngoài chỉ nằm trong thư mục tạm, không đưa vào gói hoặc repo kết quả.
Kích thước khung đứng, đo phần có alpha: đầu **83×76**, thân gồm tay **82×43**, chân **58×31**, toàn người **87×131 px**. Đầu chiếm **58.02%** chiều cao, cao **1.767 lần khung bao thân gồm tay**. Chồng đầu–thân **8px**, thân–chân **11px**: `76+43+31−8−11=131`. Không dùng lại tỷ lệ tự đặt 1.3 hoặc ép mọi áo về một chiều cao chung.
`parts/native/` giữ đúng cỡ gốc của từng ảnh, dùng được như ảnh thay thế theo số; có cả tên vũ khí 262/283. Hai bản 256/128 dùng chung hệ số 256/131 và 128/131. Khung đứng xuất cao đúng 256/128px; các tư thế khác giữ biến thiên chiều cao của bảng gốc, không kéo tất cả về 256px.
## Ghép và vũ khí
Ghép trực tiếp `x=cx+(dx+pdx)×4×S`, `y=cy+(−dy+pdy)×4×S`. **Không dịch khớp**, không thêm tay cầm, không xoay vũ khí và không bù riêng khung 12/21. Lật toàn khung để có hướng trái. Bốn mảnh lộn là bốn ảnh được tạo riêng, không xoay ảnh đứng.
Vũ khí nằm **trước thân** theo tờ ghép người dùng cung cấp. Để giữ mặt không bị che, phần vũ khí qua vùng đầu lấy lại pixel nhân vật tay không dưới mặt nạ đầu; không thay tọa độ vũ khí hay vẽ thêm người. Ở các khung được phép, kiếm/cung giữ nguyên slot và khung bao gốc. Ngoài 00–07,12,21, hai biến thể có vũ khí giống tay không từng pixel.
Kiếm native: canvas **104×64**, bao **102×60px**; cung native: canvas **108×136**, bao **87×132px**. Tỷ lệ rộng bao kiếm/chiều cao người là `102/131=0.7786`; đây không phải chiều dài chéo theo trục. Không tráo hai phép đo này. Không ép tay vào chuôi để tạo một cấu trúc cầm khác mẫu; sai lệch tay–chuôi ghi **N/A**, không ghi khoảng cách giả bằng 0.
## Phạm vi kiểm chứng
Script xác minh chính xác **canvas, khung bao từng mảnh, khung bao toàn bộ 30 tư thế ở cỡ native, tọa độ số, ảnh lật, nguồn tạo ảnh và quy tắc vũ khí**. Khung bao giống nhau không chứng minh đường viền cơ thể trùng từng pixel: đây là ảnh vẽ mới, không phải đổi màu trực tiếp ảnh gốc. Dáng tay/chân và khớp được so bằng ảnh ghép; chưa xác nhận trong client thực tế.
Đã xem toàn bộ 30 khung tay không, bốn mảnh lộn, và tờ phóng vũ khí 00,03,07,12,21 × kiếm/cung. Không thấy hở cổ/hông hoặc mất giày trong các ảnh đã soát. Tỷ lệ áo/tay của mỗi tư thế theo mảnh riêng; không dùng lại thao tác ép mọi tư thế về thân 8 của bản trước.
## Số lần tạo ảnh từng mảnh
| Mảnh | Canvas native | Bao phần có hình native | Lần gọi công cụ ảnh |
|---|---|---|---:|
| 01 | [113, 116] | [1, 0, 113, 116] | 1 |
| 02 | [116, 113] | [0, 1, 116, 113] | 1 |
| 03 | [113, 116] | [0, 0, 112, 116] | 1 |
| 04 | [116, 113] | [0, 0, 116, 112] | 1 |
| 05 | [84, 44] | [0, 0, 82, 43] | 3 |
| 06 | [60, 40] | [0, 0, 59, 38] | 1 |
| 07 | [84, 36] | [0, 0, 81, 36] | 1 |
| 08 | [60, 40] | [0, 0, 60, 38] | 1 |
| 09 | [76, 36] | [0, 0, 74, 36] | 2 |
| 10 | [60, 40] | [0, 0, 59, 38] | 1 |
| 11 | [72, 32] | [0, 0, 70, 31] | 1 |
| 12 | [104, 64] | [0, 0, 102, 63] | 1 |
| 14 | [72, 48] | [0, 2, 70, 48] | 1 |
| 15 | [88, 44] | [0, 0, 87, 43] | 1 |
| 16 | [52, 44] | [0, 0, 50, 42] | 2 |
| 17 | [76, 44] | [0, 0, 74, 43] | 1 |
| 18 | [100, 60] | [0, 1, 97, 60] | 1 |
| 19 | [100, 48] | [0, 3, 99, 48] | 1 |
| 20 | [60, 60] | [0, 0, 56, 60] | 1 |
| 21 | [96, 56] | [0, 1, 96, 55] | 1 |
| 22 | [4, 4] | N/A — trống | N/A — ô trống |
| 23 | [60, 32] | [0, 0, 58, 31] | 1 |
| 24 | [56, 48] | [0, 0, 53, 48] | 1 |
| 25 | [80, 40] | [0, 0, 78, 38] | 1 |
| 26 | [56, 40] | [0, 0, 54, 40] | 1 |
| 27 | [84, 40] | [0, 0, 82, 40] | 1 |
| 28 | [64, 40] | [0, 0, 63, 39] | 1 |
| 29 | [44, 56] | [0, 0, 43, 55] | 1 |
| 30 | [52, 56] | [0, 0, 51, 56] | 1 |
| 31 | [76, 36] | [0, 0, 74, 36] | 1 |
| 32 | [84, 76] | [0, 0, 83, 76] | 1 |
| 33 | [84, 84] | [0, 0, 83, 81] | 1 |
| 35 | [100, 84] | [6, 0, 97, 82] | 1 |
Thân 5: ba lần tạo, hai lần đầu bàn tay quá nhỏ; chọn lần ba. Thân 9: hai lần, bỏ bản lộ thêm tay sau. Thân 16: hai lần, bỏ bản tự dựng thêm thân đầy đủ, chọn mảnh tay/áo bị che như mẫu. Các mảnh còn lại một lần. Prompt nguyên văn từng lần thử có trong `prompts/` và log mỗi mảnh; raw là file trực tiếp từ công cụ, có SHA256.
## Đối chiếu 30 khung
| Khung | Bao toàn người native (px) | Lệch mép [trái,trên,phải,dưới] | Cổ/hông đã so | Hai giày đã so | Vũ khí đúng slot |
|---|---|---|---|---|---|
| 00 | [87, 131] | [0, 0, 0, 0] | Có | Có | Có |
| 01 | [87, 135] | [0, 0, 0, 0] | Có | Có | Có |
| 02 | [83, 136] | [0, 0, 0, 0] | Có | Có | Có |
| 03 | [87, 130] | [0, 0, 0, 0] | Có | Có | Có |
| 04 | [83, 140] | [0, 0, 0, 0] | Có | Có | Có |
| 05 | [87, 132] | [0, 0, 0, 0] | Có | Có | Có |
| 06 | [83, 135] | [0, 0, 0, 0] | Có | Có | Có |
| 07 | [87, 139] | [0, 0, 0, 0] | Có | Có | Có |
| 08 | [112, 116] | [0, 0, 0, 0] | Lộn riêng | Có | Có |
| 09 | [116, 112] | [0, 0, 0, 0] | Lộn riêng | Có | Có |
| 10 | [112, 116] | [0, 0, 0, 0] | Lộn riêng | Có | Có |
| 11 | [116, 112] | [0, 0, 0, 0] | Lộn riêng | Có | Có |
| 12 | [103, 144] | [0, 0, 0, 0] | Có | Có | Có |
| 13 | [91, 128] | [0, 0, 0, 0] | Có | Có | Có |
| 14 | [99, 136] | [0, 0, 0, 0] | Có | Có | Có |
| 15 | [95, 132] | [0, 0, 0, 0] | Có | Có | Có |
| 16 | [103, 132] | [0, 0, 0, 0] | Có | Có | Có |
| 17 | [99, 128] | [0, 0, 0, 0] | Có | Có | Có |
| 18 | [99, 132] | [0, 0, 0, 0] | Có | Có | Có |
| 19 | [91, 128] | [0, 0, 0, 0] | Có | Có | Có |
| 20 | [96, 132] | [0, 0, 0, 0] | Có | Có | Có |
| 21 | [109, 140] | [0, 0, 0, 0] | Có | Có | Có |
| 22 | [87, 148] | [0, 0, 0, 0] | Có | Có | Có |
| 23 | [87, 156] | [0, 0, 0, 0] | Có | Có | Có |
| 24 | [83, 152] | [0, 0, 0, 0] | Có | Có | Có |
| 25 | [103, 152] | [0, 0, 0, 0] | Có | Có | Có |
| 26 | [99, 147] | [0, 0, 0, 0] | Có | Có | Có |
| 27 | [99, 151] | [0, 0, 0, 0] | Có | Có | Có |
| 28 | [83, 147] | [0, 0, 0, 0] | Có | Có | Có |
| 29 | [96, 151] | [0, 0, 0, 0] | Có | Có | Có |
Bốn giá trị lệch mép lần lượt là trái, trên, phải, dưới; toàn bộ bằng 0px. Số này là kiểm tra hình học, không được diễn giải là đường nét ảnh mới giống hệt ảnh cũ.
## Vũ khí từng khung
| Khung | Loại | Góc 256 (°) | Góc hướng dẫn (°) | Lệch góc (°) | Bao 256 (px) | Lệch vị trí số (px) | Mặt giữ nguyên |
|---|---|---:|---:|---:|---|---:|---|
| 00 | kiem | 151.861 | 152.182 | 0.321 | [199, 117] | 0.000000 | Có |
| 01 | kiem | 151.861 | 152.182 | 0.321 | [199, 117] | 0.000000 | Có |
| 02 | kiem | 151.861 | 152.182 | 0.321 | [199, 117] | 0.000000 | Có |
| 03 | kiem | 151.861 | 152.182 | 0.321 | [199, 117] | 0.000000 | Có |
| 04 | kiem | 151.861 | 152.182 | 0.321 | [199, 117] | 0.000000 | Có |
| 05 | kiem | 151.861 | 152.182 | 0.321 | [199, 117] | 0.000000 | Có |
| 06 | kiem | 151.861 | 152.182 | 0.321 | [199, 117] | 0.000000 | Có |
| 07 | kiem | 151.861 | 152.182 | 0.321 | [199, 117] | 0.000000 | Có |
| 12 | kiem | 151.861 | 152.182 | 0.321 | [199, 117] | 0.000000 | Có |
| 21 | kiem | 151.861 | 152.182 | 0.321 | [199, 117] | 0.000000 | Có |
| 00 | cung | -64.023 | -63.182 | 0.841 | [170, 258] | 0.000000 | Có |
| 01 | cung | -64.023 | -63.182 | 0.841 | [170, 258] | 0.000000 | Có |
| 02 | cung | -64.023 | -63.182 | 0.841 | [170, 258] | 0.000000 | Có |
| 03 | cung | -64.023 | -63.182 | 0.841 | [170, 258] | 0.000000 | Có |
| 04 | cung | -64.023 | -63.182 | 0.841 | [170, 258] | 0.000000 | Có |
| 05 | cung | -64.023 | -63.182 | 0.841 | [170, 258] | 0.000000 | Có |
| 06 | cung | -64.023 | -63.182 | 0.841 | [170, 258] | 0.000000 | Có |
| 07 | cung | -64.023 | -63.182 | 0.841 | [170, 258] | 0.000000 | Có |
| 12 | cung | -64.023 | -63.182 | 0.841 | [170, 258] | 0.000000 | Có |
| 21 | cung | -64.023 | -63.182 | 0.841 | [170, 258] | 0.000000 | Có |
`tools/weapon_audit.json` có đủ 80 phép kiểm cho cả hai hướng và hai cỡ. Kiểm tra pixel vũ khí đục còn nhìn thấy so với đúng asset ở vị trí đó; không chỉ dựa vào tọa độ ghi trong báo cáo. Tổng lỗi máy kiểm: 0.
## Preview và gói tải
`preview/ty_le_goc.png`: hình mới kèm tỷ lệ đã đo. `preview/parts_33.png`: đủ 33 slot, gồm ô trống 22. `preview/tay_dong_bo.png`: đủ 16 thân tại cùng hệ số phóng. `preview/vu_khi_zoom.png`: 10 ô vũ khí phóng 2×. Có ba tờ 30 khung, tờ tổng hợp hai hướng và GIF chạy/nhảy. Tất cả preview trong gói chỉ chứa hình tự thiết kế.
## Output nguyên văn các script
### weapons.txt
```text
WEAPON kiem: native canvas=[104, 64]; occupied rectangle=[0, 3, 102, 63]; rotation=0; position correction=[0,0]; front layer.
WEAPON cung: native canvas=[108, 136]; occupied rectangle=[12, 3, 99, 135]; rotation=0; position correction=[0,0]; front layer.
```

### manifest.txt
```text
MANIFEST: 32 fresh character images; actual image calls=36; slot22=empty control, not an ungenerated character.
Native drop-in names: 01–35 as used by the numeric rig; 262/283 weapon aliases also supplied. Three new raw masters saved.
```

### normalize.txt
```text
PART 01: native_canvas=[113, 116]; native_bbox=[1, 0, 113, 116]; raw_crop=(110, 107, 1112, 1190); correction=[0,0]; NEW_IMAGE_RASTER
PART 02: native_canvas=[116, 113]; native_bbox=[0, 1, 116, 113]; raw_crop=(119, 101, 1165, 1145); correction=[0,0]; NEW_IMAGE_RASTER
PART 03: native_canvas=[113, 116]; native_bbox=[0, 0, 112, 116]; raw_crop=(72, 146, 1031, 1238); correction=[0,0]; NEW_IMAGE_RASTER
PART 04: native_canvas=[116, 113]; native_bbox=[0, 0, 116, 112]; raw_crop=(65, 74, 1113, 1157); correction=[0,0]; NEW_IMAGE_RASTER
PART 05: native_canvas=[84, 44]; native_bbox=[0, 0, 82, 43]; raw_crop=(1, 1, 1731, 908); correction=[0,0]; NEW_IMAGE_RASTER
PART 06: native_canvas=[60, 40]; native_bbox=[0, 0, 59, 38]; raw_crop=(139, 55, 1407, 882); correction=[0,0]; NEW_IMAGE_RASTER
PART 07: native_canvas=[84, 36]; native_bbox=[0, 0, 81, 36]; raw_crop=(55, 22, 1858, 769); correction=[0,0]; NEW_IMAGE_RASTER
PART 08: native_canvas=[60, 40]; native_bbox=[0, 0, 60, 38]; raw_crop=(115, 49, 1385, 893); correction=[0,0]; NEW_IMAGE_RASTER
PART 09: native_canvas=[76, 36]; native_bbox=[0, 0, 74, 36]; raw_crop=(24, 23, 1759, 837); correction=[0,0]; NEW_IMAGE_RASTER
PART 10: native_canvas=[60, 40]; native_bbox=[0, 0, 59, 38]; raw_crop=(103, 72, 1369, 813); correction=[0,0]; NEW_IMAGE_RASTER
PART 11: native_canvas=[72, 32]; native_bbox=[0, 0, 70, 31]; raw_crop=(20, 20, 1863, 821); correction=[0,0]; NEW_IMAGE_RASTER
PART 12: native_canvas=[104, 64]; native_bbox=[0, 0, 102, 63]; raw_crop=(40, 9, 1524, 974); correction=[0,0]; NEW_IMAGE_RASTER
PART 14: native_canvas=[72, 48]; native_bbox=[0, 2, 70, 48]; raw_crop=(116, 63, 1409, 1010); correction=[0,0]; NEW_IMAGE_RASTER
PART 15: native_canvas=[88, 44]; native_bbox=[0, 0, 87, 43]; raw_crop=(169, 86, 1605, 810); correction=[0,0]; NEW_IMAGE_RASTER
PART 16: native_canvas=[52, 44]; native_bbox=[0, 0, 50, 42]; raw_crop=(66, 37, 1196, 1110); correction=[0,0]; NEW_IMAGE_RASTER
PART 17: native_canvas=[76, 44]; native_bbox=[0, 0, 74, 43]; raw_crop=(132, 88, 1494, 856); correction=[0,0]; NEW_IMAGE_RASTER
PART 18: native_canvas=[100, 60]; native_bbox=[0, 1, 97, 60]; raw_crop=(97, 43, 1557, 939); correction=[0,0]; NEW_IMAGE_RASTER
PART 19: native_canvas=[100, 48]; native_bbox=[0, 3, 99, 48]; raw_crop=(52, 38, 1745, 859); correction=[0,0]; NEW_IMAGE_RASTER
PART 20: native_canvas=[60, 60]; native_bbox=[0, 0, 56, 60]; raw_crop=(43, 39, 1130, 1247); correction=[0,0]; NEW_IMAGE_RASTER
PART 21: native_canvas=[96, 56]; native_bbox=[0, 1, 96, 55]; raw_crop=(55, 65, 1531, 886); correction=[0,0]; NEW_IMAGE_RASTER
PART 22: native_canvas=[4, 4]; native_bbox=None; raw_crop=None; correction=[0,0]; EMPTY_CONTROL
PART 23: native_canvas=[60, 32]; native_bbox=[0, 0, 58, 31]; raw_crop=(351, 7, 1394, 915); correction=[0,0]; NEW_IMAGE_RASTER
PART 24: native_canvas=[56, 48]; native_bbox=[0, 0, 53, 48]; raw_crop=(114, 0, 1222, 1154); correction=[0,0]; NEW_IMAGE_RASTER
PART 25: native_canvas=[80, 40]; native_bbox=[0, 0, 78, 38]; raw_crop=(79, 12, 1719, 799); correction=[0,0]; NEW_IMAGE_RASTER
PART 26: native_canvas=[56, 40]; native_bbox=[0, 0, 54, 40]; raw_crop=(240, 5, 1200, 1011); correction=[0,0]; NEW_IMAGE_RASTER
PART 27: native_canvas=[84, 40]; native_bbox=[0, 0, 82, 40]; raw_crop=(53, 14, 1763, 827); correction=[0,0]; NEW_IMAGE_RASTER
PART 28: native_canvas=[64, 40]; native_bbox=[0, 0, 63, 39]; raw_crop=(94, 0, 1436, 989); correction=[0,0]; NEW_IMAGE_RASTER
PART 29: native_canvas=[44, 56]; native_bbox=[0, 0, 43, 55]; raw_crop=(113, 0, 960, 1379); correction=[0,0]; NEW_IMAGE_RASTER
PART 30: native_canvas=[52, 56]; native_bbox=[0, 0, 51, 56]; raw_crop=(98, 8, 1077, 1295); correction=[0,0]; NEW_IMAGE_RASTER
PART 31: native_canvas=[76, 36]; native_bbox=[0, 0, 74, 36]; raw_crop=(254, 31, 1506, 856); correction=[0,0]; NEW_IMAGE_RASTER
PART 32: native_canvas=[84, 76]; native_bbox=[0, 0, 83, 76]; raw_crop=(187, 144, 1146, 1042); correction=[0,0]; NEW_IMAGE_RASTER
PART 33: native_canvas=[84, 84]; native_bbox=[0, 0, 83, 81]; raw_crop=(112, 118, 1144, 1151); correction=[0,0]; NEW_IMAGE_RASTER
PART 35: native_canvas=[100, 84]; native_bbox=[6, 0, 97, 82]; raw_crop=(170, 36, 1195, 1082); correction=[0,0]; NEW_IMAGE_RASTER
```

### assemble.txt
```text
ASSEMBLE: 360 PNG = 30 frames x 3 variants x 2 directions x 2 scales.
Literal numeric table positions: 100%; per-piece joint corrections=0; extra hand layers=0; runtime rotation=0.
Layer order: character then weapon in FRONT, matching supplied assembled reference. Weapon crossing face is masked behind the original head; no new hands.
Four separately image-generated rolling sprites, no standing image rotation; empty slot 22 retained.
Standing alpha heights: [256, 128]
Clipped outputs: 0
```

### previews.txt
```text
PREVIEWS: 33 slots at shared 2x native scale; all 16 torsos; 10 weapon zoom panels at 2x; original-rig proportions illustrated with own artwork only; four-roll and fresh-master previews also replaced.
```

### proportions.txt
```text
PROPORTIONS: standing native=[87, 131]; head=83x76; torso including arms=82x43; legs=58x31.
Head/whole height=0.580153; head/torso bbox height=1.767442; overlaps=8/11 native px.
frame | native width x height | bbox-edge deviation [L,T,R,B]
00 | [87, 131] | [0, 0, 0, 0]
01 | [87, 135] | [0, 0, 0, 0]
02 | [83, 136] | [0, 0, 0, 0]
03 | [87, 130] | [0, 0, 0, 0]
04 | [83, 140] | [0, 0, 0, 0]
05 | [87, 132] | [0, 0, 0, 0]
06 | [83, 135] | [0, 0, 0, 0]
07 | [87, 139] | [0, 0, 0, 0]
08 | [112, 116] | [0, 0, 0, 0]
09 | [116, 112] | [0, 0, 0, 0]
10 | [112, 116] | [0, 0, 0, 0]
11 | [116, 112] | [0, 0, 0, 0]
12 | [103, 144] | [0, 0, 0, 0]
13 | [91, 128] | [0, 0, 0, 0]
14 | [99, 136] | [0, 0, 0, 0]
15 | [95, 132] | [0, 0, 0, 0]
16 | [103, 132] | [0, 0, 0, 0]
17 | [99, 128] | [0, 0, 0, 0]
18 | [99, 132] | [0, 0, 0, 0]
19 | [91, 128] | [0, 0, 0, 0]
20 | [96, 132] | [0, 0, 0, 0]
21 | [109, 140] | [0, 0, 0, 0]
22 | [87, 148] | [0, 0, 0, 0]
23 | [87, 156] | [0, 0, 0, 0]
24 | [83, 152] | [0, 0, 0, 0]
25 | [103, 152] | [0, 0, 0, 0]
26 | [99, 147] | [0, 0, 0, 0]
27 | [99, 151] | [0, 0, 0, 0]
28 | [83, 147] | [0, 0, 0, 0]
29 | [96, 151] | [0, 0, 0, 0]
PROPORTION FAILURES: 0
```

### weapon_audit.txt
```text
WEAPON AUDIT: 80 frame/variant/direction/scale checks; fixed original numeric positions and rectangles.
kiem 00: angle=151.861; ref=152.182; delta=0.321; bbox=[199, 117]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
kiem 01: angle=151.861; ref=152.182; delta=0.321; bbox=[199, 117]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
kiem 02: angle=151.861; ref=152.182; delta=0.321; bbox=[199, 117]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
kiem 03: angle=151.861; ref=152.182; delta=0.321; bbox=[199, 117]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
kiem 04: angle=151.861; ref=152.182; delta=0.321; bbox=[199, 117]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
kiem 05: angle=151.861; ref=152.182; delta=0.321; bbox=[199, 117]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
kiem 06: angle=151.861; ref=152.182; delta=0.321; bbox=[199, 117]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
kiem 07: angle=151.861; ref=152.182; delta=0.321; bbox=[199, 117]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
kiem 12: angle=151.861; ref=152.182; delta=0.321; bbox=[199, 117]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
kiem 21: angle=151.861; ref=152.182; delta=0.321; bbox=[199, 117]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
cung 00: angle=-64.023; ref=-63.182; delta=0.841; bbox=[170, 258]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
cung 01: angle=-64.023; ref=-63.182; delta=0.841; bbox=[170, 258]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
cung 02: angle=-64.023; ref=-63.182; delta=0.841; bbox=[170, 258]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
cung 03: angle=-64.023; ref=-63.182; delta=0.841; bbox=[170, 258]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
cung 04: angle=-64.023; ref=-63.182; delta=0.841; bbox=[170, 258]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
cung 05: angle=-64.023; ref=-63.182; delta=0.841; bbox=[170, 258]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
cung 06: angle=-64.023; ref=-63.182; delta=0.841; bbox=[170, 258]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
cung 07: angle=-64.023; ref=-63.182; delta=0.841; bbox=[170, 258]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
cung 12: angle=-64.023; ref=-63.182; delta=0.841; bbox=[170, 258]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
cung 21: angle=-64.023; ref=-63.182; delta=0.841; bbox=[170, 258]; position_error=0.000000; face=True; visible_pixel_match=1.000000; pass=True
Hand-hilt error: N/A; no extra grip layers and no invented zero-distance claim.
WEAPON AUDIT FAILURES: 0
```

### validate.txt
```text
VALIDATE: 32 newly image-generated character parts + one truly empty control slot 22.
All 33 native canvases and occupied rectangles match numeric source geometry exactly.
Generation invocations recorded: 36; character vector/SVG count=0; weapon SVG count=2.
360 transparent frame PNGs; literal rig positions; zero per-part assembly correction; zero extra hand layers; left mirrors verified.
Weapon-free frame variants match unarmed pixels; independent roll sources verified; no clipped output.
VISUAL LIMIT: exact bounding rectangles are not proof of identical anatomical silhouettes. See visual review table and comparison log.
FAILURES: 0
```

### package.txt
```text
PACKAGE: 659 files; 360 frame PNGs; 32 newly generated character sources + 1 empty rig slot; native/256/128 parts; ZIP CRC PASS.
Only own original character/weapon artwork included; all external pose comparison pictures remain outside the package.
```

