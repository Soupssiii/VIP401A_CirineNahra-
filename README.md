# VIP401A - MS Lesion Segmentation Pipeline

Deep learning pipeline for **3D MRI Multiple Sclerosis (MS) lesion segmentation**, including preprocessing, model training, residual architecture improvements, sliding-window inference, and postprocessing-based visualization.

---

## Author

**Cirine Nahra**  
American University of Beirut (AUB)  
VIP 401A - Final Submission

---

## Project Overview

This repository contains the complete development workflow of an MS lesion segmentation project:

- MRI preprocessing and data preparation
- Baseline 3D U-Net experimentation
- Residual 3D U-Net architecture refinement
- Patch-based training strategy
- Sliding-window inference on 3D volumes
- Dice-based quantitative evaluation
- Postprocessing and slice-level qualitative analysis
- Hyperparameter grid-search experimentation

---

## Recommended Notebook

> **Primary notebook to read and run:**  
> `CCN04_MS_Lesion_Segmentation_FullPipeline.ipynb`

This is the **FINAL and MOST ORGANIZED** notebook in the repository and the one recommended for reviewers, instructors, and reproducibility.

It includes:

- Cleaned and structured code
- Clear comments and section titles
- Architecture explanations
- Full training workflow
- Checkpoint loading and resume workflow
- Residual architecture implementation
- Inference pipeline
- Evaluation metrics
- Postprocessing
- Visualization pipeline

---

## Notebook Guide

### 1) `CCN04_MS_Lesion_Segmentation_FullPipeline.ipynb` (Final Polished Version)

**Role:** Final production-quality notebook for the project.

**What it contains:**

- End-to-end pipeline from loading to evaluation
- Original modified 3D U-Net and residual 3D U-Net
- Training and resume training utilities
- Sliding-window inference and patient-level analysis
- Postprocessing and visualization exports

**Use this notebook when:**

- You want the complete and most reliable workflow
- You want to reproduce final results
- You are reviewing the final submission structure

---

### 2) `VIP401A_ccn.ipynb` (Baseline / Early Version)

**Role:** Original baseline notebook from early project stages.

**What it represents:**

- Initial architecture implementation
- Early experimental iterations
- Smaller-scale setup for initial validation

**Use this notebook when:**

- You want to understand the project starting point
- You want to compare baseline setup versus final improvements

---

### 3) `VIP401A_ccn_gridsearch_500epochs.ipynb` (Grid Search + Long Training)

**Role:** Hyperparameter experimentation notebook.

**What it contains:**

- Learning-rate and weight-decay testing
- Long training experiments (including 500-epoch runs)
- Checkpoint-based evaluation during hyperparameter tuning

**Use this notebook when:**

- You want to inspect optimization strategy
- You want to trace how final training parameters were selected

**Best configuration identified:**

- Learning Rate: `3e-4`
- Weight Decay: `1e-6`

---

### 4) `Full_Pipeline_Before_Comments_and_Edits.ipynb` (Pre-Cleanup Version)

**Role:** Earlier full-pipeline version before documentation cleanup.

**What it represents:**

- Pre-polish structure and code layout
- Historical snapshot before comments/organizational improvements

**Use this notebook when:**

- You want historical comparison with the final polished notebook
- You need reference to earlier formatting/state of the full pipeline

---

## Version Summary Table

| Notebook | Version Type | Main Purpose | Status |
|---|---|---|---|
| `CCN04_MS_Lesion_Segmentation_FullPipeline.ipynb` | Final organized version | End-to-end final pipeline, training, inference, evaluation, postprocessing | **Recommended** |
| `VIP401A_ccn.ipynb` | Baseline version | Early architecture and initial experiments | Legacy / baseline |
| `VIP401A_ccn_gridsearch_500epochs.ipynb` | Experimental tuning version | Hyperparameter search and long-training studies | Experimental |
| `Full_Pipeline_Before_Comments_and_Edits.ipynb` | Pre-cleanup full pipeline | Historical reference before documentation improvements | Archived reference |

---

## PDF Versions

The `PDFS` folder contains exported static versions of the notebooks.

**Purpose of the PDF files:**

- Easier reading without opening notebook environments
- Submission and review convenience
- Static documentation for archival/reference
- Direct content mirror of corresponding notebooks

---

## Dataset Inputs

Each patient sample includes:

- Baseline MRI volume
- Follow-up MRI volume
- Ground-truth lesion mask

Expected naming convention:

- `baseline_0p5_norm_padded.nii.gz`
- `followup_registered_0p5_norm_padded.nii.gz`
- `label_0p5_padded.nii.gz`

---

## Model and Training Snapshot

### Architecture Progression

- **Baseline:** Modified 3D U-Net
  - Encoder-decoder structure
  - Instance normalization
  - LeakyReLU activations
  - Skip connections
- **Improved:** Residual 3D U-Net
  - Residual blocks
  - Dropout in deeper levels
  - Improved gradient flow and stability

### Core Training Setup

| Parameter | Value |
|---|---|
| Patch Size | `64 x 64 x 64` |
| Stride | `32 x 32 x 32` |
| Learning Rate | `3e-4` |
| Weight Decay | `1e-6` |
| Threshold | `0.5` |
| Loss | Dice + BCE |

---

## Postprocessing and Visualization

Postprocessing pipeline supports:

- Slice-level lesion inspection
- Ground-truth vs prediction comparison
- Overlay visualization
- Patient-level Dice summaries

Overlay color convention:

- Green -> Ground Truth
- Red -> Prediction
- Yellow -> Overlap

---

## Saved Outputs

Generated artifacts typically include:

- Prediction masks
- Training checkpoints
- Training history curves/logs
- Patient-level Dice summaries
- Slice-level PNG visualizations

---

## How to Run

Use the workflow below (recommended with the final notebook):

1. **Open in Google Colab**  
   Upload or open `CCN04_MS_Lesion_Segmentation_FullPipeline.ipynb`.

2. **Mount Google Drive**  
   Mount Drive to access datasets, checkpoints, and output directories.

3. **Install dependencies**  
   Run the package installation cell (or execute):

   ```bash
   pip install torch torchvision nibabel numpy pandas matplotlib
   ```

4. **Run setup cells**  
   Execute environment/configuration cells and path setup sections.

5. **Load data**  
   Confirm patient folder structure and input file naming are correct.

6. **Load checkpoints**  
   Restore pre-trained model checkpoints when available (or train from scratch if needed).

7. **Run inference**  
   Execute sliding-window inference to generate prediction masks.

8. **Run postprocessing and visualization**  
   Generate overlays, slice-level analyses, and patient-level performance summaries.

---

## Repository Usage Notes

- For most users, start directly with `CCN04_MS_Lesion_Segmentation_FullPipeline.ipynb`.
- Use the other notebooks to understand project evolution, baselines, and tuning experiments.
- Use PDFs for quick reading/review when interactive execution is not required.
