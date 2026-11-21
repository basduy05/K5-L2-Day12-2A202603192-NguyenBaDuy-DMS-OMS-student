# Tự đánh giá — Nguyễn Bá Duy · G07

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_rgb.png | child_seat (booster) | seat_flip | Nhầm ghế bên trái ảnh là rear_middle | Đã sửa thành rear_right theo bạn Nhật Anh |
| S02_rgb.png | person | seat_flip | Người ngồi bên phải ảnh nhầm là rear_right | Đã sửa thành rear_left theo quy tắc xe |
| D01.png | hand | lr_flip | Nhầm 2 bàn tay đều để side=left | Đã sửa 1 tay sang right |
| D04.png | face | ok | Thấy rõ khe mí mắt nên gán open, chuẩn hơn bạn Nhật Anh (bị WARN unknown) | Đã kiểm tra ok |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Gọi vị trí ghế theo mắt nhìn trên ảnh thay vì theo quy chiếu của xe (camera nhìn về sau nên trái ảnh là bên phải xe `rear_right`, phải ảnh là bên trái xe `rear_left`).

Vì sao mình mắc: Thói quen phản xạ tự nhiên khi nhìn màn hình mà chưa đặt mình vào vị trí người lái nhìn về phía sau xe.

Lần sau tránh bằng cách: Luôn tự nhủ nguyên tắc "Đứng cùng chiều xe: Trái ảnh = Phải xe" trước khi đặt thuộc tính `seat` cho hàng ghế sau.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó:
Ở các ảnh S02_rgb, S03_ir, S04_ir... bạn Hoàng Nhật Anh xác định đúng vị trí ghế theo xe (vật/người bên phải màn hình thuộc ghế `rear_left`, bên trái màn hình thuộc ghế `rear_right`). Sau khi chạy lệnh diff và cùng bạn đối chiếu mục 4.4-3 của guideline, mình đã nhận ra và sửa lại toàn bộ sang `export_final_v2.zip`, giúp file v2 đạt tuyệt đối 0 lỗi 0 cảnh báo.
