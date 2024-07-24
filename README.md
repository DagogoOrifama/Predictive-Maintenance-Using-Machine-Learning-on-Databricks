# Machine Learning Model Development

This part of the project focuses on developing machine learning models to predict machine faults using sensor data from an industrial vibration sensor.

## Setup and Environment

- **Platform**: Databricks Machine Learning
- **Cluster**: Created with the latest Databricks runtime
- **Dataset**: `faultDataset.csv`

## Data Exploration and Cleaning

1. **Importing Dataset**: 
    - Uploaded `faultDataset.csv` to the Databricks file system.
    - Imported dataset into RDD and DataFrame formats using `sc.textFile` and `spark.read.csv`.

2. **Initial Data Cleaning**: 
    - Removed header rows using `mapPartitionsWithIndex`.
    - Defined schema for the DataFrame and converted RDD to DataFrame.
    - Created temporary views for SQL analysis using `createOrReplaceTempView`.

3. **Data Exploration**: 
    - Analyzed the dataset to evaluate minimum, average, and maximum values for each state of the `fault_detected` column.
    - Identified any missing or inconsistent data.

## Data Preprocessing

1. **Data Transformation**:
    - Used `RFormula` to transform data into a format suitable for machine learning.
    - The target variable (`fault_detected`) was assigned to the label column, and other features were included in the features column.

2. **Data Splitting**:
    - Split data into training (70%) and test (30%) sets using `randomSplit`.

## Machine Learning Models Developed

### Decision Tree Classification Model

- **Training**:
    - Trained the Decision Tree model using the training dataset.
    - Evaluated the model using `MulticlassClassificationEvaluator` to measure accuracy.

- **Results**:
    - Achieved 95.55% accuracy with default hyperparameters.
    - Improved accuracy to 95.56% through hyperparameter tuning using grid search.

### Other Models

- **Linear SVC**:
    - Trained and evaluated using the same process as the Decision Tree model.
    - Achieved an accuracy of 80.65%.

- **Logistic Regression**:
    - Trained and evaluated, achieving competitive accuracy.

- **Random Forest**:
    - Trained and evaluated, with a higher accuracy than Linear SVC and Logistic Regression.

- **Gradient-Boosted Tree**:
    - Achieved the highest accuracy of 99.67%.
    - Performed hyperparameter tuning for further optimization.

## Hyperparameter Tuning

- **Grid Search**:
    - Specified grids of values for parameters such as `maxDepth`, `maxBins`, `impurity`, and `minInstancesPerNode`.
    - Used `TrainValidationSplit` to find the optimal set of hyperparameters for each model.

- **Results**:
    - Gradient-Boosted Tree model maintained its high accuracy of 99.67% even after tuning.

## Data Privacy, Ethical, and Legal Issues

- Ensured that datasets used were publicly available and licensed for educational and research purposes.
- Adhered to data privacy and ethical guidelines throughout the project.

## Conclusion

This task demonstrates the development and evaluation of multiple machine learning models to predict machine maintenance needs based on sensor data. The Gradient-Boosted Tree model achieved the highest accuracy, showcasing its effectiveness for this task. The project highlights the importance of data preprocessing, model selection, and hyperparameter tuning in achieving high-performance machine learning models.

For more detailed information, please refer to the project report included in the repository.
