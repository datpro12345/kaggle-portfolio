# Project A: Telco Customer Churn Prediction

## Business Problem
Predict which Telco customers are likely to churn (cancel service) to enable timely retention strategies and reduce customer attrition costs.

## Dataset
- **Source**: Kaggle - `blastchar/telco-customer-churn`
- **Size**: 7,043 customers, 21 features
- **Target**: Churn (Yes/No) - 26.5% churn rate
- **Key Features**: Contract type, Tenure, Internet Service, Monthly Charges

## Model Performance

### Technical Metrics
- **Best Model**: XGBoost with GridSearchCV
- **ROC-AUC**: 0.8443
- **Test Accuracy**: 79.13%
- **Precision**: 68.18%
- **Recall**: 40.11% → 71% (after threshold optimization to 0.574)

### Business Impact
- **20/80 Strategy ROI**: $167,310
- **Break-even intervention cost**: $117.47
- Model outperforms baseline when intervention cost > $117
- Top 20% high-risk segment recommended for phone outreach, remaining 80% for email campaigns

## Methodology

### Feature Engineering
- **ChargeRatio**: MonthlyCharges/TotalCharges
- **TenureBin**: 12-month interval binning (0-12, 13-24, etc.)
- **Interaction Terms**: Internet_TechSupport

### Model Pipeline
- `ColumnTransformer` with separate transformers for numeric/categorical features
- `StandardScaler` + `OneHotEncoder`
- XGBoost with `scale_pos_weight=2.77` to handle class imbalance
- GridSearchCV for hyperparameter tuning (learning_rate: 0.01, max_depth: 6, n_estimators: 200)

### Evaluation Strategy
- Precision-Recall Curve for optimal threshold selection
- Cost-Benefit Analysis (assumptions: LTV=$500, Intervention Cost=$50-100)
- Lift & Cumulative Gains Charts for business value assessment

## Key Findings

### Root Cause Analysis
- **45.72%** of Fiber Optic customers churned within the first year without contacting Tech Support
- Median monthly charge for churners: $87.55 (indicates price sensitivity)
- **Top Features**: Contract type, Tenure, Internet Service type, Tech Support usage

### Actionable Insights
1. **Early Tenure Risk**: Customers in 0-12 month tenure bin require proactive monitoring
2. **Silent Failure Segment**: 593 Fiber Optic customers need infrastructure investigation (packet loss/latency logs)
3. **Tiered Intervention**: Deploy call campaigns for top 20%, email for remaining 80% to optimize cost-effectiveness

## Practical Lessons Learned: Academic vs Business Mindset

### 1. Objective
- **Academic**: Maximize Accuracy/Precision/ROC-AUC. Proud of 79% accuracy but ignores 40% Recall (missing 60% of churners).
- **Business**: Optimize Profit/ROI. Accept lower Precision for 71% Recall because missing a $500 LTV customer costs more than a $10 wrong voucher.

### 2. Solution Architecture
- **Academic**: Over-engineer with Ensemble/Stacking for 1-2% gain. Run sensitivity analysis on hypothetical costs when actual cost is known.
- **Business**: KISS principle. Use "Target Everyone" for cheap interventions (email) if it beats AI. Deploy AI only for expensive channels (calls). Ship baseline if it wins.

### 3. Data Interpretation
- **Academic**: Data is truth. Sees "Fiber Optic = high churn" and stops. Passively waits for more data.
- **Business**: Data shows symptoms. Asks "Why?" → Investigates infrastructure logs immediately. Proactive root cause analysis.

### 4. Decision Making
- **Academic**: Perfectionism. "No-Go" if model isn't perfect. Fears False Positives hurting metrics.
- **Business**: Speed over perfection. "Fix it in production." Ship imperfect model TODAY to capture revenue. Transform False Positives into opportunities (customers appreciate wrong vouchers).

**Key Takeaway**: In production ML, revenue waits for no one. Imperfect action today beats perfect analysis tomorrow.

## Next Steps

1. **Infrastructure Investigation**: Analyze packet loss/latency logs for 593 "Early Tech Failure" Fiber Optic customers
2. **A/B Testing**: Test conversion rates of Call vs Email segments
3. **Feedback Loop**: Collect actual intervention success rate data to refine cost-benefit assumptions
4. **Expand Model**: Incorporate time-series behavior patterns for dynamic churn prediction

## Project Structure

churn-prediction/
├── notebooks/
│   └── telco_churn_analysis.ipynb    # Full analysis & modeling
├── data/
│   └── .gitkeep                       # Raw data (gitignored)
├── results/
│   └── High_Risk_Customers.csv        # Top 20% priority list
├── README.md                          # This file
└── requirements.txt                   # Python dependencies

## Dependencies

pandas==2.0.3
numpy==1.24.3
matplotlib==3.7.2
seaborn==0.12.2
scikit-learn==1.3.0
xgboost==1.7.6
kagglehub==0.2.5


---

**Author Note**: This project demonstrates the shift from academic metric optimization to business value creation. The "Practical Lessons Learned" section is designed for reuse across future projects to avoid over-engineering and perfectionism traps.

