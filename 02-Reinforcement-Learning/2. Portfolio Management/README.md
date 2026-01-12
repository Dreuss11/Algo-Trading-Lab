# 📊 AI-Based Portfolio Management System (Dow Jones 30)

[🇻🇳 Tiếng Việt](#vietnamese) | [🇺🇸 English](#english)

---

<a name="vietnamese"></a>
## 🇻🇳 Tổng quan dự án

Dự án này xây dựng một hệ thống **tự động tối ưu hóa phân bổ tài sản (Asset Allocation)** cho danh mục đầu tư gồm 29 mã cổ phiếu thuộc chỉ số **Dow Jones 30**.

Khác với giao dịch cổ phiếu đơn lẻ, hệ thống này tập trung vào bài toán quản lý danh mục: Tự động tính toán và điều chỉnh tỷ trọng (weights) của từng mã cổ phiếu để cân bằng tối ưu giữa **Rủi ro và Lợi nhuận** trong môi trường thị trường biến động.

### 🛠️ Phương pháp & Thuật toán
Hệ thống áp dụng Deep Reinforcement Learning (DRL) với các kỹ thuật nâng cao:
* **Thuật toán:** So sánh hiệu quả giữa hai thuật toán Policy Gradient hiện đại là **PPO** (Proximal Policy Optimization) và **A2C** (Advantage Actor-Critic).
* **Không gian trạng thái (State Space):** Được thiết kế đặc biệt, tích hợp thêm:
    * **Ma trận Hiệp phương sai (Covariance Matrix):** Để Agent hiểu mối tương quan biến động giữa các mã.
    * **Chỉ số hỗn loạn (Turbulence Index):** Giúp Agent nhận diện rủi ro hệ thống (khủng hoảng thị trường) để phòng thủ kịp thời.

### 🏗️ Kiến trúc hệ thống
* **Môi trường:** Google Colab.
* **Mô phỏng:** Sử dụng **FinRL** để tạo môi trường `StockPortfolioEnv`.
* **Đánh giá:** Sử dụng **QuantStats** để Backtest và so sánh với chỉ số Dow Jones (DJI).

### 📊 Kết quả nổi bật (2023 - 2025)
Sau quá trình huấn luyện và kiểm thử trên dữ liệu thực tế, chiến lược sử dụng **PPO** đã cho kết quả vượt trội:

| Tiêu chí | PPO Agent | A2C Agent | Ghi chú |
| :--- | :--- | :--- | :--- |
| **Lợi nhuận đầu tư** | **$1,000,000 ➝ $1,380,282** | Thấp hơn PPO | Tăng trưởng ~38% |
| **Sharpe Ratio** | **~1.26** | ~1.19 | Hiệu suất điều chỉnh rủi ro tốt hơn |
| **Tính ổn định** | **Cao** | Trung bình | Duy trì tăng trưởng ngay cả khi thị trường rung lắc |

### 🔧 Công nghệ sử dụng (Tech Stack)
* **Ngôn ngữ:** Python 3.x
* **Thư viện AI/Finance:** FinRL, PyTorch, Pandas, NumPy.
* **Dữ liệu:** Yahoo Finance API (yfinance).
* **Trực quan hóa & Backtest:** QuantStats, Matplotlib.

### 📚 Tài liệu tham khảo
Dự án được xây dựng dựa trên nghiên cứu nền tảng:
> *Paper: "FinRL: A Deep Reinforcement Learning Library for Automated Stock Trading in Quantitative Finance" (NeurIPS 2020) - arXiv:2011.09607.*

---

<a name="english"></a>
## 🇺🇸 Project Overview

This project develops an **automated asset allocation system** for a portfolio consisting of 29 constituent stocks of the **Dow Jones 30** index.

Unlike single-stock trading, this system focuses on Portfolio Management: Automatically calculating and adjusting the **weights** of each stock to achieve an optimal balance between **Risk and Return** in dynamic market conditions.

### 🛠️ Methodology & Algorithms
The system leverages Deep Reinforcement Learning (DRL) with advanced techniques:
* **Algorithms:** Comparative analysis between two state-of-the-art Policy Gradient algorithms: **PPO** (Proximal Policy Optimization) and **A2C** (Advantage Actor-Critic).
* **State Space Engineering:** Enhanced with:
    * **Covariance Matrix:** Allowing the Agent to understand the correlation between assets.
    * **Turbulence Index:** Enabling the Agent to detect systemic risk (market crashes) and adjust strategies accordingly.

### 🏗️ System Architecture
* **Environment:** Google Colab.
* **Simulation:** Utilizing **FinRL** to build the `StockPortfolioEnv`.
* **Evaluation:** Using **QuantStats** for backtesting and benchmarking against the Dow Jones Index (DJI).

### 📊 Key Results (2023 - 2025)
After training and backtesting on real-world data, the **PPO Strategy** demonstrated superior performance:

| Metric | PPO Agent | A2C Agent | Notes |
| :--- | :--- | :--- | :--- |
| **Capital Growth** | **$1,000,000 ➝ $1,380,282** | Lower than PPO | ~38% Return |
| **Sharpe Ratio** | **~1.26** | ~1.19 | Superior risk-adjusted return |
| **Stability** | **High** | Medium | Consistent growth during market volatility |

### 🔧 Tech Stack
* **Language:** Python 3.x
* **AI/Finance Libs:** FinRL, PyTorch, Pandas, NumPy.
* **Data Source:** Yahoo Finance API (yfinance).
* **Backtesting:** QuantStats, Matplotlib.

### 📚 References
This project is based on the foundational research:
> *Paper: "FinRL: A Deep Reinforcement Learning Library for Automated Stock Trading in Quantitative Finance" (NeurIPS 2020) - arXiv:2011.09607.*

---
*Disclaimer: This project is for educational and research purposes only. Not financial advice.*