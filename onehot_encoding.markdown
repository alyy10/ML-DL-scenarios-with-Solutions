# One-Hot Encoding

## Question
In developing a machine learning model, a significant portion of the work is done before the training begins. Giuliana knows that she must prepare her data before it can be used. She has been considering encoding some of the features in her dataset. One-Hot Encoding appears to be a suitable option. It's been a long time since Giuliana used One-Hot Encoding, and she could use some guidance. Which of the following statements accurately describes how One-Hot Encoding functions?

- One-Hot Encoding transforms a numerical feature into its categorical equivalent.
- One-Hot Encoding converts a string-encoded feature into its numerical equivalent.
- One-Hot Encoding changes a string-encoded feature into its categorical equivalent.
- One-Hot Encoding generates additional features based on the number of unique values in a categorical feature.

## Solution
The correct answer is: **One-Hot Encoding generates additional features based on the number of unique values in a categorical feature.**

## Explanation
One-Hot Encoding is a technique used to convert categorical data into a numerical format that machine learning algorithms can understand. Categorical data are variables with label values, like "red," "blue," or "green" for a color feature, instead of numbers. Since most machine learning models work with numerical data, we need to transform these labels.

Here's how One-Hot Encoding works in simple terms:
- For a categorical feature (e.g., "color" with values "red," "blue," "green"), One-Hot Encoding creates a new binary column for each unique value.
- Each column represents one category, and for each data point, the corresponding column gets a `1` (if the category is present) or a `0` (if it’s not).
- For example, if a data point has the color "blue," the "blue" column will have a `1`, while the "red" and "green" columns will have `0`.

This process expands the dataset by adding new columns (features) based on the number of unique categories in the original feature. It ensures that the model can process categorical data without assuming any numerical relationship between the categories (e.g., "red" is not "less than" or "greater than" "blue").