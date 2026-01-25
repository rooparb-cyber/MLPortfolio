# Bank Marketing Campaign Analysis: Predicting Term Deposit Subscriptions

This project aims to build and evaluate machine learning models to predict whether a bank client will subscribe to a term deposit based on various client, campaign, and economic attributes. The ultimate goal is to optimize marketing campaign efficiency and conversion rates.

## Problem Statement (Business Objective)

The business objective is to predict whether a client will subscribe to a term deposit ('y') so the bank can target marketing calls more efficiently, improve campaign conversion rates, and reduce wasted outreach efforts. By accurately identifying potential subscribers, the bank can optimize resource allocation and enhance overall campaign effectiveness.

## Key metrics considered and reasoning 
In this context, high recall is vital because the business goal is to capture as many potential subscribers as possible; missing a "yes" (a False Negative) represents a direct loss of revenue and a failed campaign opportunity. Since the cost of an automated marketing call is relatively low compared to the lifetime value of a new term deposit, it is more profitable to cast a wide net than to be overly selective.

### Link to Notebook###
https://github.com/rooparb-cyber/MLPortfolio/blob/main/Practical%20Application%203/solution_III.ipynb

## Key Insights Generated

### 1. Data Imbalance

*   The target variable 'y' (term deposit subscription) is highly imbalanced - this lists the proportions of the full dataset and sample dataset is comparable:
    *   `'no'`: ~88.7%
    *   `'yes'`: ~11.3%
*   This imbalance means traditional accuracy alone is not a reliable metric. Precision, Recall, and F1-score are crucial for evaluating performance.

### 2. Model Performance Comparison (Default Settings)

*(Refer to the 'All Metrics Comparison Across Models' heatmap or the series of bar plots in the notebook for a visual overview)*

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Model</th>
      <th>Fit Time (s)</th>
      <th>Predict Time (s)</th>
      <th>Train Accuracy</th>
      <th>Test Accuracy</th>
      <th>Test Precision</th>
      <th>Test Recall</th>
      <th>Test F1-Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>K Nearest Neighbors</td>
      <td>0.049654</td>
      <td>0.174859</td>
      <td>0.914264</td>
      <td>0.888080</td>
      <td>0.512195</td>
      <td>0.291979</td>
      <td>0.371935</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Support Vector Machine</td>
      <td>42.373660</td>
      <td>6.409299</td>
      <td>0.904765</td>
      <td>0.896941</td>
      <td>0.612565</td>
      <td>0.250267</td>
      <td>0.355353</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Decision Tree</td>
      <td>0.183644</td>
      <td>0.008773</td>
      <td>0.995357</td>
      <td>0.840252</td>
      <td>0.311573</td>
      <td>0.336898</td>
      <td>0.323741</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Logistic Regression</td>
      <td>0.179525</td>
      <td>0.009433</td>
      <td>0.901275</td>
      <td>0.897062</td>
      <td>0.641694</td>
      <td>0.210695</td>
      <td>0.317230</td>
    </tr>
  </tbody>
</table>
</div>

*   **K Nearest Neighbors** showed the highest `Test F1-Score` (0.3714) among default models, indicating the best balance of precision and recall for identifying 'yes' subscriptions, despite a relatively high `Predict Time`.
*   **Support Vector Machine** had competitive `Test F1-Score` (0.3554) and high `Test Precision`, but suffered from significantly long `Fit Time`.
*   **Decision Tree** shows the best recall but might have overfit the training data (`Train Accuracy` 0.9954 vs `Test Accuracy` 0.8399), making it unreliable. 
*   **Logistic Regression** offered fast prediction and high precision but struggled with `Recall`.

### 3. Tuned Model performance on all models using sampled data

