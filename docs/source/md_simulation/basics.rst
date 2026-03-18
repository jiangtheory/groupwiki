MD Basics: Polymeric Materials
==============================

Fundamentals of Molecular Dynamics Simulation for Polymers
-----------------------------------------------------------

**What is Molecular Dynamics?**

Molecular Dynamics is a simulation technique that computes the trajectories of particles (atoms or molecules) by integrating Newton's equations of motion. For polymeric materials, MD allows us to observe chain conformations, dynamics, and properties at the atomic scale.


Key Concepts
------------

**Force Fields**
   Mathematical representations of how atoms interact. For polymers they define:

   - Bond stretching potential (harmonic or Morse)
   - Angle bending potential
   - Dihedral angles (torsion) - critical for polymer structure
   - Non-bonded interactions (van der Waals, electrostatic)

   Common force fields for polymers: OPLS-AA, GAFF, AMBER, TraPPE

**Ensemble Types**

- **NVE (Microcanonical)**: Constant Number, Volume, Energy
- **NVT (Canonical)**: Constant Number, Volume, Temperature
- **NPT (Isothermal-Isobaric)**: Constant Number, Pressure, Temperature

**Time Integration**

The most common method is the Verlet algorithm (and variants):

- Leapfrog integrator
- Velocity Verlet
- Time step typically 1-2 femtoseconds


Basic Workflow for Polymer Simulations
--------------------------------------

1. **System Preparation**
   - Build polymer chain or network structure
   - Define topology and force field parameters
   - Add solvent (if studying solution) or periodic boundaries (if bulk)
   - Set initial coordinates and velocities

2. **Minimization**
   - Remove steric clashes in polymer structure
   - Relax overlapping chains
   - Steepest descent or conjugate gradient methods

3. **Equilibration**
   - Gradually heat system to target temperature
   - Allow polymer chains to relax and sample conformations
   - Temperature and pressure equilibration
   - Achieve constant properties

4. **Production Run**
   - Collect trajectory data for analysis
   - Monitor chain conformations and dynamics
   - Output positions and velocities for analysis


Important Parameters
--------------------

- **Time Step**: Controls integration accuracy (1-2 fs typical)
- **Cut-off Distances**: Determines how far interactions are calculated
- **Temperature**: Controlled via thermostat (Langevin, Berendsen, Bussi)
- **Pressure**: Controlled via barostat (Parrinello-Rahman, Berendsen)
- **Simulation Length**: Needed for equilibration and averaging


Common Pitfalls
---------------

- Time step too large → simulation becomes unstable
- Insufficient equilibration → biased results
- Poor force field choice for system → incorrect behavior
- Cutting off electrostatics abruptly → artifacts
- Not checking convergence of properties

See :doc:`../troubleshooting` for solutions.


Energy Minimization with LAMMPS
--------------------------------

Before running MD, we minimize energy in LAMMPS. Example input file (in.minimize):

.. code-block:: bash

   # Minimization
   minimize         1.0e-4 1.0e-6 1000 10000
   thermo           100
   thermo_style     custom step pe lx ly lz press pxx pyy pzz
   dump             minDump all atom 100 min_dump.lammpstrj


Equilibration with LAMMPS
--------------------------

Typical equilibration protocol in LAMMPS (in.equilibrate):

1. NVT equilibration (constant temperature, free volume adjustment)
2. NPT equilibration (allow pressure/volume equilibration)
3. Extended equilibration for polymer chain relaxation

.. code-block:: bash

   # Set up thermostat and barostat
   fix              1 all nvt temp 300 300 100
   # or for pressure control:
   fix              2 all npt temp 300 300 100 iso 1.0 1.0 1000


Next Steps
----------

- See :doc:`tools` for software-specific instructions
- See :doc:`tutorials` for practical examples
- Read the papers in :doc:`resources`


Further Reading
---------------

- LAMMPS documentation: https://lammps.sandia.gov/
- Polymer simulation reviews: See :doc:`../resources/reading_list`
- LAMMPS tutorials for polymers: Available on LAMMPS website
