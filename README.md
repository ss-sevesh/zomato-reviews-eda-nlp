# Zomato Restaurant Reviews — EDA & NLP Sentiment Prediction

Individual machine-learning project: exploratory analysis of 10,000 Zomato reviews plus a TF-IDF text classifier that predicts rating-derived sentiment (Negative / Neutral / Positive).

## Highlights
- **Data:** 10,000 reviews (100 restaurants) + 105 metadata rows; 9,936 usable for modelling.
- **Target:** ratings 1–2 = Negative, 3 = Neutral, 4–5 = Positive (proxy labels, not human-annotated).
- **EDA:** 15+ charts (univariate, bivariate, multivariate) with insight and business-impact notes.
- **Hypothesis tests:** Mann–Whitney U, chi-square, Kruskal–Wallis (all significant at α = 0.05).
- **Models:** Logistic Regression, Linear SVM, Multinomial Naive Bayes — TF-IDF (1–2-grams), stratified 3-fold GridSearchCV on macro-F1, stratified 80:20 hold-out.

## Results (held-out set)
| Model | Accuracy | Macro-P | Macro-R | Macro-F1 |
|---|---|---|---|---|
| **Logistic Regression** (selected) | 0.8094 | 0.6980 | 0.7067 | **0.7020** |
| Linear SVM | 0.8214 | 0.6987 | 0.6737 | 0.6820 |
| Multinomial NB | 0.8003 | 0.5479 | 0.5661 | 0.5507 |

Logistic Regression was selected on macro-F1 because the classes are imbalanced.

## Repository structure
```
├── Zomato_Individual_Project.ipynb   # full analysis + modelling notebook
├── data/                             # put the two source CSVs here (see data/README.md)
├── reports/                          # written report (.docx) and slide deck (.pptx)
├── video/                            # captioned project walkthrough (.mp4)
├── results/                          # model_comparison.csv, unseen_predictions.csv
├── models/                           # zomato_sentiment_model.joblib (created by the notebook)
├── requirements.txt
└── README.md
```

## How to run
```bash
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook Zomato_Individual_Project.ipynb     # Kernel → Restart & Run All
```

## Limitations
Labels are derived from star ratings, so metrics measure how well text reproduces ratings, not true sentiment. Sarcasm, mixed sentiment and multilingual text are not handled. Use predictions to prioritise human review, not to automate high-impact decisions.

## Video walkthrough
Silent captioned walkthrough: [`video/Zomato_Project_Video.mp4`](video/Zomato_Project_Video.mp4) (~3 min). Optionally add a YouTube / Drive link here.
