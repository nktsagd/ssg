# Control Chart (Biểu đồ kiểm soát)

> Mức ưu tiên: **CRITICAL** — 4 loại chart + 8 dấu hiệu bất thường

---

## 1. Control Chart là gì?

- Công cụ phân biệt **biến động do nguyên nhân chung** (common cause) và **nguyên nhân đặc biệt** (special cause)
- Gồm: **CL** (center line), **UCL** (upper control limit), **LCL** (lower control limit)
- Điểm trong UCL-LCL → **in control** → không cần can thiệp
- Điểm ngoài UCL/LCL → **out of control** → cần điều tra & sửa

---

## 2. Hai nhóm Control Chart

| Nhóm | Loại chart | Dùng khi |
|---|---|---|
| **Variable** (đo lường) | X̄ chart, R chart | Đo được con số (mm, g, cm...) |
| **Attribute** (thuộc tính) | p chart, c chart | Chỉ đếm được (đạt/không đạt, số lỗi) |

---

## 3. X̄ CHART (Mean Chart) — ĐO LƯỜNG

### Mục đích
Theo dõi **giá trị trung bình** của các mẫu theo thời gian

### Công thức
```
X̄̄ = ΣX̄i / k          ← trung bình của tất cả X̄ mẫu (k = số mẫu)
R̄ = ΣRi / k           ← trung bình khoảng biến thiên

CL  = X̄̄
UCL = X̄̄ + A₂ × R̄
LCL = X̄̄ − A₂ × R̄
```
> A₂ tra bảng theo **cỡ mẫu n** (số đơn vị trong mỗi mẫu)

### Các bước vẽ
1. Chọn đặc tính chất lượng cần đo
2. Xác định cỡ mẫu n
3. Thu thập 20-30 mẫu
4. Tính X̄ cho mỗi mẫu
5. Tính R cho mỗi mẫu (R = Xmax − Xmin trong mẫu)
6. Tính X̄̄ và R̄
7. Tra bảng A₂ theo n
8. Tính UCL, LCL → vẽ chart

---

## 4. R CHART (Range Chart) — ĐO LƯỜNG

### Mục đích
Theo dõi **độ biến thiên** (phạm vi) của các mẫu

### Công thức
```
CL  = R̄
UCL = D₄ × R̄
LCL = D₃ × R̄
```
> D₃, D₄ tra bảng theo **cỡ mẫu n**

---

## 5. BẢNG HẰNG SỐ (CẦN NHỚ VỊ TRÍ TRA)

| n (cỡ mẫu) | A₂ | D₃ | D₄ |
|---|---|---|---|
| 2 | 1.880 | 0 | 3.267 |
| 3 | 1.023 | 0 | 2.574 |
| 4 | 0.729 | 0 | 2.282 |
| 5 | 0.577 | 0 | 2.114 |
| 6 | **0.483** | **0** | **2.004** |
| 7 | 0.419 | 0.076 | 1.924 |
| 8 | 0.373 | 0.136 | 1.864 |
| 9 | 0.337 | 0.184 | 1.816 |
| 10 | 0.308 | 0.223 | 1.777 |

> **Lưu ý:** n ≤ 6 thì D₃ = 0 → LCL = 0

---

## 6. Bài tập mẫu: X̄ & R Chart (Washer — từ slide)

**Đề:** Đường kính washer = 5mm, mỗi 10 phút lấy 6 cái, 20 mẫu.

**Kết quả tính:**
```
X̄̄ = 5.00215
R̄ = 0.136
n = 6 → A₂ = 0.483, D₃ = 0, D₄ = 2.004
```

**X̄ Chart:**
```
UCL = 5.00215 + 0.483 × 0.136 = 5.068
LCL = 5.00215 − 0.483 × 0.136 = 4.936
```
→ Mẫu 5, 16 trên UCL; mẫu 11, 19 dưới LCL → **4 mẫu out of control**

**R Chart:**
```
UCL = 2.004 × 0.136 = 0.273
LCL = 0 × 0.136 = 0
```
→ Mẫu 3 vượt UCL → **biến thiên mẫu 3 không chấp nhận được**

---

