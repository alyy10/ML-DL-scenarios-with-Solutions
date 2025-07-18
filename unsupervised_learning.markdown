# Customer Segmentation Using Unsupervised Learning

## Question

Anna has just landed her dream job.

She is working for a big fashion retailer. Thousands of products are sold monthly, and Anna plans to assist the company in understanding its customers better.

After a week of examining all the data they collected about each customer, Anna started pondering a suitable method to categorize them into clusters based on their attributes.

The challenge is that Anna is uncertain about the optimal approach. Should she classify customers based on their purchasing habits, or would it be better to do it by age? What about the type of apparel or spending capacity?

How would you tackle this problem if you were in Anna's position?

- Use a semi-supervised learning algorithm to process the data, thus leveraging supervised and unsupervised techniques.
- Use an unsupervised learning algorithm to find interesting ways to categorize customers.
- Define a few categories beforehand, and train a supervised learning algorithm to sort every customer into one.
- Apply a supervised learning algorithm to discover potentially interesting ways to categorize customers.

## Answer

Customer segmentation is a popular field where you try to find similar characteristics among your customers. It's the perfect opportunity to use unsupervised learning: a clustering algorithm.

For example, Anna could use K-Means to find interesting patterns and group together the customers that share them. A critical distinction is that she doesn't need to consider the segments preemptively; the clustering algorithm will find them for her.