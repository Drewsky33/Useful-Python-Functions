# Useful Python Workflow functions

## Calculating the weighted mean 

``` python
# Computing weighted mean 
def weighted_mean(distribution, weights):
    weighted_sum = []
    
    for mean, weight in zip(distribution, weights):
        weighted_sum.append(mean * weight)
    
    return sum(weighted_sum) / sum(weights)
 ```

**With numpy**

``` python 
numpy.average(a, axis=None, weights=None, returned=False, *, keepdims=<no value>)

```
