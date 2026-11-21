# TEAM — Ngày 12

Mã bộ ảnh: **G07** · Hình thức: nhóm / cá nhân

| Họ tên | MSSV | Đã gán đủ 22 ảnh? | Review chéo với (peer diff) | Số dòng disagreement đã xử lý |
|---|---|---|---|---|
| Nguyễn Bá Duy | 2A202603192 | có | Hoàng Nhật Anh (2A202603183) | 47 |

Ca hai bạn vẫn không thống nhất và đã hỏi coach (ghi tên ảnh + đối tượng):

- **D04.png (mắt tài xế):** Hoàng Nhật Anh gán `eye_left/eye_right = unknown` nhưng các điểm keypoint mắt không có cờ occluded (bị cảnh báo WARN trong check_final.txt). Nhóm đã thống nhất theo quan sát của Nguyễn Bá Duy: nhìn thấy rõ khe mắt mở nên gán `eye = open`, không bật cờ occluded.
- **S02 / S08 (phân loại ghế):** Thảo luận về việc phân loại `child_seat` (ghế trẻ em có tựa lưng) hay `infant_seat` (nôi xách): thống nhất theo cấu trúc hình học của mô hình 3D SVIRO.

## Cá nhân

Mỗi người một mục, 1–2 dòng mỗi ý.

### NguyenBaDuy-2A202603192
- Phần mình làm: Gán đủ 22 ảnh cốt lõi (16 OMS + 6 DMS) và 4 ảnh mở rộng S09-S10. Chạy script cabin_check diff đối chiếu 47 điểm khác biệt với bạn Hoàng Nhật Anh, hoàn thiện export_final_v2.zip đạt 0 lỗi 0 cảnh báo.
- Điều mình học được hôm nay: Nắm vững hệ quy chiếu cabin (ghế theo xe, trái phải theo người lái trên ảnh xoay 90°), hiểu sâu sắc cơ chế quang học của camera NIR 940nm và tầm quan trọng của việc đối chiếu chéo (QC) trong gán nhãn dữ liệu xe tự hành.
