## 2026-09-13
pI  
Tests were run on my computed features vs Moran et al 2024's, with bins matching their Figure 5. For fraction fragile, data from Moran et al 2024's supplementary data DataS1 were used, a column indicating significant peptides if a protein's structure was disrupted under pressure.  
Chi-square p-value (100 MPa): <0.0001  
Chi-square p-value (50 MPa):  <0.0001  
U-shape visible, with both extremes of pI<5 or pI>10 having a fraction fragile of ~0.6 and the middle pI having a fraction fragile of ~0.2 to 0.4

Packing density 
Proteins sorted from least to greatest packing density, and found that those with highest packing density and fewest internal voids (Q4) were most fragile. The data should have an ascending order of fragility from Q1 to Q4, but Q1 had a 20 protein difference more than Q2, but it could be due to different reasons such as extreme pI or noise.  
Chi-square p (100 MPa): 0.0014  
Chi-square p (50 MPa):  0.1093  (not significant)
spearman rho (100 MPa): 0.1488  
Partially matched, and significant at 100MPa, but not completely clean across all quartiles.

Cofactor chemistry
Type of cofactor vs fraction fragile.  
Chi-square p (100 MPa): 0.0048  
Chi-square p (50 MPa):  0.4414 (not significant but similar pattern)  
Covalent < divalent: at 100 MPa, proteins with only covalent cofactors had 23.7% fragile proteins while proteins with only divalent cations had fragile proteins 45.5% of the time. This is likely due to the fact that the covalent bond physically holds the protein together under compression, while the metal ion doesn't, causing proteins with covalent cofactors to be more protected under pressure.  
There were only 18 proteins with both covalent cofactors and divalent cations, and later were merged into the covalent category, forming a 24.2% fragile proteins, and actually lowered the p-value to 0.0017.

Overall the 50 MPa results were less significant because at a lower pressure, there were less fragile proteins, causing less difference overall for the chi-square tests. The gate passed, and all three features were reproduced for 100 MPa.

## 2026-09-05
Added corresponding fraction disorder to each protein.
Tried to use Metapredict to calculate fraction of disorder in each protein in Jupyterlab, but the kernel kept crashing. I switched to trying it in terminal instead, but that also kept crashing with a segmentation fault, so I decided to use Alphafold pLDDT instead for disorder, though it could be less accurate (?). Though pLDDT doesn't directly measure disorder, its confidence prediction is correlated with it.

Instead of Metapredict fraction of > .5, it would be pLDDT < 50 to assess for high disorder. 
Was the (# low pLDDT residues)/(total residues) per protein, giving most fraction values of very close to 0.

## 2026-09-02
Gromacs force field: Amber99sb (7)
Adding Hydrogens for one protein(Q72IK0) test: 
gmx pdb2gmx -f AF-Q72IK0-F1.pdb -o Q72IK0_H.pdb -water none -ignh

Used Gromacs to hydrogenate and ProteinVolume to calculate packing density for 1226 proteins; took around 9 hours! Because I am trying to replicate Moran et al's results, I am using the tools they used. 


## 2026-08-29
searched Uniprot rest API for cofactor annotations on all t. thermophilus proteins, seeing if each has a COFACTOR comment, then a cofactor name to see if it is divalent cation or covalent.
Covalent: 132, Divalent: 141, Both: 18, Neither 969.
had to run the loop twice because of rate limits and connection! At first, only 1224/1225 proteins were classified, with one protein Q72IX5 left, which I checked individually. 

## 2026-08-20
Built the join table, and Downloaded DataS1 from Moran 2024 piezophile supplemental data of 1225 proteins, finding that my computed pI matches.

## 2026-06-25
Emailed author of ProteinVolume Dr. Makhatadze, asking whether it was ok to use static AlphaFold 
structures to compare packing density between ortholog pairs of 2 species, and whether running molecular
dynamics was necessary? He replied that static would work (yay) for relative comparisons.

## 2026-06-22
Computed isoelectric points for the full T. thermophilus HB27 proteome (UP000000592) using 
Biopython ProteinAnalysis. 2000 proteins, ranging around 4.5 to 11, and still need to organize 
into a pandas DataFrame

## 2026-06-16
Installed Miniforge & set up computing environment. Created conda environment piezo with Python 3.11, 
Biopython, pandas, JupyterLab, and I verified that the environment works
