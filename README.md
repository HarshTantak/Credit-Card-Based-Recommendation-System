# 💳 Credit Card-Based Recommendation System


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

## 🔐 Fraud Detection

### ✅ Models Used:
- **XGBoost**: Best balance of recall and precision  
- **Random Forest**: High accuracy but overfits  
- **Graph Neural Network (GNN)**: Captures relational patterns across cards and merchants

### 📈 Evaluation (XGBoost):
| Metric      | Value   |
|-------------|---------|
| Accuracy    | 94%     |
| Precision   | 0.88    |
| Recall      | 0.72    |
| ROC-AUC     | **0.9619** (with 'Use Chip' feature)

---

### 🧠 GNN-Based Fraud Detection

Constructed a **heterogeneous transaction graph** where:
- **Nodes** = Cards and Merchants  
- **Edges** = Transactions between card–merchant pairs  

**Edge Features**:
- Amount, timestamp, chip usage  
- MCC, Merchant location, Error flags

**Model Design**:
- Used GraphSAGE/GCN layers  
- Feature matrix `X ∈ ℝⁿˣᵈ`  
- Binary cross-entropy loss  
- Adam optimizer

**Outcome**:
- Captured merchant–card fraud rings  
- Detected subtle fraud trends not found by classic ML  
- Low recall due to high class imbalance; better performance with oversampling strategies

---

## 👥 Customer Segmentation

Used K-Means with PCA after VIF checks on 2,000+ users.

### Cluster Profiles:
- **Cluster 0**: Young, low-income, first-time credit users  
- **Cluster 1**: Balanced spenders with stable financial patterns  
- **Cluster 2**: Affluent, lifestyle-oriented, high credit use  
- **Cluster 3**: High-limit, digitally active power spenders  
- **Cluster 4**: Older, risk-averse, financially conservative

---

## 🤖 Recommendation System (NCF)

Trained a **Neural Collaborative Filtering** model on user–card interaction pairs.  

**Architecture**:  
- Embedding(Users, Cards) → FC(128→64→32) → Sigmoid Output  

### Metrics:
| Metric      | Score  |
|-------------|--------|
| ROC-AUC     | 0.9411 |
| Precision@K | 0.9100 |
| Hit@10      | 0.9639 |
| NDCG@10     | 0.3567 |

---

## 📌 Example Output

**User 913 (Cluster 4)**:
1. Chase Sapphire Reserve – 0.9269  
2. Marriott Bonvoy Business – 0.9222  
3. Amex Business Platinum – 0.9055  

---

## 🧾 Conclusion

- GNN enhanced fraud detection by leveraging graph structures  
- Customer segmentation yielded 5 behavior-driven profiles  
- NCF provided tailored card suggestions per cluster

---

## 🚧 Limitations

- GNN scalability for massive datasets  
- Cold start in recommendations  
- Static clustering lacks user evolution tracking

---

## 🔮 Future Scope

- Time-aware GNNs and hybrid recommenders  
- Mobile-first deployment  
- Expansion into other domains (POS fraud, digital wallets, BNPL)
