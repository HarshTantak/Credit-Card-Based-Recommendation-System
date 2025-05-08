
# 💳 Credit Card-Based Recommendation System


---

## 🧠 Overview

This project presents a smart, secure, and personalized credit card system that integrates:
- 🔐 **Fraud Detection** using ML and GNNs
- 👥 **Customer Segmentation** based on financial behavior
- 🤖 **Credit Card Recommendations** using deep learning (Neural Collaborative Filtering)

Built on a large real-world-scale transactional dataset (24M+ records), the system ensures fraud resilience, personalized service, and enhanced customer experience.

---

## 🎯 Objectives

1. **Fraud Detection**: Identify suspicious transactions using ensemble and graph-based models.  
2. **Customer Segmentation**: Cluster users based on financial and behavioral data.  
3. **Recommendation System**: Recommend credit card products tailored to user clusters using NCF.

---

## 📦 Dataset Overview

- `sd254_users.csv` – User demographics and financials  
- `sd254_cards.csv` – Card metadata (type, limit, chip, dark web exposure)  
- `User_credit_card_transactions.csv` – 24.4M transactions (with fraud labels)

---

## 📊 Exploratory Data Analysis Highlights

- 🔍 Most frauds occur for low-value transactions (<$250) and peak at 10–11 AM.
- 💳 Online transactions (non-chip) are more fraud-prone.
- 💸 Spending peaks in 2019, with “Other” categories dominating expenses.
- 🧓 Income declines with age; 18–24 earn the most on average.

---

## 🔐 Fraud Detection

### ✅ Models Used:
- **XGBoost**: Best balance of recall and precision
- **Random Forest**: High accuracy but overfits
- **Graph Neural Network (GNN)**: Edge-based learning from transaction networks

### 📈 Evaluation (XGBoost):
| Metric      | Value   |
|-------------|---------|
| Accuracy    | 94%     |
| Precision   | 0.88    |
| Recall      | 0.72    |
| ROC-AUC     | **0.9619** (with 'Use Chip' feature)

---

## 👥 Customer Segmentation

Filtered non-fraudulent users were clustered using K-Means (k=5), post PCA and VIF checks.

### 🚀 Features Used:
- Demographics: Age, Gender, Income  
- Credit Health: FICO Score, Debt, Credit Ratio  
- Behavior: Spend Category, Fraud Rate, Chip Use, Monthly Spend

### 🧪 Model Evaluation:
| Metric              | Value    |
|---------------------|----------|
| Silhouette Score    | **0.6092** |
| Davies-Bouldin Score| 0.9941   |

### 🔎 User Cluster Profiles:
- **Cluster 0**: Young, low-income, low-spend users  
- **Cluster 1**: Mid-age, responsible spenders  
- **Cluster 2**: Digitally active, lifestyle spenders  
- **Cluster 3**: High-credit, high-spending users  
- **Cluster 4**: Mature, conservative spenders

---

## 🤖 Recommendation System (NCF)

Built using **Neural Collaborative Filtering**, trained on a synthetic user–card interaction matrix with positive/negative labels.

### 🧠 Model Architecture:
- User & Card Embedding (16-dim)
- MLP: Layers [128 → 64 → 32]
- Output: Sigmoid → Interaction Score (0 to 1)

### 📊 Evaluation Metrics:
| Metric      | Value   |
|-------------|---------|
| Accuracy    | 0.9392  |
| Precision   | 0.9100  |
| Recall      | 0.9615  |
| F1-Score    | 0.9351  |
| ROC-AUC     | 0.9411  |
| Hit@10      | 0.9639  |
| Recall@10   | 0.5084  |
| NDCG@10     | 0.3567  |

---

## 📌 Example Output

**User 1019 (Cluster 0):**  
1. Bluebird by Amex – 0.896  
2. Citi Custom Card – 0.8817  
3. Discover It Cash Back – 0.8781  

**User 913 (Cluster 4):**  
1. Chase Sapphire Reserve – 0.9269  
2. Marriott Bonvoy Business – 0.9222  
3. Amex Business Platinum – 0.9055  

---

## 🧾 Conclusion

- **Fraud Detection**: XGBoost performed best with ROC-AUC 0.96  
- **Segmentation**: K-Means yielded 5 actionable user profiles  
- **Recommendations**: NCF achieved high personalization accuracy  
- Integrated system allows secure, tailored, and data-informed decision-making for credit card management.

---

## 🚧 Limitations

- Static clustering does not reflect evolving user behavior  
- Recommendations may not suit all individuals in a cluster  
- Cold start issues for new users  
- High computational cost for real-time inference

---

## 🔮 Future Scope

- Dynamic behavior tracking and time-aware clustering  
- Real-time fraud detection using graph streaming  
- Cross-platform deployment (mobile/POS integration)  
- Application to other domains like digital wallets and BNPL
