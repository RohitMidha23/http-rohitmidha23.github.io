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

    ## DataFrames


    ```python
    data = {'year': [1990, 1994, 1998, 2002, 2006, 2010, 2014],
            'winner': ['Germany', 'Brazil', 'France', 'Brazil','Italy', 'Spain', 'Germany'],
            'runner-up': ['Argentina', 'Italy', 'Brazil','Germany', 'France', 'Netherlands', 'Argentina'],
            'final score': ['1-0', '0-0 (pen)', '3-0', '2-0', '1-1 (pen)', '1-0', '1-0'] }
    world_cup = pd.DataFrame(data, columns=['year', 'winner', 'runner-up', 'final score'])
    world_cup
    ```




    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>year</th>
          <th>winner</th>
          <th>runner-up</th>
          <th>final score</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1990</td>
          <td>Germany</td>
          <td>Argentina</td>
          <td>1-0</td>
        </tr>
        <tr>
          <th>1</th>
          <td>1994</td>
          <td>Brazil</td>
          <td>Italy</td>
          <td>0-0 (pen)</td>
        </tr>
        <tr>
          <th>2</th>
          <td>1998</td>
          <td>France</td>
          <td>Brazil</td>
          <td>3-0</td>
        </tr>
        <tr>
          <th>3</th>
          <td>2002</td>
          <td>Brazil</td>
          <td>Germany</td>
          <td>2-0</td>
        </tr>
        <tr>
          <th>4</th>
          <td>2006</td>
          <td>Italy</td>
          <td>France</td>
          <td>1-1 (pen)</td>
        </tr>
        <tr>
          <th>5</th>
          <td>2010</td>
          <td>Spain</td>
          <td>Netherlands</td>
          <td>1-0</td>
        </tr>
        <tr>
          <th>6</th>
          <td>2014</td>
          <td>Germany</td>
          <td>Argentina</td>
          <td>1-0</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    # Another way to set a DataFrame is the using of Python list of dictionaries:

    data_2 = [{'year': 1990, 'winner': 'Germany', 'runner-up': 'Argentina', 'final score': '1-0'},
              {'year': 1994, 'winner': 'Brazil', 'runner-up': 'Italy', 'final score': '0-0 (pen)'},
              {'year': 1998, 'winner': 'France', 'runner-up': 'Brazil', 'final score': '3-0'},
              {'year': 2002, 'winner': 'Brazil', 'runner-up': 'Germany', 'final score': '2-0'},
              {'year': 2006, 'winner': 'Italy','runner-up': 'France', 'final score': '1-1 (pen)'},
              {'year': 2010, 'winner': 'Spain', 'runner-up': 'Netherlands', 'final score': '1-0'},
              {'year': 2014, 'winner': 'Germany', 'runner-up': 'Argentina', 'final score': '1-0'}
             ]
    world_cup = pd.DataFrame(data_2)
    world_cup
    ```




    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>final score</th>
          <th>runner-up</th>
          <th>winner</th>
          <th>year</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1-0</td>
          <td>Argentina</td>
          <td>Germany</td>
          <td>1990</td>
        </tr>
        <tr>
          <th>1</th>
          <td>0-0 (pen)</td>
          <td>Italy</td>
          <td>Brazil</td>
          <td>1994</td>
        </tr>
        <tr>
          <th>2</th>
          <td>3-0</td>
          <td>Brazil</td>
          <td>France</td>
          <td>1998</td>
        </tr>
        <tr>
          <th>3</th>
          <td>2-0</td>
          <td>Germany</td>
          <td>Brazil</td>
          <td>2002</td>
        </tr>
        <tr>
          <th>4</th>
          <td>1-1 (pen)</td>
          <td>France</td>
          <td>Italy</td>
          <td>2006</td>
        </tr>
        <tr>
          <th>5</th>
          <td>1-0</td>
          <td>Netherlands</td>
          <td>Spain</td>
          <td>2010</td>
        </tr>
        <tr>
          <th>6</th>
          <td>1-0</td>
          <td>Argentina</td>
          <td>Germany</td>
          <td>2014</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    print("First 2 Rows: ",end="\n\n")
    print (world_cup.head(2),end="\n\n")
    print ("Last 2 Rows : ",end="\n\n")
    print (world_cup.tail(2),end="\n\n")
    print("Using slicing : ",end="\n\n")
    print (world_cup[2:4])
    ```

        First 2 Rows:

          final score  runner-up   winner  year
        0         1-0  Argentina  Germany  1990
        1   0-0 (pen)      Italy   Brazil  1994

        Last 2 Rows :

          final score    runner-up   winner  year
        5         1-0  Netherlands    Spain  2010
        6         1-0    Argentina  Germany  2014

        Using slicing :

          final score runner-up  winner  year
        2         3-0    Brazil  France  1998
        3         2-0   Germany  Brazil  2002


    ### CSV
    #### Reading:

    `df = pd.read_csv("path\to\the\csv\file\for\reading")`
    #### Writing:

    `df.to_csv("path\to\the\folder\where\you\want\save\csv\file")`


    ### TXT file(s)
    (txt file can be read as a CSV file with other separator (delimiter); we suppose below that columns are separated by tabulation):

    #### Reading:

    `df = pd.read_csv("path\to\the\txt\file\for\reading", sep='\t')`
    #### Writing:

    `df.to_csv("path\to\the\folder\where\you\want\save\txt\file", sep='\t')`
    ### JSON files
    (an open-standard format that uses human-readable text to transmit data objects consisting of attribute–value pairs. It is the most common data format used for asynchronous browser/server communication. By its view it is very similar to Python dictionary)

    #### Reading:

    `df = pd.read_json("path\to\the\json\file\for\reading", sep='\t')`
    #### Writing:

    `df.to_json("path\to\the\folder\where\you\want\save\json\file", sep='\t')`


    ```python
    # To write world_cup Dataframe to a CSV File
    world_cup.to_csv("worldcup.csv")
    # To save CSV file without index use index=False attribute

    print("File Written!",end="\n\n")

    #To check if it was written
    import os
    print(os.path.exists('worldcup.csv'))

    # reading from it in a new dataframe df
    df = pd.read_csv('worldcup.csv')
    print(df.head())


    ```

        File Written!

        True
           Unnamed: 0 final score  runner-up   winner  year
        0           0         1-0  Argentina  Germany  1990
        1           1   0-0 (pen)      Italy   Brazil  1994
        2           2         3-0     Brazil   France  1998
        3           3         2-0    Germany   Brazil  2002
        4           4   1-1 (pen)     France    Italy  2006



    ```python
    # We can also load the data without index as :
    df = pd.read_csv('worldcup.csv',index_col=0)
    print(df)
    ```

          final score    runner-up   winner  year
        0         1-0    Argentina  Germany  1990
        1   0-0 (pen)        Italy   Brazil  1994
        2         3-0       Brazil   France  1998
        3         2-0      Germany   Brazil  2002
        4   1-1 (pen)       France    Italy  2006
        5         1-0  Netherlands    Spain  2010
        6         1-0    Argentina  Germany  2014



    ```python
    movies=pd.read_csv("data/movies.csv",encoding = "ISO-8859-1")
    # encoding is added only for this specific dataset because it gave error with utf-8
    ```


    ```python
    movies['release_date'] = movies['release_date'].map(pd.to_datetime)
    print(movies.head(20))

    #print(movies.describe())
    ```

            user_id  movie_id  rating  timestamp   age gender     occupation zip_code  \
        0       196       242       3  881250949  49.0      M         writer    55105   
        1       305       242       5  886307828  23.0      M     programmer    94086   
        2         6       242       4  883268170  42.0      M      executive    98101   
        3       234       242       4  891033261  60.0      M        retired    94702   
        4        63       242       3  875747190  31.0      M      marketing    75240   
        5       181       242       1  878961814  26.0      M      executive    21218   
        6       201       242       4  884110598  27.0      M         writer    E2A4H   
        7       249       242       5  879571438  25.0      M        student    84103   
        8        13       242       2  881515193  47.0      M       educator    29206   
        9       279       242       3  877756647  33.0      M     programmer    85251   
        10      145       242       5  875269755  31.0      M  entertainment    V3N4P   
        11       90       242       4  891382267  60.0      M       educator    78155   
        12      271       242       4  885844495  51.0      M       engineer    22932   
        13       18       242       5  880129305  35.0      F          other    37212   
        14        1       242       5  889751633   NaN      M            NaN    85711   
        15      207       242       4  890793823  39.0      M      marketing    92037   
        16       14       242       4  876964570  45.0      M      scientist    55106   
        17      113       242       2  875075887  47.0      M      executive    95032   
        18      123       242       5  879809053   NaN      F         artist    20008   
        19      296       242       4  884196057  43.0      F  administrator    16803   

             movie_title release_date   ...    Fantasy  Film-Noir  Horror  Musical  \
        0   Kolya (1996)   1997-01-24   ...          0          0       0        0   
        1   Kolya (1996)   1997-01-24   ...          0          0       0        0   
        2   Kolya (1996)   1997-01-24   ...          0          0       0        0   
        3   Kolya (1996)   1997-01-24   ...          0          0       0        0   
        4   Kolya (1996)   1997-01-24   ...          0          0       0        0   
        5   Kolya (1996)   1997-01-24   ...          0          0       0        0   
        6   Kolya (1996)   1997-01-24   ...          0          0       0        0   
        7   Kolya (1996)   1997-01-24   ...          0          0       0        0   
        8   Kolya (1996)   1997-01-24   ...          0          0       0        0   
        9   Kolya (1996)   1997-01-24   ...          0          0       0        0   
        10  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        11  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        12  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        13  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        14  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        15  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        16  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        17  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        18  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        19  Kolya (1996)   1997-01-24   ...          0          0       0        0   

            Mystery  Romance  Sci-Fi  Thriller  War  Western  
        0         0        0       0         0    0        0  
        1         0        0       0         0    0        0  
        2         0        0       0         0    0        0  
        3         0        0       0         0    0        0  
        4         0        0       0         0    0        0  
        5         0        0       0         0    0        0  
        6         0        0       0         0    0        0  
        7         0        0       0         0    0        0  
        8         0        0       0         0    0        0  
        9         0        0       0         0    0        0  
        10        0        0       0         0    0        0  
        11        0        0       0         0    0        0  
        12        0        0       0         0    0        0  
        13        0        0       0         0    0        0  
        14        0        0       0         0    0        0  
        15        0        0       0         0    0        0  
        16        0        0       0         0    0        0  
        17        0        0       0         0    0        0  
        18        0        0       0         0    0        0  
        19        0        0       0         0    0        0  

        [20 rows x 30 columns]



    ```python
    movies_rating = movies['rating']
    # Here we are showing only one column, i.e. a Series
    print ('type:', type(movies_rating))
    movies_rating.head()
    ```

        type: <class 'pandas.core.series.Series'>





        0    3
        1    5
        2    4
        3    4
        4    3
        Name: rating, dtype: int64




    ```python
    # Filtering data
    # Let's display only women
    movies_user_female = movies[movies['gender']=='F']
    print(movies_user_female.head())
    ```

            user_id  movie_id  rating  timestamp   age gender     occupation zip_code  \
        13       18       242       5  880129305  35.0      F          other    37212   
        18      123       242       5  879809053   NaN      F         artist    20008   
        19      296       242       4  884196057  43.0      F  administrator    16803   
        21      270       242       5  876953744  18.0      F        student    63119   
        22      240       242       5  885775683  23.0      F       educator    20784   

             movie_title release_date   ...    Fantasy  Film-Noir  Horror  Musical  \
        13  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        18  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        19  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        21  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        22  Kolya (1996)   1997-01-24   ...          0          0       0        0   

            Mystery  Romance  Sci-Fi  Thriller  War  Western  
        13        0        0       0         0    0        0  
        18        0        0       0         0    0        0  
        19        0        0       0         0    0        0  
        21        0        0       0         0    0        0  
        22        0        0       0         0    0        0  

        [5 rows x 30 columns]



    ```python
    #to see all the different values possible for a given column
    occupation_list = movies['occupation']
    print(occupation_list)
    ```

        0               writer
        1           programmer
        2            executive
        3              retired
        4            marketing
        5            executive
        6               writer
        7              student
        8             educator
        9           programmer
        10       entertainment
        11            educator
        12            engineer
        13               other
        14                 NaN
        15           marketing
        16           scientist
        17           executive
        18              artist
        19       administrator
        20             student
        21             student
        22            educator
        23                 NaN
        24              writer
        25                 NaN
        26                 NaN
        27           marketing
        28       administrator
        29             student
                     ...      
        99970         educator
        99971            other
        99972            other
        99973            other
        99974    administrator
        99975           artist
        99976           artist
        99977           artist
        99978           artist
        99979           artist
        99980           artist
        99981    entertainment
        99982          student
        99983          student
        99984           artist
        99985           artist
        99986           artist
        99987          student
        99988        librarian
        99989           writer
        99990              NaN
        99991           artist
        99992            other
        99993            other
        99994          student
        99995          student
        99996          student
        99997          student
        99998           writer
        99999         engineer
        Name: occupation, Length: 100000, dtype: object


    ### Work with indexes and MultiIndex option


    ```python
    import random
    indexes = [random.randrange(0,100) for i in range(5)]
    data = [{i:random.randint(0,10) for i in 'ABCDE'} for i in range(5)]
    df = pd.DataFrame(data, index=[1,2,3,4,5])
    df
    ```




    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>A</th>
          <th>B</th>
          <th>C</th>
          <th>D</th>
          <th>E</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>1</th>
          <td>5</td>
          <td>8</td>
          <td>6</td>
          <td>4</td>
          <td>2</td>
        </tr>
        <tr>
          <th>2</th>
          <td>1</td>
          <td>3</td>
          <td>9</td>
          <td>8</td>
          <td>2</td>
        </tr>
        <tr>
          <th>3</th>
          <td>8</td>
          <td>7</td>
          <td>2</td>
          <td>1</td>
          <td>2</td>
        </tr>
        <tr>
          <th>4</th>
          <td>3</td>
          <td>8</td>
          <td>1</td>
          <td>3</td>
          <td>8</td>
        </tr>
        <tr>
          <th>5</th>
          <td>0</td>
          <td>7</td>
          <td>4</td>
          <td>4</td>
          <td>2</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    movies_user_gender_male = movies[movies['gender']=='M']
    movies_user_gender_male_dup = movies_user_gender_male.drop_duplicates(keep=False)
    print(movies_user_gender_male.head())
    # From this we can clearly see age has missing value and that from 100,000 the data reduced to 74260,
    # due to filtering and removing duplicates

    ```

           user_id  movie_id  rating  timestamp   age gender  occupation zip_code  \
        0      196       242       3  881250949  49.0      M      writer    55105   
        1      305       242       5  886307828  23.0      M  programmer    94086   
        2        6       242       4  883268170  42.0      M   executive    98101   
        3      234       242       4  891033261  60.0      M     retired    94702   
        4       63       242       3  875747190  31.0      M   marketing    75240   

            movie_title release_date   ...    Fantasy  Film-Noir  Horror  Musical  \
        0  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        1  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        2  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        3  Kolya (1996)   1997-01-24   ...          0          0       0        0   
        4  Kolya (1996)   1997-01-24   ...          0          0       0        0   

           Mystery  Romance  Sci-Fi  Thriller  War  Western  
        0        0        0       0         0    0        0  
        1        0        0       0         0    0        0  
        2        0        0       0         0    0        0  
        3        0        0       0         0    0        0  
        4        0        0       0         0    0        0  

        [5 rows x 30 columns]



    ```python
    #gender = female and age between 30 and 40
    gender_required = ['F']
    filtered_df = movies[((movies['gender'] == 'F') & (movies['age'] > 30) & (movies['age'] <40))]
    filtered_df
    ```




    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>user_id</th>
          <th>movie_id</th>
          <th>rating</th>
          <th>timestamp</th>
          <th>age</th>
          <th>gender</th>
          <th>occupation</th>
          <th>zip_code</th>
          <th>movie_title</th>
          <th>release_date</th>
          <th>...</th>
          <th>Fantasy</th>
          <th>Film-Noir</th>
          <th>Horror</th>
          <th>Musical</th>
          <th>Mystery</th>
          <th>Romance</th>
          <th>Sci-Fi</th>
          <th>Thriller</th>
          <th>War</th>
          <th>Western</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>13</th>
          <td>18</td>
          <td>242</td>
          <td>5</td>
          <td>880129305</td>
          <td>35.0</td>
          <td>F</td>
          <td>other</td>
          <td>37212</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>27</th>
          <td>129</td>
          <td>242</td>
          <td>4</td>
          <td>883243972</td>
          <td>36.0</td>
          <td>F</td>
          <td>marketing</td>
          <td>07039</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>39</th>
          <td>34</td>
          <td>242</td>
          <td>5</td>
          <td>888601628</td>
          <td>38.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>42141</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>42</th>
          <td>209</td>
          <td>242</td>
          <td>4</td>
          <td>883589606</td>
          <td>33.0</td>
          <td>F</td>
          <td>educator</td>
          <td>85710</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>110</th>
          <td>861</td>
          <td>242</td>
          <td>5</td>
          <td>881274504</td>
          <td>38.0</td>
          <td>F</td>
          <td>NaN</td>
          <td>14085</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>147</th>
          <td>11</td>
          <td>393</td>
          <td>4</td>
          <td>891905222</td>
          <td>39.0</td>
          <td>F</td>
          <td>other</td>
          <td>30329</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>157</th>
          <td>269</td>
          <td>393</td>
          <td>1</td>
          <td>891451036</td>
          <td>31.0</td>
          <td>F</td>
          <td>librarian</td>
          <td>43201</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>160</th>
          <td>5</td>
          <td>393</td>
          <td>2</td>
          <td>875636265</td>
          <td>33.0</td>
          <td>F</td>
          <td>other</td>
          <td>15213</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>161</th>
          <td>18</td>
          <td>393</td>
          <td>3</td>
          <td>880130930</td>
          <td>35.0</td>
          <td>F</td>
          <td>NaN</td>
          <td>37212</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>167</th>
          <td>151</td>
          <td>393</td>
          <td>2</td>
          <td>879528692</td>
          <td>38.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>48103</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>178</th>
          <td>152</td>
          <td>393</td>
          <td>5</td>
          <td>884018430</td>
          <td>33.0</td>
          <td>F</td>
          <td>educator</td>
          <td>68767</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>187</th>
          <td>330</td>
          <td>393</td>
          <td>4</td>
          <td>876547004</td>
          <td>35.0</td>
          <td>F</td>
          <td>educator</td>
          <td>33884</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>210</th>
          <td>450</td>
          <td>393</td>
          <td>4</td>
          <td>882812349</td>
          <td>35.0</td>
          <td>F</td>
          <td>educator</td>
          <td>11758</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>213</th>
          <td>457</td>
          <td>393</td>
          <td>3</td>
          <td>882548583</td>
          <td>33.0</td>
          <td>F</td>
          <td>salesman</td>
          <td>30011</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>241</th>
          <td>577</td>
          <td>393</td>
          <td>4</td>
          <td>880475363</td>
          <td>36.0</td>
          <td>F</td>
          <td>student</td>
          <td>77845</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>246</th>
          <td>593</td>
          <td>393</td>
          <td>4</td>
          <td>886194041</td>
          <td>31.0</td>
          <td>F</td>
          <td>educator</td>
          <td>68767</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>267</th>
          <td>716</td>
          <td>393</td>
          <td>3</td>
          <td>879796596</td>
          <td>36.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>44265</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>280</th>
          <td>796</td>
          <td>393</td>
          <td>4</td>
          <td>893218933</td>
          <td>32.0</td>
          <td>F</td>
          <td>writer</td>
          <td>33755</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>325</th>
          <td>264</td>
          <td>381</td>
          <td>4</td>
          <td>886123596</td>
          <td>36.0</td>
          <td>F</td>
          <td>writer</td>
          <td>90064</td>
          <td>Muriel's Wedding (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>328</th>
          <td>5</td>
          <td>381</td>
          <td>1</td>
          <td>875636540</td>
          <td>33.0</td>
          <td>F</td>
          <td>other</td>
          <td>15213</td>
          <td>Muriel's Wedding (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>329</th>
          <td>18</td>
          <td>381</td>
          <td>4</td>
          <td>880131474</td>
          <td>35.0</td>
          <td>F</td>
          <td>other</td>
          <td>37212</td>
          <td>Muriel's Wedding (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>330</th>
          <td>256</td>
          <td>381</td>
          <td>5</td>
          <td>882165135</td>
          <td>35.0</td>
          <td>F</td>
          <td>none</td>
          <td>39042</td>
          <td>Muriel's Wedding (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>331</th>
          <td>151</td>
          <td>381</td>
          <td>5</td>
          <td>879528754</td>
          <td>38.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>48103</td>
          <td>Muriel's Wedding (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>358</th>
          <td>450</td>
          <td>381</td>
          <td>2</td>
          <td>882374497</td>
          <td>35.0</td>
          <td>F</td>
          <td>educator</td>
          <td>11758</td>
          <td>Muriel's Wedding (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>384</th>
          <td>716</td>
          <td>381</td>
          <td>4</td>
          <td>879795644</td>
          <td>36.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>44265</td>
          <td>Muriel's Wedding (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>387</th>
          <td>786</td>
          <td>381</td>
          <td>3</td>
          <td>882843397</td>
          <td>36.0</td>
          <td>F</td>
          <td>engineer</td>
          <td>01754</td>
          <td>Muriel's Wedding (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>388</th>
          <td>796</td>
          <td>381</td>
          <td>3</td>
          <td>893047208</td>
          <td>32.0</td>
          <td>F</td>
          <td>writer</td>
          <td>33755</td>
          <td>Muriel's Wedding (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>397</th>
          <td>861</td>
          <td>381</td>
          <td>4</td>
          <td>881274780</td>
          <td>38.0</td>
          <td>F</td>
          <td>student</td>
          <td>14085</td>
          <td>Muriel's Wedding (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>406</th>
          <td>911</td>
          <td>381</td>
          <td>5</td>
          <td>892839846</td>
          <td>37.0</td>
          <td>F</td>
          <td>writer</td>
          <td>53210</td>
          <td>Muriel's Wedding (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>423</th>
          <td>79</td>
          <td>251</td>
          <td>5</td>
          <td>891271545</td>
          <td>39.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>03755</td>
          <td>Shall We Dance? (1996)</td>
          <td>1997-07-11</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>...</th>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
        </tr>
        <tr>
          <th>99139</th>
          <td>5</td>
          <td>374</td>
          <td>3</td>
          <td>875636905</td>
          <td>33.0</td>
          <td>F</td>
          <td>other</td>
          <td>15213</td>
          <td>Mighty Morphin Power Rangers: The Movie (1995)</td>
          <td>1995-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99146</th>
          <td>911</td>
          <td>374</td>
          <td>1</td>
          <td>892841118</td>
          <td>37.0</td>
          <td>F</td>
          <td>writer</td>
          <td>53210</td>
          <td>Mighty Morphin Power Rangers: The Movie (1995)</td>
          <td>1995-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99189</th>
          <td>18</td>
          <td>958</td>
          <td>5</td>
          <td>880129731</td>
          <td>35.0</td>
          <td>F</td>
          <td>other</td>
          <td>37212</td>
          <td>To Live (Huozhe) (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99235</th>
          <td>450</td>
          <td>1249</td>
          <td>3</td>
          <td>882812821</td>
          <td>35.0</td>
          <td>F</td>
          <td>educator</td>
          <td>11758</td>
          <td>For Love or Money (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99249</th>
          <td>796</td>
          <td>1055</td>
          <td>3</td>
          <td>893188577</td>
          <td>32.0</td>
          <td>F</td>
          <td>writer</td>
          <td>33755</td>
          <td>Simple Twist of Fate, A (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99255</th>
          <td>264</td>
          <td>1474</td>
          <td>2</td>
          <td>886123728</td>
          <td>36.0</td>
          <td>F</td>
          <td>writer</td>
          <td>90064</td>
          <td>Nina Takes a Lover (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99261</th>
          <td>264</td>
          <td>1475</td>
          <td>2</td>
          <td>886123596</td>
          <td>36.0</td>
          <td>F</td>
          <td>writer</td>
          <td>90064</td>
          <td>Bhaji on the Beach (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99279</th>
          <td>938</td>
          <td>1254</td>
          <td>1</td>
          <td>891357019</td>
          <td>38.0</td>
          <td>F</td>
          <td>technician</td>
          <td>55038</td>
          <td>Gone Fishin' (1997)</td>
          <td>1997-05-30</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99294</th>
          <td>269</td>
          <td>1479</td>
          <td>2</td>
          <td>891451111</td>
          <td>31.0</td>
          <td>F</td>
          <td>librarian</td>
          <td>43201</td>
          <td>Reckless (1995)</td>
          <td>1995-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99298</th>
          <td>450</td>
          <td>1479</td>
          <td>3</td>
          <td>882377479</td>
          <td>35.0</td>
          <td>F</td>
          <td>educator</td>
          <td>11758</td>
          <td>Reckless (1995)</td>
          <td>1995-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99313</th>
          <td>5</td>
          <td>267</td>
          <td>4</td>
          <td>875635064</td>
          <td>33.0</td>
          <td>F</td>
          <td>other</td>
          <td>15213</td>
          <td>unknown</td>
          <td>NaT</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99324</th>
          <td>18</td>
          <td>113</td>
          <td>5</td>
          <td>880129628</td>
          <td>35.0</td>
          <td>F</td>
          <td>other</td>
          <td>37212</td>
          <td>Horseman on the Roof, The (Hussard sur le toit...</td>
          <td>1996-04-19</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99333</th>
          <td>18</td>
          <td>973</td>
          <td>3</td>
          <td>880129595</td>
          <td>35.0</td>
          <td>F</td>
          <td>other</td>
          <td>37212</td>
          <td>Grateful Dead (1995)</td>
          <td>1996-10-18</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99352</th>
          <td>151</td>
          <td>1297</td>
          <td>1</td>
          <td>879542847</td>
          <td>38.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>48103</td>
          <td>Love Affair (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99359</th>
          <td>450</td>
          <td>1297</td>
          <td>4</td>
          <td>882812635</td>
          <td>35.0</td>
          <td>F</td>
          <td>educator</td>
          <td>11758</td>
          <td>Love Affair (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99361</th>
          <td>796</td>
          <td>1297</td>
          <td>2</td>
          <td>893047504</td>
          <td>32.0</td>
          <td>F</td>
          <td>writer</td>
          <td>33755</td>
          <td>Love Affair (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99364</th>
          <td>151</td>
          <td>1299</td>
          <td>4</td>
          <td>879543423</td>
          <td>38.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>48103</td>
          <td>Penny Serenade (1941)</td>
          <td>1941-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99370</th>
          <td>796</td>
          <td>1299</td>
          <td>2</td>
          <td>892676043</td>
          <td>32.0</td>
          <td>F</td>
          <td>writer</td>
          <td>33755</td>
          <td>Penny Serenade (1941)</td>
          <td>1941-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99452</th>
          <td>688</td>
          <td>1127</td>
          <td>5</td>
          <td>884153606</td>
          <td>37.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>60476</td>
          <td>Truman Show, The (1998)</td>
          <td>1998-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99477</th>
          <td>34</td>
          <td>1024</td>
          <td>5</td>
          <td>888602618</td>
          <td>38.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>42141</td>
          <td>Mrs. Dalloway (1997)</td>
          <td>1997-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99501</th>
          <td>129</td>
          <td>1176</td>
          <td>4</td>
          <td>883244059</td>
          <td>36.0</td>
          <td>F</td>
          <td>marketing</td>
          <td>07039</td>
          <td>Welcome To Sarajevo (1997)</td>
          <td>1997-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99541</th>
          <td>356</td>
          <td>1294</td>
          <td>4</td>
          <td>891405721</td>
          <td>32.0</td>
          <td>F</td>
          <td>homemaker</td>
          <td>92688</td>
          <td>Ayn Rand: A Sense of Life (1997)</td>
          <td>1998-02-13</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99561</th>
          <td>796</td>
          <td>1415</td>
          <td>3</td>
          <td>893219254</td>
          <td>32.0</td>
          <td>F</td>
          <td>writer</td>
          <td>33755</td>
          <td>Next Karate Kid, The (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99630</th>
          <td>450</td>
          <td>1518</td>
          <td>4</td>
          <td>887138957</td>
          <td>35.0</td>
          <td>F</td>
          <td>educator</td>
          <td>11758</td>
          <td>Losing Isaiah (1995)</td>
          <td>1995-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99642</th>
          <td>577</td>
          <td>1517</td>
          <td>3</td>
          <td>880475644</td>
          <td>36.0</td>
          <td>F</td>
          <td>student</td>
          <td>77845</td>
          <td>Race the Sun (1996)</td>
          <td>1996-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99648</th>
          <td>450</td>
          <td>1521</td>
          <td>3</td>
          <td>882812350</td>
          <td>35.0</td>
          <td>F</td>
          <td>educator</td>
          <td>11758</td>
          <td>Mr. Wonderful (1993)</td>
          <td>1993-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99660</th>
          <td>796</td>
          <td>1522</td>
          <td>3</td>
          <td>893194740</td>
          <td>32.0</td>
          <td>F</td>
          <td>writer</td>
          <td>33755</td>
          <td>Trial by Jury (1994)</td>
          <td>1994-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99695</th>
          <td>577</td>
          <td>1531</td>
          <td>4</td>
          <td>880475408</td>
          <td>36.0</td>
          <td>F</td>
          <td>student</td>
          <td>77845</td>
          <td>Far From Home: The Adventures of Yellow Dog (1...</td>
          <td>1995-01-01</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99852</th>
          <td>450</td>
          <td>1603</td>
          <td>3</td>
          <td>887139728</td>
          <td>35.0</td>
          <td>F</td>
          <td>educator</td>
          <td>11758</td>
          <td>Angela (1995)</td>
          <td>1996-02-16</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>99981</th>
          <td>839</td>
          <td>1664</td>
          <td>1</td>
          <td>875752902</td>
          <td>38.0</td>
          <td>F</td>
          <td>entertainment</td>
          <td>90814</td>
          <td>8 Heads in a Duffel Bag (1997)</td>
          <td>1997-04-18</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
      </tbody>
    </table>
    <p>5183 rows × 30 columns</p>
    </div>



    #### Note
    In the above fragment you HAVE TO ADD parantheses to each and every argument that is being compared else you will get an error.

    As you can see after filtering result tables (i.e. DataFrames) have non-ordered indexes. To fix this trouble you may write the following:


    ```python
    filtered_df = filtered_df.reset_index()
    filtered_df.head(10)
    ```




    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>index</th>
          <th>user_id</th>
          <th>movie_id</th>
          <th>rating</th>
          <th>timestamp</th>
          <th>age</th>
          <th>gender</th>
          <th>occupation</th>
          <th>zip_code</th>
          <th>movie_title</th>
          <th>...</th>
          <th>Fantasy</th>
          <th>Film-Noir</th>
          <th>Horror</th>
          <th>Musical</th>
          <th>Mystery</th>
          <th>Romance</th>
          <th>Sci-Fi</th>
          <th>Thriller</th>
          <th>War</th>
          <th>Western</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>13</td>
          <td>18</td>
          <td>242</td>
          <td>5</td>
          <td>880129305</td>
          <td>35.0</td>
          <td>F</td>
          <td>other</td>
          <td>37212</td>
          <td>Kolya (1996)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>1</th>
          <td>27</td>
          <td>129</td>
          <td>242</td>
          <td>4</td>
          <td>883243972</td>
          <td>36.0</td>
          <td>F</td>
          <td>marketing</td>
          <td>07039</td>
          <td>Kolya (1996)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>2</th>
          <td>39</td>
          <td>34</td>
          <td>242</td>
          <td>5</td>
          <td>888601628</td>
          <td>38.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>42141</td>
          <td>Kolya (1996)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>3</th>
          <td>42</td>
          <td>209</td>
          <td>242</td>
          <td>4</td>
          <td>883589606</td>
          <td>33.0</td>
          <td>F</td>
          <td>educator</td>
          <td>85710</td>
          <td>Kolya (1996)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>4</th>
          <td>110</td>
          <td>861</td>
          <td>242</td>
          <td>5</td>
          <td>881274504</td>
          <td>38.0</td>
          <td>F</td>
          <td>NaN</td>
          <td>14085</td>
          <td>Kolya (1996)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>5</th>
          <td>147</td>
          <td>11</td>
          <td>393</td>
          <td>4</td>
          <td>891905222</td>
          <td>39.0</td>
          <td>F</td>
          <td>other</td>
          <td>30329</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>6</th>
          <td>157</td>
          <td>269</td>
          <td>393</td>
          <td>1</td>
          <td>891451036</td>
          <td>31.0</td>
          <td>F</td>
          <td>librarian</td>
          <td>43201</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>7</th>
          <td>160</td>
          <td>5</td>
          <td>393</td>
          <td>2</td>
          <td>875636265</td>
          <td>33.0</td>
          <td>F</td>
          <td>other</td>
          <td>15213</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>8</th>
          <td>161</td>
          <td>18</td>
          <td>393</td>
          <td>3</td>
          <td>880130930</td>
          <td>35.0</td>
          <td>F</td>
          <td>NaN</td>
          <td>37212</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>9</th>
          <td>167</td>
          <td>151</td>
          <td>393</td>
          <td>2</td>
          <td>879528692</td>
          <td>38.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>48103</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
      </tbody>
    </table>
    <p>10 rows × 31 columns</p>
    </div>




    ```python
    # set 'user_id' 'movie_id' as index
    filtered_df_new = filtered_df.set_index(['user_id','movie_id'])
    filtered_df_new.head(10)

    # Note that set_index takes only a list as an argument to it.
    # if you remove the [] then only the first argument is set as the index.
    ```




    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th></th>
          <th>index</th>
          <th>rating</th>
          <th>timestamp</th>
          <th>age</th>
          <th>gender</th>
          <th>occupation</th>
          <th>zip_code</th>
          <th>movie_title</th>
          <th>release_date</th>
          <th>IMDb_URL</th>
          <th>...</th>
          <th>Fantasy</th>
          <th>Film-Noir</th>
          <th>Horror</th>
          <th>Musical</th>
          <th>Mystery</th>
          <th>Romance</th>
          <th>Sci-Fi</th>
          <th>Thriller</th>
          <th>War</th>
          <th>Western</th>
        </tr>
        <tr>
          <th>user_id</th>
          <th>movie_id</th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>18</th>
          <th>242</th>
          <td>13</td>
          <td>5</td>
          <td>880129305</td>
          <td>35.0</td>
          <td>F</td>
          <td>other</td>
          <td>37212</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>http://us.imdb.com/M/title-exact?Kolya%20(1996)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>129</th>
          <th>242</th>
          <td>27</td>
          <td>4</td>
          <td>883243972</td>
          <td>36.0</td>
          <td>F</td>
          <td>marketing</td>
          <td>07039</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>http://us.imdb.com/M/title-exact?Kolya%20(1996)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>34</th>
          <th>242</th>
          <td>39</td>
          <td>5</td>
          <td>888601628</td>
          <td>38.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>42141</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>http://us.imdb.com/M/title-exact?Kolya%20(1996)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>209</th>
          <th>242</th>
          <td>42</td>
          <td>4</td>
          <td>883589606</td>
          <td>33.0</td>
          <td>F</td>
          <td>educator</td>
          <td>85710</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>http://us.imdb.com/M/title-exact?Kolya%20(1996)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>861</th>
          <th>242</th>
          <td>110</td>
          <td>5</td>
          <td>881274504</td>
          <td>38.0</td>
          <td>F</td>
          <td>NaN</td>
          <td>14085</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>http://us.imdb.com/M/title-exact?Kolya%20(1996)</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>11</th>
          <th>393</th>
          <td>147</td>
          <td>4</td>
          <td>891905222</td>
          <td>39.0</td>
          <td>F</td>
          <td>other</td>
          <td>30329</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>http://us.imdb.com/M/title-exact?Mrs.%20Doubtf...</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>269</th>
          <th>393</th>
          <td>157</td>
          <td>1</td>
          <td>891451036</td>
          <td>31.0</td>
          <td>F</td>
          <td>librarian</td>
          <td>43201</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>http://us.imdb.com/M/title-exact?Mrs.%20Doubtf...</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>5</th>
          <th>393</th>
          <td>160</td>
          <td>2</td>
          <td>875636265</td>
          <td>33.0</td>
          <td>F</td>
          <td>other</td>
          <td>15213</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>http://us.imdb.com/M/title-exact?Mrs.%20Doubtf...</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>18</th>
          <th>393</th>
          <td>161</td>
          <td>3</td>
          <td>880130930</td>
          <td>35.0</td>
          <td>F</td>
          <td>NaN</td>
          <td>37212</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>http://us.imdb.com/M/title-exact?Mrs.%20Doubtf...</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>151</th>
          <th>393</th>
          <td>167</td>
          <td>2</td>
          <td>879528692</td>
          <td>38.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>48103</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>http://us.imdb.com/M/title-exact?Mrs.%20Doubtf...</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
      </tbody>
    </table>
    <p>10 rows × 29 columns</p>
    </div>




    ```python
    # By default, `set_index()` returns a new DataFrame.
    # so you’ll have to specify if you’d like the changes to occur in place.
    # Here we used filtered_df_new to get the new dataframe and now see the type of filtererd_df_new

    print(type(filtered_df_new.index))
    ```

        <class 'pandas.core.indexes.multi.MultiIndex'>


    Notice here that we now have a new sort of 'index' which is `MultiIndex`, which contains information about indexing of DataFrame and allows manipulating with this data.


    ```python
    filtered_df_new.index.names
    # Gives you the names of the two index values we set as a FrozenList
    ```




        FrozenList(['user_id', 'movie_id'])



    Method `get_level_values()` allows to get all values for the corresponding index level.
    `get_level_values(0)` corresponds to 'user_id' and `get_level_values(1)` corresponds to 'movie_id'


    ```python
    print(filtered_df_new.index.get_level_values(0))
    print(filtered_df_new.index.get_level_values(1))
    ```

        Int64Index([ 18, 129,  34, 209, 861,  11, 269,   5,  18, 151,
                    ...
                    129, 356, 796, 450, 577, 450, 796, 577, 450, 839],
                   dtype='int64', name='user_id', length=5183)
        Int64Index([ 242,  242,  242,  242,  242,  393,  393,  393,  393,  393,
                    ...
                    1176, 1294, 1415, 1518, 1517, 1521, 1522, 1531, 1603, 1664],
                   dtype='int64', name='movie_id', length=5183)


    ### Selection by label and position
    Object selection in pandas is now supported by three types of multi-axis indexing.

    * `.loc` works on labels in the index;
    * `.iloc` works on the positions in the index (so it only takes integers);

    The sequence of the following examples demonstrates how we can manipulate with DataFrame’s rows.
    At first let’s get the first row of movies:


    ```python
    movies.loc[0]
    ```




        user_id                                                     196
        movie_id                                                    242
        rating                                                        3
        timestamp                                             881250949
        age                                                          49
        gender                                                        M
        occupation                                               writer
        zip_code                                                  55105
        movie_title                                        Kolya (1996)
        release_date                                1997-01-24 00:00:00
        IMDb_URL        http://us.imdb.com/M/title-exact?Kolya%20(1996)
        unknown                                                       0
        Action                                                        0
        Adventure                                                     0
        Animation                                                     0
        Childrens                                                     0
        Comedy                                                        1
        Crime                                                         0
        Documentary                                                   0
        Drama                                                         0
        Fantasy                                                       0
        Film-Noir                                                     0
        Horror                                                        0
        Musical                                                       0
        Mystery                                                       0
        Romance                                                       0
        Sci-Fi                                                        0
        Thriller                                                      0
        War                                                           0
        Western                                                       0
        Name: 0, dtype: object




    ```python
    movies.loc[1:3]
    ```




    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>user_id</th>
          <th>movie_id</th>
          <th>rating</th>
          <th>timestamp</th>
          <th>age</th>
          <th>gender</th>
          <th>occupation</th>
          <th>zip_code</th>
          <th>movie_title</th>
          <th>release_date</th>
          <th>...</th>
          <th>Fantasy</th>
          <th>Film-Noir</th>
          <th>Horror</th>
          <th>Musical</th>
          <th>Mystery</th>
          <th>Romance</th>
          <th>Sci-Fi</th>
          <th>Thriller</th>
          <th>War</th>
          <th>Western</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>1</th>
          <td>305</td>
          <td>242</td>
          <td>5</td>
          <td>886307828</td>
          <td>23.0</td>
          <td>M</td>
          <td>programmer</td>
          <td>94086</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>2</th>
          <td>6</td>
          <td>242</td>
          <td>4</td>
          <td>883268170</td>
          <td>42.0</td>
          <td>M</td>
          <td>executive</td>
          <td>98101</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>3</th>
          <td>234</td>
          <td>242</td>
          <td>4</td>
          <td>891033261</td>
          <td>60.0</td>
          <td>M</td>
          <td>retired</td>
          <td>94702</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
      </tbody>
    </table>
    <p>3 rows × 30 columns</p>
    </div>



    If you want to return specific columns then you have to specify them as a separate argument of .loc


    ```python
    movies.loc[1:3 , 'movie_title']
    ```




        1    Kolya (1996)
        2    Kolya (1996)
        3    Kolya (1996)
        Name: movie_title, dtype: object




    ```python
    movies.loc[1:5 , ['movie_title','age','gender']]
    # If more than one column is to be selected then you have to give the second argument of .loc as a list
    ```




    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>movie_title</th>
          <th>age</th>
          <th>gender</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>1</th>
          <td>Kolya (1996)</td>
          <td>23.0</td>
          <td>M</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Kolya (1996)</td>
          <td>42.0</td>
          <td>M</td>
        </tr>
        <tr>
          <th>3</th>
          <td>Kolya (1996)</td>
          <td>60.0</td>
          <td>M</td>
        </tr>
        <tr>
          <th>4</th>
          <td>Kolya (1996)</td>
          <td>31.0</td>
          <td>M</td>
        </tr>
        <tr>
          <th>5</th>
          <td>Kolya (1996)</td>
          <td>26.0</td>
          <td>M</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    # movies.iloc[1:5 , ['movie_title','age','gender']]
    # Gives error as iloc only uses integer values
    ```


    ```python
    movies.iloc[0]
    ```




        user_id                                                     196
        movie_id                                                    242
        rating                                                        3
        timestamp                                             881250949
        age                                                          49
        gender                                                        M
        occupation                                               writer
        zip_code                                                  55105
        movie_title                                        Kolya (1996)
        release_date                                1997-01-24 00:00:00
        IMDb_URL        http://us.imdb.com/M/title-exact?Kolya%20(1996)
        unknown                                                       0
        Action                                                        0
        Adventure                                                     0
        Animation                                                     0
        Childrens                                                     0
        Comedy                                                        1
        Crime                                                         0
        Documentary                                                   0
        Drama                                                         0
        Fantasy                                                       0
        Film-Noir                                                     0
        Horror                                                        0
        Musical                                                       0
        Mystery                                                       0
        Romance                                                       0
        Sci-Fi                                                        0
        Thriller                                                      0
        War                                                           0
        Western                                                       0
        Name: 0, dtype: object




    ```python
    movies.iloc[1:5]
    ```




    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>user_id</th>
          <th>movie_id</th>
          <th>rating</th>
          <th>timestamp</th>
          <th>age</th>
          <th>gender</th>
          <th>occupation</th>
          <th>zip_code</th>
          <th>movie_title</th>
          <th>release_date</th>
          <th>...</th>
          <th>Fantasy</th>
          <th>Film-Noir</th>
          <th>Horror</th>
          <th>Musical</th>
          <th>Mystery</th>
          <th>Romance</th>
          <th>Sci-Fi</th>
          <th>Thriller</th>
          <th>War</th>
          <th>Western</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>1</th>
          <td>305</td>
          <td>242</td>
          <td>5</td>
          <td>886307828</td>
          <td>23.0</td>
          <td>M</td>
          <td>programmer</td>
          <td>94086</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>2</th>
          <td>6</td>
          <td>242</td>
          <td>4</td>
          <td>883268170</td>
          <td>42.0</td>
          <td>M</td>
          <td>executive</td>
          <td>98101</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>3</th>
          <td>234</td>
          <td>242</td>
          <td>4</td>
          <td>891033261</td>
          <td>60.0</td>
          <td>M</td>
          <td>retired</td>
          <td>94702</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>4</th>
          <td>63</td>
          <td>242</td>
          <td>3</td>
          <td>875747190</td>
          <td>31.0</td>
          <td>M</td>
          <td>marketing</td>
          <td>75240</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
      </tbody>
    </table>
    <p>4 rows × 30 columns</p>
    </div>




    ```python
    # movies.select(lambda x: x%2==0).head() is the same as :
    movies.loc[movies.index.map(lambda x: x%2==0)].head()

    # .select() has been deprecated for now and will be completely removed in future updates so use .loc
    ```




    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>user_id</th>
          <th>movie_id</th>
          <th>rating</th>
          <th>timestamp</th>
          <th>age</th>
          <th>gender</th>
          <th>occupation</th>
          <th>zip_code</th>
          <th>movie_title</th>
          <th>release_date</th>
          <th>...</th>
          <th>Fantasy</th>
          <th>Film-Noir</th>
          <th>Horror</th>
          <th>Musical</th>
          <th>Mystery</th>
          <th>Romance</th>
          <th>Sci-Fi</th>
          <th>Thriller</th>
          <th>War</th>
          <th>Western</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>196</td>
          <td>242</td>
          <td>3</td>
          <td>881250949</td>
          <td>49.0</td>
          <td>M</td>
          <td>writer</td>
          <td>55105</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>2</th>
          <td>6</td>
          <td>242</td>
          <td>4</td>
          <td>883268170</td>
          <td>42.0</td>
          <td>M</td>
          <td>executive</td>
          <td>98101</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>4</th>
          <td>63</td>
          <td>242</td>
          <td>3</td>
          <td>875747190</td>
          <td>31.0</td>
          <td>M</td>
          <td>marketing</td>
          <td>75240</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>6</th>
          <td>201</td>
          <td>242</td>
          <td>4</td>
          <td>884110598</td>
          <td>27.0</td>
          <td>M</td>
          <td>writer</td>
          <td>E2A4H</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>8</th>
          <td>13</td>
          <td>242</td>
          <td>2</td>
          <td>881515193</td>
          <td>47.0</td>
          <td>M</td>
          <td>educator</td>
          <td>29206</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
      </tbody>
    </table>
    <p>5 rows × 30 columns</p>
    </div>
