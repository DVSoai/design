# Đinh Bộ Lĩnh Lv1 — sửa vũ khí và đồng bộ tay

Mốc đầu vào: commit `1def3359b400ec09f18a9045b8c487370db85390`. Bản này giữ nguyên đầu, chân, bốn mảnh lộn và các thân ngoài 5, 14, 15, 17, 18, 19. Kiểu lộn 08–11 được giữ nguyên. Hash xác nhận **156 file PNG được bảo vệ không thay đổi**, gồm 108 PNG mảnh/raster/mặt nạ và 48 PNG khung lộn.

## Hai điều chỉnh đã được người dùng chốt

1. Cho phép thêm lớp tay cầm riêng bằng công cụ ảnh cho biến thể có vũ khí, giữ riêng mảnh gốc và tay không. Các lớp này cần thiết vì tay gốc ở một số dáng không trùng chuôi khi dùng đúng tọa độ yêu cầu.
2. Ngưỡng **±12% áp cho độ dày bắp tay**; diện tích da ghi riêng theo dáng, không dùng diện tích để loại ảnh có che khuất khác nhau.

**Một giới hạn đo cần giữ rõ:** giữa bắp tay trái của thân 16 bị cẳng tay/quấn cổ tay che. Mảnh này được giữ nguyên theo phạm vi công việc; độ dày đầy đủ ghi **N/A**, không được coi là một phép đo đạt. Dải da nhìn thấy vẫn có số đo tham khảo và diện tích mặt nạ. Điều này ảnh hưởng cột đo tay ở khung 15 và 24.

## Kiếm và cung

- Vị trí dùng trực tiếp ô thứ tư của bảng khung cộng độ lệch mảnh: `x = cx + (dx+pdx)×4×256/131`; `y = cy + (-dy+pdy)×4×256/131`. Điểm gốc khung là `(320,444)` ở canvas 640px. Chỉ làm tròn khi đặt lên lưới pixel; **không bù tay, không tự dịch vũ khí theo nắm tay và không xoay vũ khí lúc ghép**.
- Kiếm được vẽ trực tiếp theo hướng mũi xuống-trái, chuôi lên-phải; lưỡi bản dày có sống, chuôi quấn, đốc vàng. Khung bao đục ở cỡ 256 là **199×117px**, chuẩn quy đổi **199,328×117,252px**. Góc lưỡi **152,425°**, hướng dẫn **152,182°**, lệch **0,243°**.
- Cung chéo từ dưới-trái lên trên-phải, gỗ nâu dày, quấn tay cầm ở giữa, dây ở phía lưng. Khung bao **170×258px**, chuẩn quy đổi **170,015×257,954px**. Trục cung **−65,201°**, hướng dẫn **−63,182°**, lệch **2,019°**.
- Vũ khí vẽ **trên thân**, ngón tay từ lớp ảnh tạo riêng vẽ trên chuôi. Không dùng hình khối/vector để vẽ người. Các chấm đăng ký và chuôi xanh tạm được loại khỏi ảnh xuất.
- Ở khung đứng 00/01, đáy cung lần lượt là y=427/419, bàn chân là y=452/444; cung không thấp hơn chân.
- Vũ khí chỉ hiện ở **00–07, 12, 21**. Hai biến thể vũ khí ở các khung còn lại giống tay không, được kiểm tra bằng pixel.

Quy ước góc: trục x sang phải, y xuống dưới, góc tính theo chiều kim đồng hồ từ +x. Kiếm đo từ chuôi về mũi; cung đo từ đầu dưới về đầu trên. Hướng trái đo lại trên ảnh lật, không dùng cùng dấu PCA của hướng phải. Đo ở cỡ 128 được thực hiện trên lớp pixel thu nhỏ thực tế. Khung bao đo tại alpha >127; có sai số làm tròn dưới một pixel so với kích thước liên tục quy đổi.

## Đối chiếu từng khung có vũ khí

Đã tạo 20 ảnh cặp hướng dẫn | của mình, mỗi ô 640×640 cùng hệ số 256/131 và thêm bốn tờ tổng hợp trong thư mục tạm. Đã xem các tờ khung và các cặp đứng/rơi ở cả kiếm/cung. **Toàn bộ ảnh đối chiếu nằm ngoài ZIP và ngoài thư mục xuất**; gói chỉ lưu số đo.

Bảng dưới có đầy đủ 10 khung × 2 vũ khí × 2 hướng; mỗi dòng ghi cả hai cỡ. File `tools/weapon_audit.json` chứa 80 bản ghi, gồm vị trí, đối chiếu pixel vũ khí đục, góc, sai lệch, khung bao và lớp ngón tay.

