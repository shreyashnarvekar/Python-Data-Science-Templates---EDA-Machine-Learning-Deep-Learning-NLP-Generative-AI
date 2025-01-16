# GRID SEARCH CV WITH ML MODELS SYNTAX CHEATSHEET
> **REGRESSION & CLASSIFICATION** 

> **HYPERPARAMETER TUNING**

> **CROSS VALIDATION**

> **BEST PARAMETERS**

> **PERFORMANCE METRICS - (MODEL EVALUATION)**

<br>

---

> ## &#8595; &nbsp; **1. REGRESSION WITH GRID SEARCH CV &nbsp; &#8595;** 

---

## 1.1 Import Libraries
```python
from sklearn.model_selection import GridSearchCV
from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score
from sklearn.linear_model import LinearRegression
from sklearn.ensemble import RandomForestRegressor
from sklearn.tree import DecisionTreeRegressor
from sklearn.svm import SVR
from xgboost import XGBRegressor
from lightgbm import LGBMRegressor
```

---
### 1.2 Initialize models

```python
model_lr = LinearRegression()
model_rf = RandomForestRegressor(random_state=42)
model_dt = DecisionTreeRegressor(random_state=42)
model_svr = SVR()
model_xgb = XGBRegressor(random_state=42)
model_lgbm = LGBMRegressor(random_state=42)
```

---

### 1.3 Define hyperparameter grid for GridSearchCV
```python
param_grid_lr = {
    'fit_intercept': [True, False],
    'normalize': [True, False]
}
param_grid_rf = {
    'n_estimators': [50, 100, 200],
    'max_depth': [10, 20, 30],
    'random_state': [42]
}
param_grid_dt = {
    'max_depth': [10, 20, 30],
    'min_samples_split': [2, 5, 10],
    'random_state': [42]
}
param_grid_svr = {
    'C': [1, 10, 100],
    'kernel': ['linear', 'poly', 'rbf'],
    'gamma': ['scale', 'auto']
}
param_grid_xgb = {
    'n_estimators': [50, 100, 200],
    'learning_rate': [0.01, 0.1, 0.2],
    'max_depth': [3, 5, 7]
}
param_grid_lgbm = {
    'n_estimators': [50, 100, 200],
    'learning_rate': [0.01, 0.1, 0.2],
    'num_leaves': [31, 50, 100]
}
```

---

### 1.4 Grid Search with Cross Validation for each model

```python
grid_search_lr = GridSearchCV(estimator=model_lr, param_grid=param_grid_lr, cv=5, n_jobs=-1, scoring='neg_mean_squared_error')
grid_search_rf = GridSearchCV(estimator=model_rf, param_grid=param_grid_rf, cv=5, n_jobs=-1, scoring='neg_mean_squared_error')
grid_search_dt = GridSearchCV(estimator=model_dt, param_grid=param_grid_dt, cv=5, n_jobs=-1, scoring='neg_mean_squared_error')
grid_search_svr = GridSearchCV(estimator=model_svr, param_grid=param_grid_svr, cv=5, n_jobs=-1, scoring='neg_mean_squared_error')
grid_search_xgb = GridSearchCV(estimator=model_xgb, param_grid=param_grid_xgb, cv=5, n_jobs=-1, scoring='neg_mean_squared_error')
grid_search_lgbm = GridSearchCV(estimator=model_lgbm, param_grid=param_grid_lgbm, cv=5, n_jobs=-1, scoring='neg_mean_squared_error')
```

---

### 1.5 Train models using Grid Search

```python
grid_search_lr.fit(X_train, y_train)
grid_search_rf.fit(X_train, y_train)
grid_search_dt.fit(X_train, y_train)
grid_search_svr.fit(X_train, y_train)
grid_search_xgb.fit(X_train, y_train)
grid_search_lgbm.fit(X_train, y_train)
```

---

