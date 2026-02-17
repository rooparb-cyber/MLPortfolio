# Capstone Project - University Student Mental Health Indicators

**Roopa Balakrishnan(Ramaswamy)**

# Executive summary

# Rationale
Institutional resources for student support are often limited and reactive. By identifying the most impactful predictors of distress, universities and high schools can shift toward proactive intervention. This allows for the design of targeted support programs that address the root causes of stress—whether they be academic, financial, or social—before they escalate into severe mental health crises.

# Research Question
Can we accurately predict the risk of significant student mental health distress by modeling the interplay between academic performance, socioeconomic proxies, and lifestyle factors?

# Data Sources
Structured student dataset, such as "University Student Mental Health Indicators Dataset" available on [Kaggle](https://www.kaggle.com/datasets/yuanchunhong/university-student-mental-health-indicators), which provides validated stress indices alongside demographic and academic variables.

# Methodology
To address both the prediction and inference goals of this study, I will apply the following methods:

- Preprocessing & Feature Engineering: Creating composite "Pressure Indices" and applying StandardScaler to ensure coefficients are comparable across different scales.

- Logistic Regression: To establish a baseline for prediction and use its coefficients to understand the linear relationship between factors like financial stress and mental health risk. <code style="color : red">(*look at methodology changes*)</code>

- Decision Tree Classifier: To capture non-linear relationships and create an interpretable "risk flowchart." This will help identify specific thresholds (e.g., a critical drop-off in health when sleep falls below 5 hours).  Although the dataset I have chosen has 1800 rows - and could be considered limiting for decision trees.

- Support Vector Classifier (SVC): To find the optimal hyperplane that separates "At Risk" from "Not At Risk" students, particularly if the relationships in the data are high-dimensional or complex.

- K-Nearest Neighbors (KNN): To classify students based on their similarity to "profiles" of previous students. 

# Results

## Exploratory Data Analysis (EDA) Findings (Notebook link )
The EDA identified that the dataset’s strength lies in its psychological indicators rather than its academic or demographic variables.

- Feature Variance: PCA results showed a flat variance profile, showing that no single linear combination of features dominates the dataset.

- Correlation Analysis: The correlation matrix revealed near-zero coefficients between features (e.g., PHQ9 and GAD7 had a correlation of only -0.016), indicating high feature independence.

- Predictive Signals: KDE plots demonstrated significant class separation for PHQ9 and GAD7, making them the primary candidates for the baseline model.

- Feature Pruning: GPA was removed from the feature set prior to modeling due to its perfect distributional overlap between classes, which would have introduced unnecessary noise.


### Methodology Changes 
I had originally planned for Logistic Regression for baseline modeling, but have moved in favor of Decision tree to better handle the non-linear thresholds found in the KDE plots

### Baseline Model Performance
A Decision Tree Classifier was utilized to establish a performance benchmark, specifically chosen for its ability to handle non-linear thresholds and class imbalance.

### Choice of Evaluation Metric: F1-Score vs. Accuracy
* While Accuracy is a common metric, it can be highly misleading when working with imbalanced datasets like this one.

* The Accuracy Trap: In a dataset where 90% of students are "Not at Risk," a model could achieve 90% accuracy by simply predicting "Not at Risk" for everyone—completely failing to identify the 10% of students who actually need help.

* Balancing Precision and Recall: The F1-score is the harmonic mean of Precision and Recall, making it a much more robust measure for this research question.

> | Model | F1-Score | Note |
> |---|---|---|
> | Dummy Classifier | 0.3700 | Stratified baseline representing random chance|
> | Decision Tree (Baseline) | 0.5929 | Higher performing baseline using class_weight='balanced'.  There is substantial "heavy lifting" left. |

### Feature Importance Analysis
The chart in the *Feature importance graphing* cell provides a mathematical ranking of how much each variable contributed to the Decision Tree’s 0.5929 F1-score:

- Dominant Predictors: PHQ9 and GAD7 are the clear leaders, validating the KDE plot findings that these clinical scales offer the strongest class separation.

- Secondary Signals: ExerciseFreq and FinancialStress hold mid-tier importance. While they didn't show massive shifts in EDA, the model found specific thresholds within these variables to refine its predictions.

- Noise Reduction: Features like SocialActivity and SleepQuality appear at the bottom. This supports the earlier intuition that many lifestyle factors in this dataset provide very subtle, perhaps even negligible, predictive value on their own.

- Successful Pruning: By having already removed GPA (which showed zero separation), we have ensured the model didn't waste its limited "splitting power" on a feature that would have ranked at the very bottom or confused the baseline.

#### Next steps
What suggestions do you have for next steps?

#### Outline of project

- [Link to notebook 1]()
- [Link to notebook 2]()
- [Link to notebook 3]()


##### Contact and Further Information