| Khung | Vũ khí | Hướng | Góc 256 / 128 (°) | Hướng dẫn (°) | Lệch 256 / 128 (°) | Tay bọc chuôi | Bao 256 thực / chuẩn (px) | Bao 128 thực / chuẩn (px) |
|---|---|---|---:|---:|---:|---|---|---|
| 00 | kiem | phai | 152.425 / 152.325 | 152.182 | 0.243 / 0.143 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 00 | kiem | trai | 27.575 / 27.675 | 27.818 | 0.243 / 0.143 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 01 | kiem | phai | 152.425 / 152.325 | 152.182 | 0.243 / 0.143 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 01 | kiem | trai | 27.575 / 27.675 | 27.818 | 0.243 / 0.143 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 02 | kiem | phai | 152.425 / 152.372 | 152.182 | 0.243 / 0.190 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 02 | kiem | trai | 27.575 / 27.628 | 27.818 | 0.243 / 0.190 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 03 | kiem | phai | 152.425 / 152.372 | 152.182 | 0.243 / 0.190 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 03 | kiem | trai | 27.575 / 27.628 | 27.818 | 0.243 / 0.190 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 04 | kiem | phai | 152.425 / 152.372 | 152.182 | 0.243 / 0.190 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 04 | kiem | trai | 27.575 / 27.628 | 27.818 | 0.243 / 0.190 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 05 | kiem | phai | 152.425 / 152.372 | 152.182 | 0.243 / 0.190 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 05 | kiem | trai | 27.575 / 27.628 | 27.818 | 0.243 / 0.190 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 06 | kiem | phai | 152.425 / 152.372 | 152.182 | 0.243 / 0.190 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 06 | kiem | trai | 27.575 / 27.628 | 27.818 | 0.243 / 0.190 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 07 | kiem | phai | 152.425 / 152.285 | 152.182 | 0.243 / 0.103 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 07 | kiem | trai | 27.575 / 27.715 | 27.818 | 0.243 / 0.103 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 12 | kiem | phai | 152.425 / 152.285 | 152.182 | 0.243 / 0.103 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 12 | kiem | trai | 27.575 / 27.715 | 27.818 | 0.243 / 0.103 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 21 | kiem | phai | 152.425 / 152.370 | 152.182 | 0.243 / 0.189 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 21 | kiem | trai | 27.575 / 27.630 | 27.818 | 0.243 / 0.189 | Có | 199×117 / 199.328×117.252 | 100×58 / 99.664×58.626 |
| 00 | cung | phai | -65.201 / -64.773 | -63.182 | 2.019 / 1.592 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 00 | cung | trai | -114.799 / -115.227 | -116.818 | 2.019 / 1.592 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 01 | cung | phai | -65.201 / -64.773 | -63.182 | 2.019 / 1.592 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 01 | cung | trai | -114.799 / -115.227 | -116.818 | 2.019 / 1.592 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 02 | cung | phai | -65.201 / -64.678 | -63.182 | 2.019 / 1.497 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 02 | cung | trai | -114.799 / -115.322 | -116.818 | 2.019 / 1.497 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 03 | cung | phai | -65.201 / -64.678 | -63.182 | 2.019 / 1.497 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 03 | cung | trai | -114.799 / -115.322 | -116.818 | 2.019 / 1.497 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 04 | cung | phai | -65.201 / -64.678 | -63.182 | 2.019 / 1.497 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 04 | cung | trai | -114.799 / -115.322 | -116.818 | 2.019 / 1.497 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 05 | cung | phai | -65.201 / -64.678 | -63.182 | 2.019 / 1.497 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 05 | cung | trai | -114.799 / -115.322 | -116.818 | 2.019 / 1.497 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 06 | cung | phai | -65.201 / -64.678 | -63.182 | 2.019 / 1.497 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 06 | cung | trai | -114.799 / -115.322 | -116.818 | 2.019 / 1.497 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 07 | cung | phai | -65.201 / -64.773 | -63.182 | 2.019 / 1.592 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 07 | cung | trai | -114.799 / -115.227 | -116.818 | 2.019 / 1.592 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 12 | cung | phai | -65.201 / -64.773 | -63.182 | 2.019 / 1.592 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 12 | cung | trai | -114.799 / -115.227 | -116.818 | 2.019 / 1.592 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 21 | cung | phai | -65.201 / -64.678 | -63.182 | 2.019 / 1.497 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |
| 21 | cung | trai | -114.799 / -115.322 | -116.818 | 2.019 / 1.497 | Có | 170×258 / 170.015×257.954 | 85×129 / 85.008×128.977 |

