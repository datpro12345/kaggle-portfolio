# House Prices: Advanced Regression Techniques

This project is based on the Kaggle competition [House Prices: Advanced Regression Techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques). The objective of this competition is to predict the final price of residential homes in Ames, Iowa, based on various features describing the properties.

## Project Structure

- **notebook.ipynb**: This Jupyter notebook contains the Exploratory Data Analysis (EDA), where data is explored and visualized to gain insights into the features and their relationships with the target variable (SalePrice).
- **model.ipynb**: This notebook focuses on building, training, and evaluating machine learning models to predict house prices. Different regression models are explored and optimized in this notebook.
- **train.csv**: The training dataset provided by Kaggle, containing the features and target variable (SalePrice).
- **test.csv**: The test dataset provided by Kaggle, containing the features without the target variable. Predictions for this dataset are to be submitted for evaluation.
- **sample_submission.csv**: A sample submission file provided by Kaggle, showing the required format for submitting predictions.
- **submission.csv**: The actual submission file containing predictions made by the model. This file is uploaded to Kaggle to evaluate the model's performance.
- **data_description.txt**: A text file provided by Kaggle that describes the meaning of each feature in the dataset.

## Overview

1. **Exploratory Data Analysis (EDA)**: The `notebook.ipynb` contains visualizations and statistical summaries to understand the distribution of the data, identify missing values, and uncover relationships between features and the target variable.

2. **Model Development**: The `model.ipynb` notebook contains the process of selecting, training, and fine-tuning machine learning models. Techniques such as Linear Regression, Decision Trees, and advanced methods like Gradient Boosting are explored.

3. **Submission**: The predictions generated in `model.ipynb` are saved in `submission.csv`, which is formatted according to the guidelines provided in `sample_submission.csv`.

## Getting Started

To explore this project:
1. Open `notebook.ipynb` to review the exploratory data analysis.
2. Move on to `model.ipynb` to understand the modeling process.
3. Check the `submission.csv` to see the final predictions submitted to Kaggle.

This project demonstrates the complete workflow of a typical Kaggle competition, from initial data exploration to final model submission.
