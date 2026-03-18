Datasets for Research
=====================

Public Datasets
---------------

**Molecular & Structural Data**

**Protein Data Bank (PDB)**
   https://www.rcsb.org/

   - Experimentally determined protein structures
   - Over 200,000 structures
   - Search and download by protein name or ID
   - Essential for protein simulations

**UniProt**
   https://www.uniprot.org/

   - Protein sequence and function database
   - 200+ million sequences
   - Annotations and cross-references
   - Great for sequence analysis


**AlphaFold Protein Structure Database**
   https://alphafold.ebi.ac.uk/

   - Predicted structures for millions of proteins
   - Ready for simulation
   - High confidence scores available


**Materials Databases**

**Materials Project**
   https://materialsproject.org/

   - 160,000+ calculated materials properties
   - Crystal structures
   - Electronic structure data
   - Perfect for materials ML


**ICSD (Inorganic Crystal Structure Database)**
   https://icsd.fiz-karlsruhe.de/

   - Crystal structures of inorganic compounds
   - 250,000+ structures
   - Physical properties


**NOMAD**
   https://nomad-lab.eu/

   - Open Materials Database
   - Computational materials data
   - Free access


Chemistry & Drug Discovery
--------------------------

**PubChem**
   https://pubchem.ncbi.nlm.nih.gov/

   - Chemical compounds and bioassay data
   - 100+ million compounds
   - Molecular properties
   - Free download


**ChEMBL**
   https://www.ebi.ac.uk/chembl/

   - Bioactive molecules database
   - 2+ million molecules
   - Binding, functional, ADMET data
   - Great for drug discovery ML


**ZINC**
   https://zinc.docking.org/

   - Free database for virtual screening
   - Commercial compounds
   - Purchasable molecules


Biological Data
---------------

**BioStudies**
   https://www.ebi.ac.uk/biostudies/

   - Biological research data
   - Genomic data
   - Experimental data
   - Open access


**Kaggle Datasets**
   https://www.kaggle.com/datasets

   - 60,000+ datasets
   - Various domains and sizes
   - Includes competitions


**Hugging Face Datasets**
   https://huggingface.co/datasets

   - Ready-to-use datasets for ML
   - Often with benchmarks
   - Easy integration with ML pipelines


General Purpose Datasets
------------------------

**UCI Machine Learning Repository**
   https://archive.ics.uci.edu/ml/

   - 600+ datasets
   - Classic ML benchmark datasets
   - Good for learning


**OpenML**
   https://www.openml.org/

   - 10,000+ datasets
   - Automatic evaluation tools
   - Good for benchmarking


**Google Dataset Search**
   https://datasetsearch.research.google.com/

   - Find datasets across the web
   - Search by topic


Literature & Text Data
----------------------

**arXiv**
   https://arxiv.org/

   - Preprints of papers
   - 2+ million papers
   - Download in bulk or individual papers


**PubMed**
   https://pubmed.ncbi.nlm.nih.gov/

   - Biomedical literature
   - 30+ million citations
   - Free access


**Common Crawl**
   https://commoncrawl.org/

   - Web crawl data
   - 25+ petabytes
   - Multiple snapshots


Trajectory & Simulation Data
----------------------------

**Molecular Dynamics Trajectory Data**

Group-specific trajectories:
   - Contact group leads for access
   - Usually stored on local clusters
   - Use MDAnalysis to analyze


**AMBER NetCDF Trajectories**

   Common format: .nc files
   Can be converted to other formats


**GROMACS Trajectories**

   Common formats: .xtc, .trr files
   Use gromacs tools for analysis


Data Organization Guidelines
----------------------------

**Directory Structure**

.. code-block:: text

   data/
   ├── public/
   │   ├── pdb/
   │   ├── materials/
   │   └── chemistry/
   ├── group/
   │   ├── simulations/
   │   ├── experiments/
   │   └── analysis/
   └── processed/
       ├── training/
       ├── validation/
       └── test/


**File Naming**

- Use descriptive names
- Include date or version
- Example: ``protein_trajectory_2024_01_15.xtc``
- Avoid spaces; use underscores


**Metadata**

Document for each dataset:

- Source and URL
- Download date
- License and attribution
- Processing steps applied
- Data shape and format
- Any issues or limitations


Data Sharing Guidelines
-----------------------

**Making Data Available**

1. **Review licenses**: Check usage rights
2. **Clean data**: Remove sensitive information
3. **Document thoroughly**: Include README
4. **Choose platform**:
   - Zenodo: General research data
   - Figshare: Standalone datasets
   - GitHub: Code + small data
   - Open Science Framework (OSF): Preregistration + data
5. **Get DOI**: Makes data citable
6. **Announce**: Share in publications


**Accessing Shared Data**

1. Check group wiki for available datasets
2. Contact data owner for access
3. Follow usage guidelines
4. Cite appropriately
5. Report any issues


Data Privacy & Security
------------------------

- Do NOT share data without permission
- Check licenses before distributing
- Remove personally identifiable information
- Use secure transfer methods
- Maintain backups


Using Datasets in ML
--------------------

**General Workflow**

1. Download and explore data
2. Check for missing values and outliers
3. Split into train/validation/test sets
4. Preprocess and normalize
5. Train model
6. Evaluate on test set
7. Document process


**Reproducibility**

- Fix random seeds
- Document preprocessing steps
- Share train/test splits used
- Include all hyperparameters
- Make code available


Finding More Data
-----------------

**Search Strategies**

- Google Dataset Search: https://datasetsearch.research.google.com/
- Research papers often reference datasets
- GitHub often has associated datasets
- Check corresponding authors' websites

**Specialized Databases**

- Domain-specific research communities
- University repositories
- Government databases
- Open data initiatives


Data Licenses
-------------

Check licensing before use:

- **Creative Commons**: Various restrictions
- **Open Data Commons**: Data-specific licenses
- **MIT/Apache**: Code-like licenses
- **Custom**: Check terms


Questions?
----------

- Ask group members
- See :doc:`computing` for storage options
- Contact data curator/group leads
