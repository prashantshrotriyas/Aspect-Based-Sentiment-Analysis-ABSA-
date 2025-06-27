# 🧠 Aspect-Based Sentiment Analysis (ABSA) Pipeline

A two-stage pipeline for **fine-grained sentiment analysis**, extracting opinion targets and classifying their sentiments.

---

## 🌟 Overview

Traditional sentiment analysis provides a single label for an entire sentence, but real-world reviews often contain **multiple sentiments targeting different aspects**. ABSA offers granular insights by:

1. **Extracting aspect terms** (e.g., "food", "service")
2. **Classifying sentiment** for each aspect (positive/negative/neutral/conflict)

### 🎯 Example
> *"The food was excellent, but the service was disappointing."*  
> → `food` → ⭐️ **positive**  
> → `service` → ❌ **negative**

---

## 🏗️ Project Structure
ABSA-Pipeline/
├── Task1/ # Aspect Term Extraction (ATE)
│ ├── train.json # Training data
│ ├── test.json # Test data
│ ├── val.json # Validation data
│ ├── vocab_task1.json # Vocabulary
│ └── Aspect Term Extraction.ipynb # Implementation notebook
│
└── Task2/ # Aspect Sentiment Classification (ASC)
├── train_task2.json # Training data
├── test_task2.json # Test data
├── val_task2.json # Validation data
├── vocab_task2.json # Vocabulary
└── Aspect Based Sentiment Analysis.ipynb # Implementation notebook

---

## 🔍 Task 1: Aspect Term Extraction (ATE)

### ✅ Objective
Identify exact spans representing opinion targets in text.

### 🧠 Model Architecture
| Component          | Specification                          |
|--------------------|---------------------------------------|
| Architecture       | Bi-GRU / RNN                          |
| Embeddings         | GloVe (300D) / fastText               |
| Tagging Scheme     | BIO (Beginning-Inside-Outside)        |
| Loss Function      | CrossEntropyLoss (with masking)       |
| Evaluation Metric  | Chunk-level F1 (`conlleval`)          |

### 🏆 Performance
| Model              | Validation F1 | Test F1 (Best) |
|--------------------|--------------|----------------|
| GRU + fastText     | 0.7165       | ⭐️ **0.7132**  |
| GRU + GloVe        | 0.7092       |                |
| RNN + fastText     | 0.7013       |                |
| RNN + GloVe        | 0.7000       |                |

---

## 💬 Task 2: Aspect Sentiment Classification (ASC)

### ✅ Objective
Predict sentiment polarity for each extracted aspect term.

### 🧠 Model Architecture
| Component          | Specification                          |
|--------------------|---------------------------------------|
| Architecture       | Bi-LSTM with Aspect-Specific Attention|
| Embeddings         | GloVe (300D)                          |
| Input Format       | Context + aspect indices              |
| Attention Mechanism| Focused on relevant aspect context    |
| Loss Function      | CrossEntropyLoss                      |
| Evaluation Metric  | Accuracy                              |

### 🏆 Performance
| Metric             | Score       |
|--------------------|-------------|
| Validation Accuracy| 0.6523      |
| **Test Accuracy**  | **0.6250**  |

---

## 🚀 Applications
- 🍽️ Restaurant reviews  
- 📱 Product feature analysis  
- 📊 Customer feedback analytics  
- ...and any domain requiring fine-grained sentiment insights!

---

## 📜 License
Open-source (MIT)