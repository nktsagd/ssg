# CHEAT SHEET CÔNG THỨC — Chapter 8 (In 1 trang A4)

---

## PHÂN PHỐI CHUẨN
μ ± 1σ = 68% | μ ± 2σ = 95% | μ ± 3σ = 99.7%

## PROCESS CAPABILITY
```
Cp  = (USL − LSL) / 6σ
Cpk = min(CpU, CpL)
CpU = (USL − X̄) / 3σ
CpL = (X̄ − LSL) / 3σ
```
| Cp > 1.68 | 1.33-1.68 | 1.0-1.33 | 0.67-1.0 | ≤ 0.67 |
|---|---|---|---|---|
| Excellence | Good | Acceptable | Bad | Really bad |

## CONTROL CHARTS
| Chart | CL | UCL | LCL |
|---|---|---|---|
| X̄ | X̄̄ | X̄̄ + A₂R̄ | X̄̄ − A₂R̄ |
| R | R̄ | D₄R̄ | D₃R̄ |
| p | p̄ | p̄ + 3√(p̄q̄/n) | p̄ − 3√(p̄q̄/n) |
| c | c̄ | c̄ + 3√c̄ | c̄ − 3√c̄ |

q̄ = 1 − p̄ | Nếu LCL < 0 → LCL = 0

### Hằng số (tra bảng theo n)
| n | A₂ | D₃ | D₄ |
|---|---|---|---|
| 2 | 1.880 | 0 | 3.267 |
| 3 | 1.023 | 0 | 2.574 |
| 4 | 0.729 | 0 | 2.282 |
| 5 | 0.577 | 0 | 2.114 |
| 6 | 0.483 | 0 | 2.004 |
| 7 | 0.419 | 0.076 | 1.924 |
| 8 | 0.373 | 0.136 | 1.864 |
| 9 | 0.337 | 0.184 | 1.816 |
| 10 | 0.308 | 0.223 | 1.777 |

## HISTOGRAM
```
k = √n                                    (số khoảng)
Độ rộng = (Xmax − Xmin) / k               (làm tròn lên)
Giới hạn dưới = Xmin − (đơn vị đo / 2)
```

## SCATTER (hệ số tương quan)
```
r = Sxy / √(Sxx × Syy)
Sxx = Σ(xi−x̄)²  |  Syy = Σ(yi−ȳ)²  |  Sxy = Σ(xi−x̄)(yi−ȳ)
```
| ±0.01-0.1 | ±0.2-0.3 | ±0.4-0.5 | ±0.6-0.7 | ±0.8+ |
|---|---|---|---|---|
| Không đáng kể | Thấp | TB | Cao | Rất cao |

## PARETO: 80% vấn đề ← 20% nguyên nhân
## AQL: Lỗi ≤ P → Accept | Lỗi ≥ F → Reject (F = P+1)
## ISHIKAWA: 4M1E (Man, Material, Machine, Method, Equipment) + 5W1H

## PHƯƠNG SAI & ĐỘ LỆCH CHUẨN
```
Tổng thể: σ² = Σ(xi−μ)²/N        Mẫu: s² = Σ(xi−X̄)²/(n−1)
σ̂ = R̄/d₂   (ước lượng σ từ R̄)
```
