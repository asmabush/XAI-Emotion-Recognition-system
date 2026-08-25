# XAI-Emotion-Recognition-system

## Overview

This repository contains the implementation and experimental work conducted for a Master's thesis on **explainable text-based emotion recognition**.

The project investigates emotion classification using multiple machine learning and deep learning approaches and evaluates the reliability of their predictions through **Explainable Artificial Intelligence (XAI)** methods. In particular, **SHAP** and **LIME** are used to explain model predictions, while **Spearman's rank correlation coefficient** is employed to evaluate the stability of the generated explanations under input perturbations.

The main workflow is:

**Dataset → Data Preprocessing → Emotion Classification → SHAP/LIME Explanations → Input Perturbation → Stability Evaluation**

---

## Research Objectives

The repository supports the following objectives:

- Develop and compare different text-based emotion classification models.
- Evaluate both traditional machine learning and deep learning approaches.
- Apply post-hoc XAI methods to interpret model predictions.
- Investigate whether feature/token importance explanations remain consistent when the input is slightly modified.
- Quantitatively evaluate explanation stability using Spearman's rank correlation.

---

## Dataset

The experiments are based on the **ISEAR (International Survey on Emotion Antecedents and Reactions)** dataset.

The repository includes the dataset-related files used during the experimental process, including augmented and punctuation-processed versions.

 the dataset has been used in this project is >> punctuation_augmented_isear_... 

### Dataset Processing

The preprocessing workflow includes operations required to prepare the text for emotion classification and subsequent explanation analysis. The repository also contains exploratory data analysis (EDA) for examining the dataset before model training.

Relevant files:

```text
Dataset/
├── augmented_dataset.xlsx
└── punctuation_augmented_isear_...
```

The exact preprocessing and experimental settings are documented in the corresponding notebooks and in the thesis methodology.

---

## Classification Models

Four classification approaches were implemented and evaluated:

| Model | Category | Purpose |
|---|---|---|
| Logistic Regression | Traditional ML | Provides a strong and interpretable classical baseline |
| Multinomial Naive Bayes | Traditional ML | Probabilistic baseline for text classification |
| BiLSTM | Deep Learning | Captures sequential and contextual information in text |
| BERT | Transformer | Uses contextualized language representations for emotion classification |

The model implementations are located in:

```text
Models/
├── BERT_SHAP_LIME_STABILITY.ipynb
├── Bilstm.ipynb
├── EDA_ISEAR.ipynb
├── Logistic_regression.ipynb
└── Multinomial_Naive_bayes.ipynb
```

---

## Explainable Artificial Intelligence

To improve the interpretability of the classification models, two post-hoc explanation methods were investigated:

### SHAP

**SHAP (SHapley Additive exPlanations)** assigns contribution values to input features/tokens to indicate their influence on a model prediction.

### LIME

**LIME (Local Interpretable Model-agnostic Explanations)** creates locally interpretable approximations of model behaviour by perturbing the input and observing changes in the prediction.

The repository includes experiments applying SHAP and LIME to the BERT model:

```text
Explainability/
└── SHAP_LIME_on_BERT.ipynb
```

---

## Explanation Stability

A key component of this research is evaluating whether XAI explanations are **stable and consistent**, rather than only visually or qualitatively meaningful.

The stability experiments generate explanations for an original input and corresponding perturbed versions of that input. The resulting feature/token rankings are then compared using **Spearman's rank correlation coefficient (ρ)**.

A higher positive correlation indicates that the ranking of important features remains more consistent between the original and perturbed inputs.

The stability analysis focuses on:

- SHAP explanation stability
- LIME explanation stability
- Original versus perturbed inputs
- Rank-based comparison of important features/tokens

Relevant files:

```text
Stability_Spearmans/
└── SHAP_LIME_STABILITY.ipynb
```

The repository also contains the combined BERT, SHAP, LIME, and stability experiment:

```text
Models/
└── BERT_SHAP_LIME_STABILITY.ipynb
```

---

## Repository Structure

