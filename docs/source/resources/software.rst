Software Installation & Setup
=============================

Complete Guide to Setting Up Your Development Environment
----------------------------------------------------------


System Requirements
-------------------

**Operating System**

- Linux (recommended for HPC clusters)
- macOS
- Windows (with WSL2 recommended)


**Minimum Hardware**

- CPU: Modern multi-core processor
- RAM: 16 GB (32 GB recommended)
- Storage: 500 GB free space
- **For GPU work**: NVIDIA GPU with CUDA support


**Base Software**

- Python 3.8 or higher
- Git
- C/C++ compiler


Core Python Installation
------------------------

**1. Install Python**

macOS (using Homebrew):
.. code-block:: bash

   brew install python@3.11

Linux (Ubuntu/Debian):
.. code-block:: bash

   sudo apt-get install python3.11 python3.11-venv

Windows:
   Download from https://www.python.org/downloads/


**2. Create Virtual Environment**

.. code-block:: bash

   python3 -m venv ml_research
   source ml_research/bin/activate  # macOS/Linux
   # or
   ml_research\Scripts\activate  # Windows


**3. Update pip**

.. code-block:: bash

   pip install --upgrade pip setuptools wheel


MD Simulation Software
----------------------

**GROMACS**

Installation (macOS):
.. code-block:: bash

   brew install gromacs

Installation (Linux):
.. code-block:: bash

   sudo apt-get install gromacs

Or download from: https://manual.gromacs.org/


**LAMMPS**

Installation:
.. code-block:: bash

   conda install -c conda-forge lammps

Or build from source: https://lammps.sandia.gov/


**AMBER**

Contact group leads for academic license and installation assistance.


**OpenMM**

.. code-block:: bash

   pip install openmm


Scientific Python Stack
-----------------------

**Essential Libraries**

.. code-block:: bash

   pip install numpy pandas scipy matplotlib jupyter


**Data Science & ML**

.. code-block:: bash

   pip install scikit-learn xgboost lightgbm


**Deep Learning**

TensorFlow:
.. code-block:: bash

   pip install tensorflow

PyTorch (CPU):
.. code-block:: bash

   pip install torch torchvision

PyTorch (GPU - CUDA 11.8):
.. code-block:: bash

   pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118


**NLP & Vision**

.. code-block:: bash

   pip install transformers opencv-python


**Analysis & Visualization**

.. code-block:: bash

   pip install seaborn plotly


Bioscience Tools
----------------

**MDAnalysis**

.. code-block:: bash

   pip install MDAnalysis

**RDKit** (Cheminformatics)

.. code-block:: bash

   conda install -c conda-forge rdkit

**BioPython**

.. code-block:: bash

   pip install biopython


Development Tools
-----------------

**Git**

Installation:
.. code-block:: bash

   # macOS
   brew install git
   # Linux
   sudo apt-get install git

Configuration:
.. code-block:: bash

   git config --global user.name "Your Name"
   git config --global user.email "your.email@institution.edu"


**Code Editors**

- **VS Code**: https://code.visualstudio.com/
- **PyCharm**: https://www.jetbrains.com/pycharm/
- **Sublime Text**: https://www.sublimetext.com/


**Jupyter Notebook**

.. code-block:: bash

   pip install jupyter jupyterlab

Launch:
.. code-block:: bash

   jupyter notebook


**Pre-commit Hooks**

.. code-block:: bash

   pip install pre-commit


Conda Environment Files
-----------------------

**Create requirements.txt**

.. code-block:: bash

   pip freeze > requirements.txt

**Create environment.yml** (recommended for conda):

.. code-block:: yaml

   name: ml_research
   channels:
     - conda-forge
     - pytorch
   dependencies:
     - python=3.11
     - numpy
     - pandas
     - scipy
     - matplotlib
     - jupyter
     - scikit-learn
     - pytorch::pytorch
     - pytorch::pytorch-cuda=11.8
     - pytorch::torchvision
     - pytorch::torchaudio
     - openmm
     - mdanalysis

**Install environment:**

.. code-block:: bash

   conda env create -f environment.yml
   conda activate ml_research


GPU Support
-----------

**For NVIDIA GPUs**

1. Install CUDA Toolkit: https://developer.nvidia.com/cuda-downloads
2. Install cuDNN: https://developer.nvidia.com/cudnn
3. Test with PyTorch:

.. code-block:: python

   import torch
   print(torch.cuda.is_available())
   print(torch.cuda.get_device_name(0))


Group-Specific Tools
--------------------

TBD - Add any group-specific software here


Docker Installation
-------------------

For reproducible environments:

.. code-block:: bash

   # macOS/Windows
   Download from https://www.docker.com/products/docker-desktop

   # Linux
   sudo apt-get install docker.io


Troubleshooting
---------------

**Package Installation Fails**

- Update pip: ``pip install --upgrade pip``
- Try conda instead: ``conda install package-name``
- Check Python version compatibility

**CUDA/GPU Issues**

- Verify NVIDIA drivers: ``nvidia-smi``
- Check CUDA version compatibility
- Reinstall PyTorch with correct CUDA version

**Import Errors**

- Verify correct environment is activated
- Check package is installed: ``pip list``
- Try uninstall and reinstall


Verification Checklist
----------------------

□ Python 3.8+ installed and working
□ Virtual environment created
□ pip/conda working correctly
□ NumPy and scientific stack installed
□ Jupyter notebook working
□ Git installed and configured
□ MD software (GROMACS/LAMMPS) installed
□ PyTorch/TensorFlow functional
□ GPU support verified (if applicable)


Quick Setup Script
------------------

Create ``setup.sh`` to automate setup:

.. code-block:: bash

   #!/bin/bash
   python3 -m venv ml_research
   source ml_research/bin/activate
   pip install --upgrade pip
   pip install numpy pandas scipy matplotlib jupyter
   pip install scikit-learn xgboost
   pip install torch torchvision torchaudio
   pip install transformers opencv-python
   pip install MDAnalysis
   echo "Setup complete! Activate with: source ml_research/bin/activate"


System-Wide Setup
------------------

For lab workstations, contact system administrators:

- Multi-user environment setup
- Shared software repositories
- HPC cluster configuration

See :doc:`computing` for cluster-specific setup


Keeping Software Updated
------------------------

**Update pip packages**

.. code-block:: bash

   pip install --upgrade package-name

**Update all packages**

.. code-block:: bash

   pip list --outdated
   pip install --upgrade -r requirements.txt


Questions & Support
-------------------

- See :doc:`../troubleshooting` for common issues
- Ask group members
- Check package documentation
- Post on Stack Overflow for common errors
