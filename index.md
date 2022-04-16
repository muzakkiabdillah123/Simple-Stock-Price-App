## Overview

This mini project contain three files
```
1. 1_stock.py
2. Procfile
3. setup.sh
```

### 1_stock.py
```
import streamlit as st
import yfinance as yf
import pandas as pd

st.write("""
# Simple Stock Price App
""")

st.header('Enter Stock Name')

ticker_symbol_input = 'MSFT'

ticker_symbol = st.text_area(
    "Stock name input", ticker_symbol_input, height=10)

tickerData = yf.Ticker(ticker_symbol)

tickerDf = tickerData.history(period='1d', start='2010-5-31', end='2020-5-31')

st.write("""
## Closing Price
""")
st.line_chart(tickerDf.Close)

st.write("""
## Volume
""")
st.line_chart(tickerDf.Volume)

tickerData.calendar
```

### Procfile
```
web: sh setup.sh && streamlit run 1_stock.py
```

### setup.sh
```
mkdir -p ~/.streamlit/

echo "\
[server]\n\
port = $PORT\n\
enableCORS = false\n\
headless = true\n\
\n\
" > ~/.streamlit/config.toml
```

Try it
```
(https://simple-stock-price-app.herokuapp.com/)
```
