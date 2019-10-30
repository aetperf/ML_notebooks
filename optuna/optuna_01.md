# Optuna


## Installation

```bash
$ conda install -y pandas matplotlib jupyterlab
$ conda install -y sklearn xgboost
$ pip install optuna
```

## Imports

```python
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split, RepeatedKFold
from sklearn.metrics import mean_absolute_error
from xgboost import XGBRegressor
import optuna

RS = 124  # random state
```

## Train-test split

Suppose that you have a clean dataframe `df` ready to perform a regression. Labels are located in the `target` column. First we start by splitting the dataset:

```python
X, y = df.drop('target', axis='columns'), df.target
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.33, random_state=RS, shuffle=True)
```

## Objective function

```python
def objective(trial, X_train, y_train, random_state=13, n_splits=4, n_repeats=2, n_jobs=1):

    param = {
        'silent': 1,
        'objective': 'reg:squarederror',
        'booster': 'gbtree',
        'tree_method': 'auto',
        'random_state': random_state,
        'n_jobs': n_jobs,
        'max_delta_step': 0,  # [0,∞]
        'lambda': trial.suggest_loguniform('lambda', 1e-8, 1.0),  # reg_lambda
        'alpha': trial.suggest_loguniform('alpha', 1e-8, 1.0),  # reg_alpha
        'max_depth': trial.suggest_int('max_depth', 1, 50),  # [0,∞] 
        'n_estimators': trial.suggest_int('n_estimators', 5, 500),
        'learning_rate': trial.suggest_loguniform('learning_rate', 1e-8, 1.0),  # eta [0,1]
        'min_split_loss': trial.suggest_loguniform('min_split_loss', 1e-8, 1e2),  # gamma [0,∞]
        'min_child_weight': trial.suggest_loguniform('min_child_weight', 1e-8, 1e2),  # [0,∞]
        'subsample': trial.suggest_loguniform('subsample', 1e-8, 1.0),  # (0,1]
        'colsample_bytree': trial.suggest_loguniform('colsample_bytree', 1e-8, 1.0),  # (0, 1]
    }

    rkf = RepeatedKFold(n_splits, n_repeats, random_state)
    X, y = X_train.values, y_train.values

    mae = []
    for train_index, test_index in rkf.split(X):
        X_tr, X_te = X[train_index, :], X[test_index, :]
        y_tr, y_te = y[train_index], y[test_index]
        model = XGBRegressor(**param)
        model.fit(X_tr, y_tr)
        y_pr = model.predict(X_te)
        mae.append(mean_absolute_error(y_te, y_pr))
    return np.mean(mae)
```

## Optimization

```python
study = optuna.create_study(direction='minimize')
study.optimize(lambda trial: objective(trial, X_train, y_train, RS, 4, 2, 8), n_trials=100)
```

```python
print(study.best_params)
```
{'lambda': 0.08114273206725574, 'alpha': 2.4514986506320294e-08, 'max_depth': 41, 'n_estimators': 474, 'learning_rate': 0.20393744904739788, 'min_split_loss': 0.12357278295663555, 'min_child_weight': 5.278711556327162, 'subsample': 0.6269243888545352, 'colsample_bytree': 0.6948974426994208}

```python
print(study.best_value)
```
1.1739429493099292


```python
trials = study_eta.trials_dataframe()
```

```python
reg = XGBRegressor(
    'objective': 'reg:squarederror',
    'booster': 'gbtree',
    'tree_method': 'auto',
    'random_state': RS,
    'n_jobs': 8,
    'max_delta_step': 0, 
    **study.best_params)
reg.fit(X_train, y_train)
y_pred = reg.predict(X_test)
mean_absolute_error(y_test, y_pred)
```