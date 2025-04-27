# 📊 Stock Data Analysis: Tesla vs GameStop

## 📝 Project Overview
This project simulates a real-world scenario in which a data analyst is tasked with extracting and visualizing stock market data for two companies: **Tesla** and **GameStop**. The main goal is to explore the relationship between stock prices and company revenue using publicly available data.

---

## 📁 Table of Contents
1. Project Goals
2. Tools & Libraries
3. Data Sources
4. Data Extraction
5. Data Cleaning
6. Data Visualization
7. Key Learnings
8. Next Steps

---

## 🎯 1. Project Goals
- Extract stock price data using `yfinance`
- Scrape revenue data from web sources using `BeautifulSoup`
- Clean and convert financial data using `pandas`
- Visualize stock prices and revenue trends
- Simulate a business reporting environment

---

## 🛠️ 2. Tools & Libraries
- **Python** (v3.12)
- `yfinance`
- `pandas`
- `matplotlib`
- `BeautifulSoup`
- `requests`

---

## 🌐 3. Data Sources
- **Tesla & GameStop Stock Data:** Yahoo Finance (via `yfinance`)
- **Revenue Data:** Scraped from Macrotrends.net

---

## ⛏️ 4. Data Extraction
```python
import yfinance as yf

# Tesla stock data
tesla_data = yf.download('TSLA', start='2010-01-01', end='2021-06-30')

# GameStop stock data
gme_data = yf.download('GME', start='2010-01-01', end='2021-06-30')
```

---

## 🌐 5. Revenue Data via Web Scraping
```python
from bs4 import BeautifulSoup
import requests

# Example for Tesla revenue
tesla_url = "https://www.macrotrends.net/stocks/charts/TSLA/tesla/revenue"
html_tesla = requests.get(tesla_url).text
soup_tesla = BeautifulSoup(html_tesla, "html.parser")
```

---

## 🧹 6. Data Cleaning & Formatting
```python
# Cleaning revenue column
tesla_revenue['Revenue'] = tesla_revenue['Revenue'].str.replace(',|\$', '')
tesla_revenue.dropna(inplace=True)
tesla_revenue = tesla_revenue[tesla_revenue['Revenue'] != '']
tesla_revenue['Revenue'] = tesla_revenue['Revenue'].astype(float)
```

---

## 📈 7. Data Visualization
```python
def make_graph(stock_data, revenue_data, stock):
    fig, ax1 = plt.subplots(figsize=(14, 6))

    ax1.plot(stock_data.index, stock_data['Close'], color='blue', label='Stock Price')
    ax1.set_ylabel('Stock Price', color='blue')
    ax1.tick_params(axis='y', labelcolor='blue')
    ax1.set_title(f'{stock} Stock Price & Revenue')

    ax2 = ax1.twinx()
    ax2.plot(revenue_data['Date'], revenue_data['Revenue'], color='red', label='Revenue')
    ax2.set_ylabel('Revenue (in billions)', color='red')
    ax2.tick_params(axis='y', labelcolor='red')

    plt.show()

# Call the function
make_graph(tesla_data, tesla_revenue, 'Tesla')
make_graph(gme_data, gme_revenue, 'GameStop')
```

---

## 🧠 8. Key Learnings
- Automated data collection using APIs and scraping
- Cleaning and converting financial data to usable formats
- Combining datasets from different sources
- Creating insightful and readable visualizations

---

## 🚀 9. Next Steps
- Add stock performance prediction using regression
- Include additional companies for broader analysis
- Automate monthly updates and generate reports

---

## 🔗 Author
**Abdeljalil El Khyati**  
Data Analyst - Scientist in training | Mathematics Teacher  
https://github.com/JALILOHUB/DataSpark | https://www.linkedin.com/in/abdeljalil-el-khyati/

---

> This project is part of a practical assignment for learning data analysis and visualization using real-world financial datasets.

