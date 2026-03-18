MD Tutorials: LAMMPS for Polymeric Materials
==============================================

Step-by-Step Guides for Polymer Simulations with LAMMPS
-------------------------------------------------------

Essential LAMMPS Workflow for Polymers
---------------------------------------

**Goal**: Run a complete polymer simulation from setup to analysis

**Prerequisites**
   - LAMMPS installed
   - Basic familiarity with terminal/command line
   - Understanding of your polymer system (monomer structure, chain length, etc.)


LAMMPS Polyethylene (PE) Chain Simulation
-------------------------------------------

**Goal**: Run a realistic polymer simulation - a single polyethylene chain

**Step 1: Create Initial Structure with Moltemplate**

Create a data file for a linear polyethylene chain (in.molecules):

.. code-block:: bash

   import "forcefield.lt"

   CH2 {
     write_once("Data Atoms") {
       $atom:c $mol:. @atom:CH2 0 0 0 0
       $atom:h1 $mol:. @atom:H 0 0.109 0.0 0.0
       $atom:h2 $mol:. @atom:H 0 -0.0545 0.0946 0.0
       $atom:h3 $mol:. @atom:H 0 -0.0545 -0.0946 0.0
     }
   }

   # Build a chain of CH2 units
   chain = new CH2 [20]

Run moltemplate to generate LAMMPS data file:

.. code-block:: bash

   moltemplate.sh -atomstyle full in.molecules

**Step 2: LAMMPS Energy Minimization Script (in.minimize)**

.. code-block:: bash

   # Energy Minimization for Polyethylene

   units           real
   atom_style      full
   pair_style      lj/cut/coul/long 10.0
   pair_modify     tail yes
   kspace_style    pppm 1.0e-4

   read_data       system.data

   # Define force field if not in data file
   bond_style      harmonic
   angle_style     harmonic
   dihedral_style  opls

   thermo          100
   thermo_style    custom step pe lx ly lz press pxx pyy pzz
   dump            min_dump all atom 100 min_dump.lammpstrj

   minimize        1.0e-4 1.0e-6 1000 10000

   write_data      minimized.data

Run minimization:

.. code-block:: bash

   lammps < in.minimize

**Step 3: NVT Equilibration Script (in.nvt)**

.. code-block:: bash

   # NVT Equilibration

   units           real
   atom_style      full

   read_data       minimized.data

   pair_style      lj/cut/coul/long 10.0
   pair_modify     tail yes
   kspace_style    pppm 1.0e-4

   bond_style      harmonic
   angle_style     harmonic
   dihedral_style  opls

   # Thermostat: Langevin at 300K
   fix             1 all langevin 300 300 100 123456
   fix             2 all nve

   thermo          100
   thermo_style    custom step pe ke etotal temp vol
   dump            nvt_dump all atom 100 nvt_dump.lammpstrj

   timestep        1.0
   run             10000

   write_data      equilibrated_nvt.data

Run NVT equilibration:

.. code-block:: bash

   lammps < in.nvt

**Step 4: NPT Equilibration Script (in.npt)**

.. code-block:: bash

   # NPT Equilibration for pressure control

   units           real
   atom_style      full

   read_data       equilibrated_nvt.data

   pair_style      lj/cut/coul/long 10.0
   pair_modify     tail yes
   kspace_style    pppm 1.0e-4

   bond_style      harmonic
   angle_style     harmonic
   dihedral_style  opls

   # Barostat + thermostat
   fix             1 all npt temp 300 300 100 iso 1.0 1.0 1000

   thermo          100
   thermo_style    custom step pe ke etotal temp press vol
   dump            npt_dump all atom 100 npt_dump.lammpstrj

   timestep        1.0
   run             20000

   write_data      equilibrated_npt.data

Run NPT equilibration:

.. code-block:: bash

   lammps < in.npt

**Step 5: Production Run Script (in.production)**

.. code-block:: bash

   # Production Run - Collect Data

   units           real
   atom_style      full

   read_data       equilibrated_npt.data

   pair_style      lj/cut/coul/long 10.0
   pair_modify     tail yes
   kspace_style    pppm 1.0e-4

   bond_style      harmonic
   angle_style     harmonic
   dihedral_style  opls

   # NVT production run
   fix             1 all langevin 300 300 100 654321
   fix             2 all nve

   # Compute gyration radius (chain conformation)
   compute         gyr all gyration

   thermo          100
   thermo_style    custom step pe ke etotal temp c_gyr
   dump            prod_dump all atom 100 prod_dump.lammpstrj

   timestep        1.0
   run             100000

Run production:

.. code-block:: bash

   lammps < in.production > log.lammps


Polymer Trajectory Analysis with Python
-----------------------------------------

**Goal**: Extract polymer properties from simulation data

