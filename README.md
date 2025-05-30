# Blast_Classification
 Train, validate and test random forest and k-nearest neighbors models to identify blasts and RLs (Reactive Lymphocytes)

> This GitHub page is made, along with that of [Nucleus_Crop](https://github.com/jhtullis/Nucleus_Crop), to accompany "Distinguishing Reactive Lymphocytes from Blasts Using Fractal Chromatin Patterns" by R. Cordner et al, under review by the *International Journal of Laboratory Hematology* as of May 2025.

## Introduction

Blasts and reactive lymphocytes (RLs) are classes of white blood cells that are hard for even experts to differentiate under the microscope, but signal very different clinical outcomes. This GitHub page documents the training, validation and testing of classification algorithms to differentiate between blast subtypes and RLs based solely on quantitative data describing the visual texture and structure of the cell nucleus. This data was obtained by processing labeled images of the cells' nuclei using [TWOMBLI](https://github.com/wershofe/TWOMBLI).

## Setup Instructions

These instructions will be most helpful for those wishing to reproduce or adapt these results with *limited experience with Python, Jupyter Notebooks, and Git*. The instructions can be *skipped or skimmed by intermediate and advanced users*.

### 0. Initial Requirements

To replicate the results of this project, you must have:

- **Python 3.x** installed
- The **pip** package manager (typically included with Python) or equivalent such as **conda**, these instructions focus on **pip**. 
- An IDE or environment that supports **Jupyter Notebooks** (we recommend [VS Code](https://code.visualstudio.com/))

To run the code locally, it's also best to **clone this repository**. This requires that you have [Git](https://git-scm.com/) installed.

Open your command prompt or terminal, navigate to the directory (folder) where you'd like to store the project, and run:

```bash
git clone <https url>
cd <repository-folder>
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

This GitHub page is made, along with that of [Nucleus_Crop](https://github.com/jhtullis/Nucleus_Crop), to accompany "Distinguishing Reactive Lymphocytes from Blasts Using Fractal Chromatin Patterns" by R. Cordner et al, under review by the *International Journal of Laboratory Hematology* as of May 2025.
- Data was sourced and preprocessed by Abigail Gordhamer and Ryan Cordner as described in the paper referenced above.
  - Blood smear slides containing each of the cell types considered in this study were sourced from an archival slide bank
  - Individual cells were manually photographed using a light microscope
  - Images were cropped to individual cell nuclei, both manually and with [Nucleus_Crop](https://github.com/jhtullis/Nucleus_Crop)
  - The background cytoplasm and other artifacts were removed from the image
  - Feature extraction was then performed on each of these images using [TWOMBLI](https://github.com/wershofe/TWOMBLI)
  - Some additional features were engineered from this dataset and other features were removed
- Inspiration and direction for the study, including the use of k-nearest neighbors and random forest to classify blasts based on the processed data, came from Ryan Cordner
- Initial analyses with random forest were completed by Ryan Cordner and Abigail Gordhamer
- The code, documentation, and analyses contained in this repository using random forest and k-nearest neighbors were created/performed by Jason Henry Tullis
- OpenAI's Chat GPT was useful in guiding, debugging, and improving isolated portions of the code in this repository, as well as helping structure and refine the content of this `README.md`.
