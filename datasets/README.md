# Financial Transactions Dataset for Fraud Detection

**Author:** Aryan Kumar

Welcome to the Financial Transactions Dataset for Fraud Detection. This dataset is designed for research and development of fraud detection systems and machine learning models.

## Dataset Access

Download the dataset from Kaggle:  
[Financial Transactions Dataset for Fraud Detection](https://www.kaggle.com/datasets/aryan208/financial-transactions-dataset-for-fraud-detection)

> **Note:** The dataset is not included in this repository due to its large size.

## Overview

This dataset contains **5 million** synthetically generated financial transactions simulating real-world behavior. It is suitable for:

- Binary and multiclass classification
- Fraud detection systems
- Time-series anomaly detection
- Feature engineering and model explainability

## Features

Each transaction record includes the following fields:

| Column Name                | Description                                                                                   |
|---------------------------|-----------------------------------------------------------------------------------------------|
| `transaction_id`           | Unique identifier for each transaction                                                        |
| `timestamp`                | ISO-format timestamp when the transaction occurred                                            |
| `sender_account`           | Account ID of the transaction initiator                                                      |
| `receiver_account`         | Account ID of the transaction recipient                                                      |
| `amount`                   | Transaction amount in USD                                                                    |
| `transaction_type`         | Type of transaction: deposit, withdrawal, transfer, or payment                               |
| `merchant_category`        | Business category involved (e.g., retail, utilities)                                         |
| `location`                 | Location from where the transaction was initiated                                            |
| `device_used`              | Device type used: mobile, web, ATM, POS                                                      |
| `is_fraud`                 | Boolean flag indicating whether the transaction was fraudulent                               |
| `fraud_type`               | Type of fraud (e.g., money_laundering, account_takeover); null if not fraudulent             |
| `time_since_last_transaction` | Hours since the user's previous transaction                                               |
| `spending_deviation_score` | Deviation from normal spending pattern (Gaussian-distributed)                                |
| `velocity_score`           | Number of transactions over a recent period (proxy for velocity-based fraud)                 |
| `geo_anomaly_score`        | Measure of unusual geographic transaction behavior (0-1)                                     |
| `payment_channel`          | Channel used: card, ACH, wire_transfer, UPI                                                  |
| `ip_address`               | Simulated IPv4 address of the transaction source                                             |
| `device_hash`              | Anonymized hash representing the user’s device fingerprint                                   |

## Usage

This dataset is ideal for:

- Training and evaluating fraud detection algorithms
- Feature engineering and model interpretability
- Benchmarking anomaly detection techniques

## License

Refer to the [Kaggle dataset page](https://www.kaggle.com/datasets/aryan208/financial-transactions-dataset-for-fraud-detection) for licensing and usage restrictions.

---

For questions or feedback, please open an issue or contact the dataset author via Kaggle.