```text
.
├── Dataset/
│   ├── .gitignore
│   ├── augmented_dataset.xlsx
│   └── punctuation_augmented_isear_...
│
├── Explainability/
│   ├── .gitignore
│   └── SHAP_LIME_on_BERT.ipynb
│
├── Models/
│   ├── BERT_SHAP_LIME_STABILITY.ipynb
│   ├── Bilstm.ipynb
│   ├── EDA_ISEAR.ipynb
│   ├── Logistic_regression.ipynb
│   └── Multinomial_Naive_bayes.ipynb
│
├── Stability_Spearmans/
│   ├── .gitignore
│   └── SHAP_LIME_STABILITY.ipynb
│
├── requirements.txt
└── README.md
```

---

## Experimental Workflow

The experiments are organized into the following stages:

### 1. Exploratory Data Analysis

The ISEAR dataset is examined to understand its structure, emotion distribution, and text characteristics.

### 2. Data Preparation

The text data is processed and prepared for model training. Augmented and punctuation-processed data are also included where required by the experiments.

### 3. Model Development

Four models are trained and evaluated:

- Logistic Regression
- Multinomial Naive Bayes
- BiLSTM
- BERT

### 4. Explainability Analysis

SHAP and LIME are applied to generate local explanations for model predictions, with particular focus on the BERT-based classifier.

### 5. Perturbation

Input text is modified through controlled perturbations to investigate whether explanation rankings remain consistent.

### 6. Stability Evaluation

The rankings produced by SHAP and LIME are compared between the original and perturbed inputs using Spearman's rank correlation.

This provides a quantitative measure of explanation consistency.

---

## Technologies

The project uses Python and the following main libraries/frameworks:

- Python
- Jupyter Notebook
- pandas
- NumPy
- scikit-learn
- TensorFlow / Keras
- Transformers
- BERT
- SHAP
- LIME
- SciPy
- Matplotlib

---

## How to Run

### 1. Clone the repository

```bash
git clone <YOUR-GITHUB-REPOSITORY-URL>
cd <REPOSITORY-NAME>
```

### 2. Install the required libraries

If a `requirements.txt` file is provided:

```bash
pip install -r requirements.txt
```

Otherwise, install the required dependencies used by the individual notebooks.

### 3. Open the notebooks

The notebooks can be opened using Jupyter Notebook, JupyterLab, or Google Colab.

For example:

```bash
jupyter notebook
```

### 4. Run the experiments

A recommended order is:

1. `Models/EDA_ISEAR.ipynb`
2. `Models/Logistic_regression.ipynb`
3. `Models/Multinomial_Naive_bayes.ipynb`
4. `Models/Bilstm.ipynb`
5. `Models/BERT_SHAP_LIME_STABILITY.ipynb`
6. `Explainability/SHAP_LIME_on_BERT.ipynb`
7. `Stability_Spearmans/SHAP_LIME_STABILITY.ipynb`

The exact execution order may depend on the generated datasets and intermediate outputs used by each notebook.


---

## Reproducibility

For reproducibility, the repository provides the main datasets, preprocessing outputs, model implementations, explainability experiments, and stability analysis notebooks.

To reproduce the experiments as closely as possible:

1. Use the provided dataset files.
2. Follow the notebook execution order.
3. Use the same preprocessing procedure.
4. Keep the model and XAI configurations unchanged.
5. Record the software/library versions used during execution.

If exact reproducibility is required, the Python and library versions should also be fixed through a `requirements.txt` or equivalent environment configuration.

---

## Thesis Contribution

The main contribution represented by this repository is the integration of **emotion classification, explainability, and explanation stability evaluation** within a single experimental framework.

Rather than evaluating XAI methods only based on whether their explanations appear meaningful, the work investigates their **consistency under input perturbations**. This provides an additional perspective for assessing the reliability of explanations produced by SHAP and LIME.

---

## Author

**Asma Abubaker Bushaala**

Master's Degree in Artificial Intelligence and Data Science  
Istanbul Aydin University

---

## Academic Note

This repository was developed as part of academic thesis research. The notebooks are provided to document the methodology, experiments, and analysis supporting the research work.
