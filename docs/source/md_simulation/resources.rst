MD Resources: Polymeric Materials
==================================

Databases & Data for Polymers
------------------------------

**Polymer Databases**

- **PoLyInfo**: https://www.nims.go.jp/polyinfo/
  Comprehensive polymer materials database with experimental data

- **NIST Polymer Data**: https://www.nist.gov/
  Reference data for polymer properties

- **PubChem**: https://pubchem.ncbi.nlm.nih.gov/
  Chemical compound data, useful for small hydrocarbon monomers


**Force Field Databases & Parameters**

- **LAMMPS Potentials**: https://lammps.sandia.gov/doc/Commands_pair.html
  Available pair force field types for LAMMPS

- **OPLS-AA Force Field**: Resources for OPLS parameters for organics
  Great for organic polymers

- **TraPPE**: http://trappe.oit.umn.edu/
  Transferable Potentials for Phase Equilibria - good for polymer chains

- **GAFF (General Amber Force Field)**: Widely used for organics


Reference Papers: Polymeric Materials
--------------------------------------

**Essential Reading on Polymer MD Simulations**

- Baschnagel, J., Binder, K., Doruker, P., et al. (2000). "Simulating polymers at the atomistic and coarse-grained level." Advances in Polymer Science, 152, 41-156.

- Faller, R., Müller-Plathe, F. (2001). "Polymer Simulation: From Atomistic to Mesoscale." Trends in Polymer Science (Trends in Polymer Science), 9(12), 358-364.

- Allen, M. P., & Tildesley, D. J. (2017). "Computer Simulation of Liquids" (2nd ed.). Oxford University Press.

- Groot, R. D., & Warren, P. B. (1997). "Dissipative particle dynamics: Bridging the gap between atomistic and mesoscopic simulation." Journal of Chemical Physics, 107(11), 4423-4435.

**Specific Polymer Properties**

- Glass Transition Temperature (Tg) simulations
- Chain dynamics and reptation
- Mechanical properties and stress-strain relationships
- Polymer crystallization
- Phase separation in blends

See :doc:`../resources/reading_list` for comprehensive bibliography on polymer MD


Educational Resources
----------------------

**Online Courses**

- LAMMPS official tutorials: https://lammps.sandia.gov/doc/Tutorials.html
- LAMMPS webinars and workshops
- University computational polymer science courses
- CECAM (Centre Européen de Calcul Atomique et Moléculaire) workshops

**Video Tutorials**

- LAMMPS webinars and tutorial videos
- Polymer simulation workshops
- Molecular dynamics fundamentals courses


Computing Resources
-------------------

For large simulations:

- HPC clusters: :doc:`../resources/computing`
- GPU availability: Contact group leads
- Storage requirements: Plan ahead


Software Installation
---------------------

See :doc:`../resources/software` for installation guides for:

- **LAMMPS** (primary tool)
- Moltemplate (LAMMPS input generation)
- MDAnalysis (analysis)
- OVITO (visualization)
- Analysis tools (Python, VMD, etc.)


Cheat Sheets & Quick References
-------------------------------

**LAMMPS Common Commands for Polymer Simulations**

.. code-block:: bash

   # Structure manipulation
   read_data            # Read initial structure
   create_atoms         # Create atoms in regions
   change_box           # Change simulation box

   # Force field setup
   pair_style           # Set interaction potential
   pair_coeff           # Set interaction coefficients
   bond_style           # Set bond potential
   angle_style          # Set angle potential
   dihedral_style       # Set dihedral potential

   # Simulation control
   minimize             # Energy minimization
   fix nve              # Constant energy ensemble
   fix nvt              # Constant temperature
   fix npt              # Constant pressure and temperature
   run                  # Run simulation

   # Analysis
   compute              # Define computes for analysis
   thermo               # Output thermodynamic data
   dump                 # Output trajectory data
   thermo_style custom  # Customize output format

**Polymer-Specific LAMMPS Tips**

- Use bond, angle, and dihedral potentials for explicit chain modeling
- Consider your polymer chain length and system size - scale accordingly
- For coarse-graining, use effective potentials to represent multiple atoms
- Use `compute gyration` to track chain conformation
- Monitor energy and temperature carefully during equilibration
- Use constraints on bonds if using larger timesteps


Troubleshooting
---------------

Common issues: :doc:`../troubleshooting`


Community & Discussion
----------------------

- LAMMPS Mailing List: https://lammps.sandia.gov/
- LAMMPS GitHub issues: https://github.com/lammps/lammps
- Group meetings: :doc:`../collaboration/meetings`
- Stack Exchange and GitHub communities


Contributing to This Section
-----------------------------

Have a useful MD trick or resource? Contribute to this wiki:

See :doc:`../collaboration/guidelines` for how to contribute.
