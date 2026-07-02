# Phishing Website Detection — A Critical Reproduction Study

Final project for Data Science in Cyber (Dr. Uri Itai).

## Project description

This project critically evaluates a published tutorial that trains a decision tree to detect phishing websites and claims 90.5% accuracy. We (1) reproduce the author's experiment exactly as published, (2) audit its methodology, and (3) rebuild the pipeline properly — deduplication and contradiction removal, stratified seeded splits, EDA with justified correlation methodology, feature engineering, three model families, seven evaluation metrics, and error analysis — so that every one of the author's methodological shortcuts is isolated and measured.

Headline result: the 90.5% claim reproduces (we get 90.4%), but 29.6% of the author's test set consists of exact copies of training rows, the dataset is 47.1% duplicates, and accuracy is his only metric. On a clean, leakage-free setup: Decision Tree 94.5%, Random Forest 96.3% accuracy / MCC 0.927 / ROC-AUC 0.994 (5-fold CV F1 = 0.965 ± 0.004).

## Links

- **Selected tutorial (source under evaluation):** https://medium.com/@NicolasPapernot/detecting-phishing-websites-using-a-decision-tree-ed069d073723
- **Original GitHub repository:** https://github.com/npapernot/phishing-detection
- **Dataset source:** UCI Machine Learning Repository — "Phishing Websites" (Mohammad, Thabtah & McCluskey, 2015): https://archive.ics.uci.edu/dataset/327/phishing+websites (the exact CSV used is `dataset.csv`, as shipped inside the tutorial's repository)

## Repository contents

| File | Description |
|------|-------------|
| `report.pdf` | Full project report (all required sections, executive summary included) |
| `phishing__project.ipynb` | Complete executable notebook: data loading → EDA → feature engineering → models → evaluation → error analysis |
| `dataset.csv` | The dataset (copied unmodified from the source repository) |
| `README.md` | This file |

## Execution instructions

**Easiest — Google Colab:**
1. Upload `phishing__project.ipynb` via File → Upload notebook.
2. In the left Files panel (folder icon), upload `dataset.csv`.
3. Runtime → Run all (~2–3 minutes).
4. Verify the two sanity gates: both cells printing `ALL CHECKS PASSED`.

**Locally:**
```bash
pip install pandas numpy scikit-learn matplotlib jupyter
jupyter notebook phishing_project.ipynb
# dataset.csv must sit in the same folder
```

All randomness is controlled with `RANDOM_STATE = 42`; results are fully reproducible.