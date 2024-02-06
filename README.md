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

where $K$ denotes the number of total query.
