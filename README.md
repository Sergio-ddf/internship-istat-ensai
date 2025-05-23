# EMit Emotion Detection with LLM Fine-Tuning

This repository contains the code, data, and resources for experimenting with fine-tuning a model aimed at the automatic recognition of emotions in texts from social media.

The main objective of this phase is to become familiar with LLM fine-tuning techniques and address common challenges in the process.

## Objectives

* Gain practical experience in fine-tuning Transformer models for multilabel classification tasks.
* Tackle and resolve typical difficulties such as class imbalance, loss selection and calibration, hyperparameter tuning, etc.
* Establish a reproducible and documented pipeline for future extensions.

## Structure

* `Emit_finetuning.ipynb`: Jupyter notebook containing the entire fine-tuning pipeline.
* `data/`: directory containing the EMit datasets used.
* `fine_tuned_umberto_emotions.zip`: archive with the fine-tuned model files.
* `.requirements.txt`: file listing the dependencies.

## Pipeline Steps

### 1. Setup and Environment Preparation

* Installation of main dependencies (`transformers`, `datasets`, `wandb`, etc.).
* Configuration of WandB for experiment tracking.

### 2. Preprocessing and Data Analysis

* Dataset loading and initial analysis of class distribution.
* Minimal text cleaning specific to Italian social media (handling URLs, mentions, hashtags, and emojis).

### 3. Multilabel Stratified Split

* Division of the dataset into train and validation sets, maintaining consistent multilabel distributions (90/10).

### 4. Baseline: TF-IDF + Logistic Regression

* Implementation of a baseline to establish an initial reference point (macro-F1).

### 5. Hugging Face Dataset Preparation

* Tokenization of data and conversion to a format compatible with Hugging Face datasets.

### 6. Fine-Tuning the UmBERTo Model

* Selection and initialization of UmBERTo (`Musixmatch/umberto-commoncrawl-cased-v1`).
* Initial setting of the classifier bias using class prevalences to improve convergence.
* Use of weighted BCE (`pos_weight`) to handle imbalance.
* Hyperparameter configuration.

### 7. Threshold Calibration

* Post-training tuning of thresholds on the validation set to maximize Macro-F1.

### 8. Final Evaluation

* Calculation of final metrics (Macro-F1 and detailed classification report per class).

## Difficulties Encountered

* **Multilabel imbalance handling**: Resolved by using `pos_weight` and properly initializing the bias.
* **Type and device mismatch**: Solved by adapting the custom Trainer and explicit tensor management (CPU/GPU).
* **Threshold calibration**: Necessary to maximize real-world performance on the test set.

## Results Obtained

After fine-tuning with optimized parameters, we obtained:

* Initial TF-IDF+LR Macro-F1: 0.16 (baseline)
* Macro-F1 after UmBERTo fine-tuning without threshold calibration: \~0.47
* Final Macro-F1 after threshold calibration: \~0.51

These results highlight how LLM fine-tuning on multilabel tasks can yield significant improvements over traditional approaches, while also underscoring the importance of careful threshold, loss, and regularization management.

## Next Steps

* Implement additional regularization techniques (dropout, focal loss).
* Data augmentation for rare classes.
* Evaluate larger architectures for further improvements.
