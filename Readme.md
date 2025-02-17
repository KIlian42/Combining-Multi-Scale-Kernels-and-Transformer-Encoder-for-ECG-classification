# Combining Multi-Scale Kernels and Transformer Encoder for ECG classification

This repository contains the research and code (Python) from my master thesis. (2023-2024)

Title: "Combining Multi-Scale Kernels and Transformer Encoder for ECG classification"

The research utilizes electrocardiogram (ECG) data from the Physionet 2021 challenge: https://physionet.org/content/challenge-2021/1.0.3/.

# Start

You can directly download the challenge data from the Physionet 2021 homepage: https://physionet.org/content/challenge-2021/1.0.3/#files,
or you might have a look at my Google Drive, where I wrapped all the ECG files in a single .h5 (key-value) file:
https://drive.google.com/drive/folders/1e0LygPzn5tM9i2m2leXFwSs5J5og97W5 -> do download physionet2021.h5, physionet2021_references.csv (labels) and codes_SNOMED.csv.

#### About the data

Each ECG in physionet2021.h5 is stored as key (str): "PATIENT-ID" and value: 12-lead ECG (list[12 lists]), where each ECG has 12-leads and was recorded with a sampling rate of 500Hz. Most, but not all are 10 seconds long ECGs with 5000 sample points. Physionet 2021 and the provided .h5 dataset also include some ECG recordings less than 10 seconds or up to 15 minutes, which can be preprocessed (padded/truncated) to 10 seconds. The ECGs can have multiple labels, see Physionet2021_references.csv. The corresponding arrhythmia label names are in the codes_SNOMED.csv listed. Notice, in my Google Drive is also the Physionet 2017 challenge data available and in the  directory "prepared" are further prepared datasets, since this thesis focuses particularly on the arrhythmia types Sinus Rhythm (SR), Atrial Fibrilliation (AF), Atrial Flutter (AFL), Premature Atrial Contraction (PAC) and Premature Ventricular Contraction (PVC). The Physionet 2021 labels distinguish between more than 100 known arrhythmia types. 

Reyna MA, Sadr N, Perez Alday EA, Gu A, Shah AJ, Robichaux C, Rad AB, Elola A, Seyedi S, Ansari S, Ghanbari H, Li Q, Sharma A, Clifford GD. Will Two Do? Varying Dimensions in Electrocardiography: The PhysioNet/Computing in Cardiology Challenge 2021. 2021 Computing in Cardiology (CinC), Brno, Czech Republic, 2021 (pp. 1-4). doi: 10.23919/CinC53138.2021.9662687

Reyna, M., Sadr, N., Gu, A., Perez Alday, E. A., Liu, C., Seyedi, S., Shah, A., & Clifford, G. (2022). Will Two Do? Varying Dimensions in Electrocardiography: The PhysioNet/Computing in Cardiology Challenge 2021 (version 1.0.3). PhysioNet. https://doi.org/10.13026/34va-7q14.

Goldberger AL, Amaral LAN, Glass L, Hausdorff JM, Ivanov PCh, Mark RG, Mietus JE, Moody GB, Peng C-K, Stanley HE. PhysioBank, PhysioToolkit, and PhysioNet: Components of a New Research Resource for Complex Physiologic Signals. Circulation 101(23):e215-e220 [Circulation Electronic Pages; http://circ.ahajournals.org/content/101/23/e215.full]; 2000 (June 13).

Please go to section [Setup](#Setup) for an installation guide to run this repository.

<img width="700" alt="https://en.wikipedia.org/wiki/Electrocardiography" src="https://github.com/KIlian42/Atrial-Fibrillation-Classification-Using-Ensembled-Models/assets/57774167/1a2b2533-3aae-4876-8f32-2c24ce4cc90e">
<br />Source: https://en.wikipedia.org/wiki/Electrocardiography
<br /><br /><br /><br />
<img width="1013" alt="Transformer model" src="https://github.com/KIlian42/Atrial-Fibrillation-Classification-Using-Ensembled-Models/assets/57774167/3c0b185b-b43b-49ef-bd72-5369edcab3a4">
<br />Source: Ashish Vaswani and Noam Shazeer and Niki Parmar and Jakob Uszkoreit and Llion Jones
and Aidan N. Gomez and Lukasz Kaiser and Illia Polosukhin. "Attention Is All You Need", 2017
<br /><br /><br /><br />
<img src="https://github.com/KIlian42/Atrial-Fibrillation-Classification-Using-Ensembled-Models/assets/57774167/66c8ec15-edfb-4a55-ae57-db5118aa18f2">
<br /><br /><br /><br />
<img src="https://github.com/KIlian42/Atrial-Fibrillation-Classification-Using-Ensembled-Models/assets/57774167/e1c2090c-f9e5-4027-9432-6cd6b535a130">
<br /><br /><br /><br />
<img src="https://github.com/KIlian42/Atrial-Fibrillation-Classification-Using-Ensembled-Models/assets/57774167/94422599-de4d-4001-9ae0-e068863220c6">

# Setup

<b> The repostiory is still under development, therefore just take a look at Jupiter_notebook_Physionet2021_categoricalCrossentropy.ipynb and ignore the following steps at the moment. </b>


#### Prerequisites

If not done yet, install

1. ... Git: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
2. ... Python 3.11: https://www.python.org/downloads/
3. ... Pip (Package Installer Python): https://pip.pypa.io/en/stable/installation/

#### Installation

1. Open a folder or directory on your computer, where you want to save the project.

2. Open terminal on Mac OS/Linux or cmd (Command Prompt) on Windows.

3. Clone repository
```
git clone https://github.com/KIlian42/Atrial-Fibrillation-Classification-Using-Ensembled-Models.git
```
4. Change directory
```
cd Atrial-Fibrillation-Classification-Using-Ensembled-Models
```
5. Install library to create virtual environments
```
pip install virtualenv
```
6. Create Python 3.11 environment
> Mac OS/Linux:
```
python3.11 -m venv .venv
```
> Windows:
```
py -3.11 -m venv .venv
```
7. Source enviroment
> Mac OS/Linux:
```
source .venv/bin/activate
```
> Windows:
```
.venv\Scripts\activate
```
8. Install requirements
```
pip install -r requirements.txt
```
