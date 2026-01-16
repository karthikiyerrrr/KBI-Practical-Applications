# Used Car Price Analysis - Key Findings and Recommendations

## Executive Summary

This analysis identified the key factors that drive used car prices based on a dataset of 426,880 used car listings. The final dataset after cleaning contained 303,869 complete records, and a Linear Regression model was used to predict car prices and identify feature importance.

## Key Drivers of Used Car Prices

Based on the feature importance analysis, the following factors are the most influential in determining used car prices:

### Top 5 Most Important Features:

1. **Manufacturer** (Importance: 1.97) - The car brand/manufacturer has the strongest impact on price
2. **Condition** (Importance: 1.55) - Vehicle condition significantly affects valuation
3. **Vehicle Type** (Importance: 0.71) - The type of vehicle (sedan, SUV, truck, etc.) impacts price
4. **Fuel Type** (Importance: 0.51) - Fuel type (gas, diesel, hybrid, etc.) influences price
5. **Paint Color** (Importance: 0.46) - Paint color has a moderate impact on price

*Note: Feature importance values are measured differently for numeric vs categorical features. Numeric features use absolute coefficient values, while categorical features use the range method (max - min coefficient values).*

### Additional Important Features:

- **Transmission** (Importance: 0.40)
- **Drive Type** (Importance: 0.39)
- **Year** (Importance: 0.31)
- **Odometer** (Importance: 0.10)
- **Cylinders** (Importance: 0.07)

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
   - **Vehicle Type Selection**: Different vehicle types have varying price impacts - align inventory mix with market demand
   - **Fuel Type Consideration**: Fuel type (gas, diesel, hybrid, electric) has a meaningful impact on price - consider market preferences

### 3. **Marketing and Positioning**
   - **Emphasize Condition**: Highlight vehicle condition in listings, as this significantly affects consumer valuation
   - **Manufacturer Branding**: Leverage manufacturer reputation and brand value in marketing materials

### 4. **Data Collection Priorities**
   - Ensure accurate recording of: manufacturer, condition, vehicle type, fuel type, and paint color
   - These top five features together explain the majority of price variation
   - While cylinders is less important, it should still be recorded for completeness

## Methodology

- **Dataset**: 426,880 used car listings (cleaned to 303,869 complete records)
- **Data Cleaning**: 
  - Removed records with missing critical information (model, odometer, year)
  - Applied price filter: 0 < price ≤ $200,000 (removed zero prices and extreme outliers)
  - Imputed missing values using contextual information (model, year, etc.)
- **Model**: Linear Regression with log-transformed target variable
- **Features**: 
  - Standardized numeric features: year, odometer, cylinders (cylinders converted from categorical to numeric during data preparation)
  - One-hot encoded categorical features: manufacturer, fuel, type, transmission, drive, paint_color, condition
- **Evaluation**: Train/Validation/Test split (60%/20%/20%) with consistent performance across all sets

## Visualizations

The analysis includes comprehensive visualizations showing:
- Feature importance rankings for all features
- Categorical feature statistics (range, standard deviation, mean) demonstrating the variability of impact within each categorical feature

