ML Tools & Frameworks
====================

Popular Machine Learning Libraries
-----------------------------------


Python Ecosystem
----------------

**scikit-learn**

   **Overview**
      General-purpose ML library with classical algorithms.

   **Strengths**
      - Easy to use
      - Excellent documentation
      - Good for tabular data
      - Consistent API

   **What it includes**
      - Regression & Classification
      - Clustering
      - Dimensionality reduction
      - Model selection tools

   **Install**
      ``pip install scikit-learn``

   **Best for**
      Starting with ML, classical algorithms, smaller datasets


**TensorFlow & Keras**

   **Overview**
      Deep learning framework by Google. Keras is high-level API.

   **Strengths**
      - Production-ready
      - Good community support
      - Mobile/edge deployment
      - Extensive documentation

   **What it includes**
      - Neural networks
      - Convolutional networks
      - Recurrent networks
      - Pre-trained models

   **Install**
      ``pip install tensorflow``

   **Best for**
      Production systems, deep learning, large-scale projects


**PyTorch**

   **Overview**
      Deep learning framework by Meta. Research-friendly.

   **Strengths**
      - Dynamic computation graph
      - Easier debugging
      - Strong research community
      - Clean syntax

   **What it includes**
      - Neural networks
      - Vision models
      - NLP models
      - Transformers (via transformers library)

   **Install**
      ``pip install torch``

   **Best for**
      Research, experimentation, cutting-edge methods


**XGBoost & LightGBM**

   **Overview**
      Gradient boosting libraries. State-of-the-art for tabular data.

   **Strengths**
      - Best performance on tabular data
      - Fast training
      - Feature importance
      - Handles mixed data types

   **XGBoost Install**
      ``pip install xgboost``

   **LightGBM Install**
      ``pip install lightgbm``

   **Best for**
      Tabular data prediction, Kaggle-style competitions


**Pandas & NumPy**

   **Overview**
      Data manipulation and numerical computing.

   **Essential for**
      - Data loading and preprocessing
      - Feature engineering
      - Exploratory analysis
      - Data visualization

   **Install**
      ``pip install pandas numpy``


Specialized Libraries
---------------------

**Matplotlib & Seaborn**

   Data visualization libraries.

   - ``pip install matplotlib seaborn``
   - Essential for exploratory analysis


**Scikit-Optimize**

   Hyperparameter optimization.

   - ``pip install scikit-optimize``
   - Bayesian optimization for hyperparameters


**Optuna**

   Modern hyperparameter optimization.

   - ``pip install optuna``
   - Efficient hyperparameter search


**MDAnalysis**

   Analyze MD trajectories.

   - ``pip install MDAnalysis``
   - Perfect integration with ML workflows


**RDKit**

   Chemistry toolkit for molecular analysis.

   - ``conda install -c conda-forge rdkit``
   - Molecular representations for ML models


ML Workflows & Pipelines
------------------------

**Creating a Pipeline**

.. code-block:: python

   from sklearn.pipeline import Pipeline
   from sklearn.preprocessing import StandardScaler
   from sklearn.ensemble import RandomForestRegressor

   # Create pipeline
   pipeline = Pipeline([
       ('scaler', StandardScaler()),
       ('model', RandomForestRegressor())
   ])

   # Train
   pipeline.fit(X_train, y_train)

   # Predict
   y_pred = pipeline.predict(X_test)


**Hyperparameter Search**

.. code-block:: python

   from sklearn.model_selection import GridSearchCV

   param_grid = {
       'model__n_estimators': [100, 200, 300],
       'model__max_depth': [5, 10, 15]
   }

   grid = GridSearchCV(pipeline, param_grid, cv=5)
   grid.fit(X_train, y_train)


**Cross-Validation**

.. code-block:: python

   from sklearn.model_selection import cross_val_score

   scores = cross_val_score(model, X, y, cv=5)
   print(f"Mean accuracy: {scores.mean()}")


Jupyter Notebooks for ML
------------------------

Recommended for:

- Interactive exploration
- Prototyping models
- Sharing results

Installation: ``pip install jupyter``

Usage: ``jupyter notebook``


Production Deployment
---------------------

Tools for deploying models:

- **FastAPI**: Create REST APIs for models
- **Docker**: Containerize ML applications
- **Flask/Django**: Web framework integration
- **TensorFlow Serving**: Production TF models
- **MLflow**: Model tracking and deployment


Model Management
----------------

**Saving & Loading Models**

.. code-block:: python

   # Scikit-learn
   import joblib
   joblib.dump(model, 'model.pkl')
   model = joblib.load('model.pkl')

   # PyTorch
   torch.save(model.state_dict(), 'model.pth')
   model.load_state_dict(torch.load('model.pth'))


**Version Control**

- Git for code versioning
- MLflow for experiment tracking
- DVC for data/model versioning


Getting Started
---------------

1. **Install Python**: 3.8+ recommended
2. **Create virtual environment**: ``python -m venv ml_env``
3. **Install core tools**: ``pip install numpy pandas scikit-learn matplotlib jupyter``
4. **Try tutorials and examples**
5. **Pick a project to work on**


Setup for Group
---------------

See :doc:`../resources/software` for system-wide setup.

Individual setup: Follow the installation instructions above.


Best Practices
--------------

- Use virtual environments
- Document dependencies in requirements.txt
- Version your code
- Track experiments
- Use Jupyter for exploration, .py files for production


Questions?
----------

See :doc:`../troubleshooting` or ask group members.
