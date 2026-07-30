# AI Prompt Documentation

This file records the prompts used to generate the `ai/` project and any follow-up changes.

---

## Prompt 1 — Initial project generation

**Prompt (summary):**

> Create a reproducible R project for a beginner machine learning workflow using the built-in Iris dataset and supervised classification. Requirements included:
>
> - R Jupyter Notebook (`.ipynb`) with data loading, EDA, train/test split, multiple `caret` classifiers (LDA, kNN, decision tree, Naive Bayes, SVM, random forest), 10-fold cross-validation, best-model selection, and test-set evaluation (accuracy, confusion matrix, other metrics).
> - Clear markdown explanations in the notebook.
> - `README.md` with project overview, setup, and run instructions.
> - `environment.yml` with Conda packages for R, JupyterLab, IRkernel, caret, and dependencies.
> - Store in an `ai/` folder alongside a manual version.
> - Set a random seed for reproducibility.
> - Use current R/caret practices; do not copy an existing tutorial verbatim.
> - Create this `PROMPTS.md` file.

**Changes made:**

- Created `ai/` directory with a new project structure separate from the manual assignment in the parent folder.
- Wrote `iris_classification.ipynb` with an original workflow: structured markdown sections, `ggplot2` visualizations, stratified 80/20 train/test split via `caret::createDataPartition`, six classifiers trained under shared 10-fold CV settings, model comparison with `resamples()` / `dotplot()`, and test-set metrics via `caret::confusionMatrix` including per-class sensitivity and F1.
- Added `environment.yml` targeting Conda-forge with R ≥ 4.3, JupyterLab, IRkernel, caret, and model-specific R packages.
- Added `README.md` describing the dataset, models, setup, and execution steps.
- Set `RANDOM_SEED <- 42` before splitting and re-set the seed before each model fit for reproducibility.

**Post-generation validation:** The workflow was executed end-to-end in R to confirm all six models train and evaluate correctly. `multiClassSummary` was removed from cross-validation settings to avoid incomplete resampled metric warnings; detailed per-class metrics are still computed on the test set via `confusionMatrix()`.

---

## Follow-up prompts

### Prompt 2 — Fix `confusionMatrix` mode error

**Prompt (summary):**

> Reported a runtime error: `confusionMatrix(..., mode = "prec_class")` is invalid. Valid `mode` values are `'sens_spec'`, `'prec_recall'`, or `'everything'`. Requested a fix and updates to `README.md` and `PROMPTS.md`.

**Changes made:**

- Updated `iris_classification.ipynb` to use `mode = "everything"` so the test-set evaluation returns sensitivity, specificity, precision, and F1 for each species class.
- Added an inline comment in the notebook listing the valid `mode` options.
- Updated `README.md` to describe the test-set metrics and the `confusionMatrix` mode used.
- Documented this fix in `PROMPTS.md`.
