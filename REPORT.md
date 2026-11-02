# Đinh Bộ Lĩnh Lv1 — bản tạo bằng công cụ ảnh

## Kết quả

Toàn bộ **33 mảnh nhân vật** là ảnh được tạo bằng công cụ tạo ảnh: đầu 32/33/35, thân 5–12 và 14–21, chân 22–31, bốn ảnh lộn toàn thân 1–4. **Không có SVG nhân vật**. Chỉ kiếm và cung dùng SVG.

Ba mẫu gốc đầu/thân/chân trong ảnh người dùng duyệt được giữ làm mẫu cố định. Các mảnh biến thể đều được tạo với đúng bốn đầu vào: ba mẫu đã duyệt và ảnh hướng dẫn cùng số. Mỗi lần sửa bằng công cụ ảnh cũng dùng đủ bốn đầu vào này. Prompt nguyên văn nằm trong `prompts/`; nhật ký từng mảnh nằm trong `tools/logs/` và `tools/image_calls.json`. Dấu vân tay của các đầu vào nằm trong `tools/reference_fingerprints.json`; ảnh hướng dẫn bên ngoài không được đóng gói.

Có **33 lần gọi mới** cho 30 mảnh biến thể, gồm 27 mảnh một lần và ba mảnh hai lần. Ba mảnh mẫu gốc được tạo chung trong **một lần gọi atlas trước đó**, rồi được người dùng duyệt. Vì vậy tổng số lần gọi độc lập gồm cả atlas là **34**, không cộng lặp ba mảnh mẫu thành ba lần gọi riêng. Không mảnh nhân vật nào có số lần gọi bằng 0.

## Số lần gọi cho từng mảnh

| Mảnh | Loại | Lần gọi ảnh | Ghi chú |
|---|---|---:|---|
| 32 | đầu | 1 | Mẫu đã duyệt; một lần atlas chung với hai mẫu còn lại |
| 33 | đầu | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 35 | đầu | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 05 | thân | 1 | Mẫu đã duyệt; một lần atlas chung với hai mẫu còn lại |
| 06 | thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 07 | thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 08 | thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 09 | thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 10 | thân | 2 | Tạo lại một lần để nắm tay trước đóng đúng dáng |
| 11 | thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 12 | thân | 2 | Tạo lại một lần để nắm tay trước đóng đúng dáng |
| 14 | thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 15 | thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 16 | thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 17 | thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 18 | thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 19 | thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 20 | thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 21 | thân | 2 | Tạo lại một lần để nắm tay trước đóng đúng dáng |
| 22 | chân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 23 | chân | 1 | Mẫu đã duyệt; một lần atlas chung với hai mẫu còn lại |
| 24 | chân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 25 | chân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 26 | chân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 27 | chân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 28 | chân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 29 | chân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 30 | chân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 31 | chân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 01 | lộn toàn thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 02 | lộn toàn thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 03 | lộn toàn thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |
| 04 | lộn toàn thân | 1 | Một lần tạo riêng; đủ bốn ảnh đầu vào |

Kiếm và cung là ngoại lệ SVG được người dùng cho phép, không phải mảnh nhân vật trong bảng trên.

## Ghép và xuất

- Mảnh PNG nền trong ở mức 256/128px, kèm ảnh đầu vào độ phân giải cao trong `parts/raw/` để có thể xử lý lại mà không cần gọi mô hình.
- `0_mau/` gồm ba mẫu gốc, atlas đã duyệt, ba mảnh chuẩn hóa ở hai cỡ và ảnh ghép đứng.
- 30 khung × 3 biến thể × 2 hướng × 2 cỡ = **360 PNG khung**. Khung nguồn có canvas 640×640 để chứa vũ khí; mức nhỏ có canvas 320×320. Nhân vật đứng ở nguồn cao 256px; ảnh đứng cắt sát có hai bản cao chính xác 256/128px.
- `sheet_30_khung.png` có 180 ô: ba biến thể ở hai hướng. Các bảng xem trước hướng phải có 30 ô mỗi bảng, 6 cột × 5 hàng.
- `anim_chay.gif`: 5 khung; `anim_nhay.gif`: 8 khung. GIF có nền kem; PNG mảnh và khung có nền trong.
- **Vũ khí chỉ xuất hiện ở 0–7, 12, 21.** Ở 20 khung còn lại, hai biến thể có tên kiếm/cung giống hệt ảnh tay không theo yêu cầu; không phải 90 hình nhân vật khác nhau được vẽ độc lập.
- Khung 8–11 dùng bốn ảnh toàn thân lộn được tạo riêng. Không có phép xoay ảnh nhân vật trong công cụ ghép. Chỉ vũ khí được xoay khi đặt vào nắm tay; ảnh trái dùng lật ngang.

