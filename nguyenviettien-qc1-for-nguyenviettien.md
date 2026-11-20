# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Nguyễn Viết Tiến        Người kiểm (học viên): Nguyễn Viết Tiến (tự kiểm)  
Ngày: 20/11/2026                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): nguyenviettien-front.zip, nguyenviettien-fisheye.zip (revision 1)  
Số ảnh kiểm: 6 (A01, A04, A05, B01, B03, B05)   Số nhãn đã kiểm (shape + tag): 64 (40 shape + 24 tag)  

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 6 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 11 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 11 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 11 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 11 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 9 | 0 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 3 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 10 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 7 | 0 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 16 | 1 | chính |
| QC1-12 file | lỗi file | 2 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-11 | B03 | road_curb#6@(764,298) | chính | Đoạn road_curb ngắn trên fisheye chỉ có 2 điểm |

*(Ghi chú miễn QC1-02: A05 không có vạch kẻ làn sơn trên mặt đường nên không vẽ L1/R1; A07 bên trái là dải phân cách cứng không có L1; A14 ban đêm bên phải không có vạch dọc R1.)*

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A05 | Đường không có vạch sơn kẻ làn, chỉ có road_curb hai bên thì miễn QC1-02 đúng không? | Được miễn theo CHECKPOINTS.md |

## Quyết định
Lỗi nặng: 0   Lỗi chính: 1 / 64 nhãn = 1.56 %   Lỗi nhẹ: 0   Ca chờ lead: 0  
Quyết định (Release / Hold / Rework): Release  
Lý do (theo luật của phiếu): Không còn lỗi nặng, tỉ lệ lỗi chính 1.56 % <= 5 % số nhãn đã kiểm.  

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](docs/qc_severity_road_v1.0.md).
