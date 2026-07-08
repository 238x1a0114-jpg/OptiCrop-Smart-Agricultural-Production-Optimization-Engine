# Model Evaluation and Saving the Best Model

## Model Evaluation

The Logistic Regression model was evaluated using the following metrics:

- Accuracy
- Precision
- Recall
- F1-Score
- Confusion Matrix

### Python Code

```python
from sklearn.metrics import classification_report, confusion_matrix, accuracy_score
import pickle

y_pred = model.predict(X_test)

print(classification_report(y_test, y_pred))
print(confusion_matrix(y_test, y_pred))
print("Accuracy:", accuracy_score(y_test, y_pred))

with open("model.pkl", "wb") as file:
    pickle.dump(model, file)

print("Best model saved successfully!")
```

## Result

The Logistic Regression model achieved high accuracy and was selected as the best-performing model. The trained model was saved as `model.pkl` for deployment in the Flask application.
