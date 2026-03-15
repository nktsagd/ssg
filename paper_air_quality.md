# Dự Đoán Nồng Độ CO Trong Không Khí Sử Dụng Các Phương Pháp Học Máy: Phân Tích Time-Aware Protocol, Đa Cộng Tuyến và Đặc Tính Phi Tuyến

---

## Tóm Tắt (Abstract)

Chất lượng không khí là một vấn đề môi trường đang được quan tâm sâu sắc. Bài báo này trình bày một quy trình học máy (Machine Learning Pipeline) hoàn chỉnh để phân tích và dự đoán nồng độ CO từ dữ liệu cảm biến khí UCI Air Quality (UCI-360). Mô hình được thiết kế hướng tới việc trả lời hệ thống ba câu hỏi nghiên cứu về: (1) Drift theo thời gian và time-aware protocol; (2) Cách xử lý đa cộng tuyến (multicollinearity) của hệ thống đa cảm biến; (3) Tính hiệu quả của Support Vector Regression (SVR) trên không gian tính năng (feature space) phù hợp. Chúng tôi đề xuất mô hình phân luồng (Dual-Flow Strategy) với tỷ lệ chia Train/Val/Test 60/20/20 để đảm bảo tính khách quan. 

---

## 1. Introduction

**Bối cảnh (Context):** Giám sát ô nhiễm không khí đóng vai trò thiết yếu để đảm bảo sức khỏe cộng đồng và thiết kế đô thị [1]. Ngày nay, mạng lưới cảm biến hạt chi phí thấp (low-cost sensor networks) đang phổ biến nhằm thay thế máy đo đắt tiền [2]. Tuy nhiên, dữ liệu này có đặc thù là nhiễu cao, bị trôi tín hiệu theo thời gian (drift), và đa cộng tuyến giữa nhiều kênh cảm biến.

**Bài toán và Câu hỏi nghiên cứu (Problem/Research question):** 
Nghiên cứu tập trung giải quyết ba vấn đề:
1. Time-aware split có cần thiết do drift theo thời gian không?
2. Ridge/Lasso có tận dụng tốt các kênh sensor tương quan cao không?
3. SVR có cải thiện dự đoán khi quan hệ phi tuyến giữa sensor và target không?

**Giải pháp (Solution):** 
Đề xuất một ML Pipeline có quy trình Time-Aware Protocol kết hợp Ablation Study để bóc tách tính hiệu quả của các feature. Xây dựng chiến lược huấn luyện phân luồng (Dual-Flow): Luồng cơ sở kiểm tra tính chống nhiễu (Ridge/Lasso/MLP) và luồng phi tuyến tối ưu hoá môi trường (SVR).

**Thành tựu đạt được (Achievement):** 
Bài báo đo lường và định lượng thành công mức độ tụt hậu hiệu suất do Drift gây ra (R²=0.66 so với ăn gian random split R²=0.79). Đồng thời chứng minh sức mạnh của SVR-RBF (R²=0.71) vượt OLS (R²=0.66) khi tập trung vào không gian con bao gồm nhiệt độ và độ ẩm.

---

## 2. Related Work

Việc áp dụng hồi quy cho máy học không khí đã được nghiên cứu rộng rãi. Ban đầu, De Vito et al. [2] đã thu thập và giới thiệu chính bộ dữ liệu UCI Air Quality này. Họ dùng Neural Network giản đơn để hiệu chuẩn tín hiệu hóa học. Về kỹ thuật chia dữ liệu, Bergmeir và Benítez [4] nhấn mạnh về sự nguy hiểm của việc rò rỉ dữ liệu (data leakage) khi thực hiện random split hay k-fold thông thường với dữ liệu chuỗi thời gian của IoT.

Với đặc tính đa cộng tuyến do nhiều thiết bị đo lặp (Multicollinearity), Hastie et al. [5] cho thấy Lasso Regression sẽ ép nhiều feature về 0 nhằm loại bỏ sự rườm rà. Đối với tín hiệu phi tuyến, SVR thường được báo cáo thành công [6] bằng việc bẻ cong đặc tuyến bằng kernel trick, tạo động lực để bài viết tinh chỉnh SVR trên luồng dữ liệu môi trường.

---

## 3. Main Contribution