## Thân vẽ lại và số lần gọi công cụ ảnh

Các thân được tạo trên nền xanh phẳng rồi key nền, chuẩn hóa neo cổ/hông, áo 82px và cùng bảng da `#F2C98F`, `#D9A066`, `#FBE3B8`. Mọi thay đổi dáng nhân vật đều bắt đầu từ công cụ ảnh. Prompt nguyên văn theo từng lần gọi nằm trong `prompts/`; raster gốc và nhật ký được giữ để đối chiếu.

| Thân | Công việc | Số gọi ảnh ở lượt này | Tổng lịch sử | Kết quả |
|---|---|---:|---:|---|
| 05 | Làm đầy tay theo thân 8; giữ tư thế đứng | 1 | 2 | Đã chọn bản cuối |
| 14 | Giảm bắp tay phồng ở dáng thủ | 1 | 2 | Đã chọn bản cuối |
| 15 | Đấm thấp ra trước; tay kia kéo về hông | 2 | 3 | Đã chọn bản cuối |
| 17 | Tay sau vung ra sau lưng; tay trước thủ | 1 | 2 | Đã chọn bản cuối |
| 18 | Giảm tay quá to/dài theo chuẩn 8 | 1 | 2 | Đã chọn bản cuối |
| 19 | Giảm bắp tay phồng theo chuẩn 8 | 1 | 2 | Đã chọn bản cuối |

Thân 15 được gọi lại vì bản đầu còn để tay thấp bên hông, chưa đẩy rõ ra trước. Các thân đồng bộ tay dùng thân 8 và ảnh dáng cùng số; thân 15/17 dùng thân 5 và ảnh dáng cùng số. Tất cả các lần này có đúng hai ảnh đầu vào theo yêu cầu mới, nền #00FF00. Không mảnh nào vượt ba lần tạo ở lượt sửa này.

Có thêm 18 nguồn ảnh lớp tay cầm cho các vị trí tương đối, tổng 20 lần gọi gồm hai lần sửa. Lớp kiếm 02 được sửa để chỉ một tay nắm chuôi; lớp kiếm 12 được sửa để tay cầm ở vị trí thấp, tay kia mở và giơ lên. Khung 01 dùng lại lớp 00; không tính đó là một lần gọi ảnh mới. Lớp tay cầm được đăng ký từ các mốc màu, ghép lại raster; ngón tay là pixel đã được công cụ ảnh vẽ, không được vẽ bằng mã. Mảnh gốc ngoài sáu thân kể trên không bị ghi lại.

## Số đo tay

Chuẩn thân 8: trung bình **17,625px** ở cỡ 256. Mỗi bên đo ba mặt cắt vuông góc tại 45%, 50%, 55% đoạn vai–khuỷu đã ghi trong `arm_metrics.py`; lấy trung bình hai bên đo được cho phép so sánh từng thân. Bảng vẫn ghi số đo mỗi bên để không giấu khác biệt góc nhìn. Các mốc ở tay gập được rà lại trên ảnh để tránh đo nhầm cẳng tay/quấn cổ tay.

Diện tích là số pixel trắng trong mặt nạ da chuẩn hóa đã lưu, cùng quy tắc cho mọi thân, gồm cổ và bàn tay. Đây là diện tích da nhìn thấy theo mặt nạ màu, không phải diện tích cơ thể 3D; sau xác nhận của người dùng không áp ngưỡng ±12% cho cột này.

| Thân | Bắp bên 1 / bên 2 (px) | Trung bình (px) | Lệch so với 8 | Diện tích mặt nạ da (px²) | Độ dày |
|---|---:|---:|---:|---:|---|
| 05 | 21.83 / 11.00 | 16.42 | -6.86% | 2764 | Đạt |
| 06 | 20.67 / 15.83 | 18.25 | +3.55% | 2212 | Đạt |
| 07 | 19.42 / 12.92 | 16.17 | -8.27% | 2546 | Đạt |
| 08 | 18.42 / 16.83 | 17.62 | +0.00% | 2828 | Đạt |
| 09 | 18.75 / 13.42 | 16.08 | -8.75% | 2593 | Đạt |
| 10 | 18.50 / 17.33 | 17.92 | +1.65% | 1994 | Đạt |
| 11 | 21.17 / 15.42 | 18.29 | +3.78% | 2321 | Đạt |
| 12 | 21.17 / 18.08 | 19.62 | +11.35% | 3100 | Đạt |
| 14 | 14.25 / 21.33 | 17.79 | +0.95% | 2363 | Đạt |
| 15 | 23.08 / 12.42 | 17.75 | +0.71% | 1977 | Đạt |
| 16 | 9.08 / 13.42 | N/A | N/A | 2203 | N/A — giữa bắp bị che |
| 17 | 13.92 / 17.50 | 15.71 | -10.87% | 1716 | Đạt |
| 18 | 18.50 / 15.92 | 17.21 | -2.36% | 2730 | Đạt |
| 19 | 18.50 / 15.75 | 17.12 | -2.84% | 2442 | Đạt |
| 20 | 18.75 / 19.25 | 19.00 | +7.80% | 3008 | Đạt |
| 21 | 17.42 / 15.00 | 16.21 | -8.04% | 2590 | Đạt |

