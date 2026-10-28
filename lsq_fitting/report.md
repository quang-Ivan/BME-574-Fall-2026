## 1. What model are you fitting, and what does each parameter mean physically? Give units.

We’re fitting a double exponential function ($A{e}^{-\alpha t}+B{e}^{-\beta t}$) to the “indometh” data package. A and B have units of concentration and α and β have units of hr<sup>-1</sup>. A + B is the total starting concentration, with A/(A+B) eliminated through method one, and B/(A+B) the proportion eliminated through method two. α is the decay rate constant for elimination method 1 (possibly urinary excretion), and β is the decay rate constant for elimination method 2 (possibly fecal excretion).

## 2. Did your fitter agree with `lmfit`, and did both agree with the certified warm-up values? Give the numbers.

Our fitter is better than `lmfit` on the warmup track bundle. The maximum relative error of the self-written LM compared with the reference value is approximately $1.15\times10^{-10}$, while that of `lmfit` is approximately $3.1\times10^{-6}$, and the RSS is approximately 1168.00888.

## 3. Report your parameters with uncertainties. Say where the uncertainty came from and what assumption it rests on.

- A had values of 2.029278, 2.827672, 5.468324, 2.198135, 3.566102, 3.002251 with respective standard errors of 0.109903, 0.439089, 1.590691, 0.189357, 0.291842, 0.160278.

- B had values of 0.110626, 0.346163, 0.238664, 0.223075, 0.143164, 0.132924 with respective standard errors of 0.110626, 0.346163, 0.238664, 0.223075, 0.143164, 0.132924.

- Alpha had values of 1.784949, 2.228474, 5.753429, 1.274189, 2.831382, 2.968967 with respective standard errors of 0.2225  , 0.763522, 1.51663 , 0.185663, 0.416725, 0.348319.

- Finally, Beta had values of 0.167331, 0.194883, 0.662192, 0.201351, 0.221606, 0.417641 with respective standard errors of 0.13171 , 0.176919, 0.094337, 0.178696, 0.142148, 0.051897.

The standard error was calculated from the square root of the diagonal of the covariance matrices for the four fitting parameters in each of the six subjects. This assumes symmetric, gaussian, distribution of the error about the parameters.

## 4. Which parameters are poorly determined, and how do you know? Point at the correlation block, the error bars in Figure 3, or the multi-start result.

- Some of the parameters are poorly determined, but overall the model seems good. The multi-start result yielded the same values for all starts for all subjects, which would not be the case with poorly determined parameters because it would yield divergent results.

- In Figure 3, each parameter has subjects for which the error bars do not reach the mean of other subjects, or do not overlap at all. This further suggests that the differences are not due to uncertainty in the data but rather differences in biology.

- Further, looking at the correlation block of fit report between different parameters for each replicate, only one of the values exceed 0.95, that being the correlation between B and beta on the fourth replicate (0.9641). All others are sufficiently low.

- In general B and beta are the most poorly determined. The RSE for A, Alpha, B, Beta are 5.3%-29.1%, 11.7%-34.3%, 13.7%-87.6%, 12.4%-90.8%.

## 5. Did the multi-start find more than one answer? If yes, say what distinguishes them and which you would report. If no, say that.

No, the multistart found the same answer every time. This indicates that the parameters are well-distinguished.

## 6. What would make these estimates trustworthy enough to use? More sampling times? A different experiment design? Fixing a parameter from prior knowledge? Be concrete.

From a brief look at what is already known about the elimination of indomethicin the elimination halflife seems a bit too quick (average is between 2.6 and 11 hours while the six subjects show elimation half-lives of rougly 1 hour). However, given how large of range that average is the fast elimation times that we are seeing are possible. Looking specifically at the residuals, they seem to be high at low timepoints for each replicate; it seems like the experimental design attempted to mitigate this by sampling more frequently at low time points than at higher timepoints, but this issue is somewhat inherent to the steep slope at the beginning of any exponential decay curve. More data points per replicate would decrease the uncertainty in the parameters for the per-replicate fits, and more replicates would give better confidence regarding the spread of the parameters within the population.
