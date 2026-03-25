# Bài tập tổng hợp + Lời giải — Chapter 8

> Tất cả bài tập từ slide, sắp xếp theo chủ đề

---

## BÀI 1: Phân phối chuẩn + Empirical Rule

**Đề:** Van có trọng lượng phân phối chuẩn: μ = 1,365g, σ = 294g

a) 95% trọng lượng nằm trong khoảng nào?
b) 16% van nặng hơn bao nhiêu gram?
c) 0.15% van nhẹ hơn bao nhiêu gram?

<details>
<summary><b>👉 Xem lời giải</b></summary>

a) μ ± 2σ = 1,365 ± 2×294 = 1,365 ± 588 → **từ 777 đến 1,953g**

b) 68% trong μ±1σ → 32% ngoài → 16% trên μ+1σ
   = 1,365 + 294 = **1,659g**

c) 99.7% trong μ±3σ → 0.3% ngoài → 0.15% dưới μ−3σ
   = 1,365 − 3×294 = **483g**

</details>

---

## BÀI 2: Tính Cp

**Đề:** Sản phẩm FA, quy trình J12. USL = 15cm, LSL = 10cm. 100 mẫu cho s = 0.69

<details>
<summary><b>👉 Xem lời giải</b></summary>

```
Cp = (USL − LSL) / 6s = (15 − 10) / (6 × 0.69) = 5 / 4.14 = 1.21
```

1.0 < Cp = 1.21 ≤ 1.33 → **Acceptable**

(s được tính từ: s = √(46.8/99) = 0.69)

</details>

---

## BÀI 3: Tính Cp & Cpk

**Đề:** USL = 51cm, LSL = 20cm, X̄ = 50cm, σ = 3cm

<details>
<summary><b>👉 Xem lời giải</b></summary>

**Cp:**
```
Cp = (51 − 20) / (6 × 3) = 31/18 = 1.72  → Excellence
```

**Cpk (Cách 1 — dùng k):**
```
m = (51 + 20)/2 = 35.5
k = |2(35.5 − 50)| / (51 − 20) = 29/31 = 0.9354
Cpk = 1.72 × (1 − 0.9354) = 0.111
```

**Cpk (Cách 2 — dùng CpU, CpL):**
```
CpU = (51 − 50) / (3×3) = 1/9 = 0.111
CpL = (50 − 20) / (3×3) = 30/9 = 3.33
Cpk = min(0.111, 3.33) = 0.111
```

**Nhận xét:** Cp rất cao (1.72) nhưng Cpk rất thấp (0.111) → quy trình bị **lệch tâm nghiêm trọng**

</details>

---

## BÀI 4: Pareto — Lỗi hàn

**Đề:** Từ dữ liệu lỗi quy trình hàn, vẽ biểu đồ Pareto

| Loại lỗi | Số lỗi |
|---|---|
| Que hàn | 28 |
| Vẩy hàn | 19 |
| Thiếu que hàn | 7 |
| Không hàn | 5 |
| Bong que hàn | 4 |
| Khác | 5 |

<details>
<summary><b>👉 Xem lời giải</b></summary>

**Bước 1-4: Sắp xếp giảm dần + tính % tích lũy**

| Loại lỗi | Số lỗi | Tích lũy | % tích lũy |
|---|---|---|---|
| Que hàn | 28 | 28 | 41.2% |
| Vẩy hàn | 19 | 47 | 69.1% |
| Thiếu que hàn | 7 | 54 | 79.4% |
| Không hàn | 5 | 59 | 86.8% |
| Bong que hàn | 4 | 63 | 92.6% |
| Khác | 5 | 68 | 100% |
| **Tổng** | **68** | | |

**Nhận xét:** Que hàn + Vẩy hàn = 69.1% tổng lỗi → ưu tiên cải tiến 2 loại này

**Lưu ý vẽ:** Không khoảng cách giữa cột, đường tích lũy bắt đầu từ đỉnh cột 1

</details>

---

## BÀI 5: Pareto — Before/After Kaizen (In ấn)

**Đề:** So sánh biểu đồ Pareto trước và sau Kaizen cho quy trình in

<details>
<summary><b>👉 Xem lời giải</b></summary>

