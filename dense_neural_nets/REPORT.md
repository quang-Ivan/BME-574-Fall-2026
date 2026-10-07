1. **What is your track, and what is the bar?** Name the dataset, the number of rows, features and classes, and the two baselines with their accuracy *and* macro-F1.

   We used track A, the thyroid dataset. This dataset has 7200 rows, with 21 features per row, and three classes. The two baselines are the majority-class rule (where the model picks the majority class every time) and the straight-boundary model (a straight cut in feature space).

   - The majority-class rule: accuracy of 0.9256, macro-F1 of 0.3204

   - The straight-boundary model: accuracy of 0.9556, macro-f1 of 0.7566

2. **Did the network beat the straight-boundary model?** Quote the mean over three seeds and the spread. If the margin is smaller than the spread, say so — that is a finding, not a failure.

   The mean accuracy across 3 seeds of the neural network is 0.9898, with a spread of 0.0022, and the mean macro F1 score is 0.9509, with a spread of 0.0112. The network beats the straight-boundary model: the margins are 0.0343 for accuracy and 0.1943 for macro-F1, both larger than the corresponding spreads.

3. **Where do the errors go?** Use the confusion matrix and the per-class recalls. Which class is the model worst at, and is that the class it would matter most to get right?

   The unweighted model has the worst recall rate for the hypothyroidism class (0.880), and while it is a priority class (it is not the healthy class), hyperthyroidism is the smallest class.

4. **How much would a careless split have flattered you?** Quote both numbers from Figure 3 and the fraction of subjects that appear on both sides. Explain in one sentence *why* the effect is the size it is on your data.

   In our track, each patient only had one row, so there was no major difference between the different splitting methods: there was no opportunity for the model to recognise the same patient across the training and test sets.

   Subject-wise accuracy: 0.9898; random-row accuracy: 0.9906; subject overlap: 0/7200 (0%).

5. **What did class weighting cost and buy?** Give the before/after recall for the rarest class and the change in overall accuracy. State which you would ship and why.

   There was no change seen in recall for the rarest class (hyperthyroidism, 0.976 → 0.976) and the overall accuracy dropped to 0.9806 from 0.9906. However, the second rarest class (hypothyroidism) had a large increase in recall (0.880 → 0.957). As this is also a disease case, and there was no change to the other disease case, we would ship the class weighted model.

6. **What would you do with another two weeks?** One concrete, specific thing — not "try a bigger network".

   Given two more weeks, we would do more cross-validation within the training set. We could try different weighting parameters to see if they improve hypothyroid recall and reduce the loss in macro-F1.
