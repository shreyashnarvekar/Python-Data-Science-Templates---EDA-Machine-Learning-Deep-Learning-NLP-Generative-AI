# ML MODELS SYNTAX CHEATSHEET
> **REGRESSION & CLASSIFICATION** 

> **PERFORMANCE METRICS - (MODEL EVALUATION)**

> **SAVE & LOAD MODEL**

> ***CLICK HERE*** &nbsp; 👉 &nbsp;<u>[**MODEL WITH GRID SEARCH CV**](https://github.com/shreyashnarvekar/Python-Data-Science-Templates---EDA-Machine-Learning-Deep-Learning-NLP-Generative-AI/tree/main/00%20Syntax%20Cheatsheet/06%20ML%20Models/Grid%20Search%20CV/)</u>


<br>

---

> ## &#8595; &nbsp; **1. REGRESSION &nbsp; &#8595;** 

---
## 1.1 Model Initialization, Training and Prediction

### Linear Regression
```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

### Support Vector Regressor (SVR)
```python
from sklearn.svm import SVR

model = SVR(kernel='linear')
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```


### Decision Tree Regressor
```python
from sklearn.tree import DecisionTreeRegressor

model = DecisionTreeRegressor(random_state=42)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

### Random Forest Regressor
```python
from sklearn.ensemble import RandomForestRegressor

model = RandomForestRegressor(n_estimators=100, random_state=42)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```


### XGBoost Regressor
```python
from xgboost import XGBRegressor

model = XGBRegressor(n_estimators=100, learning_rate=0.1, random_state=42)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)

```

### LightGBM Regressor
```python
from lightgbm import LGBMRegressor

model = LinearRegression()
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

---

## **1.2 Regression Performance Metrics - (Model Evaluation)**

### Mean Squared Error (MSE)
```python
from sklearn.metrics import mean_squared_error

mse = mean_squared_error(y_test, y_pred)
print("Mean Squared Error (MSE):", mse)
```

### Root Mean Squared Error (RMSE)
```python
import numpy
from sklearn.metrics import mean_squared_error

rmse = np.sqrt(mse)
print("Root Mean Squared Error (RMSE):", rmse)
```

### Mean Absolute Error (MAE)
```python
from sklearn.metrics import mean_absolute_error

mae = mean_absolute_error(y_test, y_pred)
print("Mean Absolute Error (MAE):", mae)
```

### R-squared Score
```python
from sklearn.metrics import r2_score

r2 = r2_score(y_test, y_pred)
print("R-squared Score (R2):", r2)
```

---

## 1.3 Save and Load Model

```python
import joblib

joblib.dump(model, 'regression_model.pkl')
loaded_model = joblib.load('regression_model.pkl')
y_pred = loaded_model.predict(X_test)
```

<br>

---

> ## &#8595; &nbsp; **2. CLASSIFICATION &nbsp; &#8595;** 

---
## 2.1 Model Initialization, Training and Prediction

### Logistic Regression
```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression()
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

### Support Vector Classifier (SVC)
```python
from sklearn.svm import SVC

model = SVC(kernel='linear')
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```


### Decision Tree Classifier
```python
from sklearn.tree import DecisionTreeClassifier

model = DecisionTreeClassifier(random_state=42)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

### Random Forest Classifier
```python
from sklearn.ensemble import RandomForestClassifier

model = RandomForestRegressor(n_estimators=100, random_state=42)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```


### XGBoost Classifier
```python
from xgboost import XGBClassifier

model = XGBClassifier(n_estimators=100, learning_rate=0.1, random_state=42)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)

```

### LightGBM Classifier
```python
from lightgbm import LGBMClassifier

model = LGBMClassifier(n_estimators=100, learning_rate=0.1, random_state=42)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

---

## **2.2 Classifier Performance Metrics - (Model Evaluation)**

### Accuracy Score
```python
rom sklearn.metrics import accuracy_score

accuracy = accuracy_score(y_test, y_pred)
print(accuracy)
```

### Confusion Matrix
```python
from sklearn.metrics import confusion_matrix

conf_matrix = confusion_matrix(y_test, y_pred)
print(conf_matrix)
```

### Classification Report
```python
from sklearn.metrics import classification_report

class_report = classification_report(y_test, y_pred)
print(class_report)
```

### ROC AUC Score (Area Under the Curve for ROC)
```python
from sklearn.metrics import roc_auc_score

roc_auc = roc_auc_score(y_test, model.predict_proba(X_test)[:, 1])  # For binary classification
print(roc_auc)
```

---

## 2.3 Save and Load Model

```python
import joblib

joblib.dump(model, 'classification_model.pkl')
loaded_model = joblib.load('classification_model.pkl')
y_pred = loaded_model.predict(X_test)
```

---
