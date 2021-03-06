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
## Calculating the median: when we have an open-ended dataset

``` python 
# Sort values in column in ascending order 
new_df = df['col'].copy()
new_df = new_df.replace({'value': replaced_value})
new_df = new_df.astype(int)
new_df_sorted = new_df.sort_values()

# Calculate the median, first we need to find the middle indices
middle_indices = [int((len(new_df_sorted) / 2) - 1),
                 int((len(new_df_sorted) / 2))
                 ]

# Index values with boolean mask 
middle_values = new_df_sorted.iloc[middle_indices]

# Calculate the median between middle values 
median = middle_values.mean()

```

## Calculate the mode: When we have ordinal values denoted with text.

``` python 

def calc_mode(array):
    counts = {}
    
    for value in array:
        if value in counts:
            counts[value] += 1
        else:
            counts[value] = 1
    return max(counts, key = counts.get)

```
**WITH pandas**

``` python 
mode_method = df['col'].mode()

```

## Calculating the variance: Average Squared Distance from the mean

``` python
def get_variance(array):
    reference_point = sum(array) / len(array)
    distance = []
    
    # Loop through values and square them 
    for value in array:
        squared_distance = (value-reference_point)** 2
        
        distance.append(squared_distance)
        
    return sum(distance) / len(distance)
```

## Compute the standard deviation: The distance from the mean

``` python

def get_standard_dev(array):
    reference_point = sum(array) / len(array)
    distance = []
    
    # Loop through each value and calculate the variance 
    
    for value in array:
        squared_distance = (value - reference_point) ** 2
        
        distance.append(squared_distance)
    
    # Compute the variance 
    variance = sum(distance) / len(distance)
    
    # Compute the standard_deviation
    return sqrt(variance)
    
```

**IN pandas**

``` python

df['col'].std()

```
## Compute the Z score

``` python

def z_score(value, array, bessel = 0):
    mean = sum(array) / len(array)
    
    from numpy import std
    st_dev = std(array, ddof = bessel)
    
    distance = value - mean
    z = distance / st_dev
    
    return z
```

## Standardizing  a series: useful when comparing variables measured on a different scale. 

``` python

standardized_distro = Series.apply(
    lambda x: (x - Series.mean()) / Series.std()
    )

```
