# AurumSignal-ML | Gold Price Movement Classification

Can recent price changes help predict whether one gram of gold in Turkish lira will rise at the next recorded observation? We trained Logistic Regression and Random Forest classifiers and compared them with a baseline that always predicts a rise.

[Open the notebook](gold_price_prediction_final.ipynb) · [View the dataset](Data/gold_try.csv)

## Dataset and method

- Source: [Turkey Gram Gold Prices (2020–2025) on Kaggle](https://www.kaggle.com/datasets/abdullahaydnn/turkey-gram-gold-prices-20202025)
- Coverage: 1,279 observations from January 31, 2021 to June 30, 2025.
- Target: `1` if the next recorded price rises and `0` if it falls or stays flat.
- Model inputs: percentage change since the previous record, percentage change since five records ago, and percentage distance from the ten-record moving average.
- Evaluation: 1,014 older observations were used for training and 254 newer observations for testing. One record between the two periods was excluded because its target depends on the first test price.

## Test results

| Method                 | Correct predictions | Accuracy | Balanced accuracy |
| ---------------------- | ------------------: | -------: | ----------------: |
| Always predicts a rise |             148/254 |   58.27% |            50.00% |
| Logistic Regression    |             148/254 |   58.27% |            50.00% |
| Random Forest          |             150/254 |   59.06% |            52.28% |

Of the 254 test observations, 148 rose and 106 fell or stayed flat. Logistic Regression predicted a rise every time. Random Forest correctly identified 138 rises and 12 flat or falling prices. It caught 12 movements the baseline missed, but missed 10 rises itself. The net gain was two correct forecasts.

The notebook ends with eight examples showing the model's forecast, the next recorded price, the actual movement, and whether the forecast was correct.

## Run the notebook

1. Clone or download this repository. The dataset is included at `Data/gold_try.csv`.
2. Create and activate a Python virtual environment. The project was developed with Python 3.14.7.
3. Run `python -m pip install -r requirements.txt`.
4. Open `gold_price_prediction_final.ipynb` in VS Code, select the environment as the notebook kernel, and choose **Run All**.

## Authors

- Mehmet Ali Külek
- Ahmet Nazlan
