
# Evaluation metrics

**Question**

Kira has been assigned a new project at her job, where she needs to design an object detection model to identify different types of birds from various camera trap images.

She wants to build a versatile model that can be adapted and used across different tasks in the future.

However, to do so, Kira needs an effective way to evaluate her model's performance, enabling her to compare various versions of her model and choose the most efficient one.

Which evaluation metrics should Kira use to evaluate her model?

1) ROC Curve 
2) Precision-Recall Curve 
3) Recall 
4) F1 score

**Solution**

The recall is a beneficial metric for object detection, but it doesn't provide Kira with a comprehensive view of her model's performance unless combined with precision. A model might have high recall but poor precision, which would not serve Kira's purpose well. Hence, recall alone isn't the most suitable metric for her.

An issue with ROC Curves for object detection tasks is that they require a concept of True Negatives for the computation of False Positive Rate, which is one of the axes of the ROC curve. However, in object detection, the number of bounding boxes that don't contain an object of interest is too large to compute True Negatives accurately. Therefore, ROC curves are not typically used in such scenarios.

Kira should consider using a Precision-Recall Curve. Similar to the ROC curve, the Precision-Recall curve doesn't depend on True Negatives. It uses the model's precision, making it more suitable for her object detection task.

Lastly, calculating the F1-score is another excellent option for Kira. It considers both the precision and recall of the model, providing a balanced measure of its performance.

**Correct answer:** Precision-Recall Curve , F1-score