### 1.6 Get best model from Grid Search
```python
best_model_lr = grid_search_lr.best_estimator_
best_model_rf = grid_search_rf.best_estimator_
best_model_dt = grid_search_dt.best_estimator_
best_model_svr = grid_search_svr.best_estimator_
best_model_xgb = grid_search_xgb.best_estimator_
best_model_lgbm = grid_search_lgbm.best_estimator_
```

---

### 1.7 Predictions

```python
y_pred_lr = best_model_lr.predict(X_test)
y_pred_rf = best_model_rf.predict(X_test)
y_pred_dt = best_model_dt.predict(X_test)
y_pred_svr = best_model_svr.predict(X_test)
y_pred_xgb = best_model_xgb.predict(X_test)
y_pred_lgbm = best_model_lgbm.predict(X_test)
```

---

### 1.8 Performance Metrics (using MSE, RMSE, MAE, and R²) - Model Evaluation

```python
# Linear Regression - Evaluation
mse_lr = mean_squared_error(y_test, y_pred_lr)
rmse_lr = np.sqrt(mse_lr)
mae_lr = mean_absolute_error(y_test, y_pred_lr)
r2_lr = r2_score(y_test, y_pred_lr)

# Random Forest Regressor - Evaluation
mse_rf = mean_squared_error(y_test, y_pred_rf)
rmse_rf = np.sqrt(mse_rf)
mae_rf = mean_absolute_error(y_test, y_pred_rf)
r2_rf = r2_score(y_test, y_pred_rf)

# Decision Tree Regressor - Evaluation
mse_dt = mean_squared_error(y_test, y_pred_dt)
rmse_dt = np.sqrt(mse_dt)
mae_dt = mean_absolute_error(y_test, y_pred_dt)
r2_dt = r2_score(y_test, y_pred_dt)

# Support Vector Regressor (SVR) - Evaluation
mse_svr = mean_squared_error(y_test, y_pred_svr)
rmse_svr = np.sqrt(mse_svr)
mae_svr = mean_absolute_error(y_test, y_pred_svr)
r2_svr = r2_score(y_test, y_pred_svr)

# XGBoost Regressor - Evaluation
mse_xgb = mean_squared_error(y_test, y_pred_xgb)
rmse_xgb = np.sqrt(mse_xgb)
mae_xgb = mean_absolute_error(y_test, y_pred_xgb)
r2_xgb = r2_score(y_test, y_pred_xgb)

# LightGBM Regressor - Evaluation
mse_lgbm = mean_squared_error(y_test, y_pred_lgbm)
rmse_lgbm = np.sqrt(mse_lgbm)
mae_lgbm = mean_absolute_error(y_test, y_pred_lgbm)
r2_lgbm = r2_score(y_test, y_pred_lgbm)
```

---

### 1.9 Print evaluation results with MSE, RMSE, MAE, and R²
```python
print(f"Linear Regression - MSE: {mse_lr}, RMSE: {rmse_lr}, MAE: {mae_lr}, R2: {r2_lr}")
print(f"Random Forest - MSE: {mse_rf}, RMSE: {rmse_rf}, MAE: {mae_rf}, R2: {r2_rf}")
print(f"Decision Tree - MSE: {mse_dt}, RMSE: {rmse_dt}, MAE: {mae_dt}, R2: {r2_dt}")
print(f"SVR - MSE: {mse_svr}, RMSE: {rmse_svr}, MAE: {mae_svr}, R2: {r2_svr}")
print(f"XGBoost - MSE: {mse_xgb}, RMSE: {rmse_xgb}, MAE: {mae_xgb}, R2: {r2_xgb}")
print(f"LightGBM - MSE: {mse_lgbm}, RMSE: {rmse_lgbm}, MAE: {mae_lgbm}, R2: {r2_lgbm}")
```

<br>

---

## **&#8595; &nbsp; 2. CLASSIFICATION WITH GRID SEARCH CV &nbsp; &#8595;** 

---