### 3.1 Problem Formulation
Mục tiêu là xây dựng mô hình $f(X)$ dự đoán nồng độ CO(GT) tại thời điểm $t$ thông qua mảng vector dữ liệu từ cảm biến $X_t$. Với giả định hệ thống cảm biến mắc hiện tượng già hóa (drift) $P(X_{t}) \neq P(X_{t+k})$, ta cần thiết kế $f(X)$ hoạt động theo đúng chiều thời gian và chống chịu được nhiễu chéo đa cộng tuyến của ma trận tính năng.

### 3.2 Data Engineering & Preprocessing
Sử dụng bộ dữ liệu UCI-360 [2]. Các giá trị hỏng (`-200`) được chuyển thành rỗng (`NaN`). Loại bỏ feature `NMHC(GT)` do thiếu quá 90%. Thực hiện nội suy trung vị (median imputation) để tạo tính liền mạch cho cảm biến. Trích xuất hai tính năng `hour` và `weekday` để khảo sát chu kỳ sinh hoạt giao thông. Dữ liệu sau đó được chuẩn hóa z-score (StandardScaler) cho các mô hình hồi quy tuyến tính, và RobustScaler đối với SVR để chống chịu dữ liệu ngoại lai (outliers) tốt hơn.

### 3.3 Model Architecture
Bài toán đánh giá trên năm cấu trúc mấu chốt: 
* **OLS Linear Regression:** Mô hình cơ sở (baseline) có đánh giá nhiễu chuẩn.
* **Ridge và Lasso Regression:** Chống Overfitting. Lasso sử dụng nòng cốt giải phương trình L1-norm để triệt tiêu các feature dư thừa; Ridge sử dụng L2-norm thu hẹp biên độ cảm biến tương quan mà không loại đặc trưng nào.
* **SVR (Support Vector Regression - Linear & RBF):** Với siêu tham số (C, gamma) để nắn các đường ranh giới phi tuyến do yếu tố thời tiết quy định.
* **Multi-Layer Perceptron (MLP):** Điển hình cho mô hình học sâu (DL) kiến trúc 2 lớp ẩn (64-32) kèm cơ chế Dropout (0.2) nhằm đối chứng hiệu năng so với các thuật toán ML truyền thống.

### 3.4 Evaluation Metrics
Đánh giá sai số trên 3 chỉ số khắt khe nhất để phản chiếu: 
- Mean Absolute Error (MAE): Tổng sai số tuyệt đối trung bình.
- Root Mean Squared Error (RMSE): Hình phạt nặng các điểm dữ liệu dự đoán lệch cực đoan (outliers do cực đại ô nhiễm/thời tiết lạ).
- Hệ số xác định $R^2$: Mức độ phương sai dữ liệu mà model xử lý được (1.0 là tối đa, <0 mô hình tệ hơn dự báo trung bình).

### 3.5 Training & Validation Strategy
Triển khai kỹ thuật học máy kép qua cấu hình **Time-aware split 60/20/20**:
1. **Luồng 1 (Macro Training - RQ1, RQ2):** Đưa toàn bộ các chiều không gian khí áp $\mathbb{R}^{13}$ bằng StandardScaler. Triển khai OLS, Ridge, Lasso và MLP. Khảo sát Chronological so với Random Split để đánh giá Drift.
2. **Luồng 2 (Subspace Training - RQ3):** Căn cứ vào tương tác hóa tính, cô lập cảm biến đặc thù `PT08.S1`, `PT08.S2` với biến thời tiết (`T`, `RH`, `AH`). Huấn luyện bằng RobustScaler cho SVR.
3. **Ablation:** Khảo sát ảnh hưởng của tính năng thời gian (`hour`, `weekday`) lên Ridge.

---

## 4. Experiment Result

### 4.1 Dataset
- **Mã dữ liệu:** UCI-360 (Air Quality dataset).
- **Kích cỡ:** 9.357 mẫu khí thải đô thị đo mỗi giờ. Data gốc chứa lỗi cảm biến (-200) lên đến hàng ngàn điểm. Sau bước làm sạch và điền khuyết (median imputation), dữ liệu được cấu trúc liên tục thành chuỗi sự kiện đa biến.

**Bức tranh Thiếu Hụt Dữ Liệu (Missingness):**
Hình 1 cho thấy cảm biến `NMHC(GT)` bị thiếu hơn 90% (gạch xóa), buộc phải loại bỏ hoàn toàn khỏi mô hình để tránh nhiễu.
![Hình 1: Tỷ lệ thiếu hụt dữ liệu (Missingness)](figures/fig_missingness.png)

