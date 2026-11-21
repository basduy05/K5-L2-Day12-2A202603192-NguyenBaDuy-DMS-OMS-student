# Danh sách lớp v0 — Nguyễn Bá Duy · G07

## DMS (6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | eye_state (left/right) | open / closed / unknown | Phát hiện tài xế buồn ngủ (vi giật ngủ - microsleep, nhắm mắt kéo dài > 1.5s) | Có, nhưng bị loá bởi đốm phản xạ LED trên tròng kính cận |
| 2 | gaze_zone | road, mirror_l, mirror_r, mirror_c, cluster, center, lap, other | Cảnh báo mất tập trung (nhìn điện thoại ở đùi lap, nhìn màn hình center > 2s khi xe chạy) | Có, ước lượng qua vector hướng đầu kết hợp vị trí con ngươi |
| 3 | head_pose (yaw/pitch/roll) | Góc độ (-90° đến +90°) | Giám sát hướng chú ý tổng thể; cảnh báo khi yaw lệch khỏi road quá 30° liên tục | Rất rõ trên NIR nhờ tương phản khối hình học khuôn mặt |
| 4 | hand_on_wheel | yes / no / unknown | Giám sát sẵn sàng tiếp quản quyền lái (Hands-On Detection) trong xe tự lái L2/L3 | Rõ viền tay, nhưng dễ nhầm nếu tay tựa hờ gần vô lăng |
| 5 | phone_interaction | held / mounted / lap / none | Phát hiện hành vi sử dụng điện thoại trái phép khi đang lái xe | Nhìn thấy viền thiết bị; không thấy màu màn hình hiển thị |
| 6 | impairment_behavior | smoking, drinking, eating, none | Phát hiện hành vi xao nhãng nguy cơ cao dẫn đến phản xạ chậm khi gặp sự cố | Thấy hình dạng điếu thuốc/chai nước qua bóng đổ NIR |

## OMS (6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | seat_occupancy | empty, adult, child, infant, object | Điều khiển bung túi khí thông minh (Smart Airbag Deployment) theo đối tượng | Có, nhận diện qua khối hình học và biên dạng thân nhiệt/NIR |
| 2 | seatbelt_status | worn_correct, worn_incorrect, not_worn, unknown | Nhắc nhở thắt dây an toàn từng ghế; kích hoạt cảnh báo âm thanh và siết đai chủ động | Thấy đường viền dây đai nếu tương phản tốt với áo |
| 3 | child_presence_detection | present, absent | Cảnh báo bỏ quên trẻ em trong xe (CPD) chống sốc nhiệt tử vong | Nhận diện được khối chuyển động hoặc hình dạng nôi xách |
| 4 | child_seat_orientation | rear_facing, front_facing, unknown | Tự động tắt túi khí ghế trước nếu ghế trẻ em quay về sau (tránh túi khí nổ vào đầu bé) | Rất rõ kết cấu khung ghế trẻ em trên IR |
| 5 | left_behind_objects | bag, phone, laptop, wallet, other | Cảnh báo người dùng để quên đồ vật giá trị trong xe khi tắt máy khoá cửa | Thấy hình dạng khối vật thể trên ghế hoặc sàn xe |
| 6 | passenger_posture | normal, lying_down, feet_on_dash, out_of_position | Cảnh báo tư thế ngồi không an toàn (OutOfPosition) làm tăng chấn thương khi bung túi khí | Nhận diện rõ vị trí các chi và khung xương người trên ghế |

## 2 câu hỏi leo thang

1. Câu hỏi: Khi tài xế đeo kính râm chống chói, mắt người nhìn bên ngoài thấy tròng kính tối đen, nhưng dưới camera NIR bước sóng 940nm tròng kính lại trở nên trong suốt và quan sát rõ con ngươi. Vậy trường `glasses` nên ưu tiên gán theo bản chất vật lý quang học (`glasses = sun`) hay theo thuộc tính thị giác camera ghi nhận (`glasses = clear`)?
   Khung ví dụ: D03.png
   Bạn tạm gán thế nào và vì sao: Tạm gán `glasses = sun` vì hệ thống DMS cần biết tài xế đang đeo kính râm để hiệu chỉnh thuật toán ước lượng gaze zone phù hợp với điều kiện ánh sáng chói ngoài trời.

2. Câu hỏi: Trên hàng ghế sau của mô phỏng SVIRO (BMW X5), khi có một tấm chăn hoặc áo khoác phủ kín hoàn toàn ghế trẻ em khiến camera không thể quan sát được bên trong có trẻ hay không, thì box nên được gán là `child_seat` (`occupied = unknown`) hay phải gán là `object` (`type = other`) trùm bên ngoài?
   Khung ví dụ: S04_rgb.png / S04_ir.png (ghế rear_left)
   Bạn tạm gán thế nào và vì sao: Tạm gán 1 box `child_seat` (`occupied = unknown`) bao toàn bộ khung ghế và 1 box `object` (`type = other`) cho tấm vải che để không làm mất tín hiệu ưu tiên an toàn sinh mạng của hệ thống cảnh báo trẻ em (CPD).
