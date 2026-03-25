# Histogram (Biểu đồ phân bố)

> Mức ưu tiên: **CRITICAL** — Quy trình vẽ + nhận biết 7 dạng phân bố

---

## 1. Histogram là gì?

- Biểu đồ cột đứng thể hiện **phân bố** của tập dữ liệu
- Dữ liệu được nhóm thành các **khoảng (class/interval)**
- Giúp thấy hình dạng phân bố, so sánh với specification limits

---

## 2. Các bước vẽ Histogram (6 BƯỚC — BẮT BUỘC THUỘC)

| Bước | Hành động | Công thức |
|---|---|---|
| 1 | Xác định Xmax và Xmin | — |
| 2 | Tính số khoảng k | **k = √n** |
| 3 | Tính độ rộng khoảng | **(Xmax − Xmin) / k** → làm tròn LÊN |
| 4 | Tính giới hạn dưới khoảng đầu | **Xmin − (đơn vị đo / 2)** |
| 5 | Lập bảng tần suất | Đếm số giá trị trong mỗi khoảng |
| 6 | Vẽ histogram | Cột liền nhau, không khoảng cách |

---

## 3. Bài tập mẫu (từ slide)

**Đề:** 100 dữ liệu kích thước sản phẩm Z, LSL = 77mm, USL = 82mm

**Giải:**
```
Bước 1: Xmax = 82.4, Xmin = 77.5
Bước 2: k = √100 = 10 khoảng
Bước 3: Độ rộng = (82.4 − 77.5) / 10 = 0.49 → làm tròn = 0.5
Bước 4: Giới hạn dưới = 77.5 − 0.1/2 = 77.45
```

**Bảng tần suất:**

| Khoảng | Khoảng giá trị | Tần suất |
|---|---|---|
| 1 | 77.45 – 77.95 | 2 |
| 2 | 77.95 – 78.45 | 3 |
| 3 | 78.45 – 78.95 | 6 |
| 4 | 78.95 – 79.45 | 11 |
| 5 | 79.45 – 79.95 | 19 |
| 6 | 79.95 – 80.45 | **23** ← đỉnh |
| 7 | 80.45 – 80.95 | 16 |
| 8 | 80.95 – 81.45 | 9 |
| 9 | 81.45 – 81.95 | 7 |
| 10 | 81.95 – 82.45 | 4 |
| | **Tổng** | **100** |

**Nhận xét:** Có một số sản phẩm nằm ngoài specification limit (USL = 82mm)

---

## 4. BẢY DẠNG PHÂN BỐ CẦN NHẬN BIẾT (HAY THI)

### Dạng 1: Lý tưởng ✅
- Phân bố **đối xứng**, nằm trong SL
- Đỉnh ở giữa, dữ liệu phân bố đều quanh tâm
- → **OK, không cần can thiệp**

### Dạng 2: Lệch một bên + ngoài SL ⚠️
- Mean bị lệch về một phía
- Có sản phẩm ngoài specification limit
- → **Tìm nguyên nhân, cải tiến ngay**

### Dạng 3: Lệch phải (Skewed right) ⚠️
- Phân bố trong SL nhưng **không cân đối**
- Có khả năng lỗi ở phía ngoài SL
- → **Dịch đỉnh về tâm**

### Dạng 4: Phân bố xa tâm ⚠️
- Nằm trong SL nhưng **cách xa SL** cả hai bên
- → **Lỗi đo lường, có thể trộn lẫn sản phẩm khác**

### Dạng 5: Hai đỉnh (Bimodal) ⚠️
- Phân bố có **2 đỉnh**
- → **Trộn lẫn 2 lô / 2 máy khác nhau**

### Dạng 6: Không đều (Irregular) ⚠️
- Phân bố lổn nhổn, không có pattern
- → **Lỗi đo lường, chọn khoảng sai**

### Dạng 7: Bị cắt cụt (Truncated)
- Một bên bị cắt đột ngột
- → Có thể do đã loại bỏ sản phẩm lỗi trước khi đo

---

## 5. Ứng dụng của Histogram

- Xem dữ liệu có **phân phối chuẩn** không
- Kiểm tra quy trình có đáp ứng **yêu cầu khách hàng** không
- So sánh output **giữa các thời kỳ** hoặc **giữa các quy trình**
- Truyền đạt nhanh thông tin về phân bố dữ liệu
