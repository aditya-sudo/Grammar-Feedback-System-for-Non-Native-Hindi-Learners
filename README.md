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
- [🗂️ Code Structure](#️-code-structure)
- [🚀 Usage](#-usage)
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

## 🗂️ Code Structure

The repository includes:

```
📦 Grammar-Feedback-System-for-Non-Native-Hindi-Learners/
├── 📁 Hindi_WikiEdits_DataGenerator/  # Scripts and resources for data generation
├── 📁 src/                            # Jupyter notebooks and Python scripts for modeling
├── 📄 FinalProjectReport.pdf          # Detailed methodology and results
├── 📄 README.md                       # Project overview
└── 📄 requirements.txt                # Dependencies
```

## 🚀 Usage

To reproduce results or run the models:

```bash
# Create and activate virtual environment
python3 -m venv env
source env/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run data preprocessing scripts
cd Hindi_WikiEdits_DataGenerator/
bash mlconvgec_execution.sh

# Launch Jupyter notebooks for analysis and training
cd ../src
jupyter notebook
```

> For detailed configuration and specific steps, refer to individual notebooks and scripts under `/src` and `/Hindi_WikiEdits_DataGenerator`.

## 👨‍💻 Authors

- Aditya Shah – [GitHub](https://github.com/aditya-sudo)
- Nikhil Chukka
- Uddip Yalamanchili

📂 [Project Repository](https://github.com/aditya-sudo/Grammar-Feedback-System-for-Non-Native-Hindi-Learners)
