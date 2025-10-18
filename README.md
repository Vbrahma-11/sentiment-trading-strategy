# Sentiment Trading Strategy

An ML-powered trading system that reads financial news and predicts stock movements. Built with RoBERTa and real market data.

## What This Does

This project analyzes financial news sentiment to make trading decisions:
- Collects real news from Bloomberg, Reuters, WSJ, etc.
- Uses RoBERTa AI model to determine if news is positive or negative
- Correlates sentiment with stock price movements
- Creates a trading strategy that adjusts positions based on news
- Backtests to see if it would have made money

## How It Works

**The Strategy:**
- **Very Positive News** (>30): Go 100% invested
- **Positive News** (10-30): Go 75% invested
- **Neutral News** (-10 to 10): Go 50% invested
- **Negative News** (<-10): Go 25% invested (mostly cash)

Instead of just holding a stock, this adjusts your position based on how good or bad the news is each day.

## Features

- **AI Sentiment Analysis**: RoBERTa transformer model (same tech as ChatGPT)
- **Real News Data**: NewsAPI pulls from 10+ major financial sources
- **Multi-Company Testing**: Analyzes 10 different tech stocks
- **Backtesting**: Tests if the strategy actually works on historical data


## Requirements

**APIs (Free):**
- NewsAPI key from [newsapi.org](https://newsapi.org/)
- Yahoo Finance (automatic, no key needed)

**Python Packages:**

torch transformers newsapi-client yfinance pandas numpy matplotlib

## Setup

### 1. Get Your API Key
1. Sign up at [newsapi.org](https://newsapi.org/) (free)
2. Copy your API key

### 2. Add API Key to Notebook

NEWS_API_KEY = "your_key_here"


### 3. Run the Notebook
Open in Jupyter and run cells in order. It will:
- Download the RoBERTa AI model (~500MB, one-time)
- Fetch news articles
- Analyze sentiment
- Get stock prices
- Show correlations and backtest results

## Companies Analyzed

Tests the strategy on 10 major tech stocks:
- NVIDIA (NVDA)
- Apple (AAPL)
- Microsoft (MSFT)
- Tesla (TSLA)
- Amazon (AMZN)
- Meta (META)
- Google (GOOGL)
- Netflix (NFLX)
- AMD
- Intel (INTC)

## Sample Results

The notebook shows:
- Which companies have the strongest sentiment-price correlation
- Whether positive news predicts price increases
- How far ahead sentiment predicts (1-day, 2-day, or 3-day)
- Strategy performance vs just buying and holding

**Key Findings:**
- Positive sentiment does correlate with short-term price increases
- 2-day predictions tend to work better than 1-day or 3-day
- Different stocks respond differently to news
- The strategy can outperform buy-and-hold, but not always

## What I Learned

### Machine Learning
- How transformer models (like ChatGPT) work
- Using pre-trained AI models for NLP
- GPU acceleration with PyTorch
- Transfer learning (using existing trained models)

### Quantitative Finance
- Building and testing trading strategies
- Backtesting methodology
- Position sizing and risk management
- Statistical correlation analysis
- How news affects stock prices

### Data Science
- Working with real-time APIs
- Time series analysis
- Multi-company comparative analysis
- Data visualization techniques

### Programming
- Integrating multiple APIs (NewsAPI + Yahoo Finance)
- Processing large amounts of text data
- Batch analysis across datasets
- Creating professional visualizations

## Visualizations

The notebook creates:
1. Daily sentiment bar charts
2. Stock price movement charts
3. Scatter plots (sentiment vs future returns)
4. Multi-company correlation comparison
5. Backtest performance graphs
6. Strategy vs buy-and-hold comparison

## How Sentiment Analysis Works

The RoBERTa model reads text and outputs three scores:
- Negative probability
- Neutral probability  
- Positive probability

Then converts to a single score from -100 to +100:

sentiment_score = (positive - negative) × 100


Examples:
- "Tesla announces record profits" → +85 (very positive)
- "Company faces lawsuit" → -65 (very negative)
- "Quarterly earnings as expected" → +5 (neutral/slightly positive)


Disclaimer: This was a fun educational personal project, please do not use for real trading.

## Future Improvements

- Real-time news streaming instead of daily batches
- Include earnings call transcripts
- Add social media sentiment (Twitter/Reddit)
- More sophisticated risk management
- Portfolio optimization across multiple stocks
- Machine learning to improve signal generation
- Compare different sentiment models

## Why I Built This

I wanted to understand:
- How AI models analyze text
- Whether news actually predicts stock prices
- How quantitative traders build strategies
- The process of backtesting trading ideas

This combines my interests in ML, AI, finance, and data science.

## Resources Used

### Documentation
- [Hugging Face Transformers](https://huggingface.co/docs/transformers/)
- [NewsAPI Docs](https://newsapi.org/docs)
- [yfinance](https://pypi.org/project/yfinance/)
- [PyTorch](https://pytorch.org/docs/)

## Contact

- Vishal Brahma (Carnegie Mellon University 2029)
- GitHub: @VBrahma-11
- Email: VBrahma@andrew.cmu.edu
