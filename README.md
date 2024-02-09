# Metric of Image retrieval
This repo aims at collect the metric used in popular dataset of image retrieval, helping beginner to master the essential knowledge in evaluating performance of image retrieval tasks, e.g. image retrieval, visual place recognition, metric learning.

## $R$ Oxford & $R$ Paris
Link to [revisitop](https://github.com/filipradenovic/revisitop).
```python
### Input:
# ranks : sorted list of retrieved results e.g.[0, 1, 2, 3, 5, 7, ...]
# nres  : Number of positive images (Ground Truth)
### Return:
# ap: Average precision

"""
Example:
if k == 2: # ranks = [0, 1, 4]
    AP_k = (2/4 + 3/5)/nres*2 = 0.18
elif k == 1:
    AP_k = (1/1 + 1/1)/nres*2 = 0.33
elif k == 0:
    AP_k = (1 + 1)/3*2 = 0.33
AP = 0.85
"""
```

For each query $i$, 

$$
AP_i = \sum_{k=1}^N{\frac{\frac{k}{ranks[k]}+\frac{k+1}{ranks[k] + 1}}{nres \times 2}},
$$

where $N$ denotes the number of positive samples. Note that if $ranks[k] = 0$, $ AP_k = 1+1/nres * 2$ .

$$
mAP = \frac{\sum_{i=1}^K{AP_i}}{K},
$$

where $K$ denotes the number of total queries.

## Google Landmark v2 (GLDv2)
Link to [GLDv2](https://www.kaggle.com/competitions/landmark-retrieval-2020). Submit to kaggle for evaluation.

$$
mAP@100 = \frac{1}{Q}\sum_{q=1}^Q{\frac{1}{min(m_q, 100)}}\sum_{k=1}^{min(n_q, 100)}{P_q(k)rel_q(k)},
$$

where:

- $Q$ is the number of query images
- $m_q$ is the number of *index* images containing a landmark **in common with** the query image $q$ (note that $m_q > 0$)
- $n_q$ is the number of *predictions* made by the system for query $q$
- $P_q(k)$ is the precision at rank $k$ for the $q$-th query
- $rel_q(k)$ denotes the relevance of prediciton $k$ for the $q$-th query: it’s 1 if the $k$-th prediction is correct, and 0 otherwise.

## Stanford Online Product (SOP)
Link to [SOP]()

Same with CUB, Car, INaturalist

TODO
