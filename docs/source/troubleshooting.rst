Troubleshooting & FAQ
====================

Common Issues & Solutions
-------------------------


Python & Installation Issues
-----------------------------

**Python not found**

Error: `python: command not found`

Solutions:

1. Check if Python is installed: ``which python3``
2. Install Python from https://www.python.org/
3. On macOS: ``brew install python@3.11``
4. On Linux: ``sudo apt-get install python3``

Use ``python3`` instead of ``python`` if both are available.


**pip install fails**

Error: `ModuleNotFoundError` or `pip: command not found`

Solutions:

1. Upgrade pip: ``pip install --upgrade pip``
2. Use: ``python -m pip install package_name``
3. Check virtual environment is activated
4. Try conda instead: ``conda install package_name``


**Virtual environment issues**

Can't activate virtual environment:

.. code-block:: bash

   # Recreate it
   python -m venv myenv
   source myenv/bin/activate  # macOS/Linux
   # or
   myenv\Scripts\activate     # Windows


**CUDA/GPU not working**

Error: `cuda not available` or GPU not detected

Solutions:

1. Check drivers: ``nvidia-smi``
2. Install CUDA Toolkit properly
3. Reinstall PyTorch with correct CUDA version:
   ``pip install torch --index-url https://download.pytorch.org/whl/cu118``


Molecular Dynamics Issues
--------------------------

**GROMACS not found**

Error: `gmx: command not found`

Solutions:

1. Check if installed: ``which gmx``
2. Load module: ``module load gromacs``
3. Add to PATH if needed
4. Check installation: ``gmx --version``


**Simulation crashes - out of memory**

Error: Memory allocation failed during mdrun

Solutions:

1. Reduce system size
2. Increase number of processors
3. Reduce precision (single vs double)
4. Check membrane/solvent parameters
5. Use implicit solvent instead of explicit


**Simulation crashes - floating point error**

Error: `inf` or `nan` in energies

Solutions:

1. **Time step too large**: Reduce dt (try 0.001 ps)
2. **Charges unbalanced**: Check ion concentration
3. **Starting structure poor**: Run minimization longer
4. **Force field mismatch**: Verify topology correct
5. **Constraints too tight**: Check LINCS warning

Solution:
.. code-block:: bash

   gmx grompp -f minim.mdp -c structure.gro -p topol.top -o minim.tpr
   gmx mdrun -deffnm minim -v


**Trajectory analysis: Too slow**

Tips for faster analysis:

1. Use selection strings efficiently
2. Slice trajectory: ``start=-1000`` (last 1000 frames)
3. Stride frames: ``step=10`` (every 10th frame)
4. Use compiled code (C/Cython) if available


Machine Learning Issues
------------------------

**Model training is slow**

Solutions:

1. **Check GPU usage**: Is GPU actually being used?
   ``nvidia-smi`` or ``torch.cuda.is_available()``
2. **Batch size too small**: Increase batch size
3. **Model too complex**: Reduce layers/parameters
4. **Data loading slow**: Prefetch and cache data
5. **CPU-GPU transfer bottleneck**: Check data pipeline


**Model overfitting**

Symptoms: Training loss decreases but validation loss increases

Solutions:

1. **Add regularization**: L1/L2 regularization
2. **Dropout**: Randomly zero units during training
3. **Reduce model complexity**: Fewer parameters
4. **More training data**: Collect more examples
5. **Data augmentation**: Artificially expand data
6. **Early stopping**: Stop when val loss stops improving


**Validation accuracy low**

Debugging steps:

1. **Check data**: Is training data representative?
2. **Verify preprocessing**: Same scaling/transforms?
3. **Class imbalance**: Are classes balanced?
4. **Check labels**: Are they correct?
5. **Try simpler model**: Check if problem is solvable
6. **Check hyperparameters**: Learning rate, batch size


**NaN or Inf during training**

Solutions:

1. **Learning rate too high**: Reduce by 10x
2. **Poor initialization**: Try different seed
3. **Data contains NaN**: Check data cleaning
4. **Exploding gradients**: Add gradient clipping
5. **Batch normalization**: Can help stabilize


Data & File Issues
------------------

**File format errors**

Error when loading trajectory/data:

Solutions:

1. Check file format: ``file myfile.xtc``
2. Verify format matches loader
3. Convert if needed (e.g., GRO ↔ PDB)
4. Check if file is corrupted
5. Try reading different format


**Out of disk space**

Error: `No space left on device`

Solutions:

1. Check usage: ``df -h`` or ``du -sh *``
2. Compress old files: ``gzip old_file.txt``
3. Delete temporary files
4. Archive to long-term storage
5. Request more storage


**File permissions denied**

Error: `Permission denied`

Solutions:

.. code-block:: bash

   # Check permissions
   ls -l filename

   # Make readable
   chmod +r filename

   # Make executable
   chmod +x script.sh

   # Fix current directory
   chmod u+rwx .


Data Analysis Issues
--------------------

**Pandas/NumPy memory error**

Error loading or processing large data:

