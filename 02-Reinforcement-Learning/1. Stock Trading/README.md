# 📈 Deep Reinforcement Learning for Stock Trading (Dow Jones 30)

[🇻🇳 Tiếng Việt](#vietnamese) | [🇺🇸 English](#english)

---

<a name="vietnamese"></a>
## 🇻🇳 Tổng quan dự án

Dự án này triển khai một **quy trình giao dịch tự động khép kín (End-to-End Pipeline)** áp dụng cho thị trường chứng khoán Mỹ (cụ thể là danh mục **Dow Jones 30**).

Bằng cách tận dụng Học tăng cường sâu (Deep Reinforcement Learning - DRL), hệ thống đóng vai trò là một Agent tự chủ, học cách ra quyết định giao dịch (Mua/Bán/Giữ) trực tiếp từ dữ liệu thị trường nhằm:
* **Loại bỏ yếu tố cảm xúc** trong giao dịch.
* **Tối đa hóa lợi nhuận tích lũy** và tối ưu hóa tỷ lệ Rủi ro/Lợi nhuận.

### 🛠️ Phương pháp & Thuật toán
Dựa trên framework **FinRL** và các nghiên cứu tiên tiến, dự án này triển khai và so sánh hiệu suất của 5 thuật toán DRL hiện đại:
* **A2C** (Advantage Actor-Critic)
* **PPO** (Proximal Policy Optimization)
* **DDPG** (Deep Deterministic Policy Gradient)
* **TD3** (Twin Delayed DDPG)
* **SAC** (Soft Actor-Critic)

Phương pháp luận được tham khảo từ nghiên cứu về tối ưu hóa phân bổ tài sản: *"A Deep Reinforcement Learning Framework for the Financial Portfolio Management Problem"*.

### 🏗️ Kiến trúc hệ thống
Hệ thống vận hành trên môi trường **Google Colab**, sử dụng quy trình khép kín:
1.  **Thu thập dữ liệu:** Lấy dữ liệu lịch sử thông qua **Yahoo Finance API (yfinance)**.
2.  **Kỹ thuật đặc trưng (Feature Engineering):** Xử lý **~150,000 điểm dữ liệu**, tích hợp các chỉ báo kỹ thuật:
    * **Xu hướng:** MACD, ADX.
    * **Động lượng:** RSI, CCI.
3.  **Mô phỏng môi trường:** Sử dụng **FinRL** để giả lập biến động thị trường chứng khoán.
4.  **Đánh giá:** Sử dụng **QuantStats** để đo lường rủi ro và lợi nhuận chi tiết.

### 📊 Kết quả nổi bật
Sau quá trình huấn luyện và kiểm thử (Backtest) trên dữ liệu lịch sử, **Agent TD3** đã cho thấy hiệu suất vượt trội:

| Chỉ số (Metric) | Kết quả | Mô tả |
| :--- | :--- | :--- |
| **Lợi nhuận năm** | **~22.89%** | Vượt trội so với mức cơ sở (Baseline) trong các bài kiểm tra biến động. |
| **Dữ liệu xử lý** | **~150k pts** | Huấn luyện mạnh mẽ trên không gian trạng thái đa chiều. |
| **Tính ổn định** | **Cao** | Duy trì chỉ số Sharpe Ratio ổn định ngay cả khi thị trường đi xuống. |

### 🔧 Công nghệ sử dụng (Tech Stack)
* **Ngôn ngữ:** Python 3.x
* **Thư viện cốt lõi:** FinRL, PyTorch, Pandas, NumPy, Matplotlib.
* **Dữ liệu:** Yahoo Finance API (yfinance).
* **Phân tích:** QuantStats.

### 📚 Tài liệu tham khảo
Dự án này là sự triển khai và mở rộng các khái niệm được trình bày trong:
> *Paper: "Practical Deep Reinforcement Learning Approach for Stock Trading" (NeurIPS 2018 Workshop) - arXiv:1811.07522.*

---

<a name="english"></a>
## 🇺🇸 Project Overview

This project implements an **end-to-end automated trading pipeline** applied to the US Stock Market (specifically the **Dow Jones 30** constituents).

By leveraging Deep Reinforcement Learning (DRL), the system acts as an autonomous agent that learns to make trading decisions (Buy/Sell/Hold) directly from market data, aiming to:
* **Eliminate emotional bias** in trading.
* **Maximize cumulative returns** and optimize the Risk/Reward ratio.

### 🛠️ Methodology & Algorithms
Based on the framework of **FinRL** and state-of-the-art research, this project implements and compares the performance of 5 advanced DRL algorithms:
* **A2C** (Advantage Actor-Critic)
* **PPO** (Proximal Policy Optimization)
* **DDPG** (Deep Deterministic Policy Gradient)
* **TD3** (Twin Delayed DDPG)
* **SAC** (Soft Actor-Critic)

The implementation references the methodology for asset allocation optimization from the study: *"A Deep Reinforcement Learning Framework for the Financial Portfolio Management Problem"*.

### 🏗️ System Architecture
The system operates on **Google Colab**, utilizing a closed-loop pipeline:
1.  **Data Ingestion:** Fetching historical data via **Yahoo Finance API (yfinance)**.
2.  **Feature Engineering:** Processing **~150,000 data points** and integrating technical indicators:
    * **Trend:** MACD, ADX.
    * **Momentum:** RSI, CCI.
3.  **Environment Simulation:** Using **FinRL** to simulate stock market dynamics.
4.  **Evaluation:** Using **QuantStats** for detailed risk/return metrics.

### 📊 Key Results
After training and backtesting on historical data, the **TD3 Agent** demonstrated superior performance:

| Metric | Result | Description |
| :--- | :--- | :--- |
| **Annual Return** | **~22.89%** | Outperforming the baseline in volatility tests. |
| **Data Volume** | **~150k pts** | Robust training on high-dimensional state spaces. |
| **Stability** | **High** | Maintained a stable Sharpe Ratio during market downturns. |

### 🔧 Tech Stack
* **Language:** Python 3.x
* **Core Libs:** FinRL, PyTorch, Pandas, NumPy, Matplotlib.
* **Data Source:** Yahoo Finance API (yfinance).
* **Analysis:** QuantStats.

### 📚 References
This project is an implementation and extension of concepts presented in:
> *Paper: "Practical Deep Reinforcement Learning Approach for Stock Trading" (NeurIPS 2018 Workshop) - arXiv:1811.07522.*

---
*Disclaimer: This project is for educational and research purposes only. Not financial advice.*