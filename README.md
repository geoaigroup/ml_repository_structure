# Project Repository Structure :file_folder:

This document outlines the standardized structure for all project repositories to ensure consistency and ease of collaboration.

## Repository Structure
```text
project-root/
├── media/                # Static assets (non-Python)
│   ├── image1.png        # Documentation/images
│   └── image2.jpg        # Screenshots/visuals
│
├── data/                  # Datasets (non-Python)
│   ├── raw/              # Original, immutable data
│   ├── processed/        # Cleaned and transformed data
│   └── external/         # Third-party data
│
├── notebooks/            # Jupyter notebooks (non-Python)
│
├── src/                  # Source code (Python package)
│   ├── __init__.py       
│   ├── data/             # Data processing
│   ├── models/           # Model code
│   ├── evaluation/       # Evaluation logic
│   ├── visualization/    # Visualization tools
│   ├── utils/            # Utilities
│   ├── train.py          # Main training script
│   └── eval.py           # Main evaluation script
│
├── experiments/           # Experiment results (non-Python)
│   ├── experiment_1/
│   │   ├── logs/
│   │   └── checkpoints/
│   └── experiment_2/
│       ├── logs/
│       └── checkpoints//
│
├── scripts/              # Helper scripts (.sh/.bash)
├── tests/                # Test cases
├── config/               # Configuration files
├── requirements.txt      # Python dependencies
├── Dockerfile            # Environment setup
├── .gitignore            # Git exclusion rules
└── README.md             # Project documentation
```

## Key Files & Folders :key:
(<kbd>Required</kbd> = Must exist from Day 1, even if empty)
### Core Structure
```text
- **`media/`**: Contains images displayed in documentation
  - `image1.png`, `image2.jpg` - Supplementary figures/visuals
- **`data/`** <kbd>Required</kbd> : Datasets storage 
  - `raw/`: Original immutable data
  - `processed/`: Cleaned/transformed data  
  - `external/`: Third-party sources
- **`notebooks/`** <kbd>Required</kbd>: Jupyter notebooks 
  - Exploration, prototyping, and demos
- **`src/`** <kbd>Required</kbd>: Main Python package 
  - Submodules: `data/`, `models/`, `evaluation/`, etc.
- **`experiments/`** <kbd>Required</kbd>: Training artifacts 
  - `experiment_1/`: Logs and checkpoints
  - `experiment_2/`: Alternative configurations
- **`config/`** <kbd>Required</kbd>: YAML/JSON configuration files 
```  
### Supporting Files
```text
- **`requirements.txt`**: Python dependencies  
  ```pip install -r requirements.txt```
- **`Dockerfile`**: Container configuration  
  ```docker build -t project-name .```
- **`README.md`** <kbd>Critical</kbd>: Project documentation  
  - Setup instructions, usage examples, and citations
```
### Additional Directories
```text
- **`scripts/`**: Automation scripts (.sh/.bash)
- **`tests/`**: Pytest/unittest cases
```


## Python Module Requirements :snake:

All subfolders under `src/` must be proper Python modules:
```text
src/
├── __init__.py          # Required for root package
└── data/
    ├── __init__.py      # Required for module
    └── loader.py       # Import via: from src.data import loader
```

## Repository Rules :traffic_light:

### Folder Naming
- :x: Never rename core folders (e.g., `src/data/` → `src/datasets/`)
- :white_check_mark: Keep original names

### Module Management
- :heavy_plus_sign: Add new modules as needed (e.g., `src/inference/`)
- :wastebasket: Delete unused modules (e.g., empty `src/visualization/`)

### Code Location
- :snake: Python code **only** in `src/` and `tests/` (with `__init__.py`)
- :file_folder: Non-Python files in `data/`, `notebooks/`, `experiments/`

## Real-World Scenarios :test_tube:

✅ Allowed:
- Creating `src/inference/` for prediction logic
- Deleting empty `src/visualization/` folder

❌ Not Allowed:
- Renaming `src/models/` → `src/networks/`
- Adding Python files to `data/` without `__init__.py`

## Important Notes :memo:

1. **Must-Have Folders**: Create these even if empty:
   ```
   data/, notebooks/, src/, experiments/
   ```
2. Other folders (`scripts/`, `config/`) can be added later
3. Maintain identical structure across all repositories
4. Update `.gitignore` to exclude large data files/credentials
```
