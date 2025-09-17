# evaluating model

## Question

Brielle wants to build a machine learning model that will use traffic violations to predict how to distribute the city's police force.  
She wants the model to predict the areas where new violations are likely to occur so the department can reinforce the security around those streets.  
Which of the following is a potential problem that Brielle should consider?

- There won't be any reliable way to evaluate this model.  
- The model may suffer from survivorship bias.  
- The model may suffer from decline bias.  
- The model may create a positive feedback loop.

## Solution

**Correct Option: D**

## Explanation

Brielle’s goal is to develop a machine learning model to predict traffic violation hotspots, enabling strategic police deployment to enhance security. Given the real-world application and the dynamic nature of traffic patterns, selecting an appropriate evaluation metric and anticipating potential pitfalls are crucial. Let’s analyze each option to identify the most significant challenge.

- **Option A: There won't be any reliable way to evaluate this model.**  
  This is incorrect. Brielle can employ a supervised learning approach, where historical traffic violation data serves as the training set with known outcomes (e.g., violation locations and times). Standard evaluation methods, such as accuracy, precision, recall, or the F1-score (as outlined in resources like "When accuracy doesn't help" from Bnomial), can be used to assess the model’s predictive performance. By splitting the data into training and test sets and using metrics tailored to the imbalance of violation occurrences, Brielle can reliably evaluate the model’s effectiveness, making this option invalid.

- **Option B: The model may suffer from survivorship bias.**  
  This is incorrect. Survivorship bias occurs when analysis focuses only on surviving or successful outcomes, ignoring those that failed (e.g., analyzing only surviving companies in a market study). In Brielle’s case, the model uses historical violation data, which includes all reported incidents regardless of whether they led to enforcement actions or resolutions. There’s no indication that the dataset excludes unreported or unaddressed violations in a way that would skew the analysis, so this bias is not a primary concern based on the problem statement.

- **Option C: The model may suffer from decline bias.**  
  This is incorrect. Decline bias refers to a tendency to perceive current conditions as worse than the past due to change, often seen in subjective comparisons over time. Brielle’s model is a predictive tool based on data-driven patterns (e.g., violation locations), not a comparative analysis of past versus present policing effectiveness. The problem description does not suggest a reliance on historical decline perceptions, rendering this bias irrelevant to the model’s design or evaluation.

- **Option D: The model may create a positive feedback loop.**  
  This is correct. A positive feedback loop occurs when the model’s predictions influence the system in a way that reinforces the initial data, amplifying the issue. In Brielle’s scenario, if the model identifies high-violation areas and prompts increased police patrols there, more violations are likely to be detected and reported in those areas due to heightened enforcement (as noted in the provided solution). Meanwhile, areas with less patrolling may underreport violations, skewing future data. Over time, the model will prioritize already heavily patrolled zones, neglecting others where violations might be occurring but going unnoticed. This self-reinforcing cycle could exacerbate resource allocation imbalances, making it a critical problem Brielle must address, potentially through techniques like data regularization or external validation.

### Conclusion
The most significant potential problem for Brielle’s model is the risk of creating a positive feedback loop, as outlined in Option D. This issue could distort the model’s predictions and lead to inefficient police distribution. To mitigate this, Brielle should consider incorporating external data sources (e.g., traffic camera feeds) or periodic reassessment with unpatrolled area surveys to break the loop. Evaluation remains feasible with standard supervised learning metrics, ensuring the model can be refined to balance its predictive power with real-world dynamics.