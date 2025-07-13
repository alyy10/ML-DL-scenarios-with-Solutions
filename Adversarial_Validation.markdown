# Adversarial Validation

## Question

Zoe is working on a machine learning project where her model is underperforming on the test data. She suspects the training and test datasets might have different distributions, so she uses adversarial validation to explore this possibility.

What's the correct way to set up adversarial validation?

1. Combine the training dataset (excluding the target variable) with the test dataset and assign a new binary target, with 1 for test samples and 0 for training samples.
2. Combine the training dataset (excluding the target variable) with the test dataset and assign a new binary target, with 0 for test samples and 1 for training samples.
3. Split the training dataset into two parts: one for training and one for validation. Assign a new binary target, with 1 for validation and 0 for training samples.
4. Split the test dataset into two parts and assign a new binary target to each split, with 1 for the first split and 0 for the second split.

## Solution and Background

### Adversarial Validation

Adversarial validation is a clever technique to help you understand why your machine learning model is not performing well on your test dataset. There are many sources of overfitting, but an important one is when your training and test data do not come from the same distribution.

Unfortunately, this is not an uncommon problem. For example, training a model with data collected during a period different from the test or production data could lead to poor performance. Even slight differences could considerably affect your results, but this is still an issue many people struggle to identify and decide how to better move forward.

That's where adversarial validation comes in.

### Is Your Data Identically Distributed?

Imagine you are training a model with data that significantly differs from the data used to evaluate the model's performance. You will not be surprised when your model makes wacky predictions! The model won't generalize to samples that are too far from the training data, so the results won't be good.

Fortunately, determining whether your splits come from the same distribution is not time-consuming; you can build a model to answer this question.

The intuition is simple: this model will never work if all data comes from the same distribution, but if there are differences between the training and test data, this model will learn to distinguish them.

That's the fundamental idea behind adversarial validation.

### Building the New Classifier

To understand whether your training and test splits are in good shape, you can take your training data, remove the target variable, and mix it with the test data. Then, you create a new binary target that differentiates training samples from test samples.

After preparing this new dataset, you can build a classification model to determine how easy it is to differentiate training samples from test samples.

Using a ROC curve, you can find out how easy it is for the binary model to classify the source of each sample. Ideally, you want the area under the curve to be around 0.5, which means the model can't tell both splits apart. As this area gets closer to 1.0, it is easier for the model to identify whether a particular instance comes from the training or the test set.

### Finding the Source of the Problem

Adversarial validation will help you understand whether there's a problem with your training and test splits, but that's not all: it will also help you find out what features are causing the issue.

You can list every feature and its importance in predicting whether a sample belongs to the training or test splits. The more predictive power, the more likely the variable contributes to the existing drift between training and test data.

You can use this list to investigate what specific characteristics in your data the model is using and find a way to eliminate them.

## Solution

Popular validation techniques, like cross-validation, allow you to test your models on unseen data if that data comes from the same distribution as your training dataset. Unfortunately, that's not always the case, and even slight differences between the training and test data will considerably affect the result of your model.

Adversarial validation is a technique to estimate the difference between your training and test data.

To set it up, you will create a new dataset by joining the training and test data. The target of that new dataset is a binary variable differentiating the training and test samples. You can determine how easy it is to separate both datasets by running a classifier on that new data.

Adversarial validation relies on computing the ROC-AUC, a graph showing the True Positive Rate and the False Positive Rate at different classification thresholds. The area under this curve (AUC) measures the model's performance. A perfect model will have an area of 1.0, while a model that only makes mistakes will have an area of 0.0.

If you run the classifier and the ROC-AUC is around 0.5, you will know that the training and test data are not easily distinguishable, which is good because it means the data comes from the same distribution. If the ROC-AUC is too high—closer to 1.0—the classifier can tell training and test data apart, which means they come from a different distribution.\
\
Correct options : 1 & 2