# **Phoneme-to-Text Capstone Project**
### ***Phoneme-to-Text Capstone Project***

**Author:** Zane Graper
**Models:** T5-small (ARPABET + IPA variants)

### ** Overview**

This repository contains the full codebase for a capstone project investigating phoneme-to-text transformation using sequence-to-sequence models. The objective is to build a robust system that converts phoneme sequences—especially those derived from children’s speech—into readable English text.

Because children’s speech presents unique challenges (phonological variability, inconsistent articulation, sparse datasets), this project builds an intermediate phoneme representation pipeline and fine-tunes transformer models to map phonemes back to text. The repository supports ARPABET and IPA transcription streams, large-scale corpus creation, model training, experimental baselines, and rigorous evaluation.

---

### **Repository Structure**

```
.
├── baseline_tests/
├── corpus_creation/
├── evaluation/
├── experimentation/
└── model_training/
```

### baseline_tests/

Contains early proof-of-concept experiments used to establish baseline performance for phoneme-to-text modeling.
This includes:

* A/B comparisons of boundary heuristics

* Initial runs of off-the-shelf models

* Metric baselines (CER, WER, BLEU, chrF)

* Benchmark experiments validating preprocessing assumptions

These tests provide a reference point for improvements achieved through later training and data engineering.

### corpus_creation/

Scripts and notebooks used to construct large-scale phoneme/text corpora.

Major components include:

* BookCorpus extraction + sampling

* Text normalization pipelines

* ARPABET and IPA phonemization (g2p-en, phonemizer)

* Post-G2P cleanup (stress removal, symbol filtering, deduplication)

* Dataset statistics and quality checks

The outputs of this folder feed directly into model training.

### evaluation/

All evaluation pipelines for trained models, including:

* Automated metric computation (CER, WER, BLEU, chrF)

* Substitution/Insertion/Deletion breakdowns (JIWER)

* Dataset statistics

* Sample prediction dumping

* Loss-curve visualization (W&B exports)

* Standalone `evaluate_t5_ipa_to_text.py` script

This folder provides the quantitative basis for comparing architectures, datasets, and hyperparameters.

### experimentation/

A sandbox for exploratory and iterative research, typically including:

* Alternative architectures (ByT5, T5-base trials)

* Hyperparameter search variations

* Data ablation studies

* Early phonological-rule experiments

* Child-speech prototypes

This directory is intentionally flexible and contains work that informed final decisions but did not always progress to production code.

### model_training/

5. model_training/

Core training scripts used to fine-tune:

* T5-small ARPABET→Text model, and

* T5-small IPA→Text model

Includes:

* Preprocessing + tokenization functions

* Hugging Face Trainer setup

* Training arguments for stability

* Checkpointing + model saving

* Scripts for uploading final models to Hugging Face Hub

This directory contains the canonical model-building workflow used in the capstone project.

---

### **Project Highlights**

* Construction of a 1M-line phoneme/text corpus for supervised learning

* Fine-tuning of T5-small models for ARPABET and IPA input streams

* Evaluation using industry-standard ASR metrics

* Demonstrated strong performance with low CER and competitive BLEU/chrF scores

* Reproducible end-to-end pipeline: corpus → training → evaluation → deployment

---

### **Model Availability**

Both trained models are available on the Hugging Face Hub:

* ARPABET Model
   * https://huggingface.co/zanegraper/t5-small-phoneme-to-text

* IPA Model
   * https://huggingface.co/zanegraper/t5-small-ipa-phoneme-to-text

Each model includes documentation, evaluation metrics, examples, and licensing.

---

### **Citation**

Citation

If referencing the work:.

```
Graper, Z. (2025). Phoneme-to-Text Transformation using a Sequence-to-Sequence T5 Model. 
MSAI 699 Capstone Project, University of the Cumberlands.
```

---

### **License**

Models and datasets are released under CC BY-NC 4.0 unless otherwise noted.
