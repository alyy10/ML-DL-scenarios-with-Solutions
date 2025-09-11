# F1score

## Question

Parker works at a drink factory concerned with classifying defects as bottles come out of the line. She built a computer vision model to classify bottles into three classes: "ready," "almost ready," and "waste."  
Most of the bottles that come out are "ready," and there are only a few samples that classify as "almost ready" or "waste." Parker is very aware of this imbalance.  
The factory uses Parker's model to reduce the number of defective bottles that ship to customers (any bottle that's not "ready" is defective.) They consider each of the three classes equally important and wants to ensure the evaluation process reflects that.  
Which metric should Parker use to evaluate her model?

- The accuracy of the model.  
- The Micro-average F1-Score of the model.  
- The Macro-average F1-Score of the model.  
- The Weighted F1-Score of the model.

## Solution

**Correct Option: C**

## Explanation

Parker’s task involves a multi-class classification problem with a significant class imbalance, where "ready" bottles dominate the dataset, while "almost ready" and "waste" are minority classes. The factory’s goal is to minimize defective shipments (non-"ready" bottles), and they emphasize that all three classes—"ready," "almost ready," and "waste"—are equally important. This context requires a careful choice of evaluation metric to ensure fairness across classes and relevance to the business objective.

- **Option A: The accuracy of the model**  
  This is incorrect. Accuracy measures the proportion of correctly classified instances out of the total. In an imbalanced dataset where "ready" bottles make up the majority (e.g., 99%), a model that always predicts "ready" could achieve high accuracy (e.g., 99%) while completely missing "almost ready" and "waste" bottles. As highlighted in the "When accuracy doesn't help" resource, accuracy is unreliable for imbalanced problems because it favors the majority class and fails to reflect performance on minority classes critical to the factory’s defect reduction goal.

- **Option B: The Micro-average F1-Score of the model**  
  This is incorrect. The Micro-average F1-Score aggregates contributions from all classes by summing true positives, false positives, and false negatives across the dataset, effectively aligning with overall accuracy. As noted in the "Micro, Macro & Weighted Averages of F1 Score" article, in multi-class settings with single-label predictions, Micro-average F1-Score equals accuracy. This means it suffers from the same limitation as accuracy in imbalanced scenarios, overemphasizing the majority "ready" class and not addressing the equal importance of all classes as required by the factory.

- **Option C: The Macro-average F1-Score of the model**  
  This is correct. The Macro-average F1-Score computes the arithmetic mean of F1 scores for each class, treating all classes equally regardless of their support (number of instances). According to the "Micro, Macro & Weighted Averages of F1 Score" resource, this method is ideal when all classes are equally important, as it penalizes poor performance on minority classes ("almost ready" and "waste") just as much as on the majority class ("ready"). For Parker’s case, where the factory values all classes equally to ensure no defective bottles are missed, the Macro-average F1-Score provides a balanced evaluation. It aligns with the confusion matrix’s detailed breakdown of per-class performance (as described in the "Confusion Matrix" resource), ensuring the model’s ability to classify all categories is fairly assessed.

- **Option D: The Weighted F1-Score of the model**  
  This is incorrect. The Weighted F1-Score calculates the mean of per-class F1 scores, weighted by the support of each class. This approach gives more influence to the majority class ("ready") due to its higher number of instances, as explained in the "Micro, Macro & Weighted Averages of F1 Score" article. Since the factory considers all classes equally important, weighting by support would skew the metric toward "ready" and undervalue performance on "almost ready" and "waste," which are critical for defect detection.

### Conclusion
Given the imbalanced dataset and the factory’s requirement to treat all classes equally, Parker should use the **Macro-average F1-Score**. This metric ensures that the model’s performance on "almost ready" and "waste" (minority but critical classes) is not overshadowed by the majority "ready" class, providing a fair and comprehensive evaluation. To implement this, Parker can leverage tools like scikit-learn’s classification_report, setting the average parameter to "macro," and complement it with a confusion matrix to visualize per-class performance and guide model improvements.