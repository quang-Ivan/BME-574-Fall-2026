1. What is one row of your matrix, and what are you predicting? Two sentences. Name the clinical or physiological decision your label stands in for.
   - Each row of the matrix is a pattern over the features, and the prediction entails how much that pattern is present in each new image. If there are features correlated with penumonia, we are essentially trying to calculate the extent to which that pneumonia-correlated feature is present. 
3. What do the first three components look like? Caption each from Figure 2. If a component is brightness, position, or some other nuisance, say so — that is a finding, not a failure.
   - A
4. What k would you use and why? Point at Figure 3. "The highest one" is not a reason; "accuracy plateaus after k=12 and smaller is cheaper and less prone to overfitting" is.
   - A
5. How does your result compare to all three baselines? Give the four numbers. If the no-SVD baseline ties you, say what the decomposition bought you instead.
   - A
6. Where could this pipeline have cheated, and how do you know it did not? Name the specific line where mu and Vt were fitted, and say which rows they saw.
   - A
7. What would you need to trust this clinically? One paragraph. More subjects? Better labels? A different target? Be concrete.
   - A