**Analysis Script (analyze_polymer.py)**

.. code-block:: python

   import MDAnalysis as mda
   import numpy as np
   import matplotlib.pyplot as plt

   # Load trajectory
   u = mda.Universe("prod_dump.lammpstrj", atom_style="id type x y z")

   # Calculate radius of gyration
   polymer = u.select_atoms("all")
   rg_data = []

   for ts in u.trajectory:
       com = polymer.center_of_mass()
       positions = polymer.positions - com
       rg = np.sqrt(np.sum(positions**2) / len(polymer))
       rg_data.append(rg)

   # Calculate end-to-end distance
   end_to_end = []
   for ts in u.trajectory:
       r_ee = np.linalg.norm(u.atoms[0].position - u.atoms[-1].position)
       end_to_end.append(r_ee)

   # Plot results
   fig, (ax1, ax2) = plt.subplots(2, 1, figsize=(8, 6))

   ax1.plot(rg_data)
   ax1.set_ylabel("Radius of Gyration (Å)")
   ax1.set_xlabel("Frame")

   ax2.plot(end_to_end)
   ax2.set_ylabel("End-to-End Distance (Å)")
   ax2.set_xlabel("Frame")

   plt.tight_layout()
   plt.savefig("polymer_analysis.png")

   # Print statistics
   print(f"Average Rg: {np.mean(rg_data):.3f} ± {np.std(rg_data):.3f} Å")
   print(f"Average R_ee: {np.mean(end_to_end):.3f} ± {np.std(end_to_end):.3f} Å")

Run analysis:

.. code-block:: bash

   python analyze_polymer.py


LAMMPS Input File Templates for Polymers
------------------------------------------

Common starting templates available in group repository:

- ``in.minimize`` - Energy minimization template
- ``in.nvt`` - NVT equilibration template
- ``in.npt`` - NPT equilibration template
- ``in.production`` - Production run template

Contact group leads to access or create custom templates for your specific polymer system.

**Tips for Creating Polymer Systems**

- Use Moltemplate for complex polymers
- GAFF or OPLS-AA force fields work well for organic polymers
- Always check your data file format matches atom_style
- Test minimization and short equilibration before production runs
- Monitor energy and temperature convergence carefully


Polymer-Specific Analysis Techniques
-------------------------------------

**Basic Analysis Steps for Polymeric Materials**

1. **Conformation Analysis**
   - Radius of gyration (Rg) - measure chain size
   - End-to-end distance (R_ee) - polymer extension
   - Asphericity - chain shape anisotropy

2. **Chain Dynamics**
   - Mean-square displacement (MSD) - diffusion
   - Bond autocorrelation - bond rotation dynamics
   - Dihedral angle distributions - rotational states

3. **Mechanical Properties**
   - Stress-strain relationships
   - Elastic modulus from stress fluctuations
   - Viscosity from Green-Kubo relations

4. **Structural Properties**
   - Density profiles
   - Radial distribution functions (RDF)
   - Entanglement identification

5. **Visualization & Validation**
   - Visual inspection with OVITO or VMD
   - Check for unwanted crossings or artifacts
   - Verify force field parameters applied correctly


Common Issues in Polymer Simulations
-------------------------------------

- **Polymer chains crossing through each other**: Check nonbonded cutoff distances, may need to increase box size or use dummy atoms to prevent interpenetration
- **High energy during equilibration**: Check dihedral angle definitions, bond lengths, or initial structure overlaps
- **Simulation crashes after a few steps**: Timestep may be too large; reduce to 0.5-1.0 fs for polymers. Check force field parameters.
- **Energy not converging**: Minimize longer, increase equilibration time, or check for unphysical initial configurations
- **Radius of gyration oscillating wildly**: This is normal; ensure equilibration is long enough (typically 10,000-50,000 steps)

See :doc:`../troubleshooting` for more common issues and solutions.


Best Practices for Polymer Simulations
---------------------------------------

1. **Build systematically**: Use Moltemplate or Python scripts to generate complex topologies
2. **Test force field parameters**: Validate against known experimental data or literature values
3. **Start small**: Run test simulations with shorter chains or smaller systems first
4. **Document everything**: Record force field, initial structure, simulation parameters
5. **Save checkpoints**: Use LAMMPS restart files to save intermediate states
6. **Archive carefully**: Keep input files, data files, log files, and trajectories
7. **Validate results**: Compare against experimental data or other simulations
8. **Use version control**: Track changes to input scripts and analysis code


Next Steps
----------

1. Try a basic polymer simulation (start with this tutorial)
2. Adapt to your specific polymer system
3. Run longer production simulations for your research
4. Perform detailed analysis on your results
5. Share findings and scripts with the group


Questions?
----------

Ask group members or bring to group meetings: :doc:`../collaboration/meetings`
