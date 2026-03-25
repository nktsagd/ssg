# Scatter Chart (Biểu đồ phân tán)

> Mức ưu tiên: **MEDIUM** — Tính hệ số tương quan r

---

## 1. Scatter Chart là gì?

- Đồ thị 2 chiều vẽ cặp điểm (X, Y) để xem **mối quan hệ** giữa 2 biến
- Trục X = nguyên nhân (cause), trục Y = kết quả (effect)

> **Lưu ý quan trọng:** Tương quan (correlation) ≠ Nhân quả (causation)

---

## 2. Các bước vẽ

1. Thu thập dữ liệu cặp (X, Y)
2. Vẽ X lên trục hoành, Y lên trục tung
3. Đánh dấu từng cặp điểm
4. Nếu điểm trùng → khoanh tròn hoặc đặt chấm bên cạnh
5. Tính hệ số tương quan r
6. Diễn giải

---

## 3. Công thức hệ số tương quan r

```
Sxx = Σ(xi − x̄)²
Syy = Σ(yi − ȳ)²
Sxy = Σ(xi − x̄)(yi − ȳ)

r = Sxy / √(Sxx × Syy)
```

---

## 4. Bảng diễn giải r (CẦN NHỚ)

| Giá trị r | Ý nghĩa |
|---|---|
| ±0.01 ~ ±0.1 | **Không đáng kể** (negligible) |
| ±0.2 ~ ±0.3 | **Thấp** (low) |
| ±0.4 ~ ±0.5 | **Trung bình** (moderate) |
| ±0.6 ~ ±0.7 | **Cao** (high) |
| ±0.8 trở lên | **Rất cao** (very high) |

### Hướng tương quan
- **r > 0:** Tương quan dương (X tăng → Y tăng)
- **r < 0:** Tương quan âm (X tăng → Y giảm)
- **r ≈ 0:** Không tương quan

---

## 5. Bài tập mẫu (Lò A — từ slide)

**Đề:** Nhiệt độ xử lý nhiệt vs Độ cứng (Hv) của lò A, 15 mẫu

**Tính toán:**
```
Sxx = 1,725,732
Syy = 57,354
Sxy = 280,149

r = 280,149 / √(1,725,732 × 57,354) = 0.89
```

**Nhận xét:** r = 0.89 → **tương quan dương rất cao** giữa nhiệt độ và độ cứng
