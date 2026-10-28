# Mobile SMS Spam Detection: A Transformer-Based Classification

This project evaluates three distinct classification approaches for detecting mobile SMS spam and phishing (smishing) attacks. Because traditional keyword-based filters and shallow machine learning models struggle to detect spam that relies on obfuscation and semantic manipulation, this study implements a transformer-based approach to accurately capture context and subtle malicious intent.

## Models Evaluated

* **Baseline (TF-IDF + Logistic Regression):** Uses a sparse bag-of-words representation. It is fast and interpretable but lacks semantic understanding and word order, making it vulnerable to obfuscation.
* **Intermediate (Embedding + BiLSTM):** Utilizes learned dense word embeddings to capture bidirectional context and word order.
* **Proposed (Fine-Tuned DistilBERT):** Employs contextual subword embeddings and self-attention over the entire message. DistilBERT was chosen because it is approximately 40% smaller and 60% faster at inference than BERT-base while retaining about 97% of its language understanding performance.

## Dataset

* **Source:** UCI SMS Spam Collection
* **Size:** 5,572 English SMS messages
* **Distribution:** Imbalanced, with 4,825 legitimate "ham" messages (86.6%) and 747 "spam" messages (13.4%)

## Key Results

* The fine-tuned DistilBERT model achieved **99.28% accuracy, 97.32% precision, 97.32% recall, and a 99.90% ROC-AUC** on a held-out test set of 836 messages.
* Compared to the TF-IDF baseline, DistilBERT reduced the number of missed spam messages (false negatives) from 18 to 3—an 83% reduction.
* Qualitative analysis showed the Transformer is vastly superior at detecting obfuscated phishing, social engineering, and context-dependent spam signals while keeping false positive rates low.

## Tech Stack & Environment

* **Language:** Python 3.8.10
* **Frameworks & Libraries:** PyTorch 2.0.1, Hugging Face Transformers 4.30.2, scikit-learn 1.2.2, Pandas 1.5.3, NumPy 1.23.5
* **Hardware Compute:** Google Colab with an NVIDIA Tesla T4 GPU (16 GB VRAM) and CUDA Toolkit 11.8

## Full Documentation

For complete details covering the exploratory data analysis, data preprocessing pipelines, semantic context evaluation, and experimental setup, please refer to the project's comprehensive documentation file: `Final_Documentation_SMS_Spam_Detection.md`.

## Authors

* Chaulagai Shishir
* Bishwokarma Rajkumar
* Mehta Avishek

*Institution: College of Global AI Convergence, Seoul Christian University, Korea*