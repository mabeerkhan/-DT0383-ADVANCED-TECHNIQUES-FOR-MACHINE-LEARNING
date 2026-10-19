## 📈 NVIDIA Stock Market Analysis Using a Feeling Machine

### 📌 Project Overview

This project explores the application of the **Feeling Machine concept to financial time-series data**, using historical NVIDIA (NVDA) stock prices. The objective is to represent changing market conditions through interpretable states based on price trends, volatility, and sudden market movements.

The implementation uses a rule-based approach to classify market conditions into different feeling states and analyze how these states evolve over time.


### 🛠️ Methodology & Implementation

**1. Data Loading and Preprocessing**
- Loaded historical NVIDIA stock-price data from a CSV file using Pandas.
- Converted dates into datetime format and sorted observations chronologically.
- Prepared closing prices for time-series analysis.

**2. Financial Feature Engineering**
- Calculated daily percentage returns and logarithmic closing prices.
- Estimated price trends using a rolling linear-regression slope over a 20-observation window.
- Identified trend direction and magnitude.
- Calculated rolling return volatility using a 20-observation window.

**3. Market Shock Detection**
- Identified potential market shocks when the absolute daily return exceeded twice the previous day's estimated volatility.
- Used lagged volatility to avoid incorporating the current day's volatility into its own shock threshold.

**4. Data-Driven Thresholds**
- Calculated expanding historical volatility and trend-magnitude thresholds using the 25th and 75th percentiles.
- Required at least 60 historical observations before the thresholds became valid.
- Shifted the thresholds by one observation to use previously available information.

**5. Feeling-State Classification**

Defined five categories of market conditions through rule-based mapping:

| Feeling State | Classification logic |
|---|---|
| `Alert` | A sudden market shock is detected. |
| `Excitement_Up` | Strong upward trend combined with high volatility. |
| `Excitement_Down` | Strong downward trend combined with high volatility. |
| `Stress` | High volatility combined with a weak trend. |
| `Calm` | Low volatility combined with a weak trend. |
| `Neutral` | Conditions that do not satisfy the other classification rules. |

The `Alert` state receives the highest classification priority.

**6. Visualization and State-Transition Analysis**
- Plotted NVIDIA closing prices with points representing the corresponding feeling states.
- Created a pie chart showing the distribution of the identified states.
- Constructed a transition-count matrix to measure consecutive state changes.
- Normalized transition counts by row to estimate transition probabilities.
- Visualized the transition probabilities as a heatmap.

### 📊 Key Outputs

- **Feeling Timeline:** Chronological visualization of NVIDIA stock prices and assigned market states.
- **Feeling Distribution:** Proportional representation of each state across the analyzed observations.
- **Transition Matrix:** Counts and estimated probabilities of transitions between feeling states.

### 💻 Technologies Used

- **Python** — implementation and analysis
- **Pandas** — data manipulation and time-series processing
- **NumPy** — numerical calculations and matrix operations
- **Matplotlib** — data visualization
- **Jupyter Notebook / Google Colab** — development environment

### 🧠 Skills Demonstrated

- Financial time-series analysis
- Feature engineering and rolling-window statistics
- Trend estimation and volatility analysis
- Rule-based classification
- Historical threshold calculation
- Time-series visualization
- State-transition analysis and probability matrices
- Leakage-aware feature and threshold design

### 📌 Conclusion

This project demonstrates how historical stock-market behavior can be translated into interpretable states and examined through time. By combining trend direction, volatility, shock detection, and state-transition probabilities, the implementation provides a structured way to explore changing NVIDIA market conditions.

