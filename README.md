# ai-labs

Solutions to the AI labs assigned in my coursework at INSAT (Institut National des Sciences Appliquées et de Technologie, Université de Carthage), covering three areas:

- **Machine Learning**: classical supervised and unsupervised models
- **Deep Learning**: neural networks
- **Reinforcement Learning**: agents learning from rewards

Each lab lives in its own self-contained folder: a Jupyter notebook committed **with its outputs**, the data it uses, and a short README.

## Labs

| # | Area | Lab | Topic | Key result |
|---|------|-----|-------|------------|
| 01 | Machine Learning | [lab01-iris-knn-logreg](lab01-iris-knn-logreg/) | Supervised classification on Iris: KNN vs Logistic Regression | KNN 100 % · LogReg 96.7 % test accuracy |

Deep Learning and Reinforcement Learning labs will be added as they are assigned.

## Repository structure

```
ai-labs/
├── README.md
├── requirements.txt          # pinned dependencies shared by all labs
├── .gitignore
└── labNN-topic/
    ├── README.md             # objective, data source, results
    ├── labN.ipynb            # the deliverable, with outputs
    └── data/                 # datasets used by the lab
```

## Setup

Requires **Python ≥ 3.11**. Run from the repository root.

```bash
# 1. Create the virtual environment (once)
python3 -m venv .venv            # Windows: py -3 -m venv .venv

# 2. Activate it (every new terminal)
source .venv/bin/activate        # Windows PowerShell: .venv\Scripts\Activate.ps1

# 3. Install dependencies (once)
python -m pip install --upgrade pip
pip install -r requirements.txt
```

## Running a lab

```bash
jupyter notebook lab01-iris-knn-logreg/lab1.ipynb
```

Then **Kernel → Restart Kernel and Run All Cells**. Notebooks read their data with paths relative to their own folder (e.g. `data/Iris.csv`).

In VS Code: open the notebook, **Select Kernel → Python Environments → `.venv`**, then **Run All**.