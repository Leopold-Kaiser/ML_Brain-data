# Autism Classification with Machine Learning

This project applies multiple machine learning algorithms to predict **autism spectrum disorder (ASD)** using functional brain connectivity data derived from fMRI scans.

The analysis uses the **ABIDE (Autism Brain Imaging Data Exchange)** dataset and compares several supervised learning approaches for high-dimensional neuroimaging data.

The goal is to evaluate how well machine learning models can identify complex patterns in brain connectivity that differentiate ASD from control subjects.


# Dataset

The data originates from the **ABIDE international neuroimaging dataset**, consisting of fMRI scans collected across multiple research sites.

Each subject contains:

> 200 brain regions of interest (ROIs)  
> 176 time observations per region

Functional connectivity between brain regions is computed using **Pearson correlations**, producing a **200 × 200 connectivity matrix** per subject.

Because the matrix is symmetric, only the **upper triangle** is retained, resulting in **19,900 connectivity features per subject**.

The correlations are transformed using the **Fisher z-transformation** to stabilize variance before being used as machine learning inputs.


# Project Workflow

The machine learning pipeline consists of the following steps.


Functional Connectivity Construction
---

> compute Pearson correlations between brain region time series  
> apply Fisher z-transformation


Feature Representation
---

> extract the upper triangle of the connectivity matrix  
> convert each subject into a feature vector of brain connections


Train–Test Splitting
---

> site-aware splitting keeps subjects from the same site together  
> prevents models from learning site-specific artifacts


Model Training and Evaluation
---

> multiple supervised learning models are trained  
> performance is evaluated using standard classification metrics


# Machine Learning Models


Logistic Regression
---

A probabilistic linear classifier modeling the log-odds of ASD using brain connectivity features.


Support Vector Machines
---

Both linear and nonlinear SVMs are implemented to find optimal separating hyperplanes between ASD and control subjects.


Classification Trees
---

Decision trees partition the feature space into interpretable decision rules.


Random Forest
---

An ensemble of decision trees trained on bootstrap samples and random feature subsets to improve generalization.


Gradient Boosting
---

Sequential tree ensembles that iteratively correct prediction errors using gradient-based optimization.


k-Nearest Neighbors
---

A distance-based classifier that assigns labels based on the most similar observations in the training data.


# Evaluation Metrics

Model performance is evaluated using:

> accuracy  
> precision  
> recall  
> F1 score  
> ROC curves  
> precision-recall curves


# Key Findings

Across the evaluated models:

> linear models achieve approximately 68% accuracy  
> kernel-based SVM models reach roughly 70% accuracy  
> dimensionality reduction with PCA further improves performance

These results indicate that **functional brain connectivity contains predictive information for ASD classification**, although the problem remains challenging due to high dimensionality.


# Requirements

The notebooks rely on standard Python libraries:

> numpy  
> pandas  
> scipy  
> matplotlib  
> scikit-learn  
> statsmodels


# Reproducibility

All necessary data files and scripts are included in this repository to ensure full reproducibility of the analysis.
