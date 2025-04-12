# 📝 Grammar Feedback System for Non-Native Hindi Learners

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![HuggingFace](https://img.shields.io/badge/HuggingFace-Transformers-yellow)](https://huggingface.co/transformers/)
[![Project Repository](https://img.shields.io/badge/GitHub-Project-blue)](https://github.com/aditya-sudo/Grammar-Feedback-System-for-Non-Native-Hindi-Learners)

## 📚 Table of Contents

- [📌 Overview](#-overview)
- [🎯 Objectives](#-objectives)
- [🧠 Key Features](#-key-features)
- [📊 Results](#-results)
- [📚 Learning Outcomes](#-learning-outcomes)
- [👨‍💻 Authors](#-authors)

---

## 📌 Overview

This project explores sentence-level grammatical error correction (GEC) in **Hindi**, a low-resource and morphologically rich language. The system targets personalized feedback for Hindi learners by leveraging advanced NLP models trained on both synthetic and real-world datasets.

Key models such as **T5**, **MarianMT**, **DistilBERT**, and **BERT** were used for detection, classification, and correction tasks. Performance was evaluated using BLEU/GLEU scores and human assessments.

## 🎯 Objectives

- Build a personalized Hindi grammar correction system for non-native learners.
- Generate and curate datasets using Wikipedia edit histories and synthetic rule-based errors.
- Compare token-level and sentence-level GEC approaches using transformer models.
- Fine-tune state-of-the-art models for accurate sentence-level grammatical correction.

## 🧠 Key Features

- **Data Creation**: 5 custom datasets including:
  - Synthetic errors (inflectional, word order, number agreement, case markers)
  - Real Hindi Wikipedia edit-based corpus (HiWikEd)
  - Back-translated Hindi sentences using Helsinki-NLP models

- **Dataset Process**:
  - Used Hindi Wikipedia dump (June 2024) and WikiExtractor to extract clean sentences.
  - Generated synthetic errors using rule-based POS tagging (via Stanza) and random perturbations.
  - Extracted real edits using a modified WikiEdits script to build the HiWikEd corpus.
  - Augmented data using ordered back-translation with HuggingFace translation pipelines.

- **🔗 Dataset Access**:  
  [📂 Click here to access the dataset on SharePoint](https://gmuedu-my.sharepoint.com/:f:/g/personal/uyalaman_gmu_edu/El9MKJSpVBtGutpSgO0OHxAB6IN_FFDzzj_mI7uipYpyLQ?e=dHs31D)

- **Model Pipeline**:
  - `DistilBERT`: Sentence correctness classification
  - `BERT`: Token-level error labeling (limited success)
  - `MarianMT` and `T5`: Sentence-level correction (fine-tuned for Hindi)

- **Training Infrastructure**: Fine-tuned on A100 80GB GPU with gradient accumulation and mixed-precision training.

- **Evaluation**:
  - Fine-tuned MarianMT achieved **+9.6% BLEU** and **+13.9% GLEU** over the baseline.
  - Example Correction:
    - ❌ *"उसकी प्रतिभा की गहराई किसी अनजाने समुद्र जैसा है"*
    - ✅ *"उसकी प्रतिभा की गहराई किसी अनजाने समुद्र जैसी है"*

## 📊 Results

| Model               | BLEU | GLEU |
|--------------------|------|------|
| MarianMT (baseline)| 0.52 | 0.43 |
| MarianMT (tuned)   | 0.57 | 0.49 |

| Model               | Precision | Recall | F1-Score |
|--------------------|-----------|--------|----------|
| DistilBERT (baseline) | 0.48   | 0.36   | 0.41     |
| DistilBERT (tuned)    | 0.68   | 0.58   | 0.62     |

## 📚 Learning Outcomes

- Gained practical experience in **low-resource NLP**, **dataset creation**, and **transformer fine-tuning**.
- Discovered the limitations of token-level GEC for Hindi and transitioned to sentence-level correction.
- Conducted in-depth error analysis to evaluate model performance on idioms, compound sentences, and inflections.

## 👨‍💻 Authors

- Aditya Shah – [GitHub](https://github.com/aditya-sudo)
- Nikhil Chukka
- Uddip Yalamanchili

---

## 🗂️ Code Structure

The repository includes:

```
📦Grammar-Feedback-System-for-Non-Native-Hindi-Learners/
├── 📁 data/                      # Scripts and datasets for synthetic and real error generation
│   ├── hiwikied_extraction.py   # Extracts corrections from Hindi Wikipedia edits
│   ├── generate_synthetic.py    # Adds inflectional, agreement, word order errors
│   └── back_translation.py      # Ordered back-translation using Helsinki-NLP
│
├── 📁 models/                   # Model training scripts
│   ├── train_distilbert.py      # Sentence-level classification with DistilBERT
│   ├── train_t5.py              # Sentence correction using T5
│   ├── train_marianmt.py        # Sentence correction using MarianMT
│   └── evaluate.py              # Evaluation script (BLEU, GLEU, precision, recall)
│
├── 📁 utils/                    # Utilities
│   ├── tokenizer_utils.py
│   ├── data_loader.py
│   └── helpers.py
│
├── 📄 report.pdf                # Final report with methodology and results
├── 📄 README.md                 # Project overview
└── 📄 requirements.txt          # Python dependencies
```

To reproduce results:

```bash
# Create and activate virtual environment
python3 -m venv env
source env/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run data preprocessing
python data/hiwikied_extraction.py

# Train models
python models/train_t5.py
python models/train_marianmt.py

# Evaluate results
python models/evaluate.py
```

> For detailed configuration, refer to model-specific scripts under `/models`.

