ML Fundamentals
===============

Core Machine Learning Concepts
-------------------------------

**Machine Learning Definition**

Machine Learning is a branch of artificial intelligence that enables systems to learn and improve from experience without being explicitly programmed. It finds patterns in data and uses them to make predictions.


Three Types of ML
-----------------

**Supervised Learning**
   Learning from labeled data. The algorithm learns input-output relationships.

   - Regression: Predicting continuous values
   - Classification: Predicting discrete categories
   - Example: Predicting protein binding affinity from structure

**Unsupervised Learning**
   Learning from unlabeled data. The algorithm finds hidden patterns.

   - Clustering: Grouping similar data points
   - Dimensionality Reduction: Finding lower-dimensional representations
   - Example: Clustering protein conformations from MD simulations

**Reinforcement Learning**
   Learning through interaction. The algorithm learns optimal actions through rewards.

   - Example: Optimizing molecular structures through iterative design


Key Concepts
------------

**Training Set**
   Data used to train the model. Must be representative of the problem.

**Test Set**
   Data used to evaluate model performance. Must be separate from training data.

**Validation Set**
   Data used to tune hyperparameters during training.

**Overfitting**
   Model learns noise rather than true patterns. Generalizes poorly to new data.

**Underfitting**
   Model is too simple to capture true patterns. Poor performance on both training and test data.

**Hyperparameters**
   Parameters set before training (learning rate, activation functions, etc.)

**Feature Engineering**
   Creating meaningful input features from raw data. Critical for model performance.


Model Evaluation Metrics
------------------------

**Regression Metrics**

- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- R-squared (R²)

**Classification Metrics**

- Accuracy
- Precision & Recall
- F1-Score
- ROC-AUC


Common ML Algorithms
--------------------

**Linear Models**

- Linear Regression
- Logistic Regression
- Good for simple, interpretable models

**Tree-Based Models**

- Decision Trees
- Random Forests
- Gradient Boosting
- Good for non-linear relationships

**Neural Networks**

- Multilayer Perceptrons (MLPs)
- Convolutional Neural Networks (CNNs)
- Recurrent Neural Networks (RNNs)
- Good for complex patterns

**Kernel Methods**

- Support Vector Machines (SVMs)
- Good for classification

**Clustering**

- K-means
- Hierarchical Clustering
- DBSCAN


Data Preparation Steps
----------------------

1. **Data Collection**: Gather relevant data
2. **Data Cleaning**: Handle missing values, outliers
3. **Feature Engineering**: Create meaningful features
4. **Normalization**: Scale features appropriately
5. **Train-Test Split**: Separate data for evaluation
6. **Class Balancing** (if needed): Handle imbalanced datasets


Workflow
--------

1. **Problem Definition**: What are you trying to predict?
2. **Data Preparation**: Clean and prepare data
3. **Exploratory Analysis**: Understand data patterns
4. **Model Selection**: Choose appropriate algorithm
5. **Training**: Fit model to training data
6. **Validation**: Tune hyperparameters
7. **Testing**: Evaluate on holdout test set
8. **Deployment**: Use model for predictions
9. **Monitoring**: Track performance over time


Cross-Validation
----------------

Technique to better estimate model generalization:

- K-Fold Cross-Validation: Split data into k folds
- Leave-One-Out: Each sample is test set once
- Time Series Split: For ordered data

Helps prevent overfitting and makes better use of limited data.


Bias-Variance Tradeoff
-----------------------

- **High Bias**: Underfitting, overly simple model
- **High Variance**: Overfitting, too complex model
- **Goal**: Find balance with best generalization


Key Principles
--------------

1. **Start Simple**: Begin with simple models, add complexity if needed
2. **Validate Properly**: Always use separate test data
3. **Understanding Data is Critical**: Exploratory analysis saves time
4. **Feature Engineering Matters**: Often more important than algorithm choice
5. **Iterate**: ML is iterative; expect multiple refinements


Common Pitfalls
---------------

- Using same data for training and testing
- Not scaling features appropriately
- Ignoring class imbalance
- Over-complicated models for simple problems
- Not validating results thoroughly
- Cherry-picking results


Next Steps
----------

- Choose a specific ML algorithm: :doc:`methods`
- Learn the tools: :doc:`tools`
- Try tutorials and examples
- Apply to group research


Questions?
----------

See :doc:`../troubleshooting` or ask experienced group members.
