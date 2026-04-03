# Credit-Default-Risk-Prediction
Predicting credit card default risk using Decision Tree &amp; Logistic Regression, with an honest evaluation of why 68% accuracy isn't enough to deny credit
# 💳 Should We Give Them Credit? 
### Predicting Credit Card Default Risk Using Machine Learning

> *The model is 68% accurate. But would you trust it to deny someone's mortgage application? This project says no — and explains why.*

**Author:** Tariro Kureva

---

## 💡 The Business Problem
Every year banks lose billions to credit defaults. The challenge isn't just predicting who will default — it's doing so accurately enough to act on the prediction without wrongly denying credit to good customers. A false positive in credit risk isn't just a technical error. It's a lost customer, lost revenue, and potential regulatory scrutiny.

This project builds and critically evaluates a credit default prediction system — and asks the hard question: **would you trust this model to deny someone credit?**

---

## 💥 Key Stats

| Stat | Value |
|------|-------|
| 📦 Dataset | UCI Credit Card Default Dataset |
| 👥 Clients analyzed | 30,000 |
| 🎯 Target | Default payment next month (Yes/No) |
| 🏦 Data source | UCI Machine Learning Repository |
| 🤖 Models tested | Decision Tree · Logistic Regression |
| 📊 Best accuracy | 68.38% (Logistic Regression) |
| ⚠️ Precision on defaulters | 37% |
| ✅ Recall on defaulters | 63% |
| 🚩 Biggest red flag | Pay Status September (Odds Ratio: 1.79×) |

---

## 🚩 Red Flags vs Green Flags

The Logistic Regression model identifies which factors **increase** and **decrease** default probability:

### 🔴 Red Flags (increase default risk)
- **Pay Status — September** — strongest single predictor (Odds Ratio: 1.79×). Recent payment delays are the loudest warning signal
- Consecutive payment delays across multiple months
- High delinquency scores (PAY_0 through PAY_6 combined)

### 🟢 Green Flags (decrease default risk)
- Consistent on-time payments in recent months
- Higher credit limit utilization within manageable bounds
- Stable repayment history

---

## 🛠️ Pipeline

```
UCI Credit Card Dataset (30,000 clients)
        ↓
Data Loading & Cleaning
(rename target column, handle datatypes)
        ↓
Feature Engineering
├── Rename 'default payment next month' → 'Default'
├── Create Default_Label (categorical)
└── Build Delinquency_Score (sum of PAY_0–PAY_6)
        ↓
Feature & Target Separation
(drop ID, Default_Label from features)
        ↓
Train/Test Split (70/30 stratified)
        ↓
StandardScaler (for Logistic Regression)
        ↓
Model Training
├── Decision Tree Classifier
└── Logistic Regression
        ↓
Coefficient Analysis
(Red Flag / Green Flag visualization)
        ↓
Model Evaluation
(Accuracy, Precision, Recall, F1)
        ↓
Critical Business Assessment
```

---

## 🤖 Model Performance

| Model | Accuracy | Precision (Default) | Recall (Default) |
|-------|----------|---------------------|------------------|
| Decision Tree | — | — | — |
| Logistic Regression | 68.38% | 37% | 63% |

---

## ⚖️ The Hard Question — Would You Trust This Model?

**Short answer: No. Not yet.**

With only **37% precision on defaulters**, for every 100 clients the model flags as likely to default, **63 of them are actually good customers** who would have paid. Denying credit to those 63 people means:

- 💸 Lost interest income and transaction fees
- 😡 Damaged customer relationships
- ⚖️ Potential regulatory investigations for unfair denial
- 📉 Reputational harm to the institution

The **63% recall** is reasonable — the model catches most actual defaulters. But in credit risk, precision matters more than recall for denial decisions.

---

## 💡 Recommendations

**1. 🚨 Early intervention on payment delays**
Since Pay Status September is the strongest predictor, trigger automated alerts and financial counseling the moment any client shows a payment delay — before it compounds.

**2. 🤝 Human-in-the-loop for all denials**
No automated denial without human review. The model flags risk; a human makes the final call — especially where model confidence is low.

**3. 🔬 Upgrade the model**
Explore Gradient Boosting (XGBoost, LightGBM) or Neural Networks for better precision. Incorporate cost-sensitive learning to weight false positives more heavily than false negatives.

**4. 📊 Richer feature engineering**
Add interaction terms, longer-term payment trends, and external credit bureau data to improve signal quality.

---

## ⚠️ Limitations
- 37% precision is too low for autonomous credit denial decisions
- Dataset from UCI (Taiwan credit data, 2005) — may not generalize to modern credit markets
- No demographic or income data — limits fairness assessment
- Static model — requires continuous retraining as economic conditions change

---

## 🔧 Tools & Libraries
- Python
- Pandas / NumPy
- Scikit-learn (Decision Tree, Logistic Regression, StandardScaler)
- Matplotlib / Seaborn
- UCI Machine Learning Repository

---

## 📁 Files
| File | Description |
|------|-------------|
| `Tariro_CreditDefault_Python.ipynb` | Full Jupyter notebook — EDA, modeling, evaluation |

---

## 🔗 Related Projects
👉 [Seattle Crime Pattern Analysis — XGBoost & Logistic Regression](https://github.com/Tariro-Kureva/Seattle-Crime-Pattern-Analysis)
👉 [IBM HR Analytics — K-Means Clustering & Attrition](https://github.com/Tariro-Kureva/IBM-HR-Analytics-Clustering)
👉 [IMDB Sentiment Analysis — NLP & Machine Learning](https://github.com/Tariro-Kureva/IMDB-Sentiment-Analysis-NLP)
👉 [MovieLens Rating Analysis — Collaborative Filtering](https://github.com/Tariro-Kureva/MovieLens-Rating-Analysis)
👉 [Movie Plot Narrative Similarity — SentenceTransformers](https://github.com/Tariro-Kureva/Movie-Plot-Narrative-Similarity)
👉 [Extreme Disaster Events in Southern Africa — Power BI](https://github.com/Tariro-Kureva/Extreme-disaster-events-Southern-Africa)

---

*Last updated: April 2026*

