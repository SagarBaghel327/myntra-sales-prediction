# Myntra Sales Prediction

**Author:** Sagar Baghel
**Program:** IBM SkillsBuild Data Analytics with AI Academic Internship Program — conducted by BharatCares in association with AICTE

## Project Description

This project analyzes a real-world, web-scraped Myntra product dataset (men's jeans/pants category) and builds a machine learning model to predict a **sales/demand proxy** for a product. Since Myntra does not publicly expose actual "units sold" figures, the number of customer ratings (`number_of_ratings`) is used as a practical proxy for sales — a product rated by more customers has, in general, sold to more customers.

The notebook covers the full data science workflow:
- Data cleaning (removing duplicates, fixing an inconsistent discount-percentage scale, validating price vs MRP)
- Feature engineering (extracting fit type and rise type from product titles, computing discount amount)
- Exploratory Data Analysis (brand distribution, price/rating distributions, correlations)
- Model building and comparison (Linear Regression, Random Forest, Gradient Boosting)
- Feature importance analysis
- A reusable function to predict sales for a new/hypothetical product listing

## Dataset

- **File:** `myntra_dataset_ByScraping.csv`
- **Source:** Web-scraped from Myntra.com (men's jeans/pants listings)
- **Dataset link (Kaggle):** https://www.kaggle.com/datasets/skmewati/myntra-sales-dataset
- **Size:** ~52,000 rows, 7 columns
- **Columns:** `brand_name`, `pants_description`, `price`, `MRP`, `discount_percent`, `ratings`, `number_of_ratings`

> Note: Place `myntra_dataset_ByScraping.csv` in the same folder as the notebook before running it.

## Technologies Used

- Python 3
- pandas, numpy — data handling
- matplotlib, seaborn — visualization
- scikit-learn — machine learning (Linear Regression, Random Forest, Gradient Boosting)
- Jupyter Notebook

## Setup / Run Instructions

1. Clone/download this project folder.
2. (Recommended) Create a virtual environment:
   ```
   python -m venv venv
   source venv/bin/activate      # On Windows: venv\Scripts\activate
   ```
3. Install dependencies:
   ```
   pip install -r requirements.txt
   ```
4. Ensure `myntra_dataset_ByScraping.csv` is in the same directory as the notebook.
5. Launch Jupyter and run all cells:
   ```
   jupyter notebook SagarBaghel_MyntraSalesPrediction.ipynb
   ```

## Key Results

- Compared three regression models predicting `log(number_of_ratings)` (to handle skew), converted back to the original scale for evaluation.
- **Random Forest Regressor** performed best among the three models tested, outperforming the Linear Regression baseline — indicating non-linear relationships between price, discount, brand and demand.
- `price`, `discount_percent`/`discount_amount`, and `brand` were consistently the most influential features in predicting demand.

## Files in this Submission

| File | Description |
|---|---|
| `SagarBaghel_MyntraSalesPrediction.ipynb` | Complete project code (data cleaning, EDA, modeling) |
| `requirements.txt` | Python dependencies |
| `docs/SagarBaghel_ProjectReport.docx` | Full project documentation/report |
| `README.md` | This file |
| `myntra_dataset_ByScraping.csv` | Dataset used |

## Limitations & Future Work

- `number_of_ratings` is an approximation of sales, not an exact figure.
- Currently limited to the men's jeans/pants category.
- Future improvements: add more product categories, use NLP on review text, tune hyperparameters with cross-validation, and incorporate time/seasonality data if available.
