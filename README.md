# ABFE Burn-in Set

This repository contains the files associated with the ABFE benchmark. 

The ultimate goal of this exercise is to benchmark the latest version of the Open Force Field on a large data set within an ABFE workflow.
The compute load for this benchmark could be shared amongst members of the community. Industry members could complement the benchmark with performance reports on inhouse data. 
Before this can happen, a workflow that can be adopted my multiple members in the community needs to be identified. 
This workflow must be open source, easy to establish in various architectures and also work for a range of systems. 

To identify the most appropriate ABFE workflow, it was decided to test various workflows with a "burn-in dataset".
We therefore invite members of the community to use the input files reported below in their ABFE workflows, and report back the results.
Furthermore, we encourage members of the community to test the workflows of others and report back on the transferability and ease of use. 

#### Burn-in Set Composition
The burn-in set is designed to cover a range of systems, going from "well-behaved" to "badly behaved".
All ligands are neutral, to prevent the need for charge corrections at this stage.
Ligand co-ordinates were supplied by V. Gapsys and I. Alibay, however the proteins were freshly downloaded from the PDB and re-prepared using the Schrödinger ligand preparation workflow.
This workflow restored missing loops and side chains (using Prime), retained water molecules near the binding site (but not clashing with any of the ligands) and capped chains wherever was appropriate.
  
The burn-in set contains the following systems:
- <a href="https://pubs.rsc.org/en/content/articlelanding/2016/sc/c5sc02678d">BRD4(1)</a>: with 2 ligands
- <a href="https://pubs.rsc.org/en/content/articlepdf/2020/sc/c9sc03754c ">cMet</a>: with 2 ligands
- <a href="https://www.sciencedirect.com/science/article/pii/S0960894X19306754">CycloD</a>: with 2 fragments and a merged ligand
- <a href="https://pubs.acs.org/doi/10.1021/jm060199b">jnk1</a>: with 2 ligands
- <a href="https://pubs.acs.org/doi/pdf/10.1021/jm101423y">p38</a>: with 2 ligands
- <a href="https://www.sciencedirect.com/science/article/pii/S0022283609005075?via%3Dihub">thrombin</a>: with 2 ligands

#### Burn-in set input files

The notebook, based off the super notebook examples that are available on the Open Force Field GitHub page, uses the structures files in `./structures/<target name>`.
Protein parameters are obtained from AMBER14SB and TIP3P, while the ligand parameters are from the open Force Field v.2.0 "Sage".
The workflow generates only GROMACS parameters in the form of a co-ordinate (.gro) and topology (.top) file. 

If you require AMBER-formatted input files, we recommend that you use the ParmEd library to facilitate the conversion. 

#### Directory Setup

The input files to be used for the burn-in set can be found in the `./parameters/<target name>` directory.  The files are only provided in GROMACS format. 

```
burn_in_parameter_generation.ipynb  # Notebook used to generate parameters and GROMACS files
structures
├── <target_name>                   # directory for target
│   ├── protein_water.pdb           # co-ordinates of the protein
│   ├── ligand<num>.sdf             # co-ordinates and connectivity of the ligand
│   ├── ligand<num>.pdb             # co-ordinates of the ligand
│   ├── ligand<num>.mol2            # co-ordinates and connectivity of the ligand
parameters
├── <target_name>                   # directory of parameters for target 
│   ├── ligand<num>                 # directory for files regarding <target_name> and ligand<num> 
│   │   ├── complex.gro             # co-ordinate file for protein-ligand-key waters complex
│   │   ├── complex.top             # topology file for protein-ligand-key waters complex
│   │   ├── ligand.gro              # co-ordinate file for ligand (for the solvation step)
│   │   ├── ligand.top              # topology file for ligand (for the solvation step)
```

#### Questions?

If you have any questions, please feel free to reach out to Joe Bluck or Katharina Meier. 