*(Refer to the 'All Metrics Comparison Across Tuned Models' heatmap in the notebook for a visual overview)*

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>model</th>
      <th>best_params</th>
      <th>fit_time_seconds</th>
      <th>predict_time_seconds</th>
      <th>train_accuracy</th>
      <th>train_precision</th>
      <th>train_recall</th>
      <th>train_f1</th>
      <th>test_accuracy</th>
      <th>test_precision</th>
      <th>test_recall</th>
      <th>test_f1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>dummy</td>
      <td>{'dummy__strategy': 'most_frequent'}</td>
      <td>9.019366</td>
      <td>0.004489</td>
      <td>0.891047</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.888350</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>knn</td>
      <td>{'knn__n_neighbors': 7}</td>
      <td>0.604324</td>
      <td>0.008122</td>
      <td>0.904097</td>
      <td>0.640523</td>
      <td>0.272981</td>
      <td>0.382812</td>
      <td>0.893204</td>
      <td>0.558824</td>
      <td>0.206522</td>
      <td>0.301587</td>
    </tr>
    <tr>
      <th>2</th>
      <td>logisticregression</td>
      <td>{'logisticregression__C': 0.1}</td>
      <td>0.089622</td>
      <td>0.002431</td>
      <td>0.818513</td>
      <td>0.326055</td>
      <td>0.623955</td>
      <td>0.428298</td>
      <td>0.813107</td>
      <td>0.327778</td>
      <td>0.641304</td>
      <td>0.433824</td>
    </tr>
    <tr>
      <th>3</th>
      <td>svc</td>
      <td>{'svc__C': 1, 'svc__kernel': 'rbf'}</td>
      <td>3.415156</td>
      <td>0.122358</td>
      <td>0.867982</td>
      <td>0.434028</td>
      <td>0.696379</td>
      <td>0.534759</td>
      <td>0.858010</td>
      <td>0.407407</td>
      <td>0.597826</td>
      <td>0.484581</td>
    </tr>
    <tr>
      <th>4</th>
      <td>decisiontree</td>
      <td>{'decisiontree__max_depth': 15}</td>
      <td>0.105248</td>
      <td>0.002050</td>
      <td>0.962367</td>
      <td>0.743271</td>
      <td>1.000000</td>
      <td>0.852732</td>
      <td>0.824029</td>
      <td>0.261261</td>
      <td>0.315217</td>
      <td>0.285714</td>
    </tr>
  </tbody>
</table>
</div>

*  ***The Dummy Classifier*** hits 88% accuracy by never predicting a subscription. 
* ***kNN*** yields the highest accuracy but suffers from "Recall blindness," missing 80% of potential customers.
* ***Logistic Regression*** is the top performer for the primary business goal. Its 64.1% Recall captures the largest share of the market—identifying twice as many subscribers as kNN.Operational Efficiency: Logistic Regression is a "production-ready" powerhouse. It matches the dummy model's lightning-fast 0.002s prediction time, making it 50x faster than the SVC.
* ***SVC***  While the SVC achieves a slightly higher F1-score through better precision, it is the most "expensive" model. The marginal gains do not justify the 44x increase in training time and significantly higher prediction latency.
* ***In conclusion*** Logistic Regression shows the best generalization, with nearly identical Training and Test F1-scores, ensuring reliable performance in a C# production environment.Final Verdict: Logistic Regression is the optimal choice. It balances the highest reach (Recall) with the lowest technical debt and maximum stability.

### 4. Feature Importance (Final Logistic Regression Model Coefficients)

*(Refer to the 'Logistic Regression Feature Coefficients for Predicting "Yes"' bar plot in the notebook for a visual overview)*