Mảnh lộn 02 xuất hiện ở khung 09: đầu chúc xuống bên phải, chân cuộn lên bên trái. Đây là ảnh toàn thân co người; đã xem riêng chỗ cổ, cổ áo và hướng ngực cùng ba ảnh lộn còn lại. Nó không phải một mảnh thân dùng cho tư thế đứng/chạy.

## Neo, cỡ và màu

`normalize.py` xử lý raster: alpha nền, cắt mép trong, đổi cỡ đồng đều, lượng tử hóa vùng da và dịch đến neo. Không vẽ thêm đầu, thân, tay hoặc chân. Neo cằm/cổ/hông/giày và nắm tay nằm trong `parts/parts.json`. Hình đầu đến cằm khoảng 107px so với áo cổ→vạt 82px, tỷ lệ khoảng 1,31. Ba màu da đích là `#F2C98F`, `#D9A066`, `#FBE3B8`; mặt nạ màu và kiểm tra hai cỡ được lưu lại. Viền khử răng cưa và ảnh khung thu nhỏ vẫn có màu trung gian do pha nét.

`assemble.py` áp dụng bảng tư thế và độ lệch dạng số với Z=4, hệ số 256/131; sau đó căn cổ/cằm và hông cho thiết kế mẫu. Vị trí thô, hiệu chỉnh và nắm tay cuối cùng có trong `frames/assembly.json`. Đây là ghép tư thế phù hợp nhân vật mới, không cam kết trùng từng pixel với nhân vật khác. Áo đứng/chạy/đánh dùng cùng độ dài chuẩn 82px; trong ảnh lộn, chiều dài chiếu thay đổi theo độ co người và góc nhìn của hình được tạo.

Ảnh hướng dẫn số 22 là ô trống 4×4. Mảnh chân 22 vẫn được tạo bằng công cụ ảnh với đủ bốn đầu vào, theo dáng co chân từ mẫu đã duyệt. Các khung lộn dùng ảnh toàn thân riêng, không phụ thuộc mảnh chân 22.

## Soát từng khung

Đã xem ba bảng ghép đủ 30 khung hướng phải, toàn bộ 33 mảnh và bốn ảnh lộn riêng. Hướng trái được so sánh với toàn bộ pixel của ảnh phải lật ngang. Kiểm tra tự động đối chiếu neo và pixel alpha tại cổ, hai điểm giày, điểm nắm tay, cỡ áo chuẩn, mặt nạ màu, cắt biên, tính đối xứng và quy tắc hiện vũ khí. Các kiểm tra hình học không thay thế đánh giá mỹ thuật; đối với ảnh lộn, dáng cổ/áo và hai chân được soát trên ảnh toàn thân.

Bảng dưới tổng hợp ba biến thể. Cột nắm tay áp dụng khi có vũ khí; khi ẩn theo quy tắc thì được xem là đạt điều kiện. Khung nghỉ 00/01 dùng cùng tư thế tay; các khung đánh trên không dùng lại mảnh tương ứng theo bảng.

| Khung | Cổ kín | Áo cùng cỡ | Da cùng bộ | Hai giày | Tay theo dáng | Vũ khí trong tay | Hiện/ẩn đúng | Không cắt | Lật trái đúng | Mảnh có gọi ảnh |
|---|---|---|---|---|---|---|---|---|---|---|
| 00 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 01 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 02 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 03 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 04 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 05 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 06 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 07 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 08 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 09 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 10 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 11 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 12 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 13 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 14 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 15 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 16 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 17 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 18 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 19 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 20 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 21 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 22 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 23 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 24 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 25 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 26 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 27 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 28 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |
| 29 | Có | Có | Có | Có | Có | Có | Có | Có | Có | Có |

## Nhật ký sửa

