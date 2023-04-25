# Federated-learning
It is the part of a course project for which I am mainly responsible.

task_link：https://drive.google.com/drive/folders/10Knop2BKieWm1PBHsn1HNBHY4ASmrsvq?usp=sharing

## Conception of Federated-learning

**Motivation:**

In the real world, data is often **decentralized across many parties,** compared with the centralized dataset processed in a tightly integrated system in learning. （现实就是数据各收各的

1. Sending the data may be too **costly** & Data may be considered too **sensitive (共享很难**
2. Local dataset may be too **small** & The local dataset may be **biased （自己训练不行**

**—》 Federated Learning**

Federated learning aims to train a central model collaboratively while keeping the data decentralized in each client, taking the parameters in the local models into account without obtaining the clients’ data, meeting the requirements of getting a better prediction model and keeping the data private. In the federated learning architecture, each client trains their own model separately with local data then encrypts the model parameters and uploads them to the server. The server aggregates the collected model parameters of the client using a secure aggregation approach. Finally, the server sends the new parameters to each client.

### Fed-avg

FedAvg does the aggregation by calculating the average of the parameters obtained from each client and returns the new parameters back to each client, iteratively doing the similar aggregation until termination.

## Process 

![image](https://user-images.githubusercontent.com/122254025/233258884-2f580817-28b2-447a-8274-ee87c4fdac05.png)

### distribution of data of each client

IID 非常理想，但是 NON-IID才是常态

To simulate different distribution and further discuss their impacts, Dirichlet distribution is used to split dataset. The larger the parameter alpha is, the split data will closer to the distribution of IID.


#### Dirichlet Distribution

As a multivariate beta distribution, Dirichlet distribution is a family of continuous multivariate probability distributions parameterized by the concentration parameter α. [1] Because of lots of good properties it has, Dirichlet distribution is commonly used to generate random variates with multi-labels by sampling from it.

The concentration parameter α determines and describes how "concentrated" the probability mass of the Dirichlet distribution to its center. When α is small enough and tend to 0 from the right, the mass will be highly concentrated in a few components which leads to the class imbalance. On the other hand, when α is large enough and much more than 1, the mass will be dispersed almost equally among all the components and this case can be approximately equal to class balance.[2]

Dirichlet distribution conducted in python function can be customed by vector α. Take a simple example to illustrate how α make use. Suppose that a six-sides dice is rolled and the number of occurrences of six sides is recorded after many rolling. The vector α can be described as the number of occurrences of six sides which means the distribution is inferred by this dice rolling experiment. Obviously, the number of occurrences of six sides of s fair dice will be almost the same. So, all scalars of α will be large and the same and this fair case with 6 categories is described by Dirichlet distribution. Similarly, the generation of random variates with different distributions can be processed by sampling from Dirichlet distribution.[3]

# Reference

Most are based on the lecture notes in COMP5434 in PolyU: https://www.notion.so/Federated-Learning-9a4f82036a584272b4099f513180a148

[1] LeCun, Y., Bengio, Y., & Hinton, G. (2015). Deep learning. Nature, 521(75 53),436-444.

[2] Luo, X. (2020). An overview of neural network architectures. In Proceedin gs of the 2nd International Conference on Computer Science and Application E ngineering (pp. 309-313). ACM.

[3]RLKP. (2017, March 11). 什么是 beta 分布，狄利克雷分布. Zhihu website. Retrieved April 9, 2013, from https://zhuanlan.zhihu.com/p/24555092




