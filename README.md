# ChEMBL In-Silico Drug Discovery Pipeline



End-to-end QSAR + docking pipeline using ChEMBL bioactivity data and AutoDock Vina.



## Pipeline

1. ChEMBL data curation

2. Scaffold-aware QSAR (ECFP + Random Forest)

3. Large-scale virtual screening

4. ADMET filtering

5. AutoDock Vina docking





## Structure

\- notebooks/        Jupyter notebooks

\- data/processed/  Curated datasets

\- screening/       QSAR screening outputs

\- docking/         Protein + docking

\- results/         Final ranked candidates



## Setup

```bash

pip install -r requirements.txt



