---
title: Introduction to Pandas
layout: post
date: 2019-01-11 11:20
image: /assets/images/IntroductionToPandas/pandas.png
headerImage: true
tag:
- machine learning
- pandas
- tutorial
- Explained

star: false
category: blog
author: Rohit Midha
---
## Series


```python
import pandas as pd
import numpy as np
import random
```


```python
first_series = pd.Series([1,2,3, np.nan ,"hello"])
first_series
```




    0        1
    1        2
    2        3
    3      NaN
    4    hello
    dtype: object




```python
series = pd.Series([1,2,3, np.nan ,"hello"], index = ['A','B','C','Unknown','String'])
series
#indexing the Series with custom values
```




    A              1
    B              2
    C              3
    Unknown      NaN
    String     hello
    dtype: object




```python
dict = {"Python": "Fun", "C++": "Outdated","Coding":"Hmm.."}
series = pd.Series(dict)
series
# Dict to pandas Series
```




    Python         Fun
    C++       Outdated
    Coding       Hmm..
    dtype: object




```python
series[['Coding','Python']]
```




    Coding    Hmm..
    Python      Fun
    dtype: object




```python
series.index
```




    Index(['Python', 'C++', 'Coding'], dtype='object')




```python
series.values
```




    array(['Fun', 'Outdated', 'Hmm..'], dtype=object)




```python
series.describe()
```




    count            3
    unique           3
    top       Outdated
    freq             1
    dtype: object




```python
#Series is a mutable data structures and you can easily change any item’s value:
series['Coding'] = 'Awesome'
series
```




    Python         Fun
    C++       Outdated
    Coding     Awesome
    dtype: object




```python
# add new values:
series['Java'] = 'Okay'
series
```




    Python         Fun
    C++       Outdated
    Coding     Awesome
    Java          Okay
    dtype: object




```python
# If it is necessary to apply any mathematical operation to Series items, you may done it like below:
num_series = pd.Series([1,2,3,4,5,6,None])
num_series_changed = num_series/2
num_series_changed
```




    0    0.5
    1    1.0
    2    1.5
    3    2.0
    4    2.5
    5    3.0
    6    NaN
    dtype: float64




```python
# NULL/NaN checking can be performed with isnull() and notnull().
print(series.isnull())
print(num_series.notnull())
print(num_series_changed.notnull())
```

    Python    False
    C++       False
    Coding    False
    Java      False
    dtype: bool
    0     True
    1     True
    2     True
    3     True
    4     True
    5     True
    6    False
    dtype: bool
    0     True
    1     True
    2     True
    3     True
    4     True
    5     True
    6    False
    dtype: bool
