# Decision Trees and Random Forests in Python

### The Decision Tree Algorithm
A decision tree is a flowchart-like tree structure where an internal node represents a feature(or attribute), the branch represents a decision rule, and each leaf node represents the outcome.

The topmost node in a decision tree is known as the root node. It learns to partition on the basis of the attribute value. It partitions the tree in a recursive manner called recursive partitioning. This flowchart-like structure helps you in decision-making. It's visualization like a flowchart diagram which easily mimics the human level thinking. That is why decision trees are easy to understand and interpret.

decision tree example for heart attack prevention
![image](https://user-images.githubusercontent.com/13853670/231739417-bfb9c417-4937-4e8e-b4e4-7548b5c0c64a.png)

**As a marketing manager, you want a set of customers who are most likely to purchase your product. This is how you can save your marketing budget by finding your audience. As a loan manager, you need to identify risky loan applications to achieve a lower loan default rate. This process of classifying customers into a group of potential and non-potential customers or safe or risky loan applications is known as a classification problem.**

Classification is a two-step process; a learning step and a prediction step. In the learning step, the model is developed based on given training data. In the prediction step, the model is used to predict the response to given data. A Decision tree is one of the easiest and most popular classification algorithms used to understand and interpret data. It can be utilized for both classification and regression problems.

A decision tree is a white box type of ML algorithm. It shares internal decision-making logic, which is not available in the black box type of algorithms such as with a neural network. Its training time is faster compared to the neural network algorithm.

The time complexity of decision trees is a function of the number of records and attributes in the given data. The decision tree is a distribution-free or non-parametric method which does not depend upon probability distribution assumptions. Decision trees can handle high-dimensional data with good accuracy.


### How Does the Decision Tree Algorithm Work?

The basic idea behind any decision tree algorithm is as follows:

Select the best attribute using Attribute Selection Measures (ASM) to split the records.
Make that attribute a decision node and breaks the dataset into smaller subsets.
Start tree building by repeating this process recursively for each child until one of the conditions will match:
-- All the tuples belong to the same attribute value.
-- There are no more remaining attributes.
-- There are no more instances.
![image](https://user-images.githubusercontent.com/13853670/231739628-d1b909b5-d127-4d07-83b9-7702887bc0d3.png)

### How does the Decision Tree Algorithm Work?

Attribute Selection Measures

Attribute selection measure is a heuristic for selecting the splitting criterion that partitions data in the best possible manner. It is also known as splitting rules because it helps us to determine breakpoints for tuples on a given node. ASM provides a rank to each feature (or attribute) by explaining the given dataset. The best score attribute will be selected as a splitting attribute (Source). In the case of a continuous-valued attribute, split points for branches also need to define. The most popular selection measures are Information Gain, Gain Ratio, and Gini Index.

### Information Gain:-
Claude Shannon invented the concept of entropy, which measures the impurity of the input set. In physics and mathematics, entropy is referred to as the randomness or the impurity in a system. In information theory, it refers to the impurity in a group of examples. Information gain is the decrease in entropy. Information gain computes the difference between entropy before the split and average entropy after the split of the dataset based on given attribute values. ID3 (Iterative Dichotomiser) decision tree algorithm uses information gain.

![image](https://user-images.githubusercontent.com/13853670/231739811-31090873-77fd-4e07-9569-eb48bc6711b8.png)
Where Pi is the probability that an arbitrary tuple in D belongs to class Ci.

![image](https://user-images.githubusercontent.com/13853670/231739861-fab24930-811c-4b62-ab28-3d82146cd0ad.png)information gain
![image](https://user-images.githubusercontent.com/13853670/231739935-22f9bf2a-a54d-4336-a939-33cf117a2c1c.png)

Where:

Info(D) is the average amount of information needed to identify the class label of a tuple in D.
|Dj|/|D| acts as the weight of the jth partition.
InfoA(D) is the expected information required to classify a tuple from D based on the partitioning by A.
The attribute A with the highest information gain, Gain(A), is chosen as the splitting attribute at node N().

### Gain Ratio:-
Information gain is biased for the attribute with many outcomes. It means it prefers the attribute with a large number of distinct values. For instance, consider an attribute with a unique identifier, such as customer_ID, that has zero info(D) because of pure partition. This maximizes the information gain and creates useless partitioning.

C4.5, an improvement of ID3, uses an extension to information gain known as the gain ratio. Gain ratio handles the issue of bias by normalizing the information gain using Split Info. Java implementation of the C4.5 algorithm is known as J48, which is available in WEKA data mining tool.

![image](https://user-images.githubusercontent.com/13853670/231739995-19238e9c-4807-43ce-a359-bc494cd010c2.png)
Where:

|Dj|/|D| acts as the weight of the jth partition.
v is the number of discrete values in attribute A.
The gain ratio can be defined as

![image](https://user-images.githubusercontent.com/13853670/231740069-627bac92-6f1f-4153-bbc5-fea745d797a5.png)
The attribute with the highest gain ratio is chosen as the splitting attribute (Source).

### Gini index:-
Another decision tree algorithm CART (Classification and Regression Tree) uses the Gini method to create split points.

![image](https://user-images.githubusercontent.com/13853670/231740133-6edc1ea2-120c-4ff8-ba55-4331007bf357.png)
Where pi is the probability that a tuple in D belongs to class Ci.

The Gini Index considers a binary split for each attribute. You can compute a weighted sum of the impurity of each partition. If a binary split on attribute A partitions data D into D1 and D2, the Gini index of D is:

![image](https://user-images.githubusercontent.com/13853670/231740185-13dc4db9-8700-4ad3-9855-7a3769f4126d.png)
In the case of a discrete-valued attribute, the subset that gives the minimum gini index for that chosen is selected as a splitting attribute. In the case of continuous-valued attributes, the strategy is to select each pair of adjacent values as a possible split point, and a point with a smaller gini index is chosen as the splitting point.

![image](https://user-images.githubusercontent.com/13853670/231740236-7ce297a9-9ae5-405a-a891-a5b7ef3fb7e7.png)
The attribute with the minimum Gini index is chosen as the splitting attribute.
gini index