Các giá trị 9,08/13,42px ở thân 16 chỉ là dải da nhìn thấy, không được dùng làm đường kính bắp tay đầy đủ. Thân này không được tính vào số phép đo đạt; vẫn giữ nguyên theo yêu cầu bảo toàn.

## Bảng tự soát 30 khung

Cột tay có số đo trung bình, độ lệch và diện tích; không chỉ ghi Có/Không. Khung lộn giữ nguyên byte ảnh nên không suy ra số đo tay mới từ ảnh toàn thân đã co người. Cột tay bọc chuôi áp dụng cho các khung có vũ khí; ở khung ẩn là không áp dụng. Các ô hình học đã được kiểm tra ở các biến thể; mức màu ở đường khử răng cưa có thể là màu trung gian.

| Khung | Cổ kín | Áo cùng cỡ | Da cùng bộ | Hai chân | Hiện/ẩn vũ khí đúng | Tay bọc chuôi | Tay cùng cỡ: trung bình, lệch; diện tích |
|---|---|---|---|---|---|---|---|
| 00 | Có | Có | Có | Có | Có | Có | 16.42px, -6.86%; 2764px² — Đạt |
| 01 | Có | Có | Có | Có | Có | Có | 16.42px, -6.86%; 2764px² — Đạt |
| 02 | Có | Có | Có | Có | Có | Có | 18.25px, +3.55%; 2212px² — Đạt |
| 03 | Có | Có | Có | Có | Có | Có | 16.17px, -8.27%; 2546px² — Đạt |
| 04 | Có | Có | Có | Có | Có | Có | 17.62px, +0.00%; 2828px² — Đạt |
| 05 | Có | Có | Có | Có | Có | Có | 16.08px, -8.75%; 2593px² — Đạt |
| 06 | Có | Có | Có | Có | Có | Có | 17.92px, +1.65%; 1994px² — Đạt |
| 07 | Có | Có | Có | Có | Có | Có | 18.29px, +3.78%; 2321px² — Đạt |
| 08 | Có | Có | Có | Có | Có | Không áp dụng | Giữ nguyên mảnh lộn |
| 09 | Có | Có | Có | Có | Có | Không áp dụng | Giữ nguyên mảnh lộn |
| 10 | Có | Có | Có | Có | Có | Không áp dụng | Giữ nguyên mảnh lộn |
| 11 | Có | Có | Có | Có | Có | Không áp dụng | Giữ nguyên mảnh lộn |
| 12 | Có | Có | Có | Có | Có | Có | 19.62px, +11.35%; 3100px² — Đạt |
| 13 | Có | Có | Có | Có | Có | Không áp dụng | 17.79px, +0.95%; 2363px² — Đạt |
| 14 | Có | Có | Có | Có | Có | Không áp dụng | 17.75px, +0.71%; 1977px² — Đạt |
| 15 | Có | Có | Có | Có | Có | Không áp dụng | N/A: bị che; dải chiếu 9.08/13.42px; 2203px² |
| 16 | Có | Có | Có | Có | Có | Không áp dụng | 15.71px, -10.87%; 1716px² — Đạt |
| 17 | Có | Có | Có | Có | Có | Không áp dụng | 17.21px, -2.36%; 2730px² — Đạt |
| 18 | Có | Có | Có | Có | Có | Không áp dụng | 17.12px, -2.84%; 2442px² — Đạt |
| 19 | Có | Có | Có | Có | Có | Không áp dụng | 19.00px, +7.80%; 3008px² — Đạt |
| 20 | Có | Có | Có | Có | Có | Không áp dụng | 16.21px, -8.04%; 2590px² — Đạt |
| 21 | Có | Có | Có | Có | Có | Có | 19.62px, +11.35%; 3100px² — Đạt |
| 22 | Có | Có | Có | Có | Có | Không áp dụng | 17.79px, +0.95%; 2363px² — Đạt |
| 23 | Có | Có | Có | Có | Có | Không áp dụng | 17.75px, +0.71%; 1977px² — Đạt |
| 24 | Có | Có | Có | Có | Có | Không áp dụng | N/A: bị che; dải chiếu 9.08/13.42px; 2203px² |
| 25 | Có | Có | Có | Có | Có | Không áp dụng | 15.71px, -10.87%; 1716px² — Đạt |
| 26 | Có | Có | Có | Có | Có | Không áp dụng | 17.21px, -2.36%; 2730px² — Đạt |
| 27 | Có | Có | Có | Có | Có | Không áp dụng | 17.12px, -2.84%; 2442px² — Đạt |
| 28 | Có | Có | Có | Có | Có | Không áp dụng | 19.00px, +7.80%; 3008px² — Đạt |
| 29 | Có | Có | Có | Có | Có | Không áp dụng | 16.21px, -8.04%; 2590px² — Đạt |

