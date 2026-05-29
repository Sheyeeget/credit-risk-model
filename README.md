## Credit Scoring Business Understanding

### 1. How does Basel II influence model interpretability and documentation?

The Basel II Accord requires banks to:
- **Explain decisions** - Regulators must understand WHY a customer gets a specific score
- **Document everything** - All model choices, features, and validations must be recorded
- **Be auditable** - The model must be reviewable by regulators at any time

This means our model cannot be a "black box" - we need clear documentation of why we chose each feature and how predictions are made.

### 2. Why is a proxy variable necessary and what risks does it introduce?

**Why needed:** The data has NO default labels. We don't know which customers actually defaulted.

**Our proxy solution:** Use RFM (Recency, Frequency, Monetary) analysis to identify disengaged customers as "high risk"

**Risks:**
- **Proxy gap** - Disengaged ≠ Default (may mislabel customers)
- **False positives** - Good customers denied credit (lost business)
- **False negatives** - Bad customers approved (bank losses)

### 3. Trade-offs: Simple vs Complex Models

| Aspect | Simple (Logistic Regression) | Complex (Random Forest/XGBoost) |
|--------|------------------------------|--------------------------------|
| Interpretability | Easy to explain | Hard to explain |
| Performance | Good | Better |
| Regulatory approval | Easy | Needs extra work |
| Development time | Fast | Slower |

**Our approach:** Build BOTH models. Use simple model for regulatory compliance and complex model for better predictions with SHAP explanations.
