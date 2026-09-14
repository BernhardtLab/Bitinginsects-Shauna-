# 📊 Project overview 


In this study we used sequences generated from DNA barcodng and metabarcoding on the Oxford Nanopore MinION 
to investigate nematode incidence and biting insect diversity in the Arctic. 
The data has already been run through The Barcode Inference Pipeline (BIP) which was developed at the centre for biodiversity genomics. 
Here we filter out contamination detected on the negatives controls and identify species which could not be identified with BIP (which uses probabilistic methods) using sequence similarity on BOLD (BOLDID). To investigate the success of this method we build phylogenies using maximum likelihood 
and 1000 bootstrapping iterations. We then investigated species diversity using a variety of packages such as iNEXT, vegan, and betapart. 

3 script files are used in this analysis and are set up in a way that each can be run independently without needing to run prior scripts 

## 📁 Script Files

### 1. `1_Data_Cleaning.R`
- Contains all data cleaning steps recorded in the lab notebook  
- Includes:
  - Fixes for problematic samples 
  - Handling of samples rerun on new plates  
  - Contamination correction using negative controls  
- Processing is separated by year:
  - **2024 (barcoding)**  
  - **2025 (metabarcoding)** (different control plate setup)

---

### 2. `2_Phylogenetic_Analysis_UniqueSequences.R`
- Combined phylogenetic analysis for **2024 + 2025**
- Uses **unique sequences**
- Includes:
  - BOLD database sequence import  
  - Comparison of phylogenetic assignment methods (Scripts 3 & 4)

---

### 3. `3_Ecological_Analysis.R`
- Contains ecological analyses and most figure generation:
  - iNEXT analyses  
  - Comparison with **2012 dataset (Schaefer 2014)**  
  - Species richness calculations  
  - NMDS 
  - betapart analysis 
  - Sample map production  
  - Temperature comparison plots 
  - GBIF map generation
- Clearly divided into labeled sections  

---

## 📂 Data

### Raw Data (`Raw_data`)
Contains all primary data used in analysis.

#### 2024 Sequence Data
- `KGLKTK_2024_OTUDetails.tsv`  
- `CBAY2024_AllPlates_OTUDetails.tsv`  
  - Includes `problemsamples.csv` (lab-noted issues)  
- `Shauna_CBAY2024_Plate3_OTUDetails.tsv`

#### 2025 Sequence Data
- `KBIMP2025_insectCOI_OTUDetails.tsv`  
- Control files:
  - `extractiondata2025.csv`  
  - `PCRcontrol_data.csv`

#### Outgroup Data
- `Outgroup.csv`

#### Metadata Files
- `CBAY2025_metadata.csv`  
- `KGLTK2025_metadata.csv`  
- `KBIMP2024_specimendata.csv`  
- `KBIMP_meta_sitenamesfixed.csv`  
- `vector_change.csv`

#### Results from BOLD
- `BOLDID_aedes.csv`
-`BOLDID_simuulidae.csv`
-`BOLDID_meta.csv`
-`BOLDIDspecies.csv`

#### Historical Dataset
- `schafer_2012.csv`

#### Positive control data 
-`positivecontrolplatemap.csv`
-`COINEM_POS_TaxonomicAssignments.tsv`

---

### Processed Data
Generated during analysis and reused in later steps.

#### Filtered Sequence Files
- `KBIMP2024_filteredCOI.tsv`  
- `KBIMP2025_filteredCOI.tsv`

#### Unique Sequence Files (for BOLD searches)
- `uniquemosseqforbold.fasta`  
- `unique_simseq_forbold.fasta`  
- `unique_bfseq_forbold.fasta`

#### BOLD Database Outputs
- `BOLDaedescombined.csv`  
- `BOLDID_simuulidae.csv`  
- `BOLDID_notsimulidae.csv`  
- `BOLDIDspecies.csv`  
  - Contains **BIN codes and corresponding species**

#### Final Species Dataset
- `KBIMP_updatedspecies.tsv`

---

## Required packages 

The analysis scripts require R and the following packages (versions used in the manuscript are noted):

stringr
tidyverse
readr
viridis
ggplot2 
Biostrings 
ape 
muscle
phangorn    
ggtree    
seqinr
DECIPHER
betapart
car
DescTools
iNEXT
aRtsy
vegan
ARTool
emmeans
lmerTest
patchwork
brms
ggvenn
maps
ggmap
sf
rgbif
rnaturalearth
paletteer
rentrez 

## ✅ Notes
- Processed files are generated within analysis scripts but may be reused across workflows  
- Scripts are designed to be run in sequence for reproducibility  
- Year-specific differences (2024 vs 2025) are handled explicitly in early processing