**Top 10 features positively influencing a 'yes' subscription:**

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Feature</th>
      <th>Coefficient</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>40</th>
      <td>month_mar</td>
      <td>1.351762</td>
    </tr>
    <tr>
      <th>58</th>
      <td>cons.price.idx</td>
      <td>1.164785</td>
    </tr>
    <tr>
      <th>60</th>
      <td>euribor3m</td>
      <td>0.469480</td>
    </tr>
    <tr>
      <th>36</th>
      <td>month_aug</td>
      <td>0.456832</td>
    </tr>
    <tr>
      <th>61</th>
      <td>nr.employed</td>
      <td>0.397603</td>
    </tr>
    <tr>
      <th>20</th>
      <td>education_illiterate</td>
      <td>0.328235</td>
    </tr>
    <tr>
      <th>33</th>
      <td>contact_cellular</td>
      <td>0.302481</td>
    </tr>
    <tr>
      <th>37</th>
      <td>month_dec</td>
      <td>0.299026</td>
    </tr>
    <tr>
      <th>5</th>
      <td>job_retired</td>
      <td>0.269609</td>
    </tr>
    <tr>
      <th>52</th>
      <td>poutcome_success</td>
      <td>0.253251</td>
    </tr>
  </tbody>
</table>
</div>

**Top 10 features negatively influencing a 'yes' subscription:**

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Feature</th>
      <th>Coefficient</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>job_housemaid</td>
      <td>-0.162523</td>
    </tr>
    <tr>
      <th>35</th>
      <td>month_apr</td>
      <td>-0.235852</td>
    </tr>
    <tr>
      <th>55</th>
      <td>pdays</td>
      <td>-0.244605</td>
    </tr>
    <tr>
      <th>11</th>
      <td>job_unknown</td>
      <td>-0.248336</td>
    </tr>
    <tr>
      <th>50</th>
      <td>poutcome_failure</td>
      <td>-0.362560</td>
    </tr>
    <tr>
      <th>34</th>
      <td>contact_telephone</td>
      <td>-0.375961</td>
    </tr>
    <tr>
      <th>42</th>
      <td>month_nov</td>
      <td>-0.645079</td>
    </tr>
    <tr>
      <th>41</th>
      <td>month_may</td>
      <td>-0.647913</td>
    </tr>
    <tr>
      <th>39</th>
      <td>month_jun</td>
      <td>-0.811018</td>
    </tr>
    <tr>
      <th>57</th>
      <td>emp.var.rate</td>
      <td>-2.366705</td>
    </tr>
  </tbody>
</table>
</div>

These coefficients highlight critical factors for subscription, with `month_mar` (March) being the strongest positive influence and `emp.var.rate` (employment variation rate) being the strongest negative influence.

## Actionable Recommendations for the Bank

Based on the insights from the final Logistic Regression model's feature coefficients, the bank can take the following actions to influence 'yes' subscriptions:

1.  **Optimize Campaign Timing**: Intensify marketing efforts during highly effective months such as **March, August, and December**. Reduce or re-evaluate campaigns in less effective months like **June, May, November, and April**.

2.  **Refine Contact Strategy**: Prioritize **cellular phone contact** over traditional telephone calls, as it shows a significantly higher positive impact.

3.  **Target Specific Demographics**: Focus marketing efforts on client segments that show higher propensity to subscribe:
    *   **Retired individuals** (`job_retired`).
    *   Clients with a **successful outcome** from a previous campaign (`poutcome_success`).
    *   Consider the unexpected positive influence of `education_illiterate` and investigate this demographic further to understand the underlying reasons.

4.  **Leverage Economic Indicators**: Pay attention to **consumer price index (`cons.price.idx`) and Euribor 3-month rate (`euribor3m`)** trends. Higher values in these indicators correlate with increased subscription likelihood.

5.  **Address Negative Indicators**: Avoid or rethink strategies for clients associated with strong negative indicators:
    *   Clients with a **high employment variation rate (`emp.var.rate`)** are highly unlikely to subscribe. Tailor offers or avoid outreach to this group.
    *   Clients whose previous campaign outcome was a **failure (`poutcome_failure`)** are less receptive.
    *   Clients with **unknown job types (`job_unknown`)** or in `job_housemaid` roles show lower subscription rates.

6.  **Maintain Recent Engagement**: Clients who were **recently contacted from a previous campaign (`pdays` lower than 999)** are more likely to subscribe. Avoid long gaps between contacts unless necessary.
