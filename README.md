# DSA-103-Project
"Chemical property analysis and visualization of compounds" using doi/10.1126/sciadv.adi4029



# Download the latest Miniconda installer for Linux (Python 3.10 version)
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh


#Run the installer 
bash Miniconda3-latest-Linux-x86_64.sh

#Activate Conda
source ~/.bashrc


#Creating environment
conda create -n chemproj python=3.10

#Activate environment
conda activate chemproj


#Install rdkit
conda install -c conda-forge rdkit -y


pip install pandas scikit-learn umap-learn matplotlib seaborn rdkit-pypi
pip install "numpy<2"

python3 project_main.py


Loading data...
Unique compounds: 24046
Computing descriptors...

=== PCA Analysis ===
Total variance explained by PC1+PC2: 68.1%
PC1 explains 49.7% of variance
PC2 explains 18.5% of variance
PCA loadings saved.
                  PC1       PC2
MW           0.389201 -0.122851
LogP        -0.143324 -0.307530
TPSA         0.413493  0.131515
HBD          0.336850  0.152132
HBA          0.405436  0.142195
RotBonds     0.185972 -0.237124
Rings        0.250552  0.030417
Fsp3         0.104217 -0.589796
Aromatic    -0.080495  0.596419
Heteroatoms  0.408874  0.137437
QED         -0.311896  0.223733

Interpretation of axes:
PC1 represents: PC1: [0.41×TPSA + 0.41×Heteroatoms + 0.41×HBA] - [0.31×QED + 0.14×LogP + 0.08×Aromatic]
PC2 represents: PC2: [0.60×Aromatic + 0.22×QED + 0.15×HBD] - [0.59×Fsp3 + 0.31×LogP + 0.24×RotBonds]
PCA loadings saved to: pca_loadings.csv
correlation_heatmap saved.
Computing pca...
Saved pca as pca.png
Computing scaffolds...
Saved scaffold bar plot as scaffold_distribution.png
Computing class distribution..
Saved class distribution as class_distribution.png
Generating standalone UMAP plot...
UMAP figure saved as umap_plot.png
Property plot for top 8 classes saved: analysis_output/figures/Fsp3_by_top_classes.png
Saved boxplots as boxplot_{prop}_by_top{n_classes}_classes.png

Analysis complete!
Results saved to analysis_output




