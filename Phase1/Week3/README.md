# 📘 Week 3 — Transformers + HuggingFace
### Project: Sentiment Classifier (DistilBERT) + Text Generation (GPT-2)

---

## 📌 Overview
Week 3 focuses on modern NLP using Transformer-based architectures.  
The goal is to understand the Transformer workflow, work with HuggingFace models, and build two practical NLP systems:

1. **DistilBERT Sentiment Classifier**  
2. **GPT-2 Text Generator**

All implementation and detailed exploration are inside the Jupyter notebooks.

---

## 📅 Week 3 

### Transformers Basics
- Understand the Transformer workflow  
- Learn tokenization, embeddings, attention flow  
- Set up the HuggingFace environment  
- Notebook: *Transformer basics*

### HuggingFace Pipelines
- Run pretrained NLP models for inference  
- Test sentiment analysis, text generation  
- Notebook: *Pipelines demonstration*

### Fine-Tuning DistilBERT
- Load IMDb dataset  
- Tokenize and prepare dataset  
- Fine-tune DistilBERT for sentiment classification  
- Save model + evaluation metrics  
- Notebook: *DistilBERT fine-tuning*

### GPT-2 Text Generation (Optional Finetune)
- Use GPT-2 for free-form text generation  
- Optional: finetune on small custom corpus  
- Notebook: *GPT-2 generation*

---

## 📁 Folder Structure

'''

Week3_Transformers/
│
├── notebooks/
│ ├── 1_transformer_basics.ipynb
│ ├── 2_huggingface_pipelines.ipynb
│ ├── 3_distilbert_finetuning.ipynb
│ └── 4_gpt2_generation.ipynb
│
├── models/
│ ├── distilbert_sentiment/
│ └── gpt2_model/ (optional)
│
├── app/
│ ├── app.py
│ └── requirements.txt
│
└── README.md

'''


---

## 📌 Deliverables for Week 3
- Fully organized Transformer project folder  
- Fine-tuned DistilBERT sentiment classifier  
- GPT-2 text generation demo  
- Streamlit app for inference  
- Documentation + notebooks