## Kết quả kiểm tra và xuất

- 360 PNG khung: 30 × 3 biến thể × 2 hướng × 2 cỡ; sheet hai hướng và ba preview được xuất lại.
- 80 kiểm tra vũ khí đạt, sai lệch góc đều ≤10°; vị trí đối chiếu độc lập với bảng số và pixel asset trên ảnh ghép.
- 156 PNG được bảo vệ so hash không đổi; toàn bộ lộn 08–11 giữ nguyên.
- 15 thân có số đo bắp tay đầy đủ đều trong ±12%; 1 thân có giữa bắp bị che ghi N/A, không gọi là Đạt.
- Không có SVG người; chỉ hai SVG vũ khí. Chạy/nhảy GIF được xuất lại. PNG nền trong; GIF nền kem.
- Không có ảnh hướng dẫn, mã nguồn hay tên của nguồn hướng dẫn bên ngoài trong ZIP. Các bảng đối chiếu nằm ở thư mục tạm.

## Output script nguyên văn — lượt kiểm tra cuối

### normalize.py

```text
NORMALIZE: ['5', '14', '15', '17', '18', '19']; 33 total character records; 256/128px transparent raster exports.
Only alpha cleanup, uniform resampling, color quantization, and anchor translation used; no character geometry drawn.
Fixed anchors: chin=(128,116); neck=(128,104); torso hip=(128,170); leg hip=(128,70).
Torso neck-to-hem length standardized to 82px; 3-color skin masks saved; weapons handled separately.
NORMALIZE: ['15']; 33 total character records; 256/128px transparent raster exports.
Only alpha cleanup, uniform resampling, color quantization, and anchor translation used; no character geometry drawn.
Fixed anchors: chin=(128,116); neck=(128,104); torso hip=(128,170); leg hip=(128,70).
Torso neck-to-hem length standardized to 82px; 3-color skin masks saved; weapons handled separately.
NORMALIZE: ['5', '14', '15', '17', '18', '19']; 33 total character records; 256/128px transparent raster exports.
Only alpha cleanup, uniform resampling, color quantization, and anchor translation used; no character geometry drawn.
Fixed anchors: chin=(128,116); neck=(128,104); torso hip=(128,170); leg hip=(128,70).
Torso neck-to-hem length standardized to 82px; 3-color skin masks saved; weapons handled separately.
ARM METRICS: canonical 256 scale; reference torso 08; tolerance ±12% for thickness; area reported per pose per user clarification.
05: biceps=[21.833333333333332, 11.0], mean=16.416666666666664, width_delta=-6.855791962174951, skin_area=2764, area_delta=-2.26%, PASS
06: biceps=[20.666666666666668, 15.833333333333334], mean=18.25, width_delta=3.546099290780136, skin_area=2212, area_delta=-21.78%, PASS
07: biceps=[19.416666666666668, 12.916666666666666], mean=16.166666666666668, width_delta=-8.274231678486988, skin_area=2546, area_delta=-9.97%, PASS
08: biceps=[18.416666666666668, 16.833333333333332], mean=17.625, width_delta=0.0, skin_area=2828, area_delta=0.00%, PASS
09: biceps=[18.75, 13.416666666666666], mean=16.083333333333332, width_delta=-8.747044917257686, skin_area=2593, area_delta=-8.31%, PASS
10: biceps=[18.5, 17.333333333333332], mean=17.916666666666664, width_delta=1.6548463356973908, skin_area=1994, area_delta=-29.49%, PASS
11: biceps=[21.166666666666668, 15.416666666666666], mean=18.291666666666668, width_delta=3.78250591016549, skin_area=2321, area_delta=-17.93%, PASS
12: biceps=[21.166666666666668, 18.083333333333332], mean=19.625, width_delta=11.347517730496449, skin_area=3100, area_delta=9.62%, PASS
14: biceps=[14.25, 21.333333333333332], mean=17.791666666666664, width_delta=0.9456264775413503, skin_area=2363, area_delta=-16.44%, PASS
15: biceps=[23.083333333333332, 12.416666666666666], mean=17.75, width_delta=0.7092198581560183, skin_area=1977, area_delta=-30.09%, PASS
16: biceps=[9.083333333333334, 13.416666666666666], mean=None, width_delta=None, skin_area=2203, area_delta=-22.10%, NOT_MEASURABLE_OCCLUDED
17: biceps=[13.916666666666666, 17.5], mean=15.708333333333332, width_delta=-10.874704491725772, skin_area=1716, area_delta=-39.32%, PASS
18: biceps=[18.5, 15.916666666666666], mean=17.208333333333332, width_delta=-2.3640661938534313, skin_area=2730, area_delta=-3.47%, PASS
19: biceps=[18.5, 15.75], mean=17.125, width_delta=-2.8368794326241176, skin_area=2442, area_delta=-13.65%, PASS
20: biceps=[18.75, 19.25], mean=19.0, width_delta=7.801418439716312, skin_area=3008, area_delta=6.36%, PASS
21: biceps=[17.416666666666668, 15.0], mean=16.208333333333336, width_delta=-8.037825059101644, skin_area=2590, area_delta=-8.42%, PASS
```

