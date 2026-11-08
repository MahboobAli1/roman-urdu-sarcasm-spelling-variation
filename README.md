# Robust Sarcasm Detection Under Roman Urdu Spelling Variation

Code and dataset for the paper *"Robust Sarcasm Detection Under Roman Urdu
Spelling Variation"* ( Abdul Haseeb, Mahboob Ali, Azad Ali, Abdul Aziz),
Aror University of Art, Architecture, Design and Heritage, Sukkur, Pakistan.

## Overview
We study sarcasm detection in Roman Urdu under four controlled spelling
variation tiers (Standard, Light, Moderate, Heavy) and show that random
splits on templated synthetic data inflate Macro-F1 above 0.92. With a
template-grouped split, performance falls to about 0.65-0.68.

We propose **TanzSVM**: word unigram+bigram TF-IDF (sublinear TF) with a
validation-tuned LinearSVC.

## Key results (5 template-grouped seeds)
| Model | Macro-F1 |
|---|---|
| Majority baseline | 0.321 +/- 0.022 |
| Word TF-IDF + LR | 0.656 +/- 0.116 |
| Char TF-IDF + SVM | 0.659 +/- 0.110 |
| Word+Char + SVM | 0.660 +/- 0.108 |
| **TanzSVM** | **0.680 +/- 0.106** |

Differences between TanzSVM and the linear baselines are not statistically
significant (paired bootstrap, alpha = 0.05).

## Dataset

`data/roman_urdu_sarcasm_synthetic_5000.csv`: 5,000 balanced synthetic sentences (2,500 sarcastic / 2,500 non-sarcastic), generated through a guided synthesis process using 1,500 real YouTube comments collected via the YouTube API. The dataset contains 104 carrier templates, 846 topical event clauses, and 4 controlled spelling variation tiers (Standard, Light, Moderate, Heavy). See `data/DATASHEET.md`.

**Columns:** `Text`, `Canonical_Text`, `Final_Label`, `Template_ID`, `Group_ID`, `Variation_Level`.

> **:** The 1,500 raw YouTube comments were used as source data for guided synthetic dataset generation. They are unannotated and are not included directly in the 5,000-sample experimental dataset or used as model training/evaluation samples.
## Installation
pip install -r requirements.txt

## Usage
python src/evaluate.py --data data/roman_urdu_sarcasm_synthetic_5000.csv \
    --seeds 42 1 2 3 4

## Limitations


## Citation
See `CITATION.cff` or:
@misc{ali2026tanzsvm,
  title  = {Robust Sarcasm Detection Under Roman Urdu Spelling Variation},
  author = {Ali, Mahboob and Ali, Azad and Haseeb, Abdul and Aziz, Abdul},
  year   = {2026}
}

## License
Code: MIT. Dataset: CC BY 4.0.

## Contact
Mahboob Ali - <mahboobalilaghari1976@gmail.com>
