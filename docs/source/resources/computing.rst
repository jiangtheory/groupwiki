Computing Resources
====================

Hardware & Infrastructure
-------------------------

**Local Workstations**

Contact system administrators for:

- Access and login credentials
- Installed software versions
- Storage quotas
- GPU availability
- Network connectivity


**HPC Clusters**

Access information for computing clusters:

- **Cluster Name**: TBD
- **Administrator**: TBD
- **Scheduler**: TBD (SLURM, PBS, LSF)
- **Node Types**: TBD
- **GPU Resources**: TBD
- **Storage**: TBD


Account Setup
-------------

**Getting Cluster Access**

1. Contact group leads
2. Request account from system administrators
3. Receive credentials and documentation
4. Set up SSH keys for secure login
5. Complete any required training


**First Login**

.. code-block:: bash

   ssh username@cluster.institution.edu
   # Set up your home directory
   mkdir -p ~/projects ~/data ~/scratch


Storage Organization
--------------------

**Typical Storage Structure**

.. code-block:: text

   Home (~):           Limited storage, configuration files
   Projects:          Code and scripts
   Data:              Simulation inputs and outputs
   Scratch:           Temporary files, fast I/O
   Archive:           Long-term storage


**Best Practices**

- **Home directory**: Only essential files, config
- **Project space**: Code, documentation
- **Scratch**: Temporary simulation files (cleaned regularly)
- **Archive**: Important results before scratch cleanup


Job Scheduling
--------------

**SLURM (Common on HPC)**

View jobs:
.. code-block:: bash

   squeue  # Show running/queued jobs
   squeue -u $USER  # Your jobs

Submit job:
.. code-block:: bash

   sbatch script.sh

Cancel job:
.. code-block:: bash

   scancel job_id


**Sample SLURM Script**

.. code-block:: bash

   #!/bin/bash
   #SBATCH --job-name=md_sim
   #SBATCH --nodes=1
   #SBATCH --ntasks=8
   #SBATCH --cpus-per-task=1
   #SBATCH --mem=32G
   #SBATCH --time=24:00:00
   #SBATCH --output=md_sim_%j.log
   #SBATCH --partition=gpu
   #SBATCH --gres=gpu:1

   module load gromacs
   module load cuda

   gmx mdrun -deffnm production -v -hrex


**PBS/Torque**

Submit:
.. code-block:: bash

   qsub script.pbs

Check jobs:
.. code-block:: bash

   qstat


GPU Access
----------

**Check GPU Availability**

.. code-block:: bash

   sinfo -o "%N %G"  # SLURM
   nvidia-smi         # On GPU nodes


**Requesting GPUs**

SLURM:
.. code-block:: bash

   #SBATCH --gres=gpu:4  # Request 4 GPUs


Queue Information
-----------------

TBD - Add queue information:

- Queue names and limits
- Time limits
- Priority rules
- Wait times (typical)
- Idle time policies


Storage Quotas
--------------

Check your quotas:

.. code-block:: bash

   quota -s
   # or
   lfs quota -hu $USER /path


Typical limits:
- Home: 100 GB
- Project: 1-10 TB
- Scratch: 10-100 TB (temporary)
- Archive: Unlimited (slower access)


Performance Tuning
------------------

**CPU Options**

.. code-block:: bash

   #SBATCH --ntasks=16           # For MPI
   #SBATCH --cpus-per-task=2     # For OpenMP


**Memory Options**

.. code-block:: bash

   #SBATCH --mem=64G             # Total memory
   #SBATCH --mem-per-cpu=4G      # Per task


**Time Requests**

.. code-block:: bash

   #SBATCH --time=24:00:00       # 24 hours
   #SBATCH --time=7-00:00:00     # 7 days


Data Transfer
-------------

**Moving Data To/From Cluster**

.. code-block:: bash

   # Copy to cluster
   scp -r local_path username@cluster:remote_path

   # Copy from cluster
   scp -r username@cluster:remote_path local_path

   # Recursive directory
   scp -r directory/ username@cluster:~/


Fast Transfers:

.. code-block:: bash

   rsync -avz --progress local/ username@cluster:remote/


Module System
-------------

**Load Software**

.. code-block:: bash

   # List available modules
   module avail

   # Load module
   module load gromacs/2024

   # List loaded modules
   module list

   # Unload module
   module unload gromacs


Monitoring Jobs
---------------

**Check Job Status**

.. code-block:: bash

   squeue -u $USER
   sacct -u $USER  # Completed jobs


**Monitor Running Job**

On the compute node:
.. code-block:: bash

   top        # CPU and memory
   nvidia-smi # GPU usage
   htop       # System load


**Log Files**

.. code-block:: bash

   # View end of output (while running)
   tail -f output.log

   # Search logs
   grep "error" output.log


Common Issues
-------------

**Out of Memory**

- Request more RAM: ``--mem=64G``
- Reduce simulation size
- Check memory-intensive operations

**Time Limit Exceeded**

- Increase time: ``--time=48:00:00``
- Optimize code/parameters
- Use checkpointing


**GPU Not Available**

- Check availability: ``sinfo -G``
- Lower priority queue/time
- Use CPU if possible
- Wait for queue


Software Environment
--------------------

**Installing Personal Packages**

.. code-block:: bash

   # Virtual environment
   python -m venv my_env
   source my_env/bin/activate
   pip install package_name

   # Conda
   conda create -n myenv python=3.11
   conda activate myenv
   conda install package_name


**Module Conflicts**

Some modules conflict. Unload before loading others:

.. code-block:: bash

   module unload intel
   module load gcc


Backup & Archiving
------------------

**Important Results**

- Archive regularly to safe storage
- Don't rely on scratch (gets cleaned)
- Document what you archive
- Use descriptive naming


Scratch Cleanup Policy
----------------------

Typical policies:

- Files older than 30-90 days deleted
- Automatic cleanup
- No recovery possible

**Always backup important results!**


Support & Troubleshooting
--------------------------

**HPC Support**

- System administrator: TBD
- Email: TBD
- Office hours: TBD
- Help documentation: TBD

**Cluster Wiki/Documentation**

TBD - Link to cluster-specific documentation


Building & Compiling
--------------------

**Load Compiler**

.. code-block:: bash

   module load gcc  # or intel

**Compile Code**

.. code-block:: bash

   gcc -O3 program.c -o program


**Parallel Compiling**

.. code-block:: bash

   mpicc parallel.c -o parallel


SSH Keys for Easier Access
---------------------------

Generate key:

.. code-block:: bash

   ssh-keygen -t rsa -b 4096 -f ~/.ssh/cluster_key

Add to authorized_keys on cluster:

.. code-block:: bash

   ssh-copy-id -i ~/.ssh/cluster_key.pub username@cluster


Quick Reference
---------------

.. code-block:: bash

   # Check job status
   squeue -u $USER

   # Submit job
   sbatch script.sh

   # Cancel job
   scancel JOB_ID

   # Monitor job
   tail -f output.log

   # List modules
   module avail

   # Check storage
   quota -s


Questions?
----------

- Contact system administrators (see Support)
- Email group leads
- Check cluster documentation: TBD
- Ask experienced group members