**TRƯỚC:** Tổng 186 lỗi — Stained (77, 41.4%) + Bleeding (57, 72%)

**SAU:** Tổng 95 lỗi — Bleeding (28, 29.5%) + Misprint (20, 50.5%)

**Nhận xét:** Tổng lỗi giảm 49%. Stained giảm mạnh (77→15). Thứ tự lỗi thay đổi sau Kaizen.

</details>

---

## BÀI 6: Histogram — Kích thước sản phẩm Z

**Đề:** 100 dữ liệu, LSL = 77mm, USL = 82mm

<details>
<summary><b>👉 Xem lời giải</b></summary>

```
Xmax = 82.4, Xmin = 77.5
k = √100 = 10
Độ rộng = (82.4 − 77.5)/10 = 0.49 → 0.5
Giới hạn dưới = 77.5 − 0.1/2 = 77.45
```

| Khoảng | Giá trị | Tần suất |
|---|---|---|
| 1 | 77.45-77.95 | 2 |
| 2 | 77.95-78.45 | 3 |
| 3 | 78.45-78.95 | 6 |
| 4 | 78.95-79.45 | 11 |
| 5 | 79.45-79.95 | 19 |
| 6 | 79.95-80.45 | **23** |
| 7 | 80.45-80.95 | 16 |
| 8 | 80.95-81.45 | 9 |
| 9 | 81.45-81.95 | 7 |
| 10 | 81.95-82.45 | 4 |

**Nhận xét:** Có sản phẩm nằm ngoài USL (khoảng 10: 82.45 > 82)

</details>

---

## BÀI 7: Control Chart đơn giản — Mặt bàn gỗ

**Đề:** L = 52mm, tolerance = ±0.05mm. 10 mẫu, mỗi mẫu X̄ đã cho.

| Mẫu | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|---|---|
| X̄ | 52.01 | 52.00 | 52.02 | 51.99 | 51.96 | 51.97 | 51.96 | 51.98 | 51.97 | 51.96 |

<details>
<summary><b>👉 Xem lời giải</b></summary>

```
X̄̄ = 51.98
UCL = L + 0.05 = 52.05
LCL = L − 0.05 = 51.95
```

**Nhận xét:** Tất cả mẫu nằm trong giới hạn, nhưng giá trị có xu hướng tiến về LCL → cần theo dõi.

</details>

---

## BÀI 8: X̄ & R Chart — Washer

**Đề:** Đường kính washer 5mm, mỗi lần lấy n=6, thu 20 mẫu.

<details>
<summary><b>👉 Xem lời giải</b></summary>

```
X̄̄ = 5.00215,  R̄ = 0.136
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
→ Mẫu 3 vượt UCL → biến thiên quá lớn

</details>

---

## BÀI 9: p Chart — Giấy bond

**Đề:** n = 50, k = 20 mẫu

<details>
<summary><b>👉 Xem lời giải</b></summary>

```
p̄ = 1.06/20 = 0.053,  q̄ = 0.947
UCL = 0.053 + 3√(0.053×0.947/50) = 0.053 + 0.095 = 0.148
LCL = 0.053 − 0.095 = −0.042 → LCL = 0
```

→ Tất cả 20 mẫu trong giới hạn → **process under control**

</details>

---

## BÀI 10: c Chart — Gauge áp suất dầu

**Đề:** 25 gauges, đếm số lỗi trên mỗi gauge

<details>
<summary><b>👉 Xem lời giải</b></summary>

```
c̄ = 50/25 = 2
UCL = 2 + 3√2 = 2 + 4.2 = 6.2
LCL = 2 − 3√2 = 2 − 4.2 = −2.2 → LCL = 0
```

→ Không điểm nào vượt giới hạn → **process in control**, TB 2 lỗi/sp

</details>

---

## BÀI 11: Scatter — Lò nhiệt A

**Đề:** 15 mẫu nhiệt độ vs độ cứng

<details>
<summary><b>👉 Xem lời giải</b></summary>

```
Sxx = 1,725,732
Syy = 57,354
Sxy = 280,149
r = 280,149 / √(1,725,732 × 57,354) = 0.89
```

r = 0.89 → **tương quan dương rất cao** giữa nhiệt độ và độ cứng

</details>
