# Laptop Price Prediction Using Machine Learning

## Project Overview

This project builds a **Linear Regression model** to predict laptop prices using structured features such as RAM, storage, processor speed, brand, and condition.

The workflow includes:

- Data preprocessing & encoding  
- Feature scaling  
- Model training  
- Prediction evaluation  
- Error analysis  

---

## 1. Dataset Overview

After preprocessing and encoding, the dataset was transformed into numerical features only.

### Final Feature Set

| Feature            | Description |
|--------------------|------------|
| RAM                | Memory size |
| Storage            | Disk capacity |
| Processor_Speed    | CPU speed |
| Brand              | One-hot encoded brands |
| Condition          | Laptop condition (Used / Refurbished) |

### Sample Data Characteristics

- RAM ranges: 4GB – 16GB+  
- Storage ranges: 256GB – 2048GB  
- Processor speed: ~2.0 – 3.7 GHz  

---

## 2. Train-Test Split

The dataset was split as follows:

- Training set: (768 samples, 12 features)  
- Test set: (193 samples, 12 features)  

This ensures the model is evaluated on unseen data.

---

## 3. Feature Scaling

A **StandardScaler** was applied to normalize features before training.

This is important because:

- Features like RAM and Storage are on different scales  
- Scaling improves Linear Regression performance  

---

## 4. Model Training

### Model Used
- Linear Regression  

The model was trained on scaled features to learn relationships between laptop specifications and price.

---

## 5. Model Predictions

Example predictions from the model:

| Prediction ($) |
|---------------|
| 1329.82 |
| 1269.83 |
| 1508.16 |
| 1089.35 |
| 1123.95 |

---

## 6. Model Evaluation

### R² Scores

| Dataset   | R² Score |
|-----------|---------|
| Training  | 0.7746  |
| Validation| 0.7633  |
| Test      | 0.7475  |

### Interpretation

- The model explains approximately **75% of the variation** in laptop prices  
- This indicates a strong predictive model, though not perfect  

---

## 7. Error Analysis

### Summary Statistics

| Metric               | Value |
|---------------------|------|
| Mean Actual Price   | 1262.11 |
| Mean Prediction     | 1248.71 |
| Mean Residual       | 13.40 |
| Average % Error     | 10.59% |

### Error Distribution

- Minimum error: ~0.08%  
- Median error: ~8.68%  
- Maximum error: ~82.92%  

### Insight

- Most predictions are within **±10% error**  
- Some extreme cases show large deviations ? possible missing features  

---

## Best Predictions

Examples with extremely low error:

| Prediction | Actual | Error % |
|-----------|--------|--------|
| 1623.72   | 1625.02 | 0.08% |
| 1357.80   | 1360.71 | 0.21% |
| 1076.37   | 1079.42 | 0.28% |

This shows the model performs very well for certain laptop categories.

---

## 8. Residual Analysis

Residual = Actual ? Predicted

- Residuals are centered around 0  
- Spread is quite wide (std ? 177.74)  

### Insight

The model is generally unbiased.

---

## 9. Feature Importance

From the trained model:

| Feature               | Weight |
|----------------------|--------|
| RAM                  | +0.16 |
| Storage              | +0.12 |
| Processor Speed      | +0.06 |
| Brand Apple          | +0.11 |
| Brand Asus           | -0.01 |
| Brand Dell           | +0.01 |
| Brand HP             | -0.01 |
| Condition Refurbished| -0.06 |
| Condition Used       | -0.14 |

## 10. Key Insights

1. **RAM is the strongest predictor**  
   - Highest coefficient (0.16) ? more RAM ? higher price  

2. **Storage significantly impacts price**  
   - Coefficient: 0.12 ? larger storage ? higher price  

3. **Apple brand increases price**  
   - Coefficient: +0.11 ? confirms premium brand effect  

4. **Used laptops reduce price**  
   - Coefficient: -0.14 ? strongest negative impact  

5. **Refurbished laptops also reduce price**  
   - Coefficient: -0.06  

6. **Processor speed has moderate influence**  
   - Coefficient: 0.06 ? less impact than RAM or Storage  

---

## 11. Model Strengths

- Good predictive performance (~75% accuracy)  
- Handles structured data well  
- Interpretable coefficients (easy to explain)  

---

## 12. Business Interpretation

**For Sellers:**  
- Increase RAM and SSD ? justify higher pricing  
- Brand positioning matters (Apple premium effect)  

**For Buyers:**  
- Best value laptops:  
  - Not Apple  
  - Moderate RAM  
  - Not refurbished  

**For Analysts:**  
- Condition and RAM are the most critical pricing drivers  

---

## 13. Tools Used

- Python  
- Pandas  
- Scikit-learn  
- Matplotlib  
- Jupyter Notebook  

---

## 14. Project Files

- [LaptopPriceDataPreprocessing Notebook](notebooks/LaptopPriceDataPreprocessing.ipynb) – Preprocessing and exploratory data analysis  
- [Laptop PriceML Notebook](notebooks/Laptop%20PriceML.ipynb) – Model building, evaluation, and predictions  
- [Dataset](data/laptop_price_dataset.csv) – Raw dataset  
- [Preprocessed Dataset](outputs/data_preprocessed.csv) – Cleaned dataset ready for modeling  
- [Images](images/) – Charts and visualizations  

---

## 15. Conclusion

- Linear Regression predicts laptop prices with reasonable accuracy (~75%)  
- Key price drivers: **RAM, Storage, Brand, Condition**  
- Model performs well but can improve with more features or non-linear models  

---

## 16. Further Improvements

- Include additional features (GPU, screen resolution, battery life)  
- Apply non-linear models (Random Forest, Gradient Boosting)  
- Perform hyperparameter tuning (Grid Search / Random Search)  
- Enhance feature engineering (e.g., price-per-RAM, storage type weighting)  
- Use k-fold cross-validation for stable evaluation  
- Deploy model via Flask or Streamlit for real-world use  

---

## Author

**Adedayo Adebayo**  
Data Scientist | Business Analyst

