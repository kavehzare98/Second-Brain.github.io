202406111251
Status: #learning
Tags: [Machine Learning]
# Supervised vs. Unsupervised Machine Learning

### Machine Learning definition
A computer program is said to *learn* from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E.
### Machine Learning Tools
#### Supervised Learning
- most widely used
- Applications of Machine Learning:
	- spam filtering
	- speech recognition
	- machine translation
	- online advertising
	- self-driving car
	- visual inspection
- example 1: Housing price prediction
	- house size vs. house price
	- "**Regression**" problem
		- helps predict numbers
- you're learning a mapping of x to y based on (x, y) data points
- example 2: tumor classification
	- classifying malignant and benign breast tumors
	- tumor size vs malignant
	- "**Classification**" problem
		- classify/ predict categories
- you can have multiple dimensions/ features/ regressors
- we will learn about an algorithm called: [[Support Vector Machine]]
	- uses an infinite number of input features
	- infinite-dimensional vector (how does a computer store it?)
	- Technical method called kernels
- you'll be exposed to techniques known as [[Back Propogation]] or [[Gradient Descent]]

#### Unsupervised Learning
- Data that's not associated with any output labels
- Example 1: Breast Cancer Tumor![[Screenshot 2024-06-11 at 12.41.56 PM.png]]
- Clustering algorithm
	- Group similar data points together
	- Application: Google News grouping articles together
	- Application: DNA microarray
	- Application: Grouping customers into segments
- Anomaly Detection
	- Find unusual data points
	- Application: Fraud Detection
- Dimensionality Reduction
	- Compress data using fewer numbers

## Reference
Link: https://www.youtube.com/watch?v=jGwO_UgTS7I
