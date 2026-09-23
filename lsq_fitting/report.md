## 1. What model are you fitting, and what does each parameter mean physically? Give units.

We’re fitting a double exponential function ($A{e}^{-\alpha t}+B{e}^{-\beta t}$) to the “synthetic” data package. A and B have units of concentration and α and β have units of hr<sup>-1</sup>. A + B is the total starting concentration, with A/(A+B) eliminated through method one, and B/(A+B) the proportion eliminated through method two. α is the decay rate constant for elimination method 1, and β is the decay rate constant for elimination method 2.

## 2. Did your fitter agree with `lmfit`, and did both agree with the certified warm-up values? Give the numbers.

Our fitter is better than `lmfit` on the warmup track bundle. The maximum relative error of the self-written LM compared with the reference value is approximately $1.15\times10^{-10}$, while that of `lmfit` is approximately $3.1\times10^{-6}$, and the RSS is approximately 1168.00888.

## 3. Report your parameters with uncertainties. Say where the uncertainty came from and what assumption it rests on.

- A had values of 2.605874, 2.693719, 2.473755, 2.496646 with respective standard errors of 0.044307, 0.064591, 0.069073, 0.067334.

- B had values of 0.706232, 0.854399, 0.792167, 0.799829 with respective standard errors of 0.044293, 0.063935, 0.069612, 0.068537.

- Alpha had values of 1.902263, 2.296129, 2.036828, 2.057097 with respective standard errors of 0.067116, 0.122987, 0.120524, 0.11728.

- Finally, Beta had values of 0.128737, 0.156231, 0.145002, 0.153759 with respective standard errors of 0.011266, 0.015463, 0.016855, 0.016891

The standard error was calculated from the square root of the diagonal of the covariance matrices for the four fitting parameters in each of the four replicates. This assumes symmetric, gaussian, distribution of the error about the parameters.

## 4. Which parameters are poorly determined, and how do you know? Point at the correlation block, the error bars in Figure 3, or the multi-start result.

- None of the parameters are poorly defined, for several reasons. The multi-start result yielded the same values for all starts for all replicates, which would not be the case with poorly determined parameters because it would yield divergent results.

- In Figure 3, each parameter has replicates for which the error bars do not reach the mean of other replicates, or do not overlap at all. This further suggests that the differences are not due to uncertainty in the data but rather differences in biology.

- Further, looking at the correlation block of fit report between different parameters for each replicate, none of the values exceed 0.95, with the highest being 0.8833.

- The RSE for A, Alpha, B, Beta are 1.7%-2.8%, 3.5%-5.9%, 6.3%-8.8%, 8.8%-11.6%.

## 5. Did the multi-start find more than one answer? If yes, say what distinguishes them and which you would report. If no, say that.

No, the multistart found the same answer every time. This indicates that the parameters are well-distinguished.

## 6. What would make these estimates trustworthy enough to use? More sampling times? A different experiment design? Fixing a parameter from prior knowledge? Be concrete.

It is unclear what mechanism is being fitted, without any prior knowledge about this experiment, it is difficult to say whether or not these estimates are trustworthy. Looking specifically at the residuals, they seem to be high at low timepoints for each replicate; it seems like the experimental design attempted to mitigate this by sampling more frequently at low time points than at higher timepoints, but this issue is somewhat inherent to the steep slope at the beginning of any exponential decay curve. More data points per replicate would decrease the uncertainty in the parameters for the per-replicate fits, and more replicates would give better confidence regarding the spread of the parameters within the population.
