1. **What is your track, and what is the bar?** Name the dataset, the number of rows, features and classes, and the two baselines with their accuracy *and* macro-F1.

   We used track A, the thyroid dataset: 7200 rows, 21 features, and three classes (normal, hypothyroid, and hyperthyroid). The two baselines are the majority-class rule and multinomial logistic regression (the straight-boundary model). Normal records account for 92.6% of the data, so accuracy alone can hide missed disease cases.

   - The majority-class rule: accuracy of 0.9256, macro-F1 of 0.3204

   - The straight-boundary model: accuracy of 0.9556, macro-f1 of 0.7566

2. **Did the network beat the straight-boundary model?** Quote the mean over three seeds and the spread. If the margin is smaller than the spread, say so — that is a finding, not a failure.

   The mean accuracy across seeds 0, 1, and 2 of the neural network is 0.9898, with a spread of 0.0022, and the mean macro-F1 score is 0.9509, with a spread of 0.0112 (spread = maximum minus minimum across seeds). The network beats the straight-boundary model: the margins are 0.0343 for accuracy and 0.1943 for macro-F1, both larger than the corresponding spreads.

3. **Where do the errors go?** Use the confusion matrix and the per-class recalls. Which class is the model worst at, and is that the class it would matter most to get right?

   The unweighted seed-0 model has the worst recall for hypothyroidism (81/92 = 0.880). Figure 2 shows that 10 hypothyroid cases were predicted as normal and one as hyperthyroid. Missing disease cases would matter in screening, even though hyperthyroidism is the smallest class.

4. **How much would a careless split have flattered you?** Quote both numbers from Figure 3 and the fraction of subjects that appear on both sides. Explain in one sentence *why* the effect is the size it is on your data.

   According to the bundle, each patient contributes one row, so a random-row split cannot put multiple records from the same patient into both sets. The subject identifiers are row indices, so zero overlap alone does not independently verify patient identity.

   Figure 3 accuracy: bundle split, 0.9898 (three-seed mean); random-row split, 0.9906 (seed 0); subject overlap, 0/7200 (0%). The small gap is below the 0.0022 seed spread and does not demonstrate leakage inflation.

5. **What did class weighting cost and buy?** Give the before/after recall for the rarest class and the change in overall accuracy. State which you would ship and why.

   With seed 0 for both models, recall for the rarest class (hyperthyroidism) stayed at 0.976, while hypothyroidism recall improved from 0.880 to 0.957. The cost was lower normal recall (0.997 → 0.982), accuracy (0.9906 → 0.9806, a 1.00-percentage-point drop), and macro-F1 (0.9564 → 0.9111). We would ship the weighted model for a screening task in which avoiding missed hypothyroid cases is prioritized over the additional false positives.

6. **What would you do with another two weeks?** One concrete, specific thing — not "try a bigger network".

   Given two more weeks, we would use stratified five-fold cross-validation within the training set to compare no weighting, square-root inverse-frequency weighting, and inverse-frequency weighting. Each fold would fit its scaler and calculate class weights using that fold's training rows only. We would compare hypothyroid recall, normal recall, and macro-F1, and select the weighting scheme without using the test set.
