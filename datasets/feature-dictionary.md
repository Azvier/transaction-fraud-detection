# Feature Dictionary

This document provides a dictionary of the features created in the initial `financial_fraud_detection_dataset.csv` dataset and the `02-feature-engineering.ipynb` notebook.

## Original Features
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


## Engineered Features
| Feature Name | Description |
|---|---|
| **Temporal Features** | |
| `transaction_hour` | The hour of the day when the transaction occurred (0-23). |
| `transaction_day_of_week` | The day of the week when the transaction occurred (0=Monday, 6=Sunday). |
| `transaction_month` | The month of the year when the transaction occurred (1-12). |
| `is_weekend` | A binary flag indicating if the transaction occurred on a weekend (1 for weekend, 0 for weekday). |
| `hour_sin` | The sine transformation of the transaction hour, to capture cyclical patterns. |
| `hour_cos` | The cosine transformation of the transaction hour, to capture cyclical patterns. |
| `time_of_day` | Categorical feature indicating the time of day (morning, afternoon, evening, night). |
| **Interaction & Categorical Features** | |
| `ip_subnet` | The first two octets of the IP address, to identify transactions from the same network region. |
| `sender_receiver_pair` | A unique identifier for each sender-receiver pair. |
| `is_first_sender_receiver_tx` | A binary flag indicating if this is the first transaction between a specific sender and receiver. |
| `type_device_interaction` | An interaction feature combining the transaction type and the device used. |
| `channel_merchant_interaction` | An interaction feature combining the payment channel and the merchant category. |
| `is_first_transaction_for_account` | A binary flag indicating if this is the first-ever transaction for the sender's account. |
| `account_device_pair` | A unique identifier for each sender account and device pair. |
| `is_first_account_device_pair` | A binary flag indicating if this is the first time the sender is using a particular device. |
| `is_new_location` | A binary flag indicating if the transaction location is new for the sender. |
| **Rolling Window Aggregates** | |
| `sender_1h_transaction_count` | The number of transactions made by the sender in the past hour. |
| `sender_24h_transaction_count` | The number of transactions made by the sender in the past 24 hours. |
| `sender_7d_transaction_count` | The number of transactions made by the sender in the past 7 days. |
| `sender_24h_avg_amount` | The average amount of transactions made by the sender in the past 24 hours. |
| `account_24h_sum_amount` | The total sum of amounts of transactions made by the sender in the past 24 hours. |
| `account_24h_max_amount` | The maximum transaction amount for the sender in the past 24 hours. |
| `account_24h_std_amount` | The standard deviation of transaction amounts for the sender in the past 24 hours. |
| `receiver_24h_transaction_count` | The number of transactions received by the receiver in the past 24 hours. |
| `receiver_24h_unique_senders` | The number of unique senders to the receiver in the past 24 hours. |
| `receiver_24h_sum_amount` | The total sum of amounts received by the receiver in the past 24 hours. |
| `receiver_24h_max_amount` | The maximum transaction amount received by the receiver in the past 24 hours. |
| `device_account_count_24h` | The number of unique accounts that used a specific device in the past 24 hours. |
| `account_device_count_24h` | The number of unique devices used by the sender's account in the past 24 hours. |
| `sender_24h_unique_receivers` | The number of unique receivers the sender has transacted with in the past 24 hours. |
| `ip_24h_transaction_count` | The number of transactions from the same IP address in the past 24 hours. |
| `subnet_24h_transaction_count` | The number of transactions from the same IP subnet in the past 24 hours. |
| `subnet_24h_unique_accounts` | The number of unique accounts that made transactions from the same IP subnet in the past 24 hours. |
| `sender_1h_sum_amount` | The total sum of transaction amounts made by the sender in the past hour. |
| `merchant_historical_std_amount` | The historical standard deviation of transaction amounts for a specific merchant category. |
| `velocity_change_1h_vs_24h` | The ratio of the number of transactions in the last hour to the number of transactions in the last 24 hours for the sender. |
| **Expanding Window Features** | |
| `receiver_unique_sender_devices` | The expanding count of unique devices used by senders to a specific receiver. |
| `device_unique_accounts` | The expanding count of unique accounts that have used a specific device. |
| `ip_unique_accounts` | The expanding count of unique accounts that have used a specific IP address. |
| `avg_time_between_transactions` | The historical average time between transactions for the sender. |
| `merchant_historical_avg_amount` | The historical average transaction amount for a specific merchant category. |
| `account_historical_avg_amount` | The historical average transaction amount for the sender's account. |
| `account_historical_avg_hour` | The historical average transaction hour for the sender's account. |
| `account_historical_median_amount` | The historical median transaction amount for the sender's account. |
| `receiver_historical_avg_amount` | The historical average transaction amount received by the receiver. |
| `location_historical_fraud_rate` | The historical fraud rate for the transaction's location. |
| `account_high_first_digit_ratio` | The ratio of transactions with a high first digit (7, 8, or 9) for the sender's account. |
| `receiver_device_total_users` | The expanding count of unique users for the receiver's device. |
| **Amount-Based Features** | |
| `amount_vs_receiver_avg` | The ratio of the transaction amount to the receiver's historical average amount. |
| `amount_first_digit` | The first digit of the transaction amount. |
| `is_high_first_digit` | A binary flag indicating if the first digit of the amount is 7, 8, or 9. |
| `is_amount_round_100` | A binary flag indicating if the transaction amount is a round number (multiple of 100). |
| `is_amount_round_1000` | A binary flag indicating if the transaction amount is a round number (multiple of 1000). |
| `amount_cents` | The cent value of the transaction amount. |
| `has_cents` | A binary flag indicating if the transaction amount has a non-zero cent value. |
| `is_micro_transaction` | A binary flag indicating if the transaction amount is less than 1.00. |
| `amount_merchant_z_score` | The Z-score of the transaction amount relative to the merchant's historical average and standard deviation. |
| `amount_to_merchant_avg_ratio` | The ratio of the transaction amount to the merchant's historical average amount. |
| `amount_deviation_from_merchant_avg` | The difference between the transaction amount and the merchant's historical average amount. |
| `amount_vs_account_avg` | The ratio of the transaction amount to the sender's historical average amount. |
| `amount_vs_account_median_ratio` | The ratio of the transaction amount to the sender's historical median amount. |
| `amount_x_spending_deviation` | The product of the transaction amount and the spending deviation score. |
| `amount_x_velocity` | The product of the transaction amount and the velocity score. |
| `amount_ratio_1h_vs_24h` | The ratio of the sum of transaction amounts in the last hour to the sum in the last 24 hours for the sender. |
| `amount_deviation_from_account_avg` | The difference between the transaction amount and the sender's historical average amount. |
| `account_merchant_avg_spend` | The historical average spend for a specific sender-merchant pair. |
| `amount_vs_account_merchant_avg` | The ratio of the transaction amount to the historical average spend for that sender-merchant pair. |
| **Behavioral & Relational Features** | |
| `time_between_tx_std_24h` | The standard deviation of the time between transactions for the sender in the past 24 hours. |
| `time_since_last_tx_by_merchant` | The time since the last transaction by the same sender to the same merchant category. |
| `is_night_transaction` | A binary flag indicating if the transaction occurred during the night (1 AM to 5 AM). |
| `fan_out_ratio_24h` | The ratio of unique receivers to the number of transactions for the sender in the past 24 hours. |
| `fan_in_ratio_24h` | The ratio of unique senders to the number of transactions for the receiver in the past 24 hours. |
| `time_since_account_creation` | The time, in hours, since the sender's first transaction. |
| `sender_receiver_tx_count` | The cumulative number of transactions between the sender and receiver. |
| `is_first_tx_for_receiver` | A binary flag indicating if this is the first transaction ever received by the receiver. |
| `time_since_receiver_creation` | The time, in hours, since the receiver's first transaction. |
| `relationship_duration_hours` | The duration of the relationship between the sender and receiver, in hours. |
| `time_since_last_vs_avg_ratio` | The ratio of the time since the last transaction to the sender's average time between transactions. |
| `sender_new_receiver_count_24h` | The number of new receivers the sender has transacted with in the past 24 hours. |
| `hour_deviation_from_avg` | The absolute difference between the transaction hour and the sender's historical average transaction hour. |
| `geo_x_spending_deviation` | The product of the geo-anomaly score and the spending deviation score. |
| `sender_receiver_device_same` | A binary flag indicating if the sender's device is the same as the receiver's last known device. |
| `is_shared_device_receiver` | A binary flag indicating if the receiver has used the sender's device in the past. |
| **Frequency Encoded Features** | |
| `type_device_interaction_freq_encoded` | The frequency-encoded value of the `type_device_interaction` feature. |
| `channel_merchant_interaction_freq_encoded` | The frequency-encoded value of the `channel_merchant_interaction` feature. |
| `location_freq_encoded` | The frequency-encoded value of the `location` feature. |
| `merchant_category_freq_encoded` | The frequency-encoded value of the `merchant_category` feature. |
| `ip_subnet_freq_encoded` | The frequency-encoded value of the `ip_subnet` feature. |
