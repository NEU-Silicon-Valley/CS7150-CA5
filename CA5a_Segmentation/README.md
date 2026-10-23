# **Coding Assignment 5a: Medical Image Segmentation with U-Net**

</br>

This is **Part A** of CA5. Part B is in [`../CA5b_GenerativeModels/`](../CA5b_GenerativeModels/),
and the [main README](../README.md) explains how the whole assignment is graded, including the
group discussion.

## **Overview**

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

### **You will learn to:**
* Understand and preprocess multi-modal medical imaging data (NIfTI format, MRI sequences)
* Train and modify a U-Net for semantic segmentation in PyTorch
* Evaluate segmentation models with the Dice coefficient and Jaccard index (IoU)
* Experiment with loss functions, modalities, and slice sampling to improve performance
* Move a model from binary to multi-class segmentation

---

## **Notebooks (30 points)**

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

**How to read the point markers.** Every graded item carries exactly one point value, written in
square brackets next to it. A section heading never carries a separate total on top of the items
underneath it, so you can add up the brackets as you go and get the right number.

Some closely related questions in 5a.1 are graded as a pair. Where that happens the first one says,
for example, `[Questions 4-5: 1 point total]` and the second says `[graded with Question 4]`. You
still need to answer both.

---

## **Setup: Explorer HPC (required)**

Part A **must be completed on the Explorer HPC**. The dataset is large and is already on the cluster
at `/courses/CS7150.202710/shared/brats20`, and the notebooks are set up to read it from there.

Start a JupyterLab session on the `courses-gpu` partition through
[Open OnDemand](https://ood.explorer.northeastern.edu/), using the course's shared Python
environment at `/courses/CS7150.202710/shared/env/cs7150`. It already has everything Part A needs
(PyTorch, `nibabel`, and so on), so there is nothing to install. The
[course Explorer guide](https://docs.google.com/document/d/1nsP4YUBajdM6j3R0tA4gRnwo9qPdRv5gTtXHYdiXCz8/)
walks through starting the session.

---

## **Submission Instructions**

### **Deliverables:**
- `CA5a.1_BraTS2020_EDA.ipynb`
- `CA5a.2_BrainTumorSegmentation.ipynb`

Keep the original filenames. Zip both completed notebooks into a single archive named:

```
CA5a-Your-Last-Name.zip
```

For example, a student named Jordan Rivera submits `CA5a-Rivera.zip`.

### **Requirements:**
- All TODO sections filled in with working code
- All questions answered in the markdown cells provided
- Generated outputs visible (loss curves, predictions, visualizations)
- Notebooks run top to bottom without errors

### **Where to submit:**
Post your zip file as a direct **reply** to the **Coding Assignment 5a** discussion thread on
Canvas. You'll find that thread in the **Coding Assignments** module for the week this part is due.

- Reply to the existing thread — do not start a new one.
- Attach the single zip file — do not upload the notebooks individually.
- If you cannot find the thread, check the course Canvas page or contact the TA (see the
  [main README](../README.md)).

---

## **Resources**

- U-Net: Ronneberger, Fischer and Brox (2015) — [*U-Net: Convolutional Networks for Biomedical Image Segmentation*](https://arxiv.org/abs/1505.04597)
- BraTS: Menze et al. (2015) — *The Multimodal Brain Tumor Image Segmentation Benchmark (BRATS)*
