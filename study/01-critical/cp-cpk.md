# Năng lực quy trình — Cp & Cpk

> Mức ưu tiên: **CRITICAL** — Dạng bài tính toán chắc chắn thi

---

## 1. Cp — Process Capability (không xét lệch tâm)

### Công thức
```
Cp = (USL − LSL) / 6σ
```
- **USL** = Upper Specification Limit (giới hạn trên)
- **LSL** = Lower Specification Limit (giới hạn dưới)
- **σ** = độ lệch chuẩn (dùng s nếu tính từ mẫu)

### Bảng đánh giá Cp (BẮT BUỘC THUỘC)

| Cp | Đánh giá | Hành động |
|---|---|---|
| > 1.68 | **Excellence** | Ưu tiên đơn giản hóa, giảm chi phí |
| 1.33 < Cp ≤ 1.68 | **Good** | Không cần điều chỉnh |
| 1.0 < Cp ≤ 1.33 | **Acceptable** | Cần ổn định hơn, vẫn có thể ra lỗi |
| 0.67 < Cp ≤ 1.0 | **Bad** | Cần kiểm tra 100%, cải tiến quy trình |
| ≤ 0.67 | **Really bad** | Phải xem xét và cải tiến ngay lập tức |

---

## 2. Cpk — Process Capability có xét lệch tâm

> Cpk cho biết quy trình có **bị lệch** so với tâm hay không

### Cách 1: Dùng k (hệ số lệch tâm)
```
m = (USL + LSL) / 2              ← tâm của spec
k = |2(m − X̄)| / (USL − LSL)    ← hệ số lệch (0 = perfect center)
Cpk = Cp × (1 − k)
```

### Cách 2: Dùng CpU và CpL (HAY DÙNG HƠN)
```
CpU = (USL − X̄) / 3σ            ← năng lực phía trên
CpL = (X̄ − LSL) / 3σ            ← năng lực phía dưới
Cpk = min(CpU, CpL)             ← LẤY GIÁ TRỊ NHỎ HƠN
```

### So sánh Cp vs Cpk
| | Cp | Cpk |
|---|---|---|
| Xét lệch tâm? | Không | Có |
| Luôn ≥ Cpk? | Có | — |
| Khi nào Cp = Cpk? | Khi X̄ nằm đúng tâm (m) | — |

---

## 3. Bài tập mẫu 1 (từ slide — tính Cp)

**Đề:** Sản phẩm FA, quy trình J12. USL = 15cm, LSL = 10cm. Dữ liệu 100 mẫu cho s = 0.69.

**Giải:**
```
Cp = (USL − LSL) / 6s = (15 − 10) / (6 × 0.69) = 5 / 4.14 = 1.21
```
Vì 1.0 < Cp = 1.21 ≤ 1.33 → **Acceptable**

---

## 4. Bài tập mẫu 2 (từ slide — tính Cp VÀ Cpk)

**Đề:** USL = 51cm, LSL = 20cm, X̄ = 50cm, σ = 3cm

**Tính Cp:**
```
Cp = (51 − 20) / (6 × 3) = 31 / 18 = 1.72
```

**Tính Cpk — Cách 1:**
```
m = (51 + 20) / 2 = 35.5
k = |2(35.5 − 50)| / (51 − 20) = |2 × (−14.5)| / 31 = 29/31 = 0.9354
Cpk = 1.72 × (1 − 0.9354) = 1.72 × 0.0646 = 0.111
```

**Tính Cpk — Cách 2:**
```
CpU = (51 − 50) / (3 × 3) = 1/9 = 0.111
CpL = (50 − 20) / (3 × 3) = 30/9 = 3.33
Cpk = min(0.111, 3.33) = 0.111
```

**Nhận xét:** Cp = 1.72 (Excellence) nhưng Cpk = 0.111 (rất tệ) → quy trình **bị lệch tâm nghiêm trọng** (X̄ = 50 rất xa tâm m = 35.5)

---

## 5. Mẹo làm bài

- **Cp cao nhưng Cpk thấp** = quy trình có khả năng nhưng bị lệch tâm
- **Cpk luôn ≤ Cp** — nếu tính ra Cpk > Cp thì sai
- **Cách 2 (min CpU, CpL)** thường nhanh hơn và ít sai hơn
- Đừng quên: σ tính từ mẫu dùng **(n−1)** ở mẫu số
- Ước lượng σ từ R̄: σ̂ = R̄ / d₂ (d₂ tra bảng theo cỡ mẫu)
