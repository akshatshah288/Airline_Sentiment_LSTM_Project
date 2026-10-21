# Simple Airline Sentiment LSTM

Dataset: https://www.kaggle.com/datasets/crowdflower/twitter-airline-sentiment
Reference: https://colab.research.google.com/drive/1tk3cWxvBR69T-b3rLlxbQ-1eEocLHw5q?usp=sharing

## Colab steps
1. Open Colab and upload Airline_Sentiment_LSTM_Simple.ipynb.
2. Upload Tweets.csv through the Files panel and wait for completion.
3. Run all cells from the top.
4. Read test accuracy and the two-sentence forget-gate explanation.
5. Save the notebook with outputs. Submit its accessible link if required.

## Kaggle steps
Import the notebook, attach the linked dataset, and run all cells. The loading cell finds Tweets.csv under /kaggle/input automatically.

## GitHub steps
Upload the notebook, Python script and README to a repository and submit its URL. Link to the source dataset in the README.

## Method
Keep text and airline_sentiment. Remove missing rows and all copies of repeated texts (some copies have conflicting labels). Label-encode negative/neutral/positive. Use a stratified 80/20 train/test split, random_state=42. Fit Tokenizer(num_words=5000) on training text only. Pad/truncate to exactly 50 with default pre-padding/pre-truncation. Train Embedding(5000,32) -> LSTM(32) -> Dense(3,softmax) using Adam and sparse categorical crossentropy for five epochs, batch size 100. No validation split or tuning is needed for this task. The basic cell layout follows the reference notebook.

The optional GRU notebook is a separate copy with only the recurrent layer changed. It does not add complexity to the main LSTM notebook. Both use the same split and seed. A one-run comparison is not a general ranking. Accuracy can hide weaker performance on less common sentiment classes; results can vary slightly across hardware and software versions.

For local use, install requirements.txt and run the notebook or script from this directory.

## Executed results
LSTM: 78.34% accuracy, 0.6031 test loss. Optional GRU: 77.81% accuracy, 0.6162 test loss. Both trained for five epochs on 11,392 rows and were evaluated on the same 2,848 test rows. Every training loss was finite.
