# Brain Tumor Classification using ConvNeXtTiny

Transfer learning-based multi-class brain tumor classification using ConvNeXtTiny on the Figshare Brain Tumor Dataset, evaluated with 5-fold stratified cross-validation.

---

## Overview

This project uses ConvNeXtTiny as a classifier for brain tumor type classification from T1-weighted MRI scans. 


**Result:** 91.03% average accuracy across 5 folds.

---

## Dataset

**Figshare Brain Tumor Dataset**  
T1-weighted MRI scans from 233 patients stored as MATLAB `.mat` files.

| Tumor Type | Label | Slices |
|------------|-------|--------|
| Meningioma | 0 | 708 |
| Glioma | 1 | 1,426 |
| Pituitary | 2 | 930 |

---

## Pipeline

1. **Data Loading** — MRI images and labels extracted directly from MATLAB v7.3 `.mat` files using `h5py`
2. **Preprocessing** — Images resized to 224×224, normalized to [0,1], grayscale converted to 3-channel RGB for ConvNeXtTiny compatibility
3. **Cross-Validation** — 5-fold Stratified K-Fold split to ensure class balance across folds
4. **Model** — ConvNeXtTiny pretrained on ImageNet, base frozen, custom classification head added
5. **Training** — 20 epochs per fold, Adam optimizer, categorical cross-entropy loss, batch size 32
6. **Evaluation** — Per-fold accuracy, training and validation accuracy plotted across all folds


---

## Results

| Metric | Value |
|--------|-------|
| Average Accuracy (5-fold) | 91.03% |
