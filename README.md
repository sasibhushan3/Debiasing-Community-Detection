# Debiasing-Community-Detection
Implementation of ["Debiasing Community Detection: The Importance of Lowly-Connected Nodes"](https://arxiv.org/pdf/1903.08136.pdf)


# Summary
Community detection is an important task in social network analysis, allowing us to identify and understand the communities within the social structures. Most of the community detection approaches either fail to assign lowly-connected users to communities or assign them to trivially small communities that prevent them from being included in analysis. A new approach is introduced that is more inclusive for lowly-connected users by incorporating them into larger groups.


# Requirements
Packages and their version used:
* Community version: 1.0.0
* Numpy version: 1.18.2
* Pandas version: 1.0.3
* Sklearn version: 0.22.2
* Networkx version: 2.4
* Stanford Network Analysis Platform (SNAP) - C++ implementation
* Demon


# Results
Top 2 communities were used in the calculation of results for Louvain.


## Louvain Method Results
| | Observed Value | Paper Value |
|:--|--:|--:|
| Discarded Unique Hashtags | 974 (64.97%) | 625 (40.4%) |
| F1 Score ( macro avg ) | 0.38 | 0.434 |
| F1 Score ( weighted avg ) | 0.49 | 0.434 |
| Jaccard | 0.39 | 0.282 |
| Unlabeled Users | 46% | 21% |


## Demon Method Results
| |Observed Value|
|:--|--:|
|Discarded Unique Hashtags|913 (61.7%)|
|F1 Score ( macro avg )|0.40|
|F1 Score ( weighted avg )|0.62|
|Jaccard|0.667|
|Unlabeled Users|65.7%|


## CESNA Method Results
| |Observed Value|Paper Value|
|:--|--:|--:|
|Discarded Unique Hashtags|607 (39.3%)|597 (38.6%)|
|F1 Score ( macro avg )|0.29|0.343|
|F1 Score ( weighted avg )|0.34|0.343|
|Jaccard|0.224|0.211|
|Unlabeled Users|69.13%|69%|


## CLAN Method Results
User tweets are passed through a Count vectorizer which generates the unigrams for each user which are the node attributes for the user.
| |Observed Value (Random Forests)|Observed Value (Xgboost)|Paper Value|
|:--|--:|--:|--:|
|Discarded Unique Hashtags|0|0|0|
|F1 Score ( macro avg )|0.45|0.453|0.478|
|F1 Score (weighted avg)|0.64|0.64|0.478|
|Jaccard|0.659|0.662|0.318|
|Unlabeled Users|0%|0%|0%|


# Remaining
<List of tasks that you were not able to do> <This could also be your TODO>
1. Other node attributes can be used for training the model. We can run an RNN-encoder on the tweets of the user and take the outpout vector as the attributes of the node user.
2. Various models can used for classification in part-1(Louvain was used) part-2(XGboost and Random forest were used) of CLAN algorithm.


# NOTE
<List of concerns or issues that you faced. This could be problem in data splitting or some missing details in the paper.>

* In the original paper, the algorithm used in part-2 of CLAN wasn't mentioned.
* Also in louvain algorithm, the hyper parameter used wasn't mentioned. Same was with the CESNA with number of communities. So algorithms were tested with different hyper parameters to produce the results of the paper.
* In calculation of FI score and jaccard score number of classes(*supporters, opposers, unaffiliated*) considered wasn't mentioned in paper. Hence different ways were tested. Finally, we settle on the following:
  1. All discarded users are given *Unaffiliated* status.
  2. We use multi-class Jaccard score instead of binary Jaccard score.


## Team Members
|Roll No|Name|
|--|--|
|16CS30037|Uppada Vishnu|
|16CS30018|Lakkam Sai Krishna Reddy|
|16CS30032|Seelaboyina Sasi Bhushan|
|16EC10001|Aditya Sai Chappidi|
|16EC10027|K R Abhay Chandra|
