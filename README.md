# **Coding Assignment 5: Generative Deep Learning**

</br>

## **Overview**

This assignment covers the two dominant families of generative models. You'll start with the
**autoregressive** approach, which factors a distribution into a sequence of tokens, each modeled
as a conditional probability given the previous ones — the approach behind modern language models.
You'll then move to the **latent-variable** approach, which models the distribution as a process or
function $f$ that transforms a boring distribution $z$ (e.g. a random normal vector) into an
interesting distribution $x = f(z)$ that imitates the target.

Notebooks 5.2–5.4 all use the same simple "swiss roll" target distribution, so you can compare the
three latent-variable methods directly on identical data. You will see that in some methods $f$ is
directly a neural network, whereas in others $f$ is a process that incorporates a neural network
playing a particular role within it. The final notebook scales diffusion up to real image data.

---

## **Notebooks**

### **5.1 — Language Model Architectures: RNNs to Transformers**

Implement and compare foundational architectures for text generation, from simple RNNs to
Transformers, and discover how production systems use subword tokenization.

**Topics:**
- Recurrent Neural Networks (Elman cells, BPTT)
- Multi-layer RNN architectures
- Transformer architecture (attention, causal masking, positional encoding)
- Computational efficiency analysis (FLOPs, parallelization)
- Real-world tokenization (SentencePiece, BPE)

**Point Breakdown (40 points + 4 extra credit):**

| Component | Coding | Questions/Analysis | Extra Credit |
|-----------|--------|-------------------|--------------|
| **RNN Implementation** | 7 pts | 5 pts | — |
| **Multi-Layer RNN** | 4 pts | — | — |
| **Transformer Implementation** | 7 pts | 9 pts | — |
| **Subword Tokenization** | 4 pts | 4 pts | +4 pts (Transformer + subword) |

---

### **5.2 — Variational Autoencoders**

Build a VAE from scratch to understand how generative models learn continuous latent
representations and enable sampling of new data points.

**Topics:**
- Encoder-decoder architectures
- Reparameterization trick (backprop through sampling)
- KL divergence (closed-form derivation)
- Latent space visualization and generation

**Point Breakdown (10 points):**

| Component | Coding | Reflection |
|-----------|--------|-----------|
| **VAE Implementation** | 5 pts | 5 pts |

---

### **5.3 — Generative Adversarial Networks (GANs)**

Implement the adversarial training objective and explore the learned latent space.

**Topics:**
- Minimax game formulation
- Discriminator and Generator loss functions
- Training stability and mode collapse
- Latent space interpolation

**Point Breakdown (10 points):**

| Component | Coding | Questions/Analysis |
|-----------|--------|--------------------|
| **Discriminator Loss** | 2 pts | — |
| **Generator Loss** | 1 pt | — |
| **Latent Interpolation** | 2 pts | — |
| **Analysis Questions** | — | 5 pts |

---

### **5.4 — Diffusion Models**

Implement both the forward (noising) and reverse (denoising) processes of a DDPM-style
diffusion model.

**Topics:**
- Forward diffusion process and noise scheduling
- Reverse denoising step derivation
- Noise prediction training objective
- Computational cost analysis

**Point Breakdown (13 points):**

| Component | Coding | Questions/Analysis |
|-----------|--------|--------------------|
| **Forward Diffusion** | 3 pts | — |
| **Reverse Step** | 3 pts | — |
| **Training Loss** | 2 pts | — |
| **Analysis Questions** | — | 5 pts |

---

### **5.5 — MNIST Diffusion Generation**

Apply diffusion modeling to image data, implementing the training loop and improving sample
quality. Builds directly on 5.4 — complete that notebook first.

**Topics:**
- Convolutional architectures for diffusion
- Training loop implementation
- Hyperparameter tuning for sample quality
- Architectural adaptations for image data

**Point Breakdown (7 points):**

| Component | Coding | Questions/Analysis |
|-----------|--------|--------------------|
| **Training Loop** | 2 pts | — |
| **Sample Improvement** | 2 pts | — |
| **Analysis Questions** | — | 3 pts |

---

## **Total Points: 80** (+4 extra credit)

