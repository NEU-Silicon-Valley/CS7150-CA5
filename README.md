# **Coding Assignment 5: Medical Image Segmentation and Generative Models**

</br>

## **Overview**

This assignment has two parts, each submitted on its own:

- **Part A (5a): Medical image segmentation with U-Net.** You'll explore a multi-modal brain MRI
  dataset, then build on a U-Net to segment brain tumors. Runs on the Explorer HPC, where the data
  lives.
- **Part B (5b): Generative models.** You'll implement a VAE, a GAN, and a diffusion model on the
  same toy distribution, then scale diffusion up to images. Runs anywhere.

Do Part A first. The MNIST diffusion model in 5b.4 is a U-Net, the same kind of encoder–decoder
with skip connections that you train in 5a.2.

---

## **Part A — 5a: Medical Image Segmentation with U-Net**

In previous assignments you built CNNs for classification. Part A moves to a harder and more
impactful task, **semantic segmentation**: predicting a label for every pixel. You'll train and
evaluate a U-Net that segments brain tumors from multi-modal MRI scans, working through the full
workflow of a medical imaging project from exploring the data to experimenting with the model.

### **About the dataset: BraTS 2020**

We use the **[BraTS 2020 (Brain Tumor Segmentation) dataset](https://www.kaggle.com/datasets/awsaf49/brats20-dataset-training-validation)**,
a challenging and widely used benchmark in medical imaging. Each patient case includes four
co-registered MRI modalities:
* T1-weighted (T1)
* Post-contrast T1-weighted (T1ce)
* T2-weighted (T2)
* T2-weighted FLAIR (Fluid-Attenuated Inversion Recovery)

The goal is to use these scans to predict the location and extent of gliomas, segmenting regions
such as the necrotic core, edema, and the enhancing tumor.

**You will learn to:**
* Understand and preprocess multi-modal medical imaging data (NIfTI format, MRI sequences)
* Train and modify a U-Net for semantic segmentation in PyTorch
* Evaluate segmentation models with the Dice coefficient and Jaccard index (IoU)
* Experiment with loss functions, modalities, and slice sampling to improve performance
* Move a model from binary to multi-class segmentation

### **5a.1 — Data Exploration for Brain MRIs**

A guided tour of the BraTS 2020 dataset with **13 questions**. For questions 1–11 you only run the
provided cells and answer from what you observe; no coding is needed. Some are domain-specific, so
focus on careful observation rather than hunting for a single "correct" answer. Questions 12 and 13
ask you to modify a code cell and visualize the result.

**Point breakdown (10 points):**

| Questions | Points |
|-----------|--------|
| 1–3 — Modalities and label values (1 pt each) | 3 pts |
| 4–5 — How the modalities relate (graded together) | 1 pt |
| 6–7 — Intensity ranges, and how to handle them (graded together) | 1 pt |
| 8–9 — Tumor regions and their labels (graded together) | 1 pt |
| 10–11 — Preprocessing steps, and why each matters (graded together) | 1 pt |
| 12 — The segmentation mask across all slices | 2 pts |
| 13 — Middle slices vs. every slice | 1 pt |

### **5a.2 — Brain Tumor Segmentation with U-Net**

Train a baseline U-Net, then work through **7 experimental questions**. Each one modifies the
baseline and comes with a code skeleton, `TODO` sections, and hints.

**Point breakdown (20 points):**

| Question | Points |
|----------|--------|
| 1 — Jaccard loss | 2 pts |
| 2 — Tracking Dice and Jaccard | 2 pts |
| 3 — A different MRI modality | 2 pts |
| 4 — Multiple slices | 3 pts |
| 5 — Multi-modal input | 4 pts |
| 6 — Multi-class segmentation | 5 pts |
| 7 — Reflection | 2 pts |

---

## **Part B — 5b: Generative Models**

In CA4 you built **autoregressive** models, which generate a sequence one token at a time, each
conditioned on the ones before. Part B takes the other route, the **latent-variable** approach: model
the distribution as a process or function $f$ that transforms a boring distribution $z$ (e.g. a
random normal vector) into an interesting distribution $x = f(z)$ that imitates the target.

Notebooks 5b.1–5b.3 all use the same simple "swiss roll" target distribution, so you can compare the
three methods directly on identical data. In some of them $f$ is directly a neural network; in
others $f$ is a process with a neural network playing a particular role inside it. The final
notebook scales diffusion up to real image data.

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

---

## **Grading: 60 points here, 20 from discussion**

This assignment is worth **80 points total**.

| | Points |
|---|--------|
| Part A — notebooks 5a.1 and 5a.2 | 30 |
| Part B — notebooks 5b.1 to 5b.4 | 30 |
| Group discussion | 20 |
| **Total** | **80** |

| Notebook | Points |
|----------|--------|
| 5a.1 Data exploration | 10 |
| 5a.2 Segmentation | 20 |
| 5b.1 VAE | 7 |
| 5b.2 GAN | 8 |
| 5b.3 Diffusion | 10 |
| 5b.4 MNIST diffusion | 5 |
| **Total** | **60** |

**How to read the point markers.** Every graded item carries exactly one point value, written in
square brackets next to it. A section heading never carries a separate total on top of the items
underneath it, so you can add up the brackets as you go and get the right number.

Some closely related questions are graded as a pair. Where that happens the first one says, for
example, `[Questions 4-5: 1 point total]` and the second says `[graded with Question 4]`. You still
need to answer both.

**About the discussion.** There is one discussion for the whole assignment, held after Part B is
due, and it covers both parts. You'll be in a small group of about three students. We'll walk
through parts of the assignment together and ask you to talk through your own work: why you took a
particular approach, what gave you trouble, what you would do differently. You can also earn credit
by weighing in on a question put to someone else in your group.

Keep it relaxed. There's nothing extra to prepare beyond knowing what you submitted, and "I got
stuck on this part and looked it up" is a perfectly good answer. The point is to hear you reason
about your own code, not to catch anyone out.

---

## **Setup**

### **Part A: Explorer HPC (required)**

Part A **must be completed on the Explorer HPC**. The dataset is large and is already on the cluster
at `/courses/CS7150.202710/shared/brats20`, and the notebooks are set up to read it from there.

Start a JupyterLab session on the `courses-gpu` partition through
[Open OnDemand](https://ood.explorer.northeastern.edu/), using the course's shared Python
environment at `/courses/CS7150.202710/shared/env/cs7150`. It already has everything Part A needs
(PyTorch, `nibabel`, and so on), so there is nothing to install. The
[course Explorer guide](https://docs.google.com/document/d/1nsP4YUBajdM6j3R0tA4gRnwo9qPdRv5gTtXHYdiXCz8/)
walks through starting the session.

### **Part B: anywhere**

Each notebook has a Google Colab link at the top, and Part B also runs on Explorer with the same
environment. The swiss roll notebooks (5b.1–5b.3) are small enough for a CPU. 5b.4 trains a
convolutional model on MNIST, so a GPU helps. MNIST downloads automatically into `./data` the first
time you run it.

To run locally instead:

```bash
pip install torch torchvision numpy matplotlib tqdm
```

---

## **Submission Instructions**

Parts A and B are **two separate submissions**, each with its own zip file and its own Canvas
thread. Keep the original filenames.

| | Part A | Part B |
|---|---|---|
| **Notebooks** | `CA5a.1_BraTS2020_EDA.ipynb`<br>`CA5a.2_BrainTumorSegmentation.ipynb` | `CA5b.1_VAE.ipynb`<br>`CA5b.2_GAN.ipynb`<br>`CA5b.3_Diffusion.ipynb`<br>`CA5b.4_MNIST_Generation.ipynb` |
| **Zip file** | `CA5a-Your-Last-Name.zip` | `CA5b-Your-Last-Name.zip` |
| **Canvas thread** | Coding Assignment 5a | Coding Assignment 5b |

For example, a student named Jordan Rivera submits `CA5a-Rivera.zip` and later `CA5b-Rivera.zip`.

### **Requirements:**
- All TODO sections filled in with working code
- All questions answered in the markdown cells provided
- Generated outputs visible (loss curves, predictions, sample visualizations)
- Notebooks run top to bottom without errors

### **Where to submit:**
Post each zip file as a direct **reply** to its discussion thread on Canvas. You'll find the threads
in the **Coding Assignments** module for the week each part is due.

- Reply to the existing thread — do not start a new one.
- Attach the single zip file — do not upload the notebooks individually.
- If you cannot find a thread, check the course Canvas page or contact the TA (see *Getting Help*).

---

## **Resources**

**Papers referenced:**
- U-Net: Ronneberger, Fischer and Brox (2015) — [*U-Net: Convolutional Networks for Biomedical Image Segmentation*](https://arxiv.org/abs/1505.04597)
- BraTS: Menze et al. (2015) — *The Multimodal Brain Tumor Image Segmentation Benchmark (BRATS)*
- VAEs: Kingma and Welling (2014) — [*Auto-Encoding Variational Bayes*](https://arxiv.org/abs/1312.6114)
- GANs: Goodfellow et al. (2014) — [*Generative Adversarial Networks*](https://arxiv.org/abs/1406.2661)
- Diffusion: Ho, Jain and Abbeel (2020) — [*Denoising Diffusion Probabilistic Models*](https://arxiv.org/abs/2006.11239)

**Additional reading:**
- [VAE Tutorial by Carl Doersch](https://arxiv.org/abs/1606.05908)
- [Lilian Weng's Diffusion Models Blog](https://lilianweng.github.io/posts/2021-07-11-diffusion-models/)
- [Wasserstein GAN](https://arxiv.org/abs/1701.07875) by Arjovsky et al. (2017)

---

## **Getting Help**

If you hit a problem with the notebooks, spot an error, or have a question about the setup, please
reach out. Email me at **[patel.pranav2@northeastern.edu](mailto:patel.pranav2@northeastern.edu)**
or send me a message on Microsoft Teams.

---

## **Academic Integrity**

- **Collaboration:** Follow the course syllabus policy on collaboration
- **Citations:** Credit any external resources, discussions, and AI assistance you used
- **Code reuse:** Cite any code adapted from online sources
- **Individual work:** Submit your own implementations — copying code is prohibited
