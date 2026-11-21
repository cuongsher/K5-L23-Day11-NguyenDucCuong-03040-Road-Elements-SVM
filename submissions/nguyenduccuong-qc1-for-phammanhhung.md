# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): phammanhhung        Người kiểm (học viên): nguyenduccuong (Nguyễn Đức Cường)  
Ngày: 21/11/2026                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `phammanhhung-front.zip`, `phammanhhung-fisheye.zip` — revision: ____  
Số ảnh kiểm: 6 (+ 0 ảnh thêm, ghi riêng)   Số nhãn đã kiểm (shape + tag): 108  

Ảnh đã kiểm: A01, A04, A06, A08, B03, B06. Số nhãn = shape + 4 tag mỗi ảnh: A01 10+4, A04 12+4, A06 10+4, A08 34+4, B03 13+4, B06 5+4 = 108.

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 10 | 0 (+1 chờ lead) | nặng |
| QC1-03 position | sai thuộc tính / thừa | 22 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 22 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 22 | 5 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 22 | 1 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 24 | 2 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 11 | 2 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 32 | 1 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 21 | 1 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 18 | 2 | chính |
| QC1-12 file | lỗi file | 2 | 0 | nhẹ / nặng |

Cách đếm số mục kiểm: QC1-01 = 1 tag camera/ảnh; QC1-02 = 2 vị trí L1, R1 trên 4 ảnh front + B03 (B06 là camera hai bên, không áp dụng); QC1-03…06 = 22 polyline lane; QC1-07 = 11 drivable + 8 crosswalk + 5 road_curb ảnh front; QC1-08 = 11 hộp đèn; QC1-09 = 11 đèn + 21 biển; QC1-10 = 21 biển; QC1-11 = 18 nhãn trên B03, B06; QC1-12 = 2 file.

## Danh sách lỗi (mỗi lỗi một dòng)
Nhãn ghi theo thứ tự trong `annotations.xml` của ảnh (#n) kèm toạ độ điểm đầu / góc hộp để tìm trên CVAT.

| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-05 | A01 | lane L2 #2 (0,603) và #3 (0,600) | chính | Vạch đôi trắng bên trái vẽ thành 2 polyline cùng L2 và cả hai đều `kind = double`; phải là 1 polyline trên tâm cặp vạch, `kind = double` |
| 2 | QC1-05 | A04 | lane L1 #7 (66,552) và #8 (28,552) | chính | Vàng đôi vẽ thành 2 polyline cùng L1; phải là 1 polyline `kind = double` |
| 3 | QC1-05 | A04 | lane R2 #5 (1280,516) và #6 (1280,536) | chính | Vạch đôi trắng bên phải vẽ thành 2 polyline cùng R2 |
| 4 | QC1-07 | A04 | drivable #11 (728,536) | chính | Làn bên phải vạch R1 là làn cùng chiều bên cạnh nhưng ghi `area_type = direct`; phải là `alternative` (xe đang đi giữa L1 và R1) |
| 5 | QC1-05 | A06 | lane L1 #8 (455,415) và #9 (440,417) | chính | Vạch L1 tách 2 polyline 2 điểm, mỗi đoạn chỉ ~30 px dù vạch vàng còn thấy xa hơn |
| 6 | QC1-06 | A06 | lane L1 #8, #9 | chính | Vạch là vàng nhưng ghi `color = white`; một đoạn ghi `dashed`, một đoạn `solid`, cả hai `kind = double` |
| 7 | QC1-07 | A06 | drivable #7 (963,702) | chính | Polygon `direct` thứ hai nằm phía sau hàng cột cầu cạn bên phải; vùng sau cọc không thuộc vùng lái |
| 8 | QC1-08 | A06 | traffic_light — thiếu, khoảng (330,140) | chính | Bỏ sót đèn xe cộ treo dưới cầu, đang sáng xanh, quay về xe |
| 9 | QC1-08 | A06 | traffic_light — thiếu, khoảng (545,160) | chính | Bỏ sót đèn xe cộ thứ hai, đang sáng xanh, quay về xe |
| 10 | QC1-10 | A06 | traffic_sign — thiếu, khoảng (685,227) | chính | Bỏ sót biển ONE WAY trên cột (cao > 8 px) |
| 11 | QC1-09 | A06 | traffic_sign #2 (857,321) | chính | Biển hình thoi vàng là biển cảnh báo nhưng ghi `group = other`; phải là `warning` |
| 12 | QC1-05 | A08 | lane R1 #18 (768,453) và #29 (627,290) | chính | R1 tách 2 polyline: đoạn sau vạch ngựa vạn vẽ riêng thay vì nối liền |
| 13 | QC1-11 | B03 | traffic_sign #4 (1131,362)–(1155,401) | chính | Tâm hộp ở ~513 px tính từ tâm ảnh, ngoài 80 % bán kính (512 px) nhưng `edge_zone = false` (sát ngưỡng) |
| 14 | QC1-11 | B03 | traffic_sign #12 (173,301)–(195,326) | chính | Tâm hộp ở ~486 px tính từ tâm ảnh, trong 80 % bán kính nhưng `edge_zone = true` |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A06 | Không có R1. Bên phải làn đang đi là hàng cột cầu cạn, không thấy vạch sơn. Có miễn QC1-02 không? | |
| A08 | L2 vẽ 2 đoạn: đoạn gần `solid`, đoạn xa `dashed`, nối tiếp nhau. Vạch đổi kiểu giữa chừng thì tách 2 polyline có được không? | |
| B03 | Không có lane L1. Vệt đứt mờ ở giữa đường sau xe có phải là L1 cần gán không? | |

Ghi chú ngoài 6 ảnh kiểm:
- File front không có ảnh bắt buộc A09, A10. Không phải lỗi QC1-12 vì file vẫn mở được, nhưng hai ảnh này bị tính là chưa làm.
- Lint còn báo QC1-02 nặng ở A05, A07, A14. Ở A05 có thể không có vạch; cần coach xác nhận.

## Quyết định
Lỗi nặng: 0   Lỗi chính: 14 / 108 nhãn = 13,0 %   Lỗi nhẹ: 0   Ca chờ lead: 3  
Quyết định (Release / Hold / Rework): **Rework**  
Lý do (theo luật của phiếu): Không có lỗi nặng đã xác nhận, nhưng tỉ lệ lỗi chính 13,0 % > 5 % nên phải Rework. Lỗi tập trung ở vạch đôi hoặc vạch đứt bị tách nhiều polyline (QC1-05) và ở A06 (thiếu đèn, thiếu biển, sai màu vạch, vùng lái sau cọc).

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
