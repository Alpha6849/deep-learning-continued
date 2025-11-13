# Phase 1 — Deep Learning Foundations (4 Weeks)

This phase focuses on understanding the *core building blocks* of Deep Learning through hands-on projects.

---

## 📅 Week Structure

| Week | Topic Focus | Project | Status |
|------|------------|---------|--------|
| **Week 1** | Sequence Models (RNN → LSTM → GRU) | Text Generation Model | Done |
| Week 2 | Computer Vision (CNNs + Grad-CAM) | Image Classifier + Explainability | Done |
| Week 3 | Transformers + NLP | Sentiment / Chat Model using DistilBERT / GPT-2 | ⏳ Pending |
| Week 4 | Autoencoders + GAN + Deployment | AE + GAN + Model Serving (FastAPI + UI) | ⏳ Pending |

---

##  Week 1 Summary (What I Learned)
- Text is **sequential data**, so order matters.
- RNN remembers previous characters while reading.
- LSTM improves RNN by **remembering longer patterns**.
- Temperature controls **creativity vs stability** during text generation.
- GRU is like LSTM but **simpler and trains faster**.

### Project Output
- LSTM text generator trained for ~6 epochs
- GRU model trained for comparison
- Models saved and re-loaded correctly
- Generated Shakespeare-style text with temperature tuning

Notes are inside **Week1/notes.md**

## Week 2 – CNNs & Transfer Learning
- Full plant disease classifier pipeline
- Baseline CNN → 50% accuracy
- Transfer learning with ResNet50 → 95%
- Fine-tuning ResNet50 → 98%
- Grad-CAM explainability

Notes are inside **Week2/notes.md**


