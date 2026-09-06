## 2026-09-05
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
