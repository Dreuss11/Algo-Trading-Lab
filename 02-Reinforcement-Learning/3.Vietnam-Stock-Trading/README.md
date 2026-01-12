# 🇻🇳 Algorithmic Trading System for Vietnam Market (VN30)

[🇻🇳 Tiếng Việt](#vietnamese) | [🇺🇸 English](#english)

---

<a name="vietnamese"></a>
## 🇻🇳 Tổng quan dự án

Dự án này xây dựng một **hệ thống giao dịch thuật toán chuyên biệt cho thị trường Việt Nam**, tập trung vào nhóm cổ phiếu vốn hóa lớn **VN30**.

Khác với các thị trường phát triển (như Mỹ), thị trường Việt Nam (Frontier Market) có những đặc thù rào cản kỹ thuật lớn như **Chu kỳ thanh toán T+** và thanh khoản. Hệ thống này được thiết kế để giải quyết triệt để các vấn đề đó, kết hợp giữa sức mạnh dự đoán của AI và nguyên tắc quản trị rủi ro chặt chẽ.

### 🛠️ Giải pháp Kỹ thuật & Thuật toán

#### 1. Môi trường tùy chỉnh (Custom Environment)
Viết lại hoàn toàn môi trường giao dịch (`StockTradingEnvVietnam`) để thay thế cho môi trường chuẩn của FinRL/Gym:
* **Cơ chế T+ (Settlement T+2.5):** Mô phỏng chính xác việc cổ phiếu mua xong chưa thể bán ngay, và tiền bán xong chưa về tài khoản ngay.
* **Quản lý tài sản chờ (Pending Assets):** Theo dõi dòng tiền/cổ phiếu đang trên đường về, khắc phục hoàn toàn lỗi tính toán "tài sản khống" (phantom assets) thường gặp ở các thư viện mã nguồn mở.

#### 2. Chiến lược lai (Hybrid Strategy)
Kết hợp Deep Reinforcement Learning với Quản trị rủi ro chủ động (Active Risk Management):
* **AI Core:** Sử dụng các thuật toán **PPO, A2C, DDPG** để tìm điểm mua/bán tối ưu dựa trên tín hiệu thị trường.
* **Hard Rules (Quy tắc cứng):** Tự động kích hoạt bất kể AI dự đoán thế nào:
    * **Cắt lỗ (Stop-loss):** -7% (Bảo toàn vốn).
    * **Chốt lời (Take-profit):** +15% (Hiện thực hóa lợi nhuận).
    * **Tỷ trọng tối đa:** Giới hạn 10% vốn cho một mã để tránh rủi ro tập trung.

### 🏗️ Hạ tầng & Vận hành
* **Dữ liệu:** Tích hợp dữ liệu Real-time từ **Vnstock** và **Yfinance**.
* **Audit Logging:** Hệ thống ghi nhật ký giao dịch chi tiết, minh bạch hóa lý do vào lệnh (do tín hiệu AI hay do chạm ngưỡng rủi ro) để phục vụ kiểm toán sau này.
* **Nền tảng:** Google Colab.

### 📊 Kết quả nổi bật
* **Loại bỏ Look-ahead Bias:** Đảm bảo hệ thống không "nhìn thấy tương lai" khi backtest dòng tiền, phản ánh đúng thực tế giao dịch tại Việt Nam.
* **Hiệu quả:** Hệ thống Backtest nâng cao cho thấy khả năng **bảo toàn vốn tốt hơn VN-INDEX** trong các nhịp điều chỉnh sâu nhờ cơ chế cắt lỗ tự động.

### 📚 Tài liệu tham khảo
* **Phương pháp:** Thích ứng (Adaptation) từ mô hình DRL cho thị trường Trung Quốc (A-Share) sang đặc thù thị trường Việt Nam.
* **Nguồn:** *Tutorial "Stock Trading for China A-share Market with FinRL".*

### 🔧 Tech Stack
* **Core:** Python, FinRL, Custom OpenAI Gym Env.
* **AI:** PyTorch, Pandas, NumPy.
* **Data:** Vnstock, Yfinance.

---

<a name="english"></a>
## 🇺🇸 Project Overview

This project builds a specialized **Algorithmic Trading System for the Vietnam Stock Market**, focusing on the **VN30** (Blue-chip) constituents.

Unlike developed markets (e.g., US), the Vietnam market (Frontier Market) presents unique technical challenges such as the **T+ Settlement Cycle** and liquidity constraints. This system is designed to solve these specific issues by combining the predictive power of AI with strict risk management principles.

### 🛠️ Technical Solutions & Algorithms

#### 1. Custom Environment (`StockTradingEnvVietnam`)
Completely re-engineered the trading environment to replace standard FinRL/Gym environments:
* **T+ Settlement Mechanism:** Accurately simulates the T+2.5 cycle where bought stocks cannot be sold immediately, and sold funds are not instantly available.
* **Pending Asset Management:** Tracks assets/cash in transit, completely eliminating the "phantom assets" calculation error common in open-source libraries.

#### 2. Hybrid Strategy
Combines Deep Reinforcement Learning with Active Risk Management:
* **AI Core:** Utilizes **PPO, A2C, DDPG** algorithms to identify optimal entry/exit points.
* **Hard Rules:** Automatically triggered regardless of AI predictions:
    * **Stop-loss:** -7% (Capital preservation).
    * **Take-profit:** +15% (Profit realization).
    * **Max Weight:** Limited to 10% per stock to prevent concentration risk.

### 🏗️ Infrastructure & Operations
* **Data:** Integrated Real-time data from **Vnstock** and **Yfinance**.
* **Audit Logging:** Detailed transaction logging system that clarifies the reason for each order (AI signal vs. Risk threshold trigger) for transparent auditing.
* **Platform:** Google Colab.

### 📊 Key Results
* **Eliminated Look-ahead Bias:** Ensures the system does not "see the future" regarding cash flow during backtesting, accurately reflecting Vietnam's trading reality.
* **Performance:** Advanced backtesting demonstrates superior **capital preservation compared to VN-INDEX** during deep market corrections, thanks to the automated stop-loss mechanism.

### 📚 References
* **Methodology:** Adapted from DRL models for the China A-Share market to fit Vietnam's market specifics.
* **Source:** *Tutorial "Stock Trading for China A-share Market with FinRL".*

### 🔧 Tech Stack
* **Core:** Python, FinRL, Custom OpenAI Gym Env.
* **AI:** PyTorch, Pandas, NumPy.
* **Data:** Vnstock, Yfinance.

---
*Disclaimer: This project is for educational and research purposes only. Not financial advice.*