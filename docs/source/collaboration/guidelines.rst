Research & Code Guidelines
==========================

Group Standards for Quality Research
------------------------------------


Code Standards
--------------

**Python Style Guide**

Follow PEP 8: https://pep8.org/

Key points:

- Use 4 spaces for indentation
- Max line length: 79 characters
- Use meaningful variable names
- Document complex logic

**Example**

.. code-block:: python

   """Module for analyzing MD trajectories."""

   import numpy as np
   import pandas as pd


   def calculate_rmsd(reference, trajectory):
       """
       Calculate RMSD between reference and trajectory frames.

       Parameters
       ----------
       reference : np.ndarray
           Reference coordinates (N, 3)
       trajectory : np.ndarray
           Trajectory coordinates (T, N, 3)

       Returns
       -------
       rmsd : np.ndarray
           RMSD values for each frame
       """
       # Calculate distance
       diff = trajectory - reference
       squared_diff = np.sum(diff ** 2, axis=-1)
       rmsd = np.sqrt(np.mean(squared_diff, axis=-1))

       return rmsd


**Code Review Checklist**

- [ ] Follows PEP 8 style
- [ ] Has docstrings
- [ ] Handles edge cases
- [ ] Has tests
- [ ] Comments explain why, not what
- [ ] No hardcoded values


Documentation Requirements
--------------------------

**README Files**

Every project should have a README with:

- Project description
- Installation instructions
- Quick start guide
- File descriptions
- Contact info


**Example README.md**

.. code-block:: markdown

   # Protein Trajectory Analysis

   Analysis tools for MD protein trajectories.

   ## Installation

   ```bash
   pip install -r requirements.txt
   ```

   ## Quick Start

   ```python
   from analysis import calculate_rmsd
   rmsd = calculate_rmsd(ref, traj)
   ```

   ## File Descriptions

   - `analysis.py`: Core analysis functions
   - `plotting.py`: Visualization utilities

   ## Author

   Your Name (date)


**Docstrings**

Use NumPy style for all functions:

.. code-block:: python

   def my_function(param1, param2):
       """
       Brief description.

       Longer description explaining what this does.

       Parameters
       ----------
       param1 : type
           Description of param1
       param2 : type
           Description of param2

       Returns
       -------
       result : type
           Description of result

       Examples
       --------
       >>> my_function(1, 2)
       3
       """


Version Control Practices
------------------------

**Git Workflow**

1. **Create a branch** for your feature:
   .. code-block:: bash

      git checkout -b feature/analyze-trajectories

2. **Commit regularly** with descriptive messages:
   .. code-block:: bash

      git commit -m "Add RMSD calculation function"

3. **Push to remote**:
   .. code-block:: bash

      git push origin feature/analyze-trajectories

4. **Open Pull Request** for review
5. **Address feedback** and merge


**Commit Messages**

Good commit messages:

- Start with capital letter
- Imperative mood: "Add feature" not "Added feature"
- Max 50 characters for title
- Blank line before body (if needed)
- Reference issues: "Fixes #12"

Example:
.. code-block:: text

   Add RMSD calculation for protein trajectories

   Implements RMSD calculation with both fit and no-fit options.
   Fixes issue #15.


**Branching Strategy**

- `main`: Stable, tested code
- `develop`: Integration branch
- `feature/*`: New features
- `bugfix/*`: Bug fixes
- `hotfix/*`: Urgent fixes


Testing Requirements
--------------------

**Write Tests**

Every function should have tests:

.. code-block:: python

   # test_analysis.py
   import numpy as np
   from analysis import calculate_rmsd


   def test_calculate_rmsd_identical():
       """RMSD should be zero for identical structures."""
       coords = np.zeros((10, 3))
       rmsd = calculate_rmsd(coords, coords)
       assert np.allclose(rmsd, 0)


   def test_calculate_rmsd_known():
       """Test against known RMSD value."""
       ref = np.array([[0, 0, 0]])
       traj = np.array([[[1, 0, 0]]])
       rmsd = calculate_rmsd(ref, traj)
       assert np.allclose(rmsd, np.sqrt(1/3))


**Run Tests**