| Mảnh / bước | Lỗi phát hiện | Xử lý | Số lần tạo ảnh cuối |
|---|---|---|---:|
| Thân 10 | Tay phía trước đang mở | Gọi lại công cụ ảnh, yêu cầu nắm tay đóng; đủ bốn ảnh đầu vào | 2 |
| Thân 12 | Cả hai bàn tay mở | Gọi lại: tay sau mở, tay trước nắm để cầm vũ khí; đủ bốn ảnh đầu vào | 2 |
| Thân 21 | Tay trước xòe ngón | Gọi lại: tay trước duỗi và nắm kín theo dáng hướng dẫn; đủ bốn ảnh đầu vào | 2 |
| Neo chân 29/30 | Điểm kiểm tra giày đặt lệch mép 3–5px, trong khi ảnh đã có hai giày | Sửa tọa độ neo, giữ nguyên ảnh; chạy lại kiểm tra đủ 30 khung | Không phát sinh lần tạo |
| Chuẩn hóa | Cổ nối còn dài và cỡ đứng chưa chính xác | Căn cằm vào cổ, thống nhất cỡ raster; ảnh đứng cuối cao 256px | Không phát sinh lần tạo |
| Mặt nạ màu | Một số chuyển màu nhỏ gây nhiễu một pixel | Lọc nhẹ mặt nạ và màu trước lượng tử hóa; không đổi hình học nhân vật | Không phát sinh lần tạo |

Mỗi mảnh sửa bằng công cụ ảnh chỉ gọi lại một lần, không vượt giới hạn ba lần sửa. Không có thay thế nhân vật bằng vector/code khi ảnh chưa đạt. Nhật ký kiểm tra neo giày trước sửa được giữ nguyên bên dưới.

## Output nguyên văn — lần chạy cuối

### `normalize.py`

```text
NORMALIZE: 33 image-generated character pieces; 256/128px transparent raster exports.
Only alpha cleanup, uniform resampling, color quantization, and anchor translation used; no character geometry drawn.
Fixed anchors: chin=(128,116); neck=(128,104); torso hip=(128,170); leg hip=(128,70).
Torso neck-to-hem length standardized to 82px; 3-color skin masks saved; weapons handled separately.
```

### `make_weapons.py`

```text
WEAPONS: 2 original SVG weapons, rendered at both scales. No character SVGs exist.
```

### `assemble.py`

```text
ASSEMBLE: 30 frames × 3 variants × 2 directions × 2 scales = 360 transparent frame PNGs.
Weapons visible ONLY at frames 0–7, 12, 21; all other armed-variant frames are identical to unarmed.
Roll frames 8–11 use four independently image-generated full-body sprites; ZERO character rotation applied.
Only weapons rotate; characters only translate, uniformly resample, and mirror horizontally.
Standing frame alpha height: 256px; standing display exports: exactly 256px and 128px tall.
Clipped frame count: 0
Saved both-direction sheet, 3 preview boards, run GIF (5 frames), jump GIF (8 frames).
```

### `validate.py`

```text
VALIDATE: 33 image-generated character parts; ZERO parts with 0 image-tool calls.
New image-tool invocations: 33; original approved master atlas: 1 shared invocation.
Character SVG count: 0. Weapon SVG count: 2. Four roll source images have different SHA256 hashes.
Frame PNG count: 360; both directions and scales present. GIF frame counts: 5 / 8.
Weapon visibility: only 00–07, 12, 21; forbidden frames compared byte-for-byte to unarmed pixels.
frame neck size skin feet arms grip visibility bounds mirror image_tool
00 YES YES YES YES YES YES YES YES YES YES
01 YES YES YES YES YES YES YES YES YES YES
02 YES YES YES YES YES YES YES YES YES YES
03 YES YES YES YES YES YES YES YES YES YES
04 YES YES YES YES YES YES YES YES YES YES
05 YES YES YES YES YES YES YES YES YES YES
06 YES YES YES YES YES YES YES YES YES YES
07 YES YES YES YES YES YES YES YES YES YES
08 YES YES YES YES YES YES YES YES YES YES
09 YES YES YES YES YES YES YES YES YES YES
10 YES YES YES YES YES YES YES YES YES YES
11 YES YES YES YES YES YES YES YES YES YES
12 YES YES YES YES YES YES YES YES YES YES
13 YES YES YES YES YES YES YES YES YES YES
14 YES YES YES YES YES YES YES YES YES YES
15 YES YES YES YES YES YES YES YES YES YES
16 YES YES YES YES YES YES YES YES YES YES
17 YES YES YES YES YES YES YES YES YES YES
18 YES YES YES YES YES YES YES YES YES YES
19 YES YES YES YES YES YES YES YES YES YES
20 YES YES YES YES YES YES YES YES YES YES
21 YES YES YES YES YES YES YES YES YES YES
22 YES YES YES YES YES YES YES YES YES YES
23 YES YES YES YES YES YES YES YES YES YES
24 YES YES YES YES YES YES YES YES YES YES
25 YES YES YES YES YES YES YES YES YES YES
26 YES YES YES YES YES YES YES YES YES YES
27 YES YES YES YES YES YES YES YES YES YES
28 YES YES YES YES YES YES YES YES YES YES
29 YES YES YES YES YES YES YES YES YES YES
FAILURES: 0
```