## 2.1 Import Libraries
```python
from sklearn.model_selection import GridSearchCV
from sklearn.metrics import accuracy_score, confusion_matrix, classification_report, roc_auc_score
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.svm import SVC
from xgboost import XGBClassifier
from lightgbm import LGBMClassifier
```

---
### 2.2 Initialize models

```python
model_lr = LogisticRegression(random_state=42)
model_rf = RandomForestClassifier(random_state=42)
model_dt = DecisionTreeClassifier(random_state=42)
model_svc = SVC(probability=True, random_state=42)
model_xgb = XGBClassifier(random_state=42)
model_lgbm = LGBMClassifier(random_state=42)
```

---

### 2.3 Define hyperparameter grid for GridSearchCV
```python
param_grid_lr = {
    'C': [0.01, 0.1, 1, 10],
    'solver': ['liblinear', 'saga'],
    'max_iter': [100, 200]
}
param_grid_rf = {
    'n_estimators': [50, 100, 200],
    'max_depth': [10, 20, 30],
    'random_state': [42]
}
param_grid_dt = {
    'max_depth': [10, 20, 30],
    'min_samples_split': [2, 5, 10],
    'random_state': [42]
}
param_grid_svc = {
    'C': [1, 10, 100],
    'kernel': ['linear', 'poly', 'rbf'],
    'gamma': ['scale', 'auto']
}
param_grid_xgb = {
    'n_estimators': [50, 100, 200],
    'learning_rate': [0.01, 0.1, 0.2],
    'max_depth': [3, 5, 7]
}
param_grid_lgbm = {
    'n_estimators': [50, 100, 200],
    'learning_rate': [0.01, 0.1, 0.2],
    'num_leaves': [31, 50, 100]
}
```

---

### 2.4 Grid Search with Cross Validation for each model

```python
grid_search_lr = GridSearchCV(estimator=model_lr, param_grid=param_grid_lr, cv=5, n_jobs=-1, scoring='accuracy')
grid_search_rf = GridSearchCV(estimator=model_rf, param_grid=param_grid_rf, cv=5, n_jobs=-1, scoring='accuracy')
grid_search_dt = GridSearchCV(estimator=model_dt, param_grid=param_grid_dt, cv=5, n_jobs=-1, scoring='accuracy')
grid_search_svc = GridSearchCV(estimator=model_svc, param_grid=param_grid_svc, cv=5, n_jobs=-1, scoring='accuracy')
grid_search_xgb = GridSearchCV(estimator=model_xgb, param_grid=param_grid_xgb, cv=5, n_jobs=-1, scoring='accuracy')
grid_search_lgbm = GridSearchCV(estimator=model_lgbm, param_grid=param_grid_lgbm, cv=5, n_jobs=-1, scoring='accuracy')
```

---

### 2.5 Train models using Grid Search

```python
grid_search_lr.fit(X_train, y_train)
grid_search_rf.fit(X_train, y_train)
grid_search_dt.fit(X_train, y_train)
grid_search_svc.fit(X_train, y_train)
grid_search_xgb.fit(X_train, y_train)
grid_search_lgbm.fit(X_train, y_train)
```

---

### 2.6 Get best model from Grid Search
```python
best_model_lr = grid_search_lr.best_estimator_
best_model_rf = grid_search_rf.best_estimator_
best_model_dt = grid_search_dt.best_estimator_
best_model_svc = grid_search_svc.best_estimator_
best_model_xgb = grid_search_xgb.best_estimator_
best_model_lgbm = grid_search_lgbm.best_estimator_
```

---

### 2.7 Predictions

```python
y_pred_lr = best_model_lr.predict(X_test)
y_pred_rf = best_model_rf.predict(X_test)
y_pred_dt = best_model_dt.predict(X_test)
y_pred_svc = best_model_svc.predict(X_test)
y_pred_xgb = best_model_xgb.predict(X_test)
y_pred_lgbm = best_model_lgbm.predict(X_test)
```