### make_weapons.py

```text
WEAPON kiem: bbox=[199, 117]; target=[199.3282, 117.2519]; angle=152.425; reference=152.182; delta=0.243; runtime_rotation=0
WEAPON cung: bbox=[170, 258]; target=[170.0153, 257.9542]; angle=-65.201; reference=-63.182; delta=2.019; runtime_rotation=0
```

### normalize_grips.py

```text
GRIP kiem_00: side=right; fingers_wrap=True; raster_displacement=[17.070951907249565, -6.757933289237627]; image_calls=1
GRIP kiem_02: side=right; fingers_wrap=True; raster_displacement=[8.40456197041226, -15.604159490696816]; image_calls=2
GRIP kiem_03: side=right; fingers_wrap=True; raster_displacement=[-6.735449946110322, 9.27240572702081]; image_calls=1
GRIP kiem_04: side=right; fingers_wrap=True; raster_displacement=[-35.195360118403926, -13.60646764270254]; image_calls=1
GRIP kiem_05: side=right; fingers_wrap=True; raster_displacement=[-7.10473131604877, -10.420988043979975]; image_calls=1
GRIP kiem_06: side=right; fingers_wrap=True; raster_displacement=[2.1178251733473132, -6.687700596878301]; image_calls=1
GRIP kiem_07: side=right; fingers_wrap=True; raster_displacement=[0.9125768436854855, -5.995755668410311]; image_calls=1
GRIP kiem_12: side=right; fingers_wrap=True; raster_displacement=[17.909509141348735, 36.03008098241335]; image_calls=2
GRIP kiem_21: side=right; fingers_wrap=True; raster_displacement=[24.536045641483867, 53.73887297614061]; image_calls=1
GRIP cung_00: side=right; fingers_wrap=True; raster_displacement=[-15.139178570170458, -11.398963607467152]; image_calls=1
GRIP cung_02: side=left; fingers_wrap=True; raster_displacement=[0.8080326351772555, -37.315790722584865]; image_calls=1
GRIP cung_03: side=left; fingers_wrap=True; raster_displacement=[34.10072882962848, -10.432303595996729]; image_calls=1
GRIP cung_04: side=left; fingers_wrap=True; raster_displacement=[0.8183929991940317, -18.395717091655257]; image_calls=1
GRIP cung_05: side=left; fingers_wrap=True; raster_displacement=[2.4033964689796647, -19.344337018238463]; image_calls=1
GRIP cung_06: side=left; fingers_wrap=True; raster_displacement=[5.712364295385299, -16.290637320369427]; image_calls=1
GRIP cung_07: side=right; fingers_wrap=True; raster_displacement=[-33.09844119547972, -18.79536267995732]; image_calls=1
GRIP cung_12: side=right; fingers_wrap=True; raster_displacement=[-14.858051754025041, 36.21806302891807]; image_calls=1
GRIP cung_21: side=right; fingers_wrap=True; raster_displacement=[-11.121290264788769, 29.94105964695376]; image_calls=1
GRIP LAYERS: original unarmed character pieces left unchanged; frame 01 reuses frame 00 relative pose. Colored markers removed.
```

### assemble.py

