# Báo cáo cá nhân — Ngày 11
Họ tên: Nguyễn Viết Tiến               Mã học viên: 03140
Phiên bản CVAT (Help → About): CVAT local (v2.x)
Guideline: Road v1.0    Lần nộp (`revision` trong manifest): 1
Thời điểm export (ngày giờ trên CVAT): 20/11/2026 21:05    Số lần nộp lại sau Rework: 0

## 1. Kiểm project
| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | Đúng | Đã nạp từ configs/road_v1_labels.json (lane, road_curb, crosswalk, drivable, traffic_light, traffic_sign) |
| Thuộc tính và giá trị | Đúng | Đủ các select và checkbox edge_zone theo taxonomy |
| 4 tag ảnh | Đúng | camera, timeofday, weather, source đều dùng thuộc tính select tên value |

Cách kết thúc polyline trên bản CVAT này: Bấm phím N (hoặc click đúp vào điểm cuối) sau khi chấm các điểm từ gần ra xa.
Cách đặt tag ảnh trên bản CVAT này: Chọn công cụ Tag ở thanh bên trái, chọn label (camera, timeofday, weather, source) rồi mở Details chỉnh lại giá trị.

## 2. Số lượng đã gán
| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 29 | 4 | 3 | 23 | 20 | 12 |
| front-extra (đã làm 4 / 4) | 4 | 10 | 0 | 4 | 9 | 6 | 10 |
| fisheye | 8 | 8 | 12 | 8 | 6 | 3 | 5 |
| fisheye-extra (đã làm 4 / 4) | 4 | 2 | 4 | 3 | 3 | 0 | 0 |

## 3. Bảng ca khó
| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
| --- | --- | --- | --- | --- |
| A05 | lane | Có nên tự ước lượng vẽ L1/R1 hay bỏ trống | Không vẽ L1/R1, chỉ vẽ road_curb hai bên | Đường phố không có vạch sơn kẻ làn, hai bên là xe đỗ sát vỉa hè. Ghi nhận miễn QC1-02 |
| A07 | lane | Vẽ L1 dọc rào chắn hay dùng road_curb | Chỉ vẽ road_curb bên trái, không vẽ L1 | Bên trái là dải phân cách bê tông sát mép đường, không có vạch sơn L1. Ghi nhận miễn QC1-02 |
| A14 | lane | Vẽ R1 hay bỏ qua | Không vẽ R1 | Ảnh ban đêm, phía bên phải là vỉa hè tối và vạch dừng ngang, không thấy vạch làn dọc R1 |
| B11 | lane | Gán lane cho các vạch trắng/vàng trong bãi đỗ hay không | Không gán lane, chỉ vẽ drivable và road_curb | Các vạch kẻ trên mặt sân là vạch ô đỗ xe, không phải vạch chia làn giao thông (tránh bẫy QC1-03) |
| B03, B04 | drivable | Cắt polygon ở mép dưới ảnh hay mép thân xe | Cắt dừng ở mép cản sau xe mình | Guideline quy định không bao gồm phần thân xe mình vào vùng lái được |

## 4. Phiếu QC 1 nhận được
Bạn kiểm lô của tôi: Nguyễn Viết Tiến (tự kiểm)  Quyết định nhận được: Release (đã sửa 4 lỗi từ vòng tự kiểm trước khi tạo manifest)

*(Ghi chú tự kiểm trước khi nộp: Khi chạy road_check lint lần đầu trên 4 file export, phát hiện 3 lỗi QC1-03 ở B05, B07, B08 do quên đổi position thành other trên camera hai bên, và 1 lỗi QC1-04 ở A10 do polyline vẽ ngược chiều. Đã mở lại CVAT sửa toàn bộ 4 lỗi này và export lại trước khi gộp file và tạo manifest.)*

| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
| --- | ---: | --- | --- |
| QC1-03 (tự kiểm) | 3 | Đồng ý | Đã sửa thành position = other |
| QC1-04 (tự kiểm) | 1 | Đồng ý | Đã đảo chiều vẽ từ gần ra xa ở A10 |

## 5. Kiểm file export
| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | --- | --- | --- | --- |
| nguyenviettien-front.zip | Có | 8 / 8 (A01) | 7 / 7 (A02) | Có (đủ 16/16 ảnh) |
| nguyenviettien-fisheye.zip | Có | 5 / 5 (B01) | 6 / 6 (B02) | Có (đủ 12/12 ảnh) |

## 6. Ảnh chụp màn hình
![alt text](<Screenshot 2026-11-20 212528.png>)
![alt text](<Screenshot 2026-11-20 212148-1.png>) 
![alt text](<Screenshot 2026-11-20 212118-1.png>)
![XML polyline lane](Screenshot-xml-polyline-lane.png)

## 7. Tự đánh giá
Lỗi bạn mắc nhiều nhất hôm nay (theo mã QC1-xx), và cách tránh ở Ngày 20:
Lỗi dễ mắc nhất hôm nay là quên chỉnh thuộc tính mặc định của CVAT sau khi vẽ (nhất là QC1-03 khi vẽ lane trên camera hai bên fisheye bị giữ mặc định L1 thay vì đổi sang other, và QC1-11 đặt hơi ít điểm trên các đoạn ngắn của fisheye). Ở Ngày 20, tôi sẽ tập thói quen vẽ xong mỗi đường là mở ngay Details kiểm tra lại toàn bộ thuộc tính và chạy road_check lint ngay sau khi export.

Nhãn của bạn đi vào model ở đâu? Chọn một lỗi đã sửa và nói nó làm model học sai thế nào:
Nhãn lane (polyline) và drivable (polygon) là ground truth để huấn luyện các mô hình phát hiện làn đường (như lane detection dạng row-anchor) và phân vùng mặt đường đi được cho hệ thống giữ làn (LKA). Nếu để sót lỗi QC1-03 (nhầm lane ở camera hai bên thành L1 thay vì other), mô hình sẽ hiểu nhầm vạch đường nằm ngang bên hông xe là vạch giới hạn bên trái của làn xe đang đi, dẫn đến dự đoán sai vị trí làn và tính toán góc đánh lái lệch khi xe vào giao lộ.

## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor
*(Phần tùy chọn không tính điểm)*