| Notebook | Coding | Analysis | Total |
|----------|--------|----------|-------|
| 5.1 Language Models | 22 pts | 18 pts | 40 pts |
| 5.2 VAE | 5 pts | 5 pts | 10 pts |
| 5.3 GAN | 5 pts | 5 pts | 10 pts |
| 5.4 Diffusion | 8 pts | 5 pts | 13 pts |
| 5.5 MNIST Diffusion | 4 pts | 3 pts | 7 pts |
| **Total** | **44 pts** | **36 pts** | **80 pts** |

Extra credit: +4 pts (Notebook 5.1, Transformer + subword tokenization).

---

## **Learning Objectives**

By completing this assignment, you will:
1. Implement core generative architectures (RNN, Transformer, VAE, GAN, diffusion)
2. Understand attention mechanisms and self-attention
3. Master the reparameterization trick for probabilistic models
4. Apply modern NLP preprocessing (subword tokenization)
5. Contrast autoregressive and latent-variable approaches to generative modeling
6. Analyze architectural trade-offs (sequential vs parallel, char-level vs subword, adversarial vs
   likelihood-based training)
7. Apply diffusion models to real image data (MNIST)

---

## **Data Setup**

### Text (Notebook 5.1):
Downloaded automatically by the notebook.

### Swiss Roll (Notebooks 5.2–5.4):
Generated synthetically in each notebook — no external data needed.

### MNIST (Notebook 5.5):
Downloaded automatically into `./data` by `torchvision` on first use — no manual setup needed.

### **Installation:**
```bash
pip install torch torchvision numpy matplotlib datasets ipywidgets sentencepiece tqdm
```

---

## **Submission Instructions**

Submit **all five completed notebooks** by the deadline.

### **Deliverables:**
- `CA5.1_LanguageModels.ipynb`
- `CA5.2_VAE.ipynb`
- `CA5.3_GAN.ipynb`
- `CA5.4_Diffusion.ipynb`
- `CA5.5_MNIST_Generation.ipynb`

Keep the original filenames. Zip all five completed notebooks into a single archive named:

```
CA5-Your-Last-Name.zip
```

For example, a student named Jordan Rivera submits `CA5-Rivera.zip`.

### **Requirements:**
- All TODO sections must be filled in with working code
- All questions answered in markdown cells (marked "YOUR ANSWER:")
- Generated outputs visible (loss plots, sample text, sample visualizations)
- Code runs without errors from top to bottom

### **Where to submit:**
Post your zip file as a direct **reply** to the **Coding Assignment 5** discussion thread on Canvas.
You'll find that thread in the **Coding Assignments** module for the week this assignment is due.

- Reply to the existing thread — do not start a new one.
- Attach the single zip file — do not upload the notebooks individually.
- If you cannot find the thread, check the course Canvas page or contact the TA (see *Getting Help*).

---

## **Resources**

**Papers Referenced:**
- RNNs: Elman (1990) — Finding Structure in Time
- Transformers: Vaswani et al. (2017) — Attention Is All You Need
- VAEs: Kingma & Welling (2014) — Auto-Encoding Variational Bayes
- GANs: Goodfellow et al. (2014) — Generative Adversarial Networks
- Diffusion: Ho et al. (2020) — Denoising Diffusion Probabilistic Models

**Additional Reading:**
- [Andrej Karpathy's nanoGPT](https://github.com/karpathy/nanoGPT)
- [ARENA Transformer Tutorial](https://arena-chapter1-transformer-interp.streamlit.app/)
- [VAE Tutorial by Carl Doersch](https://arxiv.org/abs/1606.05908)
- [Lilian Weng's Diffusion Models Blog](https://lilianweng.github.io/posts/2021-07-11-diffusion-models/)
- [Wasserstein GAN](https://arxiv.org/abs/1701.07875) by Arjovsky et al. (2017)

---

## **Getting Help**

If you encounter any problems with the notebooks, notice any errors, or have questions about the
setup, please do not hesitate to reach out. You can email me at
**[patel.pranav2@northeastern.edu](mailto:patel.pranav2@northeastern.edu)** or send me a message on
Microsoft Teams.

---

## **Academic Integrity**

- **Collaboration:** Follow course syllabus policy on collaboration
- **Citations:** Credit all external resources, discussions, and AI assistance used
- **Code reuse:** Cite any code adapted from online sources
- **Individual work:** Submit your own implementations — copying code is prohibited

---

**Good luck exploring generative models!**
