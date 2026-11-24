# Who Has a Bank Account? Predicting Financial Inclusion Across Countries

Blog post: [Richer Does Not Always Mean More Banked: What 161 Countries Show](https://gbmaxwell.medium.com/richer-does-not-always-mean-more-banked-what-161-countries-show-ff0458d469b8)

## Motivation

An account at a bank or a mobile money provider is the entry point to saving, borrowing and getting paid. This project uses World Bank data to look at where account ownership is low, what goes with it, and how well it can be predicted from indicators that are published every year. It was completed for the Udacity Data Scientist Nanodegree and follows the CRISP-DM process.

The project answers five questions:

1. How has account ownership changed between 2011 and 2024, and how do world regions differ?
2. Which country characteristics are most strongly related to account ownership?
3. How accurately can a model predict account ownership, and which features does it rely on most?
4. Which countries have many more, or many fewer, account owners than their income level predicts?
5. What does the model predict for a typical lower middle income country if internet use rises?

## Libraries

Python 3.10 with:

* pandas
* numpy
* scikit-learn
* matplotlib
* seaborn

The notebook downloads the data with the Python standard library (`urllib`), so no extra package is needed.

## Files

| File | Description |
|---|---|
| `bank_account_ownership.ipynb` | The full analysis: data gathering, assessment, cleaning, the five questions, the models and the conclusions. |
| `data/raw_worldbank_indicators.csv` | The thirteen World Bank indicators as downloaded, one row per country and year (2010 to 2024). |
| `data/raw_worldbank_countries.csv` | The World Bank country list with region and income group. |
| `data/clean_account_ownership.csv` | The cleaned table used in the analysis: 705 rows, 161 countries. |
| `README.md` | This file. |

The notebook reuses the files in `data` when they are present. Delete the folder to download the current data from the World Bank API.

## Summary of results

* The median country went from 37.0% of adults with an account in 2011 to 72.8% in 2024. Sub-Saharan Africa (17.3% to 55.6%) and South Asia (33.5% to 70.8%) gained the most.
* GDP per capita (Spearman correlation 0.81) and internet use (0.80) have the strongest relationship with account ownership. Mobile subscriptions (0.52) and bank branches (0.54) are only moderately related.
* A model using twelve indicators, the survey year and region predicts account ownership in countries it has never seen with an R squared of about 0.77 and a typical error of 11 percentage points, against 27 points for a baseline. A linear regression performs as well as a random forest.
* Income does not settle the outcome. In 2024 Kenya, India and Mongolia were more than 30 points above what their income suggests, and Lebanon, Iraq and Libya more than 30 points below.
* Raising internet use from 41.5% to 80% in a typical lower middle income country in Sub-Saharan Africa moves the prediction by 2 to 10 points, depending on the model.

All results are associations between country level figures. They do not show cause and effect.

## Acknowledgements

* Data: [World Bank Databank](https://databank.worldbank.org/) and the Global Findex Database, accessed through the World Bank API.
* The project brief and rubric come from the Udacity Data Scientist Nanodegree.
* scikit-learn documentation for the pipeline, grouped cross-validation and permutation importance tools.