```text
ASSEMBLE: 30 frames × 3 variants × 2 directions × 2 scales = 360 transparent frame PNGs.
Weapons visible ONLY at frames 0–7, 12, 21; all other armed-variant frames are identical to unarmed.
Roll frames 8–11 use four independently image-generated full-body sprites; ZERO character rotation applied.
Runtime weapon rotation: ZERO. Positions come directly from the fourth pose cell plus part offsets.
Layer order: character, fixed-angle weapon ABOVE torso, image-generated fingers ABOVE grip.
Standing frame alpha height: 256px; standing display exports: exactly 256px and 128px tall.
Clipped frame count: 0
Saved both-direction sheet, 3 preview boards, run GIF (5 frames), jump GIF (8 frames).
```

### arm_metrics.py

```text
ARM METRICS: canonical 256 scale; reference torso 08; tolerance ±12% for thickness; area reported per pose per user clarification.
05: biceps=[21.833333333333332, 11.0], mean=16.416666666666664, width_delta=-6.855791962174951, skin_area=2764, area_delta=-2.26%, PASS
06: biceps=[20.666666666666668, 15.833333333333334], mean=18.25, width_delta=3.546099290780136, skin_area=2212, area_delta=-21.78%, PASS
07: biceps=[19.416666666666668, 12.916666666666666], mean=16.166666666666668, width_delta=-8.274231678486988, skin_area=2546, area_delta=-9.97%, PASS
08: biceps=[18.416666666666668, 16.833333333333332], mean=17.625, width_delta=0.0, skin_area=2828, area_delta=0.00%, PASS
09: biceps=[18.75, 13.416666666666666], mean=16.083333333333332, width_delta=-8.747044917257686, skin_area=2593, area_delta=-8.31%, PASS
10: biceps=[18.5, 17.333333333333332], mean=17.916666666666664, width_delta=1.6548463356973908, skin_area=1994, area_delta=-29.49%, PASS
11: biceps=[21.166666666666668, 15.416666666666666], mean=18.291666666666668, width_delta=3.78250591016549, skin_area=2321, area_delta=-17.93%, PASS
12: biceps=[21.166666666666668, 18.083333333333332], mean=19.625, width_delta=11.347517730496449, skin_area=3100, area_delta=9.62%, PASS
14: biceps=[14.25, 21.333333333333332], mean=17.791666666666664, width_delta=0.9456264775413503, skin_area=2363, area_delta=-16.44%, PASS
15: biceps=[23.083333333333332, 12.416666666666666], mean=17.75, width_delta=0.7092198581560183, skin_area=1977, area_delta=-30.09%, PASS
16: biceps=[9.083333333333334, 13.416666666666666], mean=None, width_delta=None, skin_area=2203, area_delta=-22.10%, NOT_MEASURABLE_OCCLUDED
17: biceps=[13.916666666666666, 17.5], mean=15.708333333333332, width_delta=-10.874704491725772, skin_area=1716, area_delta=-39.32%, PASS
18: biceps=[18.5, 15.916666666666666], mean=17.208333333333332, width_delta=-2.3640661938534313, skin_area=2730, area_delta=-3.47%, PASS
19: biceps=[18.5, 15.75], mean=17.125, width_delta=-2.8368794326241176, skin_area=2442, area_delta=-13.65%, PASS
20: biceps=[18.75, 19.25], mean=19.0, width_delta=7.801418439716312, skin_area=3008, area_delta=6.36%, PASS
21: biceps=[17.416666666666668, 15.0], mean=16.208333333333336, width_delta=-8.037825059101644, skin_area=2590, area_delta=-8.42%, PASS
```

### verify_preservation.py

```text
PRESERVATION: 156 protected PNG files compared to baseline; unauthorized pixel/file changes=0.
Only torso parts 5,14,15,17,18,19 are authorized replacements. All heads, legs, rolls, other torsos and all roll frame exports remain byte-identical.
```

### weapon_audit.py

