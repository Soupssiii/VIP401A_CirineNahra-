\# VIP401A – MS Lesion Segmentation Pipeline



\## Author

\*\*Cirine Nahra\*\*  

American University of Beirut (AUB)  

VIP 401A – Final Submission



\---



\# Project Overview



This repository contains the full implementation, experiments, and postprocessing pipelines for a 3D MRI Multiple Sclerosis (MS) lesion segmentation project using deep learning.



The project focuses on:

\- MRI preprocessing

\- 3D U-Net segmentation

\- Residual 3D U-Net improvements

\- Sliding-window inference

\- Dice-based evaluation

\- Postprocessing and slice-level visualization

\- Architecture comparison experiments

\- Grid search optimization



\---



\# Repository Structure



\## 1. Collab Notebooks



\### `CCN04\_MS\_Lesion\_Segmentation\_FullPipeline.ipynb`

Main and final segmentation pipeline.



\### Contents

\- MRI loading

\- Preprocessing

\- Original Modified 3D U-Net

\- Residual 3D U-Net

\- Patch dataset generation

\- Training pipeline

\- Resume training

\- Sliding-window inference

\- Dice evaluation

\- Slice-level postprocessing

\- Visualization export

\- Patient-level analysis



\### Purpose

This is the primary notebook used for the final architecture experiments and qualitative evaluation.



\---



\### `VIP401A\_ccn\_gridsearch\_500epochs.ipynb`

Grid search and long-training experiment notebook.



\### Contents

\- Hyperparameter search

\- Learning-rate experiments

\- Weight decay experiments

\- 500-epoch training analysis

\- Checkpoint evaluation



\### Purpose

Used to identify the best training configuration.



Best configuration found:

\- Learning Rate = `3e-4`

\- Weight Decay = `1e-6`



\---



\### `VIP401A\_ccn.ipynb`

Original baseline notebook.



\### Contents

\- Initial segmentation implementation

\- Early experiments

\- Small-scale training/testing setup



\### Purpose

Represents the earlier baseline version before architecture improvements.



\---



\### `Full\_Pipeline\_Before\_Comments\_and\_Edits.ipynb`

Original notebook before cleanup and documentation edits.



\### Purpose

Preserved for reference and comparison purposes.



\---



\# 2. PDF Versions



Each notebook is also provided as a PDF version for:

\- Easier reading

\- Documentation

\- Submission review

\- Static reference



\---



\# Architecture Summary



\## Original Architecture

Modified 3D U-Net using:

\- Encoder-decoder structure

\- Instance normalization

\- LeakyReLU activations

\- Skip connections



\---



\## Improved Architecture

Residual 3D U-Net using:

\- Residual blocks

\- Dropout in deeper layers

\- Improved gradient flow

\- Better training stability

\- Same 2-channel MRI input

\- Same 1-channel segmentation output



\---



\# Dataset Information



\## MRI Inputs

Each patient contains:

\- Baseline MRI volume

\- Follow-up MRI volume

\- Ground-truth lesion mask



\### File Naming

\- `baseline\_0p5\_norm\_padded.nii.gz`

\- `followup\_registered\_0p5\_norm\_padded.nii.gz`

\- `label\_0p5\_padded.nii.gz`



\---



\# Training Details



\## Training Strategy

\- Patch-based training

\- Balanced lesion sampling

\- Sliding-window inference

\- Dice + BCE loss



\## Main Hyperparameters

| Parameter | Value |

|---|---|

| Patch Size | 64×64×64 |

| Stride | 32×32×32 |

| Learning Rate | 3e-4 |

| Weight Decay | 1e-6 |

| Threshold | 0.5 |



\---



\# Postprocessing and Visualization



The pipeline includes:

\- Slice-level lesion analysis

\- Ground-truth vs prediction comparison

\- Overlay visualization

\- Dice score summaries

\- Patient-level evaluation



\### Overlay Colors

\- Green → Ground Truth

\- Red → Prediction

\- Yellow → Overlap



\---



\# Saved Outputs



Generated outputs include:

\- Patient-level Dice summaries

\- Slice-level PNG visualizations

\- Prediction masks

\- Checkpoints

\- Training history



\---



\# Running the Notebooks



\## Requirements



\### Python Libraries

Install the following:

```bash

pip install torch torchvision nibabel numpy pandas matplotlib

