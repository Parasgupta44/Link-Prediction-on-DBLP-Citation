
## Link Prediction Techniques on Co Authors in a Citation System
The project is using the following datasets for testing.
- [Aminer Citation Dataset v10](https://aminer.org/citation)
- [Aminer Citation Dataset v11](https://aminer.org/citation)

Structure of these datasets can be found [here.](https://aminer.org/citation)

**Note**: The neo4j queries can be found in ML notebooks which have been used many times in the GraphSAGE notebooks as well.

## Contents

- [Introduction](#introduction)
- [Problem](#problem)
- [Database](#database)
- [Machine Learning Techniques](#machine-learning-techniques-for-link-prediction)
- [Graph Neural Networks](#deep-learning-techniques)
-----------
## Introduction

Link prediction is one of the most important research topics in the field of graphs and networks. **The objective of link prediction is to identify pairs of nodes that will either form a link or not in the future.**


![Link prediction depiction](https://miro.medium.com/max/700/0*4sbvBTWVmXnEC53v.png)

----------
## Problem

Given a citation network system in which different authors have collaborated with each other in the past. Our task is to find the links that can be formed with the authors in the future. (i.e. they are co-authors) 

-----------
## Database

For storing the data, we are using [`neo4j`](https://neo4j.com/) (in both ML as well as Deep Learning Techniques). `Cypher` is used for data manipulation.
For connectivity with the python Data Science Ecosystem, `py2neo` is used.

For installing neo4j instance on Linux VM, you can follow [`this.`](https://guptaparas.in/neo4j-virtual-machine/)

--------------

## Machine Learning Techniques for Link Prediction

Here we are using the following techniques to measure similarity measures to get an idea about the structure and topology of the Graph Network as well.

- Common Neighbours
- Preferential Attachment
- Total Neighbours
- Triangle Completion and Clustering Coefficients
- Label Propagation
- Louvain Algorithm

The scores obtained from these techniques can be used alone to determine the links for future. For better performance, these features can be fed into some ML model to obtain the results. We are using Random Forest Classifier for the purpose (which will act as a binary classifier).

The dataset is very large to process on a whole. So, we are using subsets of the data to perform our tasks. (Notebooks with different sets of data have been added.)

**Notebooks for the above techniques**
- [`With 4 venues`](./notebooks/link_pred_12GB_4venues.ipynb)
- [`With 6 venues`](./notebooks/link_pred_25GB_6venues.ipynb)
- [`With 2 venues and TF-IDF, cosine similarity (Citation v11)`](./notebooks/fos_link_pred_25GB_2venues_with_TF_IDF.ipynb)

-------------
## Deep Learning Techniques

We will be leveraging power of Graph Neural Networks to achieve Link Predictions in our co-author Graph. We are using [`GraphSAGE`](http://snap.stanford.edu/graphsage/) implemented in [`stellargraph`](https://github.com/stellargraph/stellargraph) library for this.

The following notebooks has been added (Citation v11 used):
- [Without LDA (Latent Dirichlet Allocation for topic modelling)](./GraphSAGE/noLDA)
- [With LDA (larger feature set)](/GraphSAGE/LDA)
- [Different metrics](/GraphSAGE/metrics)
- [Author Recommendation](/GraphSAGE/Recommend)
- [Weighted](/GraphSAGE/weighted)


--------

## Reference 

[1] [Graph Algorithms: Practical Examples in Apache Spark and Neo4j, By Mark Needham & Amy E. Hodler](https://neo4j.com/graph-algorithms-book/)

[2] [GraphSAGE: Inductive Representation Learning on Large Graphs](http://snap.stanford.edu/graphsage/)