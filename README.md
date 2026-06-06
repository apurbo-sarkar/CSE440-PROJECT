# News Topic Classification from Headlines: A Multi-Model Comparative Study

This repository contains the source code, data preprocessing pipelines, and experimental architectures designed for the automated classification of news headlines into four major domains: **Business**, **Science and Technology**, **World News**, and **Sports**. The study systematically evaluates the impact of text noise and linguistic normalization by pairing traditional machine learning and modern deep learning models against distinct text cleaning strategies.

This project was conducted at the Department of Computer Science & Engineering, BRAC University, Dhaka, Bangladesh.

---

## 📌 Project Overview

- **Dataset Size:** 117,710 total rows before deduplication, yielding **95,727 unique news samples**.
- **Task:** Short-text multi-class classification.
- **Core Investigation:** Comparing sparse high-dimensional features (**TF-IDF**) against dense sequence-level aggregations (**Skip-gram** word vectors aggregated via **Smooth Inverse Frequency (SIF)** weighting).
- **Architectures Evaluated:** Logistic Regression, Multi-Layer Perceptrons (DNN), and Recurrent Neural Networks (SimpleRNN, GRU, LSTM, and their Bidirectional variants).

---

## 🛠️ Pipeline & Methodology

### 1. Data Cleaning & Variants
To isolate how text cleaning affects different model configurations, three distinct versions of the text were engineered:
* **No Preprocessing (Raw):** Preserves original text structures, HTML tags, and web-scraped noise as a baseline.
* **Extreme Stemming:** HTML/agency tags (e.g., *Reuters*, *AP*) are removed. Text is lowercased, stripped of digits/punctuation, and processed via the **Porter Stemmer**.
* **Optimum Preprocessing:** Specialized linguistic values are mapped to descriptive placeholders (`MONEY`, `PERCENT`, `UNIT`) and structural terms are normalized via **WordNet Lemmatization** to protect syntax.

### 2. Feature Vectorization
* **TF-IDF:** Configured to extract 10,000 unigram and bigram features.
* **Skip-gram:** Custom-trained 100-dimensional word vectors over a 5-word context window, mathematically downweighted using an alpha parameter through **SIF sentence embedding**.

---

## 📊 Model Architectures & Results

The dataset uses an 85/15 train-validation split extracted from the first 83,727 rows. The remaining instances form a perfectly balanced **test set of 12,000 samples** (3,000 samples per class).

### Performance Summary
* **The Champion Configuration:** A Deep Neural Network (**MLP/DNN**) with 3 hidden layers ($256 \to 128 \to 64$ hidden units with ReLU activations) operating on **TF-IDF + Extreme Stemming**, achieving a peak Macro F1-score of **0.9170** and accuracy of **0.9169**.
* **Baseline Baseline:** **Logistic Regression** achieved an F1-score of **0.9139** using completely **raw text**, showing that short headline contexts can often lose critical predictive signals when aggressively scrubbed.
* **Recurrent Sequence Network:** Among dense embedding configurations, the **Bidirectional SimpleRNN** achieved the highest sequential model score of **0.9133** on raw text.

### Top Performing Configurations

| Model | Embedding | Preprocessing Variant | Accuracy | Macro F1-Score |
| :--- | :--- | :--- | :--- | :--- |
| **DNN (MLP)** | **TF-IDF** | **Extreme Stemming** | **0.9169** | **0.9170** |
| Logistic Regression | TF-IDF | No Preprocessing | 0.9140 | 0.9139 |
| Bi-SimpleRNN | Skip-gram | No Preprocessing | 0.9131 | 0.9133 |
| Bi-LSTM | Skip-gram | No Preprocessing | 0.9111 | 0.9112 |

---

## 📈 Class-Specific Insights (Champion DNN)
Analysis of the top-performing DNN model reveals that the **Sports** category is highly distinct and easiest to isolate, while semantic overlap slightly clusters between **Business** and **Science & Tech**:

| Class | Precision | Recall | F1-Score | Support |
| :--- | :--- | :--- | :--- | :--- |
| Business | 0.88 | 0.89 | 0.88 | 3,000 |
| Science & Tech. | 0.89 | 0.91 | 0.90 | 3,000 |
| Sports | 0.97 | 0.97 | 0.97 | 3,000 |
| World News | 0.94 | 0.89 | 0.91 | 3,000 |

---

## 💻 Repository Structure
```text
├── src/
│   ├── data_preprocessing.py   # Tokenization, Stemming, Lemmatization pipeline
│   ├── train_tfidf_models.py   # Training script for Logistic Regression & MLP
│   └── train_rnn_models.py     # Word2Vec Skip-gram pipeline and Sequential RNNs
├── requirements.txt            # Project dependencies
└── README.md                   # Project description and results
