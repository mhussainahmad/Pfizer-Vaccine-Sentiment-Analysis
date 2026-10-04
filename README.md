# Pfizer Vaccine Tweet Sentiment Analysis

A 2022 Google Colab notebook that cleans a dataset of tweets about the Pfizer/BioNTech COVID-19 vaccine, draws word clouds, and scores sentiment with NLTK's VADER analyzer.

## Overview

The notebook `Pfizer_Vaccine_Sentiment_Analysis.ipynb`:

1. Loads a CSV of tweets with user metadata (`user_name`, `user_location`, `user_verified`, `text`, `hashtags`, `retweets`, `favorites`, and so on).
2. Drops rows with missing values, leaving 4,749 tweets.
3. Cleans the text: lowercasing, removing URLs, HTML, punctuation and digit tokens, removing English stopwords and applying the Snowball stemmer.
4. Builds word clouds for the tweet text and the hashtags.
5. Counts verified and unverified accounts (580 verified, 4,169 not).
6. Scores each tweet with VADER and sums the positive, negative and neutral components to give an overall label.

## Results

The saved output of the final cells reports summed VADER scores of Positive 7.456, Negative 0.0 and Neutral 4741.544, so the notebook labels the overall sentiment as neutral.

## Limitations

The `clean()` function rejoins words with `''.join(...)` instead of `' '.join(...)`, so each tweet becomes one long run-together string (visible in the printed `text` column). VADER cannot match words in that string to its lexicon, which is why almost every tweet scores as fully neutral. The neutral result above reflects this preprocessing step, not the sentiment of the tweets. Joining with a space, and running VADER on the raw text rather than stemmed text, would be needed for meaningful scores.

## Repository layout

```
Pfizer_Vaccine_Sentiment_Analysis.ipynb   # full notebook with saved outputs and word-cloud figures
README.md
```

## Getting started

1. Obtain the tweet CSV and update the `pd.read_csv('/content/drive/MyDrive/Datasets/Twitter sentiment analysis.txt')` path in the notebook.
2. Open the notebook in Google Colab (there is an "Open in Colab" badge in the first cell) or Jupyter.
3. Run the cells in order. The notebook downloads the NLTK `stopwords` and `vader_lexicon` resources itself.

Dependencies: `pandas`, `nltk`, `wordcloud`, `matplotlib`, `seaborn`.

## Tech stack

Python, pandas, NLTK (VADER, Snowball stemmer), WordCloud, Matplotlib.

## Data

The notebook reads a local CSV of Pfizer vaccine tweets; the file is not included in this repository and its original source is not recorded in the notebook.
