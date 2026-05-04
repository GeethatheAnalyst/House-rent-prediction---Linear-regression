# House Rent Prediction — Linear Regression

This was my first machine learning project. The goal was straightforward — predict house rental prices based on property features. But the more interesting challenge turned out to be not the model itself, but cleaning the data and dealing with multicollinearity before the model could actually be trusted.

---

## What I was trying to predict

Given features like the number of bedrooms, bathrooms, living area size, location, year built, and condition of the property — can we predict how much a house will rent for?

---

## The dataset

- <a href="https://github.com/GeethatheAnalyst/House-rent-prediction---Linear-regression/blob/main/innercity.xlsx">InnerCity housing dataset</a> — property-level data with features covering size, location, age, and condition of residential units.
---

## What I did

**Step 1 — Data cleaning**
The dataset had a dirty data problem right away. Several columns that should have been numeric had `$` symbols stored in them as strings. Replaced those with NaN and filled using median values so the model could actually process them.

**Step 2 — Exploratory Data Analysis**
Plotted distributions and correlation matrices to understand which features had the strongest relationship with rent price. Some features were heavily skewed and needed attention before modelling.

**Step 3 — Building the first model**
Built an OLS (Ordinary Least Squares) regression model using `statsmodels`. The initial model technically ran — but it had multicollinearity issues hiding inside it.

**Step 4 — VIF Analysis**
This is where the real work happened. Multicollinearity means some features are too correlated with each other, which makes the model unstable — small changes in input data cause big swings in predictions.

I ran VIF (Variance Inflation Factor) analysis on all features. The rule: anything above 5 is a problem. I removed the highest-VIF feature, rebuilt the model, ran VIF again, and repeated this process until every remaining feature had a VIF score below 5.

**Step 5 — Final model evaluation**
Evaluated the cleaned model using R-squared and adjusted R-squared scores. Also checked p-values to confirm each remaining feature was statistically significant.

---


## Key takeaways

- Raw data is rarely model-ready — the cleaning step took longer than building the model itself
- VIF analysis is essential before trusting any linear regression output
- Iterative feature removal (one at a time, highest VIF first) gives a more stable result than removing multiple features at once

---

---

## Tools used

- Python 3
- Pandas, NumPy (data cleaning and manipulation)
- statsmodels (OLS regression, VIF analysis)
- scikit-learn (train-test split, evaluation)
- Matplotlib, Seaborn (visualisation)
- Jupyter Notebook

---

## Files in this repo

- <a href="https://github.com/GeethatheAnalyst/House-rent-prediction---Linear-regression/blob/main/Linear%20Regression%20Project.ipynb">Full analysis notebook</a> with code, outputs, and comments |

---



