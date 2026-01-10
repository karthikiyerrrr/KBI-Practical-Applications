# Used Car Price Analysis - Key Findings and Recommendations

## Executive Summary

This analysis identified the key factors that drive used car prices based on a dataset of 426,880 used car listings. The final dataset after cleaning contained 303,869 complete records, and a Linear Regression model was used to predict car prices and identify feature importance.

## Key Drivers of Used Car Prices

Based on the feature importance analysis, the following factors are the most influential in determining used car prices:

### Top 5 Most Important Features:

1. **Manufacturer** - The car brand/manufacturer has the strongest impact on price
2. **Condition** - Vehicle condition significantly affects valuation
3. **Cylinders** - Engine size/configuration (now modeled as numeric) is a major price driver
4. **Vehicle Type** - The type of vehicle (sedan, SUV, truck, etc.) impacts price
5. **Fuel Type** - Fuel type (gas, diesel, hybrid, etc.) influences price

*Note: Feature importance values are measured differently for numeric vs categorical features. Numeric features use absolute coefficient values, while categorical features use the range method (max - min coefficient values).*

### Additional Important Features:

- **Paint Color** (Importance: 0.41)
- **Transmission** (Importance: 0.40)
- **Drive Type** (Importance: 0.36)
- **Year** (Importance: 0.31)
- **Odometer** (Importance: 0.11)

## Model Performance

The Linear Regression model achieved consistent performance across training, validation, and test sets:

- **RMSE (Dollar Space)**: ~$10,600 - $10,800
- **MAE (Dollar Space)**: ~$6,900 - $7,000

This indicates the model generalizes well and provides reliable price predictions.

## Recommendations for Used Car Dealerships

### 1. **Inventory Strategy**
   - **Focus on Manufacturer Selection**: Since manufacturer has the highest impact on price, prioritize acquiring vehicles from brands that command higher resale values in your market
   - **Vehicle Condition is Critical**: Invest in reconditioning to improve vehicle condition ratings, as this is the second-most important price driver

### 2. **Pricing Strategy**
   - **Engine Configuration Matters**: Pay close attention to cylinder count (now modeled as a numeric feature), as it has a significant impact on price
   - **Vehicle Type Selection**: Different vehicle types have varying price impacts - align inventory mix with market demand

### 3. **Marketing and Positioning**
   - **Emphasize Condition**: Highlight vehicle condition in listings, as this significantly affects consumer valuation
   - **Manufacturer Branding**: Leverage manufacturer reputation and brand value in marketing materials

### 4. **Data Collection Priorities**
   - Ensure accurate recording of: manufacturer, condition, cylinders, vehicle type, and fuel type
   - These five features together explain the majority of price variation

## Methodology

- **Dataset**: 426,880 used car listings (cleaned to 303,869 complete records)
- **Model**: Linear Regression with log-transformed target variable
- **Features**: 
  - Standardized numeric features: year, odometer, cylinders (cylinders converted from categorical to numeric during data preparation)
  - One-hot encoded categorical features: manufacturer, fuel, type, transmission, drive, paint_color, condition
- **Evaluation**: Train/Validation/Test split (60%/20%/20%) with consistent performance across all sets

## Visualizations

The analysis includes comprehensive visualizations showing:
- Feature importance rankings for all features
- Categorical feature statistics (range, standard deviation, mean) demonstrating the variability of impact within each categorical feature

