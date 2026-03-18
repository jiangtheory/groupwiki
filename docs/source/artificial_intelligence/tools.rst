AI Tools & Platforms
====================

AI Frameworks & Libraries
-------------------------

See :doc:`../machine_learning/tools` for core ML tools that are foundation for AI.

Additional AI-specific tools:


Natural Language Processing
---------------------------

**Hugging Face Transformers**

   **Overview**
      Pre-trained transformer models and tools.

   **Features**
      - BERT, GPT, T5, and many others
      - Easy fine-tuning
      - Downstream task support

   **Install**
      ``pip install transformers``

   **Use for**
      NLP tasks, text generation, semantic analysis


**spaCy**

   **Overview**
      Industrial-strength NLP library.

   **Features**
      - Named entity recognition
      - Dependency parsing
      - Text classification
      - Trained pipelines

   **Install**
      ``pip install spacy``

   **Use for**
      Information extraction, text processing


**NLTK**

   **Overview**
      Natural Language Toolkit for NLP research.

   **Features**
      - Tokenization
      - POS tagging
      - Parsing
      - Semantic analysis

   **Install**
      ``pip install nltk``

   **Use for**
      NLP education and research


Computer Vision
---------------

**OpenCV**

   **Overview**
      Open-source computer vision library.

   **Features**
      - Image processing
      - Feature detection
      - Video analysis
      - Machine learning integration

   **Install**
      ``pip install opencv-python``

   **Use for**
      Image analysis, real-time processing


**Pillow**

   **Overview**
      Python Imaging Library for image manipulation.

   **Features**
      - Image loading and saving
      - Basic transformations
      - Filters and effects

   **Install**
      ``pip install Pillow``

   **Use for**
      Image preprocessing


**torchvision & timm**

   **Overview**
      Vision utilities for PyTorch.

   **Features**
      - Pre-trained models
      - Vision datasets
      - Transforms and utilities
      - Image classification, detection, segmentation

   **Install**
      ``pip install torchvision timm``

   **Use for**
      Computer vision deep learning


Reinforcement Learning
----------------------

**OpenAI Gym**

   **Overview**
      Toolkit for reinforcement learning.

   **Features**
      - Standard RL environments
      - Benchmark environments
      - Extensible interface

   **Install**
      ``pip install gymnasium``

   **Use for**
      RL research and development


**Stable Baselines3**

   **Overview**
      Implementations of RL algorithms.

   **Features**
      - DQN, PPO, SAC, etc.
      - Easy-to-use interface
      - Good documentation

   **Install**
      ``pip install stable-baselines3``

   **Use for**
      RL applications


Knowledge Graphs & Reasoning
----------------------------

**Rdflib**

   **Overview**
      Work with RDF and semantic web data.

   **Features**
      - Query and manipulate RDF
      - OWL support
      - SPARQL queries

   **Install**
      ``pip install rdflib``

   **Use for**
      Knowledge representation, reasoning


**Neo4j**

   **Overview**
      Graph database platform.

   **Features**
      - Store knowledge graphs
      - Graph algorithms
      - Query language (Cypher)

   **Install**
      Cloud or local instance (not pip)

   **Use for**
      Large-scale knowledge graphs


AI-Specific Platforms
---------------------

**Fast.ai**

   **Overview**
      Practical deep learning library and courses.

   **Strengths**
      - High-level abstraction
      - Great for practitioners
      - Excellent documentation

   **Install**
      ``pip install fastai``


**JAX**

   **Overview**
      Composable functional programming for arrays.

   **Strengths**
      - AutoDiff and primitives
      - GPU acceleration
      - Functional paradigm

   **Install**
      ``pip install jax jaxlib``


**Ray**

   **Overview**
      Distributed computing framework.

   **Use cases**
      - Hyperparameter tuning (Tune)
      - Reinforcement learning (RLlib)
      - Data processing


Experiment Tracking & Management
--------------------------------

**Weights & Biases (W&B)**

   **Overview**
      ML experiment tracking platform.

   **Features**
      - Log metrics and hyperparameters
      - Hyperparameter sweeps
      - Team collaboration

   **Install**
      ``pip install wandb``


**MLflow**

   **Overview**
      Open-source ML lifecycle platform.

   **Features**
      - Experiment tracking
      - Model versioning
      - Model serving

   **Install**
      ``pip install mlflow``


**Neptune.ai**

   **Overview**
      Experiment management platform.

   **Features**
      - Lightweight logging
      - Rich dashboards
      - Team collaboration


Model Deployment
----------------

**FastAPI**

   **Overview**
      Modern web framework for APIs.

   **Use for**
      Serving ML models as REST APIs

   **Install**
      ``pip install fastapi uvicorn``


**Streamlit**

   **Overview**
      Create interactive data apps.

   **Use for**
      Quick demos and interactive analysis

   **Install**
      ``pip install streamlit``


**TensorFlow Serving**

   **Overview**
      Production serving for TensorFlow models.

   **Use for**
      High-performance model serving


Data Processing & Workflows
----------------------------

**Dask**

   **Overview**
      Parallel computing for large datasets.

   **Features**
      - Lazy evaluation
      - Parallel operations
      - Easy scaling

   **Install**
      ``pip install dask[dataframe]``


**Apache Spark**

   **Overview**
      Distributed data processing.

   **Use for**
      Large-scale data processing


**Airflow**

   **Overview**
      Workflow orchestration platform.

   **Use for**
      Complex data pipelines


Specialized AI Libraries
------------------------

**Chemistry & Molecules**

- **RDKit**: Cheminformatics toolkit
- **DeepChem**: Deep learning for drug discovery
- **AlphaFold**: Protein structure prediction
- **ESMFold**: Fast protein structure prediction

**Materials Science**

- **Pymatgen**: Materials analysis
- **ASE**: Atomic Simulation Environment
- **OVITO**: Visualization and analysis

**Hardware Acceleration**

- **CUDA/cuDNN**: NVIDIA GPU computing
- **ROCm**: AMD GPU computing
- **TPU**: Google's tensor processing units


Choosing Your AI Stack
----------------------

**For Beginners**
   - PyTorch or TensorFlow
   - scikit-learn for traditional ML
   - Jupyter for exploration

**For NLP**
   - Hugging Face Transformers
   - PyTorch or TensorFlow
   - spaCy for preprocessing

**For Computer Vision**
   - PyTorch with timm
   - OpenCV for preprocessing
   - torchvision for utilities

**For Research**
   - PyTorch (more flexible)
   - JAX (advanced research)
   - Rapid prototyping with Jupyter


Setup Recommendations
---------------------

See :doc:`../resources/software` for system-wide setup


Best Practices
--------------

1. Start with libraries well-suited to your domain
2. Use established frameworks over untested tools
3. Keep dependencies manageable
4. Document your stack
5. Test with known problems first


Questions?
----------

Ask group members or see tutorials: :doc:`resources`
