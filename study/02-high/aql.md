# AQL — Acceptable Quality Level

> Mức ưu tiên: **HIGH** — Đọc bảng + ra quyết định Accept/Reject

---

## 1. AQL là gì?

- AQL = **mức phần trăm lỗi tối đa** chấp nhận được trong mẫu
- Dùng để trả lời: "Chất lượng sản xuất đang ở mức nào?"
- Người mua & người bán **thỏa thuận trước** mức AQL trong hợp đồng
- Nếu khách không chỉ định AQL → dùng AQL mặc định của công ty (ví dụ NBC dùng 1.5%)

---

## 2. Cách đọc bảng AQL

Bảng AQL cho 3 giá trị:
- **n** = cỡ mẫu (số sản phẩm kiểm tra)
- **P** = số chấp nhận (acceptance number) — số lỗi tối đa để Accept
- **F** = số từ chối (rejection number) — số lỗi tối thiểu để Reject

| | AQL 0.65% | AQL 1.0% | AQL 1.5% | AQL 2.5% |
|---|---|---|---|---|
| **Lô 281-500** | n=80, P=1, F=2 | n=50, P=1, F=2 | n=50, P=2, F=3 | n=20, P=1, F=2 |
| **Lô 501-1200** | n=80, P=1, F=2 | n=80, P=2, F=3 | n=80, P=3, F=4 | n=32, P=2, F=3 |
| **Lô 1201-3200** | n=125, P=2, F=3 | n=125, P=3, F=4 | n=125, P=5, F=6 | n=50, P=3, F=4 |

### Quy tắc quyết định
```
Số lỗi tìm được ≤ P  →  ACCEPT (chấp nhận lô)
Số lỗi tìm được ≥ F  →  REJECT (từ chối lô)
```

---

## 3. Bài tập mẫu (từ slide)

**Đề:** Công ty đặt linh kiện điện tử, lô 1000 sản phẩm, AQL = 1%

**Giải:**
1. Lô 1000 → nằm trong khoảng 501-1200
2. AQL = 1.0% → tra bảng: **n = 80, P = 2, F = 3**
3. Quy trình: kiểm tra **80 sản phẩm**
   - Nếu ≤ 2 sản phẩm lỗi → **Accept**
   - Nếu ≥ 3 sản phẩm lỗi → **Reject**

---

## 4. Lưu ý quan trọng

- Mẫu phải được chọn **ngẫu nhiên** từ toàn bộ lô
- AQL **thấp hơn** = yêu cầu chất lượng **cao hơn**
- F = P + 1 (luôn luôn)
