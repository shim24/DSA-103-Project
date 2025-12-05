# Chemical Compound Analysis Project

## Overview
This project performs comprehensive chemical compound analysis using computational chemistry methods, including molecular descriptor calculation, dimensionality reduction, and structural pattern visualization. It provides insights into chemical space distribution, scaffold diversity, and property relationships for a library of 24,046 unique compounds.

## Prerequisites
- Conda package manager (Miniconda or Anaconda)
- Python 3.10
- Basic knowledge of command line interface

## Project Structure
```
project/
├── project_main.py          # Main analysis script
├── analysis_output/         # Generated results directory
│   ├── figures/             # Visualization files
│   └── data/                # Processed data files
├── requirements.txt         # Python dependencies
└── README.md               # This file
```

## Setup Instructions

### 1. Create and Activate Conda Environment
```bash
# Create new environment with Python 3.10
conda create -n chemproj python=3.10

# Activate the environment
conda activate chemproj
```

### 2. Install Dependencies

#### Install RDKit (Core Chemistry Toolkit)
```bash
conda install -c conda-forge rdkit -y
```

#### Install Additional Python Packages
```bash
pip install pandas scikit-learn umap-learn matplotlib seaborn rdkit-pypi
pip install "numpy<2"  # Compatibility requirement
```

## Running the Analysis
Execute the main analysis script:
```bash
python3 project_main.py
```

## Analysis Output

### Key Statistics
- **Total unique compounds analyzed**: 24,046
- **Molecular descriptors computed**: 11 descriptors

### PCA Analysis Results
- **Total variance explained (PC1 + PC2)**: 68.1%
- **PC1 variance explained**: 49.7%
- **PC2 variance explained**: 18.5%

### Principal Component Interpretation

#### PC1 (49.7% variance)
**Represents**: Molecular polarity and hydrogen bonding capacity
- **Strong positive loadings**: 
  - TPSA (Topological Polar Surface Area): 0.41
  - Heteroatoms count: 0.41
  - HBA (Hydrogen Bond Acceptors): 0.41
- **Strong negative loadings**:
  - QED (Quantitative Estimate of Drug-likeness): -0.31

#### PC2 (18.5% variance)
**Represents**: Structural complexity and aromaticity
- **Strong positive loadings**:
  - Aromatic rings: 0.60
  - QED: 0.22
- **Strong negative loadings**:
  - Fsp3 (Fraction of sp3 carbons): -0.59
  - LogP (Octanol-water partition coefficient): -0.31

### Generated Output Files

#### Data Files
- `pca_loadings.csv` - Complete PCA component loadings matrix
- `molecular_descriptors.csv` - Computed descriptors for all compounds

#### Visualization Files
1. **PCA Plot** (`pca.png`)
   - 2D projection of chemical space using first two principal components
   - Color-coded by compound class or properties

2. **Scaffold Distribution** (`scaffold_distribution.png`)
   - Frequency distribution of molecular scaffolds
   - Identifies most common structural frameworks

3. **Class Distribution** (`class_distribution.png`)
   - Distribution of compounds across chemical classes
   - Shows diversity of chemical space coverage

4. **UMAP Visualization** (`umap_plot.png`)
   - Non-linear dimensionality reduction plot
   - Reveals clusters and relationships in high-dimensional space

5. **Property Analysis** (`Fsp3_by_top_classes.png`)
   - Distribution of Fsp3 (Fraction of sp3 carbons) across top compound classes
   - Assesses saturation levels in different chemical classes

6. **Boxplot Series** (`boxplot_{property}_by_top_classes.png`)
   - Comparative analysis of molecular properties across chemical classes
   - Properties include: MW, LogP, TPSA, HBD, HBA, etc.

## Molecular Descriptors Computed
The analysis computes 11 key molecular descriptors:
1. **MW** - Molecular Weight
2. **LogP** - Octanol-water partition coefficient
3. **TPSA** - Topological Polar Surface Area
4. **HBD** - Hydrogen Bond Donors
5. **HBA** - Hydrogen Bond Acceptors
6. **RotBonds** - Rotatable Bonds
7. **Rings** - Number of rings
8. **Fsp3** - Fraction of sp3 carbons
9. **Aromatic** - Aromatic rings count
10. **Heteroatoms** - Non-carbon heavy atoms
11. **QED** - Quantitative Estimate of Drug-likeness

## Output Directory Structure
```
analysis_output/
├── figures/
│   ├── pca.png
│   ├── scaffold_distribution.png
│   ├── class_distribution.png
│   ├── umap_plot.png
│   ├── Fsp3_by_top_classes.png
│   └── boxplot_*.png
├── pca_loadings.csv
└──compounds_with_descriptors.csv

```

## Troubleshooting

### Common Issues

1. **Conda environment activation fails**
   ```bash
   # On Windows
   conda activate chemproj
   
   # If above fails, try:
   conda init powershell
   # Then restart terminal
   ```

2. **RDKit installation issues**
   ```bash
   # Alternative installation method
   conda install -c rdkit rdkit
   ```

3. **NumPy compatibility warning**
   - The command `pip install "numpy<2"` ensures compatibility with RDKit
   - If already installed, use: `pip install numpy==1.24.3`

4. **Missing dependencies**
   ```bash
   # Create requirements file and install
   pip freeze > requirements.txt
   pip install -r requirements.txt
   ```

## Interpretation Guidelines

### PCA Results
- **PC1**: Higher values indicate more polar, hydrogen-bonding compounds
- **PC2**: Higher values indicate more aromatic, drug-like compounds; lower values indicate more saturated, flexible molecules

### Quality Metrics
- **Variance explained > 60%**: Good representation of chemical space
- **Scaffold diversity**: Higher diversity indicates broader chemical coverage
- **Class distribution**: Even distribution suggests balanced library design

## Applications
This analysis pipeline is useful for:
- Chemical library characterization
- Compound selection for screening
- SAR (Structure-Activity Relationship) studies
- Property-based compound clustering
- Scaffold hopping and diversity analysis

## Performance Notes
- Processing 24,046 compounds typically completes in 5-10 minutes on standard hardware
- Memory usage scales with compound count and descriptor complexity
- UMAP computation is the most computationally intensive step

## Support
For issues or questions:
1. Check the troubleshooting section
2. Verify all dependencies are correctly installed
3. Ensure input data is in the correct format
4. Consult RDKit documentation for chemistry-specific questions

## License
This project is intended for research and educational purposes. Please ensure compliance with any licensing requirements for input data and software dependencies.
