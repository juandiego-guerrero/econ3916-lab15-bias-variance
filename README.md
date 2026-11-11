# econ3916-lab15-bias-variance
Lab 15 submission

# The Bias-Variance Tradeoff: Choosing How Flexible a Model Should Be

## Objective
I used a simulated world with a known true curve to see how bias, variance and model selection decide how flexible a polynomial model should be.

## Methodology
- Simulated data from a known truth, y = sin(1.4x) + 0.25x plus noise with standard deviation 0.45, and drew one training sample of 60 points.
- Split the error of polynomial fits into bias squared and variance by fitting 200 fresh samples of 60 points at each of six degrees (1, 2, 3, 5, 9 and 15) and comparing the predictions with the truth at 40 fixed x values.
- Fit degrees 1 to 15 to the 60 training points and scored each fit twice: on the same 60 points (training error) and on 2,000 new points from the same world (held-out error).
- Chose a degree by 5-fold cross-validation on the 60 points alone, and recorded how much the error varied from fold to fold.
- Used nested cross-validation, with an outer loop for scoring and an inner loop for choosing the degree, to check whether the smallest CV error is a fair estimate of the error on new data.
- Wrote a function, `kfold_mse()`, that gives the k-fold CV error for any degree and number of folds, checked it against the 5-fold results, and used it to rerun the comparison of degrees 4 and 5 with 10 folds.

## Key Findings
- Bias squared fell sharply as the degree rose and stopped near zero from degree 9 on. Variance was roughly flat at low degrees and then climbed: [YOUR VALUE] at degree 5 and [YOUR VALUE] at degree 15.
- Training error fell at every step as the degree rose, so it could not tell me where to stop. Held-out error was lowest at degree [YOUR VALUE] and rose after that.
- 5-fold CV chose degree [YOUR VALUE], with a CV MSE of [YOUR VALUE]. The fold-to-fold spread was small at degrees 4 and 5 and much larger at every other degree.
- The nested CV estimate was [YOUR VALUE], higher than the smallest CV MSE. Picking the minimum of several noisy CV errors gives an estimate that is too optimistic.
- With 10 folds, the CV MSE was [YOUR VALUE] for degree 4 and [YOUR VALUE] for degree 5.
- (Challenge) Held-out error past the interpolation point: [YOUR RESULT]
