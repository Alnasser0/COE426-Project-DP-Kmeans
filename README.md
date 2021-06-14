# A Python Implementation of Differentially Private K-means Algorithm

## Purpose
This project has been done as part of required tasks in Data Privacy course (COE426) at KFUPM in Term 201. It discusses and implements a differentially private K-means algorithm in Python based on a psudocode and explenation given in a scientific paper.

## Introduction
The repository explains a K-means clustering algorithm that minimizes the risk of privacy disclosure. The proposed solution is to integrate differential privacy (DP) with K-means, which will help in reserving participants' privacy. In this project, the idea of both K-mean clustering and DP are combined to introduce DP k-means clustering algorithm (DP-KCCM).

## How it works
Based on algorithm proposed in the scientific paper, the algorithm divides the dataset into n × k clusters, Initially the centroids C = n × k are selected using selection algorithm. Then, some basic algorithm adds noise to each cluster and recalculates the centroids for a specific number of iterations. After the maximum iteration are reached, the algorithm merges the n × k centroids into k centroids.

## Datasets
The data file contains four datasets that are suitable for unsupervised learning and contain somehow Personal Identifiable Information (PII). For the sake of simplicity and demonstration, the algorithm will be applied to dataset that shows information about customers of a mall. It has the attributes of age, gender, annual income, and spending score. Currently, the dataset has 200 records.

## How to use
please follow the ipynb file (COE426_Project_Template.ipynb) in a jupyter notebook or in [Collab](https://colab.research.google.com/drive/1_qtDgqsStd_SFzohK29abG8NJDq5D0uN?usp=sharing) to use the algorithm.

## Result of the mall dataset
According to our calculations, a suitable K value for K-means algorithm for the mall dataset is 5. It will be used to show the result of clustering the data into 5 different groups.

### Original K-Means Output
When we applied the original K-Means clustering algorithm to the dataset, the result is shown in Figure 1. The output of the K-Means algorithm shows overlapping groups and how a sensitive attribute, Annual Income, is varying depending on other variables such as Spending Score and Age.

![Figure 1](/images/2D_Basic_K-Means.png)

### DP-KCCM Output
Figure 2 shows the output of dataset after DP-KCCM using an epsilon value of 70. We can see that it is very different from the original K-Means plot.

![Figure 2](/images/2D_DP-KCCM.png)

### Error Calculations
Based on our analysis, the error can be calculated using three different approaches. in our algorithm, we have implemented method 1 to test our result. You are more than welcome to contribute to the work of method 2 and 3.

#### Method 1
It can be calculated by comparing the number of labels for the closest centroids between the original K-means and DP K-means. The idea to do this is simple, basically we compare the number of labels for each centroid, and then find the closest centroids. Based on that, we calculate sum of squared error. It will help in punishing the algorithm if there is a big difference in number of labels between the original and DP centroids. Downside of this algorithm is that it does not account for equal changing of corresponding records.
#### Method 2
The second method is calculating the error of distance difference between centroids. This can be done by finding the closest centroids, then finding the sum of squared error of their distance. Downside of this algorithm is the same as approach 1, it does not account for records result of original dataset.

#### Method 3
a more complex and effective method can be used is to compare the number of changing records for a specific centroid. This needs the implementation of complex algorithm that checks the records in a group and compare them to closest group in the set of differentially private group.

#### Result of method 1
Figure 3 shows the graph of Error vs Epsilon. To demonstrate the error correctness, we can see that for small values of Epsilon, the error is very high, while the opposite for bigger numbers. The saturation Epsilon point of the error for our data set with the used settings in the algorithm is 25.

![Figure 3](/images/Error_Over_Different_e.png)

## Credit

### Abdullah Alnasser - KFUPM - 201535050
- Leader of the project
- Explained the work plan of the project to the team
- Found different scientific papers and decided which to implement
- Made the template of work, distributed the work, and explained the algorithm to the team
- Explained Colab and Python to the team
- Found different suitable data to use the algorithm on
- Created the data pipeline
- Created the generate centroids algorithm and noise calculation algorithm
- Edited the original K-means to be suitable to use in our algorithm
- Visualized the data and results
- Defined the error methodologies
- Revised the project code and fixed different small mistakes

### Abdulaziz Alasiri - KFUPM - 201627560
- Made the algorithm that combines nearest two clusters into one cluster
- Contributed to different aspects of the project from error calculations, report revising, and code fixing.

### Yousef Alfaris - KFUPM - 201443080
- In charge of error calculation algorithm.
- Contributed to report revising.

### Hussain Alsaffar - KFUPM - 201672140
- Found different data to use in the project
- Contributed to the report.

### Paper
[1] T. Ni, M. Qiao, Z. Chen, S. Zhang, and H. Zhong, “Utility-efficient Differentially Private K-means Clustering based on Cluster Merging,” arXiv.org, 03-Oct-2020. [Online]. Available: https://arxiv.org/abs/2010.01234.

### Original K-Means Algorithm code
[Python Data Science Handbook by Jake VanderPlas: Section 05.11-K-Means](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/05.11-K-Means.ipynb)

### Optimal K-Means using Elbow Method
[Kaggle Link to original author, cdabakoglu.](https://www.kaggle.com/cdabakoglu/clustering-mall-customers-k-means)
## License
[MIT](https://choosealicense.com/licenses/mit/)