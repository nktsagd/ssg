# Phân phối chuẩn & Empirical Rule

> Mức ưu tiên: **CRITICAL** — Nền tảng cho Cp, Cpk, Control Chart

---

## 1. Phân phối chuẩn (Normal Distribution) là gì?

- Phân phối hình chuông (bell-shaped)
- **Đối xứng** quanh giá trị trung bình (mean)
- Diện tích dưới đường cong = 1
- Là phân phối **liên tục**, **đơn đỉnh** (unimodal)
- Tiệm cận trục hoành (asymptotic)

---

## 2. Các tham số cơ bản

| Tham số | Population (tổng thể) | Sample (mẫu) |
|---|---|---|
| Trung bình | μ | X̄ = Σxi / n |
| Phương sai | σ² = Σ(xi−μ)² / N | s² = Σ(xi−X̄)² / (n−1) |
| Độ lệch chuẩn | σ = √σ² | s = √s² |

> **Lưu ý:** Mẫu chia cho **(n−1)**, tổng thể chia cho **N**

---

## 3. QUY TẮC EMPIRICAL (BẮT BUỘC THUỘC)

| Khoảng | % giá trị nằm trong | % nằm ngoài | % mỗi bên đuôi |
|---|---|---|---|
| μ ± 1σ | **68%** | 32% | 16% |
| μ ± 2σ | **95%** | 5% | 2.5% |
| μ ± 3σ | **99.7%** | 0.3% | 0.15% |

### Cách nhớ: 68 – 95 – 99.7

---

## 4. Bài tập mẫu (từ slide)

**Đề:** Công ty sản xuất van có trọng lượng tuân theo phân phối chuẩn: μ = 1.365g, σ = 294g.

**Câu 1:** 95% trọng lượng nằm trong khoảng nào?
> μ ± 2σ = 1.365 ± 2×294 = 1.365 ± 588
> → Từ **777** đến **1.953**

**Câu 2:** Khoảng 16% van nặng hơn bao nhiêu gram?
> 68% nằm trong μ ± 1σ → 32% nằm ngoài → **16% nặng hơn** μ + 1σ
> = 1.365 + 294 = **1.659g**

**Câu 3:** Khoảng 0.15% van nhẹ hơn bao nhiêu gram?
> 99.7% nằm trong μ ± 3σ → 0.3% ngoài → **0.15% nhẹ hơn** μ − 3σ
> = 1.365 − 3×294 = **483g**

---

## 5. Mẹo làm bài

- Thấy **68%** → nghĩ **±1σ**
- Thấy **95%** → nghĩ **±2σ**
- Thấy **99.7%** → nghĩ **±3σ**
- Thấy **16%** → 1 đuôi của ±1σ (100−68)/2 = 16%
- Thấy **2.5%** → 1 đuôi của ±2σ (100−95)/2 = 2.5%
- Thấy **0.15%** → 1 đuôi của ±3σ (100−99.7)/2 = 0.15%