**Hiện tượng Lệch Pha Thời Gian (Drift):**
Ngược với dữ liệu bảng tĩnh, dữ liệu IOT chất lượng không khí bị trôi qua các tháng do cảm biến hóa học già đi. Hình 2 cho thấy giá trị CO bị thay đổi biên độ trung bình và phương sai qua các tháng trong năm. Do đó, việc chia Train/Val/Test tương ứng với 5614/1871/1872 mẫu đã được quyết định theo chiến lược _Time-Aware Protocol_ (60/20/20 nối tiếp thời gian).
![Hình 2: Hiện tượng Sensor Drift theo tháng](figures/fig_drift_analysis.png)

- **Đặc tuyến:** Tốc độ tương quan chéo (Pearson CC) rất cao. Hình 3 mô tả Heatmap của các thiết bị. Nhóm biến như `PT08.S1(CO)` và `PT08.S2(NMHC)` có sự gắn kết cực kì rực rỡ và là thông số có định độ dự báo uy tín nhất đối với CO.
![Hình 3: Ma trận tương quan (Correlation Heatmap)](figures/fig_correlation_heatmap.png)

### 4.2 Result & Comparison

**Bảng 1: Kết quả dự đoán tổng hợp (Dựa trên Chronological Split 60/20/20)**

| Model | Cross-Validation (R²) | Test MAE | Test RMSE | Test R² |
| :--- | :--- | :--- | :--- | :--- |
| **Predict-Mean** | N/A | 1.0134 | 1.3403 | -0.0000 |
| **OLS Linear Regression** | $0.6907 \pm 0.0907$ | 0.5798 | 0.7836 | 0.6582 |
| **Ridge Regression** | $0.7135 \pm 0.0804$ | 0.5230 | 0.7383 | **0.6965** |
| **Lasso Regression** | $0.6880 \pm 0.0762$ | 0.5504 | 0.7231 | **0.7090** |
| **SVR (linear)** | $0.5739 \pm 0.1054$ | 0.4546 | 0.7496 | 0.6872 |
| **SVR (RBF)** | $0.5858 \pm 0.1153$ | 0.4385 | 0.7156 | **0.7149** |
| **MLP (Deep Learning)** | N/A | 1.0722 | 1.2791 | **0.0892** |

#### So sánh theo 3 câu hỏi Nghiên cứu (RQs):
**1. Drift và Time-aware split (RQ1):** 
Ridge với Chronological test cho R² chỉ 0.66 (độ trễ xu hướng đi xuống). Nếu chia tách Random Split truyền thống, R² nhảy vọt lên 0.79. Mức chênh lệch khủng khiếp 13% này minh họa lý do "bắt buộc" phải giả lập Time-aware Protocol nếu muốn triển khai IOT cho chất lượng không khí đô thị không bị ảo tưởng hóa hiệu năng.
![Hình 4: RQ1 — Ảnh hưởng của Time-aware Protocol (Drift)](figures/fig_rq1_split.png)

**2. Đa cộng tuyến qua Ridge và Lasso (RQ2):** 
Mạng lưới cảm biến khí thải ghi nhận mức giao thoa vật lý lớn. Sự dư thừa làm OLS không tốt bằng Ridge (R² 0.69). Thú vị là, Lasso đã tự động ép 8/13 loại tính năng về mức 0 nhằm loại nhiễu rườm rà. Lasso mang lại hiệu năng cao (R²=0.70) bằng số feature ít nhất.
![Hình 5: RQ2 — Xử lý tương quan chéo của Ridge và Lasso](figures/fig_rq2_coefficients.png)

Kèm theo, kết quả **Ablation Time Features:** Mô hình có chứa thuộc tính (hour, weekday) tạo R²=0.6965, mô hình không chứa thu về 0.6921. Mức sai biệt cực kỳ thấp (+0.4%) chứng minh các cảm biến sinh hóa vật lý (như S1, S2) tự thân đã nắm bắt được chu kỳ biến thiên sinh hoạt xe cộ trong ngày.
![Hình 6: Ablation Study — Ảnh hưởng của Time Features lên Ridge](figures/fig_ablation.png)

**3. Sức mạnh phi tuyến với SVR (RQ3):** 

**Bảng 2: Kết quả dự đoán tổng hợp (Luồng 2 - Subset Features: PT08.S1, PT08.S2, T, RH, AH)**

