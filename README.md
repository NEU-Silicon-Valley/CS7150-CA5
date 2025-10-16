# **Coding Assignment 5: Generative Deep Learning**

</br>

## **Overview**

This assignment explores two fundamental approaches to generative modeling: **sequential generation** with language models and **latent space generation** with variational autoencoders. You'll implement architectures from scratch, understand their theoretical foundations, and see how modern techniques improve performance.


---

## **Notebooks**

### **5.1 - Language Model Architectures: RNNs to Transformers**

Implement and compare foundational architectures for text generation, from simple RNNs to Transformers, and discover how production systems use subword tokenization.

**Topics:**
- Recurrent Neural Networks (Elman cells, BPTT)
- Transformer architecture (attention, causal masking, positional encoding)
- Computational efficiency analysis (FLOPs, parallelization)
- Real-world tokenization (SentencePiece, BPE)

**Point Breakdown (60 points + 10 extra credit):**

| Component | Coding | Questions/Analysis | Extra Credit |
|-----------|--------|-------------------|--------------|
| **RNN Implementation** | 10 pts | 10 pts | +5 pts (Multi-layer) |
| **Transformer Implementation** | 10 pts | 15 pts | — |
| **Subword Tokenization** | 9 pts | 6 pts | +5 pts (Transformer + subword) |

---

### **5.2 - Variational Autoencoders**

Build a VAE from scratch to understand how generative models learn continuous latent representations and enable sampling of new data points.

**Topics:**
- Encoder-decoder architectures
- Reparameterization trick (backprop through sampling)
- KL divergence (closed-form derivation)
- Latent space visualization and generation

**Point Breakdown (15 points):**

| Component | Coding | Reflection |
|-----------|--------|-----------|
| **VAE Implementation** | 8 pts | 7 pts |

---

## **Learning Objectives**

By completing this assignment, you will:
1. Implement core generative architectures (RNN, Transformer, VAE)
2. Understand attention mechanisms and self-attention
3. Master the reparameterization trick for probabilistic models
4. Apply modern NLP preprocessing (subword tokenization)
5. Analyze architectural trade-offs (sequential vs parallel, char-level vs subword)
6. Evaluate generative model quality through visualization and metrics

---

## **Setup & Environment**

### **Installation:**
```bash
pip install torch numpy matplotlib datasets ipywidgets sentencepiece tqdm
```

---

## **Submission Instructions**

Submit **both completed notebooks** by the deadline.

### **Deliverables:**
- `FirstName_5.1_LanguageModels.ipynb`
- `FirstName_5.2_VAE.ipynb`

### **Submission Options:**

**Option 1 - Individual files:**
Upload both `.ipynb` files separately to Canvas

**Option 2 - Zipped:**
Create `FirstName_CA5.zip` containing both notebooks


### **Requirements:**
- All TODO sections must be filled in with working code
- All questions answered in markdown cells (marked "YOUR ANSWER:")
- Generated outputs visible (loss plots, sample text, visualizations)
- Code runs without errors from top to bottom

**Submission :** Submit the file(s) as a direct **reply** to the [*coding assignment module of week 7*](#) on Canvas.

---

## **Resources**

**Papers Referenced:**
- RNNs: Elman (1990) - Finding Structure in Time
- Transformers: Vaswani et al. (2017) - Attention Is All You Need
- VAEs: Kingma & Welling (2014) - Auto-Encoding Variational Bayes

**Additional Reading:**
- [Andrej Karpathy's nanoGPT](https://github.com/karpathy/nanoGPT)
- [ARENA Transformer Tutorial](https://arena-chapter1-transformer-interp.streamlit.app/)
- [VAE Tutorial by Carl Doersch](https://arxiv.org/abs/1606.05908)

---

## **Academic Integrity**

- **Collaboration:** Follow course syllabus policy on collaboration
- **Citations:** Credit all external resources, discussions, and AI assistance used
- **Code reuse:** Cite any code adapted from online sources
- **Individual work:** Submit your own implementations - copying code is prohibited

---

**Good luck exploring generative models!** 