Solutions:

1. **Read in chunks**: ``pd.read_csv(..., chunksize=10000)``
2. **Use data types**: Specify dtypes to reduce memory
3. **Filter data**: Only read columns you need
4. **Use Dask**: For larger-than-RAM datasets
5. **Use sparse matrices**: If data is sparse


**Plotting not working**

No plot displayed in script:

Solutions:

.. code-block:: python

   # In scripts, add:
   import matplotlib.pyplot as plt
   plt.show()

   # Or in Jupyter, enable inline plotting:
   %matplotlib inline

   # Check backend
   import matplotlib
   print(matplotlib.get_backend())


Git & Version Control Issues
----------------------------

**Merge conflicts**

When pulling/merging from team:

Solutions:

1. **View conflicts**: Lines between `<<<<<<<` and `>>>>>>>`
2. **Resolve**: Keep yours, theirs, or combine
3. **Mark resolved**: ``git add filename``
4. **Complete merge**: ``git commit -m "Merge..."`

.. code-block:: bash

   # View conflicts
   git diff --name-only --diff-filter=U

   # Use their version
   git checkout --theirs filename

   # Use your version
   git checkout --ours filename


**Accidentally committed sensitive file**

Solution - **Don't push yet**:

.. code-block:: bash

   # Remove from last commit
   git rm --cached sensitive_file.txt
   echo "sensitive_file.txt" >> .gitignore
   git add .gitignore
   git commit --amend --no-edit


**Want to undo commits**

Before pushing:

.. code-block:: bash

   # View history
   git log --oneline

   # Undo last commit (keep changes)
   git reset --soft HEAD~1

   # Undo last commit (discard changes)
   git reset --hard HEAD~1


Communication & Collaboration Issues
-------------------------------------

**Can't clone/access GitHub repo**

Error: `Permission denied`

Solutions:

1. **Check SSH keys**: ``ssh -T git@github.com``
2. **Generate new keys**: See :doc:`collaboration/tools`
3. **Check write access**: Ask repo owner
4. **Try HTTPS**: ``git clone https://github.com/...``


**Merge request feedback**

How to handle:

1. **Make changes** locally
2. **Commit and push** same branch
3. **Changes appear** in PR automatically
4. **Request re-review** when ready


Computing & Cluster Issues
--------------------------

**Job stuck in queue**

Solutions:

1. Check queue: ``squeue -u $USER``
2. Try different partition: Smaller jobs run faster
3. Reduce time/resource requests
4. Contact admin if still stuck


**Can't connect to cluster**

Error: `Connection refused` or timeout

Solutions:

1. Check network: ``ping cluster.institution.edu``
2. Check credentials
3. Use correct username
4. Contact IT if problem persists


**Module not found**

Error: `module: command not found`

Solutions:

1. Initialize module system: Check cluster docs
2. Load modules manually: ``source /module/path``
3. Try: ``module loa gromacs`` (typo example)
4. See available: ``module avail``


**Compilation fails**

Error during make/compile:

Solutions:

1. **Load correct modules**: Check README
2. **Check dependencies**: May need to install first
3. **Try different compiler**: ``module load gcc``
4. **Check for errors**: Read full error message
5. **Simplify**: Test on smaller example


Questions Not Covered Here?
----------------------------

**Where to ask**

1. Group Slack #help channel
2. Stack Overflow (for general programming)
3. Official documentation
4. Ask experienced group members
5. Email group leads


**Debugging Strategy**

1. **Read error message carefully**: Usually very informative
2. **Search online**: Often someone had same problem
3. **Minimal example**: Reproduce with simplest case
4. **Systematic**: Change one thing at a time
5. **Document**: Save solution to help others


**When asking for help**

Provide:

- Full error message
- Code snippet that causes issue
- Your system info: Python version, OS, etc.
- What you've tried already
- Minimal reproducible example


Related Resources
-----------------

- General help: See :doc:`../collaboration/tools` for Slack
- Software docs: See :doc:`../resources/software`
- Computing help: See :doc:`../resources/computing`
- Research help: See group leads


Error Messages Reference
------------------------

| Error | Likely cause | Solution |
|-------|-------------|----------|
| `ModuleNotFoundError` | Package not installed | `pip install package_name` |
| `ImportError` | Wrong Python/env | Activate correct environment |
| `MemoryError` | Not enough RAM | Reduce data size, use chunks |
| `FileNotFoundError` | Wrong path | Check file location |
| `PermissionDenied` | File permissions | `chmod +x file` or check access |
| `ConnectionError` | Network issue | Check connection, restart |
| `KeyError` | Dictionary key missing | Check key name spelling |
| `IndexError` | Array index out bounds | Check array size, indexing |


Quick Reference
---------------

Common solutions:

- Installation problem? → Reinstall in clean venv
- GPU not working? → ``nvidia-smi`` first
- No output? → Check you calling print/plt.show()
- Super slow? → Check hardware (GPU active?)
- Weird behavior? → Check random seed
- Collaboration issue? → Ask first, fix second