## Output nguyên văn — lượt kiểm tra neo trước sửa

```text
VALIDATE: 33 image-generated character parts; ZERO parts with 0 image-tool calls.
New image-tool invocations: 32; original approved master atlas: 1 shared invocation.
Character SVG count: 0. Weapon SVG count: 2. Four roll source images have different SHA256 hashes.
Frame PNG count: 360; both directions and scales present. GIF frame counts: 5 / 8.
Weapon visibility: only 00–07, 12, 21; forbidden frames compared byte-for-byte to unarmed pixels.
frame neck size skin feet arms grip visibility bounds mirror image_tool
00 YES YES YES YES YES YES YES YES YES YES
01 YES YES YES YES YES YES YES YES YES YES
02 YES YES YES YES YES YES YES YES YES YES
03 YES YES YES YES YES YES YES YES YES YES
04 YES YES YES YES YES YES YES YES YES YES
05 YES YES YES YES YES YES YES YES YES YES
06 YES YES YES YES YES YES YES YES YES YES
07 YES YES YES NO YES YES YES YES YES YES
08 YES YES YES YES YES YES YES YES YES YES
09 YES YES YES YES YES YES YES YES YES YES
10 YES YES YES YES YES YES YES YES YES YES
11 YES YES YES YES YES YES YES YES YES YES
12 YES YES YES NO YES YES YES YES YES YES
13 YES YES YES YES YES YES YES YES YES YES
14 YES YES YES YES YES YES YES YES YES YES
15 YES YES YES YES YES YES YES YES YES YES
16 YES YES YES YES YES YES YES YES YES YES
17 YES YES YES YES YES YES YES YES YES YES
18 YES YES YES YES YES YES YES YES YES YES
19 YES YES YES YES YES YES YES YES YES YES
20 YES YES YES YES YES YES YES YES YES YES
21 YES YES YES NO YES YES YES YES YES YES
22 YES YES YES NO YES YES YES YES YES YES
23 YES YES YES YES YES YES YES YES YES YES
24 YES YES YES YES YES YES YES YES YES YES
25 YES YES YES NO YES YES YES YES YES YES
26 YES YES YES NO YES YES YES YES YES YES
27 YES YES YES NO YES YES YES YES YES YES
28 YES YES YES NO YES YES YES YES YES YES
29 YES YES YES NO YES YES YES YES YES YES
FAILURES: 9
Frame 07: feet
Frame 12: feet
Frame 21: feet
Frame 22: feet
Frame 25: feet
Frame 26: feet
Frame 27: feet
Frame 28: feet
Frame 29: feet
```

## Tái tạo và phạm vi gói

Xem `tools/README.md`. Có thể chạy lại chuẩn hóa/ghép/kiểm tra bằng các raster gốc trong gói. Prompt mô tả cách tạo lại, nhưng đầu ra mô hình không được cam kết lặp lại y hệt. Không đóng gói ảnh hay mã nguồn của nguồn hướng dẫn bên ngoài. Chỉ giữ dữ liệu số về khung/độ lệch và dấu vân tay đầu vào phục vụ đối chiếu.

## Output nguyên văn đóng gói

```text
PACKAGE: 608 files; 360 frame PNGs; 33 raw character images; 2 weapon SVGs; ZIP CRC PASS.
```
