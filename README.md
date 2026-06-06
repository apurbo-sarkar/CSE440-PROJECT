# 📰 News Topic Classification from Headlines

### A Multi-Model Comparative Study

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Framework](https://img.shields.io/badge/Framework-TensorFlow%20%7C%20Scikit--Learn-orange)
![Task](https://img.shields.io/badge/Task-NLP%20Text%20Classification-green)
![F1 Score](https://img.shields.io/badge/Best%20F1--Score-0.9170-brightgreen)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## 📌 Overview

This project develops a high-performance Natural Language Processing (NLP) system to automatically classify news headlines into four categories:

* 🏢 Business
* 💻 Science & Technology
* 🌍 World News
* ⚽ Sports

It evaluates multiple preprocessing strategies, feature extraction techniques, and model architectures to identify the most effective pipeline for short-text classification.

---

## 👨‍💻 Authors

* **Apurbo Sarkar** — [apurbo.sarkar@g.bracu.ac.bd](mailto:apurbo.sarkar@g.bracu.ac.bd)
* **Md. Abdulla Al Bari** — [abdulla.al.bari@g.bracu.ac.bd](mailto:abdulla.al.bari@g.bracu.ac.bd)
* **Md. Roby** — [md.roby@g.bracu.ac.bd](mailto:md.roby@g.bracu.ac.bd)

Department of Computer Science & Engineering
BRAC University, Dhaka, Bangladesh

---

## 🎯 Objective

To compare traditional machine learning and deep learning approaches for accurate and efficient classification of short news headlines.

---

## 📊 Dataset

* Total headlines: **117,710**
* Cleaned dataset: **95,727 unique samples**
* Balanced test set: **12,000 samples (3,000 per class)**

### Key Characteristics

* Contains HTML noise from scraping
* Moderate class imbalance
* Short-text format (headline-based)

---

## ⚙️ Methodology

### 🧹 Preprocessing Strategies

* **No Preprocessing** — Raw text baseline
* **Extreme Stemming** — Aggressive cleaning with Porter Stemmer
* **Optimum Preprocessing** — Cleaned + lemmatized + semantic token replacement

---

### 🔢 Feature Extraction

* **TF-IDF (10,000 features)** — Unigrams + bigrams
* **Skip-gram Embeddings (100D)** — Weighted using SIF

---

### 🤖 Models

* Logistic Regression
* Deep Neural Network (MLP)
* SimpleRNN, GRU, LSTM
* Bidirectional RNN variants

---

## 🧪 Experimental Setup

* Train/Validation split: **85% / 15%**
* Evaluation metrics:
  * **Macro F1-score (primary)**
  * Accuracy
* Total configurations tested: **24**

---

## 🏆 Results

### Best Performing Model

**DNN (MLP) + TF-IDF + Extreme Stemming**

* **Accuracy:** 0.9169
* **Macro F1-score:** **0.9170**

### Top Model Comparison

| Model | F1 Score |
| :--- | :--- |
| DNN (MLP) | ⭐ 0.9170 |
| Logistic Regression | 0.9139 |
| Bi-SimpleRNN | 0.9133 |
| LSTM | 0.9099 |

---

## 🔍 Key Insights

* TF-IDF outperforms word embeddings for short-text classification
* Logistic Regression remains highly competitive with minimal preprocessing
* Deep Neural Networks benefit from aggressive text normalization
* RNN-based models perform better with richer, less-altered text
* Most classification errors occur between **Business** and **Science & Tech**
* **Sports** category achieves the highest accuracy due to distinct vocabulary

---

## ⚠️ Limitations

* Residual noise in dataset
* Loss of word order in TF-IDF
* Semantic overlap between categories
* Limited contextual depth in short headlines

---

## 🚀 Future Work

* Transformer-based models (BERT, RoBERTa)
* Contextual embeddings
* Hybrid architectures
* Improved semantic disambiguation

---

## 🛠️ Tech Stack

* Python
* Scikit-learn
* TensorFlow / Keras
* NumPy, Pandas
* NLTK

---

## 🤝 Contributing

Contributions are welcome:

1. Fork the repository
2. Create a feature branch
3. Submit a pull request

---

## 🙏 Acknowledgment

This work was conducted at the
**Department of Computer Science & Engineering, BRAC University**,
with support for research and computational resources.

---

## 📄 License

This project is intended for academic and research purposes. 
You may add an MIT License for open-source distribution.

---

⭐ If you find this project useful, consider giving it a star!
