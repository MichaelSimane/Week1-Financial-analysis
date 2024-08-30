## Task 1: Analyzing Sentiment in Financial News Headlines

### Objective

The objective of this task is to investigate how the sentiment of news headlines about stocks might influence their prices. Specifically, I want to determine if positive news leads to higher stock prices and if negative news results in price declines.

### How I Did It

1. **Reading the Data:**
   - I began by loading a dataset that includes financial news headlines and their publication dates.
   
   ```
   import pandas as pd
   df = pd.read_csv('headlines.csv')
   df.head()
   ```
   This code loads the headlines data and displays the first few rows.

2. **Analyzing Sentiment:**
   - I utilized the `SentimentIntensityAnalyzer` from the `nltk` library to score each headline's sentiment. This tool provides a sentiment score that ranges from -1 (very negative) to 1 (very positive).
   
   ```
   import nltk
   from nltk.sentiment.vader import SentimentIntensityAnalyzer
   nltk.download('vader_lexicon')  # Ensure the VADER lexicon is downloaded
   sia = SentimentIntensityAnalyzer()
   df['sentiment_score'] = df['headline'].apply(lambda x: sia.polarity_scores(x)['compound'])
   ```
   The `sentiment_score` column now reflects the overall sentiment of each headline.

3. **Calculating Percentage of Sentiment Categories:**
   - I calculated the percentage of each sentiment category (very negative, negative, neutral, positive) relative to the total number of headlines for each publisher.
   
   ```
   # Calculating percentage of sentiment_category by headline count by publisher
   publisher_categ['very_negative_percent'] = (publisher_categ[publisher_categ.columns[1]].astype('float') / publisher_categ['headline'].astype('float')) * 100
   publisher_categ['negative_percent'] = (publisher_categ[publisher_categ.columns[2]].astype('float') / publisher_categ['headline'].astype('float')) * 100
   publisher_categ['neutral_percent'] = (publisher_categ[publisher_categ.columns[3]].astype('float') / publisher_categ['headline'].astype('float')) * 100
   publisher_categ['positive_percent'] = (publisher_categ[publisher_categ.columns[4]].astype('float') / publisher_categ['headline'].astype('float')) * 100
   ```

### What I Found

My preliminary analysis suggests a general correlation between the sentiment scores and stock prices. Positive sentiment often corresponds with increases in stock prices, while negative sentiment tends to align with price declines. Additionally, the time series decomposition of headline frequency revealed various patterns:
- **Trend:** Shows the overall direction of headline frequency over time.
- **Seasonal:** Reveals repeating patterns or cycles in the frequency of headlines.
- **Residual:** Captures the random fluctuations not explained by the trend or seasonal components.

I also found that calculating the percentage of each sentiment category relative to the total number of headlines provides insights into how different publishers contribute to the sentiment landscape. 
