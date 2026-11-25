# AurumSignal-ML | Gold Price Movement Classification

Can recent price movements help predict whether one gram of gold will rise in Turkish lira at the next recorded observation? This project trains Logistic Regression and Random Forest classifiers and compares them with a baseline that always predicts a rise.

## Dataset and method

- Dataset: [Turkey Gram Gold Prices (2020–2025) on Kaggle](https://www.kaggle.com/datasets/abdullahaydnn/turkey-gram-gold-prices-20202025)
- Coverage: 1,279 observations from January 31, 2021 to June 30, 2025.
- Target: `1` if the next recorded price rises, `0` if it falls or stays flat.
- Features: one-record return, five-record return, and percentage deviation from the ten-record moving average.
- Chronological split: 1,014 training records and 254 test records. One record was excluded at the boundary because its label depends on the first test price.

## Test results

| Method                 | Correct predictions | Accuracy | Balanced accuracy |
| ---------------------- | ------------------: | -------: | ----------------: |
| Always predicts a rise |             148/254 |   58.27% |            50.00% |
| Logistic Regression    |             148/254 |   58.27% |            50.00% |
| Random Forest          |             150/254 |   59.06% |            52.28% |

Random Forest identified 138 of 148 rises and 12 of 106 flat or falling observations. It made two more correct predictions than the baseline during this test period.

## Run the notebook

1. Download the CSV from Kaggle and save it as `Data/gold_try.csv`.
2. Create and activate a Python virtual environment. The project was developed with Python 3.14.7.
3. Run `python -m pip install -r requirements.txt`.
4. Open `gold_price_prediction_final.ipynb` in VS Code, select the environment as the kernel, and choose **Run All**.

## Author

Mehmet Ali Külek
Ahmet Nazlan
