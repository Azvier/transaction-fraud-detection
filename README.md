# Transaction Fraud Detection

This project implements a machine learning pipeline to detect fraudulent financial transactions. It uses a combination of feature engineering, exploratory data analysis, and model training to build a robust fraud detection system.

## Features

- **Feature Engineering:** Creates a rich set of features from the raw transaction data, including temporal, behavioral, and aggregated features.
- **Exploratory Data Analysis:** Analyzes the data to understand the distribution of features and their relationship with fraudulent transactions.
- **Model Training:** Trains and evaluates several models, including LightGBM, a Multi-Layer Perceptron (MLP), and a Graph Neural Network (GNN).
- **Hyperparameter Tuning:** Uses Optuna to find the optimal hyperparameters for the LightGBM model.

## Architecture and Workflow

1.  **Data Ingestion:** The project starts by reading the raw financial transaction data from a CSV file.
2.  **Feature Engineering:** A comprehensive set of features is engineered to capture various aspects of the transactions.
3.  **Exploratory Data Analysis:** The engineered features are analyzed to gain insights into the data.
4.  **Model Training and Evaluation:** Several models are trained and evaluated on the preprocessed data.
5.  **Output:** The trained models and feature importance scores are saved to the `output/` directory.

## Project Structure

```
├── .gitignore
├── LICENSE
├── pdm.lock
├── pyproject.toml
├── readme-instruction.md
├── README.md
├── datasets
│   ├── feature-dictionary.md
│   └── README.md
├── notebooks
│   ├── 00-xgboost-scale-weight.ipynb
│   ├── 01-feature-engineering.ipynb
│   ├── 02-exploratory-data-analysis.ipynb
│   └── 03-model-training-evaluation.ipynb
└── output
    ├── features-mutual-info-scores.csv
    ├── models
    └── split-dataset
```

-   **datasets/:** Contains the raw and processed data used in the project.
-   **notebooks/:** Contains the Jupyter notebooks used for feature engineering, exploratory data analysis, and model training.
-   **output/:** Contains the trained models, feature importance scores, and other outputs.

## Getting Started

### Prerequisites

-   Python 3.12
-   PDM

### Installation

1.  Clone the repository:
    ```bash
    git clone https://github.com/your-username/transaction-fraud-detection.git
    ```
2.  Install the dependencies using PDM:
    ```bash
    pdm install
    ```

## Usage

To run the project, you can execute the Jupyter notebooks in the `notebooks/` directory in the following order:

1.  `01-feature-engineering.ipynb`
2.  `02-exploratory-data-analysis.ipynb`
3.  `03-model-training-evaluation.ipynb`

## Note on Data and Models

The dataset used in this project is not included in the repository due to its size. However, the code is fully reproducible. The expected output of the training script is a set of trained models with high accuracy in detecting fraudulent transactions.

## Results and Outputs

The project produces the following outputs:

-   **Trained Models:** The trained models are saved in the `output/models/` directory.
-   **Feature Importance Scores:** The feature importance scores are saved in the `output/features-mutual-info-scores.csv` file.
-   **Split Dataset:** The split dataset is saved in the `output/split-dataset/` directory.

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue for any bugs, feature requests, or improvements.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
