# 📱 Megaline Mobile Plan Recommendation

## 📌 Project Overview

**Client:** Megaline, a mobile carrier  
**Goal:** Develop a machine learning model that classifies subscribers into one of two mobile plans — **Smart** or **Ultra** — based on monthly usage behavior.

This classification model will help Megaline target users still on legacy plans and recommend the most suitable new plan for them.

---

## 🗂️ Dataset Description

**File:** `datasets/users_behavior.csv`  
Each row contains usage statistics for a single subscriber in a given month:

| Feature     | Description                                 |
|-------------|---------------------------------------------|
| `calls`     | Number of phone calls                       |
| `minutes`   | Total call duration (in minutes)            |
| `messages`  | Number of text messages sent                |
| `mb_used`   | Internet data used (in megabytes)           |
| `is_ultra`  | Target variable: `1` for Ultra, `0` for Smart |

---

## 🧪 Project Workflow

### 1. Data Exploration

- Loaded the dataset and verified data types
- Checked for missing or anomalous values
- Visualized feature distributions for both plan types

### 2. Data Splitting

- Split dataset into:
  - **Training set (60%)**
  - **Validation set (20%)**
  - **Test set (20%)**
- Ensured stratification to preserve target distribution

### 3. Model Building & Evaluation

Tested several classification algorithms:

| Model            | Key Hyperparameters Explored              |
|------------------|-------------------------------------------|
| Decision Tree    | max_depth, min_samples_split              |
| Random Forest    | n_estimators, max_depth                   |
| Logistic Regression | C (regularization), solver           |

**Metrics Used:** Accuracy (target threshold ≥ 0.75)

### 4. Hyperparameter Tuning

- Used GridSearchCV and manual iteration to find optimal parameters
- Compared validation accuracy across models

### 5. Final Testing

- Evaluated the best model on the **test set**
- Reported **final accuracy score**
- Performed a **sanity check** using baseline accuracy (majority class model)

---

## 🧠 Key Findings

- **Internet usage (`mb_used`)** and **call duration (`minutes`)** are the most influential features.
- **Random Forest** achieved the best performance:
  - ✅ Accuracy > 0.75 on the test set
- Smart plan users tend to use fewer minutes and MBs, while Ultra plan users have heavier usage patterns.

---

## 🛠️ Tools & Libraries

- `pandas`, `numpy`: Data manipulation
- `scikit-learn`: Modeling, splitting, metrics
- `matplotlib`, `seaborn`: Visualization

---

## 📊 Accuracy Report

| Model               | Validation Accuracy | Test Accuracy |
|---------------------|---------------------|---------------|
| Logistic Regression | 0.72                | 0.71          |
| Decision Tree       | 0.75                | 0.74          |
| ✅ Random Forest     | **0.79**            | **0.78**      |