---

### 2.8 Performance Metrics (using Accuracy, Confusion Matrix, ROC AUC) - (Model Evaluation)

```python
# Logistic Regression - Evaluation
accuracy_lr = accuracy_score(y_test, y_pred_lr)
conf_matrix_lr = confusion_matrix(y_test, y_pred_lr)
class_report_lr = classification_report(y_test, y_pred_lr)
roc_auc_lr = roc_auc_score(y_test, best_model_lr.predict_proba(X_test)[:, 1])

# Random Forest - Evaluation
accuracy_rf = accuracy_score(y_test, y_pred_rf)
conf_matrix_rf = confusion_matrix(y_test, y_pred_rf)
class_report_rf = classification_report(y_test, y_pred_rf)
roc_auc_rf = roc_auc_score(y_test, best_model_rf.predict_proba(X_test)[:, 1])

# Decision Tree - Evaluation
accuracy_dt = accuracy_score(y_test, y_pred_dt)
conf_matrix_dt = confusion_matrix(y_test, y_pred_dt)
class_report_dt = classification_report(y_test, y_pred_dt)
roc_auc_dt = roc_auc_score(y_test, best_model_dt.predict_proba(X_test)[:, 1])

# SVC - Evaluation
accuracy_svc = accuracy_score(y_test, y_pred_svc)
conf_matrix_svc = confusion_matrix(y_test, y_pred_svc)
class_report_svc = classification_report(y_test, y_pred_svc)
roc_auc_svc = roc_auc_score(y_test, best_model_svc.predict_proba(X_test)[:, 1])

# XGBoost - Evaluation
accuracy_xgb = accuracy_score(y_test, y_pred_xgb)
conf_matrix_xgb = confusion_matrix(y_test, y_pred_xgb)
class_report_xgb = classification_report(y_test, y_pred_xgb)
roc_auc_xgb = roc_auc_score(y_test, best_model_xgb.predict_proba(X_test)[:, 1])

# LightGBM - Evaluation
accuracy_lgbm = accuracy_score(y_test, y_pred_lgbm)
conf_matrix_lgbm = confusion_matrix(y_test, y_pred_lgbm)
class_report_lgbm = classification_report(y_test, y_pred_lgbm)
roc_auc_lgbm = roc_auc_score(y_test, best_model_lgbm.predict_proba(X_test)[:, 1])
```

---

### 2.9 Print evaluation results
```python
print(f"Logistic Regression: Accuracy = {accuracy_lr}, ROC AUC = {roc_auc_lr}")
print(f"Confusion Matrix:\n{conf_matrix_lr}")
print(f"Classification Report:\n{class_report_lr}")

print(f"\nRandom Forest: Accuracy = {accuracy_rf}, ROC AUC = {roc_auc_rf}")
print(f"Confusion Matrix:\n{conf_matrix_rf}")
print(f"Classification Report:\n{class_report_rf}")

print(f"\nDecision Tree: Accuracy = {accuracy_dt}, ROC AUC = {roc_auc_dt}")
print(f"Confusion Matrix:\n{conf_matrix_dt}")
print(f"Classification Report:\n{class_report_dt}")

print(f"\nSVC: Accuracy = {accuracy_svc}, ROC AUC = {roc_auc_svc}")
print(f"Confusion Matrix:\n{conf_matrix_svc}")
print(f"Classification Report:\n{class_report_svc}")

print(f"\nXGBoost: Accuracy = {accuracy_xgb}, ROC AUC = {roc_auc_xgb}")
print(f"Confusion Matrix:\n{conf_matrix_xgb}")
print(f"Classification Report:\n{class_report_xgb}")

print(f"\nLightGBM: Accuracy = {accuracy_lgbm}, ROC AUC = {roc_auc_lgbm}")
print(f"Confusion Matrix:\n{conf_matrix_lgbm}")
print(f"Classification Report:\n{class_report_lgbm}")
```

---