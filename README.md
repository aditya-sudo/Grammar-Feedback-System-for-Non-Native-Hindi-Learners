# 📝 Grammar Feedback System for Non-Native Hindi Learners

## 📌 Overview

This project explores sentence-level grammatical error correction (GEC) in **Hindi**, a low-resource and morphologically rich language. The system targets personalized feedback for Hindi learners by leveraging advanced NLP models trained on both synthetic and real-world datasets.  

Key models such as **T5**, **MarianMT**, **DistilBERT**, and **BERT** were used for detection, classification, and correction tasks. Performance was evaluated using BLEU/GLEU scores and human assessments.

## 🎯 Objectives

- Build a personalized Hindi grammar correction system for non-native learners.
- Generate and curate datasets using Wikipedia edit histories and synthetic rule-based errors.
- Compare token-level and sentence-level GEC approaches using transformer models.
- Fine-tune state-of-the-art models for accurate sentence-level grammatical correction.

## 🧠 Key Features

- **Data Creation**: 5 custom datasets including synthetic inflectional errors, number agreement, word order shuffling, and real Hindi Wikipedia edits (HiWikEd).
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
