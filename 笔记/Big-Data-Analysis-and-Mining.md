---
title: Big Data Analysis and Mining
date: 2018-05-29 05:08:46
tags: [大数据,数据分析,数据挖掘]
---

![image.png](https://upload-images.jianshu.io/upload_images/665202-bb94c950d325d43f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<!--more-->

csdn：https://blog.csdn.net/linxid/article/details/80494922

# Chapter1 Introduction
## 1.1 What is Big Data:

**Answer：** used to describe a massive structured and unstructured data that is so large that it is difficult to process using traditional database and software techniques.

## 1.2 4V of Big Data:
**Answer：** Volume:大量; Velocity:快速；Variety:多样; Veracity:真实准确。

## 1.3 Knowledge Discovery from Data (KDD)
1. **Data cleaning** (to remove noise and inconsistent data)
2. **Data integration** (where multiple data sources may be combined)
3. **Data selection** (where data relevant to the analysis task are retrieved from the
database)
4. **Data transformation** (where data are transformed and consolidated into forms
appropriate for mining by performing summary or aggregation operations)4
5. **Data mining** (an essential process where intelligent methods are applied to extract
data patterns)
6. **Pattern evaluation** (to identify the truly interesting patterns representing knowledge
based on interestingness measures—see Section 1.4.6)
7. **Knowledge presentation** (where visualization and knowledge representation techniques are used to present mined knowledge to users)

## 1.4 What is Data mining:
**Answer：** Under acceptable computational efficiency limitations, applying data analysis
and discovery algorithms, to produce a particular enumeration of patterns over the
data

## 1.5 Main Data Mining Tasks:
**Answer：**
1. Association rule mining (_**Two Steps:** Find All Frequent itemsets, Generate strong association rules from frequent itemsets_),
Finding frequent patterns, associations, correlations, or causal structures among sets of items or objects in transaction databases, relational databases, and other information repositories.

2. Cluster analysis (_**Methods:** Partitioning method, Hierarchical method, Density-Based method, and Grid-Based method_),
3. Classification/Prediction,
4. Outlier detection

# Chapter2 Basic Concepts

## 2.1 Tasks of ML:
**Answer：** supervised learning; Unsupervised learning; Semi-supervised learning

## 2.2 How to avoid Overfitting:
**Answer：** Increase Sample;Remove outliers;Decrease model complexity,train-validation-test
(cross validation),regularization

## 2.3 Basic Algorithm：
### 2.3.1 Classification:
KNN；Naive Bayes；Decision Tree；SVM；

#### 2.3.2 Ensemble Learning：
Bagging -> Random Forest；Boosting -> AdaBoost；Stacking；

### 2.3.3 Clustering:
K-means；Hierarchical Clustering；DBSCAN；Apriori;

# Chapter3 Hashing
## Why we need Hashing?
To resolve the challenge, like the curse of dimensionality, storage cost, and query speed.

## 3.1 Find Similar Items

### 3.1.1 Shingling
* k-Shingling

### 3.1.2 Minhashing

**Definition:** the number of the first row in which column

* Jaccard Similarity of Sets
* From sets to Boolean Matrices
* Signatures --> Signature Matrix
* Hashing Function

**How to compute the Signature matrix**

### 3.1.3 Locality Sensitive Hashing(LSH)
### References：
https://blog.csdn.net/linxid/article/details/79745964

# Chapter4 Sampling for Big Data

## 4.1 Why we need sampling:

>sampling is the selection of a subset (a statistical sample) of individuals from within a statistical population to estimate characteristics of the whole population.

>#### Two advantages of sampling:
 the cost is lower and data collection is faster than measuring the entire population.

**The Problem:** generating values if X which are distributed according to the distribution.

## 4.2 Basics of Sampling
### 4.2.1 [Inverse Transfrom Sampling](https://en.wikipedia.org/wiki/Inverse_transform_sampling)

samling based on the inverse of Cumulative Distribution Function

**Algorithm:**
* 1.Generate a random number u from the standard uniform distribution in the interval [0,1].
* 2.Compute the value x such that Fx(x) = u.
* 3.Take x to be the random number drawn from the distribution described by Fx.

**Drawbacks:** It is hard to get the inverse function.

### 4.2.2 [Rejection Sampling](https://en.wikipedia.org/wiki/Rejection_sampling)

![image.png](https://upload-images.jianshu.io/upload_images/665202-a0372c62748b1dd0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

The problem of Rejection Sampling can be solved by using Adaptive Rejection sampling.
**Algorithm:**
* 1.Obtain a sample y from proposal distribution Y and a sample u from Uniform(0,1)(the uniform distribution over the unit interval).
* 2.If u<f(y)/Mg(y)(acceptance probability) : accept y;
  else:reject.

#### Adaptive Sampling:
It is useful for concave function of log-concave.
1. Let {xi,... xk} be the k starting points.
2. Calculate uk(x), the piece-wise linear upper bound formed from the tangents
 to h(x) at each point xi
 ![image.png](https://upload-images.jianshu.io/upload_images/665202-26724f070ed29b53.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4.2.3 Importance Sampling
Not reject but assign weight to each instance so that the correct distribution is targeted.
![image.png](https://upload-images.jianshu.io/upload_images/665202-58393d7deba32d59.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 4.2.4 Rejection Sampling VS Importance Sampling:
* Instances from RS share the same “weight”, only some of instances are reserved
* Instances from IS have different weight, all instances are reserved
* IS is less sensitive to proposal distribution

## 4.3 MCMC(Markov chain Monte Carlo)
**Markov property:**
 If the conditional probability distribution of future states of the process depends only upon the present state.
 ![image.png](https://upload-images.jianshu.io/upload_images/665202-df5dd02a33714ebf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**Markov chain:**
A Markov chain is a sequence of random variables x1,x2,x3...with Markov property.

### 4.3.1 MH(Metropolis-Hastings) Sampling：

### 4.3.2 Gibbs Sampling：

### 4.3.3 Gibbs V.S. MH
**MH Sampling:**
* Doesn’t have a 100% acceptance rate
* Doesn’t require to know the full conditionals
* Acceptance threshold would be very crucial

**Gibbs Sampling:**
* 100% acceptance rate
* Need to know the full conditionals

### References：
https://blog.csdn.net/itplus/article/details/19168937
https://blog.csdn.net/google19890102/article/details/51755242
https://en.wikipedia.org/wiki/Sampling_(statistics)
https://blog.csdn.net/ustbxy/article/details/45458725
https://blog.csdn.net/baimafujinji/article/details/51407703
《Pattern Recognition and Machine Learning》Bishop

# Chapter5 Data Stream
## 5.1 What is Data Stream

### what is the challenge of the Data Stream:
* Single Pass Handling
* Memory limitation
* Low Time complexity
* Concept Drift

## 5.2 What is Concept Drift
Concept drift means that the statistical properties of the target variable, which the model is trying to predict, change over time in unforeseen ways.

**the probability distribution changes.**

**Real concept drift:**
p(y|x) changes

**Virtual concept drift:**
p(x)changes,but not p(y|x)

## 5.3 Concept drift detection:
### 5.3.1.distribution-based detector
Monitoring the change of data distributions
#### Disadvantage:
* Hard to determine window size
* learn concept drift slower
* virtual concept drift

### 5.3.2.Error-rate based detector:
based on the change of the classification performance.
#### Disadvantage:
* Sensitive to noise
* Hard to deal with gradual concept drift
* Depend on learning model itself heavily

### Drift detection method:DDM

## 5.4 Data Stream Classification:
#### Data stream classification circle:
* Process an example at a time, and inspect it only once
* Be ready to predict at any point
* Use a limited amount of memory
* Work in a limited amount of time

### 5.4.1 VFDT(Very Fast Decision Tree)
**Algorithm:**
* calculate the information gain for the attributes and determines the best two attributes
* At each node,check for the condition: delta(G) = G(a) - G(b) > e
* if condition satisfied, create child nodes based on the test at the node.
* if not, stream in more examples and perform calculations till condition satisfied.

**Strengths:**
* Scale better than traditional methods
* incremental

**Weakness:**
* Could spend a lot of time with times
* Memory used with tree expansion
* Number of candidate a

## 5.5 Data Stream Clustering:
### Data stream clustering Framework:
#### Online Phase:
Summarize the data into memory-efficient data structures
#### Offline Phase:
Use a clustering algorithm to find the data partition

### References：
https://machinelearningmastery.com/gentle-introduction-concept-drift-machine-learning/
http://www.liaad.up.pt/kdus/products/datasets-for-concept-drift
https://www.hindawi.com/journals/tswj/2015/235810/

# Chapter6 Graph Mining
## 6.1 BackGround:
### Applications in real-world:
* information Maximization
* computer network security
* prediction

### Network types:
* regular
* Random
* small world
* scale free

### Six degree of separation:
The average distance between two random individuals in the USA: 6

The average distance between two randomly users in Facebook(721 million active users, 69 billion links): 4.74

## 6.2 Key Node Identification

### 6.2.1 Centrality:
* Degree Centrality
* Between Centrality
* Closeness Centrality

### 6.2.2 K-shell Decomposition:
Advantage:
* Low computational complexity
* Reveal the hierarchy structure clearly

Disadvantage:
* Can not use in a lot of networks
* Too coarse, sometimes is inferior to degree measure.

[Explation:](https://www.youtube.com/watch?v=6Mk9NnboDsQ)

Prune all the nodes with degree 1 till no degree 1 nodes left in the network, the nodes pruned have ks=1. Similarly, prune other nodes having degree 2 and assign them ks =2. Repeat, till the graph becomes empty.

### 6.2.3 PageRank:

If a page is linked with many high-cited pages, then it will gain high PageRank score.
We assume a customer can use URL to link to any pages, to solve the problem that a node has no outlinks.

the equation of a Page's PR:
![image.png](https://upload-images.jianshu.io/upload_images/665202-b964a4bd418b6359.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**Explanation:**

http://blog.jobbole.com/23286/

https://www.cnblogs.com/rubinorth/p/5799848.html

https://en.wikipedia.org/wiki/PageRank#Algorithm
## 6.3 Community Detection
#### How to find intrinsic Community structure in large-scale networks:

* **Minimum cut:**
may return an imbalanced partition.

* **Ratio Cut & Normalized cut:**
  How to calculate Ratio Cut and Normalized Cut.We can use spectral clustering algorithm to calculate it.

* **Modularity Maximization:**
measure the strength of a community by taking into account the degree distribution.

#### A new viewpoint for community detection

### References：
http://blog.sciencenet.cn/blog-3075-982948.html

# Chapter7 Hadoop-Spark
## 7.1 Hadoop

### 7.1.1 What is Hadoop

#### Definition：
Hadoop is a software framework for distributed processing of large datasets across large clusters of computers.

#### Design principles
* Automatic parallelization & distribution
* fault tolerance and automatic recovery
* clean and simple programming abstraction

#### Hadoop Architecture:
* Distributed file system (HDFS)
* Execution engine (MapReduce)
![image.png](https://upload-images.jianshu.io/upload_images/665202-0d2dcebd1c1f3f1a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 7.1.2 [HDFS(Hadoop Distributed File System)](https://www.yiibai.com/hadoop/hadoop_hdfs_overview.html)

#### What is HDFS:
The HDFS is a distributed, scalable, and portable file system written in Java for the Hadoop framework
![image.png](https://upload-images.jianshu.io/upload_images/665202-7476a6640a70103c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**Namenode(名称结点):**

**Datanodes(数据结点)：**

#### Main properties of HDFS:
* **Large:** A HDFS instance may consist of thousands of server machines
* **replication:** Each data block is replicated many times
* **failure:** Failure is the norm rather than exception
* **fault tolerance:** Detection of faults and quick, automatic recovery from them is a core architectural goal of HDFS

#### Hadoop vs other systems:
Hadoop is a software framework for distributed processing of large datasets across large clusters of computers
### 7.1.2 Design principles
Automatic parallelization & distribution, fault tolerance and automatic recovery, clean and simple programming
abstraction
* **Main properties of HDFS**
Large, replication, failure, fault tolerance
* **Hadoop vs other systems**
|  | Distributed database | Hadoop|
| --- | --- | --- |
| Computing model | Transactions, concurrency control| Job and no concurrency control|
| Data model | Sturcture data, read/write mode | un(semi)structure, read only mode|
| Cost model | Expensive| Cheap|
| Fault tolerance | Rare | Common|
| Key characteristics | Efficiency, optimizations, fine-tuning| Scalability, flexibility, fault tolerance|

### 7.1.3 [MapReduce](https://en.wikipedia.org/wiki/MapReduce)
#### What is MapReduce:
MapReduce is a programming model and an associated implementation for processing and generating big data sets with a parallel, distributed algorithm on a cluster.

Users only provide the “Map” and “Reduce” functions.

#### How it Works:
![image.png](https://upload-images.jianshu.io/upload_images/665202-480d44aaa4a23d13.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### Example:


## 7.2 Spark
### MapReduce limitations:
* Great at one-pass computation, but inefficient for `multi-pass` algorithms.
* No efficient primitives for data sharing

### Spark's Goal:
Generalize MapReduce to support new apps within same engine

### MapReduce VS Spark:
* **MapReduce limitations**
Great at one-pass computation, but inefficient for `multi-pass` algorithms.
No efficient primitives for data sharing
* **Spark's Goal**
Generalize MapReduce to support new apps within same engine

### MapReduce VS Spark**

| MapReduce | Spark |
| --- | --- |
| Great **at one-pass** computation, but inefficient for `multi-pass` algorithims | Extends programming languages with a distributed collection data-structure **(RDD)** |
| No efficient primitives for data sharing | Clean APIs in Java, Scala, Python, R |

### References：
https://www.yiibai.com/hadoop/hadoop_introduction_to_hadoop.html
https://blog.csdn.net/qq_26437925/article/details/78467216