| Model | Cross-Validation (R²) | Test MAE | Test RMSE | Test R² |
| :--- | :--- | :--- | :--- | :--- |
| **Predict-Mean** | N/A | 1.0134 | 1.3403 | -0.0000 |
| **OLS Linear Regression** | $0.5859 \pm 0.0842$ | 0.4875 | 0.7733 | 0.6671 |
| **Ridge Regression** | $0.6081 \pm 0.0824$ | 0.4977 | 0.7796 | 0.6617 |
| **Lasso Regression** | $0.6019 \pm 0.0670$ | 0.5435 | 0.8449 | 0.6026 |
| **SVR (linear)** | $0.5739 \pm 0.1054$ | 0.4546 | 0.7496 | 0.6872 |
| **SVR (RBF)** | $0.5858 \pm 0.1153$ | 0.4385 | 0.7156 | **0.7149** |
| **MLP (Deep Learning)** | N/A | 0.5093 | 0.7699 | 0.6701 |

Hồi quy SVR-RBF với các siêu cực số được hiệu chỉnh, sau khi giải tải khỏi các nhánh cảm biến dư bị đa cộng tuyến, đã bứt phá hoàn toàn so với OLS trên luồng Test môi trường ngẫu nhiên (R²=0.7149 > 0.6671). Sự cách biệt là rõ rệt khi xét theo phân phối nhiệt độ khắc nghiệt cực đoan, chứng minh được Kernel RBF ưu việt ở vùng biên (Extreme Weather Conditions).
![Hình 7: RQ3 — So sánh độ ổn định các mô hình trên Data Subset môi trường](figures/fig_rq3_svr.png)

---

## 5. Discussion

**Thảo Luận:** 
Kết quả thực nghiệm đã khẳng định được ba chân lý khi tiến hành bài toán Regresssion với môi trường IoT: phải chia Test bằng luồng thời gian thực tế, phải xài thuật toán Regularization để cô lập linh kiện hư/trùng rải rác trong môi trường, và phải áp dụng RBF khi biên độ thời tiết biến đổi mạnh ngoài sức chịu đựng của tuyến tính. Lasso có thể định tính làm kim chỉ nam để tối ưu dự án ngân sách phần cứng.
      
**Hạn Chế (Limitation):** 
Nhược điểm của nghiên cứu nằm ở việc SVR quá ngốn tài nguyên (compute-intensive) cũng như chỉ mới phân tách theo môi trường tự nhiên (nhiệt, ẩm). Khảo sát MLP (Deep Learning cơ bản) trên dữ liệu bảng thể hiện sự yếu thế nặng, điều này khơi mào cho việc những hướng thiết kế mô hình nâng cao như LSTMs, Transformers vẫn đang còn để ngỏ cho nghiên cứu trong tương lai.

---

## 6. Conclusion
Nghiên cứu áp dụng quy chuẩn nghiêm ngặt cho bài toán học máy hồi quy khí CO dựa trên Data cảm biến giá rẻ. Hệ thống trả lời ba nan đề mấu chốt: Sự dịch tuyến của bộ máy khi chia bằng Time-Aware; Sức mạnh tiết kiệm feature của Lasso ($R^2=0.70$, cắt 8 tính năng) để giải quyết lộn xộn đa cộng tuyến; và khả năng phòng thủ của SVR ($R^2=0.71$) trước OLS ($R^2=0.65$) khi rơi vào thời tiết khó ngờ. Kiến trúc tổng thể đóng gói trọn vẹn lý thuyết học máy cho việc hiệu chỉnh cảm biến trong đô thị thực tiễn.

---

## Tài Liệu Tham Khảo (References)

[1] World Health Organization, "Ambient (outdoor) air pollution," WHO Fact Sheet, 2022.

[2] S. De Vito, et al., "On field calibration of an electronic nose for benzene estimation in an urban pollution monitoring scenario," *Sensors and Actuators B: Chemical*, 2008.

[3] N. Zimmerman et al., "A machine learning calibration model using random forests to improve sensor performance," *Atmospheric Measurement Techniques*, 2018.

[4] C. Bergmeir and J. M. Benítez, "On the use of cross-validation for time series predictor evaluation," *Information Sciences*, 2012.

[5] T. Hastie, R. Tibshirani, and J. Friedman, *The Elements of Statistical Learning*, 2nd ed. Springer, 2009.

[6] A. Suárez Sánchez, et al., "SVM-based regression model for air quality forecasting," *Environmental Modelling & Software*, 2011.
