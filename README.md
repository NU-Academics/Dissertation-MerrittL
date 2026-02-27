# Dissertation-MerrittL
# Dissertation Research Repository  
**Efficient Deepfake Detection in Low-Resolution Images Using Tabular Feature Engineering and Ensemble Learning**

This repository contains the notebooks and supporting assets used to generate, preprocess, featurize, and model **real vs. manipulated (deepfake/forged) images** for dissertation research. The workflow is organized as a **four-notebook pipeline** that should be executed in sequence.

Large image datasets are distributed via **GitHub Releases** as zipped archives to keep the repository lightweight.

---

## Contents

### Notebooks (Run in This Order)

1. **`1_Source AFHQ Images and StarGAN Deepfakes_clean.ipynb`**  
   Sources/organizes AFHQ real images and StarGAN-generated deepfake images into the project’s dataset structure.  
   **Output:** standardized folders and/or metadata used downstream.

2. **`2_Untiling, Deepfake Generation, Sampling_orig.ipynb`** *(Updated)*  
   Processes StarGAN grid outputs (untiling), performs deepfake generation workflows where applicable, and samples images for training/testing.  
   **Output:** finalized train/test image sets (by class and technique) and any sampling manifests.

3. **`3_Apply BoVW, K-means, and PCA (4).ipynb`**  
   Builds the unsupervised/feature branch: Bag-of-Visual-Words (BoVW), clustering with K-means, and dimensionality reduction with PCA.  
   **Output:** BoVW histograms / PCA feature matrices (typically saved as CSV/NPY/PKL) for modeling.

4. **`4_Model Development and Testing_clean_for_github.ipynb`** *(Updated)*  
   Trains and evaluates models using engineered features (including BoVW/PCA outputs when enabled). Produces performance metrics and analysis artifacts.  
   **Output:** trained model artifacts, metrics tables, figures (AUC/F1/MCC/lift), and evaluation summaries.

> **Tip:** If you rerun the pipeline from scratch, clear or version your output folders so each experiment is reproducible.

---

## Dataset Packaging (GitHub Releases)

The image data used in the experiments is stored as **zip files in GitHub Releases**. Download and extract these archives before running the notebooks.

### Releases (11 Zip Archives)

**Test Sets**
- `Test Real Images.zip`
- `Test Fake Images.zip`

**Train Real (by AFHQ class)**
- `Train Real Wild Images.zip`
- `Train Real Dog Images.zip`
- `Train Real Cat Images.zip`

**Train Fake (by manipulation technique)**
- `Train Fake SwapLike Images.zip`
- `Train Fake StarGAN Images.zip`
- `Train Fake Splicing Images.zip`
- `Train Fake PostProc Images.zip`
- `Train Fake InPaint Images.zip`
- `Train Fake CopyMove Images.zip`

---

## Expected Folder Structure

After extraction, place the data in a structure like:
data/
train/
real/
cat/
dog/
wild/
fake/
copymove/
inpaint/
postproc/
splicing/
stargan/
swaplike/
test/
real/
fake/

If your repository uses different paths, update the **path variables at the top of each notebook** accordingly.

---

## Setup

### Environment
- Python 3.9+ recommended (3.10+ preferred)
- Jupyter Notebook / JupyterLab

### Dependencies
Install requirements (if provided):
```bash
pip install -r requirements.txt

If referencing this work, cite:
Merritt, L. L. (2026). Efficient Deepfake Detection in Low-Resolution Images Using Tabular Feature Engineering and Ensemble Learning (Doctoral dissertation).

@phdthesis{merritt_deepfake_Year,
  title  = {Efficient Deepfake Detection in Low-Resolution Images Using Tabular Feature Engineering and Ensemble Learning},
  author = {Merritt, Lien Lea},
  school = {Northcentral University},
  year   = {Year}
}
