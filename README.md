# 📰 News Topic Classification from Headlines

### A Multi-Model Comparative Study

---

## 📌 Overview

This project focuses on **automated news headline classification** using machine learning and deep learning techniques. The system categorizes news headlines into four distinct classes:

* Business
* Science & Technology
* World News
* Sports

The study compares multiple preprocessing techniques, feature extraction methods, and model architectures to determine the most effective pipeline for short-text classification.

---

## 👨‍💻 Authors

* **Apurbo Sarkar**
  CSE Department, BRAC University
  📧 [apurbo.sarkar@g.bracu.ac.bd](mailto:apurbo.sarkar@g.bracu.ac.bd)

* **Md. Abdulla Al Bari**
  CSE Department, BRAC University
  📧 [abdulla.al.bari@g.bracu.ac.bd](mailto:abdulla.al.bari@g.bracu.ac.bd)

* **Md. Roby**
  CSE Department, BRAC University
  📧 [md.roby@g.bracu.ac.bd](mailto:md.roby@g.bracu.ac.bd)

---

## 🎯 Objectives

* Classify news headlines into predefined categories
* Compare performance of:

  * Traditional ML models
  * Deep Neural Networks
  * Recurrent Neural Networks
* Evaluate impact of different preprocessing strategies
* Analyze effectiveness of TF-IDF vs word embeddings

---

## 📊 Dataset

* Total headlines: **117,710**
* After cleaning: **95,727 unique samples**
* Categories:

  * World News
  * Business
  * Science & Technology
  * Sports

### Data Characteristics

* Contains HTML noise from scraping
* Moderate class imbalance
* Short-text format (headlines only)

---

## ⚙️ Methodology

### 1. Preprocessing Techniques

Three versions of text were used:

#### 🔹 No Preprocessing

* Raw text with HTML tags
* Baseline approach

#### 🔹 Extreme Stemming

* Remove HTML tags, punctuation, numbers
* Lowercasing
* Stopword removal
* Porter Stemming

#### 🔹 Optimum Preprocessing

* Replace symbols (e.g., `$ → MONEY`, `% → PERCENT`)
* WordNet Lemmatization
* Clean but human-readable text

---

### 2. Feature Extraction

#### 📌 TF-IDF

* 10,000 features (unigrams + bigrams)
* Used with:

  * Logistic Regression
  * Deep Neural Network

#### 📌 Skip-gram Embeddings

* 100-dimensional vectors
* Context window: 5
* Weighted using SIF (Smooth Inverse Frequency)
* Used with RNN-based models

---

### 3. Models Used

#### 🔹 Traditional ML

* Logistic Regression (L2 regularization)

#### 🔹 Deep Learning

* Multi-Layer Perceptron (DNN)

#### 🔹 Recurrent Neural Networks

* SimpleRNN
* GRU
* LSTM
* Bidirectional variants of all above

---

## 🧪 Training Setup

* Train/Validation Split: **85% / 15%**
* Test Set: **12,000 samples (balanced)**
* Evaluation Metric:

  * **Macro F1-score (primary)**
  * Accuracy

---

## 📈 Results

### 🏆 Best Model

| Model         | Features | Preprocessing    | F1 Score   |
| ------------- | -------- | ---------------- | ---------- |
| **DNN (MLP)** | TF-IDF   | Extreme Stemming | **0.9170** |

### 🥈 Second Best

| Model               | Features | Preprocessing    | F1 Score |
| ------------------- | -------- | ---------------- | -------- |
| Logistic Regression | TF-IDF   | No Preprocessing | 0.9139   |

---

## 🔍 Key Findings

* **TF-IDF outperformed word embeddings** for this task
* **Extreme stemming improved DNN performance significantly**
* **Logistic Regression performed strongly even on raw text**
* **RNN models performed best with minimal preprocessing**
* Sports category had the highest classification accuracy
* Most confusion occurred between:

  * Business
  * Science & Technology

---

## 🧠 Model Insights

### Why TF-IDF worked well:

* Captures important keywords directly
* Effective for short texts like headlines
* Large dataset helps define strong boundaries

### Why RNNs underperformed:

* SIF removes word order
* Headlines are short → limited sequence benefit

---

## ⚠️ Limitations

* Residual noise in dataset
* Loss of word order in TF-IDF
* Slight class imbalance
* Limited contextual understanding

---

## 🚀 Future Work

* Implement transformer-based models (e.g., BERT)
* Use contextual embeddings
* Improve handling of semantic overlap
* Experiment with hybrid architectures

---

## 🛠️ Technologies Used

* Python
* Scikit-learn
* TensorFlow / Keras
* NumPy / Pandas
* NLP Libraries (NLTK, etc.)

---

## 🙏 Acknowledgment

This work was conducted at the
**Department of Computer Science & Engineering, BRAC University, Dhaka, Bangladesh**,
with support for computational resources and research facilities.

---

## 📚 References

* TF-IDF (Salton & Buckley, 1988)
* Word2Vec Skip-gram (Mikolov et al., 2013)
* SIF Embeddings (Arora et al., 2017)
* Logistic Regression (Cox, 1958)
* Perceptron (Rosenblatt, 1958)
* LSTM (Hochreiter & Schmidhuber, 1997)
* GRU (Cho et al., 2014)
* Porter Stemmer (Porter, 1980)
* NLTK (Bird et al., 2009)
* TensorFlow (Abadi et al., 2016)

---

## ⭐ Contributing

Contributions are welcome! Feel free to:

* Fork the repo
* Create a feature branch
* Submit a pull request

---

## 📄 License

This project is for academic and research purposes. Add a license if distributing publicly.

---
