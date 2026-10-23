# **Coding Assignment 5b: Generative Models**

</br>

This is **Part B** of CA5. Part A is in [`../CA5a_Segmentation/`](../CA5a_Segmentation/), and the
[main README](../README.md) explains how the whole assignment is graded, including the group
discussion.

## **Overview**

In CA4 you built **autoregressive** models, which generate a sequence one token at a time, each
conditioned on the ones before. Part B takes the other route, the **latent-variable** approach: model
the distribution as a process or function $f$ that transforms a boring distribution $z$ (e.g. a
random normal vector) into an interesting distribution $x = f(z)$ that imitates the target.

Notebooks 5b.1–5b.3 all use the same simple "swiss roll" target distribution, so you can compare the
three methods directly on identical data. In some of them $f$ is directly a neural network; in
others $f$ is a process with a neural network playing a particular role inside it. The final
notebook scales diffusion up to real image data, using a U-Net like the one from Part A.

Work through the notebooks in order; each one refers back to the ones before it.

---

## **Notebooks (30 points)**

### **5b.1 — Variational Autoencoders**

Build a VAE to see how a generative model learns a continuous latent representation that you can
sample new data from.

**Topics:** encoder–decoder architectures, the reparameterization trick, the closed-form KL
divergence, latent space visualization and generation.

**Point breakdown (7 points):**

| Component | Points |
|-----------|--------|
| Reparameterization trick | 2 pts |
| VAE loss (closed-form KL) | 2 pts |
| Reflection questions (3) | 3 pts |

### **5b.2 — Generative Adversarial Networks**

Implement the adversarial training objective and explore the learned latent space.

**Topics:** the minimax game, discriminator and generator losses, training stability and mode
collapse, latent space interpolation.

**Point breakdown (8 points):**

| Component | Points |
|-----------|--------|
| Discriminator loss | 2 pts |
| Generator loss | 1 pt |
| Latent interpolation | 1 pt |
| Analysis questions (4) | 4 pts |

### **5b.3 — Diffusion Models**

Implement the forward (noising) and reverse (denoising) processes of a DDPM-style diffusion model.

**Topics:** the forward process and noise schedules, the reverse denoising step, the noise
prediction objective, computational cost.

**Point breakdown (10 points):**

| Component | Points |
|-----------|--------|
| Forward diffusion | 2 pts |
| Reverse step | 2 pts |
| Training loss | 1 pt |
| Analysis questions (4) | 5 pts |

### **5b.4 — MNIST Diffusion Generation**

Apply diffusion to image data: implement the training loop and improve sample quality. Builds
directly on 5b.3, so complete that notebook first.

**Topics:** convolutional architectures for diffusion, the training loop, tuning for sample quality.

**Point breakdown (5 points):**

| Component | Points |
|-----------|--------|
| Training step | 1 pt |
| Improving sample quality | 1 pt |
| Analysis questions (3) | 3 pts |

**How to read the point markers.** Every graded item carries exactly one point value, written in
square brackets next to it. A section heading never carries a separate total on top of the items
underneath it, so you can add up the brackets as you go and get the right number.

---

## **Setup: anywhere**

Each notebook has a Google Colab link at the top, and Part B also runs on the Explorer HPC with the
course's shared environment at `/courses/CS7150.202710/shared/env/cs7150`. The swiss roll notebooks
(5b.1–5b.3) are small enough for a CPU. 5b.4 trains a convolutional model on MNIST, so a GPU helps.
MNIST downloads automatically into `./data` the first time you run it.

To run locally instead:

```bash
pip install torch torchvision numpy matplotlib tqdm
```

---

## **Submission Instructions**

### **Deliverables:**
- `CA5b.1_VAE.ipynb`
- `CA5b.2_GAN.ipynb`
- `CA5b.3_Diffusion.ipynb`
- `CA5b.4_MNIST_Generation.ipynb`

Keep the original filenames. Zip all four completed notebooks into a single archive named:

```
CA5b-Your-Last-Name.zip
```

For example, a student named Jordan Rivera submits `CA5b-Rivera.zip`.

### **Requirements:**
- All TODO sections filled in with working code
- All questions answered in the markdown cells provided
- Generated outputs visible (loss plots, sample visualizations)
- Notebooks run top to bottom without errors

### **Where to submit:**
Post your zip file as a direct **reply** to the **Coding Assignment 5b** discussion thread on
Canvas. You'll find that thread in the **Coding Assignments** module for the week this part is due.

- Reply to the existing thread — do not start a new one.
- Attach the single zip file — do not upload the notebooks individually.
- If you cannot find the thread, check the course Canvas page or contact the TA (see the
  [main README](../README.md)).

---

## **Resources**

**Papers referenced:**
- VAEs: Kingma and Welling (2014) — [*Auto-Encoding Variational Bayes*](https://arxiv.org/abs/1312.6114)
- GANs: Goodfellow et al. (2014) — [*Generative Adversarial Networks*](https://arxiv.org/abs/1406.2661)
- Diffusion: Ho, Jain and Abbeel (2020) — [*Denoising Diffusion Probabilistic Models*](https://arxiv.org/abs/2006.11239)

**Additional reading:**
- [VAE Tutorial by Carl Doersch](https://arxiv.org/abs/1606.05908)
- [Lilian Weng's Diffusion Models Blog](https://lilianweng.github.io/posts/2021-07-11-diffusion-models/)
- [Wasserstein GAN](https://arxiv.org/abs/1701.07875) by Arjovsky et al. (2017)
