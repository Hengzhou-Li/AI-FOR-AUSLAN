# AI-FOR-AUSLAN

**Translating Australian Sign Language (Auslan) videos into fluent English sentences using Deep Learning.**

> Runner-Up | Coding Fest 2025  
> Creativity Unlocker Award  
> Team NeuroSigns: Hai Son Nguyen, Hengzhou Li, Mahak Saini, Sourav Suresh Shinde

---

## Project Overview

**AI-FOR-AUSLAN** is a deep learning project developed to **translate Australian Sign Language (Auslan)** videos into natural language English text. 

Leveraging the **Auslan-Daily dataset** featuring 13,214 video clips from the children's TV show *Sally & Possum*, our team built a **sequence-to-sequence model with attention** to perform **sentence-level translation**. The system processes **skeletal keypoints** (hands and body) from video frames to generate fluent English output using **beam search** decoding.

This project aims to make communication more inclusive by enhancing accessibility for the **Deaf and Hard of Hearing (DHoH)** community.

---

## What the Model Does

- Converts Auslan videos into **complete English sentences**
- Translates at the **sentence level**, not just word-level
- Enhances **accessibility** for the DHoH community
- Demonstrates the power of AI for **social good**

---

## Who It’s For

- Deaf and Hard of Hearing individuals  
- Accessibility & Language Service Providers  
- Researchers in Sign Language Processing  
- Educators & Inclusion Advocates  

---

## How It Works

| Component              | Description                                                           |
|------------------------|-----------------------------------------------------------------------|
| **Input**              | Auslan video clips                                                    |
| **Feature Extraction** | Skeletal keypoints (hands + body) per frame                           |
| **Model**              | Seq2Seq RNN with Attention                                            |
| **Decoding**           | Beam Search (Beam size = 4)                                           |
| **Output**             | Fluent English sentence                                               |

---
## Models Tested

We experimented with multiple architectures to identify the best-performing model:

### 1. **Vanilla LSTM-based Seq2Seq**

- Encoder-decoder LSTM
- Word-level output tokens
- Trained for 100 epochs
- BLEU@4: **~3.12**

### 2. **LSTM with Attention (Final Model)**

- Sequence-to-sequence with Bahdanau-style attention
- Beam Search decoder with size = 4
- Used both **hand** and **body** skeletal keypoints
- BLEU@4: **4.90**
- **Best Epoch:** `Epoch 63` (selected based on validation loss and BLEU)

### 3. **Transformer-based Seq2Seq (Future Work)**

- Tested on small-scale subset
- Promising, but underperforms LSTM + Attention in current setting
- Will be improved in future versions


## Tech Stack

- **Python 3.11.3**
- **PyTorch 2.3.0** & **TorchText 0.6.0**
- Trained on **13,214** annotated video clips
- Used **RGB frames** and **lower-cased subtitles**
- Achieved **BLEU@4 score: 4.90**
- Trained over **100 epochs**

---

## 📈 Results

| Model               | BLEU@4    | Best Epoch | Notes                              |
|---------------------|-----------|------------|------------------------------------|
| LSTM (no attention) | ~3.12     | 84         | Lacks context awareness            |
| LSTM + Attention    | **4.90**  | **63**     | Final model with best results      |
| Transformer (WIP)   | ~2.5      | -          | Under-trained, needs more tuning   |

---

## 🗂 Dataset Access

The **Auslan-Daily dataset** used in this project is large and cannot be included directly in this repository.

### 📎 Download via Google Drive:
*https://drive.google.com/drive/folders/1bR_WWsXW83UVK3vsMppGATdo-1QE6flc*

### 📁 Folder contents:
- `train.pkl` / `val.pkl` / `test_feature.pkl`: Processed keypoint data  
- `train.csv`: Sentence annotations  
- `vocab/`: Vocabulary files for tokenization  
- `config.yaml`: Model configuration settings  

---

## ⚙️ Dataset Setup Instructions

All steps for setting up the dataset (including downloading, unpacking, and loading into the training pipeline) are clearly documented in:

📓 **Colab_Env_Setup.ipynb**

> 💡 Open the notebook and follow step-by-step instructions to:
> - Mount Google Drive  
> - Download & unzip the dataset  
> - Prepare environment & dependencies  
> - Load data for training and evaluation  

---
