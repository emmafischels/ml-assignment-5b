# Iris Species Classification (AI-Generated Workflow)

This folder contains a reproducible supervised classification analysis of the classic **Iris** dataset. The workflow is implemented in an R Jupyter Notebook using the [`caret`](https://topepo.github.io/caret/) package and follows a standard machine learning pipeline: explore the data, split into training and test sets, compare several classifiers with cross-validation, select the best model, and evaluate it on held-out data.

A manually authored version of the same assignment lives in the parent directory (`../`).

## Dataset

The **Iris** dataset (Fisher, 1936) describes 150 observations of three iris species:

| Variable       | Description                          |
|----------------|--------------------------------------|
| `Sepal.Length` | Sepal length in cm                   |
| `Sepal.Width`  | Sepal width in cm                    |
| `Petal.Length` | Petal length in cm                   |
| `Petal.Width`  | Petal width in cm                    |
| `Species`      | Target class: *setosa*, *versicolor*, *virginica* |

The dataset is built into R (`data(iris)`) and requires no external download.

## Models Compared

Using 10-fold cross-validation on the training set, the notebook trains and compares:

- Linear Discriminant Analysis (LDA)
- k-Nearest Neighbors (kNN)
- Decision Tree (CART via `rpart`)
- Naive Bayes
- Support Vector Machine (radial kernel)
- Random Forest

The model with the highest cross-validated accuracy is refit and evaluated on the test set using overall accuracy, a confusion matrix, and per-class metrics (sensitivity, specificity, precision, and F1) from `caret::confusionMatrix(..., mode = "everything")`.

## Software Requirements

- [Conda](https://docs.conda.io/) (Miniconda or Anaconda)
- Packages listed in [`environment.yml`](environment.yml)

## Environment Setup

From this directory (`ai/`):

```bash
# Create and activate the Conda environment
conda env create -f environment.yml
conda activate ml-assignment-5b-ai

# Register the R kernel with Jupyter (run once per environment)
R -e "IRkernel::installspec(name = 'ir', displayname = 'R')"
```

## Running the Notebook

```bash
conda activate ml-assignment-5b-ai
jupyter lab iris_classification.ipynb
```

In JupyterLab, select the **R** kernel (`ir`) and run all cells from top to bottom.

Alternatively, execute the notebook non-interactively:

```bash
jupyter execute iris_classification.ipynb
```

## Reproducibility

A fixed random seed (`42`) is set before data partitioning and model training so that train/test splits and cross-validation folds are identical across runs on the same machine and package versions.

## Project Files

| File | Purpose |
|------|---------|
| `iris_classification.ipynb` | Main analysis notebook |
| `environment.yml` | Conda environment specification |
| `PROMPTS.md` | Documentation of AI prompts used to generate this project |
| `README.md` | This file |

## References

- Fisher, R. A. (1936). The use of multiple measurements in taxonomic problems. *Annals of Eugenics*, 7(2), 179–188.
- Kuhn, M. (2008). Building predictive models in R using the caret package. *Journal of Statistical Software*, 28(5), 1–26.
