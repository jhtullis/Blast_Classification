# Blast_Classification
 Validate, train and test random forest and k-nearest neighbors classifiers to differentiate between white blood cells with clinical applications.

> This GitHub repo and [Nucleus_Crop](https://github.com/jhtullis/Nucleus_Crop) accompany "Distinguishing Reactive Lymphocytes from Blasts Using Fractal Chromatin Patterns" by R. Cordner et al, under review by the *International Journal of Laboratory Hematology* as of May 2025.

## Introduction

Blasts and reactive lymphocytes (RLs) are different classes of white blood cells that are hard for even expert pathologists to differentiate under the microscope. They signal very different clinical outcomes - high numbers of blasts are indicative of different types blood cancer, while high reactive lymph counts signal potential viral infection. This GitHub page documents the training, validation and testing of (shallow) classification algorithms to differentiate between blast subtypes and RLs. The numeric features used to train the algorithms were engineered from images of the cell nuclei using [TWOMBLI](https://github.com/wershofe/TWOMBLI) and reflect the texture and fractal structure of chromatin in the nuclei.

Because the models are trained on relatively meaningful, texture related features extracted from images, the models function in a more interpretable way than deep learning based classifiers such as convolutional neural networks (CNNs). In theory, these algorithms could translate to image-based screening technologies, giving the medical laboratory scientist or pathologist a consistent, inexpensive, and independent second opinion.

## Content
```bash
Blast_Classification
├── Data/               
│   └── Cell_Data.xlsx  # labeled data used to train classifiers
├── Modeling/           
│   ├── models_workflow.ipynb   # code to train and test models
│   ├── results.pickle          # trained models, results for model validation and final testing 
│   ├── results.txt             # human readable summary of final testing results
│   └── validation.xlsx         # results for model validation 
├── requirements.txt    # project dependencies
└── README.md           # you are here
```

## Setup Instructions

These instructions will be most helpful for those wishing to reproduce or adapt these results with *limited experience with Python, Jupyter Notebooks, and Git*. The instructions can be *skipped or skimmed by intermediate and advanced users*. The trained models can also be directly accessed by unpickling `models.pickle`.

### 0. Initial Requirements

To replicate the results of this project, you must have:

- **Python 3.x** installed
- The **pip** package manager (typically included with Python) or equivalent such as **conda**, these instructions focus on **pip**. 
- An IDE or environment that supports **Jupyter Notebooks** (we recommend [VS Code](https://code.visualstudio.com/))

To run the code locally, it's also best to **clone this repository**. This requires that you have [Git](https://git-scm.com/) installed.

Open your command prompt or terminal, navigate to the directory where you'd like to store the project, and run:

```bash
git clone https://github.com/jhtullis/Blast_Classification.git
cd Blast_Classification
```

### 1. Create and Activate a Virtual Environment (recommended)

Creating a virtual environment helps to isolate dependencies.

#### On macOS / Linux:
```bash
python3 -m venv venv
source venv/bin/activate
```

#### On Windows:
```bash
python -m venv venv
venv\Scripts\activate
```

### 2. Install required packages

Install the required Python packages listed in `requirements.txt` by running the following from your command prompt:

```bash
pip install -r requirements.txt
```

If you run into issues with dependencies, try using a virtual environment and install the packages listed under the `# versions used in development` section in `requirements.txt`.

### 3. Run the Jupyter Notebook
Open the notebook located at `Modeling/model_workflow.ipynb`.

To run it with the correct Python environment, make sure your IDE is using the interpreter from your virtual environment (recommended):

In VSCode,
1. Open the Command Palette with `Ctrl+Shift+P`
2. Search and select `> Python: Select Interpreter`
3. Click 'Enter interpreter path...'. 
4. Navigate to your virtual environment and select the appropriate interpreter file:
- On macOS / Linux:
`venv/bin/python3`

- On Windows:`venv\Scripts\python.exe`

5. Click 'Run All' to run the notebook cells.

## Attribution

This GitHub repo and [Nucleus_Crop](https://github.com/jhtullis/Nucleus_Crop) accompany "Distinguishing Reactive Lymphocytes from Blasts Using Fractal Chromatin Patterns" by R. Cordner et al, under review by the *International Journal of Laboratory Hematology* as of May 2025.
- Data was sourced and preprocessed by Abigail Gordhamer and Ryan Cordner as described in the paper referenced above.
  - Blood smear slides containing each of the cell types considered in this study were sourced from an archival slide bank
  - Individual cells were manually photographed using a light microscope
  - Images were cropped to individual cell nuclei, both manually and with [Nucleus_Crop](https://github.com/jhtullis/Nucleus_Crop)
  - The background cytoplasm and other artifacts were removed from the image
  - Feature extraction was then performed on each of these images using [TWOMBLI](https://github.com/wershofe/TWOMBLI)
  - Some additional features were engineered from the extracted features, and other features were removed from the dataset
- Inspiration and direction for the study, including the use of k-nearest neighbors and random forest to classify blasts based on the processed data, came from Ryan Cordner
- Initial analyses with random forest were completed by Ryan Cordner and Abigail Gordhamer
- Dr. Emily Evans from the BYU Math Department and Marshall Nielsen provided helpful input early in the modeling process
- The code, documentation, and analyses contained in this repository using random forest and k-nearest neighbors were created/performed by Jason Henry Tullis
- OpenAI's Chat GPT was useful in guiding, debugging, and improving isolated portions of the code in this repository, as well as helping structure and refine the content of this `README.md`.