## 7. p CHART (Proportion Chart) — THUỘC TÍNH

### Mục đích
Theo dõi **tỷ lệ sản phẩm lỗi** trong mỗi mẫu

### Công thức
```
p̂ = n_lỗi / n                    ← tỷ lệ lỗi của 1 mẫu
p̄ = Σp̂ / k                      ← trung bình tỷ lệ lỗi (k mẫu)
q̄ = 1 − p̄

CL  = p̄
UCL = p̄ + 3 × √(p̄ × q̄ / n)
LCL = p̄ − 3 × √(p̄ × q̄ / n)    ← nếu < 0 thì LCL = 0
```

### Bài tập mẫu (Bond paper — từ slide)
```
n = 50, k = 20 mẫu
p̄ = 1.06 / 20 = 0.053
UCL = 0.053 + 3 × √(0.053 × 0.947 / 50) = 0.053 + 0.095 = 0.148
LCL = 0.053 − 0.095 = −0.042 → LCL = 0
```
→ Tất cả 20 mẫu trong giới hạn → **process under control**

---

## 8. c CHART (Count Chart) — THUỘC TÍNH

### Mục đích
Theo dõi **số lỗi trên mỗi đơn vị** (cho phép nhiều lỗi/sản phẩm)

### Công thức
```
c̄ = Σci / i                     ← trung bình số lỗi (i = số đơn vị)

CL  = c̄
UCL = c̄ + 3 × √c̄
LCL = c̄ − 3 × √c̄              ← nếu < 0 thì LCL = 0
```

### So sánh p chart vs c chart

| | p chart | c chart |
|---|---|---|
| Đo gì | **Tỷ lệ** sp lỗi | **Số lỗi** trên sp |
| 1 sp có thể | Lỗi hoặc không | Nhiều lỗi |
| Phân phối | Binomial | **Poisson** |
| Ví dụ | 3/50 sp lỗi = 6% | 1 sp có 5 vết xước |

### Bài tập mẫu (Gauge — từ slide)
```
25 gauges, c̄ = 50/25 = 2
UCL = 2 + 3√2 = 2 + 4.2 = 6.2
LCL = 2 − 3√2 = 2 − 4.2 = −2.2 → LCL = 0
```
→ Không điểm nào vượt giới hạn → **process in control**, trung bình 2 lỗi/sp

---

## 9. TÁM DẤU HIỆU BẤT THƯỜNG (HAY THI)

| Case | Dấu hiệu | Ý nghĩa |
|---|---|---|
| 1 | Điểm **ngoài UCL/LCL** | Out of control rõ ràng |
| 2 | **8+ điểm liên tiếp** cùng phía CL | Shift (dịch chuyển) |
| 3 | **6+ điểm liên tiếp** tăng/giảm | Trend (xu hướng) |
| 4 | **14 điểm liên tiếp** dao động lên xuống sát | Quá ổn định (đáng nghi) |
| 5 | **2/3 điểm** ngoài zone B, cùng phía | Gần mất kiểm soát |
| 6 | **4/5 điểm** ngoài zone C, cùng phía | Gần mất kiểm soát |
| 7 | **15 điểm liên tiếp** trong zone C | Biến thiên quá nhỏ |
| 8 | **8 điểm liên tiếp** 2 phía CL, không điểm nào trong zone C | Biến thiên bất thường |

### Nguyên nhân có thể
1. Thay đổi môi trường
2. Mệt mỏi công nhân
3. Dụng cụ mòn
4. Thay đổi operator/máy
5. Bảo trì
6. Thay đổi kỹ năng công nhân
7. Thay đổi nguyên vật liệu
8. Thay đổi quy trình

---

## 10. Tổng hợp công thức 4 loại chart

| Chart | CL | UCL | LCL |
|---|---|---|---|
| X̄ | X̄̄ | X̄̄ + A₂R̄ | X̄̄ − A₂R̄ |
| R | R̄ | D₄R̄ | D₃R̄ |
| p | p̄ | p̄ + 3√(p̄q̄/n) | p̄ − 3√(p̄q̄/n) |
| c | c̄ | c̄ + 3√c̄ | c̄ − 3√c̄ |
