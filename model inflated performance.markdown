# model inflated performance

## Question

Skylar's model had the best performance in the entire class, but there was a problem: the results were too good to be correct.  
The professor decided to review her process step by step. Skylar stood in front of the class and wrote down her process:  

1. Skylar loaded the entire dataset in memory.  
2. Replaced one column's missing values with the mean of the column and scaled another column using Min-Max Scaling.  
3. She then split the dataset into a train and a test set.  
4. And finally, she trained her model.  

As soon as she finished, the professor knew what the issue was.  
Which of the following is the reason for the model's inflated performance?

## Options

- Skylar loaded the entire dataset in memory. She should have loaded it in batches.  
- Skylar transformed her data before splitting the dataset. She should have split the data before transforming it.  
- Skylar used the mean of the column to impute missing values. She should have used the median instead.  
- Skylar used Min-Max Scaling to transform one of the columns. She should have applied log transformation instead.

## Solution

**Correct Option: B**

## Explanation

A key principle in machine learning is that model performance estimates should reflect how well the model will generalize to new, unseen data. When results appear "too good to be true," it often signals an underlying issue like data leakage, which artificially inflates performance metrics.

In Skylar's case, the primary problem is **data leakage** through **train-test contamination**, a type of leakage where information from the test set inadvertently influences the training process. This occurs because Skylar performed data transformations—imputation of missing values using the column mean and Min-Max Scaling—on the entire dataset before splitting it into training and test sets. As a result, statistics derived from the test data (e.g., mean, minimum, and maximum values) "leak" into the training process, giving the model an unfair advantage and leading to overly optimistic evaluation results.

### Understanding the Transformations and Leakage
- **Imputation with Mean:** Replacing missing values with the mean of the entire column incorporates data from what will become the test set. During training, the model benefits from this "future" information, which wouldn't be available in a real-world scenario. This violates the isolation of the test set, meant to simulate unseen production data.
  
- **Min-Max Scaling:** This technique, also known as rescaling or min-max normalization, transforms features to a specified range (typically [0, 1]) using the formula:  
  \[
  x' = \frac{x - \min(x)}{\max(x) - \min(x)}
  \]
  where \( x \) is the original value, and \( \min(x) \) and \( \max(x) \) are computed from the entire dataset. By including test data in these calculations, Skylar leaks the distribution of the test set into the training data, allowing the model to "cheat" and achieve higher performance than it would on truly unseen data.

Both transformations rely on global statistics (mean, min, max) that should only be computed from the training data to prevent contamination. When applied prematurely, they expose the model to test set characteristics, resulting in a model that overfits the combined data and produces invalid, inflated performance estimates.

### Why Not the Other Options?
- **Option A (Loading the entire dataset in memory):** This is not inherently problematic for most datasets, especially if memory constraints aren't an issue. Batch loading is useful for very large datasets but doesn't cause data leakage or inflated performance here.
  
- **Option C (Using mean vs. median for imputation):** The choice between mean and median depends on data distribution (e.g., median is better for skewed data), but it's not the root cause of inflated performance. The issue is the timing of imputation, not the statistic used.
  
- **Option D (Min-Max Scaling vs. log transformation):** Log transformation might be suitable for certain distributions (e.g., to handle skewness), but again, the problem lies in when the scaling was applied, not the method itself.

### Correct Approach to Avoid Leakage
To fix this, Skylar should split the dataset into training and test sets first. Then:
1. Compute transformation parameters (e.g., mean for imputation, min and max for scaling) solely from the training set.
2. Apply these parameters to transform both the training and test sets.

This ensures the test set remains "unseen," providing a realistic evaluation of the model's generalization ability. Tools like scikit-learn's Pipeline can automate this process, fitting transformations on the training data and applying them consistently to the test data.

By addressing data leakage, Skylar's model performance will become more reliable and reflective of real-world applicability, aligning with the core goal of predictive modeling: accurate predictions on new data.