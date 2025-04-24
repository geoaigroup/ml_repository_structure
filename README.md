
# Project Repository Structure :file_folder:

This document outlines the standardized structure for all project repositories to ensure consistency and ease of collaboration.

## Repository Structure
```text
project-root/
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
├── experiments/          # Experiment results
│   ├── experiment_1/
│   └── experiment_2/
│
├── scripts/              # Helper scripts (.sh/.bash)
├── tests/                # Test cases
├── config/               # Configuration files
├── requirements.txt      # Python dependencies
├── Dockerfile            # Environment setup
├── .gitignore            # Git exclusion rules
└── README.md             # Project documentation
```

## Key Folders :key:

- **`data/`** (Must Have): Stores all datasets
  - `raw/`: Immutable original data
  - `processed/`: Cleaned data
  - `external/`: Third-party data
  
- **`notebooks/`** (Must Have): Jupyter notebooks for exploration/demos

- **`src/`** (Must Have): Core Python code
  - Submodules: `data/`, `models/`, `evaluation/`, etc.

- **`experiments/`** (Must Have): Saves training logs and model checkpoints

- **`tests/`**: Unit/integration tests
- **`config/`**: YAML/JSON configuration files
- **`scripts/`**: Automation scripts

## Python Module Requirements :snake:

All subfolders under `src/` must be proper Python modules:
```python
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
