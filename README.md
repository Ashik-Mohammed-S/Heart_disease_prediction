# Heart Disease Label Classification — Research Study

[![Validation](https://github.com/Ashik-Mohammed-S/Heart_disease_prediction/actions/workflows/validate.yml/badge.svg)](https://github.com/Ashik-Mohammed-S/Heart_disease_prediction/actions/workflows/validate.yml)

Classify the supplied binary label and report minority-class behavior with the limitations of a very small sample.

Independent public portfolio work; historical educational notebooks remain under `historical/`. The current implementation and results described here take precedence over historical in-sample numbers.

## Data and approach

270 records; 216 train and 54 test records, with four supplied predictors.

Stratified holdout with train-only imputation, scaling and category encoding. Use class-balanced logistic regression at a fixed 0.5 threshold and report a dummy prior baseline.

## Current full-data result

| Measure | Current analysis | Baseline where applicable |
| --- | --- | --- |
| ROC-AUC | 0.688 | 0.500 |
| Positive-class recall | 0.667 | 0.000 |
| F1 | 0.604 | 0.000 |
| Accuracy | 0.611 | 0.556 |

Results are specific to the documented dataset and split. See generated `results/analysis.json` after execution for full metrics and assumptions.

## Run locally

Use the Python version in `.python-version`, then:

```sh
python -m pip install -r requirements.txt
python scripts/fetch_data.py
python scripts/run_notebook.py --mode full
```

Reference data is committed under `dataset/`, directly or as reconstructable compressed parts. The downloader verifies checksums and restores stored data offline. See [DATA.md](DATA.md) and [dataset-sources.json](dataset-sources.json) for provenance and upstream terms. Package installation and the spaCy model, where needed, require network access on a fresh machine.

## Review the implementation

Inspect the tiny holdout size and recall/precision tradeoff instead of interpreting a single accuracy number. Start with [scripts/analysis.py](scripts/analysis.py), then the root notebook. The workflow validates dependencies, smoke checks and full-data notebook execution with dataset downloads disabled.

## Limitations

Modest, unstable small-sample results. This is an educational classification task, not a diagnostic application, medical recommendation or clinically validated model.

[Method notes](ANALYSIS.md) · [All portfolio projects](https://github.com/Ashik-Mohammed-S/Ashik-Mohammed-S/blob/main/PORTFOLIO.md)