```text
STANDING 00: bow_bottom=427; feet_bottom=452; PASS
STANDING 01: bow_bottom=419; feet_bottom=444; PASS
WEAPON AUDIT: 10 frames × 2 weapons × 2 directions × 2 scales = 80 checks.
kiem 00: angle=152.425; ref=152.182; delta=0.243; wrap=True; bbox=[199, 117]; target=[199.328, 117.252]; PASS
kiem 01: angle=152.425; ref=152.182; delta=0.243; wrap=True; bbox=[199, 117]; target=[199.328, 117.252]; PASS
kiem 02: angle=152.425; ref=152.182; delta=0.243; wrap=True; bbox=[199, 117]; target=[199.328, 117.252]; PASS
kiem 03: angle=152.425; ref=152.182; delta=0.243; wrap=True; bbox=[199, 117]; target=[199.328, 117.252]; PASS
kiem 04: angle=152.425; ref=152.182; delta=0.243; wrap=True; bbox=[199, 117]; target=[199.328, 117.252]; PASS
kiem 05: angle=152.425; ref=152.182; delta=0.243; wrap=True; bbox=[199, 117]; target=[199.328, 117.252]; PASS
kiem 06: angle=152.425; ref=152.182; delta=0.243; wrap=True; bbox=[199, 117]; target=[199.328, 117.252]; PASS
kiem 07: angle=152.425; ref=152.182; delta=0.243; wrap=True; bbox=[199, 117]; target=[199.328, 117.252]; PASS
kiem 12: angle=152.425; ref=152.182; delta=0.243; wrap=True; bbox=[199, 117]; target=[199.328, 117.252]; PASS
kiem 21: angle=152.425; ref=152.182; delta=0.243; wrap=True; bbox=[199, 117]; target=[199.328, 117.252]; PASS
cung 00: angle=-65.201; ref=-63.182; delta=2.019; wrap=True; bbox=[170, 258]; target=[170.015, 257.954]; PASS
cung 01: angle=-65.201; ref=-63.182; delta=2.019; wrap=True; bbox=[170, 258]; target=[170.015, 257.954]; PASS
cung 02: angle=-65.201; ref=-63.182; delta=2.019; wrap=True; bbox=[170, 258]; target=[170.015, 257.954]; PASS
cung 03: angle=-65.201; ref=-63.182; delta=2.019; wrap=True; bbox=[170, 258]; target=[170.015, 257.954]; PASS
cung 04: angle=-65.201; ref=-63.182; delta=2.019; wrap=True; bbox=[170, 258]; target=[170.015, 257.954]; PASS
cung 05: angle=-65.201; ref=-63.182; delta=2.019; wrap=True; bbox=[170, 258]; target=[170.015, 257.954]; PASS
cung 06: angle=-65.201; ref=-63.182; delta=2.019; wrap=True; bbox=[170, 258]; target=[170.015, 257.954]; PASS
cung 07: angle=-65.201; ref=-63.182; delta=2.019; wrap=True; bbox=[170, 258]; target=[170.015, 257.954]; PASS
cung 12: angle=-65.201; ref=-63.182; delta=2.019; wrap=True; bbox=[170, 258]; target=[170.015, 257.954]; PASS
cung 21: angle=-65.201; ref=-63.182; delta=2.019; wrap=True; bbox=[170, 258]; target=[170.015, 257.954]; PASS
WEAPON AUDIT FAILURES: 0
```

### validate.py

```text
VALIDATE: 33 image-generated character parts; ZERO parts with 0 image-tool calls.
Current revision image-tool invocations: torso=7, additional grip layers=20.
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

### So sánh trong thư mục tạm

```text
COMPARISON_TEMP: 20 source|character pairs, 640×640 each panel, same source scale 256/131, plus four contact pages.
Fresh numeric pose/part data matched the saved measurements. Comparisons remain outside the deliverable folder and ZIP.
Temporary comparison folder: /tmp/dbl_weapon_revision/comparisons
```

## Nhật ký chẩn đoán trước đó

`revision2_arm_metrics_round1.txt` giữ nguyên lần đo thử theo ngưỡng diện tích cũ và mốc tay gập tạm. Tiêu chí đã đổi theo trả lời của người dùng; mốc vai–khuỷu được cập nhật trên ảnh. `revision2_weapon_audit_round1.txt` giữ nguyên lỗi chọn dấu trục PCA của kiếm trái: ban đầu chọn hướng ngược 180°, đã sửa phép đo về chiều chuôi→mũi, không xoay hay sửa ảnh vũ khí để làm kiểm tra qua. Đây không phải kết quả cuối.

Chạy lại pipeline theo `tools/README.md`. Các raster gốc, mặt nạ, metadata, prompt và nhật ký có trong gói để xử lý lại mà không cần tải ảnh hướng dẫn ngoài.

## Kiểm tra nội dung và đóng gói — output nguyên văn

```text
ARCHIVE CONTENT CHECK: 35 reference-image hashes checked; copied reference PNGs=0; forbidden source-name/code-path matches=0.
PACKAGE: 774 files; 360 frame PNGs; 33 main character rasters; 18 image-generated grip sources; 2 weapon SVGs; ZIP CRC PASS.
Reference-image comparison boards excluded. One occluded biceps midpoint (torso 16) remains explicitly N/A in the report.
```
