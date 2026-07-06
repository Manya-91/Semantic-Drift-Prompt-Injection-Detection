# Semantic Drift-Based Detection of Prompt Injection Attacks Using Multi-Feature XGBoost Classification


## Overview

Prompt Injection attacks are among the most critical security threats affecting Large Language Model (LLM) applications. Attackers embed malicious instructions within otherwise legitimate text, causing models to ignore previous instructions, leak sensitive information, or perform unintended actions.

This project proposes a **semantic drift-based detection framework** that identifies prompt injection attacks by measuring the semantic divergence between an original email and its cleaned counterpart using multiple embedding models and machine learning.

Instead of relying solely on cosine similarity, this work extracts **ten geometric and statistical drift features** and trains an **XGBoost classifier** capable of accurately distinguishing injected prompts from clean inputs.

---

## Key Features

- Semantic Drift Detection
- Multi-feature Embedding Analysis
- XGBoost Classification
- Neural Network Comparison
- Gaussian Mixture Model Baseline
- Support for Multiple Embedding Models
    - MPNet
    - LLaMA 3.2 3B
    - Qwen2 1.5B
    - Phi-3 Mini
- Fast preprocessing pipeline
- Scalable architecture

---

## Project Architecture

```
Input Email
      │
      ▼
Preprocessing
      │
      ▼
Embedding Generation
(MPNet / LLaMA / Qwen / Phi)
      │
      ▼
Semantic Drift Feature Extraction
(10 Features)
      │
      ▼
Machine Learning Classifier
(XGBoost / Neural Network)
      │
      ▼
Prompt Injection Detection
```

---

## Dataset

This project uses the **LLMail-Inject** benchmark dataset containing enterprise email prompt injection attacks.

Dataset preprocessing includes:

- Duplicate removal
- English language filtering
- Email normalization
- Synthetic clean pair generation
- Attack category annotation

Attack categories include:

- Jailbreak
- Prompt Confusion
- Task Override
- System Leak
- Encoding Manipulation

---

## Drift Features

The model extracts ten embedding drift features:

| Feature | Description |
|----------|-------------|
| Cosine Drift | Semantic similarity |
| Euclidean Distance | Geometric displacement |
| Angular Distance | Embedding angle |
| Manhattan Distance | Sparse changes |
| Dot Product | Vector alignment |
| Norm Ratio | Length ratio |
| Norm Difference | Magnitude difference |
| Element Variance | Distributed drift |
| Maximum Difference | Largest dimension change |
| Pearson Correlation | Linear similarity |

---

## Models Evaluated

| Model | Parameters |
|---------|------------|
| all-mpnet-base-v2 | 110M |
| LLaMA 3.2 3B | 3B |
| Qwen2 1.5B | 1.5B |
| Phi-3 Mini | 3.8B |

---

## Results

| Model | Accuracy | F1 Score |
|---------|----------|----------|
| MPNet + XGBoost | 97.5% | 97.3% |
| LLaMA 3B + XGBoost | **99.3%** | **99.2%** |
| Qwen2 + XGBoost | 98.9% | 98.8% |
| Phi-3 + XGBoost | 97.9% | 97.7% |

---

## Installation

```bash
git clone https://github.com/yourusername/Prompt-Injection-Detection.git

cd Prompt-Injection-Detection

pip install -r requirements.txt
```

---

## Usage

Generate embeddings

```bash
python src/embedding.py
```

Extract drift features

```bash
python src/feature_extraction.py
```

Train model

```bash
python src/train_xgboost.py
```

Evaluate

```bash
python src/evaluate.py
```

---
