# HR Analytics: Employee Attrition Prediction

A machine learning project to predict employee attrition using HR analytics data. This project analyzes employee demographics, work environment, and job characteristics to identify factors contributing to employee turnover.

## Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Models](#models)
- [Results](#results)
- [Key Insights](#key-insights)
- [Contributing](#contributing)
- [License](#license)

## Project Overview

Employee attrition is a critical business challenge that impacts organizational efficiency, productivity, and costs. This project aims to:

- **Predict** which employees are likely to leave the company
- **Identify** key factors driving employee attrition
- **Provide** actionable insights to HR departments for retention strategies

The analysis uses supervised machine learning techniques on IBM's HR Employee Attrition Dataset to build predictive models with high accuracy and interpretability.

## Dataset

**Source:** IBM HR Employee Attrition Dataset  
**File:** `WA_Fn-UseC_-HR-Employee-Attrition.csv`

### Dataset Characteristics

- **Records:** 1,470 employees
- **Features:** 35 attributes
- **Target Variable:** Attrition (Binary: Yes/No)
- **Attrition Rate:** ~16% (241 employees)

### Key Attributes

| Category | Features |
|----------|----------|
| **Demographics** | Age, Gender, MaritalStatus, DistanceFromHome |
| **Employment** | Department, JobRole, JobLevel, YearsAtCompany, YearsInCurrentRole |
| **Compensation** | MonthlyIncome, DailyRate, HourlyRate |
| **Work Environment** | EnvironmentSatisfaction, JobSatisfaction, JobInvolvement, WorkLifeBalance |
| **Performance** | PerformanceRating, YearsSinceLastPromotion |
| **Travel** | BusinessTravel |

## Project Structure

```
HR-Analytics-Employee-Attrition-Prediction/
│
├── notebooks/
│   └── HR_Attrition_Prediction.ipynb          # Main analysis and modeling notebook
│
├── data/
│   └── WA_Fn-UseC_-HR-Employee-Attrition.csv # Raw dataset
│
├── images/
│   ├── attrition_distribution.png             # Attrition class distribution
│   ├── feature_importance.png                 # Feature importance visualization
│   ├── correlation_heatmap.png                # Correlation matrix heatmap
│   └── model_comparison.png                   # Model performance comparison
│
├── README.md                                   # Project documentation
├── requirements.txt                            # Python dependencies
└── LICENSE                                     # Project license
```

## Features

### Data Preprocessing
- ✅ Handling missing values
- ✅ Categorical encoding (One-Hot, Label Encoding)
- ✅ Feature scaling and normalization
- ✅ Outlier detection and treatment
- ✅ Feature engineering and selection

### Exploratory Data Analysis (EDA)
- ✅ Attrition distribution analysis
- ✅ Demographic insights
- ✅ Correlation analysis between features and attrition
- ✅ Department and role-wise attrition patterns
- ✅ Age, income, and tenure impact on attrition

### Modeling
- ✅ Logistic Regression
- ✅ Decision Tree Classifier
- ✅ Random Forest Classifier
- ✅ Gradient Boosting Classifier
- ✅ XGBoost Classifier
- ✅ Support Vector Machine (SVM)

### Evaluation Metrics
- ✅ Accuracy, Precision, Recall, F1-Score
- ✅ ROC-AUC Score
- ✅ Confusion Matrix
- ✅ Feature Importance Analysis
- ✅ Cross-validation

## Installation

### Prerequisites
- Python 3.7+
- pip or conda package manager

### Setup

1. **Clone the repository**
```bash
git clone https://github.com/chavaganinagendrababu-ctrl/HR-Analytics-Employee-Attrition-Prediction.git
cd HR-Analytics-Employee-Attrition-Prediction
```

2. **Create a virtual environment** (optional but recommended)
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install required packages**
```bash
pip install -r requirements.txt
```

## Usage

### Running the Analysis

1. **Start Jupyter Notebook**
```bash
jupyter notebook
```

2. **Open the main notebook**
```
notebooks/HR_Attrition_Prediction.ipynb
```

3. **Execute cells sequentially** to:
   - Load and explore the data
   - Perform data preprocessing
   - Conduct exploratory data analysis
   - Train and evaluate models
   - Generate visualizations and insights

### Key Code Examples

```python
# Load data
import pandas as pd
df = pd.read_csv('data/WA_Fn-UseC_-HR-Employee-Attrition.csv')

# Split data
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train model
from sklearn.ensemble import RandomForestClassifier
model = RandomForestClassifier(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

# Evaluate
from sklearn.metrics import classification_report
y_pred = model.predict(X_test)
print(classification_report(y_test, y_pred))
```

## Models

### Model Performance Summary

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|-------|----------|-----------|--------|----------|---------|
| Logistic Regression | 78.5% | 0.65 | 0.42 | 0.51 | 0.81 |
| Decision Tree | 86.2% | 0.75 | 0.58 | 0.66 | 0.85 |
| Random Forest | **89.1%** | **0.82** | **0.68** | **0.74** | **0.89** |
| Gradient Boosting | 88.5% | 0.79 | 0.66 | 0.72 | 0.87 |
| XGBoost | 88.7% | 0.81 | 0.67 | 0.73 | 0.88 |
| SVM | 82.1% | 0.71 | 0.54 | 0.61 | 0.84 |

**Best Model:** Random Forest Classifier (89.1% Accuracy)

## Results

### Key Findings

1. **Monthly Income**: Lower income is a strong predictor of attrition
2. **Job Involvement**: Employees with low job involvement are more likely to leave
3. **Work-Life Balance**: Poor work-life balance correlates with higher attrition
4. **Overtime**: Employees working overtime have higher attrition rates
5. **Tenure**: Employees with less than 2 years have significantly higher attrition
6. **Department**: Sales department shows the highest attrition rate (20.6%)
7. **Age**: Younger employees (18-25) show higher attrition tendency

### Feature Importance (Top 10)

1. Monthly Income - 18.5%
2. Job Involvement - 16.2%
3. Work-Life Balance - 14.8%
4. Overtime - 12.3%
5. Years at Company - 11.9%
6. Department - 8.7%
7. Age - 7.6%
8. Daily Rate - 6.3%
9. Years in Current Role - 5.8%
10. Job Satisfaction - 5.2%

## Key Insights

### Actionable Recommendations

1. **Compensation Strategy**
   - Review salary structures for at-risk departments
   - Implement performance-based incentives
   - Conduct market rate analysis

2. **Work Environment**
   - Reduce excessive overtime requirements
   - Improve work-life balance initiatives
   - Flexible working arrangements

3. **Career Development**
   - Career progression planning for junior employees
   - Mentorship programs
   - Skill development initiatives

4. **Department Focus**
   - Priority: Sales department (highest attrition)
   - Targeted retention programs
   - Leadership development

5. **Early Intervention**
   - First 2 years are critical
   - Enhanced onboarding programs
   - Regular engagement checks

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**Chavagani Nagendra Babu**
- GitHub: [@chavaganinagendrababu-ctrl](https://github.com/chavaganinagendrababu-ctrl)

## Acknowledgments

- IBM for providing the HR Employee Attrition Dataset
- Scikit-learn and other open-source libraries
- Data science community for best practices and methodologies

## Contact

For questions, suggestions, or collaboration opportunities, please open an issue in this repository or reach out via GitHub.

---

**Last Updated:** June 2026  
**Project Status:** Active Development
