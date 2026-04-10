# 🏎️ Tesla Stock Price Prediction: An Evolution from Stats to Deep Learning

This project was developed during my **Data Science Remote Internship**. It documents the journey of predicting **$TSLA** stock prices by transitioning from baseline statistical models to complex sequence-based Neural Networks.

## 📌 Project Motivation
Predicting stock prices is a "wicked" problem due to market volatility. The goal of this project was to analyze how different architectures handle time-series data and to understand why "lower error" in training doesn't always mean a "better model" in the real world.

---

## 🛠️ Technical Roadmap

### Phase 1: Statistical Baseline (Linear Regression)
I started with **Linear Regression** to establish a benchmark. 
* **Features:** Open, High, Low, Close, Volume.
* **Result:** Mean Absolute Error (MAE) of **$9.52**.
* **The Catch:** While the error was low, the model suffered from **Lagging**. It essentially predicted that "Tomorrow = Today," which is a common trap in financial modeling.

### Phase 2: Feature Engineering (Momentum Indicators)
To give the AI more context about market "energy," I manually engineered two technical indicators:
* **MA10 (10-Day Moving Average):** To filter out short-term "noise."
* **RSI (Relative Strength Index):** To identify overbought or oversold conditions.
* **Outcome:** These features helped the model recognize trends rather than just raw numbers.

### Phase 3: Deep Learning (LSTM)
I implemented a **Long Short-Term Memory (LSTM)** network via **TensorFlow/Keras**. Unlike regression, LSTMs have "gates" that allow them to remember or forget information over long periods.
* **Data Structure:** A **60-day sliding window**. The model studies two months of history to predict the next day.
* **Preprocessing:** Used `MinMaxScaler` to normalize data between (0,1).
* **Architecture:** * 2 LSTM Layers (50 units each).
    * **Dropout Layers (0.2):** Strategically implemented to prevent overfitting by randomly "turning off" neurons during training.
* **Result:** MAE of **$26.08**. 

---

## 🧠 Key Insight: The "Accuracy Paradox"
A major takeaway from this project is that the **$26.08 error** of the LSTM is more valuable than the **$9.52 error** of the Linear Regression. 
* **Linear Regression** was "cheating" by lagging one day behind. 
* **LSTM** was attempting to model the **volatility** and non-linear patterns of Tesla’s price action. 

---

## 📂 Project Structure
* `TSLA_Prediction.ipynb`: The complete Google Colab notebook with code and visualizations.
* `requirements.txt`: List of dependencies (TensorFlow, Scikit-learn, yfinance).
* `Project_Report.docx`: The detailed internship submission report.

## 🚀 How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/reyaan9900-collab/Tesla-Stock-Prediction.git
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the notebook in Jupyter or Google Colab.

## 🔮 Future Enhancements
* **Sentiment Analysis:** Integrating a Natural Language Processing (NLP) layer to analyze Elon Musk's tweets and news headlines.
* **Multi-Variate Input:** Adding macro-economic indicators (Interest rates, S&P 500 performance) to the LSTM.

---

**Author:** Muhammad Rehan  