.. code-block:: bash

   pytest
   pytest -v         # Verbose
   pytest --cov      # Coverage


**Continuous Integration**

Use GitHub Actions for automated testing.


Data Management
---------------

**Organize Data**

.. code-block:: text

   project/
   ├── README.md
   ├── data/
   │   ├── raw/          # Original data
   │   ├── processed/    # Cleaned/prepared
   │   └── external/     # Reference data
   ├── simulations/
   │   ├── parameters/
   │   ├── inputs/
   │   └── outputs/
   └── analysis/
       ├── scripts/
       └── results/


**Document Data**

Create `data/README.md`:

.. code-block:: markdown

   # Data Description

   ## Sources
   - trajectory.xtc: From simulation run 1 (2024-01-15)
   - protein.pdb: Downloaded from PDB (1ABC)

   ## Processing
   - Aligned to residues 10-50
   - Removed water molecules
   - Resampled to 1 ps intervals

   ## Files
   - `raw/`: Original files as downloaded
   - `processed/`: Analysis-ready data
```

Reproducibility
---------------

**Requirements**

Make sure results are reproducible:

- Pin dependency versions in `requirements.txt`
- Document random seeds
- Include all parameters
- Share preprocessed data

**Example requirements.txt**

.. code-block:: text

   numpy==1.24.3
   pandas==2.0.2
   MDAnalysis==2.4.2
   matplotlib==3.7.1


**Reproducible Notebooks**

.. code-block:: python

   # Set random seed at start
   np.random.seed(42)
   random.seed(42)
   torch.manual_seed(42)

   # Document parameters clearly
   LEARNING_RATE = 0.001
   BATCH_SIZE = 32
   NUM_EPOCHS = 100


Manuscript Preparation
----------------------

**Writing Guidelines**

- Be clear and concise
- Explain before presenting results
- Use active voice when possible
- Define notation before using
- Check grammar and style


**Figures & Tables**

- Figures should be self-contained
- Include legends and labels
- Use consistent styling
- High resolution (300+ dpi)
- Reference all figures in text


**Authorship & Attribution**

- Discuss authorship order early (don't wait until end)
- Use CRediT for clear contributions
- Cite code and data sources
- Acknowledge funding and support
- List all collaborators


**Submission Process**

1. Create GitHub branch for paper
2. Circulate draft for feedback
3. Track changes using Git
4. Export final PDF
5. Submit to journal/conference


Open Science Practices
----------------------

**Data Sharing**

- Archive code on GitHub
- Share data on Zenodo or similar
- Use open file formats
- Provide data dictionary
- Get persistent identifier (DOI)

**Pre-registration**

For new studies, consider pre-registering:

- OSF: https://osf.io/
- Specifies hypothesis before data analysis
- Improves transparency


**Open Access**

Publish in open-access journals when possible.


Code of Conduct
---------------

**Expectations**

- Treat colleagues with respect
- Provide constructive feedback
- Be open to feedback
- Credit others' work
- Professional communication


**Unacceptable Behavior**

- Harassment or discrimination
- Plagiarism
- Data fabrication
- Exclusion or isolation
- Aggressive communication


Consequences for violations in collaboration area:

- Discussion with group lead
- Written warning
- Remediation requirements
- Escalation if needed


Attribution & Citation
----------------------

**Citing Group Code/Data**

If using group member's code:

1. Cite the GitHub repository
2. Include version/commit hash
3. Mention in acknowledgments
4. Discuss publication plans


**External Attribution**

- Cite all sources you used
- Include preprints and theses
- Cite software packages
- Link to GitHub repositories


Common Issues & Solutions
------------------------

**Issue**: Code doesn't work on colleague's computer

- Solution: Check dependencies and versions
- Include requirements.txt
- Test on multiple systems
- Provide setup instructions


**Issue**: Data files are too large

- Solution: Use Git LFS for large files
- Store on shared server/cloud
- Reference rather than include
- Provide download script


**Issue**: Conflicting edits to shared files

- Solution: Use branches in Git
- Set up Git merge strategy
- Use discussion before merging
- Consider naming conventions


Questions?
----------

- Ask group members
- Bring concerns to group leads
- See related pages: :doc:`index`
