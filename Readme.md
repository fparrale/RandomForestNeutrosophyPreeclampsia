# Preeclampsia Prediction using Random Forest with Neutrosophic Interpretation

## Description
This project implements a Random Forest classifier to predict preeclampsia cases from clinical and demographic data, enhanced with neutrosophic logic to quantify prediction uncertainty. The model evaluates the confidence of predictions by categorizing them into Truth (T), Indeterminacy (I), and Falsity (F) components based on probability thresholds.

## Dataset
The dataset (`02-Logan preeclampsia dataset FinalORIGINAL.csv`) contains clinical records with the following relevant features:
- Maternal age, education, marital status
- Pregnancy history (gravidity, parity)
- Antenatal care visits
- Delivery mode and birth weight
- Hemoglobin levels
- Lifestyle factors (tobacco/alcohol use)
- Medical history (diabetes, hypertension)

The target variable `casecontrol` is binary (Case = Preeclampsia, Control = Normal).

## Methodology
1. **Data Preprocessing**:  
   - Selected relevant features and removed missing values.
   - Converted the target variable to a factor (`Control`/`Case`).

2. **Model Training**:  
   - Split data into 80% training and 20% testing sets.
   - Trained a Random Forest model with 100 trees and evaluated feature importance.

3. **Neutrosophic Interpretation**:  
   - Predictions were mapped to neutrosophic values (T, I, F) based on probability thresholds:
     - **T ≥ 0.9**: High confidence (Truth = 0.9, Indeterminacy = 0.1, Falsity = 0.0)
     - **0.7 ≤ T < 0.9**: Moderate confidence (Truth = 0.7, Indeterminacy = 0.2, Falsity = 0.1)
     - **0.5 ≤ T < 0.7**: Low confidence (Truth = 0.5, Indeterminacy = 0.3, Falsity = 0.2)
     - **T < 0.5**: Very low confidence (Truth = 0.2, Indeterminacy = 0.3, Falsity = 0.5)

4. **Evaluation**:  
   - Generated a confusion matrix and visualized feature importance.
   - Plotted neutrosophic values against predicted probabilities.

## Results
- The model performance is summarized in the confusion matrix (printed during execution).
- Key features influencing predictions are shown in the variable importance plot.
- The neutrosophic plot illustrates the relationship between prediction probabilities and confidence levels (T, I, F).

## Requirements
- R (≥ 4.0.0)
- R Libraries:
  - `tidyverse`
  - `randomForest`
  - `caret`
  - `ggplot2`

## Usage
1. Clone the repository and set the working directory in `PreeclampsiaNeutrosophyRandomForest.R`.
2. Ensure the dataset is placed in the specified path.
3. Run the script to train the model, generate predictions, and visualize results.

## Output
- **Variable Importance Plot**: Highlights key predictors of preeclampsia.
- **Neutrosophic Plot**: Displays Truth (blue), Indeterminacy (orange), and Falsity (red) values against predicted probabilities.

## License
This project is open-source under the MIT License.
