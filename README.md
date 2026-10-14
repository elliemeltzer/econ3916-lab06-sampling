# Sampling for Machine Learning — Train-Test Splits

## Objective

I examined how sampling design and data leakage affect the reliability of machine-learning evaluation and population estimates.

## Methodology

- I explored survival outcomes for 891 Titanic passengers.
- I compared naive and stratified train-test splits.
- I checked survival and passenger-class shares across the training and test sets.
- I identified leakage caused by fitting a scaler before splitting the data.
- I corrected scaling and missing-value imputation by fitting each preprocessing step only on the training rows.
- I wrote a `split_by_share()` function and checked it against the lab’s original split.
- I simulated biased and random election samples from a population of 10 million voters.
- I repeated the comparison 100 times and calculated the data defect correlation.

## Key Findings

The stratified split kept the survival rate at approximately 0.406 in both the training and test sets. The naive test set had a lower survival rate of 0.392 and contained a larger share of third-class passengers.

The simulated biased survey collected 4,382,503 responses but overestimated the target outcome by 8.3 percentage points. A random sample of only 50,000 observations produced an error of approximately 0.2 percentage points.

The biased sample’s data defect correlation was 0.1475. Its large size produced a precise but consistently incorrect result, showing that sample design can matter more than sample size.

I also found that preprocessing must be learned only from training data. Allowing test rows to influence scaling or imputation makes the evaluation less independent and can produce misleading performance estimates.
