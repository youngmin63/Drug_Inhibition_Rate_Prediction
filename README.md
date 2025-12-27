## I. Project Goals and Tasks

This project aims to predict CYP3A4 inhibition rates using molecular structure data represented as SMILES, supporting early-stage drug discovery and toxicity screening.
The final solution is based on molecular fingerprint features combined with gradient boosting regression models, selected for their robustness, interpretability, and efficient training.

## II. EDA Summary

- Inhibition rates ranged from 0 to 100 and showed a highly imbalanced distribution, with most compounds exhibiting low to moderate inhibition and relatively few high-inhibition samples.
- Elemental composition analysis indicated that compounds were primarily composed of common atoms such as carbon, nitrogen, and oxygen, with only a small number of halogen-containing molecules.
- The number of heavy atoms per compound was concentrated within a moderate range, suggesting relatively consistent molecular complexity across the dataset.
- Molecular weight distribution was right-skewed, with most compounds falling into the small to medium molecular weight range and a limited number of heavier molecules.
- Correlation analysis revealed weak but statistically significant positive relationships between molecular size-related features (SMILES length and molecular weight) and inhibition rate.
- Scatter plots showed substantial dispersion, indicating that inhibition cannot be adequately explained by simple linear relationships and motivating the use of fingerprint-based representations.

## III. Description of Approach

### Data Preparation

The molecular dataset was cleaned and standardised by validating SMILES strings, removing invalid or duplicate molecules, and aligning inhibition rate values across sources. 
To address data imbalance, particularly the scarcity of high-inhibition compounds, SMILES randomisation was applied to augment samples with inhibition rates above 70%.

### Feature Engineering

Molecules were represented using a combination of physicochemical descriptors and Morgan fingerprints. 
Basic molecular properties and RDKit descriptors were extracted and concatenated with 2048-bit Morgan fingerprints to form fixed-length feature vectors for model training.

### Modelling Approach

The task was formulated as a regression problem.

The following models were implemented and evaluated:

- Gradient Boosting Regressor
- XGBoost Regressor

Models were trained using cross-validation and evaluated with MAE and RMSE.

## IV. Results – Inhibition Rate Prediction

Fingerprint-based gradient boosting models showed stable performance under cross-validation, indicating reliable learning behaviour across different data splits. The models generalised well to unseen compounds while maintaining efficient training and inference compared to more complex modelling approaches.

The final selected model achieved a local validation score of approximately 0.82 and a leaderboard score of around 0.77. This model was subsequently used to generate CYP3A4 inhibition rate predictions for previously unseen molecular compounds.

## V. Conclusion

This project demonstrates that molecular fingerprints combined with gradient boosting models can effectively predict CYP3A4 inhibition rates with reliable accuracy.
By focusing on well-established machine learning techniques, the final approach provides a strong and interpretable baseline suitable for practical drug discovery workflows.
