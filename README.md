

````markdown
# GMM from Scratch – Clustering Digits 0, 1, 2

This project implements **Gaussian Mixture Model (GMM)** **from scratch** using the EM (Expectation-Maximization) algorithm to cluster handwritten digits **0**, **1**, and **2** from the `sklearn.datasets.load_digits()` dataset.

The project also compares results to the **KMeans** clustering algorithm, and uses **Principal Component Analysis (PCA)** to reduce data to 2D for visualization and modeling.

---

## 🛠Key Features

- Dimensionality reduction using **PCA** (2 components)
- Implementation of **GMM with EM algorithm**:
  - Supports both `full` and `diag` covariance types
  - Calculates responsibilities, log-likelihoods, and parameter updates manually
- Baseline comparison using **KMeans**
- Performance evaluation using:
  - Accuracy (after cluster-label mapping)
  - Adjusted Rand Index (ARI)
- Visualization of:
  - Clusters vs. true labels
  - Log-likelihood progression across EM iterations

---

## Structure

- `Ex2.ipynb` – The main notebook with full implementation, analysis, and visualizations.
- No external files required. Dataset is loaded from `sklearn.datasets.load_digits`.

---

## Methods Used

### PCA (Principal Component Analysis)
- Reduces 64-dimensional digit vectors to 2D.
- Enables visualization and speeds up convergence of EM.
- Preserves structure needed for clustering digits 0, 1, 2.

### KMeans
- Runs on the PCA-reduced data as a baseline clustering method.
- Compared to GMM using both accuracy and ARI.

### GMM (Gaussian Mixture Model)
- Implemented manually without `sklearn.mixture`.
- Uses EM algorithm:
  - **E-Step**: Compute soft cluster assignments (responsibilities)
  - **M-Step**: Update weights, means, and covariances
- Convergence checked via log-likelihood change.
- Two covariance types:
  - `full`: complete covariance matrices
  - `diag`: diagonal matrices (uncorrelated features)

---

## Results Summary

| Method           | Covariance | Accuracy | ARI   |
|------------------|------------|----------|-------|
| KMeans           | N/A        | ~91%     | ~0.768|
| GMM (from scratch)| `full`     | ~89.5%   | ~0.726|
| GMM (from scratch)| `diag`     | ~88.3%   | ~0.701|

- PCA enables clear cluster separation.
- KMeans performs slightly better than GMM (possibly due to PCA making clusters more spherical).
- GMM with `full` covariance slightly outperforms `diag`, at the cost of more computation.
- Log-likelihood increases monotonically across EM iterations, indicating proper convergence.

---

## Visualizations

- ✅ PCA projection of digit samples (0, 1, 2)
- ✅ KMeans clusters vs. true labels
- ✅ GMM predicted clusters (`full` & `diag`)
- ✅ Log-likelihood progression per iteration

---

## Requirements

```bash
pip install numpy matplotlib scipy scikit-learn
````

---

## Educational Value

This project is ideal for:

* Understanding **unsupervised learning** via clustering
* Learning how **EM and GMM** work under the hood
* Comparing clustering approaches (KMeans vs. GMM)
* Practicing **PCA for dimensionality reduction**
* Visualizing and interpreting results of unsupervised models

---

## Author

Developed by Shlomi Assayag
