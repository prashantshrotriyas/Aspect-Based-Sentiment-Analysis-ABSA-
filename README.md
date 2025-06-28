# 🧠 ASPECT-BASED SENTIMENT ANALYSIS (ABSA)

A two-stage pipeline for **Aspect-Based Sentiment Analysis**, designed to extract opinion targets and classify sentiments at a fine-grained level.

---

## 🎯 TASK OVERVIEW

### 🔍 Task 1: Aspect Term Extraction (ATE)
Identify **opinion targets (aspects)** in a sentence.

### 🎯 Task 2: Aspect Sentiment Classification (ASC)
Predict **sentiment polarity** (**positive**, **negative**, **neutral**, **conflict**) for each extracted aspect.

---

## 💡 MOTIVATION

Traditional sentiment analysis gives a single label to a sentence, but real-world reviews often express **multiple sentiments for different aspects**.

#### 🧾 Example:
> *"The food was excellent, but the service was disappointing."*  
> → `food` → ⭐️ **positive**  
> → `service` → ❌ **negative**

🔍 **ABSA** offers **fine-grained insights**, critical in domains like:
- Restaurant reviews
- Product analysis
- Customer feedback

---

## 📁 PROJECT STRUCTURE

```text
Task1/                       # Aspect Term Extraction (ATE)
├── train.json
├── train.task1.json
├── test.json
├── test_task1.json
├── val.json
├── val.task1.json
├── vocab_task1.json
└── Aspect Term Extraction.ipynb

Task2/                       # Aspect Sentiment Classification (ASC)
├── train.json
├── train_task2.json
├── test.json
├── test_task2.json
├── val.json
├── val_task2.json
├── vocab_task2.json
└── Aspect Based Sentiment Analysis.ipynb

README.md                    # You're here!
```

---

## 💾 DATASET

We use the **SemEval-2014 Task 4: Aspect-Based Sentiment Analysis (Restaurant Domain)** dataset.

🔗 **Source:** [SemEval-2014 Task 4 Official Site](https://alt.qcri.org/semeval2014/task4/)

📂 **Structure:**
- Each sentence is annotated with:
    - `aspect_terms`: opinion targets with start/end offsets and polarity
    - `aspect_categories`: high-level categories with polarity (e.g., `food`, `service`)
- Polarity labels: `positive`, `negative`, `neutral`, `conflict`

📊 **Data Splits:**

| Split      | Samples |
|------------|---------|
| Train      | 2,435   |
| Validation | 304     |
| Test       | 305     |

📝 **Format:** JSON (converted from the original XML for easier processing)

🔍 **Domain:** Restaurant reviews (English)

---

## 🧩 TASK 1 – ASPECT TERM EXTRACTION (ATE)

### ✅ Objective
Extract exact spans from a sentence that represent opinion targets.

### 🧠 Model Specs
- 🔧 **Architecture:** Bi-GRU / RNN
- 🔤 **Embedding:** GloVe / fastText
- 🏷️ **Tagging:** BIO (Beginning, Inside, Outside)
- ❌ **Loss Function:** CrossEntropyLoss with masking
- 📊 **Evaluation:** Chunk-level F1 (conlleval)

### 🏆 Results

| Model              | Validation F1 |
|--------------------|---------------|
| GRU + fastText     | 0.7165        |
| GRU + GloVe        | 0.7092        |
| RNN + fastText     | 0.7013        |
| RNN + GloVe        | 0.7000        |

**Test F1 (Best):** ⭐️ **0.7132**

---

## 💬 TASK 2 – ASPECT SENTIMENT CLASSIFICATION (ASC)

### ✅ Objective
For each aspect term, predict its sentiment label.

### 🧠 Model Specs
- 🔧 **Architecture:** Bi-LSTM with Aspect-Specific Attention
- 🔤 **Embedding:** GloVe (300D)
- 🧠 **Input:** Context + aspect indices
- 🎯 **Attention:** Focus on relevant context around each aspect
- ❌ **Loss Function:** CrossEntropyLoss
- 📊 **Evaluation:** Accuracy

### 🏆 Results

| Metric                      | Score  |
|-----------------------------|--------|
| Validation Accuracy         | 0.6523 |
| Test Accuracy (Best Model) | 0.6250 |