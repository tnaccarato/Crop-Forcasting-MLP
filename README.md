
# Machine Learning Model for Predicting Export Crop Values

## Overview

This project involves the development of a machine learning model aimed at predicting the export value of crops three years into the future. The model is built using a Multi-Layer Perceptron (MLP) regression model, which was trained on historical crop data. The objective is to forecast future crop export values for different geographic regions, enabling better planning and decision-making.

## Table of Contents

1. [Performance Evaluation](#performance-evaluation)
2. [Model Architecture](#model-architecture)
3. [Features and Labels](#features-and-labels)
4. [Data Preprocessing](#data-preprocessing)
5. [Usage Instructions](#usage-instructions)
6. [File Structure](#file-structure)
7. [Contributing](#contributing)
8. [License](#license)

## Performance Evaluation

The model's performance was evaluated using Mean Absolute Error (MAE) and R² score. The MAE was approximately $310,600, which is a small percentage of the target variable given the scale of export values. The model achieved an R² score of 0.864, indicating a good fit, though there is evidence of overfitting as the training score was 0.968.

### Visual Analysis
- **Scatter Plot:** Shows the relationship between actual and predicted values, with points clustered around the ideal prediction line.
- **Density Plot:** Illustrates that the model’s predictions closely follow the actual data distribution.
- **Residual Plot:** Displays residuals mostly centered around zero, indicating accurate predictions with minimal systematic bias.

## Model Architecture

The model was developed using Scikit-learn’s MLPRegressor, consisting of:
- **Input Layer:** Receives the features of the dataset.
- **Two Hidden Layers:** Each with 100 neurons, using the Tanh activation function.
- **Output Layer:** Produces the predicted export value using an identity function.

### Overfitting Prevention Techniques
- **Cross Validation:** Implemented with a Time Series Split to preserve data order.
- **L2 Regularization:** Used to prevent weight values from becoming too large.
- **Early Stopping:** Training was halted if performance did not improve after 10 iterations.
- **Bagging Regressor:** Employed to improve robustness and reduce overfitting by averaging predictions from multiple models.

## Features and Labels

### Labels
The target variable is the 'Total Export Crop Value in 1000 US$_lead_3', representing the export value shifted three years ahead.

### Features
- **Total Import Crop Value**
- **Fertiliser Use x Pesticides Use** (Interaction Term)
- **Total Export Crop Value (Lagged by 3 years)**
- **Area** (Geographic Region)
- **Year**
- **Item** (Specific Crop Type)

Additional features initially considered were dropped due to multicollinearity.

## Data Preprocessing

### Steps Involved
1. **Data Preparation:** Loading datasets, removing duplicates, and handling missing values.
2. **Mapping and Merging:** Integrating multiple datasets based on common attributes like Year, Area, and Item.
3. **Exploratory Data Analysis (EDA):** Analyzing distributions and applying log transformations to normalize skewed data.
4. **Encoding Categorical Features:** Using One Hot Encoding to convert categorical variables into a numerical format.
5. **Numeric Feature Transformation:** Applying log transformations and scaling to ensure equal contribution of features to the model.

## Usage Instructions

1. Clone the repository to your local machine:
   ```bash
   git clone https://github.com/yourusername/crop-export-prediction.git
   ```
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Prepare your dataset by following the preprocessing steps mentioned above.
4. Train the model:
   ```bash
   python train_model.py
   ```
5. Evaluate the model:
   ```bash
   python evaluate_model.py
   ```

## File Structure

- `train_model.py`: Script to train the MLP model.
- `evaluate_model.py`: Script to evaluate the model performance.
- `data/`: Directory containing the datasets.
- `models/`: Directory to save trained models.
- `notebooks/`: Jupyter notebooks for exploratory data analysis and feature engineering.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request for review.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
