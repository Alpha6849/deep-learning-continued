# Phase 1 — Deep Learning Foundations (4 Weeks)

This phase focuses on understanding the *core building blocks* of Deep Learning through hands-on projects.

---

## 📅 Week Structure

| Week | Topic Focus | Project | Status |
|------|------------|---------|--------|
| **Week 1** | Sequence Models (RNN → LSTM → GRU) | Text Generation Model | ✔ Done |
| **Week 2** | Computer Vision (CNNs + Grad-CAM) | Image Classifier + Explainability | ✔ Done |
| **Week 3** | Transformers + NLP | Sentiment / Chat Model using DistilBERT / GPT-2 | 🟡 In Progress |
| **Week 4** | Autoencoders + GAN + Deployment | AE + GAN + Model Serving (FastAPI + UI) | ⏳ Pending |

---

## 📘 Week 1 — Sequence Models (RNN, LSTM, GRU)

### What I Learned
- Text is **sequential**, order matters.
- RNN keeps memory but forgets long-term context.
- LSTM improves long-term memory using **gates**.
- GRU is simpler & faster than LSTM.
- Temperature controls **creativity vs stability** in text generation.

### Project Output
- Character-level text generator (LSTM + GRU)
- Temperature-based sampling implemented
- Saved & reloaded models
- Generated Shakespeare-style text

📄 Notes: **Week1/notes.md**

---

## 📘 Week 2 — CNNs + Transfer Learning

### What I Learned
- Convolution filters detect patterns: edges → textures → shapes.
- CNN architecture pipeline: Conv → Pool → Dense.
- Transfer Learning massively speeds up training.
- Grad-CAM helps **visualize what the model is focusing on**.

### Project Output
- Baseline CNN → ~50%
- ResNet50 TL → ~95%
- ResNet50 Fine-tuned → ~98%
- Grad-CAM heatmaps for interpretability

📄 Notes: **Week2/notes.md**

---

## 📘 Week 3 — Transformers + NLP (In Progress)

### What I’m Learning Now
- Transformer architecture basics (Q/K/V, Attention, Multi-Head Attention)
- Positional Encoding and why Transformers need it
- Tokenization using subwords (WordPiece / BPE)
- HuggingFace **pipelines** for quick NLP tasks
- Fine-tuning DistilBERT for sentiment classification
- GPT-2 text generation basics (temperature, top-k, top-p)

### Project Deliverables
- **Notebook 1:** Transformer Basics (Self-Attention from scratch)
- **Notebook 2:** HuggingFace Pipelines (Sentiment, QA, etc.)
- **Notebook 3:** Fine-tuning DistilBERT for classification
- **Notebook 4:** GPT-2 Text Generation demo

📄 Notes: **Week3/notes.md**

---

## 📘 Week 4 — Autoencoders, GANs, and Deployment (Upcoming)
- Autoencoder fundamentals  
- Latent space visualization  
- GAN architecture (Generator + Discriminator)  
- Training a small GAN  
- Deploying models using FastAPI / Streamlit  
- Building a simple UI for inference  

📄 Notes: Coming soon




