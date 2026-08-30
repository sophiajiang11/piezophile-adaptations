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
