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



    ## Working with Missing Data
    Pandas primarily uses the value np.nan to represent missing data (in table missed/empty value are marked by NaN). It is by default not included in computations. Missing data creates many issues at mathematical or computational tasks with DataFrames and Series and it’s important to know how fight with these values.


    ```python
    ages = movies['age']
    sum(ages)
    ```




        nan



    This is because there are so many cases where Age isn't given and hence takes on the value of np.nan.
    We can use `fillna()`a very effecient pandas method for filling missing values


    ```python
    ages = movies['age'].fillna(0)
    sum(ages)
    ```




        3089983.0



    This fills all the values with 0 and calculates the sum.
    To remain only rows with non-null values you can use method `dropna()`


    ```python
    ages = movies['age'].dropna()
    sum(ages)
    ```




        3089983.0




    ```python
    movies_nonnull = movies.dropna()
    movies_nonnull.head(20)
    #14th value was dropped because it had a missing value in a column
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
        <tr>
          <th>5</th>
          <td>181</td>
          <td>242</td>
          <td>1</td>
          <td>878961814</td>
          <td>26.0</td>
          <td>M</td>
          <td>executive</td>
          <td>21218</td>
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
          <th>7</th>
          <td>249</td>
          <td>242</td>
          <td>5</td>
          <td>879571438</td>
          <td>25.0</td>
          <td>M</td>
          <td>student</td>
          <td>84103</td>
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
        <tr>
          <th>9</th>
          <td>279</td>
          <td>242</td>
          <td>3</td>
          <td>877756647</td>
          <td>33.0</td>
          <td>M</td>
          <td>programmer</td>
          <td>85251</td>
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
          <th>10</th>
          <td>145</td>
          <td>242</td>
          <td>5</td>
          <td>875269755</td>
          <td>31.0</td>
          <td>M</td>
          <td>entertainment</td>
          <td>V3N4P</td>
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
          <th>11</th>
          <td>90</td>
          <td>242</td>
          <td>4</td>
          <td>891382267</td>
          <td>60.0</td>
          <td>M</td>
          <td>educator</td>
          <td>78155</td>
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
          <th>12</th>
          <td>271</td>
          <td>242</td>
          <td>4</td>
          <td>885844495</td>
          <td>51.0</td>
          <td>M</td>
          <td>engineer</td>
          <td>22932</td>
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
          <th>15</th>
          <td>207</td>
          <td>242</td>
          <td>4</td>
          <td>890793823</td>
          <td>39.0</td>
          <td>M</td>
          <td>marketing</td>
          <td>92037</td>
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
          <th>16</th>
          <td>14</td>
          <td>242</td>
          <td>4</td>
          <td>876964570</td>
          <td>45.0</td>
          <td>M</td>
          <td>scientist</td>
          <td>55106</td>
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
          <th>17</th>
          <td>113</td>
          <td>242</td>
          <td>2</td>
          <td>875075887</td>
          <td>47.0</td>
          <td>M</td>
          <td>executive</td>
          <td>95032</td>
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
          <th>19</th>
          <td>296</td>
          <td>242</td>
          <td>4</td>
          <td>884196057</td>
          <td>43.0</td>
          <td>F</td>
          <td>administrator</td>
          <td>16803</td>
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
          <th>20</th>
          <td>154</td>
          <td>242</td>
          <td>3</td>
          <td>879138235</td>
          <td>25.0</td>
          <td>M</td>
          <td>student</td>
          <td>53703</td>
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
          <th>21</th>
          <td>270</td>
          <td>242</td>
          <td>5</td>
          <td>876953744</td>
          <td>18.0</td>
          <td>F</td>
          <td>student</td>
          <td>63119</td>
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
    <p>20 rows × 30 columns</p>
    </div>




    ```python
    movies_notnull = movies.dropna(how='all',subset=['age','occupation'])
    #Drops all nan values from movies belonging to age and occupation
    movies_notnull.info()
    #Notice how age and occupation now have nearly 6000 lesser values
    ```

        <class 'pandas.core.frame.DataFrame'>
        Int64Index: 99616 entries, 0 to 99999
        Data columns (total 30 columns):
        user_id         99616 non-null int64
        movie_id        99616 non-null int64
        rating          99616 non-null int64
        timestamp       99616 non-null int64
        age             93731 non-null float64
        gender          99616 non-null object
        occupation      93806 non-null object
        zip_code        99616 non-null object
        movie_title     99616 non-null object
        release_date    99607 non-null datetime64[ns]
        IMDb_URL        99603 non-null object
        unknown         99616 non-null int64
        Action          99616 non-null int64
        Adventure       99616 non-null int64
        Animation       99616 non-null int64
        Childrens       99616 non-null int64
        Comedy          99616 non-null int64
        Crime           99616 non-null int64
        Documentary     99616 non-null int64
        Drama           99616 non-null int64
        Fantasy         99616 non-null int64
        Film-Noir       99616 non-null int64
        Horror          99616 non-null int64
        Musical         99616 non-null int64
        Mystery         99616 non-null int64
        Romance         99616 non-null int64
        Sci-Fi          99616 non-null int64
        Thriller        99616 non-null int64
        War             99616 non-null int64
        Western         99616 non-null int64
        dtypes: datetime64[ns](1), float64(1), int64(23), object(5)
        memory usage: 23.6+ MB


    Thus, if `how='all'`, we get DataFrame, where all values in both columns from subset are NaN.

    If `how='any'`, we get DataFrame, where at least one contains NaN.


    ```python
    movies.describe()
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
          <th>unknown</th>
          <th>Action</th>
          <th>Adventure</th>
          <th>Animation</th>
          <th>Childrens</th>
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
          <th>count</th>
          <td>100000.00000</td>
          <td>100000.000000</td>
          <td>100000.000000</td>
          <td>1.000000e+05</td>
          <td>93731.000000</td>
          <td>100000.0000</td>
          <td>100000.000000</td>
          <td>100000.000000</td>
          <td>100000.000000</td>
          <td>100000.000000</td>
          <td>...</td>
          <td>100000.000000</td>
          <td>100000.000000</td>
          <td>100000.000000</td>
          <td>100000.000000</td>
          <td>100000.000000</td>
          <td>100000.000000</td>
          <td>100000.00000</td>
          <td>100000.00000</td>
          <td>100000.000000</td>
          <td>100000.000000</td>
        </tr>
        <tr>
          <th>mean</th>
          <td>462.48475</td>
          <td>425.530130</td>
          <td>3.529860</td>
          <td>8.835289e+08</td>
          <td>32.966500</td>
          <td>0.0001</td>
          <td>0.255890</td>
          <td>0.137530</td>
          <td>0.036050</td>
          <td>0.071820</td>
          <td>...</td>
          <td>0.013520</td>
          <td>0.017330</td>
          <td>0.053170</td>
          <td>0.049540</td>
          <td>0.052450</td>
          <td>0.194610</td>
          <td>0.12730</td>
          <td>0.21872</td>
          <td>0.093980</td>
          <td>0.018540</td>
        </tr>
        <tr>
          <th>std</th>
          <td>266.61442</td>
          <td>330.798356</td>
          <td>1.125674</td>
          <td>5.343856e+06</td>
          <td>11.561809</td>
          <td>0.0100</td>
          <td>0.436362</td>
          <td>0.344408</td>
          <td>0.186416</td>
          <td>0.258191</td>
          <td>...</td>
          <td>0.115487</td>
          <td>0.130498</td>
          <td>0.224373</td>
          <td>0.216994</td>
          <td>0.222934</td>
          <td>0.395902</td>
          <td>0.33331</td>
          <td>0.41338</td>
          <td>0.291802</td>
          <td>0.134894</td>
        </tr>
        <tr>
          <th>min</th>
          <td>1.00000</td>
          <td>1.000000</td>
          <td>1.000000</td>
          <td>8.747247e+08</td>
          <td>7.000000</td>
          <td>0.0000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>...</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.00000</td>
          <td>0.00000</td>
          <td>0.000000</td>
          <td>0.000000</td>
        </tr>
        <tr>
          <th>25%</th>
          <td>254.00000</td>
          <td>175.000000</td>
          <td>3.000000</td>
          <td>8.794487e+08</td>
          <td>24.000000</td>
          <td>0.0000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>...</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.00000</td>
          <td>0.00000</td>
          <td>0.000000</td>
          <td>0.000000</td>
        </tr>
        <tr>
          <th>50%</th>
          <td>447.00000</td>
          <td>322.000000</td>
          <td>4.000000</td>
          <td>8.828269e+08</td>
          <td>30.000000</td>
          <td>0.0000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>...</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.00000</td>
          <td>0.00000</td>
          <td>0.000000</td>
          <td>0.000000</td>
        </tr>
        <tr>
          <th>75%</th>
          <td>682.00000</td>
          <td>631.000000</td>
          <td>4.000000</td>
          <td>8.882600e+08</td>
          <td>40.000000</td>
          <td>0.0000</td>
          <td>1.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>...</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.000000</td>
          <td>0.00000</td>
          <td>0.00000</td>
          <td>0.000000</td>
          <td>0.000000</td>
        </tr>
        <tr>
          <th>max</th>
          <td>943.00000</td>
          <td>1682.000000</td>
          <td>5.000000</td>
          <td>8.932866e+08</td>
          <td>73.000000</td>
          <td>1.0000</td>
          <td>1.000000</td>
          <td>1.000000</td>
          <td>1.000000</td>
          <td>1.000000</td>
          <td>...</td>
          <td>1.000000</td>
          <td>1.000000</td>
          <td>1.000000</td>
          <td>1.000000</td>
          <td>1.000000</td>
          <td>1.000000</td>
          <td>1.00000</td>
          <td>1.00000</td>
          <td>1.000000</td>
          <td>1.000000</td>
        </tr>
      </tbody>
    </table>
    <p>8 rows × 24 columns</p>
    </div>



    At first, let’s find all unique dates in `‘release_date’` column of `movies` and then select only dates in range lower than 1995.


    ```python
    movies['release_date'] = movies['release_date'].map(pd.to_datetime)
    # We map it to_datetime as pandas has a set way to deal with dates and then we can effectively work with dates.
    unique_dates = movies['release_date'].drop_duplicates().dropna()
    # Drops duplicates and nan values
    unique_dates
    ```




        0       1997-01-24
        117     1993-01-01
        309     1994-01-01
        409     1997-07-11
        455     1986-01-01
        785     1997-01-01
        881     1987-01-01
        1137    1979-01-01
        1253    1996-04-26
        1525    1995-01-01
        1557    1996-03-08
        1850    1996-11-15
        2331    1990-01-01
        2851    1971-01-01
        2972    1978-01-01
        3432    1997-07-04
        3735    1996-04-12
        4269    1996-12-18
        4347    1996-04-23
        4583    1996-10-04
        4745    1997-06-27
        4751    1997-01-31
        4798    1996-06-28
        4961    1988-01-01
        5208    1995-10-30
        5392    1996-02-09
        5863    1996-09-28
        6861    1997-05-09
        7058    1996-10-11
        7186    1997-08-15
                   ...    
        96679   1996-09-24
        96855   1997-01-29
        96948   1996-09-04
        97195   1996-09-16
        97434   1997-12-18
        97639   1998-03-17
        97816   1996-06-05
        98068   1996-12-15
        98546   1998-04-03
        98574   1996-05-17
        98590   1998-03-10
        98739   1996-10-26
        98748   1998-01-23
        98786   1998-03-14
        98856   1932-01-01
        98969   1996-01-15
        99205   1996-04-02
        99280   1998-02-20
        99321   1997-04-22
        99598   1998-10-09
        99650   1998-02-01
        99702   1996-07-22
        99737   1926-01-01
        99813   1998-01-21
        99885   1998-02-11
        99938   1986-04-26
        99940   1998-03-06
        99958   1996-09-18
        99967   1996-02-28
        99977   1997-04-30
        Name: release_date, Length: 240, dtype: datetime64[ns]




    ```python
    # find dates with year lower/equal than 1995
    unique_dates_1 = filter(lambda x: x.year <= 1995, unique_dates)
    # filter() takes two arguments. First one should return only boolean values and the second one is the variable over which ititerates over.
    # This basically takes unique_dates and uses the lambda function (here, it returns bool values) and filters True cases.

    unique_dates_1
    ```




        <filter at 0x1187af6a0>



    Here we have used `drop_duplicates()` method to select only `unique` Series values. Then we can filter `movies` with respect to `release_date` condition. Each `datetime` Python object possesses with attributes `year`, `month`, `day`, etc. allowing to extract values of year, month, day, etc. from the date. We call the new DataFrame as `old_movies`.


    ```python
    old_movies = movies[movies['release_date'].isin(unique_dates_1)]
    old_movies.head()
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
          <th>117</th>
          <td>196</td>
          <td>393</td>
          <td>4</td>
          <td>881251863</td>
          <td>49.0</td>
          <td>M</td>
          <td>writer</td>
          <td>55105</td>
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
          <th>118</th>
          <td>22</td>
          <td>393</td>
          <td>4</td>
          <td>878886989</td>
          <td>25.0</td>
          <td>M</td>
          <td>writer</td>
          <td>40206</td>
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
          <th>119</th>
          <td>244</td>
          <td>393</td>
          <td>3</td>
          <td>880607365</td>
          <td>28.0</td>
          <td>M</td>
          <td>technician</td>
          <td>80525</td>
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
          <th>120</th>
          <td>298</td>
          <td>393</td>
          <td>4</td>
          <td>884183099</td>
          <td>44.0</td>
          <td>M</td>
          <td>executive</td>
          <td>01581</td>
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
          <th>121</th>
          <td>286</td>
          <td>393</td>
          <td>4</td>
          <td>877534481</td>
          <td>27.0</td>
          <td>M</td>
          <td>student</td>
          <td>15217</td>
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
      </tbody>
    </table>
    <p>5 rows × 30 columns</p>
    </div>



    Now we may filter DataFrame `old_movies` by `age` and `rating`. Lets’ drop `timestamp`, `zip_code`


    ```python
    # get all users with age less than 25 that rated old movies higher than 3
    old_movies_watch = old_movies[(old_movies['age']<25) & (old_movies['rating']>3)]
    # Drop timestamp and zip_code
    old_movies_watch = old_movies_watch.drop(['timestamp', 'zip_code'],axis=1)

    old_movies_watch.head()
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
          <th>age</th>
          <th>gender</th>
          <th>occupation</th>
          <th>movie_title</th>
          <th>release_date</th>
          <th>IMDb_URL</th>
          <th>unknown</th>
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
          <th>124</th>
          <td>303</td>
          <td>393</td>
          <td>4</td>
          <td>19.0</td>
          <td>M</td>
          <td>student</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>http://us.imdb.com/M/title-exact?Mrs.%20Doubtf...</td>
          <td>0</td>
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
          <th>135</th>
          <td>276</td>
          <td>393</td>
          <td>4</td>
          <td>21.0</td>
          <td>M</td>
          <td>student</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>http://us.imdb.com/M/title-exact?Mrs.%20Doubtf...</td>
          <td>0</td>
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
          <th>153</th>
          <td>128</td>
          <td>393</td>
          <td>4</td>
          <td>24.0</td>
          <td>F</td>
          <td>marketing</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>http://us.imdb.com/M/title-exact?Mrs.%20Doubtf...</td>
          <td>0</td>
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
          <th>162</th>
          <td>130</td>
          <td>393</td>
          <td>5</td>
          <td>20.0</td>
          <td>M</td>
          <td>none</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>http://us.imdb.com/M/title-exact?Mrs.%20Doubtf...</td>
          <td>0</td>
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
          <th>183</th>
          <td>314</td>
          <td>393</td>
          <td>4</td>
          <td>20.0</td>
          <td>F</td>
          <td>student</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
          <td>http://us.imdb.com/M/title-exact?Mrs.%20Doubtf...</td>
          <td>0</td>
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
    <p>5 rows × 28 columns</p>
    </div>



    `Pandas` has support for accelerating certain types of binary numerical and boolean operations using the `numexpr `library (it uses smart chunking, caching, and multiple cores) and the `bottleneck` libraries (is a set of specialized cython routines that are especially fast when dealing with arrays that have NaNs). It allows one to increase pandas functionality a lot. This advantage is shown for some boolean and calculation operations. To count the time elapsed on operation performing we will use the decorator


    ```python
    # this function counts the time for a particular operation

    def timer(func):
        from datetime import datetime
        def wrapper(*args):
            start = datetime.now()
            func(*args)
            end = datetime.now()
            return 'elapsed time = {' + str(end - start)+'}'
        return wrapper

    ```


    ```python
    import random
    n = 100
    # generate rangon datasets
    df_1 = pd.DataFrame({'col :'+str(i):[random.randint(-100,100) for j in range(n)]for i in range(n)})
    # here we pass a dictionary to the DataFrame() constructor.
    # The key is "col : i" where i can take random values and the value for those keys is i.

    df_2 = pd.DataFrame({'col :'+str(i):[random.randint(-100,100) for j in range(n)] for i in range(n)})

    @timer
    def direct_comparison(df_1, df_2):
        bool_df = pd.DataFrame({'col_{}'.format(i): [True for j in range(n)] for i in range(n)})
        for i in range(len(df_1.index)):
            for j in range(len(df_1.loc[i])):
                if df_1.loc[i, df_1.columns[j]] >= df_2.loc[i, df_2.columns[j]]:
                    bool_df.loc[i,bool_df.columns[j]] = False
        return bool_df

    @timer
    def pandas_comparison(df_1, df_2):
        return df_1 < df_2

    print ('direct_comparison:', (direct_comparison(df_1, df_2)))
    print ('pandas_comparison:', (pandas_comparison(df_1, df_2)))
    ```

        direct_comparison: elapsed time = {0:00:03.362719}
        pandas_comparison: elapsed time = {0:00:00.029600}


    As you can see, the difference in speed is too noticeable.

    Besides, pandas possesses methods `eq` (equal), `ne` (not equal), `lt` (less then), `gt` (greater than), `le` (less or equal) and `ge` (greater or equal) for simplifying boolean comparison

    ## Matrix Addition


    ```python
    df = pd.DataFrame({'A':[1,2,3],'B':[-2,-3,-4],"C":[7,8,9]})
    dfa = pd.DataFrame({'A':[1,2,3],'D':[6,7,8],"C":[12,12,12]})
    dfc = df + dfa
    dfc
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
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>2</td>
          <td>NaN</td>
          <td>19</td>
          <td>NaN</td>
        </tr>
        <tr>
          <th>1</th>
          <td>4</td>
          <td>NaN</td>
          <td>20</td>
          <td>NaN</td>
        </tr>
        <tr>
          <th>2</th>
          <td>6</td>
          <td>NaN</td>
          <td>21</td>
          <td>NaN</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    df.le(dfa)
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
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>True</td>
          <td>False</td>
          <td>True</td>
          <td>False</td>
        </tr>
        <tr>
          <th>1</th>
          <td>True</td>
          <td>False</td>
          <td>True</td>
          <td>False</td>
        </tr>
        <tr>
          <th>2</th>
          <td>True</td>
          <td>False</td>
          <td>True</td>
          <td>False</td>
        </tr>
      </tbody>
    </table>
    </div>



    You can also apply the reductions: `empty`, `any()`, `all()`, and `bool()` to provide a way to summarize a boolean result:


    ```python
    (df<0).all()
    ```




        A    False
        B     True
        C    False
        dtype: bool




    ```python
    # here horyzontal direction for comparison is taking into account and we check all row’s items
    (df < 0).all(axis=1)
    ```




        0    False
        1    False
        2    False
        dtype: bool




    ```python
    # here vertical direction for comparison is taking into
    # account and we check if just one column’s item satisfies the condition
    (df < 0).any()
    ```




        A    False
        B     True
        C    False
        dtype: bool




    ```python
    # here we check if all DataFrame's items satisfy the condition
    (df < 0).any().any()
    ```




        True




    ```python
    # here we check if DataFrame no one element
    df.empty
    ```




        False



    ### Descriptive Statistics


    |Function|Description|
    |--|-------------------------------|
    |abs|absolute value|
    |count|number of non-null observations|
    |cumsum|cumulative sum (a sequence of partial sums of a given sequence)|
    |sum|sum of values|
    |mean|mean of values|
    |mad|mean absolute deviation|
    |median|arithmetic median of values|
    |min|minimum value|
    |max|maximum value|
    |mode|mode|
    |prod|product of values|
    |std|unbiased standard deviation|
    |var|unbiased variance|



    ```python
    print("Sum : ", movies['age'].sum())
    ```

        Sum :  3089983.0



    ```python
    print(df)
    ```

           A  B  C
        0  1 -2  7
        1  2 -3  8
        2  3 -4  9



    ```python
    print("Mean : ")
    print(df.mean())

    print("\nMean of all Mean Values: ")
    print(df.mean().mean())

    print("\nMedian: ")
    print(df.median())

    print("\nStandard Deviation: ")
    print(df.std())

    print("\nVariance: ")
    print(df.var())

    print("\nMax: ")
    print(df.max())
    ```

        Mean :
        A    2.0
        B   -3.0
        C    8.0
        dtype: float64

        Mean of all Mean Values:
        2.3333333333333335

        Median:
        A    2.0
        B   -3.0
        C    8.0
        dtype: float64

        Standard Deviation:
        A    1.0
        B    1.0
        C    1.0
        dtype: float64

        Variance:
        A    1.0
        B    1.0
        C    1.0
        dtype: float64

        Max:
        A    3
        B   -2
        C    9
        dtype: int64


    ## Function Applications
    When you need to make some transformations with some column’s or row’s elements, then method `map` will be helpful (it works like pure Python function `map()` ). But there is also possibility to apply some function to each DataFrame element (not to a column or a row) – method `apply(map)` aids in this case.



    ```python
    movies.loc[:, (movies.dtypes == np.int64) | (movies.dtypes == np.float64)].apply(np.mean)
    # This calculates the mean of all the columns present in movies
    ```




        user_id        4.624848e+02
        movie_id       4.255301e+02
        rating         3.529860e+00
        timestamp      8.835289e+08
        age            3.296650e+01
        unknown        1.000000e-04
        Action         2.558900e-01
        Adventure      1.375300e-01
        Animation      3.605000e-02
        Childrens      7.182000e-02
        Comedy         2.983200e-01
        Crime          8.055000e-02
        Documentary    7.580000e-03
        Drama          3.989500e-01
        Fantasy        1.352000e-02
        Film-Noir      1.733000e-02
        Horror         5.317000e-02
        Musical        4.954000e-02
        Mystery        5.245000e-02
        Romance        1.946100e-01
        Sci-Fi         1.273000e-01
        Thriller       2.187200e-01
        War            9.398000e-02
        Western        1.854000e-02
        dtype: float64




    ```python
    # to print mean of all row values in movies :
    movies.loc[:,(movies.dtypes==np.int64) | (movies.dtypes==np.float64)].apply(np.mean, axis = 1)
    ```




        0        3.671881e+07
        1        3.692952e+07
        2        3.680285e+07
        3        3.712641e+07
        4        3.648948e+07
        5        3.662343e+07
        6        3.683796e+07
        7        3.664883e+07
        8        3.672981e+07
        9        3.657322e+07
        10       3.646959e+07
        11       3.714094e+07
        12       3.691021e+07
        13       3.667207e+07
        14       3.868486e+07
        15       3.711643e+07
        16       3.654020e+07
        17       3.646151e+07
        18       3.825258e+07
        19       3.684153e+07
        20       3.663078e+07
        21       3.653976e+07
        22       3.690734e+07
        23       3.700433e+07
        24       3.804139e+07
        25       3.704913e+07
        26       3.715335e+07
        27       3.680185e+07
        28       3.682009e+07
        29       3.682872e+07
                     ...     
        99970    3.836551e+07
        99971    3.702680e+07
        99972    3.703066e+07
        99973    3.705424e+07
        99974    3.661341e+07
        99975    3.714594e+07
        99976    3.714594e+07
        99977    3.714592e+07
        99978    3.714594e+07
        99979    3.714594e+07
        99980    3.714592e+07
        99981    3.648981e+07
        99982    3.869825e+07
        99983    3.720672e+07
        99984    3.714594e+07
        99985    3.714584e+07
        99986    3.876098e+07
        99987    3.704094e+07
        99988    3.712668e+07
        99989    3.696509e+07
        99990    3.712652e+07
        99991    3.713393e+07
        99992    3.807540e+07
        99993    3.684269e+07
        99994    3.678404e+07
        99995    3.705384e+07
        99996    3.866487e+07
        99997    3.705384e+07
        99998    3.696514e+07
        99999    3.670202e+07
        Length: 100000, dtype: float64



    ### Remember

    The attribute axis define the horizontal `(axis=1)` or vertical direction for calculations `(axis=0)`

    ### Groupby with Dictionary


    ```python
    import numpy as np
    import pandas as pd
    ```


    ```python
    d = {'id':[1,2,3],
         'Column 1.1':[14,15,16],
         'Column 1.2':[10,10,10],
         'Column 1.3':[1,4,5],
         'Column 2.1':[1,2,3],
         'Column 2.2':[10,10,10],
    }
    df = pd.DataFrame(d)
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
          <th>id</th>
          <th>Column 1.1</th>
          <th>Column 1.2</th>
          <th>Column 1.3</th>
          <th>Column 2.1</th>
          <th>Column 2.2</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1</td>
          <td>14</td>
          <td>10</td>
          <td>1</td>
          <td>1</td>
          <td>10</td>
        </tr>
        <tr>
          <th>1</th>
          <td>2</td>
          <td>15</td>
          <td>10</td>
          <td>4</td>
          <td>2</td>
          <td>10</td>
        </tr>
        <tr>
          <th>2</th>
          <td>3</td>
          <td>16</td>
          <td>10</td>
          <td>5</td>
          <td>3</td>
          <td>10</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    groupby_dict = {'Column 1.1':'Column 1','Column 1.2':'Column 1','Column 1.3':'Column 1','Column 2.1':'Column 2','Column 2.2':'Column 2'}
    df = df.set_index('id')
    df=df.groupby(groupby_dict,axis=1).min()
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
          <th>Column 1</th>
          <th>Column 2</th>
        </tr>
        <tr>
          <th>id</th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>1</th>
          <td>1</td>
          <td>1</td>
        </tr>
        <tr>
          <th>2</th>
          <td>4</td>
          <td>2</td>
        </tr>
        <tr>
          <th>3</th>
          <td>5</td>
          <td>3</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    import numpy as np
    import pandas as pd

    ```


    ```python
    dict = {
        "ID":[1,2,3],
        "Movies":["The Godfather","Fight Club","Casablanca"],
        "Week_1_Viewers":[30,30,40],
        "Week_2_Viewers":[60,40,80],
        "Week_3_Viewers":[40,20,20]
    };
    df = pd.DataFrame(dict);
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
          <th>ID</th>
          <th>Movies</th>
          <th>Week_1_Viewers</th>
          <th>Week_2_Viewers</th>
          <th>Week_3_Viewers</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1</td>
          <td>The Godfather</td>
          <td>30</td>
          <td>60</td>
          <td>40</td>
        </tr>
        <tr>
          <th>1</th>
          <td>2</td>
          <td>Fight Club</td>
          <td>30</td>
          <td>40</td>
          <td>20</td>
        </tr>
        <tr>
          <th>2</th>
          <td>3</td>
          <td>Casablanca</td>
          <td>40</td>
          <td>80</td>
          <td>20</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    mapping = {"Week_1_Viewers":"Total_Viewers",
               "Week_2_Viewers":"Total_Viewers",
               "Week_3_Viewers":"Total_Viewers",
               "Movies":"Movies"
              }
    df = df.set_index('ID')
    df=df.groupby(mapping,axis=1).sum()
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
          <th>Movies</th>
          <th>Total_Viewers</th>
        </tr>
        <tr>
          <th>ID</th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>1</th>
          <td>The Godfather</td>
          <td>130</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Fight Club</td>
          <td>90</td>
        </tr>
        <tr>
          <th>3</th>
          <td>Casablanca</td>
          <td>140</td>
        </tr>
      </tbody>
    </table>
    </div>



    ### Breaking up a String into columns using regex


    ```python
    dict = {'movie_data':['The Godfather 1972 9.2',
                         'Bird Box 2018 6.8',
                         'Fight Club 1999 8.8']
            }
    df = pd.DataFrame(dict)
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
          <th>movie_data</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>The Godfather 1972 9.2</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Bird Box 2018 6.8</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Fight Club 1999 8.8</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    df['Name'] = df['movie_data'].str.extract('(\w*\s\w*)', expand=True)
    df['Year'] = df['movie_data'].str.extract('(\d\d\d\d)', expand=True)
    df['Rating'] = df['movie_data'].str.extract('(\d\.\d)', expand=True)
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
          <th>movie_data</th>
          <th>Name</th>
          <th>Year</th>
          <th>Rating</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>The Godfather 1972 9.2</td>
          <td>The Godfather</td>
          <td>1972</td>
          <td>9.2</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Bird Box 2018 6.8</td>
          <td>Bird Box</td>
          <td>2018</td>
          <td>6.8</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Fight Club 1999 8.8</td>
          <td>Fight Club</td>
          <td>1999</td>
          <td>8.8</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    import re

    movie_data = ["Name:The Godfather Year: 1972 Rating: 9.2",
                  "Name:Bird Box Year: 2018 Rating: 6.8",
                  "Name:Fight Club Year: 1999 Rating: 8.8"]
    movies={"Name":[],
           "Year":[],
           "Rating":[]}

    ```


    ```python
    for item in movie_data:
        name_field = re.search("Name:.*",item)
        if name_field is not None:
            name = re.search('\w*\s\w*',name_field.group())
        else:
            name = None
        movies["Name"].append(name.group())
        year_field = re.search("Year: .*",item)
        if year_field is not None:
            year = re.search('\s\d\d\d\d',year_field.group())
        else:
            year = None
        movies["Year"].append(year.group().strip())
        rating_field = re.search("Rating: .*",item)
        if rating_field is not None:
            rating = re.search('\s\d.\d',rating_field.group())
        else:
            rating - None
        movies["Rating"].append(rating.group().strip())
    movies
    ```




        {'Name': ['The Godfather', 'Bird Box', 'Fight Club'],
         'Year': ['1972', '2018', '1999'],
         'Rating': ['9.2', '6.8', '8.8']}




    ```python
    df = pd.DataFrame(movies)
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
          <th>Name</th>
          <th>Year</th>
          <th>Rating</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>The Godfather</td>
          <td>1972</td>
          <td>9.2</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Bird Box</td>
          <td>2018</td>
          <td>6.8</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Fight Club</td>
          <td>1999</td>
          <td>8.8</td>
        </tr>
      </tbody>
    </table>
    </div>



    ### Ranking Rows in Pandas


    ```python
    import pandas as pd

    ```


    ```python
    movies = {'Name': ['The Godfather', 'Bird Box', 'Fight Club'],
             'Year': ['1972', '2018', '1999'],
             'Rating': ['9.2', '6.8', '8.8']}
    df = pd.DataFrame(movies)
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
          <th>Name</th>
          <th>Year</th>
          <th>Rating</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>The Godfather</td>
          <td>1972</td>
          <td>9.2</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Bird Box</td>
          <td>2018</td>
          <td>6.8</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Fight Club</td>
          <td>1999</td>
          <td>8.8</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    df['Rating_Rank'] = df['Rating'].rank(ascending=1)
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
          <th>Name</th>
          <th>Year</th>
          <th>Rating</th>
          <th>Rating_Rank</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>The Godfather</td>
          <td>1972</td>
          <td>9.2</td>
          <td>3.0</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Bird Box</td>
          <td>2018</td>
          <td>6.8</td>
          <td>1.0</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Fight Club</td>
          <td>1999</td>
          <td>8.8</td>
          <td>2.0</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    df =df.set_index('Rating_Rank')
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
          <th>Name</th>
          <th>Year</th>
          <th>Rating</th>
        </tr>
        <tr>
          <th>Rating_Rank</th>
          <th></th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>3.0</th>
          <td>The Godfather</td>
          <td>1972</td>
          <td>9.2</td>
        </tr>
        <tr>
          <th>1.0</th>
          <td>Bird Box</td>
          <td>2018</td>
          <td>6.8</td>
        </tr>
        <tr>
          <th>2.0</th>
          <td>Fight Club</td>
          <td>1999</td>
          <td>8.8</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    df.sort_index()
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
          <th>Name</th>
          <th>Year</th>
          <th>Rating</th>
        </tr>
        <tr>
          <th>Rating_Rank</th>
          <th></th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>1.0</th>
          <td>Bird Box</td>
          <td>2018</td>
          <td>6.8</td>
        </tr>
        <tr>
          <th>2.0</th>
          <td>Fight Club</td>
          <td>1999</td>
          <td>8.8</td>
        </tr>
        <tr>
          <th>3.0</th>
          <td>The Godfather</td>
          <td>1972</td>
          <td>9.2</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    # Example 2
    import pandas as pd
    ```


    ```python
    student_details = {'Name':['Raj','Raj','Raj','Aravind','Aravind','Aravind','John','John','John','Arjun','Arjun','Arjun'],
                       'Subject':['Maths','Physics','Chemistry','Maths','Physics','Chemistry','Maths','Physics','Chemistry','Maths','Physics','Chemistry'],
                       'Marks':[80,90,75,60,40,60,80,55,100,90,75,70]

    }

    df = pd.DataFrame(student_details)
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
          <th>Name</th>
          <th>Subject</th>
          <th>Marks</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>Raj</td>
          <td>Maths</td>
          <td>80</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Raj</td>
          <td>Physics</td>
          <td>90</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Raj</td>
          <td>Chemistry</td>
          <td>75</td>
        </tr>
        <tr>
          <th>3</th>
          <td>Aravind</td>
          <td>Maths</td>
          <td>60</td>
        </tr>
        <tr>
          <th>4</th>
          <td>Aravind</td>
          <td>Physics</td>
          <td>40</td>
        </tr>
        <tr>
          <th>5</th>
          <td>Aravind</td>
          <td>Chemistry</td>
          <td>60</td>
        </tr>
        <tr>
          <th>6</th>
          <td>John</td>
          <td>Maths</td>
          <td>80</td>
        </tr>
        <tr>
          <th>7</th>
          <td>John</td>
          <td>Physics</td>
          <td>55</td>
        </tr>
        <tr>
          <th>8</th>
          <td>John</td>
          <td>Chemistry</td>
          <td>100</td>
        </tr>
        <tr>
          <th>9</th>
          <td>Arjun</td>
          <td>Maths</td>
          <td>90</td>
        </tr>
        <tr>
          <th>10</th>
          <td>Arjun</td>
          <td>Physics</td>
          <td>75</td>
        </tr>
        <tr>
          <th>11</th>
          <td>Arjun</td>
          <td>Chemistry</td>
          <td>70</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    df['Mark_Rank'] = df['Marks'].rank(ascending=0)
    df = df.set_index('Mark_Rank')
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
          <th>Name</th>
          <th>Subject</th>
          <th>Marks</th>
        </tr>
        <tr>
          <th>Mark_Rank</th>
          <th></th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>4.5</th>
          <td>Raj</td>
          <td>Maths</td>
          <td>80</td>
        </tr>
        <tr>
          <th>2.5</th>
          <td>Raj</td>
          <td>Physics</td>
          <td>90</td>
        </tr>
        <tr>
          <th>6.5</th>
          <td>Raj</td>
          <td>Chemistry</td>
          <td>75</td>
        </tr>
        <tr>
          <th>9.5</th>
          <td>Aravind</td>
          <td>Maths</td>
          <td>60</td>
        </tr>
        <tr>
          <th>12.0</th>
          <td>Aravind</td>
          <td>Physics</td>
          <td>40</td>
        </tr>
        <tr>
          <th>9.5</th>
          <td>Aravind</td>
          <td>Chemistry</td>
          <td>60</td>
        </tr>
        <tr>
          <th>4.5</th>
          <td>John</td>
          <td>Maths</td>
          <td>80</td>
        </tr>
        <tr>
          <th>11.0</th>
          <td>John</td>
          <td>Physics</td>
          <td>55</td>
        </tr>
        <tr>
          <th>1.0</th>
          <td>John</td>
          <td>Chemistry</td>
          <td>100</td>
        </tr>
        <tr>
          <th>2.5</th>
          <td>Arjun</td>
          <td>Maths</td>
          <td>90</td>
        </tr>
        <tr>
          <th>6.5</th>
          <td>Arjun</td>
          <td>Physics</td>
          <td>75</td>
        </tr>
        <tr>
          <th>8.0</th>
          <td>Arjun</td>
          <td>Chemistry</td>
          <td>70</td>
        </tr>
      </tbody>
    </table>
    </div>




    ```python
    df = df.sort_index()
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
          <th>Name</th>
          <th>Subject</th>
          <th>Marks</th>
        </tr>
        <tr>
          <th>Mark_Rank</th>
          <th></th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>1.0</th>
          <td>John</td>
          <td>Chemistry</td>
          <td>100</td>
        </tr>
        <tr>
          <th>2.5</th>
          <td>Raj</td>
          <td>Physics</td>
          <td>90</td>
        </tr>
        <tr>
          <th>2.5</th>
          <td>Arjun</td>
          <td>Maths</td>
          <td>90</td>
        </tr>
        <tr>
          <th>4.5</th>
          <td>Raj</td>
          <td>Maths</td>
          <td>80</td>
        </tr>
        <tr>
          <th>4.5</th>
          <td>John</td>
          <td>Maths</td>
          <td>80</td>
        </tr>
        <tr>
          <th>6.5</th>
          <td>Raj</td>
          <td>Chemistry</td>
          <td>75</td>
        </tr>
        <tr>
          <th>6.5</th>
          <td>Arjun</td>
          <td>Physics</td>
          <td>75</td>
        </tr>
        <tr>
          <th>8.0</th>
          <td>Arjun</td>
          <td>Chemistry</td>
          <td>70</td>
        </tr>
        <tr>
          <th>9.5</th>
          <td>Aravind</td>
          <td>Maths</td>
          <td>60</td>
        </tr>
        <tr>
          <th>9.5</th>
          <td>Aravind</td>
          <td>Chemistry</td>
          <td>60</td>
        </tr>
        <tr>
          <th>11.0</th>
          <td>John</td>
          <td>Physics</td>
          <td>55</td>
        </tr>
        <tr>
          <th>12.0</th>
          <td>Aravind</td>
          <td>Physics</td>
          <td>40</td>
        </tr>
      </tbody>
    </table>
    </div>



    ## Grouping


    ```python
    movies=pd.read_csv("data/movies.csv",encoding = "ISO-8859-1")
    ```


    ```python
    # get selected columns with row indexes within ranges
    short_movies = movies[['user_id', 'movie_id', 'rating','timestamp', 'age', 'occupation','movie_title','release_date']] \
                         .loc[list(range(50)) + list(range(100,150)) + list(range(250,500))].reset_index(drop=True)
    short_movies.head(10)
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
          <th>occupation</th>
          <th>movie_title</th>
          <th>release_date</th>
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
          <td>writer</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
        <tr>
          <th>1</th>
          <td>305</td>
          <td>242</td>
          <td>5</td>
          <td>886307828</td>
          <td>23.0</td>
          <td>programmer</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
        <tr>
          <th>2</th>
          <td>6</td>
          <td>242</td>
          <td>4</td>
          <td>883268170</td>
          <td>42.0</td>
          <td>executive</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
        <tr>
          <th>3</th>
          <td>234</td>
          <td>242</td>
          <td>4</td>
          <td>891033261</td>
          <td>60.0</td>
          <td>retired</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
        <tr>
          <th>4</th>
          <td>63</td>
          <td>242</td>
          <td>3</td>
          <td>875747190</td>
          <td>31.0</td>
          <td>marketing</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
        <tr>
          <th>5</th>
          <td>181</td>
          <td>242</td>
          <td>1</td>
          <td>878961814</td>
          <td>26.0</td>
          <td>executive</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
        <tr>
          <th>6</th>
          <td>201</td>
          <td>242</td>
          <td>4</td>
          <td>884110598</td>
          <td>27.0</td>
          <td>writer</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
        <tr>
          <th>7</th>
          <td>249</td>
          <td>242</td>
          <td>5</td>
          <td>879571438</td>
          <td>25.0</td>
          <td>student</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
        <tr>
          <th>8</th>
          <td>13</td>
          <td>242</td>
          <td>2</td>
          <td>881515193</td>
          <td>47.0</td>
          <td>educator</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
        <tr>
          <th>9</th>
          <td>279</td>
          <td>242</td>
          <td>3</td>
          <td>877756647</td>
          <td>33.0</td>
          <td>programmer</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
      </tbody>
    </table>
    </div>



    pandas DataFrames can be split on any of their axes. Grouping denotes the providence of a mapping of labels to group names. Method `groupby()` is provided in pandas for grouping. The `groupby()` function returns a `GroupBy` object, but essentially describes how the rows of the original data set has been split.


    ```python
    movies_grouped = movies.groupby('movie_id')
    list(movies_grouped)[:3]
    ```




        [(1,        user_id  movie_id  rating  timestamp   age gender     occupation  \
          50260      244         1       4  880604405  28.0      M     technician   
          50261      298         1       5  884126061   NaN      M      executive   
          50262      253         1       5  891628467  26.0      F      librarian   
          50263      305         1       5  886323153  23.0      M     programmer   
          50264        6         1       4  883599478  42.0      M      executive   
          50265       62         1       2  879372813  27.0      F  administrator   
          50266      286         1       4  876521699  27.0      M        student   
          50267      200         1       5  876042340  40.0      M     programmer   
          50268      210         1       5  887731052  39.0      M       engineer   
          50269      303         1       5  879466966  19.0      M        student   
          50270      194         1       4  879539127  38.0      M  administrator   
          50271      291         1       5  874834481   NaN      M        student   
          50272      234         1       3  891227689  60.0      M        retired   
          50273      299         1       3  877877535  29.0      M            NaN   
          50274      308         1       4  887736532   NaN      M        retired   
          50275       95         1       5  879197329  31.0      M  administrator   
          50276       38         1       5  892430636  28.0      F          other   
          50277      102         1       3  883748352  38.0      M     programmer   
          50278       63         1       3  875747368  31.0      M      marketing   
          50279      160         1       4  876768025  27.0      M     programmer   
          50280      301         1       4  882074345  24.0      M        student   
          50281      290         1       5  880474327  40.0      M       engineer   
          50282       97         1       4  884238911  43.0      M         artist   
          50283      157         1       5  874813703  57.0      M       engineer   
          50284      181         1       3  878962392  26.0      M      executive   
          50285      276         1       5  874786568  21.0      M        student   
          50286       10         1       4  877888877  53.0      M         lawyer   
          50287      201         1       3  884113635  27.0      M         writer   
          50288      287         1       5  875334088   NaN      M       salesman   
          50289      246         1       4  884920918  19.0      M        student   
          ...        ...       ...     ...        ...   ...    ...            ...   
          50682      887         1       5  881377972  14.0      F        student   
          50683      894         1       4  880416286  47.0      M       educator   
          50684      896         1       4  887158579  28.0      M         writer   
          50685      897         1       5  879994113  30.0      M          other   
          50686      901         1       5  877129870  38.0      M      executive   
          50687      899         1       3  884120105  32.0      M          other   
          50688      903         1       3  891031280  28.0      M       educator   
          50689      907         1       5  880158712  25.0      F          other   
          50690      902         1       5  879465583  45.0      F         artist   
          50691      895         1       4  879437950  31.0      F      librarian   
          50692      916         1       4  880843361  27.0      M       engineer   
          50693      918         1       3  891987059  40.0      M      scientist   
          50694      919         1       4  875289321  25.0      M          other   
          50695      921         1       3  879379601  20.0      F        student   
          50696      910         1       4  880822060  28.0      M     healthcare   
          50697      913         1       2  880758579  27.0      M        student   
          50698      922         1       5  891448551  29.0      F  administrator   
          50699      923         1       3  880387306  21.0      M            NaN   
          50700      927         1       5  879191524  23.0      M     programmer   
          50701      924         1       5  884371535  29.0      M          other   
          50702      929         1       3  878402162  44.0      M      scientist   
          50703      917         1       3  882910888  22.0      F        student   
          50704      932         1       4  891249932  58.0      M       educator   
          50705      934         1       2  891225958  61.0      M       engineer   
          50706      933         1       3  874854294  28.0      M        student   
          50707      935         1       3  884472064  42.0      M         doctor   
          50708      938         1       4  891356314  38.0      F     technician   
          50709      936         1       4  886832453  24.0      M          other   
          50710      930         1       3  879534525  28.0      F            NaN   
          50711      941         1       5  875049144  20.0      M        student   

                zip_code       movie_title release_date   ...    Fantasy  Film-Noir  \
          50260    80525  Toy Story (1995)   1995-01-01   ...          0          0   
          50261    01581  Toy Story (1995)   1995-01-01   ...          0          0   
          50262    22903  Toy Story (1995)   1995-01-01   ...          0          0   
          50263    94086  Toy Story (1995)   1995-01-01   ...          0          0   
          50264    98101  Toy Story (1995)   1995-01-01   ...          0          0   
          50265    97214  Toy Story (1995)   1995-01-01   ...          0          0   
          50266    15217  Toy Story (1995)   1995-01-01   ...          0          0   
          50267    93402  Toy Story (1995)   1995-01-01   ...          0          0   
          50268    03060  Toy Story (1995)   1995-01-01   ...          0          0   
          50269    14853  Toy Story (1995)   1995-01-01   ...          0          0   
          50270    02154  Toy Story (1995)   1995-01-01   ...          0          0   
          50271    44106  Toy Story (1995)   1995-01-01   ...          0          0   
          50272    94702  Toy Story (1995)   1995-01-01   ...          0          0   
          50273    63108  Toy Story (1995)   1995-01-01   ...          0          0   
          50274    95076  Toy Story (1995)   1995-01-01   ...          0          0   
          50275    10707  Toy Story (1995)   1995-01-01   ...          0          0   
          50276    54467  Toy Story (1995)   1995-01-01   ...          0          0   
          50277    30220  Toy Story (1995)   1995-01-01   ...          0          0   
          50278    75240  Toy Story (1995)   1995-01-01   ...          0          0   
          50279    66215  Toy Story (1995)   1995-01-01   ...          0          0   
          50280    55439  Toy Story (1995)   1995-01-01   ...          0          0   
          50281    93550  Toy Story (1995)   1995-01-01   ...          0          0   
          50282    98006  Toy Story (1995)   1995-01-01   ...          0          0   
          50283    70808  Toy Story (1995)   1995-01-01   ...          0          0   
          50284    21218  Toy Story (1995)   1995-01-01   ...          0          0   
          50285    95064  Toy Story (1995)   1995-01-01   ...          0          0   
          50286    90703  Toy Story (1995)   1995-01-01   ...          0          0   
          50287    E2A4H  Toy Story (1995)   1995-01-01   ...          0          0   
          50288    31211  Toy Story (1995)   1995-01-01   ...          0          0   
          50289    28734  Toy Story (1995)   1995-01-01   ...          0          0   
          ...        ...               ...          ...   ...        ...        ...   
          50682    27249  Toy Story (1995)   1995-01-01   ...          0          0   
          50683    74075  Toy Story (1995)   1995-01-01   ...          0          0   
          50684    91505  Toy Story (1995)   1995-01-01   ...          0          0   
          50685    33484  Toy Story (1995)   1995-01-01   ...          0          0   
          50686    L1V3W  Toy Story (1995)   1995-01-01   ...          0          0   
          50687    55116  Toy Story (1995)   1995-01-01   ...          0          0   
          50688    20850  Toy Story (1995)   1995-01-01   ...          0          0   
          50689    80526  Toy Story (1995)   1995-01-01   ...          0          0   
          50690    97203  Toy Story (1995)   1995-01-01   ...          0          0   
          50691    32301  Toy Story (1995)   1995-01-01   ...          0          0   
          50692    N2L5N  Toy Story (1995)   1995-01-01   ...          0          0   
          50693    70116  Toy Story (1995)   1995-01-01   ...          0          0   
          50694    14216  Toy Story (1995)   1995-01-01   ...          0          0   
          50695    98801  Toy Story (1995)   1995-01-01   ...          0          0   
          50696    29301  Toy Story (1995)   1995-01-01   ...          0          0   
          50697    76201  Toy Story (1995)   1995-01-01   ...          0          0   
          50698    21114  Toy Story (1995)   1995-01-01   ...          0          0   
          50699    E2E3R  Toy Story (1995)   1995-01-01   ...          0          0   
          50700    55428  Toy Story (1995)   1995-01-01   ...          0          0   
          50701    11753  Toy Story (1995)   1995-01-01   ...          0          0   
          50702    53711  Toy Story (1995)   1995-01-01   ...          0          0   
          50703    20006  Toy Story (1995)   1995-01-01   ...          0          0   
          50704    06437  Toy Story (1995)   1995-01-01   ...          0          0   
          50705    22902  Toy Story (1995)   1995-01-01   ...          0          0   
          50706    48105  Toy Story (1995)   1995-01-01   ...          0          0   
          50707    66221  Toy Story (1995)   1995-01-01   ...          0          0   
          50708    55038  Toy Story (1995)   1995-01-01   ...          0          0   
          50709    32789  Toy Story (1995)   1995-01-01   ...          0          0   
          50710    07310  Toy Story (1995)   1995-01-01   ...          0          0   
          50711    97229  Toy Story (1995)   1995-01-01   ...          0          0   

                 Horror  Musical  Mystery  Romance  Sci-Fi  Thriller  War  Western  
          50260       0        0        0        0       0         0    0        0  
          50261       0        0        0        0       0         0    0        0  
          50262       0        0        0        0       0         0    0        0  
          50263       0        0        0        0       0         0    0        0  
          50264       0        0        0        0       0         0    0        0  
          50265       0        0        0        0       0         0    0        0  
          50266       0        0        0        0       0         0    0        0  
          50267       0        0        0        0       0         0    0        0  
          50268       0        0        0        0       0         0    0        0  
          50269       0        0        0        0       0         0    0        0  
          50270       0        0        0        0       0         0    0        0  
          50271       0        0        0        0       0         0    0        0  
          50272       0        0        0        0       0         0    0        0  
          50273       0        0        0        0       0         0    0        0  
          50274       0        0        0        0       0         0    0        0  
          50275       0        0        0        0       0         0    0        0  
          50276       0        0        0        0       0         0    0        0  
          50277       0        0        0        0       0         0    0        0  
          50278       0        0        0        0       0         0    0        0  
          50279       0        0        0        0       0         0    0        0  
          50280       0        0        0        0       0         0    0        0  
          50281       0        0        0        0       0         0    0        0  
          50282       0        0        0        0       0         0    0        0  
          50283       0        0        0        0       0         0    0        0  
          50284       0        0        0        0       0         0    0        0  
          50285       0        0        0        0       0         0    0        0  
          50286       0        0        0        0       0         0    0        0  
          50287       0        0        0        0       0         0    0        0  
          50288       0        0        0        0       0         0    0        0  
          50289       0        0        0        0       0         0    0        0  
          ...       ...      ...      ...      ...     ...       ...  ...      ...  
          50682       0        0        0        0       0         0    0        0  
          50683       0        0        0        0       0         0    0        0  
          50684       0        0        0        0       0         0    0        0  
          50685       0        0        0        0       0         0    0        0  
          50686       0        0        0        0       0         0    0        0  
          50687       0        0        0        0       0         0    0        0  
          50688       0        0        0        0       0         0    0        0  
          50689       0        0        0        0       0         0    0        0  
          50690       0        0        0        0       0         0    0        0  
          50691       0        0        0        0       0         0    0        0  
          50692       0        0        0        0       0         0    0        0  
          50693       0        0        0        0       0         0    0        0  
          50694       0        0        0        0       0         0    0        0  
          50695       0        0        0        0       0         0    0        0  
          50696       0        0        0        0       0         0    0        0  
          50697       0        0        0        0       0         0    0        0  
          50698       0        0        0        0       0         0    0        0  
          50699       0        0        0        0       0         0    0        0  
          50700       0        0        0        0       0         0    0        0  
          50701       0        0        0        0       0         0    0        0  
          50702       0        0        0        0       0         0    0        0  
          50703       0        0        0        0       0         0    0        0  
          50704       0        0        0        0       0         0    0        0  
          50705       0        0        0        0       0         0    0        0  
          50706       0        0        0        0       0         0    0        0  
          50707       0        0        0        0       0         0    0        0  
          50708       0        0        0        0       0         0    0        0  
          50709       0        0        0        0       0         0    0        0  
          50710       0        0        0        0       0         0    0        0  
          50711       0        0        0        0       0         0    0        0  

          [452 rows x 30 columns]),
         (2,        user_id  movie_id  rating  timestamp   age gender     occupation  \
          30722       22         2       2  878887925  25.0      M         writer   
          30723      305         2       2  886324580  23.0      M     programmer   
          30724      200         2       4  884130046  40.0      M     programmer   
          30725      303         2       3  879467191  19.0      M        student   
          30726      234         2       2  892335142  60.0      M        retired   
          30727       95         2       2  888955909  31.0      M  administrator   
          30728      102         2       2  888801522  38.0      M     programmer   
          30729      301         2       2  882076587   NaN      M            NaN   
          30730      276         2       4  874792436  21.0      M        student   
          30731      201         2       2  884112487  27.0      M         writer   
          30732      249         2       3  879641284  25.0      M        student   
          30733      178         2       4  882827375  26.0      M          other   
          30734       72         2       3  880037376  48.0      F  administrator   
          30735       87         2       4  879876074  47.0      M  administrator   
          30736       42         2       5  881109271  30.0      M  administrator   
          30737      292         2       4  881105778  35.0      F     programmer   
          30738       13         2       3  882397650  47.0      M       educator   
          30739       92         2       3  875653699  32.0      M  entertainment   
          30740      293         2       3  888907101  24.0      M         writer   
          30741      222         2       3  878183837   NaN      M     programmer   
          30742      267         2       3  878972463  23.0      M       engineer   
          30743      279         2       4  875313311  33.0      M     programmer   
          30744      250         2       4  878090414  29.0      M      executive   
          30745      271         2       1  885849386  51.0      M       engineer   
          30746      110         2       3  886988536  19.0      M        student   
          30747      213         2       4  878955914  33.0      M      executive   
          30748       49         2       1  888069606  23.0      F            NaN   
          30749      268         2       2  875744173  24.0      M       engineer   
          30750        5         2       3  875636053  33.0      F          other   
          30751      130         2       4  876252327  20.0      M           none   
          ...        ...       ...     ...        ...   ...    ...            ...   
          30823      751         2       4  889298116  24.0      F          other   
          30824      757         2       3  888466490  26.0      M        student   
          30825      764         2       3  876244856  27.0      F       educator   
          30826      773         2       3  888540146   NaN      M        student   
          30827      774         2       1  888557383  30.0      M        student   
          30828      790         2       3  885156988  27.0      M     technician   
          30829      796         2       5  893048377  32.0      F         writer   
          30830      795         2       3  883252599  30.0      M     programmer   
          30831      798         2       4  875743787  40.0      F         writer   
          30832      804         2       4  879445493  39.0      M       educator   
          30833      806         2       3  882389862  27.0      M      marketing   
          30834      807         2       4  892978338  41.0      F     healthcare   
          30835      815         2       3  878696355  32.0      M          other   
          30836      830         2       3  891561806   NaN      M     programmer   
          30837      826         2       3  885690713  28.0      M         artist   
          30838      844         2       4  877387933  22.0      M       engineer   
          30839      846         2       5  883948949  27.0      M         lawyer   
          30840      864         2       4  888889657  27.0      M     programmer   
          30841      868         2       2  877112290   NaN      M     programmer   
          30842      870         2       2  879714351  22.0      M        student   
          30843      880         2       3  880167732  13.0      M        student   
          30844      886         2       4  876033368  20.0      M        student   
          30845      889         2       3  880182460  24.0      M     technician   
          30846      892         2       4  886609006  36.0      M          other   
          30847      896         2       3  887160000  28.0      M         writer   
          30848      899         2       3  884122563  32.0      M          other   
          30849      916         2       3  880845391  27.0      M       engineer   
          30850      924         2       3  886759997  29.0      M          other   
          30851      934         2       4  891192087   NaN      M       engineer   
          30852      943         2       5  888639953  22.0      M        student   

                zip_code       movie_title release_date   ...    Fantasy  Film-Noir  \
          30722    40206  GoldenEye (1995)   1995-01-01   ...          0          0   
          30723    94086  GoldenEye (1995)   1995-01-01   ...          0          0   
          30724    93402  GoldenEye (1995)   1995-01-01   ...          0          0   
          30725    14853  GoldenEye (1995)   1995-01-01   ...          0          0   
          30726    94702  GoldenEye (1995)   1995-01-01   ...          0          0   
          30727    10707  GoldenEye (1995)   1995-01-01   ...          0          0   
          30728    30220  GoldenEye (1995)   1995-01-01   ...          0          0   
          30729    55439  GoldenEye (1995)   1995-01-01   ...          0          0   
          30730    95064  GoldenEye (1995)   1995-01-01   ...          0          0   
          30731    E2A4H  GoldenEye (1995)   1995-01-01   ...          0          0   
          30732    84103  GoldenEye (1995)   1995-01-01   ...          0          0   
          30733    49512  GoldenEye (1995)   1995-01-01   ...          0          0   
          30734    73034  GoldenEye (1995)   1995-01-01   ...          0          0   
          30735    89503  GoldenEye (1995)   1995-01-01   ...          0          0   
          30736    17870  GoldenEye (1995)   1995-01-01   ...          0          0   
          30737    94703  GoldenEye (1995)   1995-01-01   ...          0          0   
          30738    29206  GoldenEye (1995)   1995-01-01   ...          0          0   
          30739    80525  GoldenEye (1995)   1995-01-01   ...          0          0   
          30740    60804  GoldenEye (1995)   1995-01-01   ...          0          0   
          30741    27502  GoldenEye (1995)   1995-01-01   ...          0          0   
          30742    83716  GoldenEye (1995)   1995-01-01   ...          0          0   
          30743    85251  GoldenEye (1995)   1995-01-01   ...          0          0   
          30744    95110  GoldenEye (1995)   1995-01-01   ...          0          0   
          30745    22932  GoldenEye (1995)   1995-01-01   ...          0          0   
          30746    77840  GoldenEye (1995)   1995-01-01   ...          0          0   
          30747    55345  GoldenEye (1995)   1995-01-01   ...          0          0   
          30748    76111  GoldenEye (1995)   1995-01-01   ...          0          0   
          30749    19422  GoldenEye (1995)   1995-01-01   ...          0          0   
          30750    15213  GoldenEye (1995)   1995-01-01   ...          0          0   
          30751    60115  GoldenEye (1995)   1995-01-01   ...          0          0   
          ...        ...               ...          ...   ...        ...        ...   
          30823    90034  GoldenEye (1995)   1995-01-01   ...          0          0   
          30824    55104  GoldenEye (1995)   1995-01-01   ...          0          0   
          30825    62903  GoldenEye (1995)   1995-01-01   ...          0          0   
          30826    55414  GoldenEye (1995)   1995-01-01   ...          0          0   
          30827    80027  GoldenEye (1995)   1995-01-01   ...          0          0   
          30828    80913  GoldenEye (1995)   1995-01-01   ...          0          0   
          30829    33755  GoldenEye (1995)   1995-01-01   ...          0          0   
          30830    08610  GoldenEye (1995)   1995-01-01   ...          0          0   
          30831    64131  GoldenEye (1995)   1995-01-01   ...          0          0   
          30832    61820  GoldenEye (1995)   1995-01-01   ...          0          0   
          30833    11217  GoldenEye (1995)   1995-01-01   ...          0          0   
          30834    93555  GoldenEye (1995)   1995-01-01   ...          0          0   
          30835    28806  GoldenEye (1995)   1995-01-01   ...          0          0   
          30836    53066  GoldenEye (1995)   1995-01-01   ...          0          0   
          30837    77048  GoldenEye (1995)   1995-01-01   ...          0          0   
          30838    95662  GoldenEye (1995)   1995-01-01   ...          0          0   
          30839    47130  GoldenEye (1995)   1995-01-01   ...          0          0   
          30840    63021  GoldenEye (1995)   1995-01-01   ...          0          0   
          30841    55303  GoldenEye (1995)   1995-01-01   ...          0          0   
          30842    65203  GoldenEye (1995)   1995-01-01   ...          0          0   
          30843    83702  GoldenEye (1995)   1995-01-01   ...          0          0   
          30844    61820  GoldenEye (1995)   1995-01-01   ...          0          0   
          30845    78704  GoldenEye (1995)   1995-01-01   ...          0          0   
          30846    45243  GoldenEye (1995)   1995-01-01   ...          0          0   
          30847    91505  GoldenEye (1995)   1995-01-01   ...          0          0   
          30848    55116  GoldenEye (1995)   1995-01-01   ...          0          0   
          30849    N2L5N  GoldenEye (1995)   1995-01-01   ...          0          0   
          30850    11753  GoldenEye (1995)   1995-01-01   ...          0          0   
          30851    22902  GoldenEye (1995)   1995-01-01   ...          0          0   
          30852    77841  GoldenEye (1995)   1995-01-01   ...          0          0   

                 Horror  Musical  Mystery  Romance  Sci-Fi  Thriller  War  Western  
          30722       0        0        0        0       0         1    0        0  
          30723       0        0        0        0       0         1    0        0  
          30724       0        0        0        0       0         1    0        0  
          30725       0        0        0        0       0         1    0        0  
          30726       0        0        0        0       0         1    0        0  
          30727       0        0        0        0       0         1    0        0  
          30728       0        0        0        0       0         1    0        0  
          30729       0        0        0        0       0         1    0        0  
          30730       0        0        0        0       0         1    0        0  
          30731       0        0        0        0       0         1    0        0  
          30732       0        0        0        0       0         1    0        0  
          30733       0        0        0        0       0         1    0        0  
          30734       0        0        0        0       0         1    0        0  
          30735       0        0        0        0       0         1    0        0  
          30736       0        0        0        0       0         1    0        0  
          30737       0        0        0        0       0         1    0        0  
          30738       0        0        0        0       0         1    0        0  
          30739       0        0        0        0       0         1    0        0  
          30740       0        0        0        0       0         1    0        0  
          30741       0        0        0        0       0         1    0        0  
          30742       0        0        0        0       0         1    0        0  
          30743       0        0        0        0       0         1    0        0  
          30744       0        0        0        0       0         1    0        0  
          30745       0        0        0        0       0         1    0        0  
          30746       0        0        0        0       0         1    0        0  
          30747       0        0        0        0       0         1    0        0  
          30748       0        0        0        0       0         1    0        0  
          30749       0        0        0        0       0         1    0        0  
          30750       0        0        0        0       0         1    0        0  
          30751       0        0        0        0       0         1    0        0  
          ...       ...      ...      ...      ...     ...       ...  ...      ...  
          30823       0        0        0        0       0         1    0        0  
          30824       0        0        0        0       0         1    0        0  
          30825       0        0        0        0       0         1    0        0  
          30826       0        0        0        0       0         1    0        0  
          30827       0        0        0        0       0         1    0        0  
          30828       0        0        0        0       0         1    0        0  
          30829       0        0        0        0       0         1    0        0  
          30830       0        0        0        0       0         1    0        0  
          30831       0        0        0        0       0         1    0        0  
          30832       0        0        0        0       0         1    0        0  
          30833       0        0        0        0       0         1    0        0  
          30834       0        0        0        0       0         1    0        0  
          30835       0        0        0        0       0         1    0        0  
          30836       0        0        0        0       0         1    0        0  
          30837       0        0        0        0       0         1    0        0  
          30838       0        0        0        0       0         1    0        0  
          30839       0        0        0        0       0         1    0        0  
          30840       0        0        0        0       0         1    0        0  
          30841       0        0        0        0       0         1    0        0  
          30842       0        0        0        0       0         1    0        0  
          30843       0        0        0        0       0         1    0        0  
          30844       0        0        0        0       0         1    0        0  
          30845       0        0        0        0       0         1    0        0  
          30846       0        0        0        0       0         1    0        0  
          30847       0        0        0        0       0         1    0        0  
          30848       0        0        0        0       0         1    0        0  
          30849       0        0        0        0       0         1    0        0  
          30850       0        0        0        0       0         1    0        0  
          30851       0        0        0        0       0         1    0        0  
          30852       0        0        0        0       0         1    0        0  

          [131 rows x 30 columns]),
         (3,        user_id  movie_id  rating  timestamp   age gender     occupation  \
          47904      244         3       5  880602451  28.0      M     technician   
          47905       62         3       3  879372325  27.0      F  administrator   
          47906      286         3       2  876522316  27.0      M        student   
          47907      303         3       3  879485184  19.0      M        student   
          47908      291         3       3  874833936  19.0      M        student   
          47909       95         3       1  879193881  31.0      M  administrator   
          47910       63         3       2  875748068  31.0      M      marketing   
          47911      160         3       3  876770124  27.0      M     programmer   
          47912      301         3       2  882075082  24.0      M        student   
          47913      157         3       3  886890734   NaN      M       engineer   
          47914      181         3       2  878963441  26.0      M      executive   
          47915      276         3       3  874786924  21.0      M        student   
          47916      246         3       2  884923390  19.0      M        student   
          47917       99         3       3  885679237  20.0      M        student   
          47918       81         3       4  876592546  21.0      M        student   
          47919       59         3       4  888203814  49.0      M       educator   
          47920      293         3       2  888905399  24.0      M         writer   
          47921      267         3       4  878970901   NaN      M       engineer   
          47922      145         3       3  875271562  31.0      M  entertainment   
          47923      216         3       4  880233061  22.0      M       engineer   
          47924       82         3       2  878768765  50.0      M     programmer   
          47925       43         3       2  884029543  29.0      F      librarian   
          47926      269         3       3  891446722  31.0      F      librarian   
          47927       49         3       3  888068877  23.0      F        student   
          47928      268         3       1  875743161  24.0      M       engineer   
          47929      130         3       5  876250897  20.0      M           none   
          47930        1         3       4  878542960  24.0      M     technician   
          47931      207         3       2  877846284   NaN      M      marketing   
          47932      104         3       3  888465739  27.0      M        student   
          47933      221         3       4  875244901  19.0      M        student   
          ...        ...       ...     ...        ...   ...    ...            ...   
          47964      582         3       3  882961723  17.0      M        student   
          47965      592         3       4  882608960  18.0      M        student   
          47966      580         3       5  884125916  16.0      M        student   
          47967      595         3       4  886922069  25.0      M     programmer   
          47968      606         3       5  880922084  28.0      M     programmer   
          47969      622         3       1  882672922  25.0      M     programmer   
          47970      621         3       5  881444887  17.0      M        student   
          47971      624         3       3  879793436  19.0      M        student   
          47972      654         3       3  887864071  27.0      F        student   
          47973      660         3       1  891405958  26.0      M        student   
          47974      663         3       4  889492614  26.0      M          other   
          47975      682         3       3  888519113  23.0      M     programmer   
          47976      699         3       3  879147917  44.0      M          other   
          47977      714         3       5  892777876  26.0      M       engineer   
          47978      747         3       2  888733567  19.0      M          other   
          47979      751         3       3  889299391  24.0      F          other   
          47980      756         3       1  874829174   NaN      F           none   
          47981      795         3       2  880561783  30.0      M     programmer   
          47982      793         3       4  875104592   NaN      M        student   
          47983      806         3       2  882385916  27.0      M      marketing   
          47984      854         3       1  882813047  29.0      F        student   
          47985      859         3       5  885775513  18.0      F          other   
          47986      880         3       1  880175023  13.0      M        student   
          47987      886         3       3  876032330   NaN      M            NaN   
          47988      889         3       4  880177664  24.0      M     technician   
          47989      916         3       3  880843838  27.0      M       engineer   
          47990      910         3       2  881421019  28.0      M     healthcare   
          47991      923         3       4  880387707  21.0      M        student   
          47992      917         3       1  882911567  22.0      F        student   
          47993      936         3       4  886833148  24.0      M          other   

                zip_code        movie_title release_date   ...    Fantasy  Film-Noir  \
          47904    80525  Four Rooms (1995)   1995-01-01   ...          0          0   
          47905    97214  Four Rooms (1995)   1995-01-01   ...          0          0   
          47906    15217  Four Rooms (1995)   1995-01-01   ...          0          0   
          47907    14853  Four Rooms (1995)   1995-01-01   ...          0          0   
          47908    44106  Four Rooms (1995)   1995-01-01   ...          0          0   
          47909    10707  Four Rooms (1995)   1995-01-01   ...          0          0   
          47910    75240  Four Rooms (1995)   1995-01-01   ...          0          0   
          47911    66215  Four Rooms (1995)   1995-01-01   ...          0          0   
          47912    55439  Four Rooms (1995)   1995-01-01   ...          0          0   
          47913    70808  Four Rooms (1995)   1995-01-01   ...          0          0   
          47914    21218  Four Rooms (1995)   1995-01-01   ...          0          0   
          47915    95064  Four Rooms (1995)   1995-01-01   ...          0          0   
          47916    28734  Four Rooms (1995)   1995-01-01   ...          0          0   
          47917    63129  Four Rooms (1995)   1995-01-01   ...          0          0   
          47918    21218  Four Rooms (1995)   1995-01-01   ...          0          0   
          47919    08403  Four Rooms (1995)   1995-01-01   ...          0          0   
          47920    60804  Four Rooms (1995)   1995-01-01   ...          0          0   
          47921    83716  Four Rooms (1995)   1995-01-01   ...          0          0   
          47922    V3N4P  Four Rooms (1995)   1995-01-01   ...          0          0   
          47923    02215  Four Rooms (1995)   1995-01-01   ...          0          0   
          47924    22902  Four Rooms (1995)   1995-01-01   ...          0          0   
          47925    20854  Four Rooms (1995)   1995-01-01   ...          0          0   
          47926    43201  Four Rooms (1995)   1995-01-01   ...          0          0   
          47927    76111  Four Rooms (1995)   1995-01-01   ...          0          0   
          47928    19422  Four Rooms (1995)   1995-01-01   ...          0          0   
          47929    60115  Four Rooms (1995)   1995-01-01   ...          0          0   
          47930    85711  Four Rooms (1995)   1995-01-01   ...          0          0   
          47931    92037  Four Rooms (1995)   1995-01-01   ...          0          0   
          47932    55108  Four Rooms (1995)   1995-01-01   ...          0          0   
          47933    20685  Four Rooms (1995)   1995-01-01   ...          0          0   
          ...        ...                ...          ...   ...        ...        ...   
          47964    93003  Four Rooms (1995)   1995-01-01   ...          0          0   
          47965    97520  Four Rooms (1995)   1995-01-01   ...          0          0   
          47966    17961  Four Rooms (1995)   1995-01-01   ...          0          0   
          47967    31909  Four Rooms (1995)   1995-01-01   ...          0          0   
          47968    63044  Four Rooms (1995)   1995-01-01   ...          0          0   
          47969    14850  Four Rooms (1995)   1995-01-01   ...          0          0   
          47970    60402  Four Rooms (1995)   1995-01-01   ...          0          0   
          47971    30067  Four Rooms (1995)   1995-01-01   ...          0          0   
          47972    78739  Four Rooms (1995)   1995-01-01   ...          0          0   
          47973    77380  Four Rooms (1995)   1995-01-01   ...          0          0   
          47974    19341  Four Rooms (1995)   1995-01-01   ...          0          0   
          47975    55128  Four Rooms (1995)   1995-01-01   ...          0          0   
          47976    96754  Four Rooms (1995)   1995-01-01   ...          0          0   
          47977    55343  Four Rooms (1995)   1995-01-01   ...          0          0   
          47978    93612  Four Rooms (1995)   1995-01-01   ...          0          0   
          47979    90034  Four Rooms (1995)   1995-01-01   ...          0          0   
          47980    90247  Four Rooms (1995)   1995-01-01   ...          0          0   
          47981    08610  Four Rooms (1995)   1995-01-01   ...          0          0   
          47982    85281  Four Rooms (1995)   1995-01-01   ...          0          0   
          47983    11217  Four Rooms (1995)   1995-01-01   ...          0          0   
          47984    55408  Four Rooms (1995)   1995-01-01   ...          0          0   
          47985    06492  Four Rooms (1995)   1995-01-01   ...          0          0   
          47986    83702  Four Rooms (1995)   1995-01-01   ...          0          0   
          47987    61820  Four Rooms (1995)   1995-01-01   ...          0          0   
          47988    78704  Four Rooms (1995)   1995-01-01   ...          0          0   
          47989    N2L5N  Four Rooms (1995)   1995-01-01   ...          0          0   
          47990    29301  Four Rooms (1995)   1995-01-01   ...          0          0   
          47991    E2E3R  Four Rooms (1995)   1995-01-01   ...          0          0   
          47992    20006  Four Rooms (1995)   1995-01-01   ...          0          0   
          47993    32789  Four Rooms (1995)   1995-01-01   ...          0          0   

                 Horror  Musical  Mystery  Romance  Sci-Fi  Thriller  War  Western  
          47904       0        0        0        0       0         1    0        0  
          47905       0        0        0        0       0         1    0        0  
          47906       0        0        0        0       0         1    0        0  
          47907       0        0        0        0       0         1    0        0  
          47908       0        0        0        0       0         1    0        0  
          47909       0        0        0        0       0         1    0        0  
          47910       0        0        0        0       0         1    0        0  
          47911       0        0        0        0       0         1    0        0  
          47912       0        0        0        0       0         1    0        0  
          47913       0        0        0        0       0         1    0        0  
          47914       0        0        0        0       0         1    0        0  
          47915       0        0        0        0       0         1    0        0  
          47916       0        0        0        0       0         1    0        0  
          47917       0        0        0        0       0         1    0        0  
          47918       0        0        0        0       0         1    0        0  
          47919       0        0        0        0       0         1    0        0  
          47920       0        0        0        0       0         1    0        0  
          47921       0        0        0        0       0         1    0        0  
          47922       0        0        0        0       0         1    0        0  
          47923       0        0        0        0       0         1    0        0  
          47924       0        0        0        0       0         1    0        0  
          47925       0        0        0        0       0         1    0        0  
          47926       0        0        0        0       0         1    0        0  
          47927       0        0        0        0       0         1    0        0  
          47928       0        0        0        0       0         1    0        0  
          47929       0        0        0        0       0         1    0        0  
          47930       0        0        0        0       0         1    0        0  
          47931       0        0        0        0       0         1    0        0  
          47932       0        0        0        0       0         1    0        0  
          47933       0        0        0        0       0         1    0        0  
          ...       ...      ...      ...      ...     ...       ...  ...      ...  
          47964       0        0        0        0       0         1    0        0  
          47965       0        0        0        0       0         1    0        0  
          47966       0        0        0        0       0         1    0        0  
          47967       0        0        0        0       0         1    0        0  
          47968       0        0        0        0       0         1    0        0  
          47969       0        0        0        0       0         1    0        0  
          47970       0        0        0        0       0         1    0        0  
          47971       0        0        0        0       0         1    0        0  
          47972       0        0        0        0       0         1    0        0  
          47973       0        0        0        0       0         1    0        0  
          47974       0        0        0        0       0         1    0        0  
          47975       0        0        0        0       0         1    0        0  
          47976       0        0        0        0       0         1    0        0  
          47977       0        0        0        0       0         1    0        0  
          47978       0        0        0        0       0         1    0        0  
          47979       0        0        0        0       0         1    0        0  
          47980       0        0        0        0       0         1    0        0  
          47981       0        0        0        0       0         1    0        0  
          47982       0        0        0        0       0         1    0        0  
          47983       0        0        0        0       0         1    0        0  
          47984       0        0        0        0       0         1    0        0  
          47985       0        0        0        0       0         1    0        0  
          47986       0        0        0        0       0         1    0        0  
          47987       0        0        0        0       0         1    0        0  
          47988       0        0        0        0       0         1    0        0  
          47989       0        0        0        0       0         1    0        0  
          47990       0        0        0        0       0         1    0        0  
          47991       0        0        0        0       0         1    0        0  
          47992       0        0        0        0       0         1    0        0  
          47993       0        0        0        0       0         1    0        0  

          [90 rows x 30 columns])]



    As it can be easily seen, the `GroupBy` object is a dictionary whose keys are the computed unique groups and corresponding values being the axis labels belonging to each group.


    ```python
    for key, value in list(movies_grouped)[:1]:
    # if you want to see more values uncomment row below and comment the previous row
    #for key, value in short_grouped:
        print(str(key) + ":" + str(value))
    ```

        1:       user_id  movie_id  rating  timestamp   age gender     occupation  \
        50260      244         1       4  880604405  28.0      M     technician   
        50261      298         1       5  884126061   NaN      M      executive   
        50262      253         1       5  891628467  26.0      F      librarian   
        50263      305         1       5  886323153  23.0      M     programmer   
        50264        6         1       4  883599478  42.0      M      executive   
        50265       62         1       2  879372813  27.0      F  administrator   
        50266      286         1       4  876521699  27.0      M        student   
        50267      200         1       5  876042340  40.0      M     programmer   
        50268      210         1       5  887731052  39.0      M       engineer   
        50269      303         1       5  879466966  19.0      M        student   
        50270      194         1       4  879539127  38.0      M  administrator   
        50271      291         1       5  874834481   NaN      M        student   
        50272      234         1       3  891227689  60.0      M        retired   
        50273      299         1       3  877877535  29.0      M            NaN   
        50274      308         1       4  887736532   NaN      M        retired   
        50275       95         1       5  879197329  31.0      M  administrator   
        50276       38         1       5  892430636  28.0      F          other   
        50277      102         1       3  883748352  38.0      M     programmer   
        50278       63         1       3  875747368  31.0      M      marketing   
        50279      160         1       4  876768025  27.0      M     programmer   
        50280      301         1       4  882074345  24.0      M        student   
        50281      290         1       5  880474327  40.0      M       engineer   
        50282       97         1       4  884238911  43.0      M         artist   
        50283      157         1       5  874813703  57.0      M       engineer   
        50284      181         1       3  878962392  26.0      M      executive   
        50285      276         1       5  874786568  21.0      M        student   
        50286       10         1       4  877888877  53.0      M         lawyer   
        50287      201         1       3  884113635  27.0      M         writer   
        50288      287         1       5  875334088   NaN      M       salesman   
        50289      246         1       4  884920918  19.0      M        student   
        ...        ...       ...     ...        ...   ...    ...            ...   
        50682      887         1       5  881377972  14.0      F        student   
        50683      894         1       4  880416286  47.0      M       educator   
        50684      896         1       4  887158579  28.0      M         writer   
        50685      897         1       5  879994113  30.0      M          other   
        50686      901         1       5  877129870  38.0      M      executive   
        50687      899         1       3  884120105  32.0      M          other   
        50688      903         1       3  891031280  28.0      M       educator   
        50689      907         1       5  880158712  25.0      F          other   
        50690      902         1       5  879465583  45.0      F         artist   
        50691      895         1       4  879437950  31.0      F      librarian   
        50692      916         1       4  880843361  27.0      M       engineer   
        50693      918         1       3  891987059  40.0      M      scientist   
        50694      919         1       4  875289321  25.0      M          other   
        50695      921         1       3  879379601  20.0      F        student   
        50696      910         1       4  880822060  28.0      M     healthcare   
        50697      913         1       2  880758579  27.0      M        student   
        50698      922         1       5  891448551  29.0      F  administrator   
        50699      923         1       3  880387306  21.0      M            NaN   
        50700      927         1       5  879191524  23.0      M     programmer   
        50701      924         1       5  884371535  29.0      M          other   
        50702      929         1       3  878402162  44.0      M      scientist   
        50703      917         1       3  882910888  22.0      F        student   
        50704      932         1       4  891249932  58.0      M       educator   
        50705      934         1       2  891225958  61.0      M       engineer   
        50706      933         1       3  874854294  28.0      M        student   
        50707      935         1       3  884472064  42.0      M         doctor   
        50708      938         1       4  891356314  38.0      F     technician   
        50709      936         1       4  886832453  24.0      M          other   
        50710      930         1       3  879534525  28.0      F            NaN   
        50711      941         1       5  875049144  20.0      M        student   

              zip_code       movie_title release_date   ...    Fantasy  Film-Noir  \
        50260    80525  Toy Story (1995)   1995-01-01   ...          0          0   
        50261    01581  Toy Story (1995)   1995-01-01   ...          0          0   
        50262    22903  Toy Story (1995)   1995-01-01   ...          0          0   
        50263    94086  Toy Story (1995)   1995-01-01   ...          0          0   
        50264    98101  Toy Story (1995)   1995-01-01   ...          0          0   
        50265    97214  Toy Story (1995)   1995-01-01   ...          0          0   
        50266    15217  Toy Story (1995)   1995-01-01   ...          0          0   
        50267    93402  Toy Story (1995)   1995-01-01   ...          0          0   
        50268    03060  Toy Story (1995)   1995-01-01   ...          0          0   
        50269    14853  Toy Story (1995)   1995-01-01   ...          0          0   
        50270    02154  Toy Story (1995)   1995-01-01   ...          0          0   
        50271    44106  Toy Story (1995)   1995-01-01   ...          0          0   
        50272    94702  Toy Story (1995)   1995-01-01   ...          0          0   
        50273    63108  Toy Story (1995)   1995-01-01   ...          0          0   
        50274    95076  Toy Story (1995)   1995-01-01   ...          0          0   
        50275    10707  Toy Story (1995)   1995-01-01   ...          0          0   
        50276    54467  Toy Story (1995)   1995-01-01   ...          0          0   
        50277    30220  Toy Story (1995)   1995-01-01   ...          0          0   
        50278    75240  Toy Story (1995)   1995-01-01   ...          0          0   
        50279    66215  Toy Story (1995)   1995-01-01   ...          0          0   
        50280    55439  Toy Story (1995)   1995-01-01   ...          0          0   
        50281    93550  Toy Story (1995)   1995-01-01   ...          0          0   
        50282    98006  Toy Story (1995)   1995-01-01   ...          0          0   
        50283    70808  Toy Story (1995)   1995-01-01   ...          0          0   
        50284    21218  Toy Story (1995)   1995-01-01   ...          0          0   
        50285    95064  Toy Story (1995)   1995-01-01   ...          0          0   
        50286    90703  Toy Story (1995)   1995-01-01   ...          0          0   
        50287    E2A4H  Toy Story (1995)   1995-01-01   ...          0          0   
        50288    31211  Toy Story (1995)   1995-01-01   ...          0          0   
        50289    28734  Toy Story (1995)   1995-01-01   ...          0          0   
        ...        ...               ...          ...   ...        ...        ...   
        50682    27249  Toy Story (1995)   1995-01-01   ...          0          0   
        50683    74075  Toy Story (1995)   1995-01-01   ...          0          0   
        50684    91505  Toy Story (1995)   1995-01-01   ...          0          0   
        50685    33484  Toy Story (1995)   1995-01-01   ...          0          0   
        50686    L1V3W  Toy Story (1995)   1995-01-01   ...          0          0   
        50687    55116  Toy Story (1995)   1995-01-01   ...          0          0   
        50688    20850  Toy Story (1995)   1995-01-01   ...          0          0   
        50689    80526  Toy Story (1995)   1995-01-01   ...          0          0   
        50690    97203  Toy Story (1995)   1995-01-01   ...          0          0   
        50691    32301  Toy Story (1995)   1995-01-01   ...          0          0   
        50692    N2L5N  Toy Story (1995)   1995-01-01   ...          0          0   
        50693    70116  Toy Story (1995)   1995-01-01   ...          0          0   
        50694    14216  Toy Story (1995)   1995-01-01   ...          0          0   
        50695    98801  Toy Story (1995)   1995-01-01   ...          0          0   
        50696    29301  Toy Story (1995)   1995-01-01   ...          0          0   
        50697    76201  Toy Story (1995)   1995-01-01   ...          0          0   
        50698    21114  Toy Story (1995)   1995-01-01   ...          0          0   
        50699    E2E3R  Toy Story (1995)   1995-01-01   ...          0          0   
        50700    55428  Toy Story (1995)   1995-01-01   ...          0          0   
        50701    11753  Toy Story (1995)   1995-01-01   ...          0          0   
        50702    53711  Toy Story (1995)   1995-01-01   ...          0          0   
        50703    20006  Toy Story (1995)   1995-01-01   ...          0          0   
        50704    06437  Toy Story (1995)   1995-01-01   ...          0          0   
        50705    22902  Toy Story (1995)   1995-01-01   ...          0          0   
        50706    48105  Toy Story (1995)   1995-01-01   ...          0          0   
        50707    66221  Toy Story (1995)   1995-01-01   ...          0          0   
        50708    55038  Toy Story (1995)   1995-01-01   ...          0          0   
        50709    32789  Toy Story (1995)   1995-01-01   ...          0          0   
        50710    07310  Toy Story (1995)   1995-01-01   ...          0          0   
        50711    97229  Toy Story (1995)   1995-01-01   ...          0          0   

               Horror  Musical  Mystery  Romance  Sci-Fi  Thriller  War  Western  
        50260       0        0        0        0       0         0    0        0  
        50261       0        0        0        0       0         0    0        0  
        50262       0        0        0        0       0         0    0        0  
        50263       0        0        0        0       0         0    0        0  
        50264       0        0        0        0       0         0    0        0  
        50265       0        0        0        0       0         0    0        0  
        50266       0        0        0        0       0         0    0        0  
        50267       0        0        0        0       0         0    0        0  
        50268       0        0        0        0       0         0    0        0  
        50269       0        0        0        0       0         0    0        0  
        50270       0        0        0        0       0         0    0        0  
        50271       0        0        0        0       0         0    0        0  
        50272       0        0        0        0       0         0    0        0  
        50273       0        0        0        0       0         0    0        0  
        50274       0        0        0        0       0         0    0        0  
        50275       0        0        0        0       0         0    0        0  
        50276       0        0        0        0       0         0    0        0  
        50277       0        0        0        0       0         0    0        0  
        50278       0        0        0        0       0         0    0        0  
        50279       0        0        0        0       0         0    0        0  
        50280       0        0        0        0       0         0    0        0  
        50281       0        0        0        0       0         0    0        0  
        50282       0        0        0        0       0         0    0        0  
        50283       0        0        0        0       0         0    0        0  
        50284       0        0        0        0       0         0    0        0  
        50285       0        0        0        0       0         0    0        0  
        50286       0        0        0        0       0         0    0        0  
        50287       0        0        0        0       0         0    0        0  
        50288       0        0        0        0       0         0    0        0  
        50289       0        0        0        0       0         0    0        0  
        ...       ...      ...      ...      ...     ...       ...  ...      ...  
        50682       0        0        0        0       0         0    0        0  
        50683       0        0        0        0       0         0    0        0  
        50684       0        0        0        0       0         0    0        0  
        50685       0        0        0        0       0         0    0        0  
        50686       0        0        0        0       0         0    0        0  
        50687       0        0        0        0       0         0    0        0  
        50688       0        0        0        0       0         0    0        0  
        50689       0        0        0        0       0         0    0        0  
        50690       0        0        0        0       0         0    0        0  
        50691       0        0        0        0       0         0    0        0  
        50692       0        0        0        0       0         0    0        0  
        50693       0        0        0        0       0         0    0        0  
        50694       0        0        0        0       0         0    0        0  
        50695       0        0        0        0       0         0    0        0  
        50696       0        0        0        0       0         0    0        0  
        50697       0        0        0        0       0         0    0        0  
        50698       0        0        0        0       0         0    0        0  
        50699       0        0        0        0       0         0    0        0  
        50700       0        0        0        0       0         0    0        0  
        50701       0        0        0        0       0         0    0        0  
        50702       0        0        0        0       0         0    0        0  
        50703       0        0        0        0       0         0    0        0  
        50704       0        0        0        0       0         0    0        0  
        50705       0        0        0        0       0         0    0        0  
        50706       0        0        0        0       0         0    0        0  
        50707       0        0        0        0       0         0    0        0  
        50708       0        0        0        0       0         0    0        0  
        50709       0        0        0        0       0         0    0        0  
        50710       0        0        0        0       0         0    0        0  
        50711       0        0        0        0       0         0    0        0  

        [452 rows x 30 columns]


    ### Selection and filtering


    Functions of descriptive statistic like `sum()`, `count()`, `max()`, `min()`, `mean()` can be quickly applied to the `GroupBy` object to obtain summary statistics for each group – an immensely useful function. The same statement is valid also for functions like `describe()` which return general information about an object.


    ```python
    movies_grouped.count().head(10)
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
          <th>1</th>
          <td>452</td>
          <td>452</td>
          <td>452</td>
          <td>417</td>
          <td>452</td>
          <td>427</td>
          <td>452</td>
          <td>452</td>
          <td>452</td>
          <td>452</td>
          <td>...</td>
          <td>452</td>
          <td>452</td>
          <td>452</td>
          <td>452</td>
          <td>452</td>
          <td>452</td>
          <td>452</td>
          <td>452</td>
          <td>452</td>
          <td>452</td>
        </tr>
        <tr>
          <th>2</th>
          <td>131</td>
          <td>131</td>
          <td>131</td>
          <td>120</td>
          <td>131</td>
          <td>127</td>
          <td>131</td>
          <td>131</td>
          <td>131</td>
          <td>131</td>
          <td>...</td>
          <td>131</td>
          <td>131</td>
          <td>131</td>
          <td>131</td>
          <td>131</td>
          <td>131</td>
          <td>131</td>
          <td>131</td>
          <td>131</td>
          <td>131</td>
        </tr>
        <tr>
          <th>3</th>
          <td>90</td>
          <td>90</td>
          <td>90</td>
          <td>82</td>
          <td>90</td>
          <td>87</td>
          <td>90</td>
          <td>90</td>
          <td>90</td>
          <td>90</td>
          <td>...</td>
          <td>90</td>
          <td>90</td>
          <td>90</td>
          <td>90</td>
          <td>90</td>
          <td>90</td>
          <td>90</td>
          <td>90</td>
          <td>90</td>
          <td>90</td>
        </tr>
        <tr>
          <th>4</th>
          <td>209</td>
          <td>209</td>
          <td>209</td>
          <td>201</td>
          <td>209</td>
          <td>201</td>
          <td>209</td>
          <td>209</td>
          <td>209</td>
          <td>209</td>
          <td>...</td>
          <td>209</td>
          <td>209</td>
          <td>209</td>
          <td>209</td>
          <td>209</td>
          <td>209</td>
          <td>209</td>
          <td>209</td>
          <td>209</td>
          <td>209</td>
        </tr>
        <tr>
          <th>5</th>
          <td>86</td>
          <td>86</td>
          <td>86</td>
          <td>82</td>
          <td>86</td>
          <td>81</td>
          <td>86</td>
          <td>86</td>
          <td>86</td>
          <td>86</td>
          <td>...</td>
          <td>86</td>
          <td>86</td>
          <td>86</td>
          <td>86</td>
          <td>86</td>
          <td>86</td>
          <td>86</td>
          <td>86</td>
          <td>86</td>
          <td>86</td>
        </tr>
        <tr>
          <th>6</th>
          <td>26</td>
          <td>26</td>
          <td>26</td>
          <td>25</td>
          <td>26</td>
          <td>25</td>
          <td>26</td>
          <td>26</td>
          <td>26</td>
          <td>26</td>
          <td>...</td>
          <td>26</td>
          <td>26</td>
          <td>26</td>
          <td>26</td>
          <td>26</td>
          <td>26</td>
          <td>26</td>
          <td>26</td>
          <td>26</td>
          <td>26</td>
        </tr>
        <tr>
          <th>7</th>
          <td>392</td>
          <td>392</td>
          <td>392</td>
          <td>365</td>
          <td>392</td>
          <td>379</td>
          <td>392</td>
          <td>392</td>
          <td>392</td>
          <td>392</td>
          <td>...</td>
          <td>392</td>
          <td>392</td>
          <td>392</td>
          <td>392</td>
          <td>392</td>
          <td>392</td>
          <td>392</td>
          <td>392</td>
          <td>392</td>
          <td>392</td>
        </tr>
        <tr>
          <th>8</th>
          <td>219</td>
          <td>219</td>
          <td>219</td>
          <td>208</td>
          <td>219</td>
          <td>198</td>
          <td>219</td>
          <td>219</td>
          <td>219</td>
          <td>219</td>
          <td>...</td>
          <td>219</td>
          <td>219</td>
          <td>219</td>
          <td>219</td>
          <td>219</td>
          <td>219</td>
          <td>219</td>
          <td>219</td>
          <td>219</td>
          <td>219</td>
        </tr>
        <tr>
          <th>9</th>
          <td>299</td>
          <td>299</td>
          <td>299</td>
          <td>279</td>
          <td>299</td>
          <td>284</td>
          <td>299</td>
          <td>299</td>
          <td>299</td>
          <td>299</td>
          <td>...</td>
          <td>299</td>
          <td>299</td>
          <td>299</td>
          <td>299</td>
          <td>299</td>
          <td>299</td>
          <td>299</td>
          <td>299</td>
          <td>299</td>
          <td>299</td>
        </tr>
        <tr>
          <th>10</th>
          <td>89</td>
          <td>89</td>
          <td>89</td>
          <td>82</td>
          <td>89</td>
          <td>86</td>
          <td>89</td>
          <td>89</td>
          <td>89</td>
          <td>89</td>
          <td>...</td>
          <td>89</td>
          <td>89</td>
          <td>89</td>
          <td>89</td>
          <td>89</td>
          <td>89</td>
          <td>89</td>
          <td>89</td>
          <td>89</td>
          <td>89</td>
        </tr>
      </tbody>
    </table>
    <p>10 rows × 29 columns</p>
    </div>




    ```python
    movies.groupby(['movie_id'])['rating'].sum()
    # calculate sum for a single column
    # it works more quickly then movies.groupby(['movie_id']).sum()['rating']
    ```




        movie_id
        1       1753
        2        420
        3        273
        4        742
        5        284
        6         93
        7       1489
        8        875
        9       1165
        10       341
        11       908
        12      1171
        13       629
        14       726
        15      1107
        16       125
        17       287
        18        28
        19       273
        20       246
        21       232
        22      1233
        23       750
        24       600
        25      1009
        26       252
        27       177
        28      1085
        29       304
        30       146
                ...
        1653       5
        1654       1
        1655       2
        1656       7
        1657       3
        1658       9
        1659       1
        1660       2
        1661       1
        1662       5
        1663       2
        1664      13
        1665       2
        1666       2
        1667       3
        1668       3
        1669       2
        1670       3
        1671       1
        1672       4
        1673       3
        1674       4
        1675       3
        1676       2
        1677       3
        1678       1
        1679       3
        1680       2
        1681       3
        1682       3
        Name: rating, Length: 1682, dtype: int64




    ```python
    movies.groupby(['movie_id', 'user_id']).sum()
    # it is possible to group by many columns
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
          <th>rating</th>
          <th>timestamp</th>
          <th>age</th>
          <th>unknown</th>
          <th>Action</th>
          <th>Adventure</th>
          <th>Animation</th>
          <th>Childrens</th>
          <th>Comedy</th>
          <th>Crime</th>
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
          <th>movie_id</th>
          <th>user_id</th>
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
          <th rowspan="30" valign="top">1</th>
          <th>1</th>
          <td>5</td>
          <td>874965758</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <td>4</td>
          <td>888550871</td>
          <td>53.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <td>4</td>
          <td>875635748</td>
          <td>33.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <td>4</td>
          <td>883599478</td>
          <td>42.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>10</th>
          <td>4</td>
          <td>877888877</td>
          <td>53.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>13</th>
          <td>3</td>
          <td>882140487</td>
          <td>47.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>15</th>
          <td>1</td>
          <td>879455635</td>
          <td>49.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>16</th>
          <td>5</td>
          <td>877717833</td>
          <td>21.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>17</th>
          <td>4</td>
          <td>885272579</td>
          <td>30.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <td>5</td>
          <td>880130802</td>
          <td>35.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>20</th>
          <td>3</td>
          <td>879667963</td>
          <td>42.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>21</th>
          <td>5</td>
          <td>874951244</td>
          <td>26.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>23</th>
          <td>5</td>
          <td>874784615</td>
          <td>30.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>25</th>
          <td>5</td>
          <td>885853415</td>
          <td>39.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>26</th>
          <td>3</td>
          <td>891350625</td>
          <td>49.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>38</th>
          <td>5</td>
          <td>892430636</td>
          <td>28.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>41</th>
          <td>4</td>
          <td>890692860</td>
          <td>33.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <td>5</td>
          <td>881105633</td>
          <td>30.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>43</th>
          <td>5</td>
          <td>875975579</td>
          <td>29.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>44</th>
          <td>4</td>
          <td>878341315</td>
          <td>0.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>45</th>
          <td>5</td>
          <td>881013176</td>
          <td>29.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>49</th>
          <td>2</td>
          <td>888068651</td>
          <td>23.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>54</th>
          <td>4</td>
          <td>880931595</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>56</th>
          <td>4</td>
          <td>892683248</td>
          <td>25.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>57</th>
          <td>5</td>
          <td>883698581</td>
          <td>16.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>58</th>
          <td>5</td>
          <td>884304483</td>
          <td>27.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>59</th>
          <td>2</td>
          <td>888203053</td>
          <td>49.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>62</th>
          <td>2</td>
          <td>879372813</td>
          <td>27.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>63</th>
          <td>3</td>
          <td>875747368</td>
          <td>31.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>64</th>
          <td>4</td>
          <td>879366214</td>
          <td>32.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <th>1658</th>
          <th>894</th>
          <td>4</td>
          <td>882404137</td>
          <td>0.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1659</th>
          <th>747</th>
          <td>1</td>
          <td>888733313</td>
          <td>19.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>1660</th>
          <th>747</th>
          <td>2</td>
          <td>888640731</td>
          <td>19.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1661</th>
          <th>751</th>
          <td>1</td>
          <td>889299429</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th rowspan="2" valign="top">1662</th>
          <th>762</th>
          <td>1</td>
          <td>878719324</td>
          <td>32.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>782</th>
          <td>4</td>
          <td>891500110</td>
          <td>21.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1663</th>
          <th>782</th>
          <td>2</td>
          <td>891499700</td>
          <td>21.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th rowspan="4" valign="top">1664</th>
          <th>782</th>
          <td>4</td>
          <td>891499699</td>
          <td>21.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>839</th>
          <td>1</td>
          <td>875752902</td>
          <td>38.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>870</th>
          <td>4</td>
          <td>890057322</td>
          <td>0.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>880</th>
          <td>4</td>
          <td>892958799</td>
          <td>13.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>1665</th>
          <th>782</th>
          <td>2</td>
          <td>891500194</td>
          <td>21.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1666</th>
          <th>782</th>
          <td>2</td>
          <td>891500194</td>
          <td>21.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1667</th>
          <th>782</th>
          <td>3</td>
          <td>891500110</td>
          <td>0.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1668</th>
          <th>782</th>
          <td>3</td>
          <td>891500067</td>
          <td>21.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>1669</th>
          <th>782</th>
          <td>2</td>
          <td>891500150</td>
          <td>21.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>1670</th>
          <th>782</th>
          <td>3</td>
          <td>891497793</td>
          <td>21.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>1671</th>
          <th>787</th>
          <td>1</td>
          <td>888980193</td>
          <td>18.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th rowspan="2" valign="top">1672</th>
          <th>828</th>
          <td>2</td>
          <td>891037722</td>
          <td>28.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>896</th>
          <td>2</td>
          <td>887159554</td>
          <td>28.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1673</th>
          <th>835</th>
          <td>3</td>
          <td>891034023</td>
          <td>44.0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1674</th>
          <th>840</th>
          <td>4</td>
          <td>891211682</td>
          <td>39.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1675</th>
          <th>851</th>
          <td>3</td>
          <td>884222085</td>
          <td>18.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1676</th>
          <th>851</th>
          <td>2</td>
          <td>875731674</td>
          <td>0.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1677</th>
          <th>854</th>
          <td>3</td>
          <td>882814368</td>
          <td>29.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1678</th>
          <th>863</th>
          <td>1</td>
          <td>889289570</td>
          <td>0.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1679</th>
          <th>863</th>
          <td>3</td>
          <td>889289491</td>
          <td>17.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>1680</th>
          <th>863</th>
          <td>2</td>
          <td>889289570</td>
          <td>17.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1681</th>
          <th>896</th>
          <td>3</td>
          <td>887160722</td>
          <td>28.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>1682</th>
          <th>916</th>
          <td>3</td>
          <td>880845755</td>
          <td>27.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
    <p>100000 rows × 22 columns</p>
    </div>




    ```python
    movies.groupby(['user_id', 'movie_id']).sum()
    # pay your attention that the changing of the order of
    # columns for grouping in
    # its list also changes the result table
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
          <th>rating</th>
          <th>timestamp</th>
          <th>age</th>
          <th>unknown</th>
          <th>Action</th>
          <th>Adventure</th>
          <th>Animation</th>
          <th>Childrens</th>
          <th>Comedy</th>
          <th>Crime</th>
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
          <th rowspan="30" valign="top">1</th>
          <th>1</th>
          <td>5</td>
          <td>874965758</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <td>3</td>
          <td>876893171</td>
          <td>24.0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>3</th>
          <td>4</td>
          <td>878542960</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>4</th>
          <td>3</td>
          <td>876893119</td>
          <td>24.0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <td>3</td>
          <td>889751712</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
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
          <th>6</th>
          <td>5</td>
          <td>887431973</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <td>4</td>
          <td>875071561</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>8</th>
          <td>1</td>
          <td>875072484</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
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
          <td>5</td>
          <td>878543541</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>10</th>
          <td>3</td>
          <td>875693118</td>
          <td>0.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>11</th>
          <td>2</td>
          <td>875072262</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
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
          <th>12</th>
          <td>5</td>
          <td>878542960</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
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
          <th>13</th>
          <td>5</td>
          <td>875071805</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>14</th>
          <td>5</td>
          <td>874965706</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>15</th>
          <td>5</td>
          <td>875071608</td>
          <td>0.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>16</th>
          <td>5</td>
          <td>878543541</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>17</th>
          <td>3</td>
          <td>875073198</td>
          <td>24.0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>18</th>
          <td>4</td>
          <td>887432020</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>19</th>
          <td>5</td>
          <td>875071515</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>20</th>
          <td>4</td>
          <td>887431883</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>21</th>
          <td>1</td>
          <td>878542772</td>
          <td>0.0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>22</th>
          <td>4</td>
          <td>875072404</td>
          <td>24.0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>23</th>
          <td>4</td>
          <td>875072895</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>24</th>
          <td>3</td>
          <td>875071713</td>
          <td>24.0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
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
          <th>25</th>
          <td>4</td>
          <td>875071805</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>26</th>
          <td>3</td>
          <td>875072442</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <td>2</td>
          <td>876892946</td>
          <td>24.0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>28</th>
          <td>4</td>
          <td>875072173</td>
          <td>24.0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>29</th>
          <td>1</td>
          <td>878542869</td>
          <td>24.0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
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
          <th>30</th>
          <td>3</td>
          <td>878542515</td>
          <td>24.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th rowspan="30" valign="top">943</th>
          <th>720</th>
          <td>1</td>
          <td>888640048</td>
          <td>22.0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>721</th>
          <td>5</td>
          <td>888639660</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>722</th>
          <td>3</td>
          <td>888640208</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>724</th>
          <td>1</td>
          <td>888639478</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>732</th>
          <td>4</td>
          <td>888639789</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>739</th>
          <td>4</td>
          <td>888639929</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>756</th>
          <td>2</td>
          <td>875502146</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>763</th>
          <td>4</td>
          <td>875501813</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>765</th>
          <td>3</td>
          <td>888640227</td>
          <td>0.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>785</th>
          <td>2</td>
          <td>888640088</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>794</th>
          <td>3</td>
          <td>888640143</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>796</th>
          <td>3</td>
          <td>888640311</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>808</th>
          <td>4</td>
          <td>888639868</td>
          <td>22.0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>816</th>
          <td>4</td>
          <td>888640186</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>824</th>
          <td>4</td>
          <td>875502483</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>825</th>
          <td>3</td>
          <td>875502283</td>
          <td>0.0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>831</th>
          <td>2</td>
          <td>875502283</td>
          <td>22.0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>840</th>
          <td>4</td>
          <td>888693104</td>
          <td>22.0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <td>1</td>
        </tr>
        <tr>
          <th>928</th>
          <td>5</td>
          <td>875502074</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
        </tr>
        <tr>
          <th>941</th>
          <td>1</td>
          <td>888639725</td>
          <td>0.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>943</th>
          <td>5</td>
          <td>888639614</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1011</th>
          <td>2</td>
          <td>875502560</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
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
          <th>1028</th>
          <td>2</td>
          <td>875502096</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>1044</th>
          <td>3</td>
          <td>888639903</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>1047</th>
          <td>2</td>
          <td>875502146</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>1067</th>
          <td>2</td>
          <td>875501756</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>1074</th>
          <td>4</td>
          <td>888640250</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <th>1188</th>
          <td>3</td>
          <td>888640250</td>
          <td>22.0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
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
          <td>1</td>
        </tr>
        <tr>
          <th>1228</th>
          <td>3</td>
          <td>888640275</td>
          <td>22.0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
          <th>1330</th>
          <td>3</td>
          <td>888692465</td>
          <td>22.0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
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
    <p>100000 rows × 22 columns</p>
    </div>




    It is possible also to show all groups


    ```python
    movies_grouped.groups
    ```




        {1: Int64Index([50260, 50261, 50262, 50263, 50264, 50265, 50266, 50267, 50268,
                     50269,
                     ...
                     50702, 50703, 50704, 50705, 50706, 50707, 50708, 50709, 50710,
                     50711],
                    dtype='int64', length=452),
         2: Int64Index([30722, 30723, 30724, 30725, 30726, 30727, 30728, 30729, 30730,
                     30731,
                     ...
                     30843, 30844, 30845, 30846, 30847, 30848, 30849, 30850, 30851,
                     30852],
                    dtype='int64', length=131),
         3: Int64Index([47904, 47905, 47906, 47907, 47908, 47909, 47910, 47911, 47912,
                     47913, 47914, 47915, 47916, 47917, 47918, 47919, 47920, 47921,
                     47922, 47923, 47924, 47925, 47926, 47927, 47928, 47929, 47930,
                     47931, 47932, 47933, 47934, 47935, 47936, 47937, 47938, 47939,
                     47940, 47941, 47942, 47943, 47944, 47945, 47946, 47947, 47948,
                     47949, 47950, 47951, 47952, 47953, 47954, 47955, 47956, 47957,
                     47958, 47959, 47960, 47961, 47962, 47963, 47964, 47965, 47966,
                     47967, 47968, 47969, 47970, 47971, 47972, 47973, 47974, 47975,
                     47976, 47977, 47978, 47979, 47980, 47981, 47982, 47983, 47984,
                     47985, 47986, 47987, 47988, 47989, 47990, 47991, 47992, 47993],
                    dtype='int64'),
         4: Int64Index([32456, 32457, 32458, 32459, 32460, 32461, 32462, 32463, 32464,
                     32465,
                     ...
                     32655, 32656, 32657, 32658, 32659, 32660, 32661, 32662, 32663,
                     32664],
                    dtype='int64', length=209),
         5: Int64Index([89357, 89358, 89359, 89360, 89361, 89362, 89363, 89364, 89365,
                     89366, 89367, 89368, 89369, 89370, 89371, 89372, 89373, 89374,
                     89375, 89376, 89377, 89378, 89379, 89380, 89381, 89382, 89383,
                     89384, 89385, 89386, 89387, 89388, 89389, 89390, 89391, 89392,
                     89393, 89394, 89395, 89396, 89397, 89398, 89399, 89400, 89401,
                     89402, 89403, 89404, 89405, 89406, 89407, 89408, 89409, 89410,
                     89411, 89412, 89413, 89414, 89415, 89416, 89417, 89418, 89419,
                     89420, 89421, 89422, 89423, 89424, 89425, 89426, 89427, 89428,
                     89429, 89430, 89431, 89432, 89433, 89434, 89435, 89436, 89437,
                     89438, 89439, 89440, 89441, 89442],
                    dtype='int64'),
         6: Int64Index([95660, 95661, 95662, 95663, 95664, 95665, 95666, 95667, 95668,
                     95669, 95670, 95671, 95672, 95673, 95674, 95675, 95676, 95677,
                     95678, 95679, 95680, 95681, 95682, 95683, 95684, 95685],
                    dtype='int64'),
         7: Int64Index([36685, 36686, 36687, 36688, 36689, 36690, 36691, 36692, 36693,
                     36694,
                     ...
                     37067, 37068, 37069, 37070, 37071, 37072, 37073, 37074, 37075,
                     37076],
                    dtype='int64', length=392),
         8: Int64Index([2632, 2633, 2634, 2635, 2636, 2637, 2638, 2639, 2640, 2641,
                     ...
                     2841, 2842, 2843, 2844, 2845, 2846, 2847, 2848, 2849, 2850],
                    dtype='int64', length=219),
         9: Int64Index([51028, 51029, 51030, 51031, 51032, 51033, 51034, 51035, 51036,
                     51037,
                     ...
                     51317, 51318, 51319, 51320, 51321, 51322, 51323, 51324, 51325,
                     51326],
                    dtype='int64', length=299),
         10: Int64Index([91967, 91968, 91969, 91970, 91971, 91972, 91973, 91974, 91975,
                     91976, 91977, 91978, 91979, 91980, 91981, 91982, 91983, 91984,
                     91985, 91986, 91987, 91988, 91989, 91990, 91991, 91992, 91993,
                     91994, 91995, 91996, 91997, 91998, 91999, 92000, 92001, 92002,
                     92003, 92004, 92005, 92006, 92007, 92008, 92009, 92010, 92011,
                     92012, 92013, 92014, 92015, 92016, 92017, 92018, 92019, 92020,
                     92021, 92022, 92023, 92024, 92025, 92026, 92027, 92028, 92029,
                     92030, 92031, 92032, 92033, 92034, 92035, 92036, 92037, 92038,
                     92039, 92040, 92041, 92042, 92043, 92044, 92045, 92046, 92047,
                     92048, 92049, 92050, 92051, 92052, 92053, 92054, 92055],
                    dtype='int64'),
         11: Int64Index([64365, 64366, 64367, 64368, 64369, 64370, 64371, 64372, 64373,
                     64374,
                     ...
                     64591, 64592, 64593, 64594, 64595, 64596, 64597, 64598, 64599,
                     64600],
                    dtype='int64', length=236),
         12: Int64Index([18462, 18463, 18464, 18465, 18466, 18467, 18468, 18469, 18470,
                     18471,
                     ...
                     18719, 18720, 18721, 18722, 18723, 18724, 18725, 18726, 18727,
                     18728],
                    dtype='int64', length=267),
         13: Int64Index([5208, 5209, 5210, 5211, 5212, 5213, 5214, 5215, 5216, 5217,
                     ...
                     5382, 5383, 5384, 5385, 5386, 5387, 5388, 5389, 5390, 5391],
                    dtype='int64', length=184),
         14: Int64Index([69923, 69924, 69925, 69926, 69927, 69928, 69929, 69930, 69931,
                     69932,
                     ...
                     70096, 70097, 70098, 70099, 70100, 70101, 70102, 70103, 70104,
                     70105],
                    dtype='int64', length=183),
         15: Int64Index([68307, 68308, 68309, 68310, 68311, 68312, 68313, 68314, 68315,
                     68316,
                     ...
                     68590, 68591, 68592, 68593, 68594, 68595, 68596, 68597, 68598,
                     68599],
                    dtype='int64', length=293),
         16: Int64Index([72394, 72395, 72396, 72397, 72398, 72399, 72400, 72401, 72402,
                     72403, 72404, 72405, 72406, 72407, 72408, 72409, 72410, 72411,
                     72412, 72413, 72414, 72415, 72416, 72417, 72418, 72419, 72420,
                     72421, 72422, 72423, 72424, 72425, 72426, 72427, 72428, 72429,
                     72430, 72431, 72432],
                    dtype='int64'),
         17: Int64Index([30377, 30378, 30379, 30380, 30381, 30382, 30383, 30384, 30385,
                     30386, 30387, 30388, 30389, 30390, 30391, 30392, 30393, 30394,
                     30395, 30396, 30397, 30398, 30399, 30400, 30401, 30402, 30403,
                     30404, 30405, 30406, 30407, 30408, 30409, 30410, 30411, 30412,
                     30413, 30414, 30415, 30416, 30417, 30418, 30419, 30420, 30421,
                     30422, 30423, 30424, 30425, 30426, 30427, 30428, 30429, 30430,
                     30431, 30432, 30433, 30434, 30435, 30436, 30437, 30438, 30439,
                     30440, 30441, 30442, 30443, 30444, 30445, 30446, 30447, 30448,
                     30449, 30450, 30451, 30452, 30453, 30454, 30455, 30456, 30457,
                     30458, 30459, 30460, 30461, 30462, 30463, 30464, 30465, 30466,
                     30467, 30468],
                    dtype='int64'),
         18: Int64Index([96837, 96838, 96839, 96840, 96841, 96842, 96843, 96844, 96845,
                     96846],
                    dtype='int64'),
         19: Int64Index([75029, 75030, 75031, 75032, 75033, 75034, 75035, 75036, 75037,
                     75038, 75039, 75040, 75041, 75042, 75043, 75044, 75045, 75046,
                     75047, 75048, 75049, 75050, 75051, 75052, 75053, 75054, 75055,
                     75056, 75057, 75058, 75059, 75060, 75061, 75062, 75063, 75064,
                     75065, 75066, 75067, 75068, 75069, 75070, 75071, 75072, 75073,
                     75074, 75075, 75076, 75077, 75078, 75079, 75080, 75081, 75082,
                     75083, 75084, 75085, 75086, 75087, 75088, 75089, 75090, 75091,
                     75092, 75093, 75094, 75095, 75096, 75097],
                    dtype='int64'),
         20: Int64Index([38849, 38850, 38851, 38852, 38853, 38854, 38855, 38856, 38857,
                     38858, 38859, 38860, 38861, 38862, 38863, 38864, 38865, 38866,
                     38867, 38868, 38869, 38870, 38871, 38872, 38873, 38874, 38875,
                     38876, 38877, 38878, 38879, 38880, 38881, 38882, 38883, 38884,
                     38885, 38886, 38887, 38888, 38889, 38890, 38891, 38892, 38893,
                     38894, 38895, 38896, 38897, 38898, 38899, 38900, 38901, 38902,
                     38903, 38904, 38905, 38906, 38907, 38908, 38909, 38910, 38911,
                     38912, 38913, 38914, 38915, 38916, 38917, 38918, 38919, 38920],
                    dtype='int64'),
         21: Int64Index([29689, 29690, 29691, 29692, 29693, 29694, 29695, 29696, 29697,
                     29698, 29699, 29700, 29701, 29702, 29703, 29704, 29705, 29706,
                     29707, 29708, 29709, 29710, 29711, 29712, 29713, 29714, 29715,
                     29716, 29717, 29718, 29719, 29720, 29721, 29722, 29723, 29724,
                     29725, 29726, 29727, 29728, 29729, 29730, 29731, 29732, 29733,
                     29734, 29735, 29736, 29737, 29738, 29739, 29740, 29741, 29742,
                     29743, 29744, 29745, 29746, 29747, 29748, 29749, 29750, 29751,
                     29752, 29753, 29754, 29755, 29756, 29757, 29758, 29759, 29760,
                     29761, 29762, 29763, 29764, 29765, 29766, 29767, 29768, 29769,
                     29770, 29771, 29772],
                    dtype='int64'),
         22: Int64Index([38950, 38951, 38952, 38953, 38954, 38955, 38956, 38957, 38958,
                     38959,
                     ...
                     39237, 39238, 39239, 39240, 39241, 39242, 39243, 39244, 39245,
                     39246],
                    dtype='int64', length=297),
         23: Int64Index([59915, 59916, 59917, 59918, 59919, 59920, 59921, 59922, 59923,
                     59924,
                     ...
                     60087, 60088, 60089, 60090, 60091, 60092, 60093, 60094, 60095,
                     60096],
                    dtype='int64', length=182),
         24: Int64Index([28958, 28959, 28960, 28961, 28962, 28963, 28964, 28965, 28966,
                     28967,
                     ...
                     29122, 29123, 29124, 29125, 29126, 29127, 29128, 29129, 29130,
                     29131],
                    dtype='int64', length=174),
         25: Int64Index([1557, 1558, 1559, 1560, 1561, 1562, 1563, 1564, 1565, 1566,
                     ...
                     1840, 1841, 1842, 1843, 1844, 1845, 1846, 1847, 1848, 1849],
                    dtype='int64', length=293),
         26: Int64Index([50187, 50188, 50189, 50190, 50191, 50192, 50193, 50194, 50195,
                     50196, 50197, 50198, 50199, 50200, 50201, 50202, 50203, 50204,
                     50205, 50206, 50207, 50208, 50209, 50210, 50211, 50212, 50213,
                     50214, 50215, 50216, 50217, 50218, 50219, 50220, 50221, 50222,
                     50223, 50224, 50225, 50226, 50227, 50228, 50229, 50230, 50231,
                     50232, 50233, 50234, 50235, 50236, 50237, 50238, 50239, 50240,
                     50241, 50242, 50243, 50244, 50245, 50246, 50247, 50248, 50249,
                     50250, 50251, 50252, 50253, 50254, 50255, 50256, 50257, 50258,
                     50259],
                    dtype='int64'),
         27: Int64Index([91757, 91758, 91759, 91760, 91761, 91762, 91763, 91764, 91765,
                     91766, 91767, 91768, 91769, 91770, 91771, 91772, 91773, 91774,
                     91775, 91776, 91777, 91778, 91779, 91780, 91781, 91782, 91783,
                     91784, 91785, 91786, 91787, 91788, 91789, 91790, 91791, 91792,
                     91793, 91794, 91795, 91796, 91797, 91798, 91799, 91800, 91801,
                     91802, 91803, 91804, 91805, 91806, 91807, 91808, 91809, 91810,
                     91811, 91812, 91813],
                    dtype='int64'),
         28: Int64Index([52923, 52924, 52925, 52926, 52927, 52928, 52929, 52930, 52931,
                     52932,
                     ...
                     53189, 53190, 53191, 53192, 53193, 53194, 53195, 53196, 53197,
                     53198],
                    dtype='int64', length=276),
         29: Int64Index([22164, 22165, 22166, 22167, 22168, 22169, 22170, 22171, 22172,
                     22173,
                     ...
                     22268, 22269, 22270, 22271, 22272, 22273, 22274, 22275, 22276,
                     22277],
                    dtype='int64', length=114),
         30: Int64Index([90497, 90498, 90499, 90500, 90501, 90502, 90503, 90504, 90505,
                     90506, 90507, 90508, 90509, 90510, 90511, 90512, 90513, 90514,
                     90515, 90516, 90517, 90518, 90519, 90520, 90521, 90522, 90523,
                     90524, 90525, 90526, 90527, 90528, 90529, 90530, 90531, 90532,
                     90533],
                    dtype='int64'),
         31: Int64Index([11303, 11304, 11305, 11306, 11307, 11308, 11309, 11310, 11311,
                     11312,
                     ...
                     11447, 11448, 11449, 11450, 11451, 11452, 11453, 11454, 11455,
                     11456],
                    dtype='int64', length=154),
         32: Int64Index([45016, 45017, 45018, 45019, 45020, 45021, 45022, 45023, 45024,
                     45025, 45026, 45027, 45028, 45029, 45030, 45031, 45032, 45033,
                     45034, 45035, 45036, 45037, 45038, 45039, 45040, 45041, 45042,
                     45043, 45044, 45045, 45046, 45047, 45048, 45049, 45050, 45051,
                     45052, 45053, 45054, 45055, 45056, 45057, 45058, 45059, 45060,
                     45061, 45062, 45063, 45064, 45065, 45066, 45067, 45068, 45069,
                     45070, 45071, 45072, 45073, 45074, 45075, 45076, 45077, 45078,
                     45079, 45080, 45081, 45082, 45083, 45084, 45085, 45086, 45087,
                     45088, 45089, 45090, 45091, 45092, 45093, 45094, 45095, 45096],
                    dtype='int64'),
         33: Int64Index([65408, 65409, 65410, 65411, 65412, 65413, 65414, 65415, 65416,
                     65417, 65418, 65419, 65420, 65421, 65422, 65423, 65424, 65425,
                     65426, 65427, 65428, 65429, 65430, 65431, 65432, 65433, 65434,
                     65435, 65436, 65437, 65438, 65439, 65440, 65441, 65442, 65443,
                     65444, 65445, 65446, 65447, 65448, 65449, 65450, 65451, 65452,
                     65453, 65454, 65455, 65456, 65457, 65458, 65459, 65460, 65461,
                     65462, 65463, 65464, 65465, 65466, 65467, 65468, 65469, 65470,
                     65471, 65472, 65473, 65474, 65475, 65476, 65477, 65478, 65479,
                     65480, 65481, 65482, 65483, 65484, 65485, 65486, 65487, 65488,
                     65489, 65490, 65491, 65492, 65493, 65494, 65495, 65496, 65497,
                     65498, 65499, 65500, 65501, 65502, 65503, 65504],
                    dtype='int64'),
         34: Int64Index([79926, 79927, 79928, 79929, 79930, 79931, 79932], dtype='int64'),
         35: Int64Index([95440, 95441, 95442, 95443, 95444, 95445, 95446, 95447, 95448,
                     95449, 95450],
                    dtype='int64'),
         36: Int64Index([98143, 98144, 98145, 98146, 98147, 98148, 98149, 98150, 98151,
                     98152, 98153, 98154, 98155],
                    dtype='int64'),
         37: Int64Index([98053, 98054, 98055, 98056, 98057, 98058, 98059, 98060], dtype='int64'),
         38: Int64Index([17126, 17127, 17128, 17129, 17130, 17131, 17132, 17133, 17134,
                     17135,
                     ...
                     17236, 17237, 17238, 17239, 17240, 17241, 17242, 17243, 17244,
                     17245],
                    dtype='int64', length=120),
         39: Int64Index([95792, 95793, 95794, 95795, 95796, 95797, 95798, 95799, 95800,
                     95801, 95802, 95803, 95804, 95805, 95806, 95807, 95808, 95809,
                     95810, 95811, 95812, 95813, 95814, 95815, 95816, 95817, 95818,
                     95819, 95820, 95821, 95822, 95823, 95824, 95825, 95826, 95827,
                     95828, 95829, 95830, 95831, 95832, 95833, 95834, 95835, 95836,
                     95837, 95838, 95839, 95840, 95841, 95842, 95843, 95844, 95845,
                     95846, 95847, 95848, 95849, 95850, 95851, 95852, 95853, 95854,
                     95855, 95856, 95857, 95858, 95859, 95860, 95861, 95862, 95863,
                     95864, 95865, 95866, 95867, 95868, 95869, 95870, 95871, 95872,
                     95873, 95874, 95875, 95876, 95877, 95878],
                    dtype='int64'),
         40: Int64Index([44143, 44144, 44145, 44146, 44147, 44148, 44149, 44150, 44151,
                     44152, 44153, 44154, 44155, 44156, 44157, 44158, 44159, 44160,
                     44161, 44162, 44163, 44164, 44165, 44166, 44167, 44168, 44169,
                     44170, 44171, 44172, 44173, 44174, 44175, 44176, 44177, 44178,
                     44179, 44180, 44181, 44182, 44183, 44184, 44185, 44186, 44187,
                     44188, 44189, 44190, 44191, 44192, 44193, 44194, 44195, 44196,
                     44197, 44198, 44199],
                    dtype='int64'),
         41: Int64Index([82344, 82345, 82346, 82347, 82348, 82349, 82350, 82351, 82352,
                     82353, 82354, 82355, 82356, 82357, 82358, 82359, 82360, 82361,
                     82362, 82363, 82364, 82365, 82366, 82367, 82368, 82369, 82370,
                     82371, 82372, 82373, 82374, 82375, 82376, 82377, 82378, 82379,
                     82380],
                    dtype='int64'),
         42: Int64Index([43318, 43319, 43320, 43321, 43322, 43323, 43324, 43325, 43326,
                     43327,
                     ...
                     43456, 43457, 43458, 43459, 43460, 43461, 43462, 43463, 43464,
                     43465],
                    dtype='int64', length=148),
         43: Int64Index([84384, 84385, 84386, 84387, 84388, 84389, 84390, 84391, 84392,
                     84393, 84394, 84395, 84396, 84397, 84398, 84399, 84400, 84401,
                     84402, 84403, 84404, 84405, 84406, 84407, 84408, 84409, 84410,
                     84411, 84412, 84413, 84414, 84415, 84416, 84417, 84418, 84419,
                     84420, 84421, 84422, 84423],
                    dtype='int64'),
         44: Int64Index([ 9998,  9999, 10000, 10001, 10002, 10003, 10004, 10005, 10006,
                     10007, 10008, 10009, 10010, 10011, 10012, 10013, 10014, 10015,
                     10016, 10017, 10018, 10019, 10020, 10021, 10022, 10023, 10024,
                     10025, 10026, 10027, 10028, 10029, 10030, 10031, 10032, 10033,
                     10034, 10035, 10036, 10037, 10038, 10039, 10040, 10041, 10042,
                     10043, 10044, 10045, 10046, 10047, 10048, 10049, 10050, 10051,
                     10052, 10053, 10054, 10055, 10056, 10057, 10058, 10059, 10060,
                     10061, 10062, 10063, 10064, 10065, 10066, 10067, 10068, 10069,
                     10070, 10071, 10072, 10073, 10074, 10075, 10076],
                    dtype='int64'),
         45: Int64Index([74427, 74428, 74429, 74430, 74431, 74432, 74433, 74434, 74435,
                     74436, 74437, 74438, 74439, 74440, 74441, 74442, 74443, 74444,
                     74445, 74446, 74447, 74448, 74449, 74450, 74451, 74452, 74453,
                     74454, 74455, 74456, 74457, 74458, 74459, 74460, 74461, 74462,
                     74463, 74464, 74465, 74466, 74467, 74468, 74469, 74470, 74471,
                     74472, 74473, 74474, 74475, 74476, 74477, 74478, 74479, 74480,
                     74481, 74482, 74483, 74484, 74485, 74486, 74487, 74488, 74489,
                     74490, 74491, 74492, 74493, 74494, 74495, 74496, 74497, 74498,
                     74499, 74500, 74501, 74502, 74503, 74504, 74505, 74506],
                    dtype='int64'),
         46: Int64Index([90030, 90031, 90032, 90033, 90034, 90035, 90036, 90037, 90038,
                     90039, 90040, 90041, 90042, 90043, 90044, 90045, 90046, 90047,
                     90048, 90049, 90050, 90051, 90052, 90053, 90054, 90055, 90056],
                    dtype='int64'),
         47: Int64Index([76714, 76715, 76716, 76717, 76718, 76719, 76720, 76721, 76722,
                     76723,
                     ...
                     76837, 76838, 76839, 76840, 76841, 76842, 76843, 76844, 76845,
                     76846],
                    dtype='int64', length=133),
         48: Int64Index([66503, 66504, 66505, 66506, 66507, 66508, 66509, 66510, 66511,
                     66512,
                     ...
                     66610, 66611, 66612, 66613, 66614, 66615, 66616, 66617, 66618,
                     66619],
                    dtype='int64', length=117),
         49: Int64Index([74043, 74044, 74045, 74046, 74047, 74048, 74049, 74050, 74051,
                     74052, 74053, 74054, 74055, 74056, 74057, 74058, 74059, 74060,
                     74061, 74062, 74063, 74064, 74065, 74066, 74067, 74068, 74069,
                     74070, 74071, 74072, 74073, 74074, 74075, 74076, 74077, 74078,
                     74079, 74080, 74081, 74082, 74083, 74084, 74085, 74086, 74087,
                     74088, 74089, 74090, 74091, 74092, 74093, 74094, 74095, 74096,
                     74097, 74098, 74099, 74100, 74101, 74102, 74103, 74104, 74105,
                     74106, 74107, 74108, 74109, 74110, 74111, 74112, 74113, 74114,
                     74115, 74116, 74117, 74118, 74119, 74120, 74121, 74122, 74123],
                    dtype='int64'),
         50: Int64Index([33306, 33307, 33308, 33309, 33310, 33311, 33312, 33313, 33314,
                     33315,
                     ...
                     33879, 33880, 33881, 33882, 33883, 33884, 33885, 33886, 33887,
                     33888],
                    dtype='int64', length=583),
         51: Int64Index([35250, 35251, 35252, 35253, 35254, 35255, 35256, 35257, 35258,
                     35259, 35260, 35261, 35262, 35263, 35264, 35265, 35266, 35267,
                     35268, 35269, 35270, 35271, 35272, 35273, 35274, 35275, 35276,
                     35277, 35278, 35279, 35280, 35281, 35282, 35283, 35284, 35285,
                     35286, 35287, 35288, 35289, 35290, 35291, 35292, 35293, 35294,
                     35295, 35296, 35297, 35298, 35299, 35300, 35301, 35302, 35303,
                     35304, 35305, 35306, 35307, 35308, 35309, 35310, 35311, 35312,
                     35313, 35314, 35315, 35316, 35317, 35318, 35319, 35320, 35321,
                     35322, 35323, 35324, 35325, 35326, 35327, 35328, 35329, 35330],
                    dtype='int64'),
         52: Int64Index([43585, 43586, 43587, 43588, 43589, 43590, 43591, 43592, 43593,
                     43594, 43595, 43596, 43597, 43598, 43599, 43600, 43601, 43602,
                     43603, 43604, 43605, 43606, 43607, 43608, 43609, 43610, 43611,
                     43612, 43613, 43614, 43615, 43616, 43617, 43618, 43619, 43620,
                     43621, 43622, 43623, 43624, 43625, 43626, 43627, 43628, 43629,
                     43630, 43631, 43632, 43633, 43634, 43635, 43636, 43637, 43638,
                     43639, 43640, 43641, 43642, 43643, 43644, 43645, 43646, 43647,
                     43648, 43649, 43650, 43651, 43652, 43653, 43654, 43655, 43656,
                     43657, 43658, 43659, 43660, 43661, 43662, 43663, 43664, 43665,
                     43666, 43667, 43668, 43669, 43670, 43671, 43672, 43673, 43674,
                     43675],
                    dtype='int64'),
         53: Int64Index([8234, 8235, 8236, 8237, 8238, 8239, 8240, 8241, 8242, 8243,
                     ...
                     8352, 8353, 8354, 8355, 8356, 8357, 8358, 8359, 8360, 8361],
                    dtype='int64', length=128),
         54: Int64Index([38380, 38381, 38382, 38383, 38384, 38385, 38386, 38387, 38388,
                     38389,
                     ...
                     38474, 38475, 38476, 38477, 38478, 38479, 38480, 38481, 38482,
                     38483],
                    dtype='int64', length=104),
         55: Int64Index([18729, 18730, 18731, 18732, 18733, 18734, 18735, 18736, 18737,
                     18738,
                     ...
                     18868, 18869, 18870, 18871, 18872, 18873, 18874, 18875, 18876,
                     18877],
                    dtype='int64', length=149),
         56: Int64Index([16082, 16083, 16084, 16085, 16086, 16087, 16088, 16089, 16090,
                     16091,
                     ...
                     16466, 16467, 16468, 16469, 16470, 16471, 16472, 16473, 16474,
                     16475],
                    dtype='int64', length=394),
         57: Int64Index([80695, 80696, 80697, 80698, 80699, 80700, 80701, 80702, 80703,
                     80704, 80705, 80706, 80707, 80708, 80709, 80710, 80711, 80712,
                     80713, 80714, 80715, 80716, 80717, 80718, 80719, 80720, 80721,
                     80722, 80723, 80724, 80725, 80726, 80727, 80728, 80729, 80730,
                     80731, 80732, 80733, 80734],
                    dtype='int64'),
         58: Int64Index([52264, 52265, 52266, 52267, 52268, 52269, 52270, 52271, 52272,
                     52273,
                     ...
                     52429, 52430, 52431, 52432, 52433, 52434, 52435, 52436, 52437,
                     52438],
                    dtype='int64', length=175),
         59: Int64Index([74256, 74257, 74258, 74259, 74260, 74261, 74262, 74263, 74264,
                     74265, 74266, 74267, 74268, 74269, 74270, 74271, 74272, 74273,
                     74274, 74275, 74276, 74277, 74278, 74279, 74280, 74281, 74282,
                     74283, 74284, 74285, 74286, 74287, 74288, 74289, 74290, 74291,
                     74292, 74293, 74294, 74295, 74296, 74297, 74298, 74299, 74300,
                     74301, 74302, 74303, 74304, 74305, 74306, 74307, 74308, 74309,
                     74310, 74311, 74312, 74313, 74314, 74315, 74316, 74317, 74318,
                     74319, 74320, 74321, 74322, 74323, 74324, 74325, 74326, 74327,
                     74328, 74329, 74330, 74331, 74332, 74333, 74334, 74335, 74336,
                     74337, 74338],
                    dtype='int64'),
         60: Int64Index([74192, 74193, 74194, 74195, 74196, 74197, 74198, 74199, 74200,
                     74201, 74202, 74203, 74204, 74205, 74206, 74207, 74208, 74209,
                     74210, 74211, 74212, 74213, 74214, 74215, 74216, 74217, 74218,
                     74219, 74220, 74221, 74222, 74223, 74224, 74225, 74226, 74227,
                     74228, 74229, 74230, 74231, 74232, 74233, 74234, 74235, 74236,
                     74237, 74238, 74239, 74240, 74241, 74242, 74243, 74244, 74245,
                     74246, 74247, 74248, 74249, 74250, 74251, 74252, 74253, 74254,
                     74255],
                    dtype='int64'),
         61: Int64Index([69593, 69594, 69595, 69596, 69597, 69598, 69599, 69600, 69601,
                     69602, 69603, 69604, 69605, 69606, 69607, 69608, 69609, 69610,
                     69611, 69612, 69613, 69614, 69615, 69616, 69617, 69618, 69619,
                     69620, 69621, 69622, 69623, 69624, 69625, 69626, 69627, 69628,
                     69629, 69630, 69631, 69632, 69633, 69634, 69635, 69636, 69637,
                     69638, 69639, 69640, 69641, 69642, 69643, 69644, 69645, 69646,
                     69647, 69648, 69649, 69650, 69651],
                    dtype='int64'),
         62: Int64Index([33179, 33180, 33181, 33182, 33183, 33184, 33185, 33186, 33187,
                     33188,
                     ...
                     33296, 33297, 33298, 33299, 33300, 33301, 33302, 33303, 33304,
                     33305],
                    dtype='int64', length=127),
         63: Int64Index([84259, 84260, 84261, 84262, 84263, 84264, 84265, 84266, 84267,
                     84268, 84269, 84270, 84271, 84272, 84273, 84274, 84275, 84276,
                     84277, 84278, 84279, 84280, 84281, 84282, 84283, 84284, 84285,
                     84286, 84287, 84288, 84289, 84290, 84291, 84292, 84293, 84294,
                     84295, 84296, 84297, 84298, 84299, 84300, 84301, 84302, 84303,
                     84304, 84305, 84306, 84307, 84308, 84309, 84310, 84311, 84312,
                     84313, 84314, 84315, 84316, 84317, 84318, 84319, 84320, 84321,
                     84322, 84323, 84324, 84325, 84326, 84327, 84328, 84329, 84330,
                     84331, 84332, 84333, 84334, 84335, 84336, 84337, 84338, 84339,
                     84340],
                    dtype='int64'),
         64: Int64Index([46920, 46921, 46922, 46923, 46924, 46925, 46926, 46927, 46928,
                     46929,
                     ...
                     47193, 47194, 47195, 47196, 47197, 47198, 47199, 47200, 47201,
                     47202],
                    dtype='int64', length=283),
         65: Int64Index([53291, 53292, 53293, 53294, 53295, 53296, 53297, 53298, 53299,
                     53300,
                     ...
                     53396, 53397, 53398, 53399, 53400, 53401, 53402, 53403, 53404,
                     53405],
                    dtype='int64', length=115),
         66: Int64Index([3270, 3271, 3272, 3273, 3274, 3275, 3276, 3277, 3278, 3279,
                     ...
                     3422, 3423, 3424, 3425, 3426, 3427, 3428, 3429, 3430, 3431],
                    dtype='int64', length=162),
         67: Int64Index([682, 683, 684, 685, 686, 687, 688, 689, 690, 691,
                     ...
                     775, 776, 777, 778, 779, 780, 781, 782, 783, 784],
                    dtype='int64', length=103),
         68: Int64Index([35116, 35117, 35118, 35119, 35120, 35121, 35122, 35123, 35124,
                     35125,
                     ...
                     35240, 35241, 35242, 35243, 35244, 35245, 35246, 35247, 35248,
                     35249],
                    dtype='int64', length=134),
         69: Int64Index([41819, 41820, 41821, 41822, 41823, 41824, 41825, 41826, 41827,
                     41828,
                     ...
                     42130, 42131, 42132, 42133, 42134, 42135, 42136, 42137, 42138,
                     42139],
                    dtype='int64', length=321),
         70: Int64Index([3019, 3020, 3021, 3022, 3023, 3024, 3025, 3026, 3027, 3028,
                     ...
                     3260, 3261, 3262, 3263, 3264, 3265, 3266, 3267, 3268, 3269],
                    dtype='int64', length=251),
         71: Int64Index([9676, 9677, 9678, 9679, 9680, 9681, 9682, 9683, 9684, 9685,
                     ...
                     9886, 9887, 9888, 9889, 9890, 9891, 9892, 9893, 9894, 9895],
                    dtype='int64', length=220),
         72: Int64Index([41571, 41572, 41573, 41574, 41575, 41576, 41577, 41578, 41579,
                     41580,
                     ...
                     41690, 41691, 41692, 41693, 41694, 41695, 41696, 41697, 41698,
                     41699],
                    dtype='int64', length=129),
         73: Int64Index([79791, 79792, 79793, 79794, 79795, 79796, 79797, 79798, 79799,
                     79800,
                     ...
                     79909, 79910, 79911, 79912, 79913, 79914, 79915, 79916, 79917,
                     79918],
                    dtype='int64', length=128),
         74: Int64Index([95031, 95032, 95033, 95034, 95035, 95036, 95037], dtype='int64'),
         75: Int64Index([98947, 98948, 98949, 98950, 98951], dtype='int64'),
         76: Int64Index([70175, 70176, 70177, 70178, 70179, 70180, 70181, 70182, 70183,
                     70184, 70185, 70186, 70187, 70188, 70189, 70190, 70191, 70192,
                     70193, 70194, 70195, 70196, 70197, 70198, 70199, 70200, 70201,
                     70202, 70203, 70204, 70205, 70206, 70207, 70208, 70209, 70210,
                     70211, 70212, 70213, 70214, 70215, 70216, 70217, 70218, 70219,
                     70220, 70221, 70222, 70223, 70224, 70225, 70226, 70227, 70228],
                    dtype='int64'),
         77: Int64Index([19652, 19653, 19654, 19655, 19656, 19657, 19658, 19659, 19660,
                     19661,
                     ...
                     19793, 19794, 19795, 19796, 19797, 19798, 19799, 19800, 19801,
                     19802],
                    dtype='int64', length=151),
         78: Int64Index([78277, 78278, 78279, 78280, 78281, 78282, 78283, 78284, 78285,
                     78286, 78287, 78288, 78289, 78290, 78291, 78292, 78293, 78294,
                     78295, 78296, 78297, 78298, 78299, 78300, 78301, 78302, 78303,
                     78304, 78305, 78306, 78307, 78308, 78309],
                    dtype='int64'),
         79: Int64Index([14030, 14031, 14032, 14033, 14034, 14035, 14036, 14037, 14038,
                     14039,
                     ...
                     14356, 14357, 14358, 14359, 14360, 14361, 14362, 14363, 14364,
                     14365],
                    dtype='int64', length=336),
         80: Int64Index([20511, 20512, 20513, 20514, 20515, 20516, 20517, 20518, 20519,
                     20520, 20521, 20522, 20523, 20524, 20525, 20526, 20527, 20528,
                     20529, 20530, 20531, 20532, 20533, 20534, 20535, 20536, 20537,
                     20538, 20539, 20540, 20541, 20542, 20543, 20544, 20545, 20546,
                     20547, 20548, 20549, 20550, 20551, 20552, 20553, 20554, 20555,
                     20556, 20557, 20558, 20559, 20560, 20561, 20562, 20563, 20564,
                     20565, 20566, 20567, 20568, 20569, 20570, 20571, 20572, 20573,
                     20574, 20575, 20576, 20577, 20578],
                    dtype='int64'),
         81: Int64Index([68830, 68831, 68832, 68833, 68834, 68835, 68836, 68837, 68838,
                     68839,
                     ...
                     68930, 68931, 68932, 68933, 68934, 68935, 68936, 68937, 68938,
                     68939],
                    dtype='int64', length=110),
         82: Int64Index([48549, 48550, 48551, 48552, 48553, 48554, 48555, 48556, 48557,
                     48558,
                     ...
                     48800, 48801, 48802, 48803, 48804, 48805, 48806, 48807, 48808,
                     48809],
                    dtype='int64', length=261),
         83: Int64Index([67000, 67001, 67002, 67003, 67004, 67005, 67006, 67007, 67008,
                     67009,
                     ...
                     67166, 67167, 67168, 67169, 67170, 67171, 67172, 67173, 67174,
                     67175],
                    dtype='int64', length=176),
         84: Int64Index([91706, 91707, 91708, 91709, 91710, 91711, 91712, 91713, 91714,
                     91715, 91716, 91717, 91718, 91719, 91720, 91721, 91722, 91723],
                    dtype='int64'),
         85: Int64Index([26963, 26964, 26965, 26966, 26967, 26968, 26969, 26970, 26971,
                     26972, 26973, 26974, 26975, 26976, 26977, 26978, 26979, 26980,
                     26981, 26982, 26983, 26984, 26985, 26986, 26987, 26988, 26989,
                     26990, 26991, 26992, 26993, 26994, 26995, 26996, 26997, 26998,
                     26999, 27000, 27001, 27002, 27003, 27004, 27005, 27006, 27007,
                     27008, 27009, 27010, 27011, 27012, 27013, 27014, 27015, 27016,
                     27017, 27018, 27019, 27020],
                    dtype='int64'),
         86: Int64Index([45201, 45202, 45203, 45204, 45205, 45206, 45207, 45208, 45209,
                     45210,
                     ...
                     45341, 45342, 45343, 45344, 45345, 45346, 45347, 45348, 45349,
                     45350],
                    dtype='int64', length=150),
         87: Int64Index([67819, 67820, 67821, 67822, 67823, 67824, 67825, 67826, 67827,
                     67828,
                     ...
                     67947, 67948, 67949, 67950, 67951, 67952, 67953, 67954, 67955,
                     67956],
                    dtype='int64', length=138),
         88: Int64Index([53961, 53962, 53963, 53964, 53965, 53966, 53967, 53968, 53969,
                     53970,
                     ...
                     54164, 54165, 54166, 54167, 54168, 54169, 54170, 54171, 54172,
                     54173],
                    dtype='int64', length=213),
         89: Int64Index([31757, 31758, 31759, 31760, 31761, 31762, 31763, 31764, 31765,
                     31766,
                     ...
                     32022, 32023, 32024, 32025, 32026, 32027, 32028, 32029, 32030,
                     32031],
                    dtype='int64', length=275),
         90: Int64Index([38653, 38654, 38655, 38656, 38657, 38658, 38659, 38660, 38661,
                     38662, 38663, 38664, 38665, 38666, 38667, 38668, 38669, 38670,
                     38671, 38672, 38673, 38674, 38675, 38676, 38677, 38678, 38679,
                     38680, 38681, 38682, 38683, 38684, 38685, 38686, 38687, 38688,
                     38689, 38690, 38691, 38692, 38693, 38694, 38695, 38696, 38697,
                     38698, 38699, 38700, 38701, 38702, 38703, 38704, 38705, 38706,
                     38707, 38708, 38709, 38710, 38711, 38712, 38713, 38714, 38715,
                     38716, 38717, 38718, 38719, 38720, 38721, 38722, 38723, 38724,
                     38725, 38726, 38727, 38728, 38729, 38730, 38731, 38732, 38733,
                     38734, 38735, 38736, 38737, 38738, 38739, 38740, 38741, 38742,
                     38743, 38744, 38745, 38746, 38747],
                    dtype='int64'),
         91: Int64Index([56959, 56960, 56961, 56962, 56963, 56964, 56965, 56966, 56967,
                     56968,
                     ...
                     57092, 57093, 57094, 57095, 57096, 57097, 57098, 57099, 57100,
                     57101],
                    dtype='int64', length=143),
         92: Int64Index([45097, 45098, 45099, 45100, 45101, 45102, 45103, 45104, 45105,
                     45106,
                     ...
                     45191, 45192, 45193, 45194, 45195, 45196, 45197, 45198, 45199,
                     45200],
                    dtype='int64', length=104),
         93: Int64Index([65148, 65149, 65150, 65151, 65152, 65153, 65154, 65155, 65156,
                     65157,
                     ...
                     65250, 65251, 65252, 65253, 65254, 65255, 65256, 65257, 65258,
                     65259],
                    dtype='int64', length=112),
         94: Int64Index([2331, 2332, 2333, 2334, 2335, 2336, 2337, 2338, 2339, 2340,
                     ...
                     2458, 2459, 2460, 2461, 2462, 2463, 2464, 2465, 2466, 2467],
                    dtype='int64', length=137),
         95: Int64Index([13542, 13543, 13544, 13545, 13546, 13547, 13548, 13549, 13550,
                     13551,
                     ...
                     13751, 13752, 13753, 13754, 13755, 13756, 13757, 13758, 13759,
                     13760],
                    dtype='int64', length=219),
         96: Int64Index([21800, 21801, 21802, 21803, 21804, 21805, 21806, 21807, 21808,
                     21809,
                     ...
                     22085, 22086, 22087, 22088, 22089, 22090, 22091, 22092, 22093,
                     22094],
                    dtype='int64', length=295),
         97: Int64Index([37220, 37221, 37222, 37223, 37224, 37225, 37226, 37227, 37228,
                     37229,
                     ...
                     37466, 37467, 37468, 37469, 37470, 37471, 37472, 37473, 37474,
                     37475],
                    dtype='int64', length=256),
         98: Int64Index([15692, 15693, 15694, 15695, 15696, 15697, 15698, 15699, 15700,
                     15701,
                     ...
                     16072, 16073, 16074, 16075, 16076, 16077, 16078, 16079, 16080,
                     16081],
                    dtype='int64', length=390),
         99: Int64Index([59079, 59080, 59081, 59082, 59083, 59084, 59085, 59086, 59087,
                     59088,
                     ...
                     59241, 59242, 59243, 59244, 59245, 59246, 59247, 59248, 59249,
                     59250],
                    dtype='int64', length=172),
         100: Int64Index([11771, 11772, 11773, 11774, 11775, 11776, 11777, 11778, 11779,
                     11780,
                     ...
                     12269, 12270, 12271, 12272, 12273, 12274, 12275, 12276, 12277,
                     12278],
                    dtype='int64', length=508),
         101: Int64Index([37892, 37893, 37894, 37895, 37896, 37897, 37898, 37899, 37900,
                     37901, 37902, 37903, 37904, 37905, 37906, 37907, 37908, 37909,
                     37910, 37911, 37912, 37913, 37914, 37915, 37916, 37917, 37918,
                     37919, 37920, 37921, 37922, 37923, 37924, 37925, 37926, 37927,
                     37928, 37929, 37930, 37931, 37932, 37933, 37934, 37935, 37936,
                     37937, 37938, 37939, 37940, 37941, 37942, 37943, 37944, 37945,
                     37946, 37947, 37948, 37949, 37950, 37951, 37952, 37953, 37954,
                     37955, 37956, 37957, 37958, 37959, 37960, 37961, 37962, 37963,
                     37964],
                    dtype='int64'),
         102: Int64Index([92972, 92973, 92974, 92975, 92976, 92977, 92978, 92979, 92980,
                     92981, 92982, 92983, 92984, 92985, 92986, 92987, 92988, 92989,
                     92990, 92991, 92992, 92993, 92994, 92995, 92996, 92997, 92998,
                     92999, 93000, 93001, 93002, 93003, 93004, 93005, 93006, 93007,
                     93008, 93009, 93010, 93011, 93012, 93013, 93014, 93015, 93016,
                     93017, 93018, 93019, 93020, 93021, 93022, 93023, 93024, 93025],
                    dtype='int64'),
         103: Int64Index([82902, 82903, 82904, 82905, 82906, 82907, 82908, 82909, 82910,
                     82911, 82912, 82913, 82914, 82915, 82916],
                    dtype='int64'),
         104: Int64Index([96850, 96851, 96852, 96853, 96854], dtype='int64'),
         105: Int64Index([27383, 27384, 27385, 27386, 27387, 27388, 27389, 27390, 27391,
                     27392, 27393, 27394, 27395, 27396, 27397, 27398, 27399, 27400,
                     27401, 27402, 27403, 27404, 27405, 27406, 27407, 27408, 27409,
                     27410, 27411, 27412, 27413, 27414, 27415, 27416, 27417, 27418,
                     27419, 27420, 27421, 27422, 27423, 27424, 27425, 27426, 27427,
                     27428, 27429, 27430, 27431, 27432, 27433, 27434, 27435, 27436,
                     27437, 27438, 27439, 27440, 27441, 27442, 27443, 27444, 27445,
                     27446, 27447, 27448, 27449, 27450, 27451, 27452, 27453, 27454,
                     27455, 27456],
                    dtype='int64'),
         106: Int64Index([14366, 14367, 14368, 14369, 14370, 14371, 14372, 14373, 14374,
                     14375, 14376, 14377, 14378, 14379, 14380, 14381, 14382, 14383,
                     14384, 14385, 14386, 14387, 14388, 14389, 14390, 14391, 14392,
                     14393, 14394, 14395, 14396, 14397, 14398, 14399, 14400, 14401,
                     14402, 14403, 14404, 14405, 14406, 14407, 14408, 14409, 14410,
                     14411, 14412, 14413, 14414, 14415, 14416, 14417, 14418, 14419,
                     14420, 14421, 14422, 14423, 14424, 14425, 14426, 14427, 14428,
                     14429, 14430, 14431, 14432, 14433, 14434, 14435, 14436],
                    dtype='int64'),
         107: Int64Index([80338, 80339, 80340, 80341, 80342, 80343, 80344, 80345, 80346,
                     80347, 80348, 80349, 80350, 80351, 80352, 80353, 80354, 80355,
                     80356, 80357, 80358, 80359, 80360, 80361, 80362, 80363, 80364,
                     80365, 80366, 80367, 80368, 80369, 80370, 80371, 80372, 80373,
                     80374, 80375, 80376, 80377, 80378, 80379],
                    dtype='int64'),
         108: Int64Index([3735, 3736, 3737, 3738, 3739, 3740, 3741, 3742, 3743, 3744, 3745,
                     3746, 3747, 3748, 3749, 3750, 3751, 3752, 3753, 3754, 3755, 3756,
                     3757, 3758, 3759, 3760, 3761, 3762, 3763, 3764, 3765, 3766, 3767,
                     3768, 3769, 3770, 3771, 3772, 3773, 3774, 3775, 3776, 3777, 3778,
                     3779, 3780, 3781, 3782, 3783, 3784, 3785, 3786, 3787, 3788, 3789,
                     3790, 3791, 3792, 3793, 3794, 3795, 3796, 3797, 3798, 3799],
                    dtype='int64'),
         109: Int64Index([29395, 29396, 29397, 29398, 29399, 29400, 29401, 29402, 29403,
                     29404,
                     ...
                     29515, 29516, 29517, 29518, 29519, 29520, 29521, 29522, 29523,
                     29524],
                    dtype='int64', length=130),
         110: Int64Index([6354, 6355, 6356, 6357, 6358, 6359, 6360, 6361, 6362, 6363, 6364,
                     6365, 6366, 6367, 6368, 6369, 6370, 6371, 6372, 6373, 6374, 6375,
                     6376, 6377, 6378, 6379, 6380, 6381, 6382, 6383, 6384],
                    dtype='int64'),
         111: Int64Index([1253, 1254, 1255, 1256, 1257, 1258, 1259, 1260, 1261, 1262,
                     ...
                     1515, 1516, 1517, 1518, 1519, 1520, 1521, 1522, 1523, 1524],
                    dtype='int64', length=272),
         112: Int64Index([83310, 83311, 83312, 83313, 83314, 83315, 83316, 83317, 83318,
                     83319, 83320, 83321, 83322, 83323, 83324, 83325, 83326, 83327,
                     83328, 83329],
                    dtype='int64'),
         113: Int64Index([99324, 99325, 99326, 99327, 99328, 99329, 99330, 99331, 99332], dtype='int64'),
         114: Int64Index([51523, 51524, 51525, 51526, 51527, 51528, 51529, 51530, 51531,
                     51532, 51533, 51534, 51535, 51536, 51537, 51538, 51539, 51540,
                     51541, 51542, 51543, 51544, 51545, 51546, 51547, 51548, 51549,
                     51550, 51551, 51552, 51553, 51554, 51555, 51556, 51557, 51558,
                     51559, 51560, 51561, 51562, 51563, 51564, 51565, 51566, 51567,
                     51568, 51569, 51570, 51571, 51572, 51573, 51574, 51575, 51576,
                     51577, 51578, 51579, 51580, 51581, 51582, 51583, 51584, 51585,
                     51586, 51587, 51588, 51589],
                    dtype='int64'),
         115: Int64Index([94661, 94662, 94663, 94664, 94665, 94666, 94667, 94668, 94669,
                     94670, 94671, 94672, 94673, 94674, 94675],
                    dtype='int64'),
         116: Int64Index([4347, 4348, 4349, 4350, 4351, 4352, 4353, 4354, 4355, 4356,
                     ...
                     4462, 4463, 4464, 4465, 4466, 4467, 4468, 4469, 4470, 4471],
                    dtype='int64', length=125),
         117: Int64Index([10077, 10078, 10079, 10080, 10081, 10082, 10083, 10084, 10085,
                     10086,
                     ...
                     10445, 10446, 10447, 10448, 10449, 10450, 10451, 10452, 10453,
                     10454],
                    dtype='int64', length=378),
         118: Int64Index([12452, 12453, 12454, 12455, 12456, 12457, 12458, 12459, 12460,
                     12461,
                     ...
                     12735, 12736, 12737, 12738, 12739, 12740, 12741, 12742, 12743,
                     12744],
                    dtype='int64', length=293),
         119: Int64Index([94001, 94002, 94003, 94004], dtype='int64'),
         120: Int64Index([86798, 86799, 86800, 86801, 86802, 86803, 86804, 86805, 86806,
                     86807, 86808, 86809, 86810, 86811, 86812, 86813, 86814, 86815,
                     86816, 86817, 86818, 86819, 86820, 86821, 86822, 86823, 86824,
                     86825, 86826, 86827, 86828, 86829, 86830, 86831, 86832, 86833,
                     86834, 86835, 86836, 86837, 86838, 86839, 86840, 86841, 86842,
                     86843, 86844, 86845, 86846, 86847, 86848, 86849, 86850, 86851,
                     86852, 86853, 86854, 86855, 86856, 86857, 86858, 86859, 86860,
                     86861, 86862, 86863, 86864],
                    dtype='int64'),
         121: Int64Index([14667, 14668, 14669, 14670, 14671, 14672, 14673, 14674, 14675,
                     14676,
                     ...
                     15086, 15087, 15088, 15089, 15090, 15091, 15092, 15093, 15094,
                     15095],
                    dtype='int64', length=429),
         122: Int64Index([39247, 39248, 39249, 39250, 39251, 39252, 39253, 39254, 39255,
                     39256,
                     ...
                     39343, 39344, 39345, 39346, 39347, 39348, 39349, 39350, 39351,
                     39352],
                    dtype='int64', length=106),
         123: Int64Index([82476, 82477, 82478, 82479, 82480, 82481, 82482, 82483, 82484,
                     82485,
                     ...
                     82581, 82582, 82583, 82584, 82585, 82586, 82587, 82588, 82589,
                     82590],
                    dtype='int64', length=115),
         124: Int64Index([65948, 65949, 65950, 65951, 65952, 65953, 65954, 65955, 65956,
                     65957,
                     ...
                     66125, 66126, 66127, 66128, 66129, 66130, 66131, 66132, 66133,
                     66134],
                    dtype='int64', length=187),
         125: Int64Index([62955, 62956, 62957, 62958, 62959, 62960, 62961, 62962, 62963,
                     62964,
                     ...
                     63189, 63190, 63191, 63192, 63193, 63194, 63195, 63196, 63197,
                     63198],
                    dtype='int64', length=244),
         126: Int64Index([50090, 50091, 50092, 50093, 50094, 50095, 50096, 50097, 50098,
                     50099, 50100, 50101, 50102, 50103, 50104, 50105, 50106, 50107,
                     50108, 50109, 50110, 50111, 50112, 50113, 50114, 50115, 50116,
                     50117, 50118, 50119, 50120, 50121, 50122, 50123, 50124, 50125,
                     50126, 50127, 50128, 50129, 50130, 50131, 50132, 50133, 50134,
                     50135, 50136, 50137, 50138, 50139, 50140, 50141, 50142, 50143,
                     50144, 50145, 50146, 50147, 50148, 50149, 50150, 50151, 50152,
                     50153, 50154, 50155, 50156, 50157, 50158, 50159, 50160, 50161,
                     50162, 50163, 50164, 50165, 50166, 50167, 50168, 50169, 50170,
                     50171, 50172, 50173, 50174, 50175, 50176, 50177, 50178, 50179,
                     50180, 50181, 50182, 50183, 50184, 50185, 50186],
                    dtype='int64'),
         127: Int64Index([32665, 32666, 32667, 32668, 32669, 32670, 32671, 32672, 32673,
                     32674,
                     ...
                     33068, 33069, 33070, 33071, 33072, 33073, 33074, 33075, 33076,
                     33077],
                    dtype='int64', length=413),
         128: Int64Index([20446, 20447, 20448, 20449, 20450, 20451, 20452, 20453, 20454,
                     20455, 20456, 20457, 20458, 20459, 20460, 20461, 20462, 20463,
                     20464, 20465, 20466, 20467, 20468, 20469, 20470, 20471, 20472,
                     20473, 20474, 20475, 20476, 20477, 20478, 20479, 20480, 20481,
                     20482, 20483, 20484, 20485, 20486, 20487, 20488, 20489, 20490,
                     20491, 20492, 20493, 20494, 20495, 20496, 20497, 20498, 20499,
                     20500, 20501, 20502, 20503, 20504, 20505, 20506, 20507, 20508,
                     20509, 20510],
                    dtype='int64'),
         129: Int64Index([71055, 71056, 71057, 71058, 71059, 71060, 71061, 71062, 71063,
                     71064,
                     ...
                     71174, 71175, 71176, 71177, 71178, 71179, 71180, 71181, 71182,
                     71183],
                    dtype='int64', length=129),
         130: Int64Index([93757, 93758, 93759, 93760, 93761, 93762, 93763, 93764, 93765,
                     93766, 93767, 93768, 93769, 93770, 93771, 93772, 93773, 93774,
                     93775, 93776, 93777, 93778, 93779],
                    dtype='int64'),
         131: Int64Index([69828, 69829, 69830, 69831, 69832, 69833, 69834, 69835, 69836,
                     69837, 69838, 69839, 69840, 69841, 69842, 69843, 69844, 69845,
                     69846, 69847, 69848, 69849, 69850, 69851, 69852, 69853, 69854,
                     69855, 69856, 69857, 69858, 69859, 69860, 69861, 69862, 69863,
                     69864, 69865, 69866, 69867, 69868, 69869, 69870, 69871, 69872,
                     69873, 69874, 69875, 69876, 69877, 69878, 69879, 69880, 69881,
                     69882, 69883, 69884, 69885, 69886, 69887, 69888, 69889, 69890,
                     69891, 69892, 69893, 69894, 69895, 69896, 69897, 69898, 69899,
                     69900, 69901, 69902, 69903, 69904, 69905, 69906, 69907, 69908,
                     69909, 69910, 69911, 69912, 69913, 69914, 69915, 69916, 69917,
                     69918, 69919, 69920, 69921, 69922],
                    dtype='int64'),
         132: Int64Index([62146, 62147, 62148, 62149, 62150, 62151, 62152, 62153, 62154,
                     62155,
                     ...
                     62382, 62383, 62384, 62385, 62386, 62387, 62388, 62389, 62390,
                     62391],
                    dtype='int64', length=246),
         133: Int64Index([60097, 60098, 60099, 60100, 60101, 60102, 60103, 60104, 60105,
                     60106,
                     ...
                     60258, 60259, 60260, 60261, 60262, 60263, 60264, 60265, 60266,
                     60267],
                    dtype='int64', length=171),
         134: Int64Index([59717, 59718, 59719, 59720, 59721, 59722, 59723, 59724, 59725,
                     59726,
                     ...
                     59905, 59906, 59907, 59908, 59909, 59910, 59911, 59912, 59913,
                     59914],
                    dtype='int64', length=198),
         135: Int64Index([41312, 41313, 41314, 41315, 41316, 41317, 41318, 41319, 41320,
                     41321,
                     ...
                     41561, 41562, 41563, 41564, 41565, 41566, 41567, 41568, 41569,
                     41570],
                    dtype='int64', length=259),
         136: Int64Index([75369, 75370, 75371, 75372, 75373, 75374, 75375, 75376, 75377,
                     75378,
                     ...
                     75464, 75465, 75466, 75467, 75468, 75469, 75470, 75471, 75472,
                     75473],
                    dtype='int64', length=105),
         137: Int64Index([66135, 66136, 66137, 66138, 66139, 66140, 66141, 66142, 66143,
                     66144,
                     ...
                     66296, 66297, 66298, 66299, 66300, 66301, 66302, 66303, 66304,
                     66305],
                    dtype='int64', length=171),
         138: Int64Index([77971, 77972, 77973, 77974, 77975, 77976, 77977, 77978, 77979,
                     77980, 77981, 77982, 77983, 77984, 77985, 77986, 77987, 77988,
                     77989],
                    dtype='int64'),
         139: Int64Index([81905, 81906, 81907, 81908, 81909, 81910, 81911, 81912, 81913,
                     81914, 81915, 81916, 81917, 81918, 81919, 81920, 81921, 81922,
                     81923, 81924, 81925, 81926, 81927, 81928, 81929, 81930, 81931,
                     81932, 81933, 81934, 81935, 81936, 81937, 81938, 81939, 81940,
                     81941, 81942, 81943, 81944, 81945, 81946, 81947, 81948, 81949,
                     81950, 81951, 81952, 81953, 81954],
                    dtype='int64'),
         140: Int64Index([83852, 83853, 83854, 83855, 83856, 83857, 83858, 83859, 83860,
                     83861, 83862, 83863, 83864, 83865, 83866, 83867, 83868, 83869,
                     83870, 83871, 83872, 83873, 83874, 83875, 83876, 83877, 83878,
                     83879, 83880, 83881, 83882, 83883, 83884, 83885, 83886, 83887,
                     83888, 83889, 83890, 83891, 83892, 83893, 83894, 83895, 83896,
                     83897, 83898, 83899, 83900, 83901, 83902, 83903, 83904, 83905,
                     83906, 83907, 83908, 83909, 83910, 83911, 83912],
                    dtype='int64'),
         141: Int64Index([84424, 84425, 84426, 84427, 84428, 84429, 84430, 84431, 84432,
                     84433, 84434, 84435, 84436, 84437, 84438, 84439, 84440, 84441,
                     84442, 84443, 84444, 84445, 84446, 84447, 84448, 84449, 84450,
                     84451, 84452, 84453, 84454, 84455, 84456, 84457, 84458, 84459,
                     84460, 84461, 84462, 84463, 84464, 84465, 84466, 84467, 84468,
                     84469, 84470, 84471, 84472, 84473, 84474, 84475, 84476, 84477,
                     84478, 84479, 84480, 84481, 84482, 84483, 84484, 84485, 84486,
                     84487, 84488, 84489, 84490, 84491, 84492, 84493, 84494, 84495],
                    dtype='int64'),
         142: Int64Index([80072, 80073, 80074, 80075, 80076, 80077, 80078, 80079, 80080,
                     80081, 80082, 80083, 80084, 80085, 80086, 80087, 80088, 80089,
                     80090, 80091, 80092, 80093, 80094, 80095, 80096, 80097, 80098,
                     80099, 80100, 80101, 80102, 80103, 80104, 80105, 80106, 80107,
                     80108, 80109, 80110, 80111, 80112, 80113, 80114, 80115, 80116,
                     80117, 80118, 80119, 80120, 80121, 80122, 80123, 80124, 80125,
                     80126, 80127, 80128],
                    dtype='int64'),
         143: Int64Index([60912, 60913, 60914, 60915, 60916, 60917, 60918, 60919, 60920,
                     60921,
                     ...
                     61124, 61125, 61126, 61127, 61128, 61129, 61130, 61131, 61132,
                     61133],
                    dtype='int64', length=222),
         144: Int64Index([30479, 30480, 30481, 30482, 30483, 30484, 30485, 30486, 30487,
                     30488,
                     ...
                     30712, 30713, 30714, 30715, 30716, 30717, 30718, 30719, 30720,
                     30721],
                    dtype='int64', length=243),
         145: Int64Index([44078, 44079, 44080, 44081, 44082, 44083, 44084, 44085, 44086,
                     44087, 44088, 44089, 44090, 44091, 44092, 44093, 44094, 44095,
                     44096, 44097, 44098, 44099, 44100, 44101, 44102, 44103, 44104,
                     44105, 44106, 44107, 44108, 44109, 44110, 44111, 44112, 44113,
                     44114, 44115, 44116, 44117, 44118, 44119, 44120, 44121, 44122,
                     44123, 44124, 44125, 44126, 44127, 44128, 44129, 44130, 44131,
                     44132, 44133, 44134, 44135, 44136, 44137, 44138, 44139, 44140,
                     44141, 44142],
                    dtype='int64'),
         146: Int64Index([96634, 96635, 96636, 96637, 96638, 96639, 96640, 96641, 96642,
                     96643],
                    dtype='int64'),
         147: Int64Index([20147, 20148, 20149, 20150, 20151, 20152, 20153, 20154, 20155,
                     20156,
                     ...
                     20322, 20323, 20324, 20325, 20326, 20327, 20328, 20329, 20330,
                     20331],
                    dtype='int64', length=185),
         148: Int64Index([7058, 7059, 7060, 7061, 7062, 7063, 7064, 7065, 7066, 7067,
                     ...
                     7176, 7177, 7178, 7179, 7180, 7181, 7182, 7183, 7184, 7185],
                    dtype='int64', length=128),
         149: Int64Index([85571, 85572, 85573, 85574, 85575, 85576, 85577, 85578, 85579,
                     85580, 85581, 85582, 85583, 85584, 85585, 85586, 85587, 85588,
                     85589, 85590, 85591, 85592, 85593],
                    dtype='int64'),
         150: Int64Index([89018, 89019, 89020, 89021, 89022, 89023, 89024, 89025, 89026,
                     89027,
                     ...
                     89165, 89166, 89167, 89168, 89169, 89170, 89171, 89172, 89173,
                     89174],
                    dtype='int64', length=157),
         151: Int64Index([42477, 42478, 42479, 42480, 42481, 42482, 42483, 42484, 42485,
                     42486,
                     ...
                     42793, 42794, 42795, 42796, 42797, 42798, 42799, 42800, 42801,
                     42802],
                    dtype='int64', length=326),
         152: Int64Index([56877, 56878, 56879, 56880, 56881, 56882, 56883, 56884, 56885,
                     56886, 56887, 56888, 56889, 56890, 56891, 56892, 56893, 56894,
                     56895, 56896, 56897, 56898, 56899, 56900, 56901, 56902, 56903,
                     56904, 56905, 56906, 56907, 56908, 56909, 56910, 56911, 56912,
                     56913, 56914, 56915, 56916, 56917, 56918, 56919, 56920, 56921,
                     56922, 56923, 56924, 56925, 56926, 56927, 56928, 56929, 56930,
                     56931, 56932, 56933, 56934, 56935, 56936, 56937, 56938, 56939,
                     56940, 56941, 56942, 56943, 56944, 56945, 56946, 56947, 56948,
                     56949, 56950, 56951, 56952, 56953, 56954, 56955, 56956, 56957,
                     56958],
                    dtype='int64'),
         153: Int64Index([4961, 4962, 4963, 4964, 4965, 4966, 4967, 4968, 4969, 4970,
                     ...
                     5198, 5199, 5200, 5201, 5202, 5203, 5204, 5205, 5206, 5207],
                    dtype='int64', length=247),
         154: Int64Index([24825, 24826, 24827, 24828, 24829, 24830, 24831, 24832, 24833,
                     24834,
                     ...
                     24989, 24990, 24991, 24992, 24993, 24994, 24995, 24996, 24997,
                     24998],
                    dtype='int64', length=174),
         155: Int64Index([36587, 36588, 36589, 36590, 36591, 36592, 36593, 36594, 36595,
                     36596, 36597, 36598, 36599, 36600, 36601, 36602, 36603, 36604,
                     36605, 36606, 36607, 36608, 36609, 36610, 36611, 36612, 36613,
                     36614, 36615, 36616, 36617, 36618, 36619, 36620, 36621, 36622,
                     36623, 36624, 36625, 36626, 36627, 36628, 36629, 36630, 36631,
                     36632, 36633, 36634, 36635, 36636, 36637, 36638, 36639, 36640,
                     36641, 36642, 36643, 36644, 36645, 36646, 36647, 36648, 36649,
                     36650, 36651, 36652, 36653, 36654, 36655, 36656, 36657, 36658,
                     36659, 36660, 36661, 36662, 36663, 36664, 36665, 36666, 36667,
                     36668, 36669, 36670, 36671, 36672, 36673, 36674, 36675, 36676,
                     36677, 36678, 36679, 36680, 36681, 36682, 36683, 36684],
                    dtype='int64'),
         156: Int64Index([47501, 47502, 47503, 47504, 47505, 47506, 47507, 47508, 47509,
                     47510,
                     ...
                     47639, 47640, 47641, 47642, 47643, 47644, 47645, 47646, 47647,
                     47648],
                    dtype='int64', length=148),
         157: Int64Index([37691, 37692, 37693, 37694, 37695, 37696, 37697, 37698, 37699,
                     37700,
                     ...
                     37808, 37809, 37810, 37811, 37812, 37813, 37814, 37815, 37816,
                     37817],
                    dtype='int64', length=127),
         158: Int64Index([50741, 50742, 50743, 50744, 50745, 50746, 50747, 50748, 50749,
                     50750, 50751, 50752, 50753, 50754, 50755, 50756, 50757, 50758,
                     50759, 50760, 50761, 50762, 50763, 50764, 50765, 50766, 50767,
                     50768, 50769, 50770, 50771, 50772, 50773, 50774, 50775, 50776,
                     50777, 50778, 50779, 50780, 50781, 50782, 50783, 50784, 50785,
                     50786, 50787, 50788, 50789, 50790, 50791, 50792, 50793, 50794,
                     50795, 50796, 50797, 50798, 50799, 50800],
                    dtype='int64'),
         159: Int64Index([18361, 18362, 18363, 18364, 18365, 18366, 18367, 18368, 18369,
                     18370,
                     ...
                     18452, 18453, 18454, 18455, 18456, 18457, 18458, 18459, 18460,
                     18461],
                    dtype='int64', length=101),
         160: Int64Index([73609, 73610, 73611, 73612, 73613, 73614, 73615, 73616, 73617,
                     73618, 73619, 73620, 73621, 73622, 73623, 73624, 73625, 73626,
                     73627, 73628, 73629, 73630, 73631, 73632, 73633, 73634, 73635,
                     73636, 73637, 73638, 73639, 73640, 73641, 73642, 73643, 73644,
                     73645, 73646, 73647, 73648, 73649, 73650, 73651, 73652, 73653,
                     73654, 73655, 73656, 73657, 73658, 73659, 73660, 73661, 73662,
                     73663, 73664, 73665, 73666, 73667, 73668, 73669, 73670, 73671,
                     73672, 73673, 73674, 73675, 73676, 73677],
                    dtype='int64'),
         161: Int64Index([30853, 30854, 30855, 30856, 30857, 30858, 30859, 30860, 30861,
                     30862,
                     ...
                     31063, 31064, 31065, 31066, 31067, 31068, 31069, 31070, 31071,
                     31072],
                    dtype='int64', length=220),
         162: Int64Index([46690, 46691, 46692, 46693, 46694, 46695, 46696, 46697, 46698,
                     46699,
                     ...
                     46786, 46787, 46788, 46789, 46790, 46791, 46792, 46793, 46794,
                     46795],
                    dtype='int64', length=106),
         163: Int64Index([29303, 29304, 29305, 29306, 29307, 29308, 29309, 29310, 29311,
                     29312, 29313, 29314, 29315, 29316, 29317, 29318, 29319, 29320,
                     29321, 29322, 29323, 29324, 29325, 29326, 29327, 29328, 29329,
                     29330, 29331, 29332, 29333, 29334, 29335, 29336, 29337, 29338,
                     29339, 29340, 29341, 29342, 29343, 29344, 29345, 29346, 29347,
                     29348, 29349, 29350, 29351, 29352, 29353, 29354, 29355, 29356,
                     29357, 29358, 29359, 29360, 29361, 29362, 29363, 29364, 29365,
                     29366, 29367, 29368, 29369, 29370, 29371, 29372, 29373, 29374,
                     29375, 29376, 29377, 29378, 29379, 29380, 29381, 29382, 29383,
                     29384, 29385, 29386, 29387, 29388, 29389, 29390, 29391, 29392,
                     29393, 29394],
                    dtype='int64'),
         164: Int64Index([40268, 40269, 40270, 40271, 40272, 40273, 40274, 40275, 40276,
                     40277,
                     ...
                     40409, 40410, 40411, 40412, 40413, 40414, 40415, 40416, 40417,
                     40418],
                    dtype='int64', length=151),
         165: Int64Index([72864, 72865, 72866, 72867, 72868, 72869, 72870, 72871, 72872,
                     72873, 72874, 72875, 72876, 72877, 72878, 72879, 72880, 72881,
                     72882, 72883, 72884, 72885, 72886, 72887, 72888, 72889, 72890,
                     72891, 72892, 72893, 72894, 72895, 72896, 72897, 72898, 72899,
                     72900, 72901, 72902, 72903, 72904, 72905, 72906, 72907, 72908,
                     72909, 72910, 72911, 72912, 72913, 72914, 72915, 72916, 72917,
                     72918, 72919, 72920, 72921, 72922, 72923, 72924, 72925, 72926,
                     72927],
                    dtype='int64'),
         166: Int64Index([73678, 73679, 73680, 73681, 73682, 73683, 73684, 73685, 73686,
                     73687, 73688, 73689, 73690, 73691, 73692, 73693, 73694, 73695,
                     73696, 73697, 73698, 73699, 73700, 73701, 73702, 73703, 73704,
                     73705, 73706, 73707, 73708, 73709, 73710, 73711, 73712, 73713,
                     73714, 73715, 73716, 73717, 73718, 73719, 73720, 73721, 73722,
                     73723, 73724, 73725, 73726, 73727, 73728, 73729, 73730, 73731,
                     73732, 73733, 73734, 73735],
                    dtype='int64'),
         167: Int64Index([27298, 27299, 27300, 27301, 27302, 27303, 27304, 27305, 27306,
                     27307, 27308, 27309, 27310, 27311, 27312, 27313, 27314, 27315,
                     27316, 27317, 27318, 27319, 27320, 27321, 27322, 27323, 27324,
                     27325, 27326, 27327, 27328, 27329, 27330, 27331, 27332, 27333,
                     27334, 27335, 27336, 27337, 27338, 27339, 27340, 27341, 27342,
                     27343, 27344, 27345, 27346, 27347, 27348, 27349, 27350, 27351,
                     27352, 27353, 27354, 27355, 27356, 27357, 27358, 27359, 27360,
                     27361, 27362, 27363, 27364],
                    dtype='int64'),
         168: Int64Index([25541, 25542, 25543, 25544, 25545, 25546, 25547, 25548, 25549,
                     25550,
                     ...
                     25847, 25848, 25849, 25850, 25851, 25852, 25853, 25854, 25855,
                     25856],
                    dtype='int64', length=316),
         169: Int64Index([49244, 49245, 49246, 49247, 49248, 49249, 49250, 49251, 49252,
                     49253,
                     ...
                     49352, 49353, 49354, 49355, 49356, 49357, 49358, 49359, 49360,
                     49361],
                    dtype='int64', length=118),
         170: Int64Index([72273, 72274, 72275, 72276, 72277, 72278, 72279, 72280, 72281,
                     72282,
                     ...
                     72384, 72385, 72386, 72387, 72388, 72389, 72390, 72391, 72392,
                     72393],
                    dtype='int64', length=121),
         171: Int64Index([52439, 52440, 52441, 52442, 52443, 52444, 52445, 52446, 52447,
                     52448, 52449, 52450, 52451, 52452, 52453, 52454, 52455, 52456,
                     52457, 52458, 52459, 52460, 52461, 52462, 52463, 52464, 52465,
                     52466, 52467, 52468, 52469, 52470, 52471, 52472, 52473, 52474,
                     52475, 52476, 52477, 52478, 52479, 52480, 52481, 52482, 52483,
                     52484, 52485, 52486, 52487, 52488, 52489, 52490, 52491, 52492,
                     52493, 52494, 52495, 52496, 52497, 52498, 52499, 52500, 52501,
                     52502, 52503],
                    dtype='int64'),
         172: Int64Index([24226, 24227, 24228, 24229, 24230, 24231, 24232, 24233, 24234,
                     24235,
                     ...
                     24583, 24584, 24585, 24586, 24587, 24588, 24589, 24590, 24591,
                     24592],
                    dtype='int64', length=367),
         173: Int64Index([5507, 5508, 5509, 5510, 5511, 5512, 5513, 5514, 5515, 5516,
                     ...
                     5821, 5822, 5823, 5824, 5825, 5826, 5827, 5828, 5829, 5830],
                    dtype='int64', length=324),
         174: Int64Index([34204, 34205, 34206, 34207, 34208, 34209, 34210, 34211, 34212,
                     34213,
                     ...
                     34614, 34615, 34616, 34617, 34618, 34619, 34620, 34621, 34622,
                     34623],
                    dtype='int64', length=420),
         175: Int64Index([28659, 28660, 28661, 28662, 28663, 28664, 28665, 28666, 28667,
                     28668,
                     ...
                     28857, 28858, 28859, 28860, 28861, 28862, 28863, 28864, 28865,
                     28866],
                    dtype='int64', length=208),
         176: Int64Index([22811, 22812, 22813, 22814, 22815, 22816, 22817, 22818, 22819,
                     22820,
                     ...
                     23085, 23086, 23087, 23088, 23089, 23090, 23091, 23092, 23093,
                     23094],
                    dtype='int64', length=284),
         177: Int64Index([19397, 19398, 19399, 19400, 19401, 19402, 19403, 19404, 19405,
                     19406,
                     ...
                     19524, 19525, 19526, 19527, 19528, 19529, 19530, 19531, 19532,
                     19533],
                    dtype='int64', length=137),
         178: Int64Index([58954, 58955, 58956, 58957, 58958, 58959, 58960, 58961, 58962,
                     58963,
                     ...
                     59069, 59070, 59071, 59072, 59073, 59074, 59075, 59076, 59077,
                     59078],
                    dtype='int64', length=125),
         179: Int64Index([38140, 38141, 38142, 38143, 38144, 38145, 38146, 38147, 38148,
                     38149,
                     ...
                     38351, 38352, 38353, 38354, 38355, 38356, 38357, 38358, 38359,
                     38360],
                    dtype='int64', length=221),
         180: Int64Index([39724, 39725, 39726, 39727, 39728, 39729, 39730, 39731, 39732,
                     39733,
                     ...
                     39935, 39936, 39937, 39938, 39939, 39940, 39941, 39942, 39943,
                     39944],
                    dtype='int64', length=221),
         181: Int64Index([29870, 29871, 29872, 29873, 29874, 29875, 29876, 29877, 29878,
                     29879,
                     ...
                     30367, 30368, 30369, 30370, 30371, 30372, 30373, 30374, 30375,
                     30376],
                    dtype='int64', length=507),
         182: Int64Index([68025, 68026, 68027, 68028, 68029, 68030, 68031, 68032, 68033,
                     68034,
                     ...
                     68241, 68242, 68243, 68244, 68245, 68246, 68247, 68248, 68249,
                     68250],
                    dtype='int64', length=226),
         183: Int64Index([35727, 35728, 35729, 35730, 35731, 35732, 35733, 35734, 35735,
                     35736,
                     ...
                     36008, 36009, 36010, 36011, 36012, 36013, 36014, 36015, 36016,
                     36017],
                    dtype='int64', length=291),
         184: Int64Index([28329, 28330, 28331, 28332, 28333, 28334, 28335, 28336, 28337,
                     28338,
                     ...
                     28435, 28436, 28437, 28438, 28439, 28440, 28441, 28442, 28443,
                     28444],
                    dtype='int64', length=116),
         185: Int64Index([58676, 58677, 58678, 58679, 58680, 58681, 58682, 58683, 58684,
                     58685,
                     ...
                     58905, 58906, 58907, 58908, 58909, 58910, 58911, 58912, 58913,
                     58914],
                    dtype='int64', length=239),
         186: Int64Index([21549, 21550, 21551, 21552, 21553, 21554, 21555, 21556, 21557,
                     21558,
                     ...
                     21790, 21791, 21792, 21793, 21794, 21795, 21796, 21797, 21798,
                     21799],
                    dtype='int64', length=251),
         187: Int64Index([26553, 26554, 26555, 26556, 26557, 26558, 26559, 26560, 26561,
                     26562,
                     ...
                     26752, 26753, 26754, 26755, 26756, 26757, 26758, 26759, 26760,
                     26761],
                    dtype='int64', length=209),
         188: Int64Index([53503, 53504, 53505, 53506, 53507, 53508, 53509, 53510, 53511,
                     53512,
                     ...
                     53663, 53664, 53665, 53666, 53667, 53668, 53669, 53670, 53671,
                     53672],
                    dtype='int64', length=170),
         189: Int64Index([69527, 69528, 69529, 69530, 69531, 69532, 69533, 69534, 69535,
                     69536, 69537, 69538, 69539, 69540, 69541, 69542, 69543, 69544,
                     69545, 69546, 69547, 69548, 69549, 69550, 69551, 69552, 69553,
                     69554, 69555, 69556, 69557, 69558, 69559, 69560, 69561, 69562,
                     69563, 69564, 69565, 69566, 69567, 69568, 69569, 69570, 69571,
                     69572, 69573, 69574, 69575, 69576, 69577, 69578, 69579, 69580,
                     69581, 69582, 69583, 69584, 69585, 69586, 69587, 69588, 69589,
                     69590, 69591, 69592],
                    dtype='int64'),
         190: Int64Index([68706, 68707, 68708, 68709, 68710, 68711, 68712, 68713, 68714,
                     68715,
                     ...
                     68820, 68821, 68822, 68823, 68824, 68825, 68826, 68827, 68828,
                     68829],
                    dtype='int64', length=124),
         191: Int64Index([39945, 39946, 39947, 39948, 39949, 39950, 39951, 39952, 39953,
                     39954,
                     ...
                     40211, 40212, 40213, 40214, 40215, 40216, 40217, 40218, 40219,
                     40220],
                    dtype='int64', length=276),
         192: Int64Index([66713, 66714, 66715, 66716, 66717, 66718, 66719, 66720, 66721,
                     66722,
                     ...
                     66819, 66820, 66821, 66822, 66823, 66824, 66825, 66826, 66827,
                     66828],
                    dtype='int64', length=116),
         193: Int64Index([53673, 53674, 53675, 53676, 53677, 53678, 53679, 53680, 53681,
                     53682,
                     ...
                     53820, 53821, 53822, 53823, 53824, 53825, 53826, 53827, 53828,
                     53829],
                    dtype='int64', length=157),
         194: Int64Index([24999, 25000, 25001, 25002, 25003, 25004, 25005, 25006, 25007,
                     25008,
                     ...
                     25230, 25231, 25232, 25233, 25234, 25235, 25236, 25237, 25238,
                     25239],
                    dtype='int64', length=241),
         195: Int64Index([25240, 25241, 25242, 25243, 25244, 25245, 25246, 25247, 25248,
                     25249,
                     ...
                     25531, 25532, 25533, 25534, 25535, 25536, 25537, 25538, 25539,
                     25540],
                    dtype='int64', length=301),
         196: Int64Index([40527, 40528, 40529, 40530, 40531, 40532, 40533, 40534, 40535,
                     40536,
                     ...
                     40768, 40769, 40770, 40771, 40772, 40773, 40774, 40775, 40776,
                     40777],
                    dtype='int64', length=251),
         197: Int64Index([48810, 48811, 48812, 48813, 48814, 48815, 48816, 48817, 48818,
                     48819,
                     ...
                     49039, 49040, 49041, 49042, 49043, 49044, 49045, 49046, 49047,
                     49048],
                    dtype='int64', length=239),
         198: Int64Index([67487, 67488, 67489, 67490, 67491, 67492, 67493, 67494, 67495,
                     67496,
                     ...
                     67604, 67605, 67606, 67607, 67608, 67609, 67610, 67611, 67612,
                     67613],
                    dtype='int64', length=127),
         199: Int64Index([62571, 62572, 62573, 62574, 62575, 62576, 62577, 62578, 62579,
                     62580,
                     ...
                     62726, 62727, 62728, 62729, 62730, 62731, 62732, 62733, 62734,
                     62735],
                    dtype='int64', length=165),
         200: Int64Index([45410, 45411, 45412, 45413, 45414, 45415, 45416, 45417, 45418,
                     45419,
                     ...
                     45606, 45607, 45608, 45609, 45610, 45611, 45612, 45613, 45614,
                     45615],
                    dtype='int64', length=206),
         201: Int64Index([29781, 29782, 29783, 29784, 29785, 29786, 29787, 29788, 29789,
                     29790, 29791, 29792, 29793, 29794, 29795, 29796, 29797, 29798,
                     29799, 29800, 29801, 29802, 29803, 29804, 29805, 29806, 29807,
                     29808, 29809, 29810, 29811, 29812, 29813, 29814, 29815, 29816,
                     29817, 29818, 29819, 29820, 29821, 29822, 29823, 29824, 29825,
                     29826, 29827, 29828, 29829, 29830, 29831, 29832, 29833, 29834,
                     29835, 29836, 29837, 29838, 29839, 29840, 29841, 29842, 29843,
                     29844, 29845, 29846, 29847, 29848, 29849, 29850, 29851, 29852,
                     29853, 29854, 29855, 29856, 29857, 29858, 29859, 29860, 29861,
                     29862, 29863, 29864, 29865, 29866, 29867, 29868, 29869],
                    dtype='int64'),
         202: Int64Index([3800, 3801, 3802, 3803, 3804, 3805, 3806, 3807, 3808, 3809,
                     ...
                     4070, 4071, 4072, 4073, 4074, 4075, 4076, 4077, 4078, 4079],
                    dtype='int64', length=280),
         203: Int64Index([16535, 16536, 16537, 16538, 16539, 16540, 16541, 16542, 16543,
                     16544,
                     ...
                     16707, 16708, 16709, 16710, 16711, 16712, 16713, 16714, 16715,
                     16716],
                    dtype='int64', length=182),
         204: Int64Index([25857, 25858, 25859, 25860, 25861, 25862, 25863, 25864, 25865,
                     25866,
                     ...
                     26197, 26198, 26199, 26200, 26201, 26202, 26203, 26204, 26205,
                     26206],
                    dtype='int64', length=350),
         205: Int64Index([60776, 60777, 60778, 60779, 60780, 60781, 60782, 60783, 60784,
                     60785,
                     ...
                     60902, 60903, 60904, 60905, 60906, 60907, 60908, 60909, 60910,
                     60911],
                    dtype='int64', length=136),
         206: Int64Index([91857, 91858, 91859, 91860, 91861, 91862, 91863, 91864, 91865,
                     91866, 91867, 91868, 91869, 91870, 91871, 91872, 91873, 91874,
                     91875, 91876, 91877, 91878, 91879, 91880, 91881, 91882, 91883,
                     91884, 91885, 91886, 91887, 91888, 91889, 91890, 91891, 91892,
                     91893, 91894, 91895, 91896, 91897, 91898, 91899, 91900, 91901,
                     91902, 91903, 91904, 91905, 91906],
                    dtype='int64'),
         207: Int64Index([71724, 71725, 71726, 71727, 71728, 71729, 71730, 71731, 71732,
                     71733, 71734, 71735, 71736, 71737, 71738, 71739, 71740, 71741,
                     71742, 71743, 71744, 71745, 71746, 71747, 71748, 71749, 71750,
                     71751, 71752, 71753, 71754, 71755, 71756, 71757, 71758, 71759,
                     71760, 71761, 71762, 71763, 71764, 71765, 71766, 71767, 71768,
                     71769, 71770, 71771, 71772, 71773, 71774, 71775, 71776, 71777,
                     71778, 71779, 71780, 71781, 71782, 71783, 71784, 71785, 71786,
                     71787, 71788, 71789],
                    dtype='int64'),
         208: Int64Index([24026, 24027, 24028, 24029, 24030, 24031, 24032, 24033, 24034,
                     24035,
                     ...
                     24216, 24217, 24218, 24219, 24220, 24221, 24222, 24223, 24224,
                     24225],
                    dtype='int64', length=200),
         209: Int64Index([33889, 33890, 33891, 33892, 33893, 33894, 33895, 33896, 33897,
                     33898,
                     ...
                     34070, 34071, 34072, 34073, 34074, 34075, 34076, 34077, 34078,
                     34079],
                    dtype='int64', length=191),
         210: Int64Index([31426, 31427, 31428, 31429, 31430, 31431, 31432, 31433, 31434,
                     31435,
                     ...
                     31747, 31748, 31749, 31750, 31751, 31752, 31753, 31754, 31755,
                     31756],
                    dtype='int64', length=331),
         211: Int64Index([28453, 28454, 28455, 28456, 28457, 28458, 28459, 28460, 28461,
                     28462,
                     ...
                     28649, 28650, 28651, 28652, 28653, 28654, 28655, 28656, 28657,
                     28658],
                    dtype='int64', length=206),
         212: Int64Index([70335, 70336, 70337, 70338, 70339, 70340, 70341, 70342, 70343,
                     70344, 70345, 70346, 70347, 70348, 70349, 70350, 70351, 70352,
                     70353, 70354, 70355, 70356, 70357, 70358, 70359, 70360, 70361,
                     70362, 70363, 70364, 70365, 70366, 70367, 70368, 70369, 70370,
                     70371, 70372, 70373, 70374, 70375, 70376, 70377, 70378, 70379,
                     70380, 70381, 70382, 70383, 70384, 70385, 70386, 70387, 70388,
                     70389, 70390, 70391, 70392, 70393, 70394, 70395, 70396, 70397,
                     70398, 70399, 70400, 70401, 70402, 70403, 70404, 70405, 70406,
                     70407, 70408, 70409, 70410, 70411, 70412, 70413, 70414, 70415,
                     70416, 70417, 70418, 70419, 70420, 70421, 70422, 70423, 70424,
                     70425, 70426],
                    dtype='int64'),
         213: Int64Index([58254, 58255, 58256, 58257, 58258, 58259, 58260, 58261, 58262,
                     58263,
                     ...
                     58378, 58379, 58380, 58381, 58382, 58383, 58384, 58385, 58386,
                     58387],
                    dtype='int64', length=134),
         214: Int64Index([51590, 51591, 51592, 51593, 51594, 51595, 51596, 51597, 51598,
                     51599,
                     ...
                     51694, 51695, 51696, 51697, 51698, 51699, 51700, 51701, 51702,
                     51703],
                    dtype='int64', length=114),
         215: Int64Index([46026, 46027, 46028, 46029, 46030, 46031, 46032, 46033, 46034,
                     46035,
                     ...
                     46228, 46229, 46230, 46231, 46232, 46233, 46234, 46235, 46236,
                     46237],
                    dtype='int64', length=212),
         216: Int64Index([28039, 28040, 28041, 28042, 28043, 28044, 28045, 28046, 28047,
                     28048,
                     ...
                     28319, 28320, 28321, 28322, 28323, 28324, 28325, 28326, 28327,
                     28328],
                    dtype='int64', length=290),
         217: Int64Index([41158, 41159, 41160, 41161, 41162, 41163, 41164, 41165, 41166,
                     41167,
                     ...
                     41268, 41269, 41270, 41271, 41272, 41273, 41274, 41275, 41276,
                     41277],
                    dtype='int64', length=120),
         218: Int64Index([66829, 66830, 66831, 66832, 66833, 66834, 66835, 66836, 66837,
                     66838,
                     ...
                     66990, 66991, 66992, 66993, 66994, 66995, 66996, 66997, 66998,
                     66999],
                    dtype='int64', length=171),
         219: Int64Index([84997, 84998, 84999, 85000, 85001, 85002, 85003, 85004, 85005,
                     85006,
                     ...
                     85098, 85099, 85100, 85101, 85102, 85103, 85104, 85105, 85106,
                     85107],
                    dtype='int64', length=111),
         220: Int64Index([37077, 37078, 37079, 37080, 37081, 37082, 37083, 37084, 37085,
                     37086, 37087, 37088, 37089, 37090, 37091, 37092, 37093, 37094,
                     37095, 37096, 37097, 37098, 37099, 37100, 37101, 37102, 37103,
                     37104, 37105, 37106, 37107, 37108, 37109, 37110, 37111, 37112,
                     37113, 37114, 37115, 37116, 37117, 37118, 37119, 37120, 37121,
                     37122, 37123, 37124, 37125, 37126, 37127, 37128, 37129, 37130,
                     37131, 37132, 37133, 37134, 37135, 37136, 37137, 37138, 37139,
                     37140, 37141, 37142],
                    dtype='int64'),
         221: Int64Index([74779, 74780, 74781, 74782, 74783, 74784, 74785, 74786, 74787,
                     74788, 74789, 74790, 74791, 74792, 74793, 74794, 74795, 74796,
                     74797, 74798, 74799, 74800, 74801, 74802, 74803, 74804, 74805,
                     74806, 74807, 74808, 74809, 74810, 74811, 74812, 74813, 74814,
                     74815, 74816, 74817, 74818, 74819, 74820, 74821, 74822, 74823,
                     74824, 74825, 74826, 74827, 74828, 74829, 74830, 74831, 74832,
                     74833, 74834, 74835, 74836, 74837, 74838, 74839, 74840, 74841,
                     74842, 74843, 74844, 74845, 74846, 74847, 74848, 74849, 74850,
                     74851, 74852],
                    dtype='int64'),
         222: Int64Index([23095, 23096, 23097, 23098, 23099, 23100, 23101, 23102, 23103,
                     23104,
                     ...
                     23450, 23451, 23452, 23453, 23454, 23455, 23456, 23457, 23458,
                     23459],
                    dtype='int64', length=365),
         223: Int64Index([72433, 72434, 72435, 72436, 72437, 72438, 72439, 72440, 72441,
                     72442,
                     ...
                     72559, 72560, 72561, 72562, 72563, 72564, 72565, 72566, 72567,
                     72568],
                    dtype='int64', length=136),
         224: Int64Index([81328, 81329, 81330, 81331, 81332, 81333, 81334, 81335, 81336,
                     81337, 81338, 81339, 81340, 81341, 81342, 81343, 81344, 81345,
                     81346, 81347, 81348, 81349, 81350, 81351, 81352, 81353, 81354,
                     81355, 81356, 81357, 81358, 81359, 81360, 81361, 81362, 81363,
                     81364, 81365, 81366, 81367, 81368, 81369, 81370, 81371],
                    dtype='int64'),
         225: Int64Index([11108, 11109, 11110, 11111, 11112, 11113, 11114, 11115, 11116,
                     11117,
                     ...
                     11207, 11208, 11209, 11210, 11211, 11212, 11213, 11214, 11215,
                     11216],
                    dtype='int64', length=109),
         226: Int64Index([12745, 12746, 12747, 12748, 12749, 12750, 12751, 12752, 12753,
                     12754,
                     ...
                     12901, 12902, 12903, 12904, 12905, 12906, 12907, 12908, 12909,
                     12910],
                    dtype='int64', length=166),
         227: Int64Index([21011, 21012, 21013, 21014, 21015, 21016, 21017, 21018, 21019,
                     21020,
                     ...
                     21162, 21163, 21164, 21165, 21166, 21167, 21168, 21169, 21170,
                     21171],
                    dtype='int64', length=161),
         228: Int64Index([32032, 32033, 32034, 32035, 32036, 32037, 32038, 32039, 32040,
                     32041,
                     ...
                     32266, 32267, 32268, 32269, 32270, 32271, 32272, 32273, 32274,
                     32275],
                    dtype='int64', length=244),
         229: Int64Index([29132, 29133, 29134, 29135, 29136, 29137, 29138, 29139, 29140,
                     29141,
                     ...
                     29293, 29294, 29295, 29296, 29297, 29298, 29299, 29300, 29301,
                     29302],
                    dtype='int64', length=171),
         230: Int64Index([24593, 24594, 24595, 24596, 24597, 24598, 24599, 24600, 24601,
                     24602,
                     ...
                     24782, 24783, 24784, 24785, 24786, 24787, 24788, 24789, 24790,
                     24791],
                    dtype='int64', length=199),
         231: Int64Index([27610, 27611, 27612, 27613, 27614, 27615, 27616, 27617, 27618,
                     27619,
                     ...
                     27742, 27743, 27744, 27745, 27746, 27747, 27748, 27749, 27750,
                     27751],
                    dtype='int64', length=142),
         232: Int64Index([38748, 38749, 38750, 38751, 38752, 38753, 38754, 38755, 38756,
                     38757,
                     ...
                     38839, 38840, 38841, 38842, 38843, 38844, 38845, 38846, 38847,
                     38848],
                    dtype='int64', length=101),
         233: Int64Index([34906, 34907, 34908, 34909, 34910, 34911, 34912, 34913, 34914,
                     34915,
                     ...
                     35020, 35021, 35022, 35023, 35024, 35025, 35026, 35027, 35028,
                     35029],
                    dtype='int64', length=124),
         234: Int64Index([51836, 51837, 51838, 51839, 51840, 51841, 51842, 51843, 51844,
                     51845,
                     ...
                     52106, 52107, 52108, 52109, 52110, 52111, 52112, 52113, 52114,
                     52115],
                    dtype='int64', length=280),
         235: Int64Index([49829, 49830, 49831, 49832, 49833, 49834, 49835, 49836, 49837,
                     49838,
                     ...
                     50036, 50037, 50038, 50039, 50040, 50041, 50042, 50043, 50044,
                     50045],
                    dtype='int64', length=217),
         236: Int64Index([89865, 89866, 89867, 89868, 89869, 89870, 89871, 89872, 89873,
                     89874, 89875, 89876, 89877, 89878, 89879, 89880, 89881, 89882,
                     89883, 89884, 89885, 89886, 89887, 89888, 89889, 89890, 89891,
                     89892, 89893, 89894, 89895, 89896, 89897, 89898, 89899, 89900,
                     89901, 89902, 89903, 89904, 89905, 89906, 89907, 89908, 89909],
                    dtype='int64'),
         237: Int64Index([9266, 9267, 9268, 9269, 9270, 9271, 9272, 9273, 9274, 9275,
                     ...
                     9640, 9641, 9642, 9643, 9644, 9645, 9646, 9647, 9648, 9649],
                    dtype='int64', length=384),
         238: Int64Index([ 881,  882,  883,  884,  885,  886,  887,  888,  889,  890,
                     ...
                     1127, 1128, 1129, 1130, 1131, 1132, 1133, 1134, 1135, 1136],
                    dtype='int64', length=256),
         239: Int64Index([70801, 70802, 70803, 70804, 70805, 70806, 70807, 70808, 70809,
                     70810,
                     ...
                     70941, 70942, 70943, 70944, 70945, 70946, 70947, 70948, 70949,
                     70950],
                    dtype='int64', length=150),
         240: Int64Index([39568, 39569, 39570, 39571, 39572, 39573, 39574, 39575, 39576,
                     39577,
                     ...
                     39714, 39715, 39716, 39717, 39718, 39719, 39720, 39721, 39722,
                     39723],
                    dtype='int64', length=156),
         241: Int64Index([20579, 20580, 20581, 20582, 20583, 20584, 20585, 20586, 20587,
                     20588,
                     ...
                     20697, 20698, 20699, 20700, 20701, 20702, 20703, 20704, 20705,
                     20706],
                    dtype='int64', length=128),
         242: Int64Index([  0,   1,   2,   3,   4,   5,   6,   7,   8,   9,
                     ...
                     107, 108, 109, 110, 111, 112, 113, 114, 115, 116],
                    dtype='int64', length=117),
         243: Int64Index([13761, 13762, 13763, 13764, 13765, 13766, 13767, 13768, 13769,
                     13770,
                     ...
                     13883, 13884, 13885, 13886, 13887, 13888, 13889, 13890, 13891,
                     13892],
                    dtype='int64', length=132),
         244: Int64Index([91318, 91319, 91320, 91321, 91322, 91323, 91324, 91325, 91326,
                     91327, 91328, 91329, 91330, 91331, 91332, 91333, 91334, 91335,
                     91336, 91337, 91338, 91339, 91340, 91341, 91342, 91343, 91344,
                     91345, 91346, 91347, 91348, 91349, 91350, 91351, 91352, 91353,
                     91354, 91355, 91356, 91357, 91358, 91359, 91360, 91361, 91362,
                     91363, 91364, 91365],
                    dtype='int64'),
         245: Int64Index([70511, 70512, 70513, 70514, 70515, 70516, 70517, 70518, 70519,
                     70520,
                     ...
                     70741, 70742, 70743, 70744, 70745, 70746, 70747, 70748, 70749,
                     70750],
                    dtype='int64', length=240),
         246: Int64Index([46796, 46797, 46798, 46799, 46800, 46801, 46802, 46803, 46804,
                     46805,
                     ...
                     46910, 46911, 46912, 46913, 46914, 46915, 46916, 46917, 46918,
                     46919],
                    dtype='int64', length=124),
         247: Int64Index([95392, 95393, 95394, 95395, 95396], dtype='int64'),
         248: Int64Index([75697, 75698, 75699, 75700, 75701, 75702, 75703, 75704, 75705,
                     75706,
                     ...
                     75847, 75848, 75849, 75850, 75851, 75852, 75853, 75854, 75855,
                     75856],
                    dtype='int64', length=160),
         249: Int64Index([51706, 51707, 51708, 51709, 51710, 51711, 51712, 51713, 51714,
                     51715,
                     ...
                     51826, 51827, 51828, 51829, 51830, 51831, 51832, 51833, 51834,
                     51835],
                    dtype='int64', length=130),
         250: Int64Index([6861, 6862, 6863, 6864, 6865, 6866, 6867, 6868, 6869, 6870,
                     ...
                     7048, 7049, 7050, 7051, 7052, 7053, 7054, 7055, 7056, 7057],
                    dtype='int64', length=197),
         251: Int64Index([409, 410, 411, 412, 413, 414, 415, 416, 417, 418, 419, 420, 421,
                     422, 423, 424, 425, 426, 427, 428, 429, 430, 431, 432, 433, 434,
                     435, 436, 437, 438, 439, 440, 441, 442, 443, 444, 445, 446, 447,
                     448, 449, 450, 451, 452, 453, 454],
                    dtype='int64'),
         252: Int64Index([56719, 56720, 56721, 56722, 56723, 56724, 56725, 56726, 56727,
                     56728,
                     ...
                     56867, 56868, 56869, 56870, 56871, 56872, 56873, 56874, 56875,
                     56876],
                    dtype='int64', length=158),
         253: Int64Index([95704, 95705, 95706, 95707, 95708, 95709, 95710, 95711, 95712,
                     95713, 95714, 95715, 95716, 95717, 95718, 95719, 95720, 95721,
                     95722, 95723, 95724, 95725, 95726, 95727, 95728, 95729],
                    dtype='int64'),
         254: Int64Index([94281, 94282, 94283, 94284, 94285, 94286, 94287, 94288, 94289,
                     94290, 94291, 94292, 94293, 94294, 94295, 94296, 94297, 94298,
                     94299, 94300, 94301, 94302, 94303, 94304, 94305, 94306, 94307,
                     94308, 94309, 94310, 94311, 94312, 94313, 94314, 94315, 94316,
                     94317, 94318, 94319, 94320, 94321, 94322, 94323, 94324, 94325,
                     94326, 94327, 94328, 94329, 94330, 94331, 94332, 94333, 94334,
                     94335, 94336, 94337, 94338, 94339, 94340, 94341, 94342],
                    dtype='int64'),
         255: Int64Index([43036, 43037, 43038, 43039, 43040, 43041, 43042, 43043, 43044,
                     43045,
                     ...
                     43198, 43199, 43200, 43201, 43202, 43203, 43204, 43205, 43206,
                     43207],
                    dtype='int64', length=172),
         256: Int64Index([96307, 96308, 96309, 96310, 96311, 96312, 96313, 96314, 96315,
                     96316, 96317, 96318, 96319, 96320, 96321, 96322],
                    dtype='int64'),
         257: Int64Index([3432, 3433, 3434, 3435, 3436, 3437, 3438, 3439, 3440, 3441,
                     ...
                     3725, 3726, 3727, 3728, 3729, 3730, 3731, 3732, 3733, 3734],
                    dtype='int64', length=303),
         258: Int64Index([17341, 17342, 17343, 17344, 17345, 17346, 17347, 17348, 17349,
                     17350,
                     ...
                     17840, 17841, 17842, 17843, 17844, 17845, 17846, 17847, 17848,
                     17849],
                    dtype='int64', length=509),
         259: Int64Index([67325, 67326, 67327, 67328, 67329, 67330, 67331, 67332, 67333,
                     67334,
                     ...
                     67477, 67478, 67479, 67480, 67481, 67482, 67483, 67484, 67485,
                     67486],
                    dtype='int64', length=162),
         260: Int64Index([87306, 87307, 87308, 87309, 87310, 87311, 87312, 87313, 87314,
                     87315,
                     ...
                     87423, 87424, 87425, 87426, 87427, 87428, 87429, 87430, 87431,
                     87432],
                    dtype='int64', length=127),
         261: Int64Index([57129, 57130, 57131, 57132, 57133, 57134, 57135, 57136, 57137,
                     57138, 57139, 57140, 57141, 57142, 57143, 57144, 57145, 57146,
                     57147, 57148, 57149, 57150, 57151, 57152, 57153, 57154, 57155,
                     57156, 57157, 57158, 57159, 57160, 57161, 57162, 57163, 57164,
                     57165, 57166, 57167, 57168, 57169, 57170, 57171],
                    dtype='int64'),
         262: Int64Index([86933, 86934, 86935, 86936, 86937, 86938, 86939, 86940, 86941,
                     86942, 86943, 86944, 86945, 86946, 86947, 86948, 86949, 86950,
                     86951, 86952, 86953, 86954, 86955, 86956, 86957, 86958, 86959,
                     86960, 86961, 86962, 86963, 86964, 86965, 86966, 86967, 86968,
                     86969, 86970, 86971, 86972, 86973, 86974, 86975, 86976, 86977,
                     86978, 86979, 86980, 86981, 86982, 86983, 86984, 86985, 86986,
                     86987, 86988, 86989, 86990, 86991, 86992, 86993, 86994, 86995,
                     86996, 86997, 86998],
                    dtype='int64'),
         263: Int64Index([7186, 7187, 7188, 7189, 7190, 7191, 7192, 7193, 7194, 7195, 7196,
                     7197, 7198, 7199, 7200, 7201, 7202, 7203, 7204],
                    dtype='int64'),
         264: Int64Index([88774, 88775, 88776, 88777, 88778, 88779, 88780, 88781, 88782,
                     88783,
                     ...
                     88865, 88866, 88867, 88868, 88869, 88870, 88871, 88872, 88873,
                     88874],
                    dtype='int64', length=101),
         265: Int64Index([34679, 34680, 34681, 34682, 34683, 34684, 34685, 34686, 34687,
                     34688,
                     ...
                     34896, 34897, 34898, 34899, 34900, 34901, 34902, 34903, 34904,
                     34905],
                    dtype='int64', length=227),
         266: Int64Index([96333, 96334, 96335, 96336, 96337, 96338, 96339, 96340, 96341,
                     96342, 96343, 96344, 96345, 96346, 96347, 96348, 96349, 96350,
                     96351, 96352, 96353, 96354, 96355, 96356, 96357, 96358, 96359,
                     96360, 96361, 96362, 96363, 96364, 96365, 96366, 96367],
                    dtype='int64'),
         267: Int64Index([99312, 99313, 99314, 99315, 99316, 99317, 99318, 99319, 99320], dtype='int64'),
         268: Int64Index([47649, 47650, 47651, 47652, 47653, 47654, 47655, 47656, 47657,
                     47658,
                     ...
                     47894, 47895, 47896, 47897, 47898, 47899, 47900, 47901, 47902,
                     47903],
                    dtype='int64', length=255),
         269: Int64Index([6039, 6040, 6041, 6042, 6043, 6044, 6045, 6046, 6047, 6048,
                     ...
                     6344, 6345, 6346, 6347, 6348, 6349, 6350, 6351, 6352, 6353],
                    dtype='int64', length=315),
         270: Int64Index([78385, 78386, 78387, 78388, 78389, 78390, 78391, 78392, 78393,
                     78394,
                     ...
                     78511, 78512, 78513, 78514, 78515, 78516, 78517, 78518, 78519,
                     78520],
                    dtype='int64', length=136),
         271: Int64Index([79328, 79329, 79330, 79331, 79332, 79333, 79334, 79335, 79336,
                     79337,
                     ...
                     79529, 79530, 79531, 79532, 79533, 79534, 79535, 79536, 79537,
                     79538],
                    dtype='int64', length=211),
         272: Int64Index([71184, 71185, 71186, 71187, 71188, 71189, 71190, 71191, 71192,
                     71193,
                     ...
                     71372, 71373, 71374, 71375, 71376, 71377, 71378, 71379, 71380,
                     71381],
                    dtype='int64', length=198),
         273: Int64Index([65539, 65540, 65541, 65542, 65543, 65544, 65545, 65546, 65547,
                     65548,
                     ...
                     65752, 65753, 65754, 65755, 65756, 65757, 65758, 65759, 65760,
                     65761],
                    dtype='int64', length=223),
         274: Int64Index([58486, 58487, 58488, 58489, 58490, 58491, 58492, 58493, 58494,
                     58495,
                     ...
                     58666, 58667, 58668, 58669, 58670, 58671, 58672, 58673, 58674,
                     58675],
                    dtype='int64', length=190),
         275: Int64Index([63291, 63292, 63293, 63294, 63295, 63296, 63297, 63298, 63299,
                     63300,
                     ...
                     63549, 63550, 63551, 63552, 63553, 63554, 63555, 63556, 63557,
                     63558],
                    dtype='int64', length=268),
         276: Int64Index([52504, 52505, 52506, 52507, 52508, 52509, 52510, 52511, 52512,
                     52513,
                     ...
                     52792, 52793, 52794, 52795, 52796, 52797, 52798, 52799, 52800,
                     52801],
                    dtype='int64', length=298),
         277: Int64Index([80267, 80268, 80269, 80270, 80271, 80272, 80273, 80274, 80275,
                     80276, 80277, 80278, 80279, 80280, 80281, 80282, 80283, 80284,
                     80285, 80286, 80287, 80288, 80289, 80290, 80291, 80292, 80293,
                     80294, 80295, 80296, 80297, 80298, 80299, 80300, 80301, 80302,
                     80303, 80304, 80305, 80306, 80307, 80308, 80309, 80310, 80311,
                     80312, 80313, 80314, 80315, 80316, 80317, 80318, 80319, 80320,
                     80321, 80322, 80323, 80324, 80325, 80326, 80327, 80328, 80329,
                     80330, 80331, 80332, 80333, 80334, 80335, 80336, 80337],
                    dtype='int64'),
         278: Int64Index([37818, 37819, 37820, 37821, 37822, 37823, 37824, 37825, 37826,
                     37827, 37828, 37829, 37830, 37831, 37832, 37833, 37834, 37835,
                     37836, 37837, 37838, 37839, 37840, 37841, 37842, 37843, 37844,
                     37845, 37846, 37847, 37848, 37849, 37850, 37851, 37852, 37853,
                     37854, 37855, 37856, 37857, 37858, 37859, 37860, 37861, 37862,
                     37863, 37864, 37865, 37866, 37867, 37868, 37869, 37870, 37871,
                     37872, 37873, 37874, 37875, 37876, 37877],
                    dtype='int64'),
         279: Int64Index([66475, 66476, 66477, 66478, 66479, 66480, 66481, 66482, 66483,
                     66484, 66485, 66486, 66487, 66488, 66489, 66490, 66491, 66492,
                     66493, 66494, 66495, 66496, 66497, 66498, 66499, 66500, 66501,
                     66502],
                    dtype='int64'),
         280: Int64Index([82591, 82592, 82593, 82594, 82595, 82596, 82597, 82598, 82599,
                     82600, 82601, 82602, 82603, 82604, 82605, 82606, 82607, 82608,
                     82609, 82610, 82611, 82612, 82613, 82614, 82615, 82616, 82617,
                     82618, 82619, 82620, 82621, 82622, 82623, 82624, 82625, 82626,
                     82627, 82628, 82629, 82630, 82631, 82632, 82633, 82634, 82635,
                     82636, 82637, 82638, 82639, 82640, 82641, 82642, 82643, 82644,
                     82645, 82646, 82647, 82648, 82649, 82650, 82651, 82652, 82653,
                     82654, 82655, 82656, 82657, 82658, 82659, 82660, 82661, 82662,
                     82663, 82664, 82665, 82666, 82667, 82668, 82669, 82670, 82671,
                     82672, 82673, 82674, 82675],
                    dtype='int64'),
         281: Int64Index([7328, 7329, 7330, 7331, 7332, 7333, 7334, 7335, 7336, 7337,
                     ...
                     7464, 7465, 7466, 7467, 7468, 7469, 7470, 7471, 7472, 7473],
                    dtype='int64', length=146),
         282: Int64Index([63854, 63855, 63856, 63857, 63858, 63859, 63860, 63861, 63862,
                     63863,
                     ...
                     64076, 64077, 64078, 64079, 64080, 64081, 64082, 64083, 64084,
                     64085],
                    dtype='int64', length=232),
         283: Int64Index([78936, 78937, 78938, 78939, 78940, 78941, 78942, 78943, 78944,
                     78945,
                     ...
                     79103, 79104, 79105, 79106, 79107, 79108, 79109, 79110, 79111,
                     79112],
                    dtype='int64', length=177),
         284: Int64Index([61653, 61654, 61655, 61656, 61657, 61658, 61659, 61660, 61661,
                     61662,
                     ...
                     61836, 61837, 61838, 61839, 61840, 61841, 61842, 61843, 61844,
                     61845],
                    dtype='int64', length=193),
         285: Int64Index([4583, 4584, 4585, 4586, 4587, 4588, 4589, 4590, 4591, 4592,
                     ...
                     4735, 4736, 4737, 4738, 4739, 4740, 4741, 4742, 4743, 4744],
                    dtype='int64', length=162),
         286: Int64Index([1850, 1851, 1852, 1853, 1854, 1855, 1856, 1857, 1858, 1859,
                     ...
                     2321, 2322, 2323, 2324, 2325, 2326, 2327, 2328, 2329, 2330],
                    dtype='int64', length=481),
         287: Int64Index([4269, 4270, 4271, 4272, 4273, 4274, 4275, 4276, 4277, 4278, 4279,
                     4280, 4281, 4282, 4283, 4284, 4285, 4286, 4287, 4288, 4289, 4290,
                     4291, 4292, 4293, 4294, 4295, 4296, 4297, 4298, 4299, 4300, 4301,
                     4302, 4303, 4304, 4305, 4306, 4307, 4308, 4309, 4310, 4311, 4312,
                     4313, 4314, 4315, 4316, 4317, 4318, 4319, 4320, 4321, 4322, 4323,
                     4324, 4325, 4326, 4327, 4328, 4329, 4330, 4331, 4332, 4333, 4334,
                     4335, 4336, 4337, 4338, 4339, 4340, 4341, 4342, 4343, 4344, 4345,
                     4346],
                    dtype='int64'),
         288: Int64Index([10630, 10631, 10632, 10633, 10634, 10635, 10636, 10637, 10638,
                     10639,
                     ...
                     11098, 11099, 11100, 11101, 11102, 11103, 11104, 11105, 11106,
                     11107],
                    dtype='int64', length=478),
         289: Int64Index([71465, 71466, 71467, 71468, 71469, 71470, 71471, 71472, 71473,
                     71474,
                     ...
                     71714, 71715, 71716, 71717, 71718, 71719, 71720, 71721, 71722,
                     71723],
                    dtype='int64', length=259),
         290: Int64Index([31237, 31238, 31239, 31240, 31241, 31242, 31243, 31244, 31245,
                     31246, 31247, 31248, 31249, 31250, 31251, 31252, 31253, 31254,
                     31255, 31256, 31257, 31258, 31259, 31260, 31261, 31262, 31263,
                     31264, 31265, 31266, 31267, 31268, 31269, 31270, 31271, 31272,
                     31273, 31274, 31275, 31276, 31277, 31278, 31279, 31280, 31281,
                     31282, 31283, 31284, 31285, 31286, 31287, 31288, 31289, 31290,
                     31291, 31292, 31293, 31294, 31295, 31296, 31297, 31298, 31299,
                     31300, 31301, 31302, 31303, 31304, 31305, 31306, 31307, 31308,
                     31309, 31310, 31311, 31312, 31313, 31314, 31315, 31316, 31317,
                     31318, 31319, 31320, 31321, 31322, 31323, 31324, 31325, 31326,
                     31327, 31328, 31329, 31330, 31331, 31332],
                    dtype='int64'),
         291: Int64Index([16733, 16734, 16735, 16736, 16737, 16738, 16739, 16740, 16741,
                     16742,
                     ...
                     16850, 16851, 16852, 16853, 16854, 16855, 16856, 16857, 16858,
                     16859],
                    dtype='int64', length=127),
         292: Int64Index([92212, 92213, 92214, 92215, 92216, 92217, 92218, 92219, 92220,
                     92221,
                     ...
                     92316, 92317, 92318, 92319, 92320, 92321, 92322, 92323, 92324,
                     92325],
                    dtype='int64', length=114),
         293: Int64Index([76289, 76290, 76291, 76292, 76293, 76294, 76295, 76296, 76297,
                     76298,
                     ...
                     76426, 76427, 76428, 76429, 76430, 76431, 76432, 76433, 76434,
                     76435],
                    dtype='int64', length=147),
         294: Int64Index([18878, 18879, 18880, 18881, 18882, 18883, 18884, 18885, 18886,
                     18887,
                     ...
                     19353, 19354, 19355, 19356, 19357, 19358, 19359, 19360, 19361,
                     19362],
                    dtype='int64', length=485),
         295: Int64Index([20332, 20333, 20334, 20335, 20336, 20337, 20338, 20339, 20340,
                     20341, 20342, 20343, 20344, 20345, 20346, 20347, 20348, 20349,
                     20350, 20351, 20352, 20353, 20354, 20355, 20356, 20357, 20358,
                     20359, 20360, 20361, 20362, 20363, 20364, 20365, 20366, 20367,
                     20368, 20369, 20370, 20371, 20372, 20373, 20374, 20375, 20376,
                     20377, 20378, 20379, 20380, 20381, 20382, 20383, 20384, 20385,
                     20386, 20387, 20388, 20389, 20390, 20391, 20392, 20393, 20394,
                     20395, 20396, 20397, 20398, 20399, 20400, 20401, 20402, 20403,
                     20404, 20405, 20406, 20407, 20408],
                    dtype='int64'),
         296: Int64Index([99534, 99535, 99536, 99537, 99538, 99539], dtype='int64'),
         297: Int64Index([74875, 74876, 74877, 74878, 74879, 74880, 74881, 74882, 74883,
                     74884, 74885, 74886, 74887, 74888, 74889, 74890, 74891, 74892,
                     74893, 74894, 74895, 74896, 74897, 74898, 74899, 74900, 74901,
                     74902, 74903, 74904, 74905, 74906, 74907, 74908, 74909, 74910,
                     74911, 74912, 74913, 74914, 74915, 74916, 74917, 74918, 74919,
                     74920, 74921, 74922, 74923, 74924],
                    dtype='int64'),
         298: Int64Index([17850, 17851, 17852, 17853, 17854, 17855, 17856, 17857, 17858,
                     17859,
                     ...
                     18034, 18035, 18036, 18037, 18038, 18039, 18040, 18041, 18042,
                     18043],
                    dtype='int64', length=194),
         299: Int64Index([13342, 13343, 13344, 13345, 13346, 13347, 13348, 13349, 13350,
                     13351, 13352, 13353, 13354, 13355, 13356, 13357, 13358, 13359,
                     13360, 13361, 13362, 13363, 13364, 13365, 13366, 13367, 13368,
                     13369, 13370, 13371, 13372, 13373, 13374, 13375, 13376, 13377,
                     13378, 13379, 13380, 13381, 13382, 13383, 13384, 13385, 13386,
                     13387, 13388, 13389, 13390, 13391, 13392, 13393, 13394, 13395,
                     13396, 13397, 13398, 13399, 13400, 13401, 13402, 13403, 13404,
                     13405, 13406, 13407, 13408, 13409, 13410, 13411, 13412, 13413,
                     13414],
                    dtype='int64'),
         300: Int64Index([12911, 12912, 12913, 12914, 12915, 12916, 12917, 12918, 12919,
                     12920,
                     ...
                     13332, 13333, 13334, 13335, 13336, 13337, 13338, 13339, 13340,
                     13341],
                    dtype='int64', length=431),
         301: Int64Index([43848, 43849, 43850, 43851, 43852, 43853, 43854, 43855, 43856,
                     43857,
                     ...
                     44068, 44069, 44070, 44071, 44072, 44073, 44074, 44075, 44076,
                     44077],
                    dtype='int64', length=230),
         302: Int64Index([6385, 6386, 6387, 6388, 6389, 6390, 6391, 6392, 6393, 6394,
                     ...
                     6672, 6673, 6674, 6675, 6676, 6677, 6678, 6679, 6680, 6681],
                    dtype='int64', length=297),
         303: Int64Index([15326, 15327, 15328, 15329, 15330, 15331, 15332, 15333, 15334,
                     15335,
                     ...
                     15450, 15451, 15452, 15453, 15454, 15455, 15456, 15457, 15458,
                     15459],
                    dtype='int64', length=134),
         304: Int64Index([75857, 75858, 75859, 75860, 75861, 75862, 75863, 75864, 75865,
                     75866,
                     ...
                     75996, 75997, 75998, 75999, 76000, 76001, 76002, 76003, 76004,
                     76005],
                    dtype='int64', length=149),
         305: Int64Index([70968, 70969, 70970, 70971, 70972, 70973, 70974, 70975, 70976,
                     70977, 70978, 70979, 70980, 70981, 70982, 70983, 70984, 70985,
                     70986, 70987, 70988, 70989, 70990, 70991, 70992, 70993, 70994,
                     70995, 70996, 70997, 70998, 70999, 71000, 71001, 71002, 71003,
                     71004, 71005, 71006, 71007, 71008, 71009, 71010, 71011, 71012,
                     71013, 71014, 71015, 71016, 71017, 71018, 71019, 71020, 71021,
                     71022, 71023, 71024, 71025, 71026, 71027, 71028, 71029, 71030,
                     71031, 71032, 71033, 71034, 71035, 71036, 71037, 71038, 71039,
                     71040, 71041, 71042, 71043, 71044, 71045, 71046, 71047, 71048,
                     71049, 71050, 71051, 71052, 71053, 71054],
                    dtype='int64'),
         306: Int64Index([785, 786, 787, 788, 789, 790, 791, 792, 793, 794, 795, 796, 797,
                     798, 799, 800, 801, 802, 803, 804, 805, 806, 807, 808, 809, 810,
                     811, 812, 813, 814, 815, 816, 817, 818, 819, 820, 821, 822, 823,
                     824, 825, 826, 827, 828, 829, 830, 831, 832, 833, 834, 835, 836,
                     837, 838, 839, 840, 841, 842, 843, 844, 845, 846, 847, 848, 849,
                     850, 851, 852, 853, 854, 855, 856, 857, 858, 859, 860, 861, 862,
                     863, 864, 865, 866, 867, 868, 869, 870, 871, 872, 873, 874, 875,
                     876, 877, 878, 879, 880],
                    dtype='int64'),
         307: Int64Index([93096, 93097, 93098, 93099, 93100, 93101, 93102, 93103, 93104,
                     93105,
                     ...
                     93274, 93275, 93276, 93277, 93278, 93279, 93280, 93281, 93282,
                     93283],
                    dtype='int64', length=188),
         308: Int64Index([77404, 77405, 77406, 77407, 77408, 77409, 77410, 77411, 77412,
                     77413, 77414, 77415, 77416, 77417, 77418, 77419, 77420, 77421,
                     77422, 77423, 77424, 77425, 77426, 77427, 77428, 77429, 77430,
                     77431, 77432, 77433],
                    dtype='int64'),
         309: Int64Index([77218, 77219, 77220, 77221, 77222, 77223, 77224, 77225, 77226,
                     77227, 77228, 77229, 77230, 77231, 77232, 77233, 77234, 77235,
                     77236, 77237, 77238, 77239, 77240, 77241, 77242, 77243, 77244,
                     77245],
                    dtype='int64'),
         310: Int64Index([36018, 36019, 36020, 36021, 36022, 36023, 36024, 36025, 36026,
                     36027,
                     ...
                     36153, 36154, 36155, 36156, 36157, 36158, 36159, 36160, 36161,
                     36162],
                    dtype='int64', length=145),
         311: Int64Index([58113, 58114, 58115, 58116, 58117, 58118, 58119, 58120, 58121,
                     58122, 58123, 58124, 58125, 58126, 58127, 58128, 58129, 58130,
                     58131, 58132, 58133, 58134, 58135, 58136, 58137, 58138, 58139,
                     58140, 58141, 58142, 58143, 58144, 58145, 58146, 58147, 58148,
                     58149, 58150, 58151, 58152, 58153, 58154, 58155, 58156, 58157,
                     58158, 58159, 58160, 58161, 58162, 58163, 58164, 58165, 58166,
                     58167, 58168, 58169, 58170, 58171, 58172, 58173, 58174, 58175,
                     58176, 58177, 58178, 58179, 58180, 58181, 58182, 58183, 58184,
                     58185, 58186, 58187],
                    dtype='int64'),
         312: Int64Index([81801, 81802, 81803, 81804, 81805, 81806, 81807, 81808, 81809,
                     81810, 81811, 81812, 81813, 81814, 81815, 81816, 81817, 81818,
                     81819, 81820, 81821, 81822, 81823, 81824, 81825, 81826, 81827,
                     81828, 81829, 81830, 81831, 81832, 81833, 81834, 81835, 81836,
                     81837, 81838, 81839, 81840, 81841, 81842, 81843, 81844, 81845,
                     81846, 81847, 81848, 81849, 81850, 81851, 81852, 81853, 81854,
                     81855, 81856, 81857, 81858, 81859, 81860, 81861, 81862, 81863,
                     81864, 81865, 81866, 81867, 81868, 81869, 81870, 81871, 81872,
                     81873, 81874, 81875, 81876, 81877, 81878, 81879, 81880],
                    dtype='int64'),
         313: Int64Index([55864, 55865, 55866, 55867, 55868, 55869, 55870, 55871, 55872,
                     55873,
                     ...
                     56204, 56205, 56206, 56207, 56208, 56209, 56210, 56211, 56212,
                     56213],
                    dtype='int64', length=350),
         314: Int64Index([98541, 98542, 98543, 98544, 98545], dtype='int64'),
         315: Int64Index([56214, 56215, 56216, 56217, 56218, 56219, 56220, 56221, 56222,
                     56223,
                     ...
                     56364, 56365, 56366, 56367, 56368, 56369, 56370, 56371, 56372,
                     56373],
                    dtype='int64', length=160),
         316: Int64Index([81972, 81973, 81974, 81975, 81976, 81977, 81978, 81979, 81980,
                     81981,
                     ...
                     82074, 82075, 82076, 82077, 82078, 82079, 82080, 82081, 82082,
                     82083],
                    dtype='int64', length=112),
         317: Int64Index([49511, 49512, 49513, 49514, 49515, 49516, 49517, 49518, 49519,
                     49520,
                     ...
                     49603, 49604, 49605, 49606, 49607, 49608, 49609, 49610, 49611,
                     49612],
                    dtype='int64', length=102),
         318: Int64Index([47203, 47204, 47205, 47206, 47207, 47208, 47209, 47210, 47211,
                     47212,
                     ...
                     47491, 47492, 47493, 47494, 47495, 47496, 47497, 47498, 47499,
                     47500],
                    dtype='int64', length=298),
         319: Int64Index([89531, 89532, 89533, 89534, 89535, 89536, 89537, 89538, 89539,
                     89540,
                     ...
                     89689, 89690, 89691, 89692, 89693, 89694, 89695, 89696, 89697,
                     89698],
                    dtype='int64', length=168),
         320: Int64Index([98501, 98502, 98503, 98504, 98505, 98506, 98507, 98508, 98509,
                     98510, 98511, 98512, 98513, 98514, 98515, 98516, 98517, 98518,
                     98519, 98520],
                    dtype='int64'),
         321: Int64Index([76510, 76511, 76512, 76513, 76514, 76515, 76516, 76517, 76518,
                     76519,
                     ...
                     76669, 76670, 76671, 76672, 76673, 76674, 76675, 76676, 76677,
                     76678],
                    dtype='int64', length=169),
         322: Int64Index([8016, 8017, 8018, 8019, 8020, 8021, 8022, 8023, 8024, 8025,
                     ...
                     8224, 8225, 8226, 8227, 8228, 8229, 8230, 8231, 8232, 8233],
                    dtype='int64', length=218),
         323: Int64Index([54947, 54948, 54949, 54950, 54951, 54952, 54953, 54954, 54955,
                     54956,
                     ...
                     55177, 55178, 55179, 55180, 55181, 55182, 55183, 55184, 55185,
                     55186],
                    dtype='int64', length=240),
         324: Int64Index([38015, 38016, 38017, 38018, 38019, 38020, 38021, 38022, 38023,
                     38024,
                     ...
                     38130, 38131, 38132, 38133, 38134, 38135, 38136, 38137, 38138,
                     38139],
                    dtype='int64', length=125),
         325: Int64Index([80129, 80130, 80131, 80132, 80133, 80134, 80135, 80136, 80137,
                     80138,
                     ...
                     80247, 80248, 80249, 80250, 80251, 80252, 80253, 80254, 80255,
                     80256],
                    dtype='int64', length=128),
         326: Int64Index([73841, 73842, 73843, 73844, 73845, 73846, 73847, 73848, 73849,
                     73850,
                     ...
                     74006, 74007, 74008, 74009, 74010, 74011, 74012, 74013, 74014,
                     74015],
                    dtype='int64', length=175),
         327: Int64Index([10455, 10456, 10457, 10458, 10459, 10460, 10461, 10462, 10463,
                     10464,
                     ...
                     10620, 10621, 10622, 10623, 10624, 10625, 10626, 10627, 10628,
                     10629],
                    dtype='int64', length=175),
         328: Int64Index([54509, 54510, 54511, 54512, 54513, 54514, 54515, 54516, 54517,
                     54518,
                     ...
                     54794, 54795, 54796, 54797, 54798, 54799, 54800, 54801, 54802,
                     54803],
                    dtype='int64', length=295),
         329: Int64Index([80780, 80781, 80782, 80783, 80784, 80785, 80786, 80787, 80788,
                     80789, 80790, 80791, 80792, 80793, 80794, 80795, 80796, 80797,
                     80798, 80799, 80800, 80801, 80802, 80803, 80804, 80805, 80806,
                     80807, 80808, 80809, 80810, 80811, 80812, 80813, 80814, 80815,
                     80816, 80817, 80818, 80819, 80820, 80821, 80822, 80823, 80824],
                    dtype='int64'),
         330: Int64Index([18233, 18234, 18235, 18236, 18237, 18238, 18239, 18240, 18241,
                     18242, 18243, 18244, 18245, 18246, 18247, 18248, 18249, 18250,
                     18251, 18252, 18253, 18254, 18255, 18256, 18257, 18258, 18259,
                     18260, 18261, 18262, 18263, 18264, 18265, 18266, 18267, 18268,
                     18269, 18270, 18271, 18272, 18273],
                    dtype='int64'),
         331: Int64Index([19539, 19540, 19541, 19542, 19543, 19544, 19545, 19546, 19547,
                     19548,
                     ...
                     19642, 19643, 19644, 19645, 19646, 19647, 19648, 19649, 19650,
                     19651],
                    dtype='int64', length=113),
         332: Int64Index([15460, 15461, 15462, 15463, 15464, 15465, 15466, 15467, 15468,
                     15469,
                     ...
                     15593, 15594, 15595, 15596, 15597, 15598, 15599, 15600, 15601,
                     15602],
                    dtype='int64', length=143),
         333: Int64Index([8362, 8363, 8364, 8365, 8366, 8367, 8368, 8369, 8370, 8371,
                     ...
                     8603, 8604, 8605, 8606, 8607, 8608, 8609, 8610, 8611, 8612],
                    dtype='int64', length=251),
         334: Int64Index([88705, 88706, 88707, 88708, 88709, 88710, 88711, 88712, 88713,
                     88714, 88715, 88716, 88717, 88718, 88719, 88720, 88721, 88722,
                     88723, 88724, 88725, 88726, 88727, 88728, 88729, 88730, 88731,
                     88732, 88733, 88734, 88735, 88736, 88737, 88738, 88739, 88740,
                     88741, 88742, 88743, 88744, 88745, 88746, 88747, 88748, 88749,
                     88750, 88751, 88752, 88753, 88754, 88755, 88756, 88757, 88758,
                     88759, 88760, 88761, 88762, 88763, 88764, 88765, 88766, 88767,
                     88768],
                    dtype='int64'),
         335: Int64Index([96218, 96219, 96220, 96221, 96222, 96223, 96224, 96225, 96226,
                     96227, 96228, 96229, 96230, 96231, 96232, 96233, 96234, 96235,
                     96236, 96237, 96238],
                    dtype='int64'),
         336: Int64Index([81714, 81715, 81716, 81717, 81718, 81719, 81720, 81721, 81722,
                     81723, 81724, 81725, 81726, 81727, 81728, 81729, 81730, 81731,
                     81732, 81733, 81734, 81735, 81736, 81737, 81738, 81739, 81740,
                     81741, 81742, 81743, 81744, 81745, 81746, 81747, 81748, 81749,
                     81750, 81751, 81752, 81753, 81754, 81755, 81756],
                    dtype='int64'),
         337: Int64Index([96655, 96656, 96657, 96658, 96659, 96660, 96661, 96662, 96663,
                     96664, 96665, 96666, 96667, 96668, 96669, 96670, 96671, 96672],
                    dtype='int64'),
         338: Int64Index([12279, 12280, 12281, 12282, 12283, 12284, 12285, 12286, 12287,
                     12288, 12289, 12290, 12291, 12292, 12293, 12294, 12295, 12296,
                     12297, 12298, 12299, 12300, 12301, 12302, 12303, 12304, 12305,
                     12306, 12307, 12308, 12309, 12310, 12311, 12312, 12313, 12314,
                     12315, 12316, 12317, 12318, 12319, 12320, 12321, 12322, 12323,
                     12324, 12325, 12326, 12327, 12328, 12329, 12330, 12331, 12332,
                     12333, 12334, 12335, 12336, 12337, 12338, 12339, 12340, 12341,
                     12342, 12343, 12344, 12345, 12346, 12347, 12348, 12349, 12350,
                     12351, 12352, 12353, 12354, 12355, 12356, 12357, 12358, 12359,
                     12360, 12361, 12362, 12363, 12364, 12365, 12366, 12367, 12368,
                     12369],
                    dtype='int64'),
         339: Int64Index([81660, 81661, 81662, 81663, 81664, 81665, 81666, 81667, 81668,
                     81669, 81670, 81671, 81672, 81673, 81674, 81675, 81676, 81677,
                     81678, 81679, 81680, 81681, 81682, 81683, 81684, 81685, 81686,
                     81687, 81688, 81689, 81690, 81691, 81692, 81693, 81694, 81695,
                     81696, 81697, 81698, 81699, 81700, 81701, 81702, 81703, 81704,
                     81705, 81706],
                    dtype='int64'),
         340: Int64Index([4080, 4081, 4082, 4083, 4084, 4085, 4086, 4087, 4088, 4089,
                     ...
                     4259, 4260, 4261, 4262, 4263, 4264, 4265, 4266, 4267, 4268],
                    dtype='int64', length=189),
         341: Int64Index([79974, 79975, 79976, 79977, 79978, 79979, 79980, 79981, 79982,
                     79983, 79984],
                    dtype='int64'),
         342: Int64Index([98289, 98290, 98291, 98292, 98293, 98294, 98295, 98296, 98297,
                     98298, 98299, 98300, 98301, 98302, 98303, 98304, 98305, 98306,
                     98307, 98308, 98309, 98310, 98311, 98312, 98313, 98314, 98315,
                     98316, 98317, 98318, 98319, 98320, 98321, 98322, 98323, 98324,
                     98325, 98326, 98327, 98328, 98329, 98330, 98331, 98332, 98333,
                     98334, 98335, 98336, 98337, 98338, 98339, 98340],
                    dtype='int64'),
         343: Int64Index([54804, 54805, 54806, 54807, 54808, 54809, 54810, 54811, 54812,
                     54813,
                     ...
                     54918, 54919, 54920, 54921, 54922, 54923, 54924, 54925, 54926,
                     54927],
                    dtype='int64', length=124),
         344: Int64Index([97938, 97939, 97940, 97941, 97942, 97943, 97944, 97945, 97946,
                     97947, 97948, 97949, 97950, 97951, 97952, 97953, 97954, 97955,
                     97956, 97957, 97958, 97959, 97960, 97961, 97962, 97963, 97964,
                     97965, 97966, 97967, 97968, 97969, 97970, 97971, 97972, 97973,
                     97974, 97975, 97976, 97977, 97978, 97979, 97980, 97981, 97982,
                     97983, 97984, 97985, 97986, 97987, 97988, 97989, 97990, 97991,
                     97992],
                    dtype='int64'),
         345: Int64Index([82724, 82725, 82726, 82727, 82728, 82729, 82730, 82731, 82732,
                     82733, 82734, 82735, 82736, 82737, 82738, 82739, 82740, 82741,
                     82742, 82743, 82744, 82745, 82746, 82747, 82748, 82749, 82750,
                     82751, 82752, 82753, 82754, 82755, 82756, 82757, 82758, 82759,
                     82760, 82761, 82762, 82763, 82764, 82765, 82766, 82767, 82768,
                     82769, 82770, 82771, 82772, 82773, 82774, 82775, 82776, 82777,
                     82778, 82779, 82780, 82781, 82782, 82783, 82784, 82785, 82786,
                     82787, 82788],
                    dtype='int64'),
         346: Int64Index([54383, 54384, 54385, 54386, 54387, 54388, 54389, 54390, 54391,
                     54392,
                     ...
                     54499, 54500, 54501, 54502, 54503, 54504, 54505, 54506, 54507,
                     54508],
                    dtype='int64', length=126),
         347: Int64Index([55727, 55728, 55729, 55730, 55731, 55732, 55733, 55734, 55735,
                     55736,
                     ...
                     55854, 55855, 55856, 55857, 55858, 55859, 55860, 55861, 55862,
                     55863],
                    dtype='int64', length=137),
         348: Int64Index([82676, 82677, 82678, 82679, 82680, 82681, 82682, 82683, 82684,
                     82685, 82686, 82687, 82688, 82689, 82690, 82691, 82692, 82693,
                     82694, 82695, 82696, 82697, 82698, 82699, 82700, 82701, 82702],
                    dtype='int64'),
         349: Int64Index([86298, 86299, 86300, 86301, 86302, 86303, 86304, 86305, 86306,
                     86307, 86308, 86309, 86310, 86311, 86312, 86313, 86314, 86315,
                     86316, 86317, 86318, 86319, 86320, 86321, 86322, 86323, 86324,
                     86325, 86326, 86327, 86328],
                    dtype='int64'),
         350: Int64Index([95557, 95558, 95559, 95560, 95561, 95562, 95563, 95564, 95565,
                     95566, 95567, 95568, 95569, 95570, 95571, 95572, 95573, 95574,
                     95575, 95576, 95577, 95578, 95579, 95580, 95581, 95582, 95583,
                     95584, 95585, 95586, 95587, 95588, 95589, 95590, 95591, 95592,
                     95593, 95594, 95595, 95596, 95597],
                    dtype='int64'),
         351: Int64Index([98709, 98710, 98711, 98712, 98713, 98714, 98715, 98716, 98717,
                     98718, 98719, 98720, 98721, 98722, 98723, 98724, 98725, 98726,
                     98727, 98728],
                    dtype='int64'),
         352: Int64Index([99153, 99154, 99155, 99156, 99157, 99158, 99159, 99160, 99161,
                     99162, 99163, 99164, 99165, 99166, 99167, 99168, 99169, 99170,
                     99171, 99172, 99173, 99174, 99175, 99176, 99177, 99178],
                    dtype='int64'),
         353: Int64Index([98679, 98680, 98681, 98682, 98683, 98684, 98685, 98686, 98687,
                     98688, 98689, 98690, 98691, 98692],
                    dtype='int64'),
         354: Int64Index([80402, 80403, 80404, 80405, 80406, 80407, 80408, 80409, 80410,
                     80411, 80412, 80413, 80414, 80415, 80416, 80417, 80418, 80419,
                     80420, 80421, 80422, 80423, 80424, 80425, 80426, 80427, 80428,
                     80429, 80430, 80431, 80432, 80433, 80434, 80435, 80436, 80437,
                     80438, 80439, 80440, 80441, 80442, 80443, 80444, 80445, 80446,
                     80447, 80448, 80449, 80450, 80451, 80452, 80453, 80454, 80455,
                     80456, 80457, 80458, 80459, 80460, 80461, 80462, 80463, 80464,
                     80465, 80466, 80467, 80468, 80469, 80470, 80471, 80472, 80473],
                    dtype='int64'),
         355: Int64Index([97595, 97596, 97597, 97598, 97599, 97600, 97601, 97602, 97603,
                     97604, 97605, 97606, 97607, 97608, 97609, 97610, 97611, 97612,
                     97613, 97614, 97615, 97616, 97617, 97618, 97619, 97620, 97621,
                     97622, 97623, 97624, 97625, 97626, 97627, 97628, 97629, 97630,
                     97631, 97632, 97633, 97634, 97635],
                    dtype='int64'),
         356: Int64Index([16860, 16861, 16862, 16863, 16864, 16865, 16866, 16867, 16868,
                     16869, 16870, 16871, 16872, 16873, 16874, 16875, 16876, 16877,
                     16878, 16879, 16880, 16881, 16882, 16883, 16884, 16885, 16886,
                     16887, 16888, 16889, 16890, 16891, 16892, 16893, 16894, 16895,
                     16896, 16897, 16898, 16899, 16900, 16901, 16902, 16903, 16904,
                     16905, 16906, 16907, 16908, 16909, 16910, 16911, 16912, 16913,
                     16914, 16915, 16916, 16917, 16918, 16919, 16920, 16921, 16922,
                     16923, 16924, 16925, 16926, 16927, 16928, 16929, 16930, 16931,
                     16932, 16933, 16934, 16935, 16936, 16937, 16938, 16939, 16940,
                     16941, 16942, 16943, 16944, 16945, 16946, 16947, 16948, 16949,
                     16950, 16951, 16952, 16953, 16954, 16955, 16956],
                    dtype='int64'),
         357: Int64Index([48285, 48286, 48287, 48288, 48289, 48290, 48291, 48292, 48293,
                     48294,
                     ...
                     48539, 48540, 48541, 48542, 48543, 48544, 48545, 48546, 48547,
                     48548],
                    dtype='int64', length=264),
         358: Int64Index([23883, 23884, 23885, 23886, 23887, 23888, 23889, 23890, 23891,
                     23892,
                     ...
                     24016, 24017, 24018, 24019, 24020, 24021, 24022, 24023, 24024,
                     24025],
                    dtype='int64', length=143),
         359: Int64Index([96121, 96122, 96123, 96124, 96125, 96126, 96127, 96128, 96129,
                     96130, 96131, 96132, 96133, 96134, 96135, 96136, 96137, 96138],
                    dtype='int64'),
         360: Int64Index([96747, 96748, 96749, 96750, 96751, 96752, 96753, 96754, 96755,
                     96756],
                    dtype='int64'),
         361: Int64Index([98268, 98269, 98270, 98271, 98272, 98273, 98274, 98275, 98276,
                     98277],
                    dtype='int64'),
         362: Int64Index([98350, 98351, 98352, 98353, 98354, 98355, 98356, 98357, 98358,
                     98359, 98360, 98361, 98362, 98363, 98364, 98365, 98366, 98367,
                     98368, 98369, 98370, 98371, 98372, 98373, 98374, 98375, 98376,
                     98377],
                    dtype='int64'),
         363: Int64Index([83570, 83571, 83572, 83573, 83574, 83575, 83576, 83577, 83578,
                     83579, 83580, 83581, 83582, 83583, 83584, 83585, 83586, 83587,
                     83588, 83589, 83590, 83591, 83592, 83593, 83594, 83595, 83596,
                     83597, 83598, 83599, 83600, 83601, 83602, 83603, 83604, 83605,
                     83606, 83607, 83608, 83609, 83610, 83611, 83612, 83613, 83614,
                     83615, 83616],
                    dtype='int64'),
         364: Int64Index([87595, 87596, 87597, 87598, 87599, 87600, 87601, 87602, 87603,
                     87604, 87605, 87606, 87607, 87608, 87609, 87610, 87611, 87612,
                     87613, 87614, 87615, 87616, 87617, 87618, 87619, 87620, 87621,
                     87622, 87623, 87624, 87625, 87626, 87627, 87628, 87629, 87630,
                     87631],
                    dtype='int64'),
         365: Int64Index([42380, 42381, 42382, 42383, 42384, 42385, 42386, 42387, 42388,
                     42389, 42390, 42391, 42392, 42393, 42394, 42395, 42396, 42397,
                     42398, 42399, 42400, 42401, 42402, 42403, 42404, 42405, 42406,
                     42407, 42408, 42409, 42410, 42411, 42412, 42413, 42414, 42415,
                     42416, 42417, 42418, 42419, 42420, 42421, 42422, 42423, 42424,
                     42425, 42426, 42427],
                    dtype='int64'),
         366: Int64Index([86089, 86090, 86091, 86092, 86093, 86094, 86095, 86096, 86097,
                     86098, 86099, 86100, 86101, 86102, 86103, 86104, 86105, 86106,
                     86107, 86108, 86109, 86110, 86111, 86112, 86113, 86114, 86115,
                     86116, 86117, 86118, 86119, 86120, 86121, 86122, 86123, 86124,
                     86125, 86126, 86127, 86128, 86129, 86130, 86131, 86132, 86133,
                     86134, 86135],
                    dtype='int64'),
         367: Int64Index([27752, 27753, 27754, 27755, 27756, 27757, 27758, 27759, 27760,
                     27761,
                     ...
                     27912, 27913, 27914, 27915, 27916, 27917, 27918, 27919, 27920,
                     27921],
                    dtype='int64', length=170),
         368: Int64Index([90222, 90223, 90224, 90225, 90226, 90227, 90228, 90229, 90230,
                     90231, 90232, 90233, 90234, 90235, 90236, 90237, 90238, 90239,
                     90240, 90241, 90242, 90243, 90244, 90245, 90246, 90247, 90248,
                     90249, 90250, 90251, 90252],
                    dtype='int64'),
         369: Int64Index([37515, 37516, 37517, 37518, 37519, 37520, 37521, 37522, 37523,
                     37524, 37525, 37526, 37527, 37528, 37529, 37530, 37531, 37532,
                     37533, 37534, 37535, 37536, 37537, 37538, 37539, 37540, 37541,
                     37542, 37543, 37544, 37545, 37546, 37547, 37548, 37549, 37550,
                     37551, 37552, 37553, 37554, 37555, 37556, 37557, 37558, 37559,
                     37560, 37561, 37562, 37563, 37564, 37565, 37566, 37567, 37568,
                     37569],
                    dtype='int64'),
         370: Int64Index([97150, 97151, 97152, 97153, 97154, 97155, 97156, 97157, 97158,
                     97159, 97160, 97161, 97162, 97163, 97164, 97165, 97166, 97167,
                     97168, 97169, 97170, 97171, 97172, 97173, 97174, 97175, 97176,
                     97177, 97178, 97179, 97180, 97181, 97182, 97183, 97184, 97185,
                     97186, 97187, 97188],
                    dtype='int64'),
         371: Int64Index([90863, 90864, 90865, 90866, 90867, 90868, 90869, 90870, 90871,
                     90872, 90873, 90874, 90875, 90876, 90877, 90878, 90879, 90880,
                     90881, 90882, 90883, 90884, 90885, 90886, 90887, 90888, 90889,
                     90890, 90891, 90892, 90893, 90894, 90895, 90896, 90897, 90898,
                     90899, 90900, 90901, 90902, 90903, 90904, 90905, 90906, 90907,
                     90908, 90909, 90910, 90911, 90912, 90913, 90914, 90915, 90916,
                     90917, 90918, 90919, 90920, 90921, 90922, 90923, 90924, 90925,
                     90926, 90927, 90928, 90929],
                    dtype='int64'),
         372: Int64Index([82168, 82169, 82170, 82171, 82172, 82173, 82174, 82175, 82176,
                     82177, 82178, 82179, 82180, 82181, 82182, 82183, 82184, 82185,
                     82186, 82187, 82188, 82189, 82190, 82191, 82192, 82193, 82194,
                     82195, 82196, 82197, 82198, 82199, 82200, 82201],
                    dtype='int64'),
         373: Int64Index([83150, 83151, 83152, 83153, 83154, 83155, 83156, 83157, 83158,
                     83159, 83160, 83161, 83162, 83163, 83164, 83165, 83166, 83167,
                     83168, 83169, 83170, 83171, 83172, 83173, 83174, 83175, 83176,
                     83177, 83178, 83179, 83180, 83181, 83182, 83183, 83184, 83185,
                     83186, 83187, 83188],
                    dtype='int64'),
         374: Int64Index([99137, 99138, 99139, 99140, 99141, 99142, 99143, 99144, 99145,
                     99146, 99147],
                    dtype='int64'),
         375: Int64Index([89772, 89773, 89774, 89775, 89776, 89777, 89778, 89779, 89780,
                     89781, 89782, 89783, 89784, 89785, 89786, 89787, 89788, 89789,
                     89790, 89791, 89792, 89793, 89794],
                    dtype='int64'),
         376: Int64Index([20422, 20423, 20424, 20425, 20426, 20427, 20428, 20429, 20430,
                     20431, 20432, 20433, 20434, 20435, 20436, 20437, 20438, 20439,
                     20440, 20441, 20442, 20443, 20444, 20445],
                    dtype='int64'),
         377: Int64Index([20409, 20410, 20411, 20412, 20413, 20414, 20415, 20416, 20417,
                     20418, 20419, 20420, 20421],
                    dtype='int64'),
         378: Int64Index([84574, 84575, 84576, 84577, 84578, 84579, 84580, 84581, 84582,
                     84583,
                     ...
                     84665, 84666, 84667, 84668, 84669, 84670, 84671, 84672, 84673,
                     84674],
                    dtype='int64', length=101),
         379: Int64Index([79748, 79749, 79750, 79751, 79752, 79753, 79754, 79755, 79756,
                     79757, 79758, 79759, 79760, 79761, 79762, 79763, 79764, 79765,
                     79766, 79767, 79768, 79769, 79770, 79771, 79772, 79773, 79774,
                     79775, 79776, 79777, 79778, 79779, 79780, 79781, 79782, 79783,
                     79784, 79785, 79786, 79787, 79788, 79789, 79790],
                    dtype='int64'),
         380: Int64Index([36381, 36382, 36383, 36384, 36385, 36386, 36387, 36388, 36389,
                     36390,
                     ...
                     36487, 36488, 36489, 36490, 36491, 36492, 36493, 36494, 36495,
                     36496],
                    dtype='int64', length=116),
         381: Int64Index([309, 310, 311, 312, 313, 314, 315, 316, 317, 318, 319, 320, 321,
                     322, 323, 324, 325, 326, 327, 328, 329, 330, 331, 332, 333, 334,
                     335, 336, 337, 338, 339, 340, 341, 342, 343, 344, 345, 346, 347,
                     348, 349, 350, 351, 352, 353, 354, 355, 356, 357, 358, 359, 360,
                     361, 362, 363, 364, 365, 366, 367, 368, 369, 370, 371, 372, 373,
                     374, 375, 376, 377, 378, 379, 380, 381, 382, 383, 384, 385, 386,
                     387, 388, 389, 390, 391, 392, 393, 394, 395, 396, 397, 398, 399,
                     400, 401, 402, 403, 404, 405, 406, 407, 408],
                    dtype='int64'),
         382: Int64Index([4472, 4473, 4474, 4475, 4476, 4477, 4478, 4479, 4480, 4481,
                     ...
                     4573, 4574, 4575, 4576, 4577, 4578, 4579, 4580, 4581, 4582],
                    dtype='int64', length=111),
         383: Int64Index([53930, 53931, 53932, 53933, 53934, 53935, 53936, 53937, 53938,
                     53939, 53940, 53941, 53942, 53943, 53944, 53945, 53946, 53947,
                     53948, 53949, 53950, 53951, 53952, 53953, 53954, 53955, 53956,
                     53957, 53958, 53959, 53960],
                    dtype='int64'),
         384: Int64Index([31168, 31169, 31170, 31171, 31172, 31173, 31174, 31175, 31176,
                     31177, 31178, 31179, 31180, 31181, 31182, 31183, 31184, 31185,
                     31186, 31187, 31188, 31189, 31190, 31191, 31192, 31193, 31194,
                     31195, 31196, 31197, 31198, 31199, 31200, 31201, 31202, 31203,
                     31204, 31205, 31206, 31207, 31208, 31209, 31210, 31211, 31212,
                     31213, 31214, 31215, 31216, 31217, 31218, 31219, 31220, 31221,
                     31222, 31223, 31224, 31225, 31226, 31227, 31228, 31229, 31230,
                     31231, 31232, 31233, 31234, 31235, 31236],
                    dtype='int64'),
         385: Int64Index([7474, 7475, 7476, 7477, 7478, 7479, 7480, 7481, 7482, 7483,
                     ...
                     7672, 7673, 7674, 7675, 7676, 7677, 7678, 7679, 7680, 7681],
                    dtype='int64', length=208),
         386: Int64Index([23575, 23576, 23577, 23578, 23579, 23580, 23581, 23582, 23583,
                     23584, 23585, 23586, 23587, 23588, 23589, 23590, 23591, 23592,
                     23593, 23594, 23595, 23596, 23597, 23598, 23599, 23600, 23601,
                     23602, 23603, 23604, 23605, 23606, 23607, 23608, 23609, 23610,
                     23611, 23612, 23613, 23614, 23615, 23616, 23617, 23618, 23619,
                     23620, 23621, 23622, 23623, 23624, 23625, 23626, 23627, 23628,
                     23629, 23630, 23631, 23632, 23633, 23634, 23635, 23636, 23637,
                     23638, 23639, 23640, 23641, 23642, 23643, 23644, 23645, 23646,
                     23647, 23648, 23649, 23650, 23651, 23652, 23653, 23654, 23655,
                     23656, 23657, 23658, 23659, 23660, 23661],
                    dtype='int64'),
         387: Int64Index([79113, 79114, 79115, 79116, 79117, 79118, 79119, 79120, 79121,
                     79122, 79123, 79124, 79125, 79126, 79127, 79128, 79129, 79130,
                     79131, 79132, 79133, 79134, 79135, 79136, 79137, 79138, 79139,
                     79140, 79141, 79142, 79143, 79144, 79145, 79146, 79147, 79148,
                     79149, 79150, 79151, 79152, 79153, 79154, 79155, 79156, 79157,
                     79158, 79159, 79160, 79161, 79162, 79163, 79164, 79165, 79166,
                     79167, 79168, 79169, 79170, 79171, 79172, 79173, 79174, 79175,
                     79176, 79177],
                    dtype='int64'),
         388: Int64Index([89503, 89504, 89505, 89506, 89507, 89508, 89509, 89510, 89511,
                     89512, 89513, 89514, 89515, 89516, 89517, 89518, 89519, 89520,
                     89521, 89522, 89523, 89524, 89525, 89526, 89527, 89528, 89529,
                     89530],
                    dtype='int64'),
         389: Int64Index([93453, 93454, 93455, 93456, 93457, 93458, 93459, 93460, 93461,
                     93462, 93463, 93464, 93465, 93466, 93467, 93468, 93469, 93470,
                     93471, 93472, 93473, 93474, 93475, 93476, 93477, 93478, 93479],
                    dtype='int64'),
         390: Int64Index([81596, 81597, 81598, 81599, 81600, 81601, 81602, 81603, 81604,
                     81605],
                    dtype='int64'),
         391: Int64Index([83211, 83212, 83213, 83214, 83215, 83216, 83217, 83218, 83219,
                     83220, 83221, 83222, 83223, 83224, 83225, 83226, 83227, 83228,
                     83229, 83230, 83231, 83232, 83233, 83234, 83235, 83236, 83237,
                     83238, 83239, 83240, 83241, 83242, 83243, 83244, 83245, 83246,
                     83247, 83248, 83249, 83250, 83251, 83252, 83253, 83254, 83255,
                     83256, 83257, 83258, 83259, 83260, 83261, 83262, 83263, 83264,
                     83265, 83266, 83267, 83268, 83269],
                    dtype='int64'),
         392: Int64Index([84104, 84105, 84106, 84107, 84108, 84109, 84110, 84111, 84112,
                     84113, 84114, 84115, 84116, 84117, 84118, 84119, 84120, 84121,
                     84122, 84123, 84124, 84125, 84126, 84127, 84128, 84129, 84130,
                     84131, 84132, 84133, 84134, 84135, 84136, 84137, 84138, 84139,
                     84140, 84141, 84142, 84143, 84144, 84145, 84146, 84147, 84148,
                     84149, 84150, 84151, 84152, 84153, 84154, 84155, 84156, 84157,
                     84158, 84159, 84160, 84161, 84162, 84163, 84164, 84165, 84166,
                     84167, 84168, 84169, 84170, 84171],
                    dtype='int64'),
         393: Int64Index([117, 118, 119, 120, 121, 122, 123, 124, 125, 126,
                     ...
                     299, 300, 301, 302, 303, 304, 305, 306, 307, 308],
                    dtype='int64', length=192),
         394: Int64Index([81059, 81060, 81061, 81062, 81063, 81064, 81065, 81066, 81067,
                     81068, 81069, 81070],
                    dtype='int64'),
         395: Int64Index([89175, 89176, 89177, 89178, 89179, 89180, 89181, 89182, 89183,
                     89184, 89185, 89186, 89187, 89188, 89189, 89190, 89191, 89192,
                     89193, 89194, 89195, 89196, 89197, 89198, 89199, 89200, 89201,
                     89202, 89203, 89204, 89205, 89206, 89207, 89208, 89209, 89210,
                     89211, 89212, 89213, 89214, 89215, 89216, 89217, 89218, 89219,
                     89220, 89221, 89222, 89223, 89224, 89225, 89226, 89227, 89228,
                     89229, 89230],
                    dtype='int64'),
         396: Int64Index([81606, 81607, 81608, 81609, 81610, 81611, 81612, 81613, 81614,
                     81615, 81616, 81617, 81618, 81619, 81620, 81621, 81622, 81623,
                     81624, 81625, 81626, 81627, 81628, 81629, 81630, 81631, 81632,
                     81633, 81634, 81635, 81636, 81637, 81638, 81639, 81640, 81641,
                     81642, 81643, 81644, 81645, 81646, 81647, 81648, 81649, 81650,
                     81651, 81652, 81653, 81654, 81655, 81656, 81657, 81658, 81659],
                    dtype='int64'),
         397: Int64Index([86606, 86607, 86608, 86609, 86610, 86611, 86612, 86613, 86614,
                     86615, 86616, 86617],
                    dtype='int64'),
         398: Int64Index([87036, 87037, 87038, 87039, 87040, 87041, 87042, 87043, 87044,
                     87045, 87046, 87047, 87048, 87049, 87050, 87051, 87052, 87053,
                     87054, 87055, 87056, 87057, 87058, 87059, 87060, 87061],
                    dtype='int64'),
         399: Int64Index([21460, 21461, 21462, 21463, 21464, 21465, 21466, 21467, 21468,
                     21469, 21470, 21471, 21472, 21473, 21474, 21475, 21476, 21477,
                     21478, 21479, 21480, 21481, 21482, 21483, 21484, 21485, 21486,
                     21487, 21488, 21489, 21490, 21491, 21492, 21493, 21494, 21495,
                     21496, 21497, 21498, 21499, 21500, 21501, 21502, 21503, 21504,
                     21505, 21506, 21507, 21508, 21509, 21510, 21511, 21512, 21513,
                     21514, 21515, 21516, 21517, 21518, 21519, 21520, 21521, 21522,
                     21523, 21524, 21525, 21526, 21527, 21528, 21529, 21530, 21531,
                     21532, 21533, 21534, 21535, 21536, 21537, 21538, 21539, 21540,
                     21541, 21542, 21543, 21544, 21545, 21546, 21547, 21548],
                    dtype='int64'),
         400: Int64Index([95422, 95423, 95424, 95425, 95426, 95427, 95428, 95429, 95430,
                     95431, 95432, 95433, 95434, 95435, 95436, 95437, 95438, 95439],
                    dtype='int64'),
         401: Int64Index([48016, 48017, 48018, 48019, 48020, 48021, 48022, 48023, 48024,
                     48025, 48026, 48027, 48028, 48029, 48030, 48031, 48032, 48033,
                     48034, 48035, 48036, 48037, 48038, 48039, 48040, 48041, 48042,
                     48043, 48044, 48045, 48046, 48047, 48048, 48049, 48050, 48051,
                     48052, 48053, 48054, 48055, 48056, 48057, 48058, 48059, 48060,
                     48061, 48062, 48063, 48064, 48065, 48066, 48067, 48068, 48069,
                     48070, 48071, 48072, 48073, 48074, 48075, 48076, 48077, 48078,
                     48079, 48080, 48081, 48082, 48083, 48084, 48085, 48086, 48087,
                     48088, 48089, 48090, 48091],
                    dtype='int64'),
         402: Int64Index([63684, 63685, 63686, 63687, 63688, 63689, 63690, 63691, 63692,
                     63693,
                     ...
                     63844, 63845, 63846, 63847, 63848, 63849, 63850, 63851, 63852,
                     63853],
                    dtype='int64', length=170),
         403: Int64Index([22327, 22328, 22329, 22330, 22331, 22332, 22333, 22334, 22335,
                     22336,
                     ...
                     22518, 22519, 22520, 22521, 22522, 22523, 22524, 22525, 22526,
                     22527],
                    dtype='int64', length=201),
         404: Int64Index([80594, 80595, 80596, 80597, 80598, 80599, 80600, 80601, 80602,
                     80603,
                     ...
                     80685, 80686, 80687, 80688, 80689, 80690, 80691, 80692, 80693,
                     80694],
                    dtype='int64', length=101),
         405: Int64Index([19803, 19804, 19805, 19806, 19807, 19808, 19809, 19810, 19811,
                     19812,
                     ...
                     20137, 20138, 20139, 20140, 20141, 20142, 20143, 20144, 20145,
                     20146],
                    dtype='int64', length=344),
         406: Int64Index([7884, 7885, 7886, 7887, 7888, 7889, 7890, 7891, 7892, 7893, 7894,
                     7895, 7896, 7897, 7898, 7899, 7900, 7901, 7902, 7903, 7904, 7905,
                     7906, 7907, 7908, 7909, 7910, 7911, 7912, 7913, 7914, 7915, 7916,
                     7917, 7918, 7919, 7920, 7921, 7922, 7923, 7924, 7925, 7926, 7927,
                     7928, 7929, 7930, 7931, 7932],
                    dtype='int64'),
         407: Int64Index([23662, 23663, 23664, 23665, 23666, 23667, 23668, 23669, 23670,
                     23671, 23672, 23673, 23674, 23675, 23676, 23677, 23678, 23679,
                     23680, 23681, 23682, 23683, 23684, 23685, 23686, 23687, 23688,
                     23689, 23690, 23691, 23692, 23693, 23694, 23695, 23696, 23697,
                     23698, 23699, 23700, 23701, 23702, 23703, 23704],
                    dtype='int64'),
         408: Int64Index([73104, 73105, 73106, 73107, 73108, 73109, 73110, 73111, 73112,
                     73113,
                     ...
                     73206, 73207, 73208, 73209, 73210, 73211, 73212, 73213, 73214,
                     73215],
                    dtype='int64', length=112),
         409: Int64Index([36311, 36312, 36313, 36314, 36315, 36316, 36317, 36318, 36319,
                     36320, 36321, 36322, 36323, 36324, 36325, 36326, 36327, 36328,
                     36329, 36330, 36331, 36332, 36333, 36334, 36335, 36336, 36337,
                     36338, 36339, 36340, 36341, 36342, 36343, 36344, 36345, 36346,
                     36347, 36348, 36349, 36350, 36351, 36352, 36353, 36354, 36355,
                     36356, 36357, 36358, 36359, 36360, 36361, 36362, 36363, 36364,
                     36365, 36366, 36367, 36368, 36369, 36370, 36371, 36372, 36373,
                     36374, 36375, 36376, 36377, 36378, 36379, 36380],
                    dtype='int64'),
         410: Int64Index([44854, 44855, 44856, 44857, 44858, 44859, 44860, 44861, 44862,
                     44863,
                     ...
                     45006, 45007, 45008, 45009, 45010, 45011, 45012, 45013, 45014,
                     45015],
                    dtype='int64', length=162),
         411: Int64Index([4798, 4799, 4800, 4801, 4802, 4803, 4804, 4805, 4806, 4807,
                     ...
                     4951, 4952, 4953, 4954, 4955, 4956, 4957, 4958, 4959, 4960],
                    dtype='int64', length=163),
         412: Int64Index([90105, 90106, 90107, 90108, 90109, 90110, 90111, 90112, 90113,
                     90114, 90115, 90116, 90117, 90118, 90119, 90120, 90121, 90122,
                     90123, 90124, 90125, 90126, 90127, 90128, 90129, 90130, 90131,
                     90132, 90133, 90134, 90135, 90136, 90137, 90138, 90139, 90140,
                     90141, 90142, 90143, 90144, 90145, 90146, 90147, 90148, 90149,
                     90150, 90151, 90152, 90153, 90154, 90155, 90156, 90157, 90158,
                     90159, 90160, 90161, 90162, 90163, 90164, 90165, 90166, 90167,
                     90168, 90169, 90170, 90171, 90172, 90173, 90174, 90175, 90176,
                     90177, 90178, 90179, 90180, 90181, 90182, 90183, 90184, 90185,
                     90186, 90187, 90188, 90189, 90190, 90191, 90192, 90193, 90194,
                     90195, 90196, 90197],
                    dtype='int64'),
         413: Int64Index([82421, 82422, 82423, 82424, 82425, 82426, 82427, 82428, 82429,
                     82430, 82431, 82432, 82433, 82434, 82435, 82436, 82437, 82438,
                     82439, 82440, 82441, 82442, 82443, 82444, 82445, 82446, 82447,
                     82448, 82449, 82450, 82451, 82452, 82453, 82454, 82455, 82456,
                     82457, 82458, 82459, 82460, 82461, 82462, 82463, 82464, 82465,
                     82466, 82467, 82468, 82469, 82470, 82471, 82472, 82473, 82474,
                     82475],
                    dtype='int64'),
         414: Int64Index([90678, 90679, 90680, 90681, 90682, 90683, 90684, 90685, 90686,
                     90687, 90688, 90689, 90690, 90691, 90692, 90693, 90694, 90695,
                     90696, 90697, 90698, 90699, 90700, 90701, 90702, 90703, 90704,
                     90705, 90706, 90707, 90708, 90709, 90710, 90711, 90712, 90713,
                     90714, 90715, 90716, 90717, 90718, 90719, 90720, 90721, 90722,
                     90723, 90724, 90725, 90726, 90727, 90728, 90729, 90730, 90731,
                     90732, 90733, 90734, 90735, 90736, 90737, 90738, 90739],
                    dtype='int64'),
         415: Int64Index([95216, 95217, 95218, 95219, 95220, 95221, 95222, 95223, 95224,
                     95225, 95226, 95227, 95228, 95229, 95230, 95231, 95232, 95233,
                     95234, 95235, 95236, 95237, 95238, 95239, 95240],
                    dtype='int64'),
         416: Int64Index([87177, 87178, 87179, 87180, 87181, 87182, 87183, 87184, 87185,
                     87186, 87187, 87188, 87189, 87190, 87191, 87192, 87193, 87194,
                     87195, 87196, 87197, 87198, 87199, 87200, 87201, 87202, 87203,
                     87204, 87205, 87206, 87207, 87208, 87209, 87210, 87211, 87212,
                     87213, 87214, 87215, 87216, 87217, 87218, 87219, 87220, 87221,
                     87222, 87223, 87224, 87225, 87226, 87227, 87228, 87229, 87230,
                     87231, 87232, 87233, 87234, 87235, 87236, 87237, 87238, 87239,
                     87240],
                    dtype='int64'),
         417: Int64Index([81213, 81214, 81215, 81216, 81217, 81218, 81219, 81220, 81221,
                     81222, 81223, 81224, 81225, 81226, 81227, 81228, 81229, 81230,
                     81231, 81232, 81233, 81234, 81235, 81236, 81237, 81238, 81239,
                     81240, 81241, 81242, 81243, 81244, 81245, 81246, 81247, 81248,
                     81249, 81250, 81251, 81252, 81253, 81254, 81255, 81256, 81257,
                     81258, 81259, 81260, 81261, 81262, 81263, 81264, 81265, 81266,
                     81267, 81268, 81269, 81270, 81271, 81272, 81273, 81274, 81275,
                     81276, 81277, 81278, 81279, 81280, 81281, 81282, 81283, 81284,
                     81285],
                    dtype='int64'),
         418: Int64Index([57346, 57347, 57348, 57349, 57350, 57351, 57352, 57353, 57354,
                     57355,
                     ...
                     57465, 57466, 57467, 57468, 57469, 57470, 57471, 57472, 57473,
                     57474],
                    dtype='int64', length=129),
         419: Int64Index([61968, 61969, 61970, 61971, 61972, 61973, 61974, 61975, 61976,
                     61977,
                     ...
                     62136, 62137, 62138, 62139, 62140, 62141, 62142, 62143, 62144,
                     62145],
                    dtype='int64', length=178),
         420: Int64Index([83771, 83772, 83773, 83774, 83775, 83776, 83777, 83778, 83779,
                     83780, 83781, 83782, 83783, 83784, 83785, 83786, 83787, 83788,
                     83789, 83790, 83791, 83792, 83793, 83794, 83795, 83796, 83797,
                     83798, 83799, 83800, 83801, 83802, 83803, 83804, 83805, 83806,
                     83807, 83808, 83809, 83810, 83811, 83812, 83813, 83814, 83815,
                     83816, 83817, 83818, 83819, 83820, 83821, 83822, 83823, 83824,
                     83825, 83826, 83827, 83828, 83829, 83830, 83831, 83832, 83833,
                     83834, 83835, 83836, 83837, 83838, 83839, 83840, 83841, 83842,
                     83843, 83844, 83845, 83846, 83847, 83848, 83849, 83850, 83851],
                    dtype='int64'),
         421: Int64Index([78043, 78044, 78045, 78046, 78047, 78048, 78049, 78050, 78051,
                     78052,
                     ...
                     78139, 78140, 78141, 78142, 78143, 78144, 78145, 78146, 78147,
                     78148],
                    dtype='int64', length=106),
         422: Int64Index([95190, 95191, 95192, 95193, 95194, 95195, 95196, 95197, 95198,
                     95199, 95200, 95201, 95202, 95203, 95204, 95205, 95206, 95207,
                     95208, 95209, 95210, 95211, 95212, 95213, 95214, 95215],
                    dtype='int64'),
         423: Int64Index([61353, 61354, 61355, 61356, 61357, 61358, 61359, 61360, 61361,
                     61362,
                     ...
                     61643, 61644, 61645, 61646, 61647, 61648, 61649, 61650, 61651,
                     61652],
                    dtype='int64', length=300),
         424: Int64Index([95346, 95347, 95348, 95349, 95350, 95351, 95352, 95353, 95354,
                     95355, 95356, 95357, 95358, 95359, 95360, 95361, 95362, 95363,
                     95364],
                    dtype='int64'),
         425: Int64Index([69385, 69386, 69387, 69388, 69389, 69390, 69391, 69392, 69393,
                     69394, 69395, 69396, 69397, 69398, 69399, 69400, 69401, 69402,
                     69403, 69404, 69405, 69406, 69407, 69408, 69409, 69410, 69411,
                     69412, 69413, 69414, 69415, 69416, 69417, 69418, 69419, 69420,
                     69421, 69422, 69423, 69424, 69425, 69426, 69427, 69428, 69429,
                     69430, 69431, 69432, 69433, 69434, 69435, 69436, 69437, 69438,
                     69439, 69440, 69441, 69442, 69443, 69444, 69445, 69446, 69447,
                     69448, 69449, 69450, 69451, 69452, 69453, 69454, 69455, 69456,
                     69457, 69458, 69459, 69460, 69461, 69462, 69463, 69464, 69465,
                     69466, 69467, 69468, 69469],
                    dtype='int64'),
         426: Int64Index([86766, 86767, 86768, 86769, 86770, 86771, 86772, 86773, 86774,
                     86775, 86776, 86777, 86778, 86779, 86780, 86781, 86782, 86783,
                     86784, 86785, 86786, 86787, 86788, 86789, 86790, 86791, 86792,
                     86793, 86794, 86795, 86796, 86797],
                    dtype='int64'),
         427: Int64Index([62736, 62737, 62738, 62739, 62740, 62741, 62742, 62743, 62744,
                     62745,
                     ...
                     62945, 62946, 62947, 62948, 62949, 62950, 62951, 62952, 62953,
                     62954],
                    dtype='int64', length=219),
         428: Int64Index([2851, 2852, 2853, 2854, 2855, 2856, 2857, 2858, 2859, 2860,
                     ...
                     2962, 2963, 2964, 2965, 2966, 2967, 2968, 2969, 2970, 2971],
                    dtype='int64', length=121),
         429: Int64Index([84779, 84780, 84781, 84782, 84783, 84784, 84785, 84786, 84787,
                     84788, 84789, 84790, 84791, 84792, 84793, 84794, 84795, 84796,
                     84797, 84798, 84799, 84800, 84801, 84802, 84803, 84804, 84805,
                     84806, 84807, 84808, 84809, 84810, 84811, 84812, 84813, 84814,
                     84815, 84816, 84817, 84818, 84819, 84820, 84821, 84822, 84823,
                     84824, 84825, 84826, 84827, 84828, 84829, 84830, 84831, 84832,
                     84833, 84834, 84835, 84836, 84837, 84838, 84839, 84840, 84841,
                     84842, 84843, 84844, 84845, 84846, 84847, 84848, 84849, 84850,
                     84851, 84852, 84853, 84854, 84855, 84856, 84857, 84858, 84859,
                     84860, 84861, 84862, 84863, 84864, 84865, 84866, 84867, 84868,
                     84869, 84870, 84871, 84872, 84873, 84874, 84875],
                    dtype='int64'),
         430: Int64Index([31333, 31334, 31335, 31336, 31337, 31338, 31339, 31340, 31341,
                     31342, 31343, 31344, 31345, 31346, 31347, 31348, 31349, 31350,
                     31351, 31352, 31353, 31354, 31355, 31356, 31357, 31358, 31359,
                     31360, 31361, 31362, 31363, 31364, 31365, 31366, 31367, 31368,
                     31369, 31370, 31371, 31372, 31373, 31374, 31375, 31376, 31377,
                     31378, 31379, 31380, 31381, 31382, 31383, 31384, 31385, 31386,
                     31387, 31388, 31389, 31390, 31391, 31392, 31393, 31394, 31395,
                     31396, 31397, 31398, 31399, 31400, 31401, 31402, 31403, 31404,
                     31405, 31406, 31407, 31408, 31409, 31410, 31411, 31412, 31413,
                     31414, 31415, 31416, 31417, 31418, 31419, 31420, 31421, 31422,
                     31423, 31424, 31425],
                    dtype='int64'),
         431: Int64Index([27457, 27458, 27459, 27460, 27461, 27462, 27463, 27464, 27465,
                     27466,
                     ...
                     27600, 27601, 27602, 27603, 27604, 27605, 27606, 27607, 27608,
                     27609],
                    dtype='int64', length=153),
         432: Int64Index([57172, 57173, 57174, 57175, 57176, 57177, 57178, 57179, 57180,
                     57181,
                     ...
                     57336, 57337, 57338, 57339, 57340, 57341, 57342, 57343, 57344,
                     57345],
                    dtype='int64', length=174),
         433: Int64Index([21172, 21173, 21174, 21175, 21176, 21177, 21178, 21179, 21180,
                     21181,
                     ...
                     21333, 21334, 21335, 21336, 21337, 21338, 21339, 21340, 21341,
                     21342],
                    dtype='int64', length=171),
         434: Int64Index([92718, 92719, 92720, 92721, 92722, 92723, 92724, 92725, 92726,
                     92727, 92728, 92729, 92730, 92731, 92732, 92733, 92734, 92735,
                     92736, 92737, 92738, 92739, 92740, 92741, 92742, 92743, 92744,
                     92745, 92746, 92747, 92748, 92749, 92750, 92751, 92752, 92753,
                     92754, 92755, 92756, 92757, 92758, 92759, 92760, 92761, 92762,
                     92763, 92764, 92765, 92766, 92767, 92768, 92769, 92770, 92771,
                     92772, 92773, 92774, 92775, 92776, 92777, 92778, 92779, 92780,
                     92781, 92782, 92783, 92784],
                    dtype='int64'),
         435: Int64Index([22595, 22596, 22597, 22598, 22599, 22600, 22601, 22602, 22603,
                     22604,
                     ...
                     22801, 22802, 22803, 22804, 22805, 22806, 22807, 22808, 22809,
                     22810],
                    dtype='int64', length=216),
         436: Int64Index([78669, 78670, 78671, 78672, 78673, 78674, 78675, 78676, 78677,
                     78678, 78679, 78680, 78681, 78682, 78683, 78684, 78685, 78686,
                     78687, 78688, 78689, 78690, 78691, 78692, 78693, 78694, 78695,
                     78696, 78697, 78698, 78699, 78700, 78701, 78702, 78703, 78704,
                     78705, 78706, 78707, 78708, 78709, 78710, 78711, 78712, 78713,
                     78714, 78715, 78716, 78717, 78718, 78719, 78720, 78721, 78722,
                     78723, 78724, 78725, 78726, 78727, 78728, 78729, 78730, 78731,
                     78732, 78733, 78734, 78735, 78736, 78737, 78738, 78739, 78740,
                     78741, 78742, 78743, 78744, 78745, 78746, 78747, 78748, 78749,
                     78750, 78751, 78752, 78753, 78754, 78755, 78756, 78757, 78758,
                     78759, 78760, 78761, 78762, 78763, 78764, 78765, 78766, 78767],
                    dtype='int64'),
         437: Int64Index([98674, 98675, 98676, 98677, 98678], dtype='int64'),
         438: Int64Index([98170, 98171, 98172, 98173, 98174, 98175], dtype='int64'),
         439: Int64Index([98801, 98802, 98803, 98804, 98805], dtype='int64'),
         440: Int64Index([97791, 97792, 97793, 97794, 97795, 97796, 97797, 97798, 97799,
                     97800, 97801, 97802, 97803, 97804],
                    dtype='int64'),
         441: Int64Index([97861, 97862, 97863, 97864, 97865, 97866, 97867, 97868, 97869,
                     97870, 97871, 97872, 97873, 97874, 97875, 97876, 97877, 97878,
                     97879, 97880, 97881, 97882, 97883, 97884, 97885, 97886, 97887,
                     97888, 97889, 97890, 97891, 97892, 97893, 97894, 97895, 97896,
                     97897, 97898, 97899, 97900, 97901, 97902, 97903, 97904, 97905,
                     97906, 97907, 97908, 97909, 97910, 97911, 97912, 97913],
                    dtype='int64'),
         442: Int64Index([98797, 98798, 98799, 98800], dtype='int64'),
         443: Int64Index([64890, 64891, 64892, 64893, 64894, 64895, 64896, 64897, 64898,
                     64899,
                     ...
                     65042, 65043, 65044, 65045, 65046, 65047, 65048, 65049, 65050,
                     65051],
                    dtype='int64', length=162),
         444: Int64Index([95300, 95301, 95302, 95303, 95304, 95305, 95306, 95307, 95308,
                     95309, 95310, 95311, 95312, 95313, 95314, 95315, 95316, 95317,
                     95318, 95319, 95320, 95321, 95322, 95323, 95324, 95325, 95326,
                     95327, 95328, 95329, 95330, 95331, 95332, 95333, 95334, 95335,
                     95336, 95337, 95338, 95339, 95340, 95341, 95342, 95343, 95344,
                     95345],
                    dtype='int64'),
         445: Int64Index([93821, 93822, 93823, 93824, 93825, 93826, 93827, 93828, 93829,
                     93830, 93831, 93832, 93833, 93834, 93835, 93836, 93837, 93838,
                     93839, 93840, 93841, 93842],
                    dtype='int64'),
         446: Int64Index([97743, 97744, 97745, 97746, 97747, 97748, 97749, 97750, 97751], dtype='int64'),
         447: Int64Index([84876, 84877, 84878, 84879, 84880, 84881, 84882, 84883, 84884,
                     84885,
                     ...
                     84987, 84988, 84989, 84990, 84991, 84992, 84993, 84994, 84995,
                     84996],
                    dtype='int64', length=121),
         448: Int64Index([67734, 67735, 67736, 67737, 67738, 67739, 67740, 67741, 67742,
                     67743, 67744, 67745, 67746, 67747, 67748, 67749, 67750, 67751,
                     67752, 67753, 67754, 67755, 67756, 67757, 67758, 67759, 67760,
                     67761, 67762, 67763, 67764, 67765, 67766, 67767, 67768, 67769,
                     67770, 67771, 67772, 67773, 67774, 67775, 67776, 67777, 67778,
                     67779, 67780, 67781, 67782, 67783, 67784, 67785, 67786, 67787,
                     67788, 67789, 67790, 67791, 67792, 67793, 67794, 67795, 67796,
                     67797, 67798, 67799, 67800, 67801, 67802, 67803, 67804, 67805,
                     67806, 67807, 67808, 67809, 67810, 67811, 67812, 67813, 67814,
                     67815, 67816, 67817, 67818],
                    dtype='int64'),
         449: Int64Index([27922, 27923, 27924, 27925, 27926, 27927, 27928, 27929, 27930,
                     27931,
                     ...
                     28029, 28030, 28031, 28032, 28033, 28034, 28035, 28036, 28037,
                     28038],
                    dtype='int64', length=117),
         450: Int64Index([87098, 87099, 87100, 87101, 87102, 87103, 87104, 87105, 87106,
                     87107, 87108, 87109, 87110, 87111, 87112, 87113, 87114, 87115,
                     87116, 87117, 87118, 87119, 87120, 87121, 87122, 87123, 87124,
                     87125, 87126, 87127, 87128, 87129, 87130, 87131, 87132, 87133,
                     87134, 87135, 87136, 87137, 87138, 87139, 87140, 87141, 87142,
                     87143, 87144, 87145, 87146, 87147, 87148, 87149, 87150, 87151,
                     87152, 87153, 87154, 87155, 87156, 87157, 87158, 87159, 87160],
                    dtype='int64'),
         451: Int64Index([27035, 27036, 27037, 27038, 27039, 27040, 27041, 27042, 27043,
                     27044,
                     ...
                     27195, 27196, 27197, 27198, 27199, 27200, 27201, 27202, 27203,
                     27204],
                    dtype='int64', length=170),
         452: Int64Index([87845, 87846, 87847, 87848, 87849, 87850, 87851, 87852, 87853,
                     87854, 87855, 87856, 87857, 87858, 87859, 87860, 87861, 87862,
                     87863, 87864, 87865, 87866, 87867, 87868, 87869, 87870, 87871,
                     87872, 87873, 87874, 87875, 87876, 87877, 87878, 87879, 87880,
                     87881, 87882, 87883, 87884, 87885, 87886, 87887, 87888, 87889,
                     87890, 87891, 87892, 87893, 87894, 87895, 87896, 87897, 87898,
                     87899, 87900, 87901, 87902, 87903, 87904, 87905, 87906, 87907,
                     87908, 87909, 87910],
                    dtype='int64'),
         453: Int64Index([97579, 97580, 97581, 97582, 97583, 97584, 97585, 97586, 97587,
                     97588, 97589, 97590, 97591, 97592, 97593, 97594],
                    dtype='int64'),
         454: Int64Index([98068, 98069, 98070, 98071, 98072, 98073, 98074, 98075, 98076,
                     98077, 98078, 98079, 98080, 98081, 98082, 98083],
                    dtype='int64'),
         455: Int64Index([23738, 23739, 23740, 23741, 23742, 23743, 23744, 23745, 23746,
                     23747,
                     ...
                     23873, 23874, 23875, 23876, 23877, 23878, 23879, 23880, 23881,
                     23882],
                    dtype='int64', length=145),
         456: Int64Index([21412, 21413, 21414, 21415, 21416, 21417, 21418, 21419, 21420,
                     21421, 21422, 21423, 21424, 21425, 21426, 21427, 21428, 21429,
                     21430, 21431, 21432, 21433, 21434, 21435, 21436, 21437, 21438,
                     21439, 21440, 21441, 21442, 21443, 21444, 21445, 21446, 21447,
                     21448, 21449, 21450, 21451, 21452, 21453, 21454, 21455, 21456,
                     21457, 21458, 21459],
                    dtype='int64'),
         457: Int64Index([96094, 96095, 96096, 96097, 96098, 96099, 96100, 96101, 96102,
                     96103, 96104, 96105, 96106, 96107, 96108, 96109, 96110, 96111,
                     96112, 96113, 96114, 96115, 96116, 96117, 96118, 96119, 96120],
                    dtype='int64'),
         458: Int64Index([46568, 46569, 46570, 46571, 46572, 46573, 46574, 46575, 46576,
                     46577, 46578, 46579, 46580, 46581, 46582, 46583, 46584, 46585,
                     46586, 46587, 46588, 46589, 46590, 46591, 46592, 46593, 46594,
                     46595, 46596, 46597, 46598, 46599, 46600, 46601, 46602, 46603,
                     46604, 46605, 46606, 46607, 46608, 46609, 46610, 46611, 46612,
                     46613, 46614, 46615, 46616, 46617, 46618, 46619, 46620, 46621,
                     46622, 46623, 46624, 46625, 46626, 46627, 46628, 46629, 46630,
                     46631, 46632, 46633, 46634, 46635, 46636, 46637, 46638, 46639,
                     46640, 46641, 46642, 46643, 46644, 46645, 46646, 46647, 46648,
                     46649, 46650, 46651, 46652, 46653, 46654, 46655, 46656, 46657],
                    dtype='int64'),
         459: Int64Index([75673, 75674, 75675, 75676, 75677, 75678, 75679, 75680, 75681,
                     75682, 75683, 75684, 75685, 75686, 75687, 75688, 75689, 75690,
                     75691, 75692, 75693, 75694, 75695, 75696],
                    dtype='int64'),
         460: Int64Index([77633, 77634, 77635, 77636, 77637, 77638, 77639, 77640, 77641,
                     77642, 77643, 77644, 77645, 77646, 77647, 77648, 77649, 77650,
                     77651, 77652, 77653, 77654, 77655, 77656, 77657, 77658, 77659,
                     77660],
                    dtype='int64'),
         461: Int64Index([76436, 76437, 76438, 76439, 76440, 76441, 76442, 76443, 76444,
                     76445, 76446, 76447, 76448, 76449, 76450, 76451, 76452, 76453,
                     76454, 76455, 76456, 76457, 76458, 76459, 76460, 76461, 76462,
                     76463, 76464, 76465, 76466, 76467, 76468, 76469, 76470, 76471,
                     76472, 76473, 76474, 76475, 76476, 76477, 76478, 76479, 76480,
                     76481, 76482, 76483, 76484, 76485, 76486, 76487, 76488, 76489,
                     76490, 76491, 76492, 76493, 76494, 76495, 76496, 76497, 76498,
                     76499, 76500, 76501, 76502, 76503, 76504, 76505, 76506, 76507,
                     76508, 76509],
                    dtype='int64'),
         462: Int64Index([64601, 64602, 64603, 64604, 64605, 64606, 64607, 64608, 64609,
                     64610,
                     ...
                     64739, 64740, 64741, 64742, 64743, 64744, 64745, 64746, 64747,
                     64748],
                    dtype='int64', length=148),
         463: Int64Index([74558, 74559, 74560, 74561, 74562, 74563, 74564, 74565, 74566,
                     74567, 74568, 74569, 74570, 74571, 74572, 74573, 74574, 74575,
                     74576, 74577, 74578, 74579, 74580, 74581, 74582, 74583, 74584,
                     74585, 74586, 74587, 74588, 74589, 74590, 74591, 74592, 74593,
                     74594, 74595, 74596, 74597, 74598, 74599, 74600, 74601, 74602,
                     74603, 74604, 74605, 74606, 74607, 74608, 74609, 74610, 74611,
                     74612, 74613, 74614, 74615, 74616, 74617, 74618, 74619, 74620,
                     74621, 74622, 74623, 74624, 74625, 74626, 74627, 74628],
                    dtype='int64'),
         464: Int64Index([74016, 74017, 74018, 74019, 74020, 74021, 74022, 74023, 74024,
                     74025, 74026, 74027, 74028, 74029, 74030, 74031, 74032, 74033,
                     74034, 74035, 74036, 74037, 74038, 74039, 74040, 74041, 74042],
                    dtype='int64'),
         465: Int64Index([57475, 57476, 57477, 57478, 57479, 57480, 57481, 57482, 57483,
                     57484, 57485, 57486, 57487, 57488, 57489, 57490, 57491, 57492,
                     57493, 57494, 57495, 57496, 57497, 57498, 57499, 57500, 57501,
                     57502, 57503, 57504, 57505, 57506, 57507, 57508, 57509, 57510,
                     57511, 57512, 57513, 57514, 57515, 57516, 57517, 57518, 57519,
                     57520, 57521, 57522, 57523, 57524, 57525, 57526, 57527, 57528,
                     57529, 57530, 57531, 57532, 57533, 57534, 57535, 57536, 57537,
                     57538, 57539, 57540, 57541, 57542, 57543, 57544, 57545, 57546,
                     57547, 57548, 57549, 57550, 57551, 57552, 57553, 57554, 57555,
                     57556, 57557, 57558, 57559],
                    dtype='int64'),
         466: Int64Index([64749, 64750, 64751, 64752, 64753, 64754, 64755, 64756, 64757,
                     64758, 64759, 64760, 64761, 64762, 64763, 64764, 64765, 64766,
                     64767, 64768, 64769, 64770, 64771, 64772, 64773, 64774, 64775,
                     64776, 64777, 64778, 64779, 64780, 64781, 64782, 64783, 64784,
                     64785, 64786, 64787, 64788, 64789, 64790, 64791, 64792, 64793,
                     64794, 64795, 64796, 64797, 64798, 64799, 64800],
                    dtype='int64'),
         467: Int64Index([75321, 75322, 75323, 75324, 75325, 75326, 75327, 75328, 75329,
                     75330, 75331, 75332, 75333, 75334, 75335, 75336, 75337, 75338,
                     75339, 75340, 75341, 75342, 75343, 75344, 75345, 75346, 75347,
                     75348, 75349, 75350, 75351, 75352, 75353, 75354, 75355, 75356,
                     75357, 75358, 75359, 75360, 75361, 75362, 75363, 75364, 75365,
                     75366, 75367, 75368],
                    dtype='int64'),
         468: Int64Index([48172, 48173, 48174, 48175, 48176, 48177, 48178, 48179, 48180,
                     48181, 48182, 48183, 48184, 48185, 48186, 48187, 48188, 48189,
                     48190, 48191, 48192, 48193, 48194, 48195, 48196, 48197, 48198,
                     48199, 48200, 48201, 48202, 48203, 48204, 48205, 48206, 48207,
                     48208, 48209, 48210, 48211, 48212, 48213, 48214, 48215, 48216,
                     48217, 48218, 48219, 48220, 48221, 48222, 48223, 48224, 48225,
                     48226, 48227, 48228, 48229, 48230, 48231, 48232, 48233, 48234,
                     48235],
                    dtype='int64'),
         469: Int64Index([74339, 74340, 74341, 74342, 74343, 74344, 74345, 74346, 74347,
                     74348, 74349, 74350, 74351, 74352, 74353, 74354, 74355, 74356,
                     74357, 74358, 74359, 74360, 74361, 74362, 74363, 74364, 74365,
                     74366, 74367, 74368, 74369, 74370, 74371, 74372, 74373, 74374,
                     74375, 74376, 74377, 74378, 74379, 74380, 74381, 74382, 74383,
                     74384, 74385, 74386, 74387, 74388, 74389, 74390, 74391, 74392,
                     74393, 74394, 74395, 74396, 74397, 74398, 74399, 74400, 74401,
                     74402, 74403, 74404, 74405],
                    dtype='int64'),
         470: Int64Index([7205, 7206, 7207, 7208, 7209, 7210, 7211, 7212, 7213, 7214,
                     ...
                     7303, 7304, 7305, 7306, 7307, 7308, 7309, 7310, 7311, 7312],
                    dtype='int64', length=108),
         471: Int64Index([44633, 44634, 44635, 44636, 44637, 44638, 44639, 44640, 44641,
                     44642,
                     ...
                     44844, 44845, 44846, 44847, 44848, 44849, 44850, 44851, 44852,
                     44853],
                    dtype='int64', length=221),
         472: Int64Index([77246, 77247, 77248, 77249, 77250, 77251, 77252, 77253, 77254,
                     77255,
                     ...
                     77394, 77395, 77396, 77397, 77398, 77399, 77400, 77401, 77402,
                     77403],
                    dtype='int64', length=158),
         473: Int64Index([57987, 57988, 57989, 57990, 57991, 57992, 57993, 57994, 57995,
                     57996,
                     ...
                     58103, 58104, 58105, 58106, 58107, 58108, 58109, 58110, 58111,
                     58112],
                    dtype='int64', length=126),
         474: Int64Index([56374, 56375, 56376, 56377, 56378, 56379, 56380, 56381, 56382,
                     56383,
                     ...
                     56558, 56559, 56560, 56561, 56562, 56563, 56564, 56565, 56566,
                     56567],
                    dtype='int64', length=194),
         475: Int64Index([40908, 40909, 40910, 40911, 40912, 40913, 40914, 40915, 40916,
                     40917,
                     ...
                     41148, 41149, 41150, 41151, 41152, 41153, 41154, 41155, 41156,
                     41157],
                    dtype='int64', length=250),
         476: Int64Index([75098, 75099, 75100, 75101, 75102, 75103, 75104, 75105, 75106,
                     75107,
                     ...
                     75248, 75249, 75250, 75251, 75252, 75253, 75254, 75255, 75256,
                     75257],
                    dtype='int64', length=160),
         477: Int64Index([17246, 17247, 17248, 17249, 17250, 17251, 17252, 17253, 17254,
                     17255, 17256, 17257, 17258, 17259, 17260, 17261, 17262, 17263,
                     17264, 17265, 17266, 17267, 17268, 17269, 17270, 17271, 17272,
                     17273, 17274, 17275, 17276, 17277, 17278, 17279, 17280, 17281,
                     17282, 17283, 17284, 17285, 17286, 17287, 17288, 17289, 17290,
                     17291, 17292, 17293, 17294, 17295, 17296, 17297, 17298, 17299,
                     17300, 17301, 17302, 17303, 17304, 17305, 17306, 17307, 17308,
                     17309, 17310, 17311, 17312, 17313, 17314, 17315, 17316, 17317,
                     17318, 17319, 17320, 17321, 17322, 17323, 17324, 17325, 17326,
                     17327, 17328, 17329, 17330, 17331, 17332, 17333, 17334, 17335,
                     17336, 17337, 17338, 17339, 17340],
                    dtype='int64'),
         478: Int64Index([73216, 73217, 73218, 73219, 73220, 73221, 73222, 73223, 73224,
                     73225,
                     ...
                     73310, 73311, 73312, 73313, 73314, 73315, 73316, 73317, 73318,
                     73319],
                    dtype='int64', length=104),
         479: Int64Index([62392, 62393, 62394, 62395, 62396, 62397, 62398, 62399, 62400,
                     62401,
                     ...
                     62561, 62562, 62563, 62564, 62565, 62566, 62567, 62568, 62569,
                     62570],
                    dtype='int64', length=179),
         480: Int64Index([72569, 72570, 72571, 72572, 72573, 72574, 72575, 72576, 72577,
                     72578,
                     ...
                     72738, 72739, 72740, 72741, 72742, 72743, 72744, 72745, 72746,
                     72747],
                    dtype='int64', length=179),
         481: Int64Index([75258, 75259, 75260, 75261, 75262, 75263, 75264, 75265, 75266,
                     75267, 75268, 75269, 75270, 75271, 75272, 75273, 75274, 75275,
                     75276, 75277, 75278, 75279, 75280, 75281, 75282, 75283, 75284,
                     75285, 75286, 75287, 75288, 75289, 75290, 75291, 75292, 75293,
                     75294, 75295, 75296, 75297, 75298, 75299, 75300, 75301, 75302,
                     75303, 75304, 75305, 75306, 75307, 75308, 75309, 75310, 75311,
                     75312, 75313, 75314, 75315, 75316, 75317, 75318, 75319, 75320],
                    dtype='int64'),
         482: Int64Index([64193, 64194, 64195, 64196, 64197, 64198, 64199, 64200, 64201,
                     64202,
                     ...
                     64311, 64312, 64313, 64314, 64315, 64316, 64317, 64318, 64319,
                     64320],
                    dtype='int64', length=128),
         483: Int64Index([59337, 59338, 59339, 59340, 59341, 59342, 59343, 59344, 59345,
                     59346,
                     ...
                     59570, 59571, 59572, 59573, 59574, 59575, 59576, 59577, 59578,
                     59579],
                    dtype='int64', length=243),
         484: Int64Index([61215, 61216, 61217, 61218, 61219, 61220, 61221, 61222, 61223,
                     61224,
                     ...
                     61343, 61344, 61345, 61346, 61347, 61348, 61349, 61350, 61351,
                     61352],
                    dtype='int64', length=138),
         485: Int64Index([63559, 63560, 63561, 63562, 63563, 63564, 63565, 63566, 63567,
                     63568,
                     ...
                     63674, 63675, 63676, 63677, 63678, 63679, 63680, 63681, 63682,
                     63683],
                    dtype='int64', length=125),
         486: Int64Index([56568, 56569, 56570, 56571, 56572, 56573, 56574, 56575, 56576,
                     56577, 56578, 56579, 56580, 56581, 56582, 56583, 56584, 56585,
                     56586, 56587, 56588, 56589, 56590, 56591, 56592, 56593, 56594,
                     56595, 56596, 56597, 56598, 56599, 56600, 56601, 56602, 56603,
                     56604, 56605, 56606, 56607, 56608, 56609, 56610, 56611, 56612,
                     56613, 56614, 56615, 56616, 56617, 56618, 56619, 56620, 56621,
                     56622, 56623, 56624, 56625, 56626, 56627, 56628, 56629, 56630,
                     56631],
                    dtype='int64'),
         487: Int64Index([67957, 67958, 67959, 67960, 67961, 67962, 67963, 67964, 67965,
                     67966, 67967, 67968, 67969, 67970, 67971, 67972, 67973, 67974,
                     67975, 67976, 67977, 67978, 67979, 67980, 67981, 67982, 67983,
                     67984, 67985, 67986, 67987, 67988, 67989, 67990, 67991, 67992,
                     67993, 67994, 67995, 67996, 67997, 67998, 67999, 68000, 68001,
                     68002, 68003, 68004, 68005, 68006, 68007, 68008, 68009, 68010,
                     68011, 68012, 68013, 68014, 68015, 68016, 68017, 68018, 68019,
                     68020, 68021, 68022, 68023, 68024],
                    dtype='int64'),
         488: Int64Index([75608, 75609, 75610, 75611, 75612, 75613, 75614, 75615, 75616,
                     75617, 75618, 75619, 75620, 75621, 75622, 75623, 75624, 75625,
                     75626, 75627, 75628, 75629, 75630, 75631, 75632, 75633, 75634,
                     75635, 75636, 75637, 75638, 75639, 75640, 75641, 75642, 75643,
                     75644, 75645, 75646, 75647, 75648, 75649, 75650, 75651, 75652,
                     75653, 75654, 75655, 75656, 75657, 75658, 75659, 75660, 75661,
                     75662, 75663, 75664, 75665, 75666, 75667, 75668, 75669, 75670,
                     75671, 75672],
                    dtype='int64'),
         489: Int64Index([77581, 77582, 77583, 77584, 77585, 77586, 77587, 77588, 77589,
                     77590, 77591, 77592, 77593, 77594, 77595, 77596, 77597, 77598,
                     77599, 77600, 77601, 77602, 77603, 77604, 77605, 77606, 77607,
                     77608, 77609, 77610, 77611, 77612, 77613, 77614, 77615, 77616,
                     77617, 77618, 77619, 77620, 77621, 77622, 77623, 77624, 77625,
                     77626, 77627, 77628, 77629, 77630, 77631, 77632],
                    dtype='int64'),
         490: Int64Index([69118, 69119, 69120, 69121, 69122, 69123, 69124, 69125, 69126,
                     69127, 69128, 69129, 69130, 69131, 69132, 69133, 69134, 69135,
                     69136, 69137, 69138, 69139, 69140, 69141, 69142, 69143, 69144,
                     69145, 69146, 69147, 69148, 69149, 69150, 69151, 69152, 69153,
                     69154, 69155, 69156, 69157, 69158, 69159, 69160, 69161, 69162,
                     69163, 69164, 69165, 69166, 69167],
                    dtype='int64'),
         491: Int64Index([77514, 77515, 77516, 77517, 77518, 77519, 77520, 77521, 77522,
                     77523, 77524, 77525, 77526, 77527, 77528, 77529, 77530, 77531,
                     77532, 77533, 77534, 77535, 77536, 77537, 77538, 77539, 77540,
                     77541, 77542, 77543, 77544, 77545, 77546, 77547, 77548, 77549,
                     77550, 77551, 77552, 77553, 77554, 77555, 77556, 77557, 77558,
                     77559, 77560, 77561, 77562, 77563, 77564, 77565, 77566, 77567,
                     77568, 77569, 77570, 77571, 77572, 77573, 77574, 77575, 77576,
                     77577, 77578, 77579, 77580],
                    dtype='int64'),
         492: Int64Index([74720, 74721, 74722, 74723, 74724, 74725, 74726, 74727, 74728,
                     74729, 74730, 74731, 74732, 74733, 74734, 74735, 74736, 74737,
                     74738, 74739, 74740, 74741, 74742, 74743, 74744, 74745, 74746,
                     74747, 74748, 74749, 74750, 74751, 74752, 74753, 74754, 74755,
                     74756, 74757, 74758, 74759, 74760, 74761, 74762, 74763, 74764,
                     74765, 74766, 74767, 74768, 74769, 74770, 74771, 74772, 74773,
                     74774, 74775, 74776, 74777, 74778],
                    dtype='int64'),
         493: Int64Index([76847, 76848, 76849, 76850, 76851, 76852, 76853, 76854, 76855,
                     76856, 76857, 76858, 76859, 76860, 76861, 76862, 76863, 76864,
                     76865, 76866, 76867, 76868, 76869, 76870, 76871, 76872, 76873,
                     76874, 76875, 76876, 76877, 76878, 76879, 76880, 76881, 76882,
                     76883, 76884, 76885, 76886, 76887, 76888, 76889, 76890, 76891,
                     76892, 76893, 76894, 76895, 76896, 76897, 76898, 76899, 76900,
                     76901, 76902, 76903, 76904, 76905, 76906],
                    dtype='int64'),
         494: Int64Index([68251, 68252, 68253, 68254, 68255, 68256, 68257, 68258, 68259,
                     68260, 68261, 68262, 68263, 68264, 68265, 68266, 68267, 68268,
                     68269, 68270, 68271, 68272, 68273, 68274, 68275, 68276, 68277,
                     68278, 68279, 68280, 68281, 68282, 68283, 68284, 68285, 68286,
                     68287, 68288, 68289, 68290, 68291, 68292, 68293, 68294, 68295,
                     68296, 68297, 68298, 68299, 68300, 68301, 68302, 68303, 68304,
                     68305, 68306],
                    dtype='int64'),
         495: Int64Index([76907, 76908, 76909, 76910, 76911, 76912, 76913, 76914, 76915,
                     76916, 76917, 76918, 76919, 76920, 76921, 76922, 76923, 76924,
                     76925, 76926, 76927, 76928, 76929, 76930, 76931, 76932, 76933,
                     76934, 76935, 76936, 76937, 76938, 76939, 76940, 76941, 76942,
                     76943, 76944, 76945, 76946, 76947, 76948, 76949, 76950, 76951,
                     76952, 76953, 76954, 76955, 76956, 76957, 76958, 76959, 76960,
                     76961, 76962, 76963, 76964, 76965],
                    dtype='int64'),
         496: Int64Index([57756, 57757, 57758, 57759, 57760, 57761, 57762, 57763, 57764,
                     57765,
                     ...
                     57977, 57978, 57979, 57980, 57981, 57982, 57983, 57984, 57985,
                     57986],
                    dtype='int64', length=231),
         497: Int64Index([77715, 77716, 77717, 77718, 77719, 77720, 77721, 77722, 77723,
                     77724, 77725, 77726, 77727, 77728, 77729, 77730, 77731, 77732,
                     77733, 77734, 77735, 77736, 77737, 77738, 77739, 77740, 77741,
                     77742, 77743, 77744, 77745, 77746, 77747, 77748, 77749, 77750,
                     77751, 77752, 77753, 77754, 77755, 77756, 77757, 77758, 77759,
                     77760, 77761, 77762, 77763, 77764, 77765, 77766, 77767, 77768,
                     77769, 77770, 77771, 77772, 77773, 77774, 77775, 77776, 77777,
                     77778, 77779, 77780, 77781, 77782],
                    dtype='int64'),
         498: Int64Index([57604, 57605, 57606, 57607, 57608, 57609, 57610, 57611, 57612,
                     57613,
                     ...
                     57746, 57747, 57748, 57749, 57750, 57751, 57752, 57753, 57754,
                     57755],
                    dtype='int64', length=152),
         499: Int64Index([75546, 75547, 75548, 75549, 75550, 75551, 75552, 75553, 75554,
                     75555, 75556, 75557, 75558, 75559, 75560, 75561, 75562, 75563,
                     75564, 75565, 75566, 75567, 75568, 75569, 75570, 75571, 75572,
                     75573, 75574, 75575, 75576, 75577, 75578, 75579, 75580, 75581,
                     75582, 75583, 75584, 75585, 75586, 75587, 75588, 75589, 75590,
                     75591, 75592, 75593, 75594, 75595, 75596, 75597, 75598, 75599,
                     75600, 75601, 75602, 75603, 75604, 75605, 75606, 75607],
                    dtype='int64'),
         500: Int64Index([74925, 74926, 74927, 74928, 74929, 74930, 74931, 74932, 74933,
                     74934, 74935, 74936, 74937, 74938, 74939, 74940, 74941, 74942,
                     74943, 74944, 74945, 74946, 74947, 74948, 74949, 74950, 74951,
                     74952, 74953, 74954, 74955],
                    dtype='int64'),
         501: Int64Index([76966, 76967, 76968, 76969, 76970, 76971, 76972, 76973, 76974,
                     76975,
                     ...
                     77079, 77080, 77081, 77082, 77083, 77084, 77085, 77086, 77087,
                     77088],
                    dtype='int64', length=123),
         502: Int64Index([22538, 22539, 22540, 22541, 22542, 22543, 22544, 22545, 22546,
                     22547, 22548, 22549, 22550, 22551, 22552, 22553, 22554, 22555,
                     22556, 22557, 22558, 22559, 22560, 22561, 22562, 22563, 22564,
                     22565, 22566, 22567, 22568, 22569, 22570, 22571, 22572, 22573,
                     22574, 22575, 22576, 22577, 22578, 22579, 22580, 22581, 22582,
                     22583, 22584, 22585, 22586, 22587, 22588, 22589, 22590, 22591,
                     22592, 22593, 22594],
                    dtype='int64'),
         503: Int64Index([58915, 58916, 58917, 58918, 58919, 58920, 58921, 58922, 58923,
                     58924, 58925, 58926, 58927, 58928, 58929, 58930, 58931, 58932,
                     58933, 58934, 58935, 58936, 58937, 58938, 58939, 58940, 58941,
                     58942, 58943, 58944, 58945, 58946, 58947, 58948, 58949, 58950,
                     58951, 58952, 58953],
                    dtype='int64'),
         504: Int64Index([61846, 61847, 61848, 61849, 61850, 61851, 61852, 61853, 61854,
                     61855,
                     ...
                     61958, 61959, 61960, 61961, 61962, 61963, 61964, 61965, 61966,
                     61967],
                    dtype='int64', length=122),
         505: Int64Index([74124, 74125, 74126, 74127, 74128, 74129, 74130, 74131, 74132,
                     74133, 74134, 74135, 74136, 74137, 74138, 74139, 74140, 74141,
                     74142, 74143, 74144, 74145, 74146, 74147, 74148, 74149, 74150,
                     74151, 74152, 74153, 74154, 74155, 74156, 74157, 74158, 74159,
                     74160, 74161, 74162, 74163, 74164, 74165, 74166, 74167, 74168,
                     74169, 74170, 74171, 74172, 74173, 74174, 74175, 74176, 74177,
                     74178, 74179, 74180, 74181, 74182, 74183, 74184, 74185, 74186,
                     74187, 74188, 74189, 74190, 74191],
                    dtype='int64'),
         506: Int64Index([76006, 76007, 76008, 76009, 76010, 76011, 76012, 76013, 76014,
                     76015, 76016, 76017, 76018, 76019, 76020, 76021, 76022, 76023,
                     76024, 76025, 76026, 76027, 76028, 76029, 76030, 76031, 76032,
                     76033, 76034, 76035, 76036, 76037, 76038, 76039, 76040, 76041,
                     76042, 76043, 76044, 76045, 76046, 76047, 76048, 76049, 76050,
                     76051, 76052, 76053, 76054, 76055, 76056, 76057, 76058, 76059,
                     76060, 76061, 76062, 76063, 76064, 76065, 76066, 76067, 76068,
                     76069, 76070, 76071, 76072, 76073, 76074, 76075, 76076, 76077,
                     76078, 76079, 76080, 76081, 76082, 76083, 76084, 76085, 76086,
                     76087, 76088, 76089, 76090, 76091, 76092, 76093, 76094, 76095],
                    dtype='int64'),
         507: Int64Index([58388, 58389, 58390, 58391, 58392, 58393, 58394, 58395, 58396,
                     58397, 58398, 58399, 58400, 58401, 58402, 58403, 58404, 58405,
                     58406, 58407, 58408, 58409, 58410, 58411, 58412, 58413, 58414,
                     58415, 58416, 58417, 58418, 58419, 58420, 58421, 58422, 58423,
                     58424, 58425, 58426, 58427, 58428, 58429, 58430, 58431, 58432,
                     58433, 58434, 58435, 58436, 58437, 58438, 58439, 58440, 58441,
                     58442, 58443, 58444, 58445, 58446, 58447, 58448, 58449, 58450,
                     58451, 58452, 58453, 58454, 58455, 58456, 58457, 58458, 58459,
                     58460, 58461, 58462, 58463, 58464, 58465, 58466, 58467, 58468,
                     58469, 58470, 58471, 58472, 58473, 58474, 58475, 58476, 58477,
                     58478, 58479, 58480, 58481, 58482, 58483, 58484, 58485],
                    dtype='int64'),
         508: Int64Index([39353, 39354, 39355, 39356, 39357, 39358, 39359, 39360, 39361,
                     39362,
                     ...
                     39558, 39559, 39560, 39561, 39562, 39563, 39564, 39565, 39566,
                     39567],
                    dtype='int64', length=215),
         509: Int64Index([37570, 37571, 37572, 37573, 37574, 37575, 37576, 37577, 37578,
                     37579,
                     ...
                     37681, 37682, 37683, 37684, 37685, 37686, 37687, 37688, 37689,
                     37690],
                    dtype='int64', length=121),
         510: Int64Index([20707, 20708, 20709, 20710, 20711, 20712, 20713, 20714, 20715,
                     20716,
                     ...
                     20818, 20819, 20820, 20821, 20822, 20823, 20824, 20825, 20826,
                     20827],
                    dtype='int64', length=121),
         511: Int64Index([20838, 20839, 20840, 20841, 20842, 20843, 20844, 20845, 20846,
                     20847,
                     ...
                     21001, 21002, 21003, 21004, 21005, 21006, 21007, 21008, 21009,
                     21010],
                    dtype='int64', length=173),
         512: Int64Index([69470, 69471, 69472, 69473, 69474, 69475, 69476, 69477, 69478,
                     69479, 69480, 69481, 69482, 69483, 69484, 69485, 69486, 69487,
                     69488, 69489, 69490, 69491, 69492, 69493, 69494, 69495, 69496,
                     69497, 69498, 69499, 69500, 69501, 69502, 69503, 69504, 69505,
                     69506, 69507, 69508, 69509, 69510, 69511, 69512, 69513, 69514,
                     69515, 69516, 69517, 69518, 69519, 69520, 69521, 69522, 69523,
                     69524, 69525, 69526],
                    dtype='int64'),
         513: Int64Index([75474, 75475, 75476, 75477, 75478, 75479, 75480, 75481, 75482,
                     75483, 75484, 75485, 75486, 75487, 75488, 75489, 75490, 75491,
                     75492, 75493, 75494, 75495, 75496, 75497, 75498, 75499, 75500,
                     75501, 75502, 75503, 75504, 75505, 75506, 75507, 75508, 75509,
                     75510, 75511, 75512, 75513, 75514, 75515, 75516, 75517, 75518,
                     75519, 75520, 75521, 75522, 75523, 75524, 75525, 75526, 75527,
                     75528, 75529, 75530, 75531, 75532, 75533, 75534, 75535, 75536,
                     75537, 75538, 75539, 75540, 75541, 75542, 75543, 75544, 75545],
                    dtype='int64'),
         514: Int64Index([60268, 60269, 60270, 60271, 60272, 60273, 60274, 60275, 60276,
                     60277,
                     ...
                     60438, 60439, 60440, 60441, 60442, 60443, 60444, 60445, 60446,
                     60447],
                    dtype='int64', length=180),
         515: Int64Index([26762, 26763, 26764, 26765, 26766, 26767, 26768, 26769, 26770,
                     26771,
                     ...
                     26953, 26954, 26955, 26956, 26957, 26958, 26959, 26960, 26961,
                     26962],
                    dtype='int64', length=201),
         516: Int64Index([77089, 77090, 77091, 77092, 77093, 77094, 77095, 77096, 77097,
                     77098, 77099, 77100, 77101, 77102, 77103, 77104, 77105, 77106,
                     77107, 77108, 77109, 77110, 77111, 77112, 77113, 77114, 77115,
                     77116, 77117, 77118, 77119, 77120, 77121, 77122, 77123, 77124,
                     77125, 77126, 77127, 77128, 77129, 77130, 77131, 77132, 77133,
                     77134, 77135, 77136, 77137, 77138, 77139, 77140, 77141, 77142,
                     77143, 77144, 77145, 77146, 77147, 77148, 77149, 77150, 77151],
                    dtype='int64'),
         517: Int64Index([74629, 74630, 74631, 74632, 74633, 74634, 74635, 74636, 74637,
                     74638, 74639, 74640, 74641, 74642, 74643, 74644, 74645, 74646,
                     74647, 74648, 74649, 74650, 74651, 74652, 74653, 74654, 74655,
                     74656, 74657, 74658, 74659, 74660, 74661, 74662, 74663, 74664,
                     74665, 74666, 74667, 74668, 74669, 74670, 74671, 74672, 74673,
                     74674, 74675, 74676, 74677, 74678, 74679, 74680, 74681, 74682,
                     74683, 74684, 74685, 74686, 74687, 74688, 74689, 74690, 74691,
                     74692, 74693, 74694, 74695, 74696, 74697, 74698, 74699, 74700,
                     74701, 74702, 74703, 74704, 74705, 74706, 74707, 74708, 74709,
                     74710, 74711, 74712, 74713, 74714, 74715, 74716, 74717, 74718,
                     74719],
                    dtype='int64'),
         518: Int64Index([69270, 69271, 69272, 69273, 69274, 69275, 69276, 69277, 69278,
                     69279, 69280, 69281, 69282, 69283, 69284, 69285, 69286, 69287,
                     69288, 69289, 69290, 69291, 69292, 69293, 69294, 69295, 69296,
                     69297, 69298, 69299, 69300, 69301, 69302, 69303, 69304, 69305,
                     69306, 69307, 69308, 69309, 69310, 69311, 69312, 69313, 69314,
                     69315, 69316, 69317, 69318, 69319, 69320, 69321, 69322, 69323,
                     69324, 69325, 69326, 69327, 69328, 69329, 69330, 69331, 69332,
                     69333, 69334, 69335, 69336, 69337, 69338, 69339, 69340, 69341,
                     69342, 69343, 69344, 69345, 69346, 69347, 69348, 69349, 69350,
                     69351, 69352, 69353, 69354, 69355, 69356, 69357, 69358],
                    dtype='int64'),
         519: Int64Index([77434, 77435, 77436, 77437, 77438, 77439, 77440, 77441, 77442,
                     77443, 77444, 77445, 77446, 77447, 77448, 77449, 77450, 77451,
                     77452, 77453, 77454, 77455, 77456, 77457, 77458, 77459, 77460,
                     77461, 77462, 77463, 77464, 77465, 77466, 77467, 77468, 77469,
                     77470, 77471, 77472, 77473, 77474, 77475, 77476, 77477, 77478,
                     77479, 77480, 77481, 77482, 77483, 77484, 77485, 77486, 77487,
                     77488, 77489, 77490, 77491, 77492, 77493, 77494, 77495, 77496,
                     77497, 77498, 77499, 77500, 77501, 77502, 77503, 77504, 77505,
                     77506, 77507, 77508, 77509, 77510, 77511, 77512, 77513],
                    dtype='int64'),
         520: Int64Index([76165, 76166, 76167, 76168, 76169, 76170, 76171, 76172, 76173,
                     76174,
                     ...
                     76279, 76280, 76281, 76282, 76283, 76284, 76285, 76286, 76287,
                     76288],
                    dtype='int64', length=124),
         521: Int64Index([46238, 46239, 46240, 46241, 46242, 46243, 46244, 46245, 46246,
                     46247,
                     ...
                     46348, 46349, 46350, 46351, 46352, 46353, 46354, 46355, 46356,
                     46357],
                    dtype='int64', length=120),
         522: Int64Index([76679, 76680, 76681, 76682, 76683, 76684, 76685, 76686, 76687,
                     76688, 76689, 76690, 76691, 76692, 76693, 76694, 76695, 76696,
                     76697, 76698, 76699, 76700, 76701, 76702, 76703, 76704, 76705,
                     76706, 76707, 76708, 76709, 76710, 76711, 76712, 76713],
                    dtype='int64'),
         523: Int64Index([29525, 29526, 29527, 29528, 29529, 29530, 29531, 29532, 29533,
                     29534,
                     ...
                     29679, 29680, 29681, 29682, 29683, 29684, 29685, 29686, 29687,
                     29688],
                    dtype='int64', length=164),
         524: Int64Index([76109, 76110, 76111, 76112, 76113, 76114, 76115, 76116, 76117,
                     76118, 76119, 76120, 76121, 76122, 76123, 76124, 76125, 76126,
                     76127, 76128, 76129, 76130, 76131, 76132, 76133, 76134, 76135,
                     76136, 76137, 76138, 76139, 76140, 76141, 76142, 76143, 76144,
                     76145, 76146, 76147, 76148, 76149, 76150, 76151, 76152, 76153,
                     76154],
                    dtype='int64'),
         525: Int64Index([74956, 74957, 74958, 74959, 74960, 74961, 74962, 74963, 74964,
                     74965, 74966, 74967, 74968, 74969, 74970, 74971, 74972, 74973,
                     74974, 74975, 74976, 74977, 74978, 74979, 74980, 74981, 74982,
                     74983, 74984, 74985, 74986, 74987, 74988, 74989, 74990, 74991,
                     74992, 74993, 74994, 74995, 74996, 74997, 74998, 74999, 75000,
                     75001, 75002, 75003, 75004, 75005, 75006, 75007, 75008, 75009,
                     75010, 75011, 75012, 75013, 75014, 75015, 75016, 75017, 75018,
                     75019, 75020, 75021, 75022, 75023, 75024, 75025, 75026, 75027,
                     75028],
                    dtype='int64'),
         526: Int64Index([34080, 34081, 34082, 34083, 34084, 34085, 34086, 34087, 34088,
                     34089,
                     ...
                     34194, 34195, 34196, 34197, 34198, 34199, 34200, 34201, 34202,
                     34203],
                    dtype='int64', length=124),
         527: Int64Index([49049, 49050, 49051, 49052, 49053, 49054, 49055, 49056, 49057,
                     49058,
                     ...
                     49234, 49235, 49236, 49237, 49238, 49239, 49240, 49241, 49242,
                     49243],
                    dtype='int64', length=195),
         528: Int64Index([52802, 52803, 52804, 52805, 52806, 52807, 52808, 52809, 52810,
                     52811,
                     ...
                     52913, 52914, 52915, 52916, 52917, 52918, 52919, 52920, 52921,
                     52922],
                    dtype='int64', length=121),
         529: Int64Index([69735, 69736, 69737, 69738, 69739, 69740, 69741, 69742, 69743,
                     69744, 69745, 69746, 69747, 69748, 69749, 69750, 69751, 69752,
                     69753, 69754, 69755, 69756, 69757, 69758, 69759, 69760, 69761,
                     69762, 69763, 69764, 69765, 69766, 69767, 69768, 69769, 69770,
                     69771, 69772, 69773, 69774, 69775, 69776, 69777, 69778, 69779,
                     69780, 69781, 69782, 69783, 69784, 69785, 69786, 69787, 69788,
                     69789, 69790, 69791, 69792, 69793, 69794, 69795, 69796, 69797,
                     69798, 69799, 69800, 69801, 69802, 69803, 69804, 69805, 69806,
                     69807, 69808, 69809, 69810, 69811, 69812, 69813, 69814, 69815,
                     69816, 69817, 69818, 69819, 69820, 69821, 69822, 69823, 69824,
                     69825, 69826, 69827],
                    dtype='int64'),
         530: Int64Index([60448, 60449, 60450, 60451, 60452, 60453, 60454, 60455, 60456,
                     60457, 60458, 60459, 60460, 60461, 60462, 60463, 60464, 60465,
                     60466, 60467, 60468, 60469, 60470, 60471, 60472, 60473, 60474,
                     60475, 60476, 60477, 60478, 60479, 60480, 60481, 60482, 60483,
                     60484, 60485, 60486, 60487, 60488, 60489, 60490, 60491, 60492,
                     60493, 60494, 60495, 60496, 60497, 60498, 60499, 60500, 60501,
                     60502, 60503, 60504, 60505, 60506, 60507, 60508, 60509, 60510,
                     60511, 60512, 60513, 60514, 60515, 60516, 60517, 60518, 60519,
                     60520, 60521, 60522, 60523, 60524, 60525, 60526, 60527],
                    dtype='int64'),
         531: Int64Index([77783, 77784, 77785, 77786, 77787, 77788, 77789, 77790, 77791,
                     77792,
                     ...
                     77902, 77903, 77904, 77905, 77906, 77907, 77908, 77909, 77910,
                     77911],
                    dtype='int64', length=129),
         532: Int64Index([74853, 74854, 74855, 74856, 74857, 74858, 74859, 74860, 74861,
                     74862, 74863, 74864, 74865, 74866, 74867, 74868, 74869, 74870,
                     74871, 74872, 74873, 74874],
                    dtype='int64'),
         533: Int64Index([77912, 77913, 77914, 77915, 77916, 77917, 77918, 77919, 77920,
                     77921, 77922, 77923, 77924, 77925, 77926],
                    dtype='int64'),
         534: Int64Index([76096, 76097, 76098, 76099, 76100, 76101, 76102, 76103, 76104,
                     76105, 76106, 76107, 76108],
                    dtype='int64'),
         535: Int64Index([77661, 77662, 77663, 77664, 77665, 77666, 77667, 77668, 77669,
                     77670, 77671, 77672, 77673, 77674, 77675, 77676, 77677, 77678,
                     77679, 77680, 77681, 77682, 77683, 77684, 77685, 77686, 77687,
                     77688, 77689, 77690, 77691, 77692, 77693, 77694, 77695, 77696,
                     77697, 77698, 77699, 77700, 77701, 77702, 77703, 77704, 77705,
                     77706, 77707, 77708, 77709, 77710, 77711, 77712, 77713, 77714],
                    dtype='int64'),
         536: Int64Index([76155, 76156, 76157, 76158, 76159, 76160, 76161, 76162, 76163,
                     76164],
                    dtype='int64'),
         537: Int64Index([45616, 45617, 45618, 45619, 45620, 45621, 45622, 45623, 45624,
                     45625, 45626, 45627, 45628, 45629, 45630, 45631, 45632, 45633,
                     45634, 45635, 45636, 45637, 45638, 45639, 45640, 45641, 45642,
                     45643, 45644, 45645],
                    dtype='int64'),
         538: Int64Index([77152, 77153, 77154, 77155, 77156, 77157, 77158, 77159, 77160,
                     77161, 77162, 77163, 77164, 77165, 77166, 77167, 77168, 77169,
                     77170, 77171, 77172, 77173, 77174, 77175, 77176, 77177, 77178,
                     77179, 77180, 77181, 77182, 77183, 77184, 77185, 77186, 77187,
                     77188, 77189, 77190, 77191, 77192, 77193, 77194, 77195, 77196,
                     77197, 77198, 77199, 77200, 77201, 77202, 77203, 77204, 77205,
                     77206, 77207, 77208, 77209, 77210, 77211, 77212, 77213, 77214,
                     77215, 77216, 77217],
                    dtype='int64'),
         539: Int64Index([77927, 77928, 77929, 77930, 77931, 77932, 77933, 77934, 77935,
                     77936, 77937, 77938, 77939, 77940, 77941, 77942, 77943, 77944,
                     77945, 77946, 77947, 77948, 77949, 77950, 77951, 77952, 77953,
                     77954, 77955, 77956, 77957, 77958, 77959, 77960, 77961, 77962,
                     77963, 77964, 77965, 77966, 77967, 77968, 77969, 77970],
                    dtype='int64'),
         540: Int64Index([15603, 15604, 15605, 15606, 15607, 15608, 15609, 15610, 15611,
                     15612, 15613, 15614, 15615, 15616, 15617, 15618, 15619, 15620,
                     15621, 15622, 15623, 15624, 15625, 15626, 15627, 15628, 15629,
                     15630, 15631, 15632, 15633, 15634, 15635, 15636, 15637, 15638,
                     15639, 15640, 15641, 15642, 15643, 15644, 15645],
                    dtype='int64'),
         541: Int64Index([78336, 78337, 78338, 78339, 78340, 78341, 78342, 78343, 78344,
                     78345, 78346, 78347, 78348, 78349, 78350, 78351, 78352, 78353,
                     78354, 78355, 78356, 78357, 78358, 78359, 78360, 78361, 78362,
                     78363, 78364, 78365, 78366, 78367, 78368, 78369, 78370, 78371,
                     78372, 78373, 78374, 78375, 78376, 78377, 78378, 78379, 78380,
                     78381, 78382, 78383, 78384],
                    dtype='int64'),
         542: Int64Index([83519, 83520, 83521, 83522, 83523, 83524, 83525, 83526, 83527,
                     83528, 83529, 83530, 83531, 83532, 83533, 83534, 83535, 83536,
                     83537, 83538, 83539, 83540, 83541, 83542, 83543, 83544, 83545,
                     83546, 83547, 83548, 83549, 83550, 83551, 83552, 83553, 83554,
                     83555, 83556, 83557, 83558, 83559, 83560, 83561, 83562, 83563,
                     83564, 83565, 83566, 83567, 83568, 83569],
                    dtype='int64'),
         543: Int64Index([65052, 65053, 65054, 65055, 65056, 65057, 65058, 65059, 65060,
                     65061, 65062, 65063, 65064, 65065, 65066, 65067, 65068, 65069,
                     65070, 65071, 65072],
                    dtype='int64'),
         544: Int64Index([86400, 86401, 86402, 86403, 86404, 86405, 86406, 86407, 86408,
                     86409, 86410, 86411, 86412, 86413, 86414, 86415, 86416, 86417,
                     86418, 86419, 86420, 86421, 86422, 86423, 86424, 86425, 86426,
                     86427, 86428, 86429, 86430, 86431, 86432, 86433, 86434, 86435,
                     86436, 86437, 86438, 86439, 86440, 86441, 86442, 86443, 86444,
                     86445, 86446, 86447, 86448, 86449, 86450, 86451, 86452, 86453,
                     86454, 86455, 86456, 86457, 86458, 86459, 86460, 86461, 86462,
                     86463, 86464, 86465, 86466, 86467, 86468, 86469, 86470],
                    dtype='int64'),
         545: Int64Index([87446, 87447, 87448, 87449, 87450, 87451, 87452, 87453, 87454,
                     87455, 87456, 87457],
                    dtype='int64'),
         546: Int64Index([11517, 11518, 11519, 11520, 11521, 11522, 11523, 11524, 11525,
                     11526,
                     ...
                     11761, 11762, 11763, 11764, 11765, 11766, 11767, 11768, 11769,
                     11770],
                    dtype='int64', length=254),
         547: Int64Index([95751, 95752, 95753, 95754, 95755, 95756, 95757, 95758, 95759,
                     95760, 95761, 95762, 95763, 95764, 95765, 95766, 95767, 95768,
                     95769, 95770, 95771, 95772, 95773, 95774, 95775, 95776, 95777,
                     95778, 95779, 95780, 95781, 95782, 95783, 95784, 95785, 95786,
                     95787, 95788, 95789, 95790, 95791],
                    dtype='int64'),
         548: Int64Index([95610, 95611, 95612, 95613, 95614, 95615, 95616, 95617, 95618,
                     95619, 95620, 95621],
                    dtype='int64'),
         549: Int64Index([63199, 63200, 63201, 63202, 63203, 63204, 63205, 63206, 63207,
                     63208, 63209, 63210, 63211, 63212, 63213, 63214, 63215, 63216,
                     63217, 63218, 63219, 63220, 63221, 63222, 63223, 63224, 63225,
                     63226, 63227, 63228, 63229, 63230, 63231, 63232, 63233, 63234,
                     63235, 63236, 63237, 63238, 63239, 63240, 63241, 63242, 63243,
                     63244, 63245, 63246, 63247, 63248, 63249, 63250, 63251, 63252,
                     63253, 63254, 63255, 63256, 63257, 63258, 63259, 63260, 63261,
                     63262, 63263, 63264, 63265, 63266, 63267, 63268, 63269, 63270,
                     63271, 63272, 63273, 63274, 63275, 63276, 63277, 63278, 63279,
                     63280, 63281, 63282, 63283, 63284, 63285, 63286, 63287, 63288,
                     63289, 63290],
                    dtype='int64'),
         550: Int64Index([9115, 9116, 9117, 9118, 9119, 9120, 9121, 9122, 9123, 9124,
                     ...
                     9256, 9257, 9258, 9259, 9260, 9261, 9262, 9263, 9264, 9265],
                    dtype='int64', length=151),
         551: Int64Index([87748, 87749, 87750, 87751, 87752, 87753, 87754, 87755, 87756,
                     87757, 87758, 87759, 87760, 87761, 87762, 87763, 87764, 87765,
                     87766, 87767, 87768, 87769, 87770, 87771],
                    dtype='int64'),
         552: Int64Index([81150, 81151, 81152, 81153, 81154, 81155, 81156, 81157, 81158,
                     81159, 81160, 81161, 81162, 81163, 81164, 81165, 81166, 81167,
                     81168, 81169, 81170, 81171, 81172, 81173, 81174, 81175, 81176,
                     81177, 81178, 81179, 81180, 81181, 81182, 81183, 81184, 81185,
                     81186, 81187, 81188, 81189, 81190, 81191, 81192, 81193, 81194],
                    dtype='int64'),
         553: Int64Index([45695, 45696, 45697, 45698, 45699, 45700, 45701, 45702, 45703,
                     45704, 45705, 45706, 45707, 45708, 45709, 45710, 45711, 45712,
                     45713, 45714, 45715, 45716, 45717, 45718, 45719, 45720, 45721,
                     45722, 45723, 45724, 45725, 45726, 45727, 45728, 45729, 45730,
                     45731, 45732, 45733, 45734, 45735, 45736, 45737, 45738, 45739,
                     45740, 45741, 45742, 45743, 45744, 45745, 45746, 45747, 45748,
                     45749, 45750, 45751, 45752, 45753, 45754, 45755, 45756, 45757],
                    dtype='int64'),
         554: Int64Index([9896, 9897, 9898, 9899, 9900, 9901, 9902, 9903, 9904, 9905,
                     ...
                     9988, 9989, 9990, 9991, 9992, 9993, 9994, 9995, 9996, 9997],
                    dtype='int64', length=102),
         555: Int64Index([86365, 86366, 86367, 86368, 86369, 86370, 86371, 86372, 86373,
                     86374],
                    dtype='int64'),
         556: Int64Index([86151, 86152, 86153, 86154, 86155, 86156, 86157, 86158, 86159,
                     86160, 86161, 86162],
                    dtype='int64'),
         557: Int64Index([70951, 70952, 70953, 70954, 70955, 70956, 70957, 70958, 70959,
                     70960, 70961, 70962, 70963, 70964, 70965, 70966, 70967],
                    dtype='int64'),
         558: Int64Index([67255, 67256, 67257, 67258, 67259, 67260, 67261, 67262, 67263,
                     67264, 67265, 67266, 67267, 67268, 67269, 67270, 67271, 67272,
                     67273, 67274, 67275, 67276, 67277, 67278, 67279, 67280, 67281,
                     67282, 67283, 67284, 67285, 67286, 67287, 67288, 67289, 67290,
                     67291, 67292, 67293, 67294, 67295, 67296, 67297, 67298, 67299,
                     67300, 67301, 67302, 67303, 67304, 67305, 67306, 67307, 67308,
                     67309, 67310, 67311, 67312, 67313, 67314, 67315, 67316, 67317,
                     67318, 67319, 67320, 67321, 67322, 67323, 67324],
                    dtype='int64'),
         559: Int64Index([42803, 42804, 42805, 42806, 42807, 42808, 42809, 42810, 42811,
                     42812,
                     ...
                     42930, 42931, 42932, 42933, 42934, 42935, 42936, 42937, 42938,
                     42939],
                    dtype='int64', length=137),
         560: Int64Index([83189, 83190, 83191, 83192, 83193, 83194, 83195, 83196, 83197,
                     83198, 83199, 83200, 83201, 83202, 83203, 83204, 83205, 83206,
                     83207, 83208, 83209, 83210],
                    dtype='int64'),
         561: Int64Index([97302, 97303, 97304, 97305, 97306, 97307, 97308, 97309, 97310,
                     97311, 97312, 97313, 97314, 97315, 97316, 97317, 97318, 97319,
                     97320, 97321, 97322, 97323, 97324, 97325, 97326, 97327, 97328,
                     97329, 97330, 97331, 97332, 97333, 97334, 97335, 97336, 97337,
                     97338, 97339, 97340, 97341, 97342, 97343, 97344, 97345, 97346,
                     97347, 97348, 97349, 97350, 97351, 97352, 97353, 97354, 97355,
                     97356, 97357, 97358, 97359, 97360],
                    dtype='int64'),
         562: Int64Index([90057, 90058, 90059, 90060, 90061, 90062, 90063, 90064, 90065,
                     90066, 90067, 90068, 90069, 90070, 90071, 90072, 90073, 90074,
                     90075, 90076, 90077, 90078, 90079, 90080, 90081, 90082, 90083,
                     90084, 90085, 90086, 90087, 90088, 90089, 90090, 90091, 90092,
                     90093, 90094, 90095, 90096, 90097, 90098, 90099, 90100, 90101,
                     90102, 90103, 90104],
                    dtype='int64'),
         563: Int64Index([91507, 91508, 91509, 91510, 91511, 91512, 91513, 91514, 91515,
                     91516, 91517, 91518, 91519, 91520, 91521, 91522, 91523, 91524,
                     91525, 91526, 91527, 91528, 91529, 91530, 91531, 91532, 91533,
                     91534, 91535],
                    dtype='int64'),
         564: Int64Index([89736, 89737, 89738, 89739, 89740, 89741, 89742, 89743, 89744,
                     89745, 89746, 89747, 89748, 89749, 89750, 89751, 89752, 89753,
                     89754, 89755, 89756, 89757, 89758, 89759, 89760, 89761, 89762],
                    dtype='int64'),
         565: Int64Index([91536, 91537, 91538, 91539, 91540, 91541, 91542, 91543, 91544,
                     91545, 91546, 91547, 91548, 91549, 91550, 91551, 91552, 91553,
                     91554, 91555, 91556, 91557],
                    dtype='int64'),
         566: Int64Index([6682, 6683, 6684, 6685, 6686, 6687, 6688, 6689, 6690, 6691,
                     ...
                     6851, 6852, 6853, 6854, 6855, 6856, 6857, 6858, 6859, 6860],
                    dtype='int64', length=179),
         567: Int64Index([91187, 91188, 91189, 91190, 91191, 91192, 91193, 91194, 91195,
                     91196, 91197, 91198, 91199, 91200, 91201, 91202, 91203, 91204,
                     91205, 91206, 91207, 91208, 91209, 91210, 91211, 91212, 91213,
                     91214, 91215, 91216, 91217, 91218, 91219, 91220, 91221],
                    dtype='int64'),
         568: Int64Index([15096, 15097, 15098, 15099, 15100, 15101, 15102, 15103, 15104,
                     15105,
                     ...
                     15316, 15317, 15318, 15319, 15320, 15321, 15322, 15323, 15324,
                     15325],
                    dtype='int64', length=230),
         569: Int64Index([79178, 79179, 79180, 79181, 79182, 79183, 79184, 79185, 79186,
                     79187, 79188, 79189, 79190, 79191, 79192, 79193, 79194, 79195,
                     79196, 79197, 79198, 79199, 79200, 79201, 79202, 79203, 79204,
                     79205, 79206, 79207, 79208, 79209, 79210, 79211, 79212, 79213,
                     79214, 79215, 79216, 79217, 79218, 79219, 79220, 79221, 79222,
                     79223, 79224, 79225, 79226, 79227, 79228, 79229, 79230, 79231,
                     79232, 79233, 79234, 79235, 79236, 79237, 79238, 79239, 79240,
                     79241, 79242, 79243, 79244],
                    dtype='int64'),
         570: Int64Index([83008, 83009, 83010, 83011, 83012, 83013, 83014, 83015, 83016,
                     83017, 83018, 83019, 83020, 83021, 83022, 83023, 83024, 83025,
                     83026, 83027, 83028, 83029, 83030, 83031, 83032, 83033, 83034,
                     83035, 83036, 83037, 83038, 83039, 83040, 83041, 83042, 83043,
                     83044, 83045, 83046, 83047, 83048, 83049, 83050, 83051, 83052,
                     83053, 83054, 83055, 83056, 83057],
                    dtype='int64'),
         571: Int64Index([90952, 90953, 90954, 90955, 90956, 90957, 90958, 90959, 90960,
                     90961, 90962, 90963, 90964, 90965, 90966, 90967, 90968, 90969,
                     90970, 90971, 90972, 90973, 90974, 90975, 90976, 90977, 90978,
                     90979],
                    dtype='int64'),
         572: Int64Index([90980, 90981, 90982, 90983, 90984, 90985, 90986, 90987, 90988,
                     90989, 90990, 90991, 90992, 90993, 90994, 90995, 90996, 90997,
                     90998, 90999, 91000, 91001, 91002, 91003, 91004, 91005, 91006,
                     91007, 91008],
                    dtype='int64'),
         573: Int64Index([91814, 91815, 91816, 91817, 91818, 91819, 91820, 91821, 91822,
                     91823, 91824, 91825, 91826, 91827, 91828, 91829, 91830, 91831,
                     91832, 91833, 91834, 91835, 91836, 91837, 91838, 91839, 91840,
                     91841, 91842, 91843, 91844, 91845, 91846],
                    dtype='int64'),
         574: Int64Index([80825, 80826, 80827, 80828, 80829, 80830, 80831, 80832, 80833,
                     80834, 80835, 80836, 80837, 80838, 80839],
                    dtype='int64'),
         575: Int64Index([88211, 88212, 88213, 88214, 88215, 88216, 88217, 88218, 88219,
                     88220, 88221, 88222, 88223, 88224, 88225, 88226, 88227, 88228,
                     88229, 88230, 88231, 88232, 88233, 88234, 88235, 88236, 88237,
                     88238, 88239, 88240, 88241, 88242, 88243, 88244, 88245, 88246,
                     88247, 88248, 88249, 88250, 88251, 88252, 88253, 88254],
                    dtype='int64'),
         576: Int64Index([83426, 83427, 83428, 83429, 83430, 83431, 83432, 83433, 83434,
                     83435, 83436, 83437, 83438, 83439, 83440, 83441, 83442, 83443,
                     83444, 83445, 83446, 83447, 83448, 83449, 83450, 83451, 83452,
                     83453, 83454, 83455, 83456, 83457, 83458, 83459, 83460, 83461,
                     83462, 83463, 83464, 83465, 83466, 83467, 83468, 83469, 83470,
                     83471, 83472, 83473, 83474, 83475, 83476, 83477, 83478, 83479,
                     83480, 83481, 83482, 83483, 83484, 83485, 83486, 83487, 83488,
                     83489, 83490, 83491, 83492, 83493, 83494, 83495, 83496, 83497,
                     83498, 83499, 83500, 83501, 83502, 83503, 83504, 83505, 83506,
                     83507, 83508, 83509, 83510, 83511, 83512, 83513, 83514, 83515,
                     83516, 83517, 83518],
                    dtype='int64'),
         577: Int64Index([80553, 80554, 80555, 80556, 80557, 80558, 80559, 80560, 80561,
                     80562, 80563, 80564, 80565, 80566, 80567, 80568, 80569, 80570,
                     80571, 80572, 80573, 80574, 80575, 80576, 80577, 80578, 80579,
                     80580, 80581, 80582, 80583, 80584, 80585, 80586, 80587, 80588,
                     80589, 80590, 80591, 80592, 80593],
                    dtype='int64'),
         578: Int64Index([83058, 83059, 83060, 83061, 83062, 83063, 83064, 83065, 83066,
                     83067, 83068, 83069, 83070, 83071, 83072, 83073, 83074, 83075,
                     83076, 83077, 83078, 83079, 83080, 83081, 83082, 83083, 83084,
                     83085, 83086, 83087, 83088, 83089, 83090, 83091, 83092, 83093,
                     83094, 83095, 83096, 83097, 83098, 83099, 83100, 83101, 83102,
                     83103, 83104, 83105, 83106, 83107, 83108, 83109, 83110, 83111,
                     83112, 83113, 83114, 83115, 83116, 83117, 83118, 83119, 83120,
                     83121, 83122, 83123, 83124, 83125, 83126, 83127, 83128, 83129,
                     83130, 83131, 83132, 83133, 83134, 83135, 83136, 83137, 83138,
                     83139, 83140, 83141, 83142, 83143, 83144, 83145, 83146, 83147,
                     83148, 83149],
                    dtype='int64'),
         579: Int64Index([94948, 94949, 94950, 94951, 94952, 94953, 94954, 94955, 94956,
                     94957, 94958, 94959, 94960, 94961, 94962, 94963, 94964, 94965,
                     94966],
                    dtype='int64'),
         580: Int64Index([1525, 1526, 1527, 1528, 1529, 1530, 1531, 1532, 1533, 1534, 1535,
                     1536, 1537, 1538, 1539, 1540, 1541, 1542, 1543, 1544, 1545, 1546,
                     1547, 1548, 1549, 1550, 1551, 1552, 1553, 1554, 1555, 1556],
                    dtype='int64'),
         581: Int64Index([45351, 45352, 45353, 45354, 45355, 45356, 45357, 45358, 45359,
                     45360, 45361, 45362, 45363, 45364, 45365, 45366, 45367, 45368,
                     45369, 45370, 45371, 45372, 45373, 45374, 45375, 45376, 45377,
                     45378, 45379, 45380, 45381, 45382, 45383, 45384, 45385, 45386,
                     45387, 45388, 45389, 45390, 45391, 45392, 45393, 45394, 45395,
                     45396, 45397, 45398, 45399, 45400, 45401, 45402, 45403, 45404,
                     45405, 45406, 45407, 45408, 45409],
                    dtype='int64'),
         582: Int64Index([71901, 71902, 71903, 71904, 71905, 71906, 71907, 71908, 71909,
                     71910,
                     ...
                     72059, 72060, 72061, 72062, 72063, 72064, 72065, 72066, 72067,
                     72068],
                    dtype='int64', length=168),
         583: Int64Index([85234, 85235, 85236, 85237, 85238, 85239, 85240, 85241, 85242,
                     85243, 85244, 85245, 85246, 85247, 85248, 85249, 85250, 85251,
                     85252, 85253, 85254, 85255, 85256, 85257, 85258, 85259, 85260,
                     85261, 85262, 85263, 85264, 85265, 85266, 85267, 85268, 85269,
                     85270],
                    dtype='int64'),
         584: Int64Index([43208, 43209, 43210, 43211, 43212, 43213, 43214, 43215, 43216,
                     43217, 43218, 43219, 43220, 43221, 43222, 43223, 43224, 43225,
                     43226, 43227, 43228, 43229, 43230, 43231, 43232, 43233, 43234,
                     43235, 43236, 43237, 43238, 43239, 43240, 43241, 43242, 43243,
                     43244, 43245, 43246, 43247, 43248, 43249, 43250, 43251, 43252,
                     43253, 43254, 43255, 43256, 43257, 43258, 43259, 43260, 43261,
                     43262, 43263, 43264, 43265, 43266, 43267, 43268, 43269, 43270,
                     43271, 43272, 43273, 43274, 43275, 43276, 43277, 43278, 43279,
                     43280, 43281, 43282, 43283, 43284, 43285, 43286],
                    dtype='int64'),
         585: Int64Index([97752, 97753, 97754, 97755, 97756, 97757, 97758, 97759, 97760,
                     97761, 97762, 97763, 97764, 97765, 97766, 97767, 97768, 97769,
                     97770, 97771, 97772, 97773, 97774, 97775, 97776, 97777, 97778,
                     97779, 97780, 97781, 97782, 97783, 97784, 97785, 97786, 97787,
                     97788, 97789, 97790],
                    dtype='int64'),
         586: Int64Index([82868, 82869, 82870, 82871, 82872, 82873, 82874, 82875, 82876,
                     82877, 82878, 82879, 82880, 82881, 82882, 82883, 82884, 82885,
                     82886, 82887, 82888, 82889, 82890, 82891, 82892, 82893, 82894,
                     82895, 82896, 82897, 82898, 82899, 82900, 82901],
                    dtype='int64'),
         587: Int64Index([97725, 97726, 97727, 97728, 97729, 97730, 97731, 97732, 97733,
                     97734, 97735, 97736, 97737, 97738],
                    dtype='int64'),
         588: Int64Index([7682, 7683, 7684, 7685, 7686, 7687, 7688, 7689, 7690, 7691,
                     ...
                     7874, 7875, 7876, 7877, 7878, 7879, 7880, 7881, 7882, 7883],
                    dtype='int64', length=202),
         589: Int64Index([92675, 92676, 92677, 92678, 92679, 92680, 92681, 92682, 92683,
                     92684, 92685, 92686, 92687, 92688, 92689, 92690, 92691, 92692,
                     92693, 92694, 92695, 92696, 92697, 92698, 92699, 92700, 92701,
                     92702, 92703, 92704, 92705, 92706, 92707, 92708, 92709, 92710,
                     92711, 92712, 92713, 92714, 92715, 92716, 92717],
                    dtype='int64'),
         590: Int64Index([95397, 95398, 95399, 95400, 95401, 95402, 95403, 95404, 95405,
                     95406, 95407, 95408, 95409, 95410, 95411, 95412, 95413, 95414],
                    dtype='int64'),
         591: Int64Index([8613, 8614, 8615, 8616, 8617, 8618, 8619, 8620, 8621, 8622,
                     ...
                     8781, 8782, 8783, 8784, 8785, 8786, 8787, 8788, 8789, 8790],
                    dtype='int64', length=178),
         592: Int64Index([91743, 91744, 91745, 91746, 91747, 91748, 91749, 91750, 91751], dtype='int64'),
         593: Int64Index([97047, 97048, 97049, 97050, 97051, 97052, 97053, 97054, 97055,
                     97056, 97057, 97058],
                    dtype='int64'),
         594: Int64Index([97816, 97817, 97818, 97819, 97820], dtype='int64'),
         595: Int64Index([14603, 14604, 14605, 14606, 14607, 14608, 14609, 14610, 14611,
                     14612, 14613, 14614, 14615, 14616, 14617, 14618, 14619, 14620,
                     14621, 14622, 14623, 14624, 14625, 14626, 14627, 14628, 14629,
                     14630, 14631, 14632, 14633, 14634, 14635, 14636, 14637, 14638,
                     14639, 14640, 14641, 14642, 14643, 14644, 14645, 14646, 14647,
                     14648, 14649, 14650, 14651, 14652, 14653, 14654, 14655, 14656,
                     14657, 14658, 14659, 14660, 14661, 14662, 14663, 14664, 14665,
                     14666],
                    dtype='int64'),
         596: Int64Index([13415, 13416, 13417, 13418, 13419, 13420, 13421, 13422, 13423,
                     13424,
                     ...
                     13532, 13533, 13534, 13535, 13536, 13537, 13538, 13539, 13540,
                     13541],
                    dtype='int64', length=127),
         597: Int64Index([73403, 73404, 73405, 73406, 73407, 73408, 73409, 73410, 73411,
                     73412,
                     ...
                     73599, 73600, 73601, 73602, 73603, 73604, 73605, 73606, 73607,
                     73608],
                    dtype='int64', length=206),
         598: Int64Index([97038, 97039, 97040, 97041], dtype='int64'),
         599: Int64Index([97739], dtype='int64'),
         600: Int64Index([97741, 97742], dtype='int64'),
         601: Int64Index([92336, 92337, 92338, 92339, 92340, 92341, 92342, 92343, 92344,
                     92345, 92346, 92347, 92348, 92349, 92350, 92351, 92352, 92353,
                     92354, 92355],
                    dtype='int64'),
         602: Int64Index([70751, 70752, 70753, 70754, 70755, 70756, 70757, 70758, 70759,
                     70760, 70761, 70762, 70763, 70764, 70765, 70766, 70767, 70768,
                     70769, 70770, 70771, 70772, 70773, 70774, 70775, 70776, 70777,
                     70778, 70779, 70780, 70781, 70782, 70783, 70784, 70785, 70786,
                     70787, 70788, 70789, 70790, 70791, 70792, 70793, 70794, 70795,
                     70796, 70797, 70798, 70799, 70800],
                    dtype='int64'),
         603: Int64Index([60528, 60529, 60530, 60531, 60532, 60533, 60534, 60535, 60536,
                     60537,
                     ...
                     60727, 60728, 60729, 60730, 60731, 60732, 60733, 60734, 60735,
                     60736],
                    dtype='int64', length=209),
         604: Int64Index([61134, 61135, 61136, 61137, 61138, 61139, 61140, 61141, 61142,
                     61143, 61144, 61145, 61146, 61147, 61148, 61149, 61150, 61151,
                     61152, 61153, 61154, 61155, 61156, 61157, 61158, 61159, 61160,
                     61161, 61162, 61163, 61164, 61165, 61166, 61167, 61168, 61169,
                     61170, 61171, 61172, 61173, 61174, 61175, 61176, 61177, 61178,
                     61179, 61180, 61181, 61182, 61183, 61184, 61185, 61186, 61187,
                     61188, 61189, 61190, 61191, 61192, 61193, 61194, 61195, 61196,
                     61197, 61198, 61199, 61200, 61201, 61202, 61203, 61204, 61205,
                     61206, 61207, 61208, 61209, 61210, 61211, 61212, 61213, 61214],
                    dtype='int64'),
         605: Int64Index([78521, 78522, 78523, 78524, 78525, 78526, 78527, 78528, 78529,
                     78530, 78531, 78532, 78533, 78534, 78535, 78536, 78537, 78538,
                     78539, 78540, 78541, 78542, 78543, 78544, 78545, 78546, 78547,
                     78548, 78549, 78550, 78551],
                    dtype='int64'),
         606: Int64Index([93480, 93481, 93482, 93483, 93484, 93485, 93486, 93487, 93488,
                     93489, 93490, 93491, 93492, 93493, 93494, 93495, 93496, 93497,
                     93498, 93499, 93500, 93501, 93502, 93503, 93504, 93505, 93506,
                     93507, 93508, 93509, 93510, 93511, 93512, 93513, 93514, 93515,
                     93516, 93517, 93518, 93519, 93520, 93521, 93522, 93523, 93524,
                     93525, 93526, 93527, 93528, 93529, 93530, 93531, 93532, 93533,
                     93534, 93535, 93536, 93537, 93538, 93539, 93540, 93541, 93542,
                     93543, 93544, 93545],
                    dtype='int64'),
         607: Int64Index([93645, 93646, 93647, 93648, 93649, 93650, 93651, 93652, 93653,
                     93654, 93655, 93656, 93657, 93658, 93659, 93660, 93661, 93662,
                     93663, 93664, 93665, 93666, 93667, 93668, 93669, 93670, 93671,
                     93672, 93673, 93674, 93675, 93676, 93677, 93678, 93679, 93680,
                     93681, 93682, 93683, 93684, 93685, 93686, 93687, 93688, 93689,
                     93690, 93691, 93692, 93693, 93694, 93695, 93696, 93697, 93698,
                     93699, 93700, 93701, 93702, 93703, 93704, 93705, 93706, 93707,
                     93708, 93709, 93710],
                    dtype='int64'),
         608: Int64Index([93052, 93053, 93054, 93055, 93056, 93057, 93058, 93059, 93060,
                     93061, 93062, 93063, 93064, 93065, 93066, 93067, 93068, 93069,
                     93070, 93071, 93072, 93073, 93074, 93075, 93076, 93077, 93078,
                     93079, 93080, 93081],
                    dtype='int64'),
         609: Int64Index([50889, 50890, 50891, 50892, 50893, 50894, 50895, 50896, 50897,
                     50898, 50899, 50900, 50901, 50902, 50903, 50904, 50905, 50906,
                     50907, 50908, 50909, 50910, 50911, 50912, 50913, 50914, 50915,
                     50916, 50917, 50918, 50919, 50920, 50921, 50922, 50923, 50924,
                     50925, 50926, 50927, 50928, 50929, 50930, 50931, 50932, 50933,
                     50934, 50935, 50936, 50937, 50938, 50939, 50940, 50941, 50942,
                     50943, 50944, 50945, 50946, 50947, 50948],
                    dtype='int64'),
         610: Int64Index([70134, 70135, 70136, 70137, 70138, 70139, 70140, 70141, 70142,
                     70143, 70144, 70145, 70146, 70147, 70148, 70149, 70150, 70151,
                     70152, 70153, 70154, 70155, 70156, 70157, 70158, 70159, 70160,
                     70161, 70162, 70163, 70164, 70165, 70166, 70167, 70168, 70169,
                     70170, 70171, 70172, 70173, 70174],
                    dtype='int64'),
         611: Int64Index([93919, 93920, 93921, 93922, 93923, 93924, 93925, 93926, 93927,
                     93928, 93929, 93930, 93931, 93932, 93933, 93934, 93935, 93936,
                     93937, 93938, 93939, 93940, 93941, 93942, 93943, 93944, 93945,
                     93946, 93947, 93948, 93949, 93950, 93951, 93952, 93953, 93954,
                     93955, 93956, 93957, 93958],
                    dtype='int64'),
         612: Int64Index([91907, 91908, 91909, 91910, 91911, 91912, 91913, 91914, 91915,
                     91916, 91917, 91918, 91919, 91920, 91921, 91922, 91923, 91924,
                     91925, 91926, 91927, 91928, 91929, 91930, 91931, 91932, 91933,
                     91934, 91935, 91936, 91937, 91938, 91939, 91940],
                    dtype='int64'),
         613: Int64Index([93426, 93427, 93428, 93429, 93430, 93431, 93432, 93433, 93434,
                     93435, 93436, 93437, 93438, 93439, 93440, 93441, 93442, 93443,
                     93444, 93445, 93446, 93447, 93448, 93449, 93450, 93451, 93452],
                    dtype='int64'),
         614: Int64Index([92064, 92065, 92066, 92067, 92068, 92069, 92070, 92071, 92072,
                     92073, 92074, 92075, 92076, 92077, 92078, 92079, 92080, 92081,
                     92082, 92083, 92084, 92085, 92086, 92087, 92088, 92089, 92090,
                     92091, 92092, 92093, 92094, 92095, 92096, 92097, 92098, 92099,
                     92100, 92101, 92102, 92103, 92104, 92105, 92106, 92107, 92108,
                     92109, 92110, 92111, 92112, 92113, 92114],
                    dtype='int64'),
         615: Int64Index([89971, 89972, 89973, 89974, 89975, 89976, 89977, 89978, 89979,
                     89980, 89981, 89982, 89983, 89984, 89985, 89986, 89987, 89988,
                     89989, 89990, 89991, 89992, 89993, 89994, 89995, 89996, 89997,
                     89998, 89999, 90000, 90001, 90002, 90003, 90004, 90005, 90006,
                     90007, 90008, 90009, 90010, 90011, 90012, 90013, 90014, 90015,
                     90016, 90017, 90018, 90019, 90020, 90021, 90022, 90023, 90024,
                     90025, 90026, 90027, 90028, 90029],
                    dtype='int64'),
         616: Int64Index([88295, 88296, 88297, 88298, 88299, 88300, 88301, 88302, 88303,
                     88304, 88305, 88306, 88307, 88308, 88309, 88310, 88311, 88312,
                     88313, 88314, 88315, 88316, 88317, 88318, 88319, 88320, 88321,
                     88322, 88323, 88324, 88325, 88326, 88327, 88328, 88329, 88330,
                     88331, 88332, 88333, 88334, 88335, 88336, 88337, 88338, 88339,
                     88340, 88341, 88342, 88343, 88344, 88345, 88346, 88347, 88348,
                     88349, 88350, 88351, 88352, 88353, 88354, 88355, 88356, 88357,
                     88358],
                    dtype='int64'),
         617: Int64Index([92115, 92116, 92117, 92118, 92119, 92120, 92121, 92122, 92123,
                     92124, 92125, 92126, 92127, 92128, 92129, 92130, 92131, 92132],
                    dtype='int64'),
         618: Int64Index([92133, 92134, 92135, 92136, 92137, 92138, 92139, 92140, 92141,
                     92142, 92143, 92144, 92145, 92146, 92147, 92148, 92149, 92150],
                    dtype='int64'),
         619: Int64Index([88502, 88503, 88504, 88505, 88506, 88507, 88508, 88509, 88510,
                     88511, 88512, 88513, 88514, 88515, 88516, 88517, 88518, 88519,
                     88520, 88521, 88522, 88523, 88524, 88525, 88526, 88527, 88528,
                     88529, 88530, 88531, 88532, 88533, 88534, 88535, 88536, 88537,
                     88538, 88539, 88540, 88541, 88542, 88543, 88544, 88545, 88546,
                     88547, 88548, 88549, 88550, 88551, 88552, 88553, 88554, 88555,
                     88556, 88557, 88558, 88559, 88560, 88561, 88562, 88563, 88564,
                     88565],
                    dtype='int64'),
         620: Int64Index([85947, 85948, 85949, 85950, 85951, 85952, 85953, 85954, 85955,
                     85956, 85957, 85958, 85959, 85960, 85961, 85962, 85963, 85964,
                     85965, 85966, 85967, 85968, 85969, 85970, 85971, 85972, 85973,
                     85974, 85975, 85976, 85977, 85978, 85979, 85980, 85981, 85982,
                     85983, 85984, 85985, 85986, 85987, 85988, 85989],
                    dtype='int64'),
         621: Int64Index([97714, 97715, 97716, 97717, 97718, 97719, 97720, 97721, 97722,
                     97723, 97724],
                    dtype='int64'),
         622: Int64Index([84496, 84497, 84498, 84499, 84500, 84501, 84502, 84503, 84504,
                     84505, 84506, 84507, 84508, 84509, 84510, 84511, 84512, 84513,
                     84514, 84515, 84516, 84517, 84518, 84519, 84520, 84521, 84522,
                     84523, 84524, 84525, 84526, 84527, 84528, 84529, 84530, 84531,
                     84532, 84533, 84534],
                    dtype='int64'),
         623: Int64Index([90541, 90542, 90543, 90544, 90545, 90546, 90547, 90548, 90549,
                     90550, 90551, 90552, 90553, 90554, 90555, 90556, 90557, 90558,
                     90559, 90560, 90561, 90562, 90563, 90564, 90565, 90566, 90567,
                     90568, 90569, 90570, 90571, 90572, 90573, 90574, 90575, 90576,
                     90577, 90578, 90579],
                    dtype='int64'),
         624: Int64Index([90798, 90799, 90800, 90801, 90802, 90803, 90804, 90805, 90806,
                     90807, 90808, 90809, 90810, 90811, 90812, 90813, 90814, 90815,
                     90816, 90817, 90818, 90819],
                    dtype='int64'),
         625: Int64Index([56632, 56633, 56634, 56635, 56636, 56637, 56638, 56639, 56640,
                     56641, 56642, 56643, 56644, 56645, 56646, 56647, 56648, 56649,
                     56650, 56651, 56652, 56653, 56654, 56655, 56656, 56657, 56658,
                     56659, 56660, 56661, 56662, 56663, 56664, 56665, 56666, 56667,
                     56668, 56669, 56670, 56671, 56672, 56673, 56674, 56675, 56676,
                     56677, 56678, 56679, 56680, 56681, 56682, 56683, 56684, 56685,
                     56686, 56687, 56688, 56689, 56690, 56691, 56692, 56693, 56694,
                     56695, 56696, 56697, 56698, 56699, 56700, 56701, 56702, 56703,
                     56704, 56705, 56706, 56707, 56708, 56709, 56710, 56711, 56712,
                     56713],
                    dtype='int64'),
         626: Int64Index([91963, 91964, 91965, 91966], dtype='int64'),
         627: Int64Index([90253, 90254, 90255, 90256, 90257, 90258, 90259, 90260, 90261,
                     90262, 90263, 90264, 90265, 90266, 90267, 90268, 90269, 90270,
                     90271, 90272, 90273, 90274, 90275, 90276, 90277, 90278, 90279,
                     90280, 90281, 90282, 90283, 90284, 90285, 90286, 90287, 90288,
                     90289, 90290, 90291, 90292, 90293, 90294, 90295, 90296, 90297,
                     90298, 90299, 90300, 90301, 90302, 90303, 90304, 90305, 90306,
                     90307, 90308, 90309, 90310, 90311, 90312, 90313, 90314, 90315,
                     90316, 90317, 90318, 90319, 90320, 90321, 90322, 90323, 90324,
                     90325, 90326, 90327],
                    dtype='int64'),
         628: Int64Index([44364, 44365, 44366, 44367, 44368, 44369, 44370, 44371, 44372,
                     44373,
                     ...
                     44523, 44524, 44525, 44526, 44527, 44528, 44529, 44530, 44531,
                     44532],
                    dtype='int64', length=169),
         629: Int64Index([49613, 49614, 49615, 49616, 49617, 49618, 49619, 49620, 49621,
                     49622, 49623, 49624, 49625, 49626, 49627, 49628, 49629, 49630,
                     49631, 49632, 49633, 49634, 49635, 49636, 49637, 49638, 49639,
                     49640, 49641, 49642, 49643, 49644, 49645, 49646, 49647, 49648,
                     49649, 49650, 49651, 49652, 49653, 49654, 49655, 49656, 49657,
                     49658, 49659, 49660, 49661, 49662, 49663, 49664, 49665, 49666,
                     49667, 49668, 49669, 49670, 49671, 49672, 49673, 49674, 49675,
                     49676, 49677, 49678, 49679, 49680, 49681, 49682, 49683, 49684,
                     49685, 49686, 49687, 49688, 49689],
                    dtype='int64'),
         630: Int64Index([92833, 92834, 92835, 92836, 92837, 92838, 92839, 92840, 92841,
                     92842, 92843, 92844, 92845, 92846, 92847, 92848, 92849, 92850,
                     92851, 92852, 92853, 92854, 92855, 92856, 92857, 92858, 92859,
                     92860, 92861, 92862, 92863],
                    dtype='int64'),
         631: Int64Index([41700, 41701, 41702, 41703, 41704, 41705, 41706, 41707, 41708,
                     41709,
                     ...
                     41809, 41810, 41811, 41812, 41813, 41814, 41815, 41816, 41817,
                     41818],
                    dtype='int64', length=119),
         632: Int64Index([85619, 85620, 85621, 85622, 85623, 85624, 85625, 85626, 85627,
                     85628, 85629, 85630, 85631, 85632, 85633, 85634, 85635, 85636,
                     85637, 85638, 85639, 85640, 85641, 85642, 85643, 85644, 85645,
                     85646, 85647, 85648, 85649, 85650, 85651, 85652, 85653, 85654,
                     85655, 85656, 85657, 85658, 85659, 85660, 85661, 85662, 85663,
                     85664, 85665, 85666, 85667, 85668, 85669, 85670, 85671, 85672,
                     85673, 85674, 85675, 85676],
                    dtype='int64'),
         633: Int64Index([90603, 90604, 90605, 90606, 90607, 90608, 90609, 90610, 90611,
                     90612, 90613, 90614, 90615, 90616, 90617, 90618, 90619, 90620,
                     90621, 90622, 90623, 90624, 90625, 90626, 90627, 90628, 90629,
                     90630, 90631, 90632, 90633, 90634, 90635, 90636, 90637, 90638,
                     90639, 90640, 90641, 90642, 90643, 90644, 90645, 90646, 90647,
                     90648, 90649, 90650, 90651, 90652, 90653, 90654, 90655, 90656,
                     90657, 90658, 90659, 90660, 90661, 90662, 90663, 90664, 90665,
                     90666, 90667, 90668, 90669, 90670, 90671],
                    dtype='int64'),
         634: Int64Index([90198, 90199, 90200, 90201, 90202, 90203, 90204, 90205, 90206,
                     90207, 90208, 90209, 90210, 90211, 90212, 90213, 90214, 90215,
                     90216, 90217, 90218, 90219, 90220, 90221],
                    dtype='int64'),
         635: Int64Index([94030, 94031, 94032, 94033, 94034, 94035, 94036, 94037, 94038,
                     94039, 94040, 94041, 94042, 94043, 94044, 94045, 94046, 94047,
                     94048, 94049, 94050, 94051, 94052],
                    dtype='int64'),
         636: Int64Index([28867, 28868, 28869, 28870, 28871, 28872, 28873, 28874, 28875,
                     28876, 28877, 28878, 28879, 28880, 28881, 28882, 28883, 28884,
                     28885, 28886, 28887, 28888, 28889, 28890, 28891, 28892, 28893,
                     28894, 28895, 28896, 28897, 28898, 28899, 28900, 28901, 28902,
                     28903, 28904, 28905, 28906, 28907, 28908, 28909, 28910, 28911,
                     28912, 28913, 28914, 28915, 28916, 28917, 28918, 28919, 28920,
                     28921, 28922, 28923, 28924, 28925, 28926, 28927, 28928, 28929,
                     28930, 28931, 28932, 28933, 28934, 28935, 28936, 28937, 28938,
                     28939, 28940, 28941, 28942, 28943, 28944, 28945, 28946, 28947,
                     28948, 28949, 28950, 28951, 28952, 28953, 28954, 28955, 28956,
                     28957],
                    dtype='int64'),
         637: Int64Index([95127, 95128, 95129, 95130, 95131, 95132, 95133, 95134, 95135,
                     95136, 95137, 95138, 95139, 95140, 95141, 95142, 95143, 95144,
                     95145, 95146, 95147, 95148, 95149, 95150, 95151, 95152, 95153,
                     95154, 95155, 95156, 95157, 95158, 95159, 95160, 95161, 95162,
                     95163, 95164],
                    dtype='int64'),
         638: Int64Index([70467, 70468, 70469, 70470, 70471, 70472, 70473, 70474, 70475,
                     70476, 70477, 70478, 70479, 70480, 70481, 70482, 70483, 70484,
                     70485, 70486, 70487, 70488, 70489, 70490, 70491, 70492, 70493,
                     70494, 70495, 70496, 70497, 70498, 70499, 70500, 70501, 70502,
                     70503, 70504, 70505, 70506, 70507, 70508, 70509, 70510],
                    dtype='int64'),
         639: Int64Index([97821, 97822, 97823, 97824, 97825, 97826, 97827, 97828, 97829,
                     97830, 97831, 97832, 97833, 97834, 97835, 97836, 97837, 97838,
                     97839, 97840, 97841, 97842, 97843, 97844, 97845, 97846, 97847,
                     97848, 97849, 97850, 97851, 97852, 97853, 97854, 97855, 97856,
                     97857, 97858, 97859, 97860],
                    dtype='int64'),
         640: Int64Index([80848, 80849, 80850, 80851, 80852, 80853, 80854, 80855, 80856,
                     80857, 80858, 80859, 80860, 80861, 80862, 80863, 80864, 80865,
                     80866, 80867, 80868, 80869, 80870, 80871, 80872, 80873, 80874,
                     80875, 80876, 80877, 80878, 80879, 80880, 80881, 80882, 80883,
                     80884, 80885, 80886, 80887, 80888, 80889, 80890, 80891, 80892,
                     80893, 80894, 80895, 80896, 80897, 80898, 80899, 80900, 80901,
                     80902, 80903, 80904, 80905, 80906, 80907, 80908, 80909, 80910,
                     80911, 80912, 80913, 80914, 80915, 80916, 80917, 80918, 80919,
                     80920, 80921, 80922, 80923, 80924, 80925, 80926, 80927, 80928,
                     80929],
                    dtype='int64'),
         641: Int64Index([93959, 93960, 93961, 93962, 93963, 93964, 93965, 93966, 93967,
                     93968, 93969, 93970, 93971, 93972, 93973, 93974, 93975, 93976,
                     93977, 93978, 93979, 93980, 93981, 93982, 93983, 93984, 93985,
                     93986, 93987, 93988, 93989, 93990, 93991],
                    dtype='int64'),
         642: Int64Index([64801, 64802, 64803, 64804, 64805, 64806, 64807, 64808, 64809,
                     64810, 64811, 64812, 64813, 64814, 64815, 64816, 64817, 64818,
                     64819, 64820, 64821, 64822, 64823, 64824, 64825, 64826, 64827,
                     64828, 64829, 64830, 64831, 64832, 64833, 64834, 64835, 64836,
                     64837, 64838, 64839, 64840, 64841, 64842, 64843, 64844, 64845,
                     64846, 64847, 64848, 64849, 64850, 64851, 64852, 64853, 64854,
                     64855, 64856, 64857, 64858, 64859, 64860, 64861, 64862, 64863,
                     64864, 64865, 64866, 64867, 64868, 64869, 64870, 64871, 64872,
                     64873, 64874, 64875, 64876, 64877, 64878, 64879, 64880, 64881,
                     64882, 64883, 64884, 64885, 64886, 64887, 64888, 64889],
                    dtype='int64'),
         643: Int64Index([97710, 97711, 97712, 97713], dtype='int64'),
         644: Int64Index([66678, 66679, 66680, 66681, 66682, 66683, 66684, 66685, 66686,
                     66687, 66688, 66689, 66690, 66691, 66692, 66693, 66694, 66695,
                     66696, 66697, 66698, 66699, 66700, 66701, 66702, 66703, 66704,
                     66705, 66706, 66707, 66708, 66709, 66710, 66711, 66712],
                    dtype='int64'),
         645: Int64Index([94572, 94573, 94574, 94575, 94576, 94577, 94578, 94579, 94580,
                     94581, 94582, 94583, 94584, 94585, 94586, 94587, 94588, 94589,
                     94590, 94591, 94592, 94593, 94594, 94595, 94596, 94597, 94598],
                    dtype='int64'),
         646: Int64Index([93284, 93285, 93286, 93287, 93288, 93289, 93290, 93291, 93292,
                     93293, 93294, 93295, 93296, 93297, 93298, 93299, 93300, 93301,
                     93302, 93303, 93304, 93305, 93306, 93307, 93308, 93309, 93310,
                     93311, 93312, 93313, 93314, 93315, 93316, 93317, 93318, 93319,
                     93320, 93321],
                    dtype='int64'),
         647: Int64Index([67614, 67615, 67616, 67617, 67618, 67619, 67620, 67621, 67622,
                     67623, 67624, 67625, 67626, 67627, 67628, 67629, 67630, 67631,
                     67632, 67633, 67634, 67635, 67636, 67637, 67638, 67639, 67640,
                     67641, 67642, 67643, 67644, 67645, 67646, 67647, 67648, 67649,
                     67650, 67651, 67652, 67653, 67654, 67655, 67656, 67657, 67658,
                     67659, 67660, 67661, 67662, 67663, 67664, 67665, 67666, 67667,
                     67668, 67669, 67670, 67671, 67672, 67673, 67674, 67675, 67676,
                     67677, 67678, 67679, 67680, 67681, 67682, 67683],
                    dtype='int64'),
         648: Int64Index([23508, 23509, 23510, 23511, 23512, 23513, 23514, 23515, 23516,
                     23517, 23518, 23519, 23520, 23521, 23522, 23523, 23524, 23525,
                     23526, 23527, 23528, 23529, 23530, 23531, 23532, 23533, 23534,
                     23535, 23536, 23537, 23538, 23539, 23540, 23541, 23542, 23543,
                     23544, 23545, 23546, 23547, 23548, 23549, 23550, 23551, 23552,
                     23553, 23554, 23555, 23556, 23557, 23558, 23559, 23560, 23561,
                     23562, 23563, 23564, 23565, 23566, 23567, 23568, 23569, 23570,
                     23571, 23572, 23573, 23574],
                    dtype='int64'),
         649: Int64Index([93322, 93323, 93324, 93325, 93326, 93327, 93328, 93329, 93330,
                     93331, 93332, 93333, 93334, 93335, 93336, 93337, 93338, 93339,
                     93340, 93341, 93342, 93343, 93344, 93345, 93346, 93347, 93348,
                     93349, 93350, 93351, 93352, 93353, 93354, 93355, 93356, 93357,
                     93358, 93359, 93360, 93361, 93362, 93363, 93364, 93365, 93366,
                     93367, 93368, 93369, 93370, 93371],
                    dtype='int64'),
         650: Int64Index([54311, 54312, 54313, 54314, 54315, 54316, 54317, 54318, 54319,
                     54320, 54321, 54322, 54323, 54324, 54325, 54326, 54327, 54328,
                     54329, 54330, 54331, 54332, 54333, 54334, 54335, 54336, 54337,
                     54338, 54339, 54340, 54341, 54342, 54343, 54344, 54345, 54346,
                     54347, 54348, 54349, 54350, 54351, 54352, 54353, 54354, 54355,
                     54356, 54357, 54358, 54359, 54360, 54361, 54362, 54363, 54364,
                     54365, 54366, 54367, 54368, 54369, 54370, 54371, 54372, 54373,
                     54374, 54375, 54376, 54377, 54378, 54379, 54380, 54381, 54382],
                    dtype='int64'),
         651: Int64Index([26282, 26283, 26284, 26285, 26286, 26287, 26288, 26289, 26290,
                     26291,
                     ...
                     26443, 26444, 26445, 26446, 26447, 26448, 26449, 26450, 26451,
                     26452],
                    dtype='int64', length=171),
         652: Int64Index([36497, 36498, 36499, 36500, 36501, 36502, 36503, 36504, 36505,
                     36506, 36507, 36508, 36509, 36510, 36511, 36512, 36513, 36514,
                     36515, 36516, 36517, 36518, 36519, 36520, 36521, 36522, 36523,
                     36524, 36525, 36526, 36527, 36528, 36529, 36530, 36531, 36532,
                     36533, 36534, 36535, 36536, 36537, 36538, 36539, 36540, 36541,
                     36542, 36543, 36544, 36545, 36546, 36547, 36548, 36549, 36550,
                     36551, 36552, 36553, 36554, 36555, 36556, 36557, 36558, 36559,
                     36560, 36561, 36562, 36563, 36564, 36565, 36566, 36567, 36568,
                     36569, 36570, 36571, 36572, 36573, 36574, 36575, 36576, 36577,
                     36578, 36579, 36580, 36581, 36582, 36583, 36584, 36585, 36586],
                    dtype='int64'),
         653: Int64Index([89231, 89232, 89233, 89234, 89235, 89236, 89237, 89238, 89239,
                     89240, 89241, 89242, 89243, 89244, 89245, 89246, 89247, 89248,
                     89249, 89250, 89251, 89252, 89253, 89254, 89255, 89256, 89257,
                     89258, 89259, 89260, 89261, 89262, 89263, 89264],
                    dtype='int64'),
         654: Int64Index([66306, 66307, 66308, 66309, 66310, 66311, 66312, 66313, 66314,
                     66315,
                     ...
                     66443, 66444, 66445, 66446, 66447, 66448, 66449, 66450, 66451,
                     66452],
                    dtype='int64', length=147),
         655: Int64Index([455, 456, 457, 458, 459, 460, 461, 462, 463, 464,
                     ...
                     672, 673, 674, 675, 676, 677, 678, 679, 680, 681],
                    dtype='int64', length=227),
         656: Int64Index([94149, 94150, 94151, 94152, 94153, 94154, 94155, 94156, 94157,
                     94158, 94159, 94160, 94161, 94162, 94163, 94164, 94165, 94166,
                     94167, 94168, 94169, 94170, 94171, 94172, 94173, 94174, 94175,
                     94176, 94177, 94178, 94179, 94180, 94181, 94182, 94183, 94184,
                     94185, 94186, 94187, 94188, 94189, 94190, 94191, 94192],
                    dtype='int64'),
         657: Int64Index([65817, 65818, 65819, 65820, 65821, 65822, 65823, 65824, 65825,
                     65826,
                     ...
                     65938, 65939, 65940, 65941, 65942, 65943, 65944, 65945, 65946,
                     65947],
                    dtype='int64', length=131),
         658: Int64Index([81071, 81072, 81073, 81074, 81075, 81076, 81077, 81078, 81079,
                     81080, 81081, 81082, 81083, 81084, 81085, 81086, 81087, 81088,
                     81089, 81090, 81091, 81092, 81093, 81094, 81095, 81096, 81097,
                     81098, 81099, 81100, 81101, 81102, 81103, 81104, 81105, 81106,
                     81107, 81108, 81109, 81110, 81111, 81112, 81113, 81114, 81115,
                     81116, 81117, 81118, 81119, 81120, 81121, 81122, 81123, 81124,
                     81125, 81126, 81127, 81128, 81129, 81130, 81131, 81132, 81133,
                     81134, 81135, 81136, 81137, 81138, 81139, 81140, 81141, 81142,
                     81143, 81144, 81145, 81146, 81147, 81148, 81149],
                    dtype='int64'),
         659: Int64Index([68959, 68960, 68961, 68962, 68963, 68964, 68965, 68966, 68967,
                     68968,
                     ...
                     69064, 69065, 69066, 69067, 69068, 69069, 69070, 69071, 69072,
                     69073],
                    dtype='int64', length=115),
         660: Int64Index([45873, 45874, 45875, 45876, 45877, 45878, 45879, 45880, 45881,
                     45882,
                     ...
                     46016, 46017, 46018, 46019, 46020, 46021, 46022, 46023, 46024,
                     46025],
                    dtype='int64', length=153),
         661: Int64Index([90359, 90360, 90361, 90362, 90363, 90364, 90365, 90366, 90367,
                     90368, 90369, 90370, 90371, 90372, 90373, 90374, 90375, 90376,
                     90377, 90378, 90379, 90380, 90381, 90382, 90383, 90384, 90385,
                     90386, 90387, 90388, 90389, 90390, 90391, 90392, 90393, 90394,
                     90395, 90396, 90397, 90398, 90399, 90400, 90401, 90402, 90403,
                     90404, 90405, 90406, 90407, 90408, 90409, 90410, 90411, 90412,
                     90413, 90414, 90415, 90416, 90417, 90418, 90419, 90420, 90421,
                     90422, 90423, 90424, 90425, 90426, 90427, 90428, 90429, 90430,
                     90431, 90432, 90433, 90434, 90435, 90436, 90437, 90438, 90439,
                     90440, 90441, 90442, 90443, 90444, 90445, 90446],
                    dtype='int64'),
         662: Int64Index([36229, 36230, 36231, 36232, 36233, 36234, 36235, 36236, 36237,
                     36238, 36239, 36240, 36241, 36242, 36243, 36244, 36245, 36246,
                     36247, 36248, 36249, 36250, 36251, 36252, 36253, 36254, 36255,
                     36256, 36257, 36258, 36259, 36260, 36261, 36262, 36263, 36264,
                     36265, 36266, 36267, 36268, 36269, 36270, 36271, 36272, 36273,
                     36274, 36275, 36276, 36277, 36278, 36279, 36280, 36281, 36282,
                     36283, 36284, 36285, 36286, 36287, 36288, 36289, 36290, 36291,
                     36292, 36293, 36294, 36295, 36296, 36297, 36298, 36299, 36300,
                     36301, 36302, 36303, 36304, 36305, 36306, 36307, 36308, 36309,
                     36310],
                    dtype='int64'),
         663: Int64Index([1137, 1138, 1139, 1140, 1141, 1142, 1143, 1144, 1145, 1146,
                     ...
                     1243, 1244, 1245, 1246, 1247, 1248, 1249, 1250, 1251, 1252],
                    dtype='int64', length=116),
         664: Int64Index([72814, 72815, 72816, 72817, 72818, 72819, 72820, 72821, 72822,
                     72823, 72824, 72825, 72826, 72827, 72828, 72829, 72830, 72831,
                     72832, 72833, 72834, 72835, 72836, 72837, 72838, 72839, 72840,
                     72841, 72842, 72843, 72844, 72845, 72846, 72847, 72848, 72849,
                     72850, 72851, 72852, 72853, 72854, 72855, 72856, 72857, 72858,
                     72859],
                    dtype='int64'),
         665: Int64Index([26453, 26454, 26455, 26456, 26457, 26458, 26459, 26460, 26461,
                     26462, 26463, 26464, 26465, 26466, 26467, 26468, 26469, 26470,
                     26471, 26472, 26473, 26474, 26475, 26476, 26477, 26478, 26479,
                     26480, 26481, 26482, 26483, 26484, 26485, 26486, 26487, 26488,
                     26489, 26490, 26491, 26492, 26493, 26494, 26495, 26496, 26497,
                     26498, 26499, 26500, 26501, 26502, 26503, 26504, 26505, 26506,
                     26507, 26508, 26509, 26510, 26511, 26512, 26513, 26514, 26515,
                     26516, 26517, 26518, 26519, 26520, 26521, 26522, 26523, 26524,
                     26525, 26526, 26527, 26528, 26529, 26530, 26531, 26532, 26533,
                     26534, 26535, 26536, 26537, 26538, 26539, 26540, 26541, 26542,
                     26543, 26544, 26545, 26546, 26547, 26548, 26549, 26550, 26551,
                     26552],
                    dtype='int64'),
         666: Int64Index([97805, 97806, 97807, 97808, 97809], dtype='int64'),
         667: Int64Index([95598, 95599, 95600, 95601, 95602, 95603, 95604, 95605, 95606,
                     95607, 95608, 95609],
                    dtype='int64'),
         668: Int64Index([97810, 97811, 97812, 97813, 97814, 97815], dtype='int64'),
         669: Int64Index([97402, 97403, 97404, 97405, 97406, 97407, 97408, 97409, 97410,
                     97411, 97412, 97413, 97414],
                    dtype='int64'),
         670: Int64Index([89321, 89322, 89323, 89324, 89325, 89326, 89327, 89328, 89329,
                     89330, 89331, 89332, 89333, 89334, 89335, 89336, 89337, 89338,
                     89339, 89340, 89341, 89342, 89343, 89344, 89345, 89346, 89347,
                     89348, 89349, 89350, 89351, 89352, 89353, 89354, 89355, 89356],
                    dtype='int64'),
         671: Int64Index([92151, 92152, 92153, 92154, 92155, 92156, 92157, 92158, 92159,
                     92160, 92161, 92162, 92163, 92164, 92165, 92166, 92167, 92168,
                     92169, 92170, 92171, 92172, 92173, 92174, 92175, 92176, 92177,
                     92178, 92179, 92180, 92181, 92182, 92183, 92184, 92185, 92186,
                     92187, 92188, 92189, 92190, 92191, 92192, 92193, 92194, 92195,
                     92196],
                    dtype='int64'),
         672: Int64Index([91039, 91040, 91041, 91042, 91043, 91044, 91045, 91046, 91047,
                     91048, 91049, 91050, 91051, 91052, 91053, 91054, 91055, 91056,
                     91057, 91058, 91059, 91060, 91061, 91062, 91063, 91064, 91065,
                     91066, 91067, 91068, 91069, 91070, 91071, 91072, 91073, 91074,
                     91075, 91076, 91077, 91078, 91079, 91080, 91081, 91082, 91083,
                     91084, 91085, 91086, 91087, 91088, 91089, 91090, 91091, 91092,
                     91093, 91094, 91095, 91096, 91097, 91098, 91099, 91100, 91101,
                     91102, 91103],
                    dtype='int64'),
         673: Int64Index([35571, 35572, 35573, 35574, 35575, 35576, 35577, 35578, 35579,
                     35580, 35581, 35582, 35583, 35584, 35585, 35586, 35587, 35588,
                     35589, 35590, 35591, 35592, 35593, 35594, 35595, 35596, 35597,
                     35598, 35599, 35600, 35601, 35602, 35603, 35604, 35605, 35606,
                     35607, 35608, 35609, 35610, 35611, 35612, 35613, 35614, 35615,
                     35616, 35617, 35618, 35619, 35620, 35621, 35622, 35623, 35624,
                     35625, 35626, 35627, 35628, 35629, 35630, 35631, 35632, 35633,
                     35634, 35635, 35636, 35637, 35638, 35639, 35640, 35641, 35642,
                     35643, 35644, 35645, 35646, 35647, 35648, 35649, 35650, 35651,
                     35652, 35653, 35654, 35655, 35656],
                    dtype='int64'),
         674: Int64Index([83378, 83379, 83380, 83381, 83382, 83383, 83384, 83385, 83386,
                     83387, 83388, 83389, 83390, 83391, 83392, 83393, 83394, 83395,
                     83396, 83397, 83398, 83399, 83400, 83401, 83402, 83403, 83404,
                     83405, 83406, 83407, 83408, 83409, 83410, 83411, 83412, 83413,
                     83414, 83415, 83416, 83417, 83418, 83419, 83420, 83421, 83422,
                     83423, 83424, 83425],
                    dtype='int64'),
         675: Int64Index([93372, 93373, 93374, 93375, 93376, 93377, 93378, 93379, 93380,
                     93381, 93382, 93383, 93384, 93385, 93386, 93387, 93388, 93389,
                     93390, 93391, 93392, 93393, 93394, 93395, 93396, 93397, 93398,
                     93399, 93400, 93401, 93402, 93403, 93404, 93405, 93406, 93407,
                     93408, 93409, 93410, 93411, 93412, 93413, 93414, 93415, 93416,
                     93417, 93418, 93419, 93420, 93421, 93422, 93423, 93424, 93425],
                    dtype='int64'),
         676: Int64Index([37143, 37144, 37145, 37146, 37147, 37148, 37149, 37150, 37151,
                     37152, 37153, 37154, 37155, 37156, 37157, 37158, 37159, 37160,
                     37161, 37162, 37163, 37164, 37165, 37166, 37167, 37168, 37169,
                     37170, 37171, 37172, 37173, 37174, 37175, 37176, 37177, 37178,
                     37179, 37180, 37181, 37182, 37183, 37184, 37185, 37186, 37187,
                     37188, 37189, 37190, 37191, 37192, 37193, 37194, 37195, 37196,
                     37197, 37198, 37199, 37200, 37201, 37202, 37203, 37204, 37205,
                     37206, 37207, 37208, 37209, 37210, 37211, 37212, 37213, 37214,
                     37215, 37216, 37217, 37218, 37219],
                    dtype='int64'),
         677: Int64Index([97740], dtype='int64'),
         678: Int64Index([85271, 85272, 85273, 85274, 85275, 85276, 85277, 85278, 85279,
                     85280,
                     ...
                     85480, 85481, 85482, 85483, 85484, 85485, 85486, 85487, 85488,
                     85489],
                    dtype='int64', length=219),
         679: Int64Index([64086, 64087, 64088, 64089, 64090, 64091, 64092, 64093, 64094,
                     64095,
                     ...
                     64183, 64184, 64185, 64186, 64187, 64188, 64189, 64190, 64191,
                     64192],
                    dtype='int64', length=107),
         680: Int64Index([96060, 96061, 96062, 96063, 96064, 96065, 96066, 96067, 96068,
                     96069, 96070, 96071, 96072, 96073, 96074, 96075, 96076, 96077,
                     96078, 96079, 96080, 96081, 96082, 96083, 96084, 96085, 96086,
                     96087, 96088, 96089, 96090, 96091, 96092, 96093],
                    dtype='int64'),
         681: Int64Index([95365, 95366, 95367, 95368, 95369, 95370, 95371, 95372, 95373,
                     95374, 95375, 95376, 95377, 95378, 95379, 95380, 95381, 95382,
                     95383, 95384, 95385, 95386, 95387, 95388, 95389, 95390, 95391],
                    dtype='int64'),
         682: Int64Index([96368, 96369, 96370, 96371, 96372, 96373, 96374, 96375, 96376,
                     96377, 96378, 96379, 96380, 96381, 96382, 96383, 96384, 96385,
                     96386, 96387, 96388, 96389, 96390, 96391, 96392, 96393, 96394,
                     96395, 96396, 96397, 96398, 96399, 96400, 96401, 96402, 96403,
                     96404, 96405, 96406, 96407, 96408, 96409, 96410, 96411, 96412,
                     96413, 96414, 96415, 96416, 96417, 96418, 96419, 96420, 96421,
                     96422, 96423, 96424, 96425, 96426, 96427, 96428, 96429, 96430,
                     96431, 96432, 96433, 96434, 96435, 96436, 96437, 96438, 96439,
                     96440, 96441, 96442, 96443, 96444, 96445, 96446, 96447, 96448,
                     96449, 96450, 96451, 96452, 96453, 96454, 96455, 96456, 96457,
                     96458, 96459, 96460, 96461, 96462, 96463, 96464, 96465, 96466,
                     96467],
                    dtype='int64'),
         683: Int64Index([22278, 22279, 22280, 22281, 22282, 22283, 22284, 22285, 22286,
                     22287, 22288, 22289, 22290, 22291, 22292, 22293, 22294, 22295,
                     22296, 22297, 22298, 22299, 22300, 22301, 22302, 22303, 22304,
                     22305, 22306, 22307, 22308, 22309, 22310, 22311, 22312, 22313,
                     22314, 22315, 22316, 22317, 22318, 22319, 22320, 22321, 22322,
                     22323, 22324, 22325, 22326],
                    dtype='int64'),
         684: Int64Index([16957, 16958, 16959, 16960, 16961, 16962, 16963, 16964, 16965,
                     16966,
                     ...
                     17116, 17117, 17118, 17119, 17120, 17121, 17122, 17123, 17124,
                     17125],
                    dtype='int64', length=169),
         685: Int64Index([43676, 43677, 43678, 43679, 43680, 43681, 43682, 43683, 43684,
                     43685,
                     ...
                     43823, 43824, 43825, 43826, 43827, 43828, 43829, 43830, 43831,
                     43832],
                    dtype='int64', length=157),
         686: Int64Index([72764, 72765, 72766, 72767, 72768, 72769, 72770, 72771, 72772,
                     72773, 72774, 72775, 72776, 72777, 72778, 72779, 72780, 72781,
                     72782, 72783, 72784, 72785, 72786, 72787, 72788, 72789, 72790,
                     72791, 72792, 72793, 72794, 72795, 72796, 72797, 72798, 72799,
                     72800, 72801, 72802, 72803, 72804, 72805, 72806, 72807, 72808,
                     72809, 72810, 72811, 72812, 72813],
                    dtype='int64'),
         687: Int64Index([21343, 21344, 21345, 21346, 21347, 21348, 21349, 21350, 21351,
                     21352, 21353, 21354, 21355, 21356, 21357, 21358, 21359, 21360,
                     21361, 21362, 21363, 21364, 21365, 21366, 21367, 21368, 21369,
                     21370, 21371, 21372, 21373, 21374, 21375, 21376, 21377, 21378,
                     21379, 21380, 21381, 21382, 21383, 21384, 21385, 21386, 21387,
                     21388, 21389, 21390, 21391, 21392, 21393, 21394, 21395, 21396,
                     21397, 21398, 21399, 21400, 21401, 21402, 21403, 21404, 21405,
                     21406, 21407, 21408, 21409, 21410, 21411],
                    dtype='int64'),
         688: Int64Index([31073, 31074, 31075, 31076, 31077, 31078, 31079, 31080, 31081,
                     31082, 31083, 31084, 31085, 31086, 31087, 31088, 31089, 31090,
                     31091, 31092, 31093, 31094, 31095, 31096, 31097, 31098, 31099,
                     31100, 31101, 31102, 31103, 31104, 31105, 31106, 31107, 31108,
                     31109, 31110, 31111, 31112, 31113, 31114, 31115, 31116],
                    dtype='int64'),
         689: Int64Index([18274, 18275, 18276, 18277, 18278, 18279, 18280, 18281, 18282,
                     18283, 18284, 18285, 18286, 18287, 18288, 18289, 18290, 18291,
                     18292, 18293, 18294, 18295, 18296, 18297, 18298, 18299, 18300,
                     18301, 18302, 18303, 18304, 18305, 18306, 18307, 18308, 18309,
                     18310, 18311, 18312, 18313, 18314, 18315, 18316, 18317, 18318,
                     18319, 18320, 18321, 18322, 18323, 18324, 18325, 18326, 18327,
                     18328, 18329, 18330, 18331, 18332, 18333, 18334, 18335, 18336,
                     18337, 18338, 18339, 18340, 18341, 18342, 18343, 18344, 18345,
                     18346, 18347, 18348, 18349, 18350, 18351, 18352, 18353, 18354,
                     18355, 18356, 18357, 18358, 18359, 18360],
                    dtype='int64'),
         690: Int64Index([72069, 72070, 72071, 72072, 72073, 72074, 72075, 72076, 72077,
                     72078,
                     ...
                     72214, 72215, 72216, 72217, 72218, 72219, 72220, 72221, 72222,
                     72223],
                    dtype='int64', length=155),
         691: Int64Index([97563, 97564, 97565, 97566, 97567, 97568, 97569, 97570, 97571,
                     97572, 97573, 97574, 97575, 97576, 97577, 97578],
                    dtype='int64'),
         692: Int64Index([2468, 2469, 2470, 2471, 2472, 2473, 2474, 2475, 2476, 2477,
                     ...
                     2622, 2623, 2624, 2625, 2626, 2627, 2628, 2629, 2630, 2631],
                    dtype='int64', length=164),
         693: Int64Index([86675, 86676, 86677, 86678, 86679, 86680, 86681, 86682, 86683,
                     86684, 86685, 86686, 86687, 86688, 86689, 86690, 86691, 86692,
                     86693, 86694, 86695, 86696, 86697, 86698, 86699, 86700, 86701,
                     86702, 86703, 86704, 86705, 86706, 86707, 86708, 86709, 86710,
                     86711, 86712, 86713, 86714, 86715, 86716, 86717, 86718, 86719,
                     86720, 86721, 86722, 86723, 86724, 86725, 86726, 86727, 86728,
                     86729, 86730, 86731, 86732, 86733, 86734, 86735, 86736, 86737,
                     86738, 86739, 86740, 86741, 86742, 86743, 86744, 86745, 86746,
                     86747, 86748, 86749, 86750, 86751, 86752, 86753, 86754, 86755,
                     86756, 86757, 86758, 86759, 86760, 86761, 86762, 86763, 86764,
                     86765],
                    dtype='int64'),
         694: Int64Index([93875, 93876, 93877, 93878, 93879, 93880, 93881, 93882, 93883,
                     93884, 93885, 93886, 93887, 93888, 93889, 93890, 93891, 93892,
                     93893, 93894, 93895, 93896, 93897, 93898, 93899, 93900, 93901,
                     93902, 93903, 93904, 93905, 93906, 93907, 93908, 93909, 93910,
                     93911, 93912, 93913, 93914, 93915, 93916, 93917, 93918],
                    dtype='int64'),
         695: Int64Index([97915, 97916, 97917, 97918, 97919, 97920, 97921, 97922, 97923,
                     97924, 97925, 97926, 97927],
                    dtype='int64'),
         696: Int64Index([67176, 67177, 67178, 67179, 67180, 67181, 67182, 67183, 67184,
                     67185, 67186, 67187, 67188, 67189, 67190, 67191, 67192, 67193,
                     67194, 67195, 67196, 67197, 67198, 67199, 67200, 67201, 67202,
                     67203, 67204, 67205, 67206, 67207, 67208, 67209, 67210, 67211,
                     67212, 67213, 67214, 67215, 67216, 67217, 67218, 67219, 67220,
                     67221, 67222, 67223, 67224, 67225, 67226, 67227, 67228, 67229,
                     67230, 67231, 67232, 67233, 67234, 67235, 67236, 67237, 67238,
                     67239, 67240, 67241, 67242, 67243, 67244, 67245, 67246, 67247,
                     67248, 67249, 67250, 67251, 67252, 67253, 67254],
                    dtype='int64'),
         697: Int64Index([49690, 49691, 49692, 49693, 49694, 49695, 49696, 49697, 49698,
                     49699, 49700, 49701, 49702, 49703, 49704, 49705, 49706, 49707,
                     49708, 49709, 49710, 49711, 49712, 49713, 49714, 49715, 49716,
                     49717, 49718, 49719, 49720, 49721, 49722, 49723, 49724, 49725,
                     49726, 49727, 49728, 49729],
                    dtype='int64'),
         698: Int64Index([94501, 94502, 94503, 94504, 94505, 94506, 94507, 94508, 94509,
                     94510],
                    dtype='int64'),
         699: Int64Index([69168, 69169, 69170, 69171, 69172, 69173, 69174, 69175, 69176,
                     69177,
                     ...
                     69260, 69261, 69262, 69263, 69264, 69265, 69266, 69267, 69268,
                     69269],
                    dtype='int64', length=102),
         700: Int64Index([86918, 86919, 86920, 86921, 86922, 86923, 86924, 86925, 86926,
                     86927, 86928, 86929, 86930, 86931, 86932],
                    dtype='int64'),
         701: Int64Index([97928, 97929, 97930, 97931, 97932, 97933, 97934, 97935, 97936,
                     97937],
                    dtype='int64'),
         702: Int64Index([77990, 77991, 77992, 77993, 77994, 77995, 77996, 77997, 77998,
                     77999, 78000, 78001, 78002, 78003, 78004, 78005, 78006, 78007,
                     78008, 78009, 78010, 78011, 78012, 78013, 78014, 78015, 78016,
                     78017, 78018, 78019, 78020, 78021, 78022, 78023, 78024, 78025,
                     78026, 78027, 78028, 78029, 78030, 78031, 78032, 78033, 78034,
                     78035, 78036, 78037, 78038, 78039, 78040, 78041, 78042],
                    dtype='int64'),
         703: Int64Index([81309, 81310, 81311, 81312, 81313, 81314, 81315, 81316, 81317,
                     81318, 81319, 81320, 81321, 81322, 81323, 81324, 81325, 81326,
                     81327],
                    dtype='int64'),
         704: Int64Index([79539, 79540, 79541, 79542, 79543, 79544, 79545, 79546, 79547,
                     79548, 79549, 79550, 79551, 79552, 79553, 79554, 79555, 79556,
                     79557, 79558, 79559, 79560, 79561, 79562],
                    dtype='int64'),
         705: Int64Index([59580, 59581, 59582, 59583, 59584, 59585, 59586, 59587, 59588,
                     59589,
                     ...
                     59707, 59708, 59709, 59710, 59711, 59712, 59713, 59714, 59715,
                     59716],
                    dtype='int64', length=137),
         706: Int64Index([91401, 91402, 91403, 91404, 91405, 91406], dtype='int64'),
         707: Int64Index([35657, 35658, 35659, 35660, 35661, 35662, 35663, 35664, 35665,
                     35666, 35667, 35668, 35669, 35670, 35671, 35672, 35673, 35674,
                     35675, 35676, 35677, 35678, 35679, 35680, 35681, 35682, 35683,
                     35684, 35685, 35686, 35687, 35688, 35689, 35690, 35691, 35692,
                     35693, 35694, 35695, 35696, 35697, 35698, 35699, 35700, 35701,
                     35702, 35703, 35704, 35705, 35706, 35707, 35708, 35709, 35710,
                     35711, 35712, 35713, 35714, 35715, 35716, 35717, 35718, 35719,
                     35720, 35721, 35722, 35723, 35724, 35725, 35726],
                    dtype='int64'),
         708: Int64Index([51389, 51390, 51391, 51392, 51393, 51394, 51395, 51396, 51397,
                     51398,
                     ...
                     51480, 51481, 51482, 51483, 51484, 51485, 51486, 51487, 51488,
                     51489],
                    dtype='int64', length=101),
         709: Int64Index([73000, 73001, 73002, 73003, 73004, 73005, 73006, 73007, 73008,
                     73009,
                     ...
                     73094, 73095, 73096, 73097, 73098, 73099, 73100, 73101, 73102,
                     73103],
                    dtype='int64', length=104),
         710: Int64Index([50949, 50950, 50951, 50952, 50953, 50954, 50955, 50956, 50957,
                     50958, 50959, 50960, 50961, 50962, 50963, 50964, 50965, 50966,
                     50967, 50968, 50969, 50970, 50971, 50972, 50973, 50974, 50975,
                     50976, 50977, 50978, 50979, 50980, 50981, 50982, 50983, 50984,
                     50985, 50986, 50987, 50988, 50989, 50990, 50991, 50992, 50993,
                     50994, 50995, 50996, 50997, 50998, 50999, 51000, 51001, 51002,
                     51003, 51004, 51005, 51006, 51007, 51008, 51009, 51010, 51011,
                     51012, 51013, 51014, 51015, 51016, 51017, 51018, 51019, 51020,
                     51021, 51022, 51023, 51024, 51025, 51026, 51027],
                    dtype='int64'),
         711: Int64Index([97914], dtype='int64'),
         712: Int64Index([31117, 31118, 31119, 31120, 31121, 31122, 31123, 31124, 31125,
                     31126, 31127, 31128, 31129, 31130, 31131, 31132, 31133, 31134,
                     31135, 31136, 31137, 31138, 31139, 31140, 31141, 31142, 31143,
                     31144, 31145, 31146, 31147, 31148, 31149, 31150, 31151, 31152,
                     31153, 31154, 31155, 31156, 31157, 31158, 31159, 31160, 31161,
                     31162, 31163, 31164, 31165, 31166, 31167],
                    dtype='int64'),
         713: Int64Index([72928, 72929, 72930, 72931, 72932, 72933, 72934, 72935, 72936,
                     72937, 72938, 72939, 72940, 72941, 72942, 72943, 72944, 72945,
                     72946, 72947, 72948, 72949, 72950, 72951, 72952, 72953, 72954,
                     72955, 72956, 72957, 72958, 72959, 72960, 72961, 72962, 72963,
                     72964, 72965, 72966, 72967, 72968, 72969, 72970, 72971, 72972,
                     72973, 72974, 72975, 72976, 72977, 72978, 72979, 72980, 72981,
                     72982, 72983, 72984, 72985, 72986, 72987, 72988, 72989, 72990,
                     72991, 72992, 72993, 72994, 72995, 72996, 72997, 72998, 72999],
                    dtype='int64'),
         714: Int64Index([99009, 99010, 99011, 99012, 99013, 99014, 99015, 99016, 99017,
                     99018, 99019, 99020, 99021],
                    dtype='int64'),
         715: Int64Index([78768, 78769, 78770, 78771, 78772, 78773, 78774, 78775, 78776,
                     78777, 78778, 78779, 78780, 78781, 78782, 78783, 78784, 78785,
                     78786, 78787, 78788, 78789, 78790, 78791, 78792, 78793, 78794,
                     78795, 78796, 78797, 78798, 78799, 78800, 78801, 78802, 78803,
                     78804, 78805, 78806, 78807, 78808, 78809, 78810, 78811, 78812,
                     78813, 78814, 78815, 78816, 78817, 78818, 78819, 78820, 78821,
                     78822, 78823, 78824, 78825, 78826, 78827, 78828, 78829, 78830,
                     78831, 78832, 78833, 78834, 78835, 78836, 78837, 78838, 78839,
                     78840, 78841, 78842, 78843, 78844, 78845, 78846, 78847, 78848,
                     78849, 78850, 78851, 78852, 78853, 78854],
                    dtype='int64'),
         716: Int64Index([48092, 48093, 48094, 48095, 48096, 48097, 48098, 48099, 48100,
                     48101, 48102, 48103, 48104, 48105, 48106, 48107, 48108, 48109,
                     48110, 48111, 48112, 48113, 48114, 48115, 48116, 48117, 48118,
                     48119, 48120, 48121, 48122, 48123, 48124, 48125, 48126, 48127,
                     48128, 48129, 48130, 48131, 48132, 48133, 48134, 48135, 48136,
                     48137, 48138, 48139, 48140, 48141, 48142, 48143, 48144, 48145,
                     48146, 48147, 48148, 48149],
                    dtype='int64'),
         717: Int64Index([12370, 12371, 12372, 12373, 12374, 12375, 12376, 12377, 12378,
                     12379, 12380, 12381, 12382, 12383, 12384, 12385, 12386, 12387,
                     12388, 12389, 12390, 12391, 12392, 12393, 12394, 12395, 12396,
                     12397, 12398, 12399, 12400, 12401, 12402, 12403, 12404, 12405,
                     12406, 12407, 12408, 12409, 12410, 12411, 12412, 12413, 12414,
                     12415, 12416, 12417, 12418, 12419, 12420, 12421, 12422, 12423,
                     12424, 12425, 12426, 12427, 12428, 12429, 12430, 12431, 12432,
                     12433, 12434, 12435, 12436, 12437, 12438, 12439, 12440, 12441,
                     12442, 12443, 12444, 12445, 12446, 12447, 12448, 12449, 12450,
                     12451],
                    dtype='int64'),
         718: Int64Index([94208, 94209, 94210, 94211, 94212, 94213, 94214, 94215, 94216,
                     94217, 94218, 94219, 94220, 94221, 94222, 94223],
                    dtype='int64'),
         719: Int64Index([94515, 94516, 94517, 94518, 94519, 94520, 94521, 94522, 94523,
                     94524, 94525, 94526, 94527, 94528, 94529, 94530, 94531, 94532,
                     94533, 94534, 94535, 94536, 94537, 94538, 94539, 94540, 94541,
                     94542, 94543],
                    dtype='int64'),
         720: Int64Index([84675, 84676, 84677, 84678, 84679, 84680, 84681, 84682, 84683,
                     84684, 84685, 84686, 84687, 84688, 84689, 84690, 84691, 84692,
                     84693, 84694, 84695, 84696, 84697, 84698, 84699, 84700, 84701,
                     84702, 84703, 84704, 84705, 84706, 84707, 84708, 84709, 84710,
                     84711, 84712, 84713, 84714, 84715, 84716, 84717, 84718, 84719,
                     84720, 84721, 84722, 84723, 84724, 84725, 84726, 84727, 84728,
                     84729, 84730, 84731, 84732, 84733, 84734, 84735, 84736, 84737,
                     84738, 84739, 84740, 84741, 84742, 84743, 84744, 84745, 84746,
                     84747, 84748, 84749, 84750, 84751, 84752, 84753, 84754, 84755,
                     84756, 84757, 84758, 84759, 84760],
                    dtype='int64'),
         721: Int64Index([45819, 45820, 45821, 45822, 45823, 45824, 45825, 45826, 45827,
                     45828, 45829, 45830, 45831, 45832, 45833, 45834, 45835, 45836,
                     45837, 45838, 45839, 45840, 45841, 45842, 45843, 45844, 45845,
                     45846, 45847, 45848, 45849, 45850, 45851, 45852, 45853, 45854,
                     45855, 45856, 45857, 45858, 45859, 45860, 45861, 45862, 45863,
                     45864, 45865, 45866, 45867, 45868, 45869, 45870, 45871, 45872],
                    dtype='int64'),
         722: Int64Index([85108, 85109, 85110, 85111, 85112, 85113, 85114, 85115, 85116,
                     85117, 85118, 85119, 85120, 85121, 85122, 85123, 85124, 85125,
                     85126, 85127, 85128, 85129, 85130, 85131, 85132, 85133, 85134,
                     85135, 85136, 85137, 85138, 85139, 85140, 85141, 85142, 85143,
                     85144, 85145, 85146, 85147, 85148, 85149, 85150, 85151, 85152,
                     85153, 85154, 85155, 85156, 85157, 85158, 85159, 85160, 85161,
                     85162, 85163, 85164, 85165],
                    dtype='int64'),
         723: Int64Index([41278, 41279, 41280, 41281, 41282, 41283, 41284, 41285, 41286,
                     41287, 41288, 41289, 41290, 41291, 41292, 41293, 41294, 41295,
                     41296, 41297, 41298, 41299, 41300, 41301, 41302, 41303, 41304,
                     41305, 41306, 41307, 41308, 41309, 41310, 41311],
                    dtype='int64'),
         724: Int64Index([42140, 42141, 42142, 42143, 42144, 42145, 42146, 42147, 42148,
                     42149, 42150, 42151, 42152, 42153, 42154, 42155, 42156, 42157,
                     42158, 42159, 42160, 42161, 42162, 42163, 42164, 42165, 42166,
                     42167, 42168, 42169, 42170, 42171, 42172, 42173, 42174, 42175,
                     42176, 42177, 42178, 42179, 42180, 42181, 42182, 42183, 42184,
                     42185, 42186, 42187, 42188, 42189, 42190, 42191, 42192, 42193,
                     42194, 42195, 42196, 42197, 42198, 42199, 42200, 42201, 42202,
                     42203, 42204, 42205, 42206, 42207, 42208, 42209, 42210, 42211,
                     42212, 42213, 42214, 42215],
                    dtype='int64'),
         725: Int64Index([89824, 89825, 89826, 89827, 89828, 89829, 89830, 89831, 89832,
                     89833, 89834, 89835, 89836, 89837, 89838, 89839],
                    dtype='int64'),
         726: Int64Index([94546, 94547, 94548, 94549, 94550, 94551, 94552, 94553, 94554,
                     94555, 94556, 94557, 94558, 94559],
                    dtype='int64'),
         727: Int64Index([86019, 86020, 86021, 86022, 86023, 86024, 86025, 86026, 86027,
                     86028, 86029, 86030, 86031, 86032, 86033, 86034, 86035, 86036,
                     86037, 86038, 86039, 86040, 86041, 86042, 86043, 86044, 86045,
                     86046, 86047, 86048, 86049, 86050, 86051, 86052, 86053, 86054,
                     86055, 86056, 86057, 86058, 86059, 86060, 86061, 86062, 86063,
                     86064, 86065, 86066, 86067, 86068, 86069, 86070, 86071, 86072,
                     86073, 86074, 86075, 86076, 86077, 86078, 86079, 86080, 86081],
                    dtype='int64'),
         728: Int64Index([82209, 82210, 82211, 82212, 82213, 82214, 82215, 82216, 82217,
                     82218, 82219, 82220, 82221, 82222, 82223, 82224, 82225, 82226,
                     82227, 82228, 82229, 82230, 82231, 82232, 82233, 82234, 82235,
                     82236, 82237, 82238, 82239, 82240, 82241, 82242, 82243, 82244,
                     82245, 82246, 82247, 82248, 82249, 82250, 82251, 82252, 82253],
                    dtype='int64'),
         729: Int64Index([73760, 73761, 73762, 73763, 73764, 73765, 73766, 73767, 73768,
                     73769, 73770, 73771, 73772, 73773, 73774, 73775, 73776, 73777,
                     73778, 73779, 73780, 73781, 73782, 73783, 73784, 73785, 73786,
                     73787, 73788, 73789, 73790, 73791, 73792, 73793, 73794, 73795,
                     73796, 73797, 73798, 73799, 73800, 73801, 73802, 73803, 73804,
                     73805, 73806, 73807, 73808, 73809, 73810, 73811, 73812, 73813,
                     73814, 73815, 73816, 73817, 73818, 73819, 73820, 73821, 73822,
                     73823, 73824, 73825, 73826, 73827, 73828, 73829, 73830, 73831,
                     73832, 73833, 73834, 73835, 73836, 73837, 73838, 73839, 73840],
                    dtype='int64'),
         730: Int64Index([94848, 94849, 94850, 94851, 94852, 94853, 94854, 94855, 94856,
                     94857, 94858, 94859, 94860, 94861, 94862, 94863, 94864, 94865,
                     94866, 94867, 94868, 94869, 94870, 94871],
                    dtype='int64'),
         731: Int64Index([34640, 34641, 34642, 34643, 34644, 34645, 34646, 34647, 34648,
                     34649, 34650, 34651, 34652, 34653, 34654, 34655, 34656, 34657,
                     34658, 34659, 34660, 34661, 34662, 34663, 34664, 34665, 34666,
                     34667, 34668, 34669, 34670, 34671, 34672, 34673, 34674, 34675,
                     34676, 34677, 34678],
                    dtype='int64'),
         732: Int64Index([32276, 32277, 32278, 32279, 32280, 32281, 32282, 32283, 32284,
                     32285,
                     ...
                     32446, 32447, 32448, 32449, 32450, 32451, 32452, 32453, 32454,
                     32455],
                    dtype='int64', length=180),
         733: Int64Index([70229, 70230, 70231, 70232, 70233, 70234, 70235, 70236, 70237,
                     70238, 70239, 70240, 70241, 70242, 70243],
                    dtype='int64'),
         734: Int64Index([82317, 82318, 82319, 82320, 82321, 82322, 82323, 82324, 82325,
                     82326, 82327, 82328, 82329, 82330, 82331, 82332, 82333, 82334,
                     82335, 82336, 82337, 82338, 82339, 82340, 82341, 82342, 82343],
                    dtype='int64'),
         735: Int64Index([54174, 54175, 54176, 54177, 54178, 54179, 54180, 54181, 54182,
                     54183,
                     ...
                     54301, 54302, 54303, 54304, 54305, 54306, 54307, 54308, 54309,
                     54310],
                    dtype='int64', length=137),
         736: Int64Index([86220, 86221, 86222, 86223, 86224, 86225, 86226, 86227, 86228,
                     86229, 86230, 86231, 86232, 86233, 86234, 86235, 86236, 86237,
                     86238, 86239, 86240, 86241, 86242, 86243, 86244, 86245, 86246,
                     86247, 86248, 86249, 86250, 86251, 86252, 86253, 86254, 86255,
                     86256, 86257, 86258, 86259, 86260, 86261, 86262, 86263, 86264,
                     86265, 86266, 86267, 86268, 86269, 86270, 86271, 86272, 86273,
                     86274, 86275, 86276, 86277, 86278, 86279, 86280, 86281, 86282,
                     86283, 86284, 86285, 86286, 86287, 86288, 86289, 86290, 86291,
                     86292, 86293, 86294, 86295, 86296, 86297],
                    dtype='int64'),
         737: Int64Index([81390, 81391, 81392, 81393, 81394, 81395, 81396, 81397, 81398,
                     81399, 81400, 81401, 81402, 81403, 81404, 81405, 81406, 81407,
                     81408, 81409, 81410, 81411, 81412, 81413, 81414, 81415, 81416,
                     81417, 81418, 81419, 81420, 81421, 81422, 81423, 81424, 81425,
                     81426, 81427, 81428, 81429, 81430, 81431, 81432, 81433, 81434,
                     81435, 81436, 81437, 81438, 81439, 81440, 81441, 81442, 81443,
                     81444, 81445, 81446, 81447, 81448],
                    dtype='int64'),
         738: Int64Index([43287, 43288, 43289, 43290, 43291, 43292, 43293, 43294, 43295,
                     43296, 43297, 43298, 43299, 43300, 43301, 43302, 43303, 43304,
                     43305, 43306, 43307, 43308, 43309, 43310, 43311, 43312, 43313,
                     43314, 43315, 43316, 43317],
                    dtype='int64'),
         739: Int64Index([44200, 44201, 44202, 44203, 44204, 44205, 44206, 44207, 44208,
                     44209,
                     ...
                     44354, 44355, 44356, 44357, 44358, 44359, 44360, 44361, 44362,
                     44363],
                    dtype='int64', length=164),
         740: Int64Index([95902, 95903, 95904, 95905, 95906, 95907, 95908, 95909, 95910,
                     95911, 95912, 95913, 95914, 95915, 95916, 95917, 95918, 95919,
                     95920, 95921, 95922, 95923, 95924, 95925, 95926, 95927, 95928,
                     95929, 95930, 95931, 95932, 95933, 95934, 95935, 95936, 95937,
                     95938, 95939, 95940, 95941, 95942, 95943, 95944, 95945, 95946,
                     95947, 95948, 95949, 95950, 95951, 95952, 95953, 95954, 95955,
                     95956, 95957, 95958, 95959, 95960, 95961, 95962, 95963, 95964],
                    dtype='int64'),
         741: Int64Index([66620, 66621, 66622, 66623, 66624, 66625, 66626, 66627, 66628,
                     66629, 66630, 66631, 66632, 66633, 66634, 66635, 66636, 66637,
                     66638, 66639, 66640, 66641, 66642, 66643, 66644, 66645, 66646,
                     66647, 66648, 66649, 66650, 66651, 66652, 66653, 66654, 66655,
                     66656, 66657, 66658, 66659, 66660, 66661, 66662, 66663, 66664,
                     66665, 66666, 66667, 66668, 66669, 66670, 66671, 66672, 66673,
                     66674, 66675, 66676, 66677],
                    dtype='int64'),
         742: Int64Index([8791, 8792, 8793, 8794, 8795, 8796, 8797, 8798, 8799, 8800,
                     ...
                     9048, 9049, 9050, 9051, 9052, 9053, 9054, 9055, 9056, 9057],
                    dtype='int64', length=267),
         743: Int64Index([37476, 37477, 37478, 37479, 37480, 37481, 37482, 37483, 37484,
                     37485, 37486, 37487, 37488, 37489, 37490, 37491, 37492, 37493,
                     37494, 37495, 37496, 37497, 37498, 37499, 37500, 37501, 37502,
                     37503, 37504, 37505, 37506, 37507, 37508, 37509, 37510, 37511,
                     37512, 37513, 37514],
                    dtype='int64'),
         744: Int64Index([53199, 53200, 53201, 53202, 53203, 53204, 53205, 53206, 53207,
                     53208, 53209, 53210, 53211, 53212, 53213, 53214, 53215, 53216,
                     53217, 53218, 53219, 53220, 53221, 53222, 53223, 53224, 53225,
                     53226, 53227, 53228, 53229, 53230, 53231, 53232, 53233, 53234,
                     53235, 53236, 53237, 53238, 53239, 53240, 53241, 53242, 53243,
                     53244, 53245, 53246, 53247, 53248, 53249, 53250, 53251, 53252,
                     53253, 53254, 53255, 53256, 53257, 53258, 53259, 53260, 53261,
                     53262, 53263, 53264, 53265, 53266, 53267, 53268, 53269, 53270,
                     53271, 53272, 53273, 53274, 53275, 53276, 53277, 53278, 53279,
                     53280, 53281, 53282, 53283, 53284, 53285, 53286, 53287, 53288,
                     53289, 53290],
                    dtype='int64'),
         745: Int64Index([92789, 92790, 92791, 92792, 92793, 92794, 92795, 92796, 92797,
                     92798, 92799, 92800, 92801, 92802, 92803, 92804],
                    dtype='int64'),
         746: Int64Index([46449, 46450, 46451, 46452, 46453, 46454, 46455, 46456, 46457,
                     46458,
                     ...
                     46558, 46559, 46560, 46561, 46562, 46563, 46564, 46565, 46566,
                     46567],
                    dtype='int64', length=119),
         747: Int64Index([38484, 38485, 38486, 38487, 38488, 38489, 38490, 38491, 38492,
                     38493,
                     ...
                     38576, 38577, 38578, 38579, 38580, 38581, 38582, 38583, 38584,
                     38585],
                    dtype='int64', length=102),
         748: Int64Index([55187, 55188, 55189, 55190, 55191, 55192, 55193, 55194, 55195,
                     55196,
                     ...
                     55493, 55494, 55495, 55496, 55497, 55498, 55499, 55500, 55501,
                     55502],
                    dtype='int64', length=316),
         749: Int64Index([73320, 73321, 73322, 73323, 73324, 73325, 73326, 73327, 73328,
                     73329, 73330, 73331, 73332, 73333, 73334, 73335, 73336, 73337,
                     73338, 73339, 73340, 73341, 73342, 73343, 73344, 73345, 73346,
                     73347, 73348, 73349, 73350, 73351, 73352, 73353, 73354, 73355,
                     73356, 73357, 73358, 73359, 73360, 73361, 73362, 73363, 73364,
                     73365, 73366, 73367, 73368, 73369, 73370],
                    dtype='int64'),
         750: Int64Index([97434, 97435, 97436, 97437, 97438, 97439, 97440, 97441, 97442,
                     97443,
                     ...
                     97548, 97549, 97550, 97551, 97552, 97553, 97554, 97555, 97556,
                     97557],
                    dtype='int64', length=124),
         751: Int64Index([55503, 55504, 55505, 55506, 55507, 55508, 55509, 55510, 55511,
                     55512,
                     ...
                     55673, 55674, 55675, 55676, 55677, 55678, 55679, 55680, 55681,
                     55682],
                    dtype='int64', length=180),
         752: Int64Index([94676, 94677, 94678, 94679, 94680, 94681, 94682, 94683, 94684,
                     94685, 94686, 94687, 94688, 94689, 94690, 94691, 94692, 94693,
                     94694, 94695, 94696, 94697, 94698, 94699, 94700, 94701, 94702,
                     94703, 94704, 94705, 94706, 94707, 94708, 94709, 94710, 94711,
                     94712, 94713, 94714],
                    dtype='int64'),
         753: Int64Index([94896, 94897, 94898, 94899, 94900, 94901, 94902, 94903, 94904,
                     94905, 94906, 94907, 94908, 94909, 94910, 94911, 94912, 94913,
                     94914, 94915, 94916, 94917, 94918, 94919],
                    dtype='int64'),
         754: Int64Index([14546, 14547, 14548, 14549, 14550, 14551, 14552, 14553, 14554,
                     14555, 14556, 14557, 14558, 14559, 14560, 14561, 14562, 14563,
                     14564, 14565, 14566, 14567, 14568, 14569, 14570, 14571, 14572,
                     14573, 14574, 14575, 14576, 14577, 14578, 14579, 14580, 14581,
                     14582, 14583, 14584, 14585, 14586, 14587, 14588, 14589, 14590,
                     14591, 14592, 14593, 14594, 14595, 14596, 14597, 14598, 14599,
                     14600, 14601, 14602],
                    dtype='int64'),
         755: Int64Index([83675, 83676, 83677, 83678, 83679, 83680, 83681, 83682, 83683,
                     83684, 83685, 83686, 83687, 83688, 83689, 83690, 83691, 83692,
                     83693, 83694, 83695, 83696, 83697, 83698, 83699, 83700, 83701,
                     83702, 83703, 83704, 83705, 83706, 83707, 83708, 83709, 83710,
                     83711, 83712, 83713, 83714, 83715, 83716, 83717, 83718, 83719,
                     83720, 83721, 83722, 83723, 83724, 83725, 83726, 83727, 83728,
                     83729, 83730, 83731, 83732, 83733, 83734, 83735, 83736, 83737,
                     83738, 83739, 83740, 83741, 83742, 83743, 83744, 83745, 83746,
                     83747, 83748, 83749, 83750, 83751, 83752, 83753, 83754, 83755,
                     83756, 83757, 83758, 83759, 83760, 83761, 83762, 83763, 83764,
                     83765, 83766, 83767, 83768, 83769, 83770],
                    dtype='int64'),
         756: Int64Index([35443, 35444, 35445, 35446, 35447, 35448, 35449, 35450, 35451,
                     35452,
                     ...
                     35561, 35562, 35563, 35564, 35565, 35566, 35567, 35568, 35569,
                     35570],
                    dtype='int64', length=128),
         757: Int64Index([98744, 98745, 98746, 98747], dtype='int64'),
         758: Int64Index([84238, 84239, 84240, 84241, 84242, 84243, 84244, 84245, 84246,
                     84247, 84248, 84249, 84250, 84251, 84252, 84253, 84254, 84255,
                     84256, 84257, 84258],
                    dtype='int64'),
         759: Int64Index([87911, 87912, 87913, 87914, 87915, 87916, 87917, 87918, 87919,
                     87920, 87921],
                    dtype='int64'),
         760: Int64Index([84192, 84193, 84194, 84195, 84196, 84197, 84198, 84199, 84200,
                     84201, 84202, 84203, 84204, 84205, 84206, 84207, 84208, 84209,
                     84210, 84211, 84212, 84213, 84214, 84215, 84216, 84217, 84218,
                     84219, 84220, 84221, 84222, 84223, 84224, 84225, 84226, 84227,
                     84228, 84229, 84230, 84231, 84232, 84233, 84234, 84235, 84236,
                     84237],
                    dtype='int64'),
         761: Int64Index([81757, 81758, 81759, 81760, 81761, 81762, 81763, 81764, 81765,
                     81766, 81767, 81768, 81769, 81770, 81771, 81772, 81773, 81774,
                     81775, 81776, 81777, 81778, 81779, 81780, 81781, 81782, 81783,
                     81784, 81785, 81786, 81787, 81788, 81789, 81790, 81791, 81792,
                     81793, 81794, 81795, 81796, 81797, 81798, 81799, 81800],
                    dtype='int64'),
         762: Int64Index([5392, 5393, 5394, 5395, 5396, 5397, 5398, 5399, 5400, 5401,
                     ...
                     5497, 5498, 5499, 5500, 5501, 5502, 5503, 5504, 5505, 5506],
                    dtype='int64', length=115),
         763: Int64Index([49362, 49363, 49364, 49365, 49366, 49367, 49368, 49369, 49370,
                     49371,
                     ...
                     49501, 49502, 49503, 49504, 49505, 49506, 49507, 49508, 49509,
                     49510],
                    dtype='int64', length=149),
         764: Int64Index([38921, 38922, 38923, 38924, 38925, 38926, 38927, 38928, 38929,
                     38930, 38931, 38932, 38933, 38934, 38935, 38936, 38937, 38938,
                     38939, 38940, 38941, 38942, 38943, 38944, 38945, 38946, 38947,
                     38948, 38949],
                    dtype='int64'),
         765: Int64Index([87813, 87814, 87815, 87816, 87817, 87818, 87819, 87820, 87821,
                     87822, 87823, 87824, 87825, 87826, 87827, 87828, 87829, 87830,
                     87831, 87832, 87833, 87834, 87835, 87836, 87837, 87838, 87839,
                     87840, 87841, 87842, 87843, 87844],
                    dtype='int64'),
         766: Int64Index([80930, 80931, 80932, 80933, 80934, 80935, 80936, 80937, 80938], dtype='int64'),
         767: Int64Index([96779, 96780, 96781, 96782, 96783, 96784, 96785, 96786, 96787,
                     96788, 96789],
                    dtype='int64'),
         768: Int64Index([80991, 80992, 80993, 80994, 80995, 80996, 80997, 80998, 80999,
                     81000, 81001, 81002, 81003, 81004, 81005, 81006, 81007, 81008,
                     81009, 81010, 81011, 81012, 81013, 81014, 81015, 81016, 81017,
                     81018, 81019, 81020, 81021, 81022, 81023, 81024, 81025, 81026,
                     81027, 81028, 81029, 81030, 81031, 81032, 81033, 81034, 81035,
                     81036, 81037, 81038, 81039, 81040, 81041, 81042],
                    dtype='int64'),
         769: Int64Index([91275, 91276, 91277, 91278, 91279, 91280, 91281, 91282, 91283,
                     91284, 91285, 91286, 91287, 91288, 91289, 91290, 91291, 91292,
                     91293, 91294, 91295, 91296, 91297, 91298, 91299, 91300, 91301,
                     91302, 91303, 91304, 91305, 91306, 91307, 91308, 91309, 91310,
                     91311, 91312, 91313, 91314, 91315, 91316],
                    dtype='int64'),
         770: Int64Index([9058, 9059, 9060, 9061, 9062, 9063, 9064, 9065, 9066, 9067, 9068,
                     9069, 9070, 9071, 9072, 9073, 9074, 9075, 9076, 9077, 9078, 9079,
                     9080, 9081, 9082, 9083, 9084, 9085, 9086, 9087, 9088, 9089, 9090,
                     9091, 9092, 9093, 9094, 9095, 9096, 9097, 9098, 9099, 9100, 9101,
                     9102, 9103, 9104, 9105, 9106, 9107, 9108, 9109, 9110, 9111, 9112,
                     9113, 9114],
                    dtype='int64'),
         771: Int64Index([79933, 79934, 79935, 79936, 79937, 79938, 79939, 79940, 79941,
                     79942, 79943, 79944, 79945, 79946, 79947, 79948, 79949, 79950,
                     79951, 79952, 79953, 79954, 79955, 79956, 79957, 79958, 79959,
                     79960, 79961, 79962, 79963, 79964, 79965, 79966, 79967, 79968,
                     79969, 79970, 79971, 79972, 79973],
                    dtype='int64'),
         772: Int64Index([48236, 48237, 48238, 48239, 48240, 48241, 48242, 48243, 48244,
                     48245, 48246, 48247, 48248, 48249, 48250, 48251, 48252, 48253,
                     48254, 48255, 48256, 48257, 48258, 48259, 48260, 48261, 48262,
                     48263, 48264, 48265, 48266, 48267, 48268, 48269, 48270, 48271,
                     48272, 48273, 48274, 48275, 48276, 48277, 48278, 48279, 48280,
                     48281, 48282, 48283, 48284],
                    dtype='int64'),
         773: Int64Index([89699, 89700, 89701, 89702, 89703, 89704, 89705, 89706, 89707,
                     89708, 89709, 89710, 89711, 89712, 89713, 89714, 89715],
                    dtype='int64'),
         774: Int64Index([78245, 78246, 78247, 78248, 78249, 78250, 78251, 78252, 78253,
                     78254, 78255, 78256, 78257, 78258, 78259, 78260, 78261, 78262,
                     78263, 78264, 78265, 78266, 78267, 78268, 78269, 78270, 78271,
                     78272, 78273, 78274, 78275, 78276],
                    dtype='int64'),
         775: Int64Index([98412, 98413, 98414, 98415, 98416, 98417, 98418, 98419, 98420,
                     98421, 98422, 98423, 98424, 98425, 98426, 98427, 98428, 98429,
                     98430, 98431, 98432, 98433, 98434, 98435, 98436, 98437],
                    dtype='int64'),
         776: Int64Index([98693, 98694, 98695, 98696, 98697, 98698, 98699, 98700, 98701], dtype='int64'),
         777: Int64Index([98061, 98062, 98063, 98064], dtype='int64'),
         778: Int64Index([71382, 71383, 71384, 71385, 71386, 71387, 71388, 71389, 71390,
                     71391, 71392, 71393, 71394, 71395, 71396, 71397, 71398, 71399,
                     71400, 71401, 71402, 71403, 71404, 71405, 71406, 71407, 71408,
                     71409, 71410, 71411, 71412, 71413, 71414, 71415, 71416, 71417,
                     71418, 71419, 71420, 71421, 71422, 71423, 71424, 71425, 71426,
                     71427, 71428, 71429, 71430, 71431, 71432, 71433, 71434, 71435,
                     71436, 71437, 71438, 71439, 71440, 71441, 71442, 71443, 71444,
                     71445, 71446, 71447, 71448, 71449, 71450, 71451, 71452, 71453,
                     71454, 71455, 71456, 71457],
                    dtype='int64'),
         779: Int64Index([86618, 86619, 86620, 86621, 86622, 86623, 86624, 86625, 86626,
                     86627, 86628, 86629, 86630, 86631, 86632, 86633, 86634, 86635,
                     86636, 86637, 86638, 86639, 86640, 86641, 86642, 86643, 86644,
                     86645, 86646, 86647, 86648],
                    dtype='int64'),
         780: Int64Index([22095, 22096, 22097, 22098, 22099, 22100, 22101, 22102, 22103,
                     22104, 22105, 22106, 22107, 22108, 22109, 22110, 22111, 22112,
                     22113, 22114, 22115, 22116, 22117, 22118, 22119, 22120, 22121,
                     22122, 22123, 22124, 22125, 22126, 22127, 22128, 22129, 22130,
                     22131, 22132, 22133, 22134, 22135, 22136, 22137, 22138, 22139,
                     22140, 22141, 22142, 22143, 22144, 22145, 22146, 22147, 22148,
                     22149, 22150, 22151, 22152, 22153, 22154, 22155, 22156, 22157,
                     22158, 22159, 22160, 22161, 22162, 22163],
                    dtype='int64'),
         781: Int64Index([82084, 82085, 82086, 82087, 82088, 82089, 82090, 82091, 82092,
                     82093, 82094, 82095, 82096, 82097, 82098, 82099, 82100, 82101,
                     82102, 82103, 82104, 82105, 82106, 82107, 82108, 82109, 82110,
                     82111, 82112, 82113, 82114, 82115, 82116, 82117, 82118, 82119,
                     82120, 82121, 82122, 82123, 82124, 82125, 82126, 82127, 82128,
                     82129, 82130, 82131, 82132, 82133, 82134, 82135, 82136, 82137,
                     82138, 82139, 82140, 82141, 82142, 82143, 82144, 82145, 82146,
                     82147, 82148, 82149, 82150, 82151, 82152, 82153, 82154, 82155,
                     82156, 82157, 82158, 82159, 82160, 82161, 82162, 82163, 82164,
                     82165, 82166, 82167],
                    dtype='int64'),
         782: Int64Index([92577, 92578, 92579, 92580, 92581, 92582, 92583, 92584, 92585,
                     92586],
                    dtype='int64'),
         783: Int64Index([89910, 89911, 89912, 89913, 89914, 89915, 89916, 89917, 89918,
                     89919, 89920, 89921, 89922, 89923, 89924, 89925, 89926, 89927,
                     89928, 89929, 89930, 89931, 89932, 89933, 89934, 89935, 89936,
                     89937, 89938, 89939, 89940, 89941, 89942, 89943, 89944, 89945,
                     89946],
                    dtype='int64'),
         784: Int64Index([98707, 98708], dtype='int64'),
         785: Int64Index([86471, 86472, 86473, 86474, 86475, 86476, 86477, 86478, 86479,
                     86480, 86481, 86482, 86483, 86484, 86485, 86486, 86487, 86488,
                     86489, 86490, 86491, 86492, 86493, 86494, 86495, 86496, 86497,
                     86498, 86499, 86500, 86501, 86502, 86503, 86504, 86505, 86506,
                     86507, 86508, 86509],
                    dtype='int64'),
         786: Int64Index([97361, 97362, 97363, 97364, 97365, 97366, 97367, 97368, 97369,
                     97370, 97371, 97372, 97373, 97374],
                    dtype='int64'),
         787: Int64Index([95165, 95166, 95167, 95168, 95169, 95170, 95171, 95172, 95173,
                     95174, 95175, 95176, 95177],
                    dtype='int64'),
         788: Int64Index([98608, 98609, 98610], dtype='int64'),
         789: Int64Index([97239, 97240, 97241, 97242, 97243, 97244, 97245, 97246, 97247,
                     97248, 97249, 97250, 97251, 97252, 97253, 97254, 97255, 97256,
                     97257, 97258, 97259, 97260, 97261, 97262, 97263, 97264, 97265,
                     97266, 97267, 97268, 97269, 97270, 97271, 97272, 97273, 97274,
                     97275, 97276, 97277, 97278, 97279, 97280, 97281, 97282, 97283,
                     97284, 97285],
                    dtype='int64'),
         790: Int64Index([36163, 36164, 36165, 36166, 36167, 36168, 36169, 36170, 36171,
                     36172, 36173, 36174, 36175, 36176, 36177, 36178, 36179, 36180,
                     36181, 36182, 36183, 36184, 36185, 36186, 36187, 36188, 36189,
                     36190, 36191, 36192, 36193, 36194, 36195, 36196, 36197, 36198,
                     36199, 36200, 36201, 36202, 36203, 36204, 36205, 36206, 36207,
                     36208, 36209, 36210, 36211, 36212, 36213, 36214, 36215, 36216,
                     36217, 36218, 36219, 36220, 36221, 36222, 36223, 36224, 36225,
                     36226, 36227, 36228],
                    dtype='int64'),
         791: Int64Index([20828, 20829, 20830, 20831, 20832, 20833, 20834, 20835, 20836,
                     20837],
                    dtype='int64'),
         792: Int64Index([35030, 35031, 35032, 35033, 35034, 35035, 35036, 35037, 35038,
                     35039, 35040, 35041, 35042, 35043, 35044, 35045, 35046, 35047,
                     35048, 35049, 35050, 35051, 35052, 35053, 35054, 35055, 35056,
                     35057, 35058, 35059, 35060, 35061, 35062, 35063, 35064, 35065,
                     35066, 35067, 35068, 35069, 35070, 35071, 35072, 35073, 35074,
                     35075, 35076, 35077, 35078, 35079, 35080, 35081, 35082, 35083,
                     35084, 35085, 35086, 35087, 35088, 35089, 35090, 35091, 35092,
                     35093, 35094, 35095, 35096, 35097, 35098, 35099, 35100, 35101,
                     35102, 35103, 35104, 35105, 35106, 35107, 35108, 35109, 35110,
                     35111, 35112, 35113, 35114, 35115],
                    dtype='int64'),
         793: Int64Index([72748, 72749, 72750, 72751, 72752, 72753, 72754, 72755, 72756,
                     72757],
                    dtype='int64'),
         794: Int64Index([91229, 91230, 91231, 91232, 91233, 91234, 91235, 91236, 91237,
                     91238, 91239, 91240, 91241, 91242, 91243, 91244, 91245, 91246,
                     91247, 91248, 91249, 91250, 91251, 91252, 91253, 91254, 91255,
                     91256, 91257, 91258, 91259, 91260, 91261, 91262, 91263, 91264,
                     91265, 91266, 91267, 91268, 91269, 91270, 91271, 91272, 91273,
                     91274],
                    dtype='int64'),
         795: Int64Index([98761, 98762, 98763, 98764, 98765, 98766, 98767, 98768, 98769,
                     98770, 98771, 98772, 98773, 98774, 98775, 98776, 98777, 98778,
                     98779, 98780, 98781],
                    dtype='int64'),
         796: Int64Index([97203, 97204, 97205, 97206, 97207, 97208, 97209, 97210, 97211,
                     97212, 97213, 97214, 97215, 97216, 97217, 97218, 97219, 97220,
                     97221, 97222, 97223, 97224, 97225, 97226, 97227, 97228, 97229,
                     97230, 97231, 97232, 97233, 97234, 97235, 97236, 97237, 97238],
                    dtype='int64'),
         797: Int64Index([95526, 95527, 95528, 95529, 95530, 95531, 95532, 95533, 95534,
                     95535, 95536, 95537, 95538, 95539, 95540, 95541, 95542, 95543,
                     95544, 95545, 95546, 95547, 95548, 95549, 95550, 95551, 95552,
                     95553, 95554, 95555, 95556],
                    dtype='int64'),
         798: Int64Index([91602, 91603, 91604, 91605, 91606, 91607, 91608, 91609, 91610], dtype='int64'),
         799: Int64Index([98815, 98816, 98817, 98818, 98819], dtype='int64'),
         800: Int64Index([82789, 82790, 82791, 82792, 82793, 82794, 82795, 82796, 82797,
                     82798, 82799, 82800, 82801, 82802, 82803, 82804, 82805, 82806,
                     82807, 82808, 82809, 82810, 82811, 82812, 82813, 82814],
                    dtype='int64'),
         801: Int64Index([88931, 88932, 88933, 88934, 88935, 88936, 88937, 88938, 88939,
                     88940, 88941, 88942, 88943, 88944, 88945, 88946],
                    dtype='int64'),
         802: Int64Index([83270, 83271, 83272, 83273, 83274, 83275, 83276, 83277, 83278,
                     83279, 83280, 83281, 83282, 83283, 83284, 83285, 83286, 83287,
                     83288, 83289, 83290, 83291, 83292, 83293, 83294, 83295, 83296,
                     83297, 83298, 83299, 83300, 83301, 83302, 83303, 83304, 83305,
                     83306, 83307, 83308, 83309],
                    dtype='int64'),
         803: Int64Index([97425, 97426, 97427, 97428, 97429, 97430, 97431, 97432, 97433], dtype='int64'),
         804: Int64Index([98485, 98486, 98487, 98488, 98489, 98490, 98491, 98492], dtype='int64'),
         805: Int64Index([81449, 81450, 81451, 81452, 81453, 81454, 81455, 81456, 81457,
                     81458, 81459, 81460, 81461, 81462, 81463, 81464, 81465, 81466,
                     81467, 81468, 81469, 81470, 81471, 81472, 81473, 81474, 81475],
                    dtype='int64'),
         806: Int64Index([67684, 67685, 67686, 67687, 67688, 67689, 67690, 67691, 67692,
                     67693, 67694, 67695, 67696, 67697, 67698, 67699, 67700, 67701,
                     67702, 67703, 67704, 67705, 67706, 67707, 67708, 67709, 67710,
                     67711, 67712, 67713, 67714, 67715, 67716, 67717, 67718, 67719,
                     67720, 67721, 67722, 67723, 67724, 67725, 67726, 67727, 67728,
                     67729, 67730, 67731, 67732, 67733],
                    dtype='int64'),
         807: Int64Index([97693, 97694, 97695, 97696, 97697, 97698, 97699, 97700, 97701], dtype='int64'),
         808: Int64Index([88180, 88181, 88182, 88183, 88184, 88185, 88186, 88187, 88188,
                     88189, 88190, 88191, 88192, 88193, 88194, 88195, 88196, 88197,
                     88198, 88199, 88200, 88201, 88202, 88203, 88204, 88205, 88206,
                     88207, 88208, 88209, 88210],
                    dtype='int64'),
         809: Int64Index([87935, 87936, 87937, 87938, 87939, 87940, 87941, 87942, 87943,
                     87944, 87945, 87946, 87947, 87948, 87949, 87950, 87951, 87952,
                     87953, 87954, 87955, 87956, 87957, 87958, 87959, 87960, 87961,
                     87962, 87963, 87964, 87965, 87966, 87967, 87968, 87969, 87970,
                     87971, 87972, 87973, 87974, 87975, 87976, 87977],
                    dtype='int64'),
         810: Int64Index([95481, 95482, 95483, 95484, 95485, 95486, 95487, 95488, 95489,
                     95490, 95491, 95492, 95493, 95494, 95495, 95496, 95497, 95498,
                     95499, 95500, 95501, 95502, 95503, 95504, 95505, 95506, 95507,
                     95508, 95509, 95510, 95511, 95512, 95513, 95514, 95515, 95516,
                     95517, 95518, 95519, 95520, 95521, 95522, 95523, 95524, 95525],
                    dtype='int64'),
         811: Int64Index([94783, 94784, 94785, 94786, 94787, 94788, 94789, 94790, 94791,
                     94792, 94793, 94794, 94795, 94796, 94797, 94798, 94799, 94800],
                    dtype='int64'),
         812: Int64Index([84761, 84762, 84763, 84764, 84765, 84766, 84767, 84768, 84769,
                     84770, 84771, 84772, 84773, 84774, 84775, 84776, 84777, 84778],
                    dtype='int64'),
         813: Int64Index([89265, 89266, 89267, 89268, 89269, 89270, 89271, 89272, 89273,
                     89274, 89275, 89276, 89277, 89278, 89279, 89280, 89281, 89282,
                     89283, 89284, 89285, 89286, 89287, 89288, 89289, 89290, 89291,
                     89292, 89293, 89294, 89295, 89296, 89297, 89298, 89299, 89300,
                     89301, 89302, 89303, 89304, 89305, 89306, 89307, 89308, 89309,
                     89310, 89311, 89312, 89313, 89314, 89315, 89316, 89317, 89318,
                     89319, 89320],
                    dtype='int64'),
         814: Int64Index([98673], dtype='int64'),
         815: Int64Index([35331, 35332, 35333, 35334, 35335, 35336, 35337, 35338, 35339,
                     35340,
                     ...
                     35433, 35434, 35435, 35436, 35437, 35438, 35439, 35440, 35441,
                     35442],
                    dtype='int64', length=112),
         816: Int64Index([91018, 91019, 91020, 91021, 91022, 91023, 91024, 91025, 91026,
                     91027, 91028, 91029, 91030, 91031, 91032, 91033, 91034, 91035,
                     91036, 91037, 91038],
                    dtype='int64'),
         817: Int64Index([98808, 98809, 98810], dtype='int64'),
         818: Int64Index([38628, 38629, 38630, 38631, 38632, 38633, 38634, 38635, 38636,
                     38637, 38638, 38639, 38640, 38641, 38642, 38643, 38644, 38645,
                     38646, 38647, 38648, 38649, 38650, 38651, 38652],
                    dtype='int64'),
         819: Int64Index([81476, 81477, 81478, 81479, 81480, 81481, 81482, 81483, 81484,
                     81485, 81486, 81487, 81488, 81489, 81490, 81491, 81492, 81493,
                     81494, 81495, 81496, 81497, 81498, 81499, 81500, 81501, 81502,
                     81503, 81504, 81505, 81506, 81507, 81508, 81509, 81510, 81511,
                     81512, 81513, 81514, 81515],
                    dtype='int64'),
         820: Int64Index([18044, 18045, 18046, 18047, 18048, 18049, 18050, 18051, 18052,
                     18053, 18054, 18055, 18056, 18057, 18058, 18059, 18060, 18061,
                     18062, 18063, 18064, 18065, 18066, 18067, 18068, 18069, 18070,
                     18071, 18072, 18073, 18074, 18075, 18076, 18077, 18078, 18079,
                     18080, 18081, 18082, 18083, 18084, 18085, 18086, 18087, 18088,
                     18089, 18090, 18091, 18092, 18093, 18094, 18095, 18096, 18097,
                     18098, 18099, 18100, 18101, 18102, 18103, 18104, 18105, 18106,
                     18107, 18108, 18109, 18110, 18111, 18112, 18113, 18114, 18115,
                     18116, 18117, 18118, 18119, 18120, 18121, 18122, 18123, 18124,
                     18125, 18126, 18127, 18128, 18129, 18130, 18131, 18132, 18133,
                     18134, 18135, 18136],
                    dtype='int64'),
         821: Int64Index([82295, 82296, 82297, 82298, 82299, 82300, 82301, 82302, 82303,
                     82304, 82305, 82306, 82307, 82308, 82309, 82310, 82311, 82312,
                     82313, 82314, 82315, 82316],
                    dtype='int64'),
         822: Int64Index([95016, 95017, 95018, 95019], dtype='int64'),
         823: Int64Index([91425, 91426, 91427, 91428, 91429, 91430, 91431, 91432, 91433,
                     91434, 91435, 91436, 91437, 91438, 91439, 91440, 91441, 91442,
                     91443, 91444, 91445, 91446, 91447, 91448, 91449, 91450, 91451,
                     91452, 91453, 91454, 91455, 91456, 91457, 91458, 91459, 91460,
                     91461, 91462, 91463, 91464, 91465, 91466, 91467, 91468, 91469,
                     91470, 91471, 91472, 91473, 91474, 91475, 91476, 91477, 91478,
                     91479, 91480, 91481, 91482, 91483, 91484, 91485, 91486, 91487,
                     91488, 91489, 91490, 91491, 91492, 91493, 91494, 91495, 91496,
                     91497, 91498, 91499, 91500, 91501, 91502, 91503, 91504, 91505,
                     91506],
                    dtype='int64'),
         824: Int64Index([80939, 80940, 80941, 80942, 80943, 80944, 80945, 80946, 80947,
                     80948, 80949, 80950, 80951, 80952, 80953, 80954, 80955, 80956,
                     80957, 80958, 80959, 80960, 80961, 80962, 80963, 80964, 80965,
                     80966, 80967, 80968, 80969, 80970, 80971, 80972, 80973, 80974,
                     80975, 80976, 80977, 80978, 80979, 80980, 80981, 80982, 80983,
                     80984, 80985, 80986, 80987],
                    dtype='int64'),
         825: Int64Index([88016, 88017, 88018, 88019, 88020, 88021, 88022, 88023, 88024,
                     88025, 88026, 88027, 88028, 88029, 88030, 88031, 88032, 88033,
                     88034, 88035, 88036, 88037, 88038, 88039, 88040, 88041, 88042,
                     88043, 88044, 88045, 88046, 88047, 88048, 88049, 88050, 88051,
                     88052, 88053, 88054, 88055, 88056, 88057, 88058, 88059, 88060,
                     88061, 88062, 88063, 88064, 88065, 88066, 88067, 88068, 88069,
                     88070, 88071, 88072, 88073, 88074, 88075, 88076, 88077, 88078,
                     88079, 88080, 88081, 88082, 88083, 88084, 88085, 88086, 88087,
                     88088, 88089, 88090, 88091, 88092, 88093, 88094, 88095, 88096,
                     88097, 88098],
                    dtype='int64'),
         826: Int64Index([83961, 83962, 83963, 83964, 83965, 83966, 83967, 83968, 83969,
                     83970, 83971, 83972, 83973, 83974, 83975, 83976, 83977, 83978,
                     83979, 83980, 83981, 83982, 83983, 83984, 83985, 83986, 83987,
                     83988, 83989, 83990, 83991, 83992, 83993, 83994, 83995, 83996,
                     83997, 83998, 83999, 84000, 84001, 84002, 84003, 84004, 84005,
                     84006, 84007, 84008, 84009, 84010, 84011, 84012, 84013, 84014,
                     84015, 84016, 84017, 84018, 84019, 84020, 84021, 84022, 84023,
                     84024, 84025, 84026, 84027, 84028, 84029, 84030, 84031, 84032,
                     84033, 84034, 84035, 84036, 84037, 84038, 84039, 84040],
                    dtype='int64'),
         827: Int64Index([78149, 78150, 78151, 78152, 78153, 78154, 78155, 78156, 78157,
                     78158, 78159, 78160, 78161, 78162, 78163, 78164, 78165, 78166,
                     78167, 78168, 78169, 78170, 78171, 78172, 78173, 78174, 78175,
                     78176, 78177, 78178, 78179, 78180, 78181, 78182, 78183, 78184,
                     78185, 78186, 78187, 78188, 78189, 78190, 78191, 78192, 78193,
                     78194, 78195, 78196, 78197, 78198, 78199, 78200, 78201, 78202,
                     78203, 78204, 78205],
                    dtype='int64'),
         828: Int64Index([95686, 95687, 95688, 95689, 95690, 95691, 95692, 95693, 95694,
                     95695, 95696, 95697, 95698],
                    dtype='int64'),
         829: Int64Index([14437, 14438, 14439, 14440, 14441, 14442, 14443, 14444, 14445,
                     14446, 14447, 14448, 14449, 14450, 14451, 14452, 14453, 14454,
                     14455, 14456, 14457, 14458, 14459, 14460, 14461, 14462, 14463,
                     14464, 14465, 14466, 14467, 14468, 14469, 14470],
                    dtype='int64'),
         830: Int64Index([98574], dtype='int64'),
         831: Int64Index([82917, 82918, 82919, 82920, 82921, 82922, 82923, 82924, 82925,
                     82926, 82927, 82928, 82929, 82930, 82931, 82932, 82933, 82934,
                     82935, 82936, 82937, 82938, 82939, 82940, 82941, 82942, 82943,
                     82944, 82945, 82946, 82947, 82948, 82949, 82950, 82951, 82952,
                     82953, 82954, 82955, 82956, 82957, 82958, 82959, 82960, 82961,
                     82962, 82963, 82964, 82965, 82966, 82967, 82968, 82969, 82970,
                     82971, 82972, 82973, 82974, 82975, 82976, 82977, 82978, 82979,
                     82980, 82981, 82982, 82983, 82984, 82985, 82986, 82987, 82988,
                     82989, 82990, 82991, 82992, 82993, 82994, 82995, 82996, 82997,
                     82998, 82999, 83000, 83001, 83002, 83003, 83004, 83005, 83006,
                     83007],
                    dtype='int64'),
         832: Int64Index([85212, 85213, 85214, 85215, 85216, 85217, 85218, 85219, 85220,
                     85221, 85222, 85223, 85224, 85225, 85226, 85227, 85228, 85229,
                     85230, 85231, 85232, 85233],
                    dtype='int64'),
         833: Int64Index([45646, 45647, 45648, 45649, 45650, 45651, 45652, 45653, 45654,
                     45655, 45656, 45657, 45658, 45659, 45660, 45661, 45662, 45663,
                     45664, 45665, 45666, 45667, 45668, 45669, 45670, 45671, 45672,
                     45673, 45674, 45675, 45676, 45677, 45678, 45679, 45680, 45681,
                     45682, 45683, 45684, 45685, 45686, 45687, 45688, 45689, 45690,
                     45691, 45692, 45693, 45694],
                    dtype='int64'),
         834: Int64Index([91126, 91127, 91128, 91129, 91130, 91131, 91132, 91133, 91134,
                     91135, 91136, 91137, 91138, 91139, 91140, 91141, 91142, 91143,
                     91144, 91145, 91146, 91147, 91148, 91149, 91150],
                    dtype='int64'),
         835: Int64Index([94193, 94194, 94195, 94196, 94197, 94198, 94199, 94200, 94201,
                     94202, 94203, 94204, 94205, 94206, 94207],
                    dtype='int64'),
         836: Int64Index([93619, 93620, 93621, 93622, 93623, 93624, 93625, 93626, 93627,
                     93628, 93629, 93630, 93631, 93632, 93633, 93634, 93635, 93636,
                     93637, 93638, 93639, 93640, 93641, 93642, 93643, 93644],
                    dtype='int64'),
         837: Int64Index([90740, 90741, 90742, 90743, 90744, 90745, 90746, 90747, 90748,
                     90749, 90750, 90751, 90752, 90753, 90754, 90755, 90756, 90757,
                     90758, 90759, 90760, 90761, 90762, 90763, 90764],
                    dtype='int64'),
         838: Int64Index([95276, 95277, 95278, 95279], dtype='int64'),
         839: Int64Index([98740, 98741, 98742, 98743], dtype='int64'),
         840: Int64Index([27205, 27206, 27207, 27208, 27209, 27210, 27211, 27212, 27213,
                     27214, 27215, 27216, 27217, 27218, 27219, 27220, 27221, 27222,
                     27223, 27224, 27225, 27226, 27227, 27228, 27229, 27230, 27231,
                     27232, 27233, 27234, 27235, 27236, 27237, 27238, 27239, 27240,
                     27241, 27242, 27243, 27244, 27245, 27246, 27247, 27248, 27249,
                     27250, 27251, 27252, 27253, 27254, 27255, 27256, 27257],
                    dtype='int64'),
         841: Int64Index([83913, 83914, 83915, 83916, 83917, 83918, 83919, 83920, 83921,
                     83922, 83923, 83924, 83925, 83926, 83927, 83928, 83929, 83930,
                     83931, 83932, 83933, 83934, 83935, 83936, 83937, 83938, 83939,
                     83940, 83941, 83942, 83943, 83944, 83945, 83946, 83947, 83948,
                     83949, 83950, 83951, 83952, 83953, 83954, 83955, 83956, 83957,
                     83958, 83959, 83960],
                    dtype='int64'),
         842: Int64Index([57102, 57103, 57104, 57105, 57106, 57107, 57108, 57109, 57110,
                     57111, 57112, 57113, 57114, 57115, 57116, 57117, 57118, 57119,
                     57120, 57121, 57122, 57123, 57124, 57125, 57126, 57127, 57128],
                    dtype='int64'),
         843: Int64Index([94097, 94098, 94099, 94100, 94101, 94102, 94103, 94104, 94105,
                     94106, 94107, 94108, 94109, 94110, 94111, 94112, 94113, 94114,
                     94115, 94116, 94117, 94118, 94119, 94120, 94121, 94122, 94123,
                     94124, 94125, 94126],
                    dtype='int64'),
         844: Int64Index([87553, 87554, 87555, 87556, 87557, 87558, 87559, 87560, 87561,
                     87562, 87563, 87564, 87565, 87566, 87567, 87568, 87569, 87570,
                     87571, 87572, 87573, 87574, 87575, 87576, 87577, 87578, 87579,
                     87580, 87581, 87582, 87583, 87584, 87585, 87586, 87587, 87588,
                     87589, 87590, 87591, 87592, 87593, 87594],
                    dtype='int64'),
         845: Int64Index([5863, 5864, 5865, 5866, 5867, 5868, 5869, 5870, 5871, 5872,
                     ...
                     6029, 6030, 6031, 6032, 6033, 6034, 6035, 6036, 6037, 6038],
                    dtype='int64', length=176),
         846: Int64Index([85824, 85825, 85826, 85827, 85828, 85829, 85830, 85831, 85832,
                     85833, 85834, 85835, 85836, 85837, 85838, 85839, 85840, 85841,
                     85842, 85843, 85844, 85845, 85846, 85847, 85848, 85849, 85850,
                     85851, 85852, 85853, 85854, 85855, 85856, 85857, 85858, 85859,
                     85860, 85861, 85862, 85863, 85864, 85865, 85866, 85867],
                    dtype='int64'),
         847: Int64Index([65762, 65763, 65764, 65765, 65766, 65767, 65768, 65769, 65770,
                     65771, 65772, 65773, 65774, 65775, 65776, 65777, 65778, 65779,
                     65780, 65781, 65782, 65783, 65784, 65785, 65786, 65787, 65788,
                     65789, 65790, 65791, 65792, 65793, 65794, 65795, 65796, 65797,
                     65798, 65799, 65800, 65801, 65802, 65803, 65804, 65805, 65806,
                     65807, 65808, 65809, 65810, 65811, 65812, 65813, 65814, 65815,
                     65816],
                    dtype='int64'),
         848: Int64Index([92659, 92660, 92661, 92662, 92663, 92664, 92665, 92666, 92667], dtype='int64'),
         849: Int64Index([87241, 87242, 87243, 87244, 87245, 87246, 87247, 87248, 87249,
                     87250, 87251, 87252, 87253, 87254, 87255, 87256, 87257, 87258,
                     87259, 87260, 87261, 87262, 87263, 87264, 87265, 87266, 87267,
                     87268, 87269, 87270, 87271, 87272, 87273, 87274, 87275, 87276,
                     87277, 87278, 87279, 87280, 87281, 87282, 87283, 87284, 87285,
                     87286, 87287, 87288, 87289, 87290, 87291, 87292, 87293],
                    dtype='int64'),
         850: Int64Index([92329, 92330, 92331, 92332], dtype='int64'),
         851: Int64Index([98782, 98783, 98784, 98785], dtype='int64'),
         852: Int64Index([98739], dtype='int64'),
         853: Int64Index([95113, 95114, 95115, 95116, 95117, 95118, 95119, 95120, 95121,
                     95122, 95123, 95124, 95125, 95126],
                    dtype='int64'),
         854: Int64Index([97375, 97376, 97377, 97378, 97379, 97380, 97381, 97382, 97383,
                     97384, 97385, 97386, 97387, 97388, 97389, 97390],
                    dtype='int64'),
         855: Int64Index([92886, 92887, 92888, 92889, 92890, 92891, 92892, 92893, 92894,
                     92895, 92896, 92897, 92898, 92899, 92900, 92901, 92902, 92903,
                     92904, 92905, 92906, 92907, 92908, 92909, 92910, 92911, 92912,
                     92913, 92914, 92915, 92916, 92917, 92918, 92919, 92920, 92921,
                     92922, 92923, 92924, 92925, 92926, 92927, 92928, 92929, 92930,
                     92931, 92932, 92933, 92934, 92935, 92936, 92937, 92938, 92939,
                     92940, 92941, 92942, 92943, 92944, 92945, 92946, 92947, 92948,
                     92949, 92950, 92951],
                    dtype='int64'),
         856: Int64Index([44533, 44534, 44535, 44536, 44537, 44538, 44539, 44540, 44541,
                     44542, 44543, 44544, 44545, 44546, 44547, 44548, 44549, 44550,
                     44551, 44552, 44553, 44554, 44555, 44556, 44557, 44558, 44559,
                     44560, 44561, 44562, 44563, 44564, 44565, 44566, 44567, 44568],
                    dtype='int64'),
         857: Int64Index([98729], dtype='int64'),
         858: Int64Index([98533, 98534, 98535], dtype='int64'),
         859: Int64Index([98575, 98576, 98577, 98578, 98579, 98580, 98581, 98582, 98583,
                     98584, 98585, 98586, 98587, 98588, 98589],
                    dtype='int64'),
         860: Int64Index([98592, 98593, 98594, 98595, 98596, 98597, 98598, 98599, 98600,
                     98601, 98602, 98603, 98604, 98605, 98606, 98607],
                    dtype='int64'),
         861: Int64Index([98704, 98705, 98706], dtype='int64'),
         862: Int64Index([27365, 27366, 27367, 27368, 27369, 27370, 27371, 27372, 27373,
                     27374, 27375, 27376, 27377, 27378, 27379, 27380, 27381, 27382],
                    dtype='int64'),
         863: Int64Index([73736, 73737, 73738, 73739, 73740, 73741, 73742, 73743, 73744,
                     73745, 73746, 73747, 73748, 73749, 73750, 73751, 73752, 73753,
                     73754, 73755, 73756, 73757, 73758, 73759],
                    dtype='int64'),
         864: Int64Index([59251, 59252, 59253, 59254, 59255, 59256, 59257, 59258, 59259,
                     59260, 59261, 59262, 59263, 59264, 59265, 59266, 59267, 59268,
                     59269, 59270, 59271, 59272, 59273, 59274, 59275, 59276, 59277,
                     59278, 59279, 59280, 59281, 59282, 59283, 59284, 59285, 59286,
                     59287, 59288, 59289, 59290, 59291, 59292, 59293, 59294, 59295,
                     59296, 59297, 59298, 59299, 59300, 59301, 59302, 59303, 59304,
                     59305, 59306, 59307, 59308, 59309, 59310, 59311, 59312, 59313,
                     59314, 59315, 59316, 59317, 59318, 59319, 59320, 59321, 59322,
                     59323, 59324, 59325, 59326, 59327, 59328, 59329, 59330, 59331,
                     59332, 59333, 59334, 59335, 59336],
                    dtype='int64'),
         865: Int64Index([74406, 74407, 74408, 74409, 74410, 74411, 74412, 74413, 74414,
                     74415, 74416, 74417, 74418, 74419, 74420, 74421, 74422, 74423,
                     74424, 74425, 74426],
                    dtype='int64'),
         866: Int64Index([43466, 43467, 43468, 43469, 43470, 43471, 43472, 43473, 43474,
                     43475,
                     ...
                     43575, 43576, 43577, 43578, 43579, 43580, 43581, 43582, 43583,
                     43584],
                    dtype='int64', length=119),
         867: Int64Index([86912, 86913, 86914, 86915, 86916, 86917], dtype='int64'),
         868: Int64Index([98536, 98537, 98538, 98539, 98540], dtype='int64'),
         869: Int64Index([89947, 89948, 89949, 89950, 89951, 89952, 89953, 89954, 89955,
                     89956, 89957, 89958, 89959, 89960, 89961, 89962, 89963, 89964,
                     89965, 89966, 89967, 89968, 89969, 89970],
                    dtype='int64'),
         870: Int64Index([96010, 96011, 96012, 96013, 96014, 96015, 96016, 96017, 96018], dtype='int64'),
         871: Int64Index([26207, 26208, 26209, 26210, 26211, 26212, 26213, 26214, 26215,
                     26216, 26217, 26218, 26219, 26220, 26221, 26222, 26223, 26224,
                     26225, 26226, 26227, 26228, 26229, 26230, 26231, 26232, 26233,
                     26234, 26235, 26236, 26237, 26238, 26239, 26240, 26241, 26242,
                     26243, 26244, 26245, 26246, 26247, 26248, 26249, 26250, 26251,
                     26252, 26253, 26254, 26255, 26256, 26257, 26258, 26259, 26260,
                     26261, 26262, 26263, 26264, 26265, 26266, 26267, 26268, 26269,
                     26270, 26271, 26272, 26273, 26274, 26275, 26276, 26277, 26278,
                     26279, 26280, 26281],
                    dtype='int64'),
         872: Int64Index([88131, 88132, 88133, 88134, 88135, 88136, 88137, 88138, 88139,
                     88140, 88141, 88142, 88143, 88144, 88145, 88146, 88147, 88148,
                     88149, 88150, 88151, 88152, 88153, 88154, 88155, 88156, 88157,
                     88158, 88159, 88160, 88161, 88162, 88163, 88164, 88165, 88166,
                     88167, 88168, 88169, 88170, 88171, 88172],
                    dtype='int64'),
         873: Int64Index([85490, 85491, 85492, 85493, 85494, 85495, 85496, 85497, 85498,
                     85499, 85500, 85501, 85502, 85503, 85504, 85505, 85506, 85507,
                     85508, 85509, 85510, 85511, 85512, 85513, 85514, 85515, 85516,
                     85517, 85518, 85519, 85520, 85521, 85522, 85523, 85524, 85525,
                     85526, 85527, 85528, 85529, 85530, 85531, 85532, 85533, 85534,
                     85535, 85536, 85537, 85538, 85539, 85540, 85541, 85542, 85543,
                     85544, 85545, 85546, 85547, 85548, 85549, 85550, 85551, 85552,
                     85553, 85554, 85555, 85556, 85557, 85558, 85559, 85560, 85561,
                     85562, 85563, 85564, 85565, 85566, 85567, 85568, 85569, 85570],
                    dtype='int64'),
         874: Int64Index([92530, 92531, 92532, 92533, 92534, 92535, 92536, 92537, 92538,
                     92539, 92540, 92541, 92542, 92543, 92544, 92545, 92546, 92547,
                     92548, 92549, 92550, 92551, 92552, 92553, 92554, 92555, 92556,
                     92557, 92558, 92559, 92560, 92561, 92562, 92563, 92564, 92565,
                     92566, 92567, 92568],
                    dtype='int64'),
         875: Int64Index([78552, 78553, 78554, 78555, 78556, 78557, 78558, 78559, 78560,
                     78561, 78562, 78563, 78564, 78565, 78566, 78567, 78568, 78569,
                     78570, 78571, 78572, 78573, 78574, 78575, 78576, 78577, 78578,
                     78579, 78580, 78581, 78582, 78583, 78584, 78585, 78586, 78587,
                     78588, 78589, 78590, 78591, 78592, 78593, 78594, 78595, 78596,
                     78597, 78598, 78599, 78600, 78601, 78602, 78603, 78604],
                    dtype='int64'),
         876: Int64Index([96790, 96791, 96792, 96793, 96794, 96795, 96796, 96797, 96798,
                     96799, 96800, 96801, 96802, 96803, 96804, 96805, 96806, 96807,
                     96808, 96809, 96810, 96811, 96812, 96813, 96814, 96815, 96816,
                     96817, 96818, 96819, 96820, 96821, 96822, 96823, 96824, 96825,
                     96826, 96827, 96828, 96829, 96830, 96831, 96832, 96833, 96834,
                     96835, 96836],
                    dtype='int64'),
         877: Int64Index([96681, 96682, 96683, 96684, 96685, 96686, 96687, 96688, 96689,
                     96690, 96691, 96692, 96693, 96694, 96695, 96696, 96697, 96698,
                     96699, 96700, 96701, 96702, 96703, 96704, 96705, 96706, 96707,
                     96708, 96709, 96710, 96711, 96712, 96713, 96714, 96715, 96716,
                     96717, 96718, 96719, 96720, 96721, 96722, 96723, 96724, 96725,
                     96726, 96727, 96728, 96729, 96730, 96731, 96732],
                    dtype='int64'),
         878: Int64Index([23705, 23706, 23707, 23708, 23709, 23710, 23711, 23712, 23713,
                     23714, 23715, 23716, 23717, 23718, 23719, 23720, 23721, 23722,
                     23723, 23724, 23725, 23726, 23727, 23728, 23729, 23730, 23731,
                     23732, 23733, 23734, 23735, 23736, 23737],
                    dtype='int64'),
         879: Int64Index([85677, 85678, 85679, 85680, 85681, 85682, 85683, 85684, 85685,
                     85686,
                     ...
                     85803, 85804, 85805, 85806, 85807, 85808, 85809, 85810, 85811,
                     85812],
                    dtype='int64', length=136),
         880: Int64Index([16476, 16477, 16478, 16479, 16480, 16481, 16482, 16483, 16484,
                     16485, 16486, 16487, 16488, 16489, 16490, 16491, 16492, 16493,
                     16494, 16495, 16496, 16497, 16498, 16499, 16500, 16501, 16502,
                     16503, 16504, 16505, 16506, 16507, 16508, 16509, 16510, 16511,
                     16512, 16513, 16514, 16515, 16516, 16517, 16518, 16519, 16520,
                     16521, 16522, 16523, 16524, 16525, 16526, 16527, 16528, 16529,
                     16530, 16531, 16532, 16533, 16534],
                    dtype='int64'),
         881: Int64Index([80735, 80736, 80737, 80738, 80739, 80740, 80741, 80742, 80743,
                     80744, 80745, 80746, 80747, 80748, 80749, 80750, 80751, 80752,
                     80753, 80754, 80755, 80756, 80757, 80758, 80759, 80760, 80761,
                     80762, 80763, 80764, 80765, 80766, 80767, 80768, 80769, 80770,
                     80771, 80772, 80773, 80774, 80775, 80776, 80777, 80778, 80779],
                    dtype='int64'),
         882: Int64Index([96182, 96183, 96184, 96185, 96186, 96187, 96188, 96189, 96190,
                     96191, 96192, 96193, 96194, 96195, 96196, 96197, 96198, 96199,
                     96200, 96201, 96202, 96203, 96204, 96205, 96206, 96207, 96208,
                     96209, 96210, 96211, 96212, 96213, 96214, 96215],
                    dtype='int64'),
         883: Int64Index([81286, 81287, 81288, 81289, 81290, 81291, 81292, 81293, 81294,
                     81295, 81296, 81297, 81298],
                    dtype='int64'),
         884: Int64Index([82202, 82203, 82204, 82205, 82206, 82207, 82208], dtype='int64'),
         885: Int64Index([96903, 96904, 96905, 96906, 96907, 96908, 96909, 96910, 96911,
                     96912, 96913, 96914, 96915],
                    dtype='int64'),
         886: Int64Index([40855, 40856, 40857, 40858, 40859, 40860, 40861, 40862, 40863,
                     40864, 40865, 40866, 40867, 40868, 40869, 40870, 40871, 40872,
                     40873, 40874, 40875, 40876, 40877, 40878, 40879, 40880, 40881,
                     40882, 40883, 40884, 40885, 40886, 40887, 40888, 40889, 40890,
                     40891, 40892, 40893, 40894, 40895, 40896, 40897, 40898, 40899,
                     40900, 40901, 40902, 40903, 40904, 40905, 40906, 40907],
                    dtype='int64'),
         887: Int64Index([18169, 18170, 18171, 18172, 18173, 18174, 18175, 18176, 18177,
                     18178, 18179, 18180, 18181, 18182, 18183, 18184, 18185, 18186,
                     18187, 18188, 18189, 18190, 18191, 18192, 18193, 18194, 18195,
                     18196, 18197, 18198, 18199, 18200, 18201, 18202, 18203, 18204,
                     18205, 18206, 18207, 18208, 18209, 18210, 18211, 18212, 18213,
                     18214, 18215, 18216, 18217, 18218, 18219, 18220, 18221, 18222,
                     18223, 18224, 18225, 18226, 18227, 18228, 18229, 18230, 18231,
                     18232],
                    dtype='int64'),
         888: Int64Index([81955, 81956, 81957, 81958, 81959, 81960, 81961, 81962, 81963,
                     81964, 81965, 81966, 81967, 81968, 81969],
                    dtype='int64'),
         889: Int64Index([94616, 94617, 94618, 94619, 94620, 94621, 94622, 94623, 94624,
                     94625, 94626, 94627, 94628],
                    dtype='int64'),
         890: Int64Index([84341, 84342, 84343, 84344, 84345, 84346, 84347, 84348, 84349,
                     84350, 84351, 84352, 84353, 84354, 84355, 84356, 84357, 84358,
                     84359, 84360, 84361, 84362, 84363, 84364, 84365, 84366, 84367,
                     84368, 84369, 84370, 84371, 84372, 84373, 84374, 84375, 84376,
                     84377, 84378, 84379, 84380, 84381, 84382, 84383],
                    dtype='int64'),
         891: Int64Index([98378, 98379, 98380, 98381, 98382, 98383], dtype='int64'),
         892: Int64Index([82815, 82816, 82817, 82818, 82819, 82820, 82821, 82822, 82823,
                     82824, 82825, 82826, 82827, 82828, 82829, 82830, 82831, 82832,
                     82833, 82834, 82835, 82836, 82837, 82838, 82839, 82840, 82841,
                     82842, 82843, 82844, 82845, 82846, 82847, 82848, 82849, 82850,
                     82851, 82852, 82853, 82854, 82855, 82856, 82857, 82858, 82859,
                     82860, 82861, 82862, 82863, 82864, 82865, 82866, 82867],
                    dtype='int64'),
         893: Int64Index([85868, 85869, 85870, 85871, 85872, 85873, 85874, 85875, 85876,
                     85877, 85878, 85879, 85880, 85881],
                    dtype='int64'),
         894: Int64Index([54928, 54929, 54930, 54931, 54932, 54933, 54934, 54935, 54936,
                     54937, 54938, 54939, 54940, 54941, 54942, 54943, 54944, 54945,
                     54946],
                    dtype='int64'),
         895: Int64Index([68600, 68601, 68602, 68603, 68604, 68605, 68606, 68607, 68608,
                     68609,
                     ...
                     68696, 68697, 68698, 68699, 68700, 68701, 68702, 68703, 68704,
                     68705],
                    dtype='int64', length=106),
         896: Int64Index([98084, 98085, 98086, 98087, 98088, 98089, 98090, 98091, 98092,
                     98093, 98094, 98095, 98096, 98097, 98098, 98099, 98100, 98101,
                     98102, 98103, 98104, 98105, 98106, 98107, 98108, 98109, 98110,
                     98111, 98112, 98113, 98114, 98115, 98116, 98117, 98118, 98119,
                     98120, 98121, 98122, 98123, 98124, 98125, 98126, 98127],
                    dtype='int64'),
         897: Int64Index([98806, 98807], dtype='int64'),
         898: Int64Index([98615, 98616, 98617, 98618, 98619, 98620, 98621, 98622, 98623,
                     98624, 98625, 98626, 98627, 98628, 98629, 98630, 98631, 98632,
                     98633, 98634, 98635, 98636, 98637, 98638, 98639, 98640, 98641,
                     98642, 98643, 98644, 98645, 98646, 98647, 98648, 98649, 98650,
                     98651, 98652, 98653, 98654, 98655, 98656, 98657, 98658, 98659,
                     98660, 98661, 98662, 98663, 98664, 98665, 98666, 98667, 98668,
                     98669, 98670, 98671, 98672],
                    dtype='int64'),
         899: Int64Index([98847, 98848, 98849, 98850, 98851, 98852, 98853, 98854, 98855], dtype='int64'),
         900: Int64Index([97993, 97994, 97995, 97996, 97997, 97998, 97999, 98000, 98001,
                     98002, 98003, 98004, 98005, 98006, 98007, 98008, 98009, 98010,
                     98011, 98012, 98013, 98014, 98015, 98016, 98017, 98018, 98019,
                     98020, 98021, 98022, 98023, 98024, 98025, 98026, 98027, 98028,
                     98029, 98030, 98031, 98032, 98033, 98034],
                    dtype='int64'),
         901: Int64Index([98521, 98522, 98523, 98524, 98525, 98526, 98527, 98528, 98529,
                     98530, 98531, 98532],
                    dtype='int64'),
         902: Int64Index([97651, 97652, 97653, 97654, 97655, 97656, 97657, 97658, 97659,
                     97660, 97661, 97662, 97663, 97664, 97665, 97666, 97667, 97668,
                     97669, 97670, 97671, 97672, 97673, 97674, 97675, 97676, 97677,
                     97678, 97679, 97680, 97681, 97682, 97683, 97684, 97685, 97686,
                     97687, 97688, 97689, 97690, 97691, 97692],
                    dtype='int64'),
         903: Int64Index([98035, 98036, 98037, 98038, 98039, 98040, 98041, 98042, 98043,
                     98044, 98045, 98046, 98047, 98048, 98049, 98050, 98051, 98052],
                    dtype='int64'),
         904: Int64Index([71881, 71882, 71883, 71884, 71885, 71886, 71887, 71888, 71889,
                     71890, 71891, 71892, 71893, 71894, 71895, 71896, 71897, 71898,
                     71899, 71900],
                    dtype='int64'),
         905: Int64Index([98820, 98821, 98822, 98823, 98824, 98825, 98826, 98827, 98828,
                     98829, 98830, 98831, 98832, 98833, 98834, 98835, 98836, 98837,
                     98838, 98839, 98840, 98841, 98842, 98843, 98844, 98845, 98846],
                    dtype='int64'),
         906: Int64Index([82703, 82704, 82705, 82706, 82707, 82708, 82709, 82710, 82711,
                     82712, 82713, 82714, 82715, 82716, 82717, 82718, 82719, 82720,
                     82721, 82722, 82723],
                    dtype='int64'),
         907: Int64Index([98702, 98703], dtype='int64'),
         908: Int64Index([98554, 98555, 98556, 98557, 98558, 98559, 98560, 98561, 98562,
                     98563, 98564, 98565, 98566, 98567, 98568, 98569, 98570, 98571,
                     98572, 98573],
                    dtype='int64'),
         909: Int64Index([98748, 98749, 98750, 98751, 98752, 98753, 98754, 98755, 98756,
                     98757, 98758, 98759, 98760],
                    dtype='int64'),
         910: Int64Index([98611, 98612, 98613, 98614], dtype='int64'),
         911: Int64Index([98811, 98812, 98813, 98814], dtype='int64'),
         912: Int64Index([98730, 98731, 98732, 98733, 98734, 98735, 98736, 98737, 98738], dtype='int64'),
         913: Int64Index([98590, 98591], dtype='int64'),
         914: Int64Index([98786, 98787, 98788, 98789, 98790, 98791, 98792, 98793, 98794,
                     98795, 98796],
                    dtype='int64'),
         915: Int64Index([94820, 94821, 94822, 94823, 94824, 94825, 94826, 94827, 94828,
                     94829, 94830, 94831, 94832],
                    dtype='int64'),
         916: Int64Index([94382, 94383, 94384, 94385, 94386, 94387, 94388, 94389, 94390,
                     94391, 94392, 94393, 94394, 94395, 94396, 94397, 94398, 94399],
                    dtype='int64'),
         917: Int64Index([94435, 94436, 94437, 94438, 94439, 94440, 94441], dtype='int64'),
         918: Int64Index([98546, 98547, 98548, 98549, 98550, 98551, 98552, 98553], dtype='int64'),
         919: Int64Index([86510, 86511, 86512, 86513, 86514, 86515, 86516, 86517, 86518,
                     86519, 86520, 86521, 86522, 86523, 86524, 86525, 86526, 86527,
                     86528, 86529, 86530, 86531, 86532, 86533, 86534, 86535, 86536,
                     86537, 86538, 86539, 86540, 86541, 86542, 86543, 86544, 86545,
                     86546, 86547, 86548, 86549, 86550, 86551, 86552, 86553, 86554,
                     86555, 86556, 86557, 86558, 86559, 86560, 86561, 86562, 86563,
                     86564, 86565, 86566, 86567, 86568, 86569, 86570, 86571, 86572,
                     86573, 86574, 86575, 86576, 86577, 86578, 86579, 86580, 86581,
                     86582, 86583, 86584, 86585, 86586, 86587, 86588, 86589, 86590,
                     86591, 86592, 86593, 86594, 86595, 86596, 86597, 86598, 86599,
                     86600, 86601, 86602, 86603, 86604, 86605],
                    dtype='int64'),
         920: Int64Index([96742, 96743, 96744, 96745, 96746], dtype='int64'),
         921: Int64Index([71790, 71791, 71792, 71793, 71794, 71795, 71796, 71797, 71798,
                     71799, 71800, 71801, 71802, 71803, 71804, 71805, 71806, 71807,
                     71808, 71809, 71810, 71811, 71812, 71813, 71814, 71815, 71816,
                     71817, 71818, 71819, 71820, 71821, 71822, 71823, 71824, 71825,
                     71826, 71827, 71828, 71829, 71830, 71831, 71832, 71833, 71834,
                     71835],
                    dtype='int64'),
         922: Int64Index([65505, 65506, 65507, 65508, 65509, 65510, 65511, 65512, 65513,
                     65514, 65515, 65516, 65517, 65518, 65519, 65520, 65521, 65522,
                     65523, 65524, 65525, 65526, 65527, 65528, 65529, 65530, 65531,
                     65532, 65533, 65534, 65535, 65536, 65537, 65538],
                    dtype='int64'),
         923: Int64Index([69677, 69678, 69679, 69680, 69681, 69682, 69683, 69684, 69685,
                     69686, 69687, 69688, 69689, 69690, 69691, 69692, 69693, 69694,
                     69695, 69696, 69697, 69698, 69699, 69700, 69701, 69702, 69703,
                     69704, 69705, 69706, 69707, 69708, 69709, 69710, 69711, 69712,
                     69713, 69714, 69715, 69716, 69717, 69718, 69719, 69720, 69721,
                     69722, 69723, 69724, 69725, 69726, 69727, 69728, 69729, 69730,
                     69731, 69732, 69733, 69734],
                    dtype='int64'),
         924: Int64Index([53406, 53407, 53408, 53409, 53410, 53411, 53412, 53413, 53414,
                     53415, 53416, 53417, 53418, 53419, 53420, 53421, 53422, 53423,
                     53424, 53425, 53426, 53427, 53428, 53429, 53430, 53431, 53432,
                     53433, 53434, 53435, 53436, 53437, 53438, 53439, 53440, 53441,
                     53442, 53443, 53444, 53445, 53446, 53447, 53448, 53449, 53450,
                     53451, 53452, 53453, 53454, 53455, 53456, 53457, 53458, 53459,
                     53460, 53461, 53462, 53463, 53464, 53465, 53466, 53467, 53468,
                     53469, 53470, 53471, 53472, 53473, 53474, 53475, 53476, 53477,
                     53478, 53479, 53480, 53481, 53482, 53483, 53484, 53485, 53486,
                     53487, 53488, 53489, 53490],
                    dtype='int64'),
         925: Int64Index([7933, 7934, 7935, 7936, 7937, 7938, 7939, 7940, 7941, 7942, 7943,
                     7944, 7945, 7946, 7947, 7948, 7949, 7950, 7951, 7952, 7953, 7954,
                     7955, 7956, 7957, 7958, 7959, 7960, 7961, 7962, 7963, 7964, 7965,
                     7966],
                    dtype='int64'),
         926: Int64Index([33078, 33079, 33080, 33081, 33082, 33083, 33084, 33085, 33086,
                     33087,
                     ...
                     33169, 33170, 33171, 33172, 33173, 33174, 33175, 33176, 33177,
                     33178],
                    dtype='int64', length=101),
         927: Int64Index([92653, 92654, 92655, 92656, 92657, 92658], dtype='int64'),
         928: Int64Index([88360, 88361, 88362, 88363, 88364, 88365, 88366, 88367, 88368,
                     88369,
                     ...
                     88454, 88455, 88456, 88457, 88458, 88459, 88460, 88461, 88462,
                     88463],
                    dtype='int64', length=104),
         929: Int64Index([82381, 82382, 82383, 82384, 82385, 82386, 82387, 82388, 82389,
                     82390, 82391, 82392, 82393, 82394, 82395, 82396, 82397, 82398,
                     82399, 82400, 82401, 82402, 82403, 82404, 82405, 82406, 82407,
                     82408, 82409, 82410, 82411, 82412, 82413, 82414, 82415, 82416,
                     82417, 82418, 82419, 82420],
                    dtype='int64'),
         930: Int64Index([81516, 81517, 81518, 81519, 81520, 81521, 81522, 81523, 81524,
                     81525, 81526, 81527, 81528, 81529, 81530, 81531, 81532, 81533,
                     81534, 81535, 81536, 81537, 81538, 81539, 81540, 81541, 81542,
                     81543, 81544, 81545, 81546, 81547, 81548, 81549, 81550, 81551,
                     81552, 81553, 81554, 81555, 81556, 81557, 81558, 81559, 81560,
                     81561, 81562, 81563, 81564, 81565, 81566, 81567, 81568, 81569,
                     81570, 81571, 81572, 81573, 81574, 81575, 81576, 81577, 81578,
                     81579, 81580, 81581, 81582, 81583, 81584, 81585, 81586, 81587,
                     81588, 81589, 81590, 81591, 81592, 81593, 81594, 81595],
                    dtype='int64'),
         931: Int64Index([79593, 79594, 79595, 79596, 79597, 79598, 79599, 79600, 79601,
                     79602, 79603, 79604, 79605, 79606, 79607, 79608, 79609, 79610,
                     79611, 79612, 79613, 79614, 79615, 79616, 79617, 79618, 79619,
                     79620, 79621, 79622, 79623, 79624, 79625, 79626, 79627, 79628,
                     79629, 79630, 79631, 79632, 79633, 79634, 79635, 79636, 79637,
                     79638, 79639, 79640, 79641, 79642, 79643, 79644, 79645, 79646,
                     79647, 79648, 79649],
                    dtype='int64'),
         932: Int64Index([27258, 27259, 27260, 27261, 27262, 27263, 27264, 27265, 27266,
                     27267, 27268, 27269, 27270, 27271, 27272, 27273, 27274, 27275,
                     27276, 27277, 27278, 27279, 27280, 27281, 27282, 27283, 27284,
                     27285, 27286, 27287, 27288, 27289, 27290, 27291, 27292, 27293,
                     27294, 27295, 27296, 27297],
                    dtype='int64'),
         933: Int64Index([91656, 91657, 91658, 91659, 91660, 91661, 91662, 91663, 91664,
                     91665, 91666, 91667, 91668, 91669, 91670, 91671, 91672, 91673,
                     91674, 91675, 91676],
                    dtype='int64'),
         934: Int64Index([14471, 14472, 14473, 14474, 14475, 14476, 14477, 14478, 14479,
                     14480, 14481, 14482, 14483, 14484, 14485, 14486, 14487, 14488,
                     14489, 14490, 14491, 14492, 14493, 14494, 14495, 14496, 14497,
                     14498, 14499, 14500, 14501, 14502, 14503, 14504, 14505, 14506,
                     14507, 14508, 14509, 14510, 14511, 14512, 14513, 14514, 14515,
                     14516, 14517, 14518, 14519, 14520, 14521, 14522, 14523, 14524,
                     14525, 14526, 14527, 14528, 14529, 14530, 14531, 14532, 14533,
                     14534, 14535, 14536, 14537, 14538],
                    dtype='int64'),
         935: Int64Index([99343, 99344, 99345, 99346, 99347, 99348, 99349], dtype='int64'),
         936: Int64Index([94629, 94630, 94631, 94632, 94633, 94634, 94635, 94636, 94637,
                     94638, 94639, 94640, 94641, 94642, 94643, 94644, 94645, 94646,
                     94647, 94648, 94649, 94650, 94651, 94652, 94653, 94654, 94655,
                     94656, 94657, 94658, 94659, 94660],
                    dtype='int64'),
         937: Int64Index([96501, 96502, 96503, 96504, 96505, 96506, 96507, 96508, 96509,
                     96510, 96511, 96512, 96513, 96514, 96515, 96516, 96517, 96518,
                     96519, 96520, 96521, 96522, 96523, 96524, 96525, 96526, 96527,
                     96528, 96529, 96530, 96531, 96532, 96533, 96534, 96535, 96536,
                     96537],
                    dtype='int64'),
         938: Int64Index([95985, 95986, 95987, 95988, 95989, 95990, 95991, 95992, 95993,
                     95994, 95995, 95996, 95997, 95998, 95999, 96000, 96001, 96002,
                     96003, 96004, 96005, 96006, 96007, 96008, 96009],
                    dtype='int64'),
         939: Int64Index([11457, 11458, 11459, 11460, 11461, 11462, 11463, 11464, 11465,
                     11466, 11467, 11468, 11469, 11470, 11471, 11472, 11473, 11474,
                     11475, 11476, 11477, 11478, 11479, 11480, 11481, 11482, 11483,
                     11484, 11485, 11486, 11487, 11488, 11489, 11490, 11491, 11492,
                     11493, 11494, 11495, 11496, 11497, 11498, 11499, 11500, 11501,
                     11502, 11503, 11504, 11505, 11506, 11507, 11508, 11509, 11510,
                     11511, 11512, 11513, 11514, 11515, 11516],
                    dtype='int64'),
         940: Int64Index([88099, 88100, 88101, 88102, 88103, 88104, 88105, 88106, 88107,
                     88108, 88109, 88110, 88111, 88112, 88113, 88114, 88115, 88116,
                     88117, 88118, 88119, 88120, 88121, 88122, 88123, 88124, 88125,
                     88126, 88127, 88128, 88129, 88130],
                    dtype='int64'),
         941: Int64Index([46358, 46359, 46360, 46361, 46362, 46363, 46364, 46365, 46366,
                     46367, 46368, 46369, 46370, 46371, 46372, 46373, 46374, 46375,
                     46376, 46377, 46378, 46379, 46380, 46381, 46382, 46383, 46384,
                     46385, 46386, 46387, 46388, 46389, 46390, 46391, 46392, 46393,
                     46394, 46395, 46396, 46397, 46398, 46399, 46400, 46401, 46402,
                     46403],
                    dtype='int64'),
         942: Int64Index([93574, 93575, 93576, 93577, 93578, 93579, 93580, 93581, 93582,
                     93583, 93584, 93585, 93586, 93587, 93588, 93589, 93590, 93591,
                     93592, 93593, 93594, 93595, 93596, 93597, 93598, 93599, 93600,
                     93601, 93602, 93603, 93604, 93605, 93606, 93607, 93608, 93609,
                     93610, 93611, 93612, 93613, 93614, 93615, 93616, 93617, 93618],
                    dtype='int64'),
         943: Int64Index([70427, 70428, 70429, 70430, 70431, 70432, 70433, 70434, 70435,
                     70436, 70437, 70438, 70439, 70440, 70441, 70442, 70443, 70444,
                     70445, 70446, 70447, 70448, 70449, 70450, 70451, 70452, 70453,
                     70454, 70455, 70456, 70457, 70458, 70459, 70460, 70461, 70462,
                     70463, 70464, 70465, 70466],
                    dtype='int64'),
         944: Int64Index([90820, 90821, 90822, 90823, 90824, 90825, 90826, 90827, 90828,
                     90829, 90830, 90831, 90832, 90833, 90834, 90835, 90836, 90837,
                     90838, 90839, 90840, 90841, 90842, 90843, 90844, 90845, 90846,
                     90847, 90848, 90849, 90850, 90851, 90852, 90853, 90854, 90855,
                     90856, 90857, 90858, 90859, 90860, 90861, 90862],
                    dtype='int64'),
         945: Int64Index([92403, 92404, 92405, 92406, 92407, 92408, 92409, 92410, 92411,
                     92412, 92413, 92414, 92415, 92416, 92417, 92418, 92419, 92420,
                     92421, 92422, 92423, 92424, 92425, 92426, 92427, 92428, 92429,
                     92430, 92431, 92432, 92433, 92434, 92435, 92436, 92437, 92438,
                     92439, 92440, 92441, 92442],
                    dtype='int64'),
         946: Int64Index([45758, 45759, 45760, 45761, 45762, 45763, 45764, 45765, 45766,
                     45767, 45768, 45769, 45770, 45771, 45772, 45773, 45774, 45775,
                     45776, 45777, 45778, 45779, 45780, 45781, 45782, 45783, 45784,
                     45785, 45786, 45787, 45788, 45789, 45790, 45791, 45792, 45793,
                     45794, 45795, 45796, 45797, 45798, 45799, 45800, 45801, 45802,
                     45803, 45804, 45805, 45806, 45807, 45808, 45809, 45810, 45811,
                     45812, 45813, 45814, 45815, 45816, 45817, 45818],
                    dtype='int64'),
         947: Int64Index([70244, 70245, 70246, 70247, 70248, 70249, 70250, 70251, 70252,
                     70253, 70254, 70255, 70256, 70257, 70258, 70259, 70260],
                    dtype='int64'),
         948: Int64Index([23460, 23461, 23462, 23463, 23464, 23465, 23466, 23467, 23468,
                     23469, 23470, 23471, 23472, 23473, 23474, 23475, 23476, 23477,
                     23478, 23479, 23480, 23481, 23482, 23483, 23484, 23485, 23486,
                     23487, 23488, 23489, 23490, 23491, 23492, 23493, 23494, 23495,
                     23496, 23497, 23498, 23499, 23500, 23501, 23502, 23503, 23504,
                     23505, 23506, 23507],
                    dtype='int64'),
         949: Int64Index([49758, 49759, 49760, 49761, 49762, 49763, 49764, 49765, 49766,
                     49767, 49768, 49769, 49770, 49771, 49772, 49773, 49774, 49775,
                     49776, 49777, 49778, 49779, 49780, 49781, 49782, 49783, 49784,
                     49785, 49786, 49787, 49788, 49789, 49790, 49791, 49792, 49793,
                     49794, 49795, 49796, 49797, 49798, 49799, 49800, 49801, 49802,
                     49803, 49804, 49805, 49806, 49807, 49808, 49809, 49810, 49811,
                     49812, 49813, 49814, 49815, 49816, 49817, 49818, 49819, 49820,
                     49821, 49822, 49823, 49824, 49825, 49826, 49827, 49828],
                    dtype='int64'),
         950: Int64Index([42350, 42351, 42352, 42353, 42354, 42355, 42356, 42357, 42358,
                     42359, 42360, 42361, 42362, 42363, 42364, 42365, 42366, 42367,
                     42368, 42369, 42370, 42371, 42372, 42373, 42374, 42375, 42376,
                     42377, 42378, 42379],
                    dtype='int64'),
         951: Int64Index([60737, 60738, 60739, 60740, 60741, 60742, 60743, 60744, 60745,
                     60746, 60747, 60748, 60749, 60750, 60751, 60752, 60753, 60754,
                     60755, 60756, 60757, 60758, 60759, 60760, 60761, 60762, 60763,
                     60764, 60765, 60766, 60767, 60768, 60769, 60770, 60771, 60772,
                     60773, 60774, 60775],
                    dtype='int64'),
         952: Int64Index([65363, 65364, 65365, 65366, 65367, 65368, 65369, 65370, 65371,
                     65372, 65373, 65374, 65375, 65376, 65377, 65378, 65379, 65380,
                     65381, 65382, 65383, 65384, 65385, 65386, 65387, 65388, 65389,
                     65390, 65391, 65392, 65393, 65394, 65395, 65396, 65397, 65398,
                     65399, 65400, 65401, 65402, 65403, 65404, 65405, 65406, 65407],
                    dtype='int64'),
         953: Int64Index([40246, 40247, 40248, 40249, 40250, 40251, 40252, 40253, 40254,
                     40255, 40256, 40257, 40258, 40259, 40260, 40261, 40262, 40263,
                     40264, 40265, 40266, 40267],
                    dtype='int64'),
         954: Int64Index([94715, 94716, 94717, 94718, 94719, 94720, 94721, 94722, 94723,
                     94724, 94725],
                    dtype='int64'),
         955: Int64Index([42428, 42429, 42430, 42431, 42432, 42433, 42434, 42435, 42436,
                     42437, 42438, 42439, 42440, 42441, 42442, 42443, 42444, 42445,
                     42446, 42447, 42448, 42449, 42450, 42451, 42452, 42453, 42454,
                     42455, 42456, 42457, 42458, 42459, 42460, 42461, 42462, 42463,
                     42464, 42465, 42466, 42467, 42468, 42469, 42470, 42471, 42472,
                     42473, 42474, 42475, 42476],
                    dtype='int64'),
         956: Int64Index([85166, 85167, 85168, 85169, 85170, 85171, 85172, 85173, 85174,
                     85175, 85176, 85177, 85178, 85179, 85180, 85181, 85182, 85183,
                     85184, 85185, 85186, 85187, 85188, 85189, 85190, 85191, 85192,
                     85193, 85194, 85195, 85196, 85197, 85198, 85199, 85200, 85201,
                     85202, 85203, 85204, 85205, 85206, 85207, 85208, 85209, 85210,
                     85211],
                    dtype='int64'),
         957: Int64Index([99337, 99338], dtype='int64'),
         958: Int64Index([99188, 99189, 99190, 99191, 99192, 99193, 99194, 99195, 99196,
                     99197, 99198, 99199, 99200, 99201],
                    dtype='int64'),
         959: Int64Index([44569, 44570, 44571, 44572, 44573, 44574, 44575, 44576, 44577,
                     44578, 44579, 44580, 44581, 44582, 44583, 44584, 44585, 44586,
                     44587, 44588, 44589, 44590, 44591, 44592, 44593, 44594, 44595,
                     44596, 44597, 44598, 44599, 44600, 44601, 44602, 44603, 44604,
                     44605, 44606, 44607, 44608, 44609, 44610, 44611, 44612, 44613,
                     44614, 44615, 44616, 44617, 44618, 44619, 44620, 44621, 44622,
                     44623, 44624, 44625, 44626, 44627, 44628, 44629, 44630, 44631,
                     44632],
                    dtype='int64'),
         960: Int64Index([69652, 69653, 69654, 69655, 69656, 69657, 69658, 69659, 69660,
                     69661, 69662, 69663, 69664, 69665, 69666, 69667, 69668, 69669,
                     69670, 69671, 69672, 69673, 69674, 69675, 69676],
                    dtype='int64'),
         961: Int64Index([74507, 74508, 74509, 74510, 74511, 74512, 74513, 74514, 74515,
                     74516, 74517, 74518, 74519, 74520, 74521, 74522, 74523, 74524,
                     74525, 74526, 74527, 74528, 74529, 74530, 74531, 74532, 74533,
                     74534, 74535, 74536, 74537, 74538, 74539, 74540],
                    dtype='int64'),
         962: Int64Index([85996, 85997, 85998, 85999, 86000, 86001, 86002, 86003, 86004,
                     86005, 86006, 86007, 86008, 86009, 86010, 86011, 86012, 86013,
                     86014, 86015, 86016, 86017, 86018],
                    dtype='int64'),
         963: Int64Index([71840, 71841, 71842, 71843, 71844, 71845, 71846, 71847, 71848,
                     71849, 71850, 71851, 71852, 71853, 71854, 71855, 71856, 71857,
                     71858, 71859, 71860, 71861, 71862, 71863, 71864, 71865, 71866,
                     71867, 71868, 71869, 71870, 71871, 71872, 71873, 71874, 71875,
                     71876, 71877, 71878, 71879, 71880],
                    dtype='int64'),
         964: Int64Index([93992, 93993, 93994, 93995, 93996, 93997, 93998, 93999, 94000], dtype='int64'),
         965: Int64Index([92356, 92357, 92358, 92359, 92360, 92361, 92362, 92363, 92364,
                     92365, 92366, 92367, 92368, 92369, 92370, 92371, 92372, 92373,
                     92374, 92375, 92376],
                    dtype='int64'),
         966: Int64Index([69359, 69360, 69361, 69362, 69363, 69364, 69365, 69366, 69367,
                     69368, 69369, 69370, 69371, 69372, 69373, 69374, 69375, 69376,
                     69377, 69378, 69379, 69380, 69381, 69382, 69383, 69384],
                    dtype='int64'),
         967: Int64Index([98935, 98936, 98937, 98938, 98939, 98940, 98941, 98942, 98943,
                     98944, 98945, 98946],
                    dtype='int64'),
         968: Int64Index([94998, 94999, 95000, 95001, 95002, 95003, 95004, 95005, 95006,
                     95007, 95008, 95009, 95010, 95011, 95012, 95013, 95014, 95015],
                    dtype='int64'),
         969: Int64Index([65073, 65074, 65075, 65076, 65077, 65078, 65079, 65080, 65081,
                     65082, 65083, 65084, 65085, 65086, 65087, 65088, 65089, 65090,
                     65091, 65092, 65093, 65094, 65095, 65096, 65097, 65098, 65099,
                     65100, 65101, 65102, 65103, 65104, 65105, 65106, 65107, 65108,
                     65109, 65110, 65111, 65112, 65113, 65114, 65115, 65116, 65117,
                     65118, 65119, 65120, 65121, 65122, 65123, 65124, 65125, 65126,
                     65127, 65128, 65129, 65130, 65131, 65132, 65133, 65134, 65135,
                     65136, 65137, 65138, 65139, 65140, 65141, 65142, 65143, 65144,
                     65145, 65146, 65147],
                    dtype='int64'),
         970: Int64Index([93044, 93045, 93046, 93047, 93048, 93049, 93050, 93051], dtype='int64'),
         971: Int64Index([72239, 72240, 72241, 72242, 72243, 72244, 72245, 72246, 72247,
                     72248, 72249, 72250, 72251, 72252, 72253, 72254, 72255, 72256,
                     72257, 72258, 72259, 72260, 72261, 72262, 72263, 72264, 72265,
                     72266, 72267, 72268, 72269, 72270, 72271, 72272],
                    dtype='int64'),
         972: Int64Index([98238, 98239, 98240, 98241, 98242, 98243, 98244, 98245, 98246,
                     98247, 98248, 98249, 98250, 98251, 98252, 98253, 98254, 98255,
                     98256, 98257, 98258, 98259, 98260, 98261, 98262, 98263, 98264,
                     98265],
                    dtype='int64'),
         973: Int64Index([99333, 99334, 99335, 99336], dtype='int64'),
         974: Int64Index([91624, 91625, 91626, 91627, 91628, 91629, 91630, 91631, 91632,
                     91633, 91634, 91635, 91636, 91637, 91638, 91639, 91640, 91641,
                     91642, 91643, 91644, 91645, 91646, 91647, 91648, 91649, 91650,
                     91651, 91652, 91653, 91654, 91655],
                    dtype='int64'),
         975: Int64Index([91558, 91559, 91560, 91561, 91562, 91563, 91564, 91565, 91566,
                     91567, 91568, 91569, 91570, 91571, 91572, 91573, 91574, 91575,
                     91576, 91577, 91578, 91579, 91580, 91581, 91582, 91583, 91584,
                     91585, 91586, 91587, 91588, 91589, 91590, 91591, 91592, 91593,
                     91594, 91595, 91596, 91597, 91598, 91599, 91600, 91601],
                    dtype='int64'),
         976: Int64Index([95178, 95179, 95180, 95181, 95182, 95183, 95184, 95185, 95186,
                     95187, 95188, 95189],
                    dtype='int64'),
         977: Int64Index([7967, 7968, 7969, 7970, 7971, 7972, 7973, 7974, 7975, 7976, 7977,
                     7978, 7979, 7980, 7981, 7982, 7983, 7984, 7985, 7986, 7987, 7988,
                     7989, 7990, 7991, 7992, 7993, 7994, 7995, 7996, 7997, 7998, 7999,
                     8000, 8001, 8002, 8003, 8004, 8005, 8006, 8007, 8008, 8009, 8010,
                     8011, 8012, 8013, 8014, 8015],
                    dtype='int64'),
         978: Int64Index([96280, 96281, 96282, 96283, 96284, 96285, 96286, 96287, 96288,
                     96289, 96290, 96291, 96292, 96293, 96294, 96295, 96296, 96297,
                     96298, 96299, 96300, 96301, 96302, 96303, 96304, 96305, 96306],
                    dtype='int64'),
         979: Int64Index([88662, 88663, 88664, 88665, 88666, 88667, 88668, 88669, 88670,
                     88671, 88672, 88673, 88674, 88675, 88676, 88677, 88678, 88679,
                     88680, 88681, 88682, 88683, 88684, 88685, 88686, 88687, 88688,
                     88689, 88690, 88691, 88692, 88693, 88694, 88695, 88696],
                    dtype='int64'),
         980: Int64Index([66453, 66454, 66455, 66456, 66457, 66458, 66459, 66460, 66461,
                     66462, 66463, 66464, 66465, 66466, 66467, 66468, 66469, 66470,
                     66471, 66472, 66473, 66474],
                    dtype='int64'),
         981: Int64Index([96948, 96949, 96950, 96951, 96952, 96953, 96954, 96955], dtype='int64'),
         982: Int64Index([84172, 84173, 84174, 84175, 84176, 84177, 84178, 84179, 84180,
                     84181, 84182, 84183, 84184, 84185, 84186, 84187, 84188, 84189,
                     84190, 84191],
                    dtype='int64'),
         983: Int64Index([7313, 7314, 7315, 7316, 7317, 7318, 7319, 7320, 7321, 7322, 7323,
                     7324, 7325, 7326, 7327],
                    dtype='int64'),
         984: Int64Index([55683, 55684, 55685, 55686, 55687, 55688, 55689, 55690, 55691,
                     55692, 55693, 55694, 55695, 55696, 55697, 55698, 55699, 55700,
                     55701, 55702, 55703, 55704, 55705, 55706, 55707, 55708, 55709,
                     55710, 55711, 55712, 55713, 55714, 55715, 55716, 55717, 55718,
                     55719, 55720, 55721, 55722, 55723, 55724, 55725, 55726],
                    dtype='int64'),
         985: Int64Index([91677, 91678, 91679, 91680, 91681, 91682, 91683, 91684, 91685,
                     91686, 91687, 91688, 91689, 91690, 91691, 91692, 91693, 91694,
                     91695, 91696, 91697, 91698],
                    dtype='int64'),
         986: Int64Index([94412, 94413, 94414, 94415, 94416, 94417, 94418, 94419, 94420,
                     94421, 94422, 94423, 94424, 94425, 94426, 94427, 94428, 94429,
                     94430, 94431, 94432, 94433, 94434],
                    dtype='int64'),
         987: Int64Index([99466, 99467, 99468, 99469], dtype='int64'),
         988: Int64Index([11217, 11218, 11219, 11220, 11221, 11222, 11223, 11224, 11225,
                     11226, 11227, 11228, 11229, 11230, 11231, 11232, 11233, 11234,
                     11235, 11236, 11237, 11238, 11239, 11240, 11241, 11242, 11243,
                     11244, 11245, 11246, 11247, 11248, 11249, 11250, 11251, 11252,
                     11253, 11254, 11255, 11256, 11257, 11258, 11259, 11260, 11261,
                     11262, 11263, 11264, 11265, 11266, 11267, 11268, 11269, 11270,
                     11271, 11272, 11273, 11274, 11275, 11276, 11277, 11278, 11279,
                     11280, 11281, 11282, 11283, 11284, 11285, 11286, 11287, 11288,
                     11289, 11290, 11291, 11292, 11293, 11294, 11295, 11296, 11297,
                     11298, 11299, 11300, 11301, 11302],
                    dtype='int64'),
         989: Int64Index([93843, 93844, 93845, 93846, 93847, 93848, 93849, 93850, 93851,
                     93852, 93853, 93854, 93855, 93856, 93857, 93858, 93859, 93860,
                     93861, 93862, 93863, 93864, 93865, 93866, 93867, 93868, 93869,
                     93870, 93871, 93872, 93873, 93874],
                    dtype='int64'),
         990: Int64Index([96468, 96469, 96470, 96471, 96472, 96473, 96474, 96475, 96476,
                     96477, 96478, 96479, 96480, 96481, 96482, 96483, 96484, 96485,
                     96486, 96487, 96488, 96489, 96490, 96491, 96492, 96493, 96494,
                     96495, 96496, 96497, 96498, 96499, 96500],
                    dtype='int64'),
         991: Int64Index([86375, 86376, 86377, 86378, 86379, 86380, 86381, 86382, 86383,
                     86384, 86385, 86386, 86387, 86388, 86389, 86390, 86391, 86392,
                     86393, 86394, 86395, 86396, 86397, 86398, 86399],
                    dtype='int64'),
         992: Int64Index([99037, 99038, 99039, 99040], dtype='int64'),
         993: Int64Index([58188, 58189, 58190, 58191, 58192, 58193, 58194, 58195, 58196,
                     58197, 58198, 58199, 58200, 58201, 58202, 58203, 58204, 58205,
                     58206, 58207, 58208, 58209, 58210, 58211, 58212, 58213, 58214,
                     58215, 58216, 58217, 58218, 58219, 58220, 58221, 58222, 58223,
                     58224, 58225, 58226, 58227, 58228, 58229, 58230, 58231, 58232,
                     58233, 58234, 58235, 58236, 58237, 58238, 58239, 58240, 58241,
                     58242, 58243, 58244, 58245, 58246, 58247, 58248, 58249, 58250,
                     58251, 58252, 58253],
                    dtype='int64'),
         994: Int64Index([99459, 99460, 99461, 99462, 99463, 99464, 99465], dtype='int64'),
         995: Int64Index([94343, 94344, 94345, 94346, 94347, 94348, 94349, 94350, 94351,
                     94352, 94353, 94354, 94355, 94356, 94357, 94358, 94359, 94360,
                     94361, 94362, 94363, 94364, 94365, 94366, 94367, 94368, 94369,
                     94370, 94371, 94372, 94373],
                    dtype='int64'),
         996: Int64Index([27021, 27022, 27023, 27024, 27025, 27026, 27027, 27028, 27029,
                     27030, 27031, 27032, 27033, 27034],
                    dtype='int64'),
         997: Int64Index([24792, 24793, 24794, 24795, 24796, 24797, 24798, 24799, 24800,
                     24801, 24802, 24803, 24804, 24805, 24806, 24807],
                    dtype='int64'),
         998: Int64Index([34624, 34625, 34626, 34627, 34628, 34629, 34630, 34631, 34632,
                     34633, 34634, 34635, 34636, 34637, 34638, 34639],
                    dtype='int64'),
         999: Int64Index([22528, 22529, 22530, 22531, 22532, 22533, 22534, 22535, 22536,
                     22537],
                    dtype='int64'),
         1000: Int64Index([30469, 30470, 30471, 30472, 30473, 30474, 30475, 30476, 30477,
                     30478],
                    dtype='int64'),
         ...}




    ```python
    movie_user_id_grouped = movies.groupby(['movie_id', 'user_id'])
    movie_user_id_grouped.groups
    ```




        {(1, 1): Int64Index([50341], dtype='int64'),
         (1, 2): Int64Index([50389], dtype='int64'),
         (1, 5): Int64Index([50335], dtype='int64'),
         (1, 6): Int64Index([50264], dtype='int64'),
         (1, 10): Int64Index([50286], dtype='int64'),
         (1, 13): Int64Index([50302], dtype='int64'),
         (1, 15): Int64Index([50343], dtype='int64'),
         (1, 16): Int64Index([50350], dtype='int64'),
         (1, 17): Int64Index([50395], dtype='int64'),
         (1, 18): Int64Index([50337], dtype='int64'),
         (1, 20): Int64Index([50301], dtype='int64'),
         (1, 21): Int64Index([50367], dtype='int64'),
         (1, 23): Int64Index([50359], dtype='int64'),
         (1, 25): Int64Index([50296], dtype='int64'),
         (1, 26): Int64Index([50338], dtype='int64'),
         (1, 38): Int64Index([50276], dtype='int64'),
         (1, 41): Int64Index([50325], dtype='int64'),
         (1, 42): Int64Index([50299], dtype='int64'),
         (1, 43): Int64Index([50329], dtype='int64'),
         (1, 44): Int64Index([50324], dtype='int64'),
         (1, 45): Int64Index([50379], dtype='int64'),
         (1, 49): Int64Index([50333], dtype='int64'),
         (1, 54): Int64Index([50349], dtype='int64'),
         (1, 56): Int64Index([50342], dtype='int64'),
         (1, 57): Int64Index([50304], dtype='int64'),
         (1, 58): Int64Index([50321], dtype='int64'),
         (1, 59): Int64Index([50297], dtype='int64'),
         (1, 62): Int64Index([50265], dtype='int64'),
         (1, 63): Int64Index([50278], dtype='int64'),
         (1, 64): Int64Index([50371], dtype='int64'),
         (1, 65): Int64Index([50373], dtype='int64'),
         (1, 66): Int64Index([50336], dtype='int64'),
         (1, 67): Int64Index([50410], dtype='int64'),
         (1, 70): Int64Index([50352], dtype='int64'),
         (1, 72): Int64Index([50298], dtype='int64'),
         (1, 73): Int64Index([50376], dtype='int64'),
         (1, 75): Int64Index([50385], dtype='int64'),
         (1, 77): Int64Index([50361], dtype='int64'),
         (1, 79): Int64Index([50384], dtype='int64'),
         (1, 81): Int64Index([50295], dtype='int64'),
         (1, 82): Int64Index([50326], dtype='int64'),
         (1, 83): Int64Index([50347], dtype='int64'),
         (1, 84): Int64Index([50330], dtype='int64'),
         (1, 89): Int64Index([50394], dtype='int64'),
         (1, 92): Int64Index([50308], dtype='int64'),
         (1, 93): Int64Index([50391], dtype='int64'),
         (1, 94): Int64Index([50322], dtype='int64'),
         (1, 95): Int64Index([50275], dtype='int64'),
         (1, 96): Int64Index([50375], dtype='int64'),
         (1, 97): Int64Index([50282], dtype='int64'),
         (1, 99): Int64Index([50292], dtype='int64'),
         (1, 101): Int64Index([50362], dtype='int64'),
         (1, 102): Int64Index([50277], dtype='int64'),
         (1, 106): Int64Index([50398], dtype='int64'),
         (1, 108): Int64Index([50393], dtype='int64'),
         (1, 109): Int64Index([50370], dtype='int64'),
         (1, 117): Int64Index([50372], dtype='int64'),
         (1, 120): Int64Index([50406], dtype='int64'),
         (1, 121): Int64Index([50332], dtype='int64'),
         (1, 124): Int64Index([50397], dtype='int64'),
         (1, 125): Int64Index([50346], dtype='int64'),
         (1, 128): Int64Index([50323], dtype='int64'),
         (1, 130): Int64Index([50339], dtype='int64'),
         (1, 131): Int64Index([50380], dtype='int64'),
         (1, 134): Int64Index([50368], dtype='int64'),
         (1, 137): Int64Index([50374], dtype='int64'),
         (1, 138): Int64Index([50303], dtype='int64'),
         (1, 141): Int64Index([50392], dtype='int64'),
         (1, 144): Int64Index([50364], dtype='int64'),
         (1, 145): Int64Index([50314], dtype='int64'),
         (1, 148): Int64Index([50345], dtype='int64'),
         (1, 150): Int64Index([50386], dtype='int64'),
         (1, 151): Int64Index([50348], dtype='int64'),
         (1, 157): Int64Index([50283], dtype='int64'),
         (1, 158): Int64Index([50358], dtype='int64'),
         (1, 160): Int64Index([50279], dtype='int64'),
         (1, 162): Int64Index([50312], dtype='int64'),
         (1, 168): Int64Index([50320], dtype='int64'),
         (1, 174): Int64Index([50328], dtype='int64'),
         (1, 177): Int64Index([50365], dtype='int64'),
         (1, 178): Int64Index([50293], dtype='int64'),
         (1, 181): Int64Index([50284], dtype='int64'),
         (1, 182): Int64Index([50378], dtype='int64'),
         (1, 184): Int64Index([50363], dtype='int64'),
         (1, 189): Int64Index([50306], dtype='int64'),
         (1, 193): Int64Index([50356], dtype='int64'),
         (1, 194): Int64Index([50270], dtype='int64'),
         (1, 198): Int64Index([50319], dtype='int64'),
         (1, 199): Int64Index([50400], dtype='int64'),
         (1, 200): Int64Index([50267], dtype='int64'),
         (1, 201): Int64Index([50287], dtype='int64'),
         (1, 202): Int64Index([50401], dtype='int64'),
         (1, 203): Int64Index([50366], dtype='int64'),
         (1, 204): Int64Index([50405], dtype='int64'),
         (1, 209): Int64Index([50408], dtype='int64'),
         (1, 210): Int64Index([50268], dtype='int64'),
         (1, 213): Int64Index([50331], dtype='int64'),
         (1, 216): Int64Index([50315], dtype='int64'),
         (1, 222): Int64Index([50311], dtype='int64'),
         (1, 223): Int64Index([50305], dtype='int64'),
         (1, 230): Int64Index([50381], dtype='int64'),
         (1, 231): Int64Index([50382], dtype='int64'),
         (1, 232): Int64Index([50344], dtype='int64'),
         (1, 234): Int64Index([50272], dtype='int64'),
         (1, 235): Int64Index([50377], dtype='int64'),
         (1, 242): Int64Index([50290], dtype='int64'),
         (1, 243): Int64Index([50307], dtype='int64'),
         (1, 244): Int64Index([50260], dtype='int64'),
         (1, 246): Int64Index([50289], dtype='int64'),
         (1, 247): Int64Index([50409], dtype='int64'),
         (1, 248): Int64Index([50390], dtype='int64'),
         (1, 249): Int64Index([50291], dtype='int64'),
         (1, 250): Int64Index([50316], dtype='int64'),
         (1, 251): Int64Index([50294], dtype='int64'),
         (1, 252): Int64Index([50404], dtype='int64'),
         (1, 253): Int64Index([50262], dtype='int64'),
         (1, 254): Int64Index([50309], dtype='int64'),
         (1, 256): Int64Index([50340], dtype='int64'),
         (1, 262): Int64Index([50327], dtype='int64'),
         (1, 263): Int64Index([50369], dtype='int64'),
         (1, 265): Int64Index([50318], dtype='int64'),
         (1, 268): Int64Index([50334], dtype='int64'),
         (1, 271): Int64Index([50317], dtype='int64'),
         (1, 274): Int64Index([50387], dtype='int64'),
         (1, 275): Int64Index([50357], dtype='int64'),
         (1, 276): Int64Index([50285], dtype='int64'),
         (1, 277): Int64Index([50402], dtype='int64'),
         (1, 279): Int64Index([50313], dtype='int64'),
         (1, 280): Int64Index([50383], dtype='int64'),
         (1, 286): Int64Index([50266], dtype='int64'),
         (1, 287): Int64Index([50288], dtype='int64'),
         (1, 289): Int64Index([50407], dtype='int64'),
         (1, 290): Int64Index([50281], dtype='int64'),
         (1, 291): Int64Index([50271], dtype='int64'),
         (1, 292): Int64Index([50300], dtype='int64'),
         (1, 293): Int64Index([50310], dtype='int64'),
         (1, 294): Int64Index([50351], dtype='int64'),
         (1, 295): Int64Index([50353], dtype='int64'),
         (1, 296): Int64Index([50360], dtype='int64'),
         (1, 297): Int64Index([50355], dtype='int64'),
         (1, 298): Int64Index([50261], dtype='int64'),
         (1, 299): Int64Index([50273], dtype='int64'),
         (1, 301): Int64Index([50280], dtype='int64'),
         (1, 303): Int64Index([50269], dtype='int64'),
         (1, 305): Int64Index([50263], dtype='int64'),
         (1, 307): Int64Index([50354], dtype='int64'),
         (1, 308): Int64Index([50274], dtype='int64'),
         (1, 311): Int64Index([50388], dtype='int64'),
         (1, 312): Int64Index([50399], dtype='int64'),
         (1, 313): Int64Index([50396], dtype='int64'),
         (1, 314): Int64Index([50403], dtype='int64'),
         (1, 320): Int64Index([50412], dtype='int64'),
         (1, 322): Int64Index([50415], dtype='int64'),
         (1, 324): Int64Index([50419], dtype='int64'),
         (1, 325): Int64Index([50411], dtype='int64'),
         (1, 326): Int64Index([50413], dtype='int64'),
         (1, 327): Int64Index([50414], dtype='int64'),
         (1, 330): Int64Index([50416], dtype='int64'),
         (1, 331): Int64Index([50417], dtype='int64'),
         (1, 332): Int64Index([50418], dtype='int64'),
         (1, 336): Int64Index([50420], dtype='int64'),
         (1, 338): Int64Index([50421], dtype='int64'),
         (1, 339): Int64Index([50422], dtype='int64'),
         (1, 340): Int64Index([50423], dtype='int64'),
         (1, 343): Int64Index([50424], dtype='int64'),
         (1, 344): Int64Index([50425], dtype='int64'),
         (1, 345): Int64Index([50426], dtype='int64'),
         (1, 347): Int64Index([50427], dtype='int64'),
         (1, 348): Int64Index([50428], dtype='int64'),
         (1, 350): Int64Index([50433], dtype='int64'),
         (1, 357): Int64Index([50431], dtype='int64'),
         (1, 359): Int64Index([50437], dtype='int64'),
         (1, 360): Int64Index([50429], dtype='int64'),
         (1, 363): Int64Index([50430], dtype='int64'),
         (1, 365): Int64Index([50432], dtype='int64'),
         (1, 371): Int64Index([50434], dtype='int64'),
         (1, 374): Int64Index([50435], dtype='int64'),
         (1, 378): Int64Index([50436], dtype='int64'),
         (1, 379): Int64Index([50438], dtype='int64'),
         (1, 380): Int64Index([50439], dtype='int64'),
         (1, 381): Int64Index([50440], dtype='int64'),
         (1, 387): Int64Index([50441], dtype='int64'),
         (1, 388): Int64Index([50442], dtype='int64'),
         (1, 389): Int64Index([50443], dtype='int64'),
         (1, 390): Int64Index([50444], dtype='int64'),
         (1, 393): Int64Index([50445], dtype='int64'),
         (1, 394): Int64Index([50446], dtype='int64'),
         (1, 395): Int64Index([50452], dtype='int64'),
         (1, 396): Int64Index([50449], dtype='int64'),
         (1, 398): Int64Index([50447], dtype='int64'),
         (1, 399): Int64Index([50448], dtype='int64'),
         (1, 401): Int64Index([50450], dtype='int64'),
         (1, 402): Int64Index([50451], dtype='int64'),
         (1, 403): Int64Index([50453], dtype='int64'),
         (1, 406): Int64Index([50454], dtype='int64'),
         (1, 407): Int64Index([50455], dtype='int64'),
         (1, 411): Int64Index([50457], dtype='int64'),
         (1, 412): Int64Index([50459], dtype='int64'),
         (1, 416): Int64Index([50456], dtype='int64'),
         (1, 417): Int64Index([50458], dtype='int64'),
         (1, 419): Int64Index([50462], dtype='int64'),
         (1, 422): Int64Index([50460], dtype='int64'),
         (1, 424): Int64Index([50464], dtype='int64'),
         (1, 425): Int64Index([50461], dtype='int64'),
         (1, 429): Int64Index([50463], dtype='int64'),
         (1, 432): Int64Index([50465], dtype='int64'),
         (1, 434): Int64Index([50467], dtype='int64'),
         (1, 435): Int64Index([50466], dtype='int64'),
         (1, 438): Int64Index([50468], dtype='int64'),
         (1, 441): Int64Index([50487], dtype='int64'),
         (1, 445): Int64Index([50469], dtype='int64'),
         (1, 447): Int64Index([50470], dtype='int64'),
         (1, 450): Int64Index([50471], dtype='int64'),
         (1, 454): Int64Index([50472], dtype='int64'),
         (1, 455): Int64Index([50473], dtype='int64'),
         (1, 456): Int64Index([50475], dtype='int64'),
         (1, 457): Int64Index([50474], dtype='int64'),
         (1, 458): Int64Index([50476], dtype='int64'),
         (1, 459): Int64Index([50477], dtype='int64'),
         (1, 460): Int64Index([50478], dtype='int64'),
         (1, 463): Int64Index([50483], dtype='int64'),
         (1, 465): Int64Index([50482], dtype='int64'),
         (1, 467): Int64Index([50479], dtype='int64'),
         (1, 468): Int64Index([50480], dtype='int64'),
         (1, 470): Int64Index([50486], dtype='int64'),
         (1, 471): Int64Index([50484], dtype='int64'),
         (1, 472): Int64Index([50481], dtype='int64'),
         (1, 478): Int64Index([50485], dtype='int64'),
         (1, 479): Int64Index([50488], dtype='int64'),
         (1, 483): Int64Index([50494], dtype='int64'),
         (1, 484): Int64Index([50489], dtype='int64'),
         (1, 486): Int64Index([50490], dtype='int64'),
         (1, 487): Int64Index([50491], dtype='int64'),
         (1, 488): Int64Index([50498], dtype='int64'),
         (1, 490): Int64Index([50493], dtype='int64'),
         (1, 493): Int64Index([50492], dtype='int64'),
         (1, 494): Int64Index([50495], dtype='int64'),
         (1, 495): Int64Index([50496], dtype='int64'),
         (1, 497): Int64Index([50497], dtype='int64'),
         (1, 500): Int64Index([50499], dtype='int64'),
         (1, 503): Int64Index([50500], dtype='int64'),
         (1, 505): Int64Index([50501], dtype='int64'),
         (1, 508): Int64Index([50503], dtype='int64'),
         (1, 512): Int64Index([50504], dtype='int64'),
         (1, 514): Int64Index([50502], dtype='int64'),
         (1, 517): Int64Index([50510], dtype='int64'),
         (1, 518): Int64Index([50506], dtype='int64'),
         (1, 521): Int64Index([50508], dtype='int64'),
         (1, 523): Int64Index([50505], dtype='int64'),
         (1, 525): Int64Index([50507], dtype='int64'),
         (1, 526): Int64Index([50514], dtype='int64'),
         (1, 532): Int64Index([50509], dtype='int64'),
         (1, 533): Int64Index([50511], dtype='int64'),
         (1, 534): Int64Index([50516], dtype='int64'),
         (1, 535): Int64Index([50512], dtype='int64'),
         (1, 536): Int64Index([50513], dtype='int64'),
         (1, 537): Int64Index([50515], dtype='int64'),
         (1, 540): Int64Index([50523], dtype='int64'),
         (1, 541): Int64Index([50517], dtype='int64'),
         (1, 542): Int64Index([50518], dtype='int64'),
         (1, 545): Int64Index([50519], dtype='int64'),
         (1, 548): Int64Index([50520], dtype='int64'),
         (1, 549): Int64Index([50528], dtype='int64'),
         (1, 550): Int64Index([50525], dtype='int64'),
         (1, 552): Int64Index([50522], dtype='int64'),
         (1, 553): Int64Index([50521], dtype='int64'),
         (1, 554): Int64Index([50524], dtype='int64'),
         (1, 560): Int64Index([50526], dtype='int64'),
         (1, 561): Int64Index([50527], dtype='int64'),
         (1, 562): Int64Index([50531], dtype='int64'),
         (1, 567): Int64Index([50529], dtype='int64'),
         (1, 569): Int64Index([50530], dtype='int64'),
         (1, 576): Int64Index([50532], dtype='int64'),
         (1, 577): Int64Index([50533], dtype='int64'),
         (1, 579): Int64Index([50534], dtype='int64'),
         (1, 580): Int64Index([50538], dtype='int64'),
         (1, 582): Int64Index([50536], dtype='int64'),
         (1, 588): Int64Index([50535], dtype='int64'),
         (1, 592): Int64Index([50537], dtype='int64'),
         (1, 593): Int64Index([50539], dtype='int64'),
         (1, 597): Int64Index([50541], dtype='int64'),
         (1, 599): Int64Index([50540], dtype='int64'),
         (1, 602): Int64Index([50542], dtype='int64'),
         (1, 605): Int64Index([50543], dtype='int64'),
         (1, 606): Int64Index([50544], dtype='int64'),
         (1, 609): Int64Index([50548], dtype='int64'),
         (1, 610): Int64Index([50545], dtype='int64'),
         (1, 612): Int64Index([50554], dtype='int64'),
         (1, 613): Int64Index([50550], dtype='int64'),
         (1, 614): Int64Index([50547], dtype='int64'),
         (1, 618): Int64Index([50546], dtype='int64'),
         (1, 620): Int64Index([50549], dtype='int64'),
         (1, 621): Int64Index([50552], dtype='int64'),
         (1, 622): Int64Index([50551], dtype='int64'),
         (1, 624): Int64Index([50553], dtype='int64'),
         (1, 630): Int64Index([50557], dtype='int64'),
         (1, 632): Int64Index([50555], dtype='int64'),
         (1, 634): Int64Index([50556], dtype='int64'),
         (1, 635): Int64Index([50561], dtype='int64'),
         (1, 636): Int64Index([50562], dtype='int64'),
         (1, 637): Int64Index([50559], dtype='int64'),
         (1, 642): Int64Index([50558], dtype='int64'),
         (1, 643): Int64Index([50560], dtype='int64'),
         (1, 648): Int64Index([50563], dtype='int64'),
         (1, 649): Int64Index([50568], dtype='int64'),
         (1, 650): Int64Index([50564], dtype='int64'),
         (1, 653): Int64Index([50566], dtype='int64'),
         (1, 654): Int64Index([50565], dtype='int64'),
         (1, 655): Int64Index([50567], dtype='int64'),
         (1, 657): Int64Index([50573], dtype='int64'),
         (1, 658): Int64Index([50569], dtype='int64'),
         (1, 660): Int64Index([50570], dtype='int64'),
         (1, 661): Int64Index([50575], dtype='int64'),
         (1, 663): Int64Index([50571], dtype='int64'),
         (1, 664): Int64Index([50572], dtype='int64'),
         (1, 665): Int64Index([50574], dtype='int64'),
         (1, 669): Int64Index([50576], dtype='int64'),
         (1, 674): Int64Index([50578], dtype='int64'),
         (1, 676): Int64Index([50577], dtype='int64'),
         (1, 677): Int64Index([50579], dtype='int64'),
         (1, 678): Int64Index([50598], dtype='int64'),
         (1, 679): Int64Index([50581], dtype='int64'),
         (1, 680): Int64Index([50589], dtype='int64'),
         (1, 682): Int64Index([50580], dtype='int64'),
         (1, 684): Int64Index([50582], dtype='int64'),
         (1, 689): Int64Index([50586], dtype='int64'),
         (1, 690): Int64Index([50585], dtype='int64'),
         (1, 691): Int64Index([50583], dtype='int64'),
         (1, 692): Int64Index([50584], dtype='int64'),
         (1, 697): Int64Index([50587], dtype='int64'),
         (1, 698): Int64Index([50588], dtype='int64'),
         (1, 699): Int64Index([50592], dtype='int64'),
         (1, 701): Int64Index([50591], dtype='int64'),
         (1, 703): Int64Index([50604], dtype='int64'),
         (1, 705): Int64Index([50590], dtype='int64'),
         (1, 706): Int64Index([50602], dtype='int64'),
         (1, 708): Int64Index([50593], dtype='int64'),
         (1, 709): Int64Index([50594], dtype='int64'),
         (1, 710): Int64Index([50595], dtype='int64'),
         (1, 714): Int64Index([50600], dtype='int64'),
         (1, 715): Int64Index([50596], dtype='int64'),
         (1, 716): Int64Index([50597], dtype='int64'),
         (1, 721): Int64Index([50599], dtype='int64'),
         (1, 723): Int64Index([50612], dtype='int64'),
         (1, 726): Int64Index([50603], dtype='int64'),
         (1, 727): Int64Index([50601], dtype='int64'),
         (1, 730): Int64Index([50606], dtype='int64'),
         (1, 731): Int64Index([50616], dtype='int64'),
         (1, 733): Int64Index([50608], dtype='int64'),
         (1, 735): Int64Index([50610], dtype='int64'),
         (1, 738): Int64Index([50605], dtype='int64'),
         (1, 742): Int64Index([50607], dtype='int64'),
         (1, 744): Int64Index([50620], dtype='int64'),
         (1, 745): Int64Index([50609], dtype='int64'),
         (1, 746): Int64Index([50615], dtype='int64'),
         (1, 747): Int64Index([50611], dtype='int64'),
         (1, 748): Int64Index([50614], dtype='int64'),
         (1, 749): Int64Index([50613], dtype='int64'),
         (1, 751): Int64Index([50617], dtype='int64'),
         (1, 756): Int64Index([50618], dtype='int64'),
         (1, 757): Int64Index([50619], dtype='int64'),
         (1, 759): Int64Index([50630], dtype='int64'),
         (1, 761): Int64Index([50628], dtype='int64'),
         (1, 763): Int64Index([50621], dtype='int64'),
         (1, 764): Int64Index([50622], dtype='int64'),
         (1, 767): Int64Index([50623], dtype='int64'),
         (1, 768): Int64Index([50626], dtype='int64'),
         (1, 769): Int64Index([50624], dtype='int64'),
         (1, 770): Int64Index([50633], dtype='int64'),
         (1, 771): Int64Index([50625], dtype='int64'),
         (1, 773): Int64Index([50627], dtype='int64'),
         (1, 777): Int64Index([50629], dtype='int64'),
         (1, 779): Int64Index([50631], dtype='int64'),
         (1, 785): Int64Index([50637], dtype='int64'),
         (1, 786): Int64Index([50632], dtype='int64'),
         (1, 788): Int64Index([50634], dtype='int64'),
         (1, 789): Int64Index([50635], dtype='int64'),
         (1, 790): Int64Index([50636], dtype='int64'),
         (1, 792): Int64Index([50645], dtype='int64'),
         (1, 793): Int64Index([50641], dtype='int64'),
         (1, 794): Int64Index([50638], dtype='int64'),
         (1, 795): Int64Index([50640], dtype='int64'),
         (1, 796): Int64Index([50639], dtype='int64'),
         (1, 798): Int64Index([50642], dtype='int64'),
         (1, 800): Int64Index([50643], dtype='int64'),
         (1, 804): Int64Index([50644], dtype='int64'),
         (1, 805): Int64Index([50646], dtype='int64'),
         (1, 806): Int64Index([50647], dtype='int64'),
         (1, 807): Int64Index([50648], dtype='int64'),
         (1, 815): Int64Index([50649], dtype='int64'),
         (1, 817): Int64Index([50650], dtype='int64'),
         (1, 821): Int64Index([50651], dtype='int64'),
         (1, 822): Int64Index([50662], dtype='int64'),
         (1, 823): Int64Index([50652], dtype='int64'),
         (1, 826): Int64Index([50655], dtype='int64'),
         (1, 829): Int64Index([50653], dtype='int64'),
         (1, 830): Int64Index([50654], dtype='int64'),
         (1, 831): Int64Index([50656], dtype='int64'),
         (1, 835): Int64Index([50657], dtype='int64'),
         (1, 838): Int64Index([50658], dtype='int64'),
         (1, 839): Int64Index([50659], dtype='int64'),
         (1, 843): Int64Index([50660], dtype='int64'),
         (1, 847): Int64Index([50661], dtype='int64'),
         (1, 852): Int64Index([50663], dtype='int64'),
         (1, 854): Int64Index([50664], dtype='int64'),
         (1, 864): Int64Index([50665], dtype='int64'),
         (1, 865): Int64Index([50666], dtype='int64'),
         (1, 867): Int64Index([50668], dtype='int64'),
         (1, 868): Int64Index([50667], dtype='int64'),
         (1, 870): Int64Index([50669], dtype='int64'),
         (1, 872): Int64Index([50670], dtype='int64'),
         (1, 879): Int64Index([50673], dtype='int64'),
         (1, 880): Int64Index([50671], dtype='int64'),
         (1, 881): Int64Index([50672], dtype='int64'),
         (1, 882): Int64Index([50675], dtype='int64'),
         (1, 883): Int64Index([50674], dtype='int64'),
         (1, 885): Int64Index([50677], dtype='int64'),
         (1, 886): Int64Index([50676], dtype='int64'),
         (1, 887): Int64Index([50682], dtype='int64'),
         (1, 889): Int64Index([50678], dtype='int64'),
         (1, 890): Int64Index([50680], dtype='int64'),
         (1, 892): Int64Index([50679], dtype='int64'),
         (1, 893): Int64Index([50681], dtype='int64'),
         (1, 894): Int64Index([50683], dtype='int64'),
         (1, 895): Int64Index([50691], dtype='int64'),
         (1, 896): Int64Index([50684], dtype='int64'),
         (1, 897): Int64Index([50685], dtype='int64'),
         (1, 899): Int64Index([50687], dtype='int64'),
         (1, 901): Int64Index([50686], dtype='int64'),
         (1, 902): Int64Index([50690], dtype='int64'),
         (1, 903): Int64Index([50688], dtype='int64'),
         (1, 907): Int64Index([50689], dtype='int64'),
         (1, 910): Int64Index([50696], dtype='int64'),
         (1, 913): Int64Index([50697], dtype='int64'),
         (1, 916): Int64Index([50692], dtype='int64'),
         (1, 917): Int64Index([50703], dtype='int64'),
         (1, 918): Int64Index([50693], dtype='int64'),
         (1, 919): Int64Index([50694], dtype='int64'),
         (1, 921): Int64Index([50695], dtype='int64'),
         (1, 922): Int64Index([50698], dtype='int64'),
         (1, 923): Int64Index([50699], dtype='int64'),
         (1, 924): Int64Index([50701], dtype='int64'),
         (1, 927): Int64Index([50700], dtype='int64'),
         (1, 929): Int64Index([50702], dtype='int64'),
         (1, 930): Int64Index([50710], dtype='int64'),
         (1, 932): Int64Index([50704], dtype='int64'),
         (1, 933): Int64Index([50706], dtype='int64'),
         (1, 934): Int64Index([50705], dtype='int64'),
         (1, 935): Int64Index([50707], dtype='int64'),
         (1, 936): Int64Index([50709], dtype='int64'),
         (1, 938): Int64Index([50708], dtype='int64'),
         (1, 941): Int64Index([50711], dtype='int64'),
         (2, 1): Int64Index([30753], dtype='int64'),
         (2, 5): Int64Index([30750], dtype='int64'),
         (2, 13): Int64Index([30738], dtype='int64'),
         (2, 22): Int64Index([30722], dtype='int64'),
         (2, 30): Int64Index([30761], dtype='int64'),
         (2, 42): Int64Index([30736], dtype='int64'),
         (2, 49): Int64Index([30748], dtype='int64'),
         (2, 64): Int64Index([30758], dtype='int64'),
         (2, 72): Int64Index([30734], dtype='int64'),
         (2, 83): Int64Index([30755], dtype='int64'),
         (2, 87): Int64Index([30735], dtype='int64'),
         (2, 92): Int64Index([30739], dtype='int64'),
         (2, 95): Int64Index([30727], dtype='int64'),
         (2, 102): Int64Index([30728], dtype='int64'),
         (2, 110): Int64Index([30746], dtype='int64'),
         (2, 130): Int64Index([30751], dtype='int64'),
         (2, 178): Int64Index([30733], dtype='int64'),
         (2, 193): Int64Index([30756], dtype='int64'),
         (2, 197): Int64Index([30757], dtype='int64'),
         (2, 200): Int64Index([30724], dtype='int64'),
         (2, 201): Int64Index([30731], dtype='int64'),
         (2, 207): Int64Index([30754], dtype='int64'),
         (2, 213): Int64Index([30747], dtype='int64'),
         (2, 217): Int64Index([30760], dtype='int64'),
         (2, 222): Int64Index([30741], dtype='int64'),
         (2, 234): Int64Index([30726], dtype='int64'),
         (2, 249): Int64Index([30732], dtype='int64'),
         (2, 250): Int64Index([30744], dtype='int64'),
         (2, 256): Int64Index([30752], dtype='int64'),
         (2, 267): Int64Index([30742], dtype='int64'),
         (2, 268): Int64Index([30749], dtype='int64'),
         (2, 271): Int64Index([30745], dtype='int64'),
         (2, 276): Int64Index([30730], dtype='int64'),
         (2, 279): Int64Index([30743], dtype='int64'),
         (2, 280): Int64Index([30759], dtype='int64'),
         (2, 292): Int64Index([30737], dtype='int64'),
         (2, 293): Int64Index([30740], dtype='int64'),
         (2, 301): Int64Index([30729], dtype='int64'),
         (2, 303): Int64Index([30725], dtype='int64'),
         (2, 305): Int64Index([30723], dtype='int64'),
         (2, 320): Int64Index([30763], dtype='int64'),
         (2, 325): Int64Index([30762], dtype='int64'),
         (2, 327): Int64Index([30764], dtype='int64'),
         (2, 346): Int64Index([30765], dtype='int64'),
         (2, 363): Int64Index([30766], dtype='int64'),
         (2, 373): Int64Index([30767], dtype='int64'),
         (2, 374): Int64Index([30768], dtype='int64'),
         (2, 378): Int64Index([30769], dtype='int64'),
         (2, 379): Int64Index([30770], dtype='int64'),
         (2, 385): Int64Index([30771], dtype='int64'),
         (2, 387): Int64Index([30772], dtype='int64'),
         (2, 393): Int64Index([30773], dtype='int64'),
         (2, 398): Int64Index([30774], dtype='int64'),
         (2, 399): Int64Index([30775], dtype='int64'),
         (2, 405): Int64Index([30776], dtype='int64'),
         (2, 407): Int64Index([30777], dtype='int64'),
         (2, 416): Int64Index([30778], dtype='int64'),
         (2, 425): Int64Index([30779], dtype='int64'),
         (2, 429): Int64Index([30780], dtype='int64'),
         (2, 435): Int64Index([30781], dtype='int64'),
         (2, 442): Int64Index([30782], dtype='int64'),
         (2, 450): Int64Index([30783], dtype='int64'),
         (2, 455): Int64Index([30784], dtype='int64'),
         (2, 466): Int64Index([30785], dtype='int64'),
         (2, 472): Int64Index([30786], dtype='int64'),
         (2, 484): Int64Index([30787], dtype='int64'),
         (2, 487): Int64Index([30788], dtype='int64'),
         (2, 495): Int64Index([30789], dtype='int64'),
         (2, 497): Int64Index([30790], dtype='int64'),
         (2, 506): Int64Index([30791], dtype='int64'),
         (2, 521): Int64Index([30792], dtype='int64'),
         (2, 532): Int64Index([30793], dtype='int64'),
         (2, 536): Int64Index([30794], dtype='int64'),
         (2, 543): Int64Index([30795], dtype='int64'),
         (2, 551): Int64Index([30796], dtype='int64'),
         (2, 561): Int64Index([30797], dtype='int64'),
         (2, 566): Int64Index([30798], dtype='int64'),
         (2, 600): Int64Index([30799], dtype='int64'),
         (2, 618): Int64Index([30800], dtype='int64'),
         (2, 621): Int64Index([30802], dtype='int64'),
         (2, 622): Int64Index([30801], dtype='int64'),
         (2, 627): Int64Index([30803], dtype='int64'),
         (2, 632): Int64Index([30804], dtype='int64'),
         (2, 640): Int64Index([30806], dtype='int64'),
         (2, 642): Int64Index([30805], dtype='int64'),
         (2, 643): Int64Index([30807], dtype='int64'),
         (2, 648): Int64Index([30808], dtype='int64'),
         (2, 650): Int64Index([30809], dtype='int64'),
         (2, 653): Int64Index([30810], dtype='int64'),
         (2, 655): Int64Index([30811], dtype='int64'),
         (2, 660): Int64Index([30812], dtype='int64'),
         (2, 671): Int64Index([30813], dtype='int64'),
         (2, 682): Int64Index([30814], dtype='int64'),
         (2, 686): Int64Index([30815], dtype='int64'),
         (2, 705): Int64Index([30816], dtype='int64'),
         (2, 709): Int64Index([30817], dtype='int64'),
         (2, 715): Int64Index([30818], dtype='int64'),
         (2, 727): Int64Index([30819], dtype='int64'),
         (2, 738): Int64Index([30820], dtype='int64'),
         (2, 746): Int64Index([30822], dtype='int64'),
         (2, 749): Int64Index([30821], dtype='int64'),
         (2, 751): Int64Index([30823], dtype='int64'),
         (2, 757): Int64Index([30824], dtype='int64'),
         (2, 764): Int64Index([30825], dtype='int64'),
         (2, 773): Int64Index([30826], dtype='int64'),
         (2, 774): Int64Index([30827], dtype='int64'),
         (2, 790): Int64Index([30828], dtype='int64'),
         (2, 795): Int64Index([30830], dtype='int64'),
         (2, 796): Int64Index([30829], dtype='int64'),
         (2, 798): Int64Index([30831], dtype='int64'),
         (2, 804): Int64Index([30832], dtype='int64'),
         (2, 806): Int64Index([30833], dtype='int64'),
         (2, 807): Int64Index([30834], dtype='int64'),
         (2, 815): Int64Index([30835], dtype='int64'),
         (2, 826): Int64Index([30837], dtype='int64'),
         (2, 830): Int64Index([30836], dtype='int64'),
         (2, 844): Int64Index([30838], dtype='int64'),
         (2, 846): Int64Index([30839], dtype='int64'),
         (2, 864): Int64Index([30840], dtype='int64'),
         (2, 868): Int64Index([30841], dtype='int64'),
         (2, 870): Int64Index([30842], dtype='int64'),
         (2, 880): Int64Index([30843], dtype='int64'),
         (2, 886): Int64Index([30844], dtype='int64'),
         (2, 889): Int64Index([30845], dtype='int64'),
         (2, 892): Int64Index([30846], dtype='int64'),
         (2, 896): Int64Index([30847], dtype='int64'),
         (2, 899): Int64Index([30848], dtype='int64'),
         (2, 916): Int64Index([30849], dtype='int64'),
         (2, 924): Int64Index([30850], dtype='int64'),
         (2, 934): Int64Index([30851], dtype='int64'),
         (2, 943): Int64Index([30852], dtype='int64'),
         (3, 1): Int64Index([47930], dtype='int64'),
         (3, 43): Int64Index([47925], dtype='int64'),
         (3, 49): Int64Index([47927], dtype='int64'),
         (3, 59): Int64Index([47919], dtype='int64'),
         (3, 62): Int64Index([47905], dtype='int64'),
         (3, 63): Int64Index([47910], dtype='int64'),
         (3, 81): Int64Index([47918], dtype='int64'),
         (3, 82): Int64Index([47924], dtype='int64'),
         (3, 95): Int64Index([47909], dtype='int64'),
         (3, 99): Int64Index([47917], dtype='int64'),
         (3, 104): Int64Index([47932], dtype='int64'),
         (3, 130): Int64Index([47929], dtype='int64'),
         (3, 145): Int64Index([47922], dtype='int64'),
         (3, 157): Int64Index([47913], dtype='int64'),
         (3, 160): Int64Index([47911], dtype='int64'),
         (3, 181): Int64Index([47914], dtype='int64'),
         (3, 207): Int64Index([47931], dtype='int64'),
         (3, 216): Int64Index([47923], dtype='int64'),
         (3, 221): Int64Index([47933], dtype='int64'),
         (3, 244): Int64Index([47904], dtype='int64'),
         (3, 246): Int64Index([47916], dtype='int64'),
         (3, 267): Int64Index([47921], dtype='int64'),
         (3, 268): Int64Index([47928], dtype='int64'),
         (3, 269): Int64Index([47926], dtype='int64'),
         (3, 276): Int64Index([47915], dtype='int64'),
         (3, 280): Int64Index([47934], dtype='int64'),
         (3, 286): Int64Index([47906], dtype='int64'),
         (3, 291): Int64Index([47908], dtype='int64'),
         (3, 293): Int64Index([47920], dtype='int64'),
         (3, 301): Int64Index([47912], dtype='int64'),
         (3, 303): Int64Index([47907], dtype='int64'),
         (3, 320): Int64Index([47935], dtype='int64'),
         (3, 336): Int64Index([47936], dtype='int64'),
         (3, 342): Int64Index([47937], dtype='int64'),
         (3, 343): Int64Index([47938], dtype='int64'),
         (3, 346): Int64Index([47939], dtype='int64'),
         (3, 393): Int64Index([47940], dtype='int64'),
         (3, 406): Int64Index([47941], dtype='int64'),
         (3, 417): Int64Index([47942], dtype='int64'),
         (3, 429): Int64Index([47943], dtype='int64'),
         (3, 432): Int64Index([47944], dtype='int64'),
         (3, 435): Int64Index([47945], dtype='int64'),
         (3, 450): Int64Index([47946], dtype='int64'),
         (3, 453): Int64Index([47947], dtype='int64'),
         (3, 456): Int64Index([47948], dtype='int64'),
         (3, 459): Int64Index([47949], dtype='int64'),
         (3, 463): Int64Index([47951], dtype='int64'),
         (3, 472): Int64Index([47950], dtype='int64'),
         (3, 486): Int64Index([47952], dtype='int64'),
         (3, 487): Int64Index([47953], dtype='int64'),
         (3, 497): Int64Index([47954], dtype='int64'),
         (3, 500): Int64Index([47955], dtype='int64'),
         (3, 523): Int64Index([47956], dtype='int64'),
         (3, 534): Int64Index([47958], dtype='int64'),
         (3, 537): Int64Index([47957], dtype='int64'),
         (3, 548): Int64Index([47959], dtype='int64'),
         (3, 551): Int64Index([47960], dtype='int64'),
         (3, 561): Int64Index([47961], dtype='int64'),
         (3, 569): Int64Index([47962], dtype='int64'),
         (3, 580): Int64Index([47966], dtype='int64'),
         (3, 582): Int64Index([47964], dtype='int64'),
         (3, 586): Int64Index([47963], dtype='int64'),
         (3, 592): Int64Index([47965], dtype='int64'),
         (3, 595): Int64Index([47967], dtype='int64'),
         (3, 606): Int64Index([47968], dtype='int64'),
         (3, 621): Int64Index([47970], dtype='int64'),
         (3, 622): Int64Index([47969], dtype='int64'),
         (3, 624): Int64Index([47971], dtype='int64'),
         (3, 654): Int64Index([47972], dtype='int64'),
         (3, 660): Int64Index([47973], dtype='int64'),
         (3, 663): Int64Index([47974], dtype='int64'),
         (3, 682): Int64Index([47975], dtype='int64'),
         (3, 699): Int64Index([47976], dtype='int64'),
         (3, 714): Int64Index([47977], dtype='int64'),
         (3, 747): Int64Index([47978], dtype='int64'),
         (3, 751): Int64Index([47979], dtype='int64'),
         (3, 756): Int64Index([47980], dtype='int64'),
         (3, 793): Int64Index([47982], dtype='int64'),
         (3, 795): Int64Index([47981], dtype='int64'),
         (3, 806): Int64Index([47983], dtype='int64'),
         (3, 854): Int64Index([47984], dtype='int64'),
         (3, 859): Int64Index([47985], dtype='int64'),
         (3, 880): Int64Index([47986], dtype='int64'),
         (3, 886): Int64Index([47987], dtype='int64'),
         (3, 889): Int64Index([47988], dtype='int64'),
         (3, 910): Int64Index([47990], dtype='int64'),
         (3, 916): Int64Index([47989], dtype='int64'),
         (3, 917): Int64Index([47992], dtype='int64'),
         (3, 923): Int64Index([47991], dtype='int64'),
         (3, 936): Int64Index([47993], dtype='int64'),
         (4, 1): Int64Index([32499], dtype='int64'),
         (4, 7): Int64Index([32472], dtype='int64'),
         (4, 10): Int64Index([32473], dtype='int64'),
         (4, 12): Int64Index([32521], dtype='int64'),
         (4, 13): Int64Index([32480], dtype='int64'),
         (4, 16): Int64Index([32504], dtype='int64'),
         (4, 18): Int64Index([32496], dtype='int64'),
         (4, 19): Int64Index([32494], dtype='int64'),
         (4, 22): Int64Index([32456], dtype='int64'),
         (4, 43): Int64Index([32491], dtype='int64'),
         (4, 49): Int64Index([32493], dtype='int64'),
         (4, 59): Int64Index([32478], dtype='int64'),
         (4, 62): Int64Index([32459], dtype='int64'),
         (4, 64): Int64Index([32515], dtype='int64'),
         (4, 77): Int64Index([32511], dtype='int64'),
         (4, 83): Int64Index([32502], dtype='int64'),
         (4, 84): Int64Index([32492], dtype='int64'),
         (4, 87): Int64Index([32479], dtype='int64'),
         (4, 92): Int64Index([32482], dtype='int64'),
         (4, 94): Int64Index([32489], dtype='int64'),
         (4, 99): Int64Index([32477], dtype='int64'),
         (4, 102): Int64Index([32468], dtype='int64'),
         (4, 109): Int64Index([32514], dtype='int64'),
         (4, 115): Int64Index([32457], dtype='int64'),
         (4, 130): Int64Index([32497], dtype='int64'),
         (4, 144): Int64Index([32512], dtype='int64'),
         (4, 151): Int64Index([32503], dtype='int64'),
         (4, 158): Int64Index([32510], dtype='int64'),
         (4, 160): Int64Index([32469], dtype='int64'),
         (4, 189): Int64Index([32481], dtype='int64'),
         (4, 194): Int64Index([32463], dtype='int64'),
         (4, 197): Int64Index([32513], dtype='int64'),
         (4, 198): Int64Index([32488], dtype='int64'),
         (4, 201): Int64Index([32474], dtype='int64'),
         (4, 207): Int64Index([32500], dtype='int64'),
         (4, 210): Int64Index([32461], dtype='int64'),
         (4, 216): Int64Index([32486], dtype='int64'),
         (4, 218): Int64Index([32509], dtype='int64'),
         (4, 219): Int64Index([32508], dtype='int64'),
         (4, 221): Int64Index([32516], dtype='int64'),
         (4, 222): Int64Index([32484], dtype='int64'),
         (4, 232): Int64Index([32501], dtype='int64'),
         (4, 233): Int64Index([32506], dtype='int64'),
         (4, 234): Int64Index([32465], dtype='int64'),
         (4, 249): Int64Index([32476], dtype='int64'),
         (4, 253): Int64Index([32458], dtype='int64'),
         (4, 256): Int64Index([32498], dtype='int64'),
         (4, 264): Int64Index([32490], dtype='int64'),
         (4, 268): Int64Index([32495], dtype='int64'),
         (4, 271): Int64Index([32487], dtype='int64'),
         (4, 276): Int64Index([32471], dtype='int64'),
         (4, 279): Int64Index([32485], dtype='int64'),
         (4, 280): Int64Index([32517], dtype='int64'),
         (4, 286): Int64Index([32460], dtype='int64'),
         (4, 287): Int64Index([32475], dtype='int64'),
         (4, 291): Int64Index([32464], dtype='int64'),
         (4, 293): Int64Index([32483], dtype='int64'),
         (4, 295): Int64Index([32505], dtype='int64'),
         (4, 297): Int64Index([32507], dtype='int64'),
         (4, 299): Int64Index([32466], dtype='int64'),
         (4, 301): Int64Index([32470], dtype='int64'),
         (4, 303): Int64Index([32462], dtype='int64'),
         (4, 308): Int64Index([32467], dtype='int64'),
         (4, 312): Int64Index([32518], dtype='int64'),
         (4, 315): Int64Index([32519], dtype='int64'),
         (4, 318): Int64Index([32520], dtype='int64'),
         (4, 320): Int64Index([32522], dtype='int64'),
         (4, 326): Int64Index([32523], dtype='int64'),
         (4, 327): Int64Index([32524], dtype='int64'),
         (4, 328): Int64Index([32525], dtype='int64'),
         (4, 334): Int64Index([32526], dtype='int64'),
         (4, 336): Int64Index([32527], dtype='int64'),
         (4, 339): Int64Index([32528], dtype='int64'),
         (4, 342): Int64Index([32529], dtype='int64'),
         (4, 343): Int64Index([32530], dtype='int64'),
         (4, 344): Int64Index([32531], dtype='int64'),
         (4, 345): Int64Index([32532], dtype='int64'),
         (4, 346): Int64Index([32533], dtype='int64'),
         (4, 347): Int64Index([32534], dtype='int64'),
         (4, 352): Int64Index([32535], dtype='int64'),
         (4, 363): Int64Index([32536], dtype='int64'),
         (4, 373): Int64Index([32537], dtype='int64'),
         (4, 374): Int64Index([32538], dtype='int64'),
         (4, 378): Int64Index([32539], dtype='int64'),
         (4, 379): Int64Index([32540], dtype='int64'),
         (4, 385): Int64Index([32541], dtype='int64'),
         (4, 387): Int64Index([32542], dtype='int64'),
         (4, 389): Int64Index([32543], dtype='int64'),
         (4, 393): Int64Index([32544], dtype='int64'),
         (4, 394): Int64Index([32545], dtype='int64'),
         (4, 398): Int64Index([32546], dtype='int64'),
         (4, 405): Int64Index([32547], dtype='int64'),
         (4, 406): Int64Index([32548], dtype='int64'),
         (4, 407): Int64Index([32549], dtype='int64'),
         (4, 411): Int64Index([32551], dtype='int64'),
         (4, 412): Int64Index([32553], dtype='int64'),
         (4, 416): Int64Index([32550], dtype='int64'),
         (4, 417): Int64Index([32552], dtype='int64'),
         (4, 421): Int64Index([32556], dtype='int64'),
         (4, 425): Int64Index([32554], dtype='int64'),
         (4, 429): Int64Index([32555], dtype='int64'),
         (4, 435): Int64Index([32557], dtype='int64'),
         (4, 450): Int64Index([32558], dtype='int64'),
         (4, 453): Int64Index([32559], dtype='int64'),
         (4, 455): Int64Index([32560], dtype='int64'),
         (4, 456): Int64Index([32562], dtype='int64'),
         (4, 457): Int64Index([32561], dtype='int64'),
         (4, 466): Int64Index([32564], dtype='int64'),
         (4, 468): Int64Index([32563], dtype='int64'),
         (4, 472): Int64Index([32565], dtype='int64'),
         (4, 474): Int64Index([32566], dtype='int64'),
         (4, 476): Int64Index([32567], dtype='int64'),
         (4, 481): Int64Index([32570], dtype='int64'),
         (4, 484): Int64Index([32568], dtype='int64'),
         (4, 487): Int64Index([32569], dtype='int64'),
         (4, 495): Int64Index([32571], dtype='int64'),
         (4, 497): Int64Index([32572], dtype='int64'),
         (4, 504): Int64Index([32573], dtype='int64'),
         (4, 514): Int64Index([32574], dtype='int64'),
         (4, 524): Int64Index([32575], dtype='int64'),
         (4, 527): Int64Index([32577], dtype='int64'),
         (4, 532): Int64Index([32576], dtype='int64'),
         (4, 533): Int64Index([32578], dtype='int64'),
         (4, 535): Int64Index([32579], dtype='int64'),
         (4, 537): Int64Index([32580], dtype='int64'),
         (4, 538): Int64Index([32581], dtype='int64'),
         (4, 543): Int64Index([32582], dtype='int64'),
         (4, 551): Int64Index([32583], dtype='int64'),
         (4, 554): Int64Index([32584], dtype='int64'),
         (4, 559): Int64Index([32585], dtype='int64'),
         (4, 561): Int64Index([32586], dtype='int64'),
         (4, 562): Int64Index([32587], dtype='int64'),
         (4, 577): Int64Index([32588], dtype='int64'),
         (4, 579): Int64Index([32589], dtype='int64'),
         (4, 591): Int64Index([32590], dtype='int64'),
         (4, 592): Int64Index([32591], dtype='int64'),
         (4, 593): Int64Index([32592], dtype='int64'),
         (4, 600): Int64Index([32593], dtype='int64'),
         (4, 608): Int64Index([32594], dtype='int64'),
         (4, 618): Int64Index([32595], dtype='int64'),
         (4, 621): Int64Index([32597], dtype='int64'),
         (4, 622): Int64Index([32596], dtype='int64'),
         (4, 625): Int64Index([32599], dtype='int64'),
         (4, 627): Int64Index([32598], dtype='int64'),
         (4, 629): Int64Index([32600], dtype='int64'),
         (4, 638): Int64Index([32604], dtype='int64'),
         (4, 640): Int64Index([32602], dtype='int64'),
         (4, 642): Int64Index([32601], dtype='int64'),
         (4, 643): Int64Index([32603], dtype='int64'),
         (4, 645): Int64Index([32605], dtype='int64'),
         (4, 648): Int64Index([32606], dtype='int64'),
         (4, 650): Int64Index([32607], dtype='int64'),
         (4, 653): Int64Index([32609], dtype='int64'),
         (4, 654): Int64Index([32608], dtype='int64'),
         (4, 655): Int64Index([32610], dtype='int64'),
         (4, 659): Int64Index([32611], dtype='int64'),
         (4, 664): Int64Index([32612], dtype='int64'),
         (4, 666): Int64Index([32613], dtype='int64'),
         (4, 671): Int64Index([32614], dtype='int64'),
         (4, 682): Int64Index([32615], dtype='int64'),
         (4, 690): Int64Index([32616], dtype='int64'),
         (4, 707): Int64Index([32617], dtype='int64'),
         (4, 709): Int64Index([32618], dtype='int64'),
         (4, 712): Int64Index([32619], dtype='int64'),
         (4, 715): Int64Index([32620], dtype='int64'),
         (4, 716): Int64Index([32621], dtype='int64'),
         (4, 738): Int64Index([32622], dtype='int64'),
         (4, 747): Int64Index([32623], dtype='int64'),
         (4, 748): Int64Index([32625], dtype='int64'),
         (4, 749): Int64Index([32624], dtype='int64'),
         (4, 757): Int64Index([32626], dtype='int64'),
         (4, 758): Int64Index([32627], dtype='int64'),
         (4, 763): Int64Index([32628], dtype='int64'),
         (4, 764): Int64Index([32629], dtype='int64'),
         (4, 771): Int64Index([32630], dtype='int64'),
         (4, 774): Int64Index([32631], dtype='int64'),
         (4, 780): Int64Index([32632], dtype='int64'),
         (4, 786): Int64Index([32633], dtype='int64'),
         (4, 788): Int64Index([32634], dtype='int64'),
         (4, 790): Int64Index([32635], dtype='int64'),
         (4, 795): Int64Index([32637], dtype='int64'),
         (4, 796): Int64Index([32636], dtype='int64'),
         (4, 804): Int64Index([32638], dtype='int64'),
         (4, 805): Int64Index([32639], dtype='int64'),
         (4, 823): Int64Index([32640], dtype='int64'),
         (4, 826): Int64Index([32641], dtype='int64'),
         (4, 833): Int64Index([32642], dtype='int64'),
         (4, 846): Int64Index([32643], dtype='int64'),
         (4, 851): Int64Index([32644], dtype='int64'),
         (4, 854): Int64Index([32645], dtype='int64'),
         (4, 860): Int64Index([32646], dtype='int64'),
         (4, 864): Int64Index([32647], dtype='int64'),
         (4, 870): Int64Index([32648], dtype='int64'),
         (4, 871): Int64Index([32649], dtype='int64'),
         (4, 875): Int64Index([32650], dtype='int64'),
         (4, 880): Int64Index([32651], dtype='int64'),
         (4, 881): Int64Index([32652], dtype='int64'),
         (4, 882): Int64Index([32654], dtype='int64'),
         (4, 883): Int64Index([32653], dtype='int64'),
         (4, 886): Int64Index([32655], dtype='int64'),
         (4, 889): Int64Index([32656], dtype='int64'),
         (4, 896): Int64Index([32657], dtype='int64'),
         (4, 903): Int64Index([32658], dtype='int64'),
         (4, 913): Int64Index([32661], dtype='int64'),
         (4, 916): Int64Index([32659], dtype='int64'),
         (4, 919): Int64Index([32660], dtype='int64'),
         (4, 933): Int64Index([32663], dtype='int64'),
         (4, 934): Int64Index([32662], dtype='int64'),
         (4, 940): Int64Index([32664], dtype='int64'),
         (5, 1): Int64Index([89376], dtype='int64'),
         (5, 13): Int64Index([89364], dtype='int64'),
         (5, 21): Int64Index([89380], dtype='int64'),
         (5, 28): Int64Index([89369], dtype='int64'),
         (5, 43): Int64Index([89372], dtype='int64'),
         (5, 44): Int64Index([89371], dtype='int64'),
         (5, 72): Int64Index([89363], dtype='int64'),
         (5, 92): Int64Index([89365], dtype='int64'),
         (5, 102): Int64Index([89361], dtype='int64'),
         (5, 109): Int64Index([89381], dtype='int64'),
         (5, 118): Int64Index([89383], dtype='int64'),
         (5, 130): Int64Index([89374], dtype='int64'),
         (5, 135): Int64Index([89370], dtype='int64'),
         (5, 145): Int64Index([89368], dtype='int64'),
         (5, 188): Int64Index([89384], dtype='int64'),
         (5, 207): Int64Index([89377], dtype='int64'),
         (5, 218): Int64Index([89378], dtype='int64'),
         (5, 234): Int64Index([89359], dtype='int64'),
         (5, 255): Int64Index([89386], dtype='int64'),
         (5, 256): Int64Index([89375], dtype='int64'),
         (5, 267): Int64Index([89367], dtype='int64'),
         (5, 269): Int64Index([89373], dtype='int64'),
         (5, 270): Int64Index([89379], dtype='int64'),
         (5, 276): Int64Index([89362], dtype='int64'),
         (5, 280): Int64Index([89382], dtype='int64'),
         (5, 291): Int64Index([89358], dtype='int64'),
         (5, 293): Int64Index([89366], dtype='int64'),
         (5, 303): Int64Index([89357], dtype='int64'),
         (5, 308): Int64Index([89360], dtype='int64'),
         (5, 311): Int64Index([89385], dtype='int64'),
         (5, 314): Int64Index([89387], dtype='int64'),
         (5, 332): Int64Index([89388], dtype='int64'),
         (5, 339): Int64Index([89389], dtype='int64'),
         (5, 344): Int64Index([89390], dtype='int64'),
         (5, 345): Int64Index([89391], dtype='int64'),
         (5, 363): Int64Index([89392], dtype='int64'),
         (5, 367): Int64Index([89393], dtype='int64'),
         (5, 368): Int64Index([89394], dtype='int64'),
         (5, 372): Int64Index([89396], dtype='int64'),
         (5, 374): Int64Index([89395], dtype='int64'),
         (5, 375): Int64Index([89398], dtype='int64'),
         (5, 378): Int64Index([89397], dtype='int64'),
         (5, 388): Int64Index([89399], dtype='int64'),
         (5, 393): Int64Index([89400], dtype='int64'),
         (5, 399): Int64Index([89401], dtype='int64'),
         (5, 405): Int64Index([89402], dtype='int64'),
         (5, 406): Int64Index([89403], dtype='int64'),
         (5, 417): Int64Index([89404], dtype='int64'),
         (5, 422): Int64Index([89405], dtype='int64'),
         (5, 425): Int64Index([89406], dtype='int64'),
         (5, 435): Int64Index([89407], dtype='int64'),
         (5, 437): Int64Index([89408], dtype='int64'),
         (5, 447): Int64Index([89409], dtype='int64'),
         (5, 468): Int64Index([89410], dtype='int64'),
         (5, 504): Int64Index([89411], dtype='int64'),
         (5, 506): Int64Index([89412], dtype='int64'),
         (5, 546): Int64Index([89413], dtype='int64'),
         (5, 551): Int64Index([89414], dtype='int64'),
         (5, 562): Int64Index([89415], dtype='int64'),
         (5, 577): Int64Index([89416], dtype='int64'),
         (5, 593): Int64Index([89417], dtype='int64'),
         (5, 604): Int64Index([89418], dtype='int64'),
         (5, 633): Int64Index([89419], dtype='int64'),
         (5, 643): Int64Index([89420], dtype='int64'),
         (5, 648): Int64Index([89421], dtype='int64'),
         (5, 655): Int64Index([89422], dtype='int64'),
         (5, 666): Int64Index([89423], dtype='int64'),
         (5, 671): Int64Index([89424], dtype='int64'),
         (5, 682): Int64Index([89425], dtype='int64'),
         (5, 709): Int64Index([89426], dtype='int64'),
         (5, 727): Int64Index([89427], dtype='int64'),
         (5, 741): Int64Index([89428], dtype='int64'),
         (5, 763): Int64Index([89429], dtype='int64'),
         (5, 776): Int64Index([89430], dtype='int64'),
         (5, 796): Int64Index([89431], dtype='int64'),
         (5, 805): Int64Index([89432], dtype='int64'),
         (5, 814): Int64Index([89433], dtype='int64'),
         (5, 833): Int64Index([89434], dtype='int64'),
         (5, 864): Int64Index([89435], dtype='int64'),
         (5, 880): Int64Index([89436], dtype='int64'),
         (5, 886): Int64Index([89437], dtype='int64'),
         (5, 892): Int64Index([89438], dtype='int64'),
         (5, 907): Int64Index([89439], dtype='int64'),
         (5, 916): Int64Index([89440], dtype='int64'),
         (5, 919): Int64Index([89441], dtype='int64'),
         (5, 925): Int64Index([89442], dtype='int64'),
         (6, 1): Int64Index([95665], dtype='int64'),
         (6, 9): Int64Index([95669], dtype='int64'),
         (6, 18): Int64Index([95664], dtype='int64'),
         (6, 63): Int64Index([95660], dtype='int64'),
         (6, 71): Int64Index([95668], dtype='int64'),
         (6, 76): Int64Index([95667], dtype='int64'),
         (6, 79): Int64Index([95666], dtype='int64'),
         (6, 90): Int64Index([95662], dtype='int64'),
         (6, 181): Int64Index([95661], dtype='int64'),
         (6, 198): Int64Index([95663], dtype='int64'),
         (6, 409): Int64Index([95670], dtype='int64'),
         (6, 486): Int64Index([95671], dtype='int64'),
         (6, 524): Int64Index([95672], dtype='int64'),
         (6, 537): Int64Index([95673], dtype='int64'),
         (6, 568): Int64Index([95674], dtype='int64'),
         (6, 590): Int64Index([95675], dtype='int64'),
         (6, 655): Int64Index([95676], dtype='int64'),
         (6, 662): Int64Index([95677], dtype='int64'),
         (6, 707): Int64Index([95678], dtype='int64'),
         (6, 758): Int64Index([95679], dtype='int64'),
         (6, 773): Int64Index([95680], dtype='int64'),
         (6, 806): Int64Index([95681], dtype='int64'),
         (6, 828): Int64Index([95682], dtype='int64'),
         (6, 870): Int64Index([95683], dtype='int64'),
         (6, 924): Int64Index([95684], dtype='int64'),
         (6, 936): Int64Index([95685], dtype='int64'),
         (7, 1): Int64Index([36756], dtype='int64'),
         (7, 6): Int64Index([36688], dtype='int64'),
         (7, 7): Int64Index([36706], dtype='int64'),
         (7, 8): Int64Index([36728], dtype='int64'),
         (7, 9): Int64Index([36823], dtype='int64'),
         (7, 10): Int64Index([36707], dtype='int64'),
         ...}



    and display the content only of necessary group


    ```python
    movies_grouped.get_group(251)
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
          <th>Action</th>
          <th>Adventure</th>
          <th>Animation</th>
          <th>Childrens</th>
          <th>Comedy</th>
          <th>Crime</th>
          <th>Documentary</th>
          <th>Drama</th>
          <th>Fantasy</th>
          <th>Film-Noir</th>
          <th>...</th>
          <th>age</th>
          <th>gender</th>
          <th>movie_title</th>
          <th>occupation</th>
          <th>rating</th>
          <th>release_date</th>
          <th>timestamp</th>
          <th>unknown</th>
          <th>user_id</th>
          <th>zip_code</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>409</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>49.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>writer</td>
          <td>3</td>
          <td>1997-07-11</td>
          <td>881251274</td>
          <td>0</td>
          <td>196</td>
          <td>55105</td>
        </tr>
        <tr>
          <th>410</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>23.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>programmer</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>886321764</td>
          <td>0</td>
          <td>305</td>
          <td>94086</td>
        </tr>
        <tr>
          <th>411</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>27.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>student</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>876521678</td>
          <td>0</td>
          <td>286</td>
          <td>15217</td>
        </tr>
        <tr>
          <th>412</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>19.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>student</td>
          <td>4</td>
          <td>1997-07-11</td>
          <td>879544533</td>
          <td>0</td>
          <td>303</td>
          <td>14853</td>
        </tr>
        <tr>
          <th>413</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>29.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>doctor</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>877877434</td>
          <td>0</td>
          <td>299</td>
          <td>63108</td>
        </tr>
        <tr>
          <th>414</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>31.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>marketing</td>
          <td>4</td>
          <td>1997-07-11</td>
          <td>875747514</td>
          <td>0</td>
          <td>63</td>
          <td>75240</td>
        </tr>
        <tr>
          <th>415</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>26.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>executive</td>
          <td>1</td>
          <td>1997-07-11</td>
          <td>878962052</td>
          <td>0</td>
          <td>181</td>
          <td>21218</td>
        </tr>
        <tr>
          <th>416</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>24.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>writer</td>
          <td>4</td>
          <td>1997-07-11</td>
          <td>888904734</td>
          <td>0</td>
          <td>293</td>
          <td>60804</td>
        </tr>
        <tr>
          <th>417</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>24.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>technician</td>
          <td>4</td>
          <td>1997-07-11</td>
          <td>875071843</td>
          <td>0</td>
          <td>1</td>
          <td>85711</td>
        </tr>
        <tr>
          <th>418</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>49.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>educator</td>
          <td>2</td>
          <td>1997-07-11</td>
          <td>879455541</td>
          <td>0</td>
          <td>15</td>
          <td>97301</td>
        </tr>
        <tr>
          <th>419</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>43.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>administrator</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>884196523</td>
          <td>0</td>
          <td>296</td>
          <td>16803</td>
        </tr>
        <tr>
          <th>420</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>18.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>student</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>876954752</td>
          <td>0</td>
          <td>270</td>
          <td>63119</td>
        </tr>
        <tr>
          <th>421</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>53.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>programmer</td>
          <td>4</td>
          <td>1997-07-11</td>
          <td>888103929</td>
          <td>0</td>
          <td>144</td>
          <td>20910</td>
        </tr>
        <tr>
          <th>422</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>59.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>administrator</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>883681723</td>
          <td>0</td>
          <td>131</td>
          <td>15237</td>
        </tr>
        <tr>
          <th>423</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>39.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>administrator</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>891271545</td>
          <td>0</td>
          <td>79</td>
          <td>03755</td>
        </tr>
        <tr>
          <th>424</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>53.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>other</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>888552084</td>
          <td>0</td>
          <td>2</td>
          <td>94043</td>
        </tr>
        <tr>
          <th>425</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>37.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>educator</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>879436035</td>
          <td>0</td>
          <td>310</td>
          <td>91711</td>
        </tr>
        <tr>
          <th>426</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>33.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>educator</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>883417810</td>
          <td>0</td>
          <td>209</td>
          <td>85710</td>
        </tr>
        <tr>
          <th>427</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>28.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>engineer</td>
          <td>4</td>
          <td>1997-07-11</td>
          <td>893081395</td>
          <td>0</td>
          <td>247</td>
          <td>20770</td>
        </tr>
        <tr>
          <th>428</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>24.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>other</td>
          <td>4</td>
          <td>1997-07-11</td>
          <td>891278996</td>
          <td>0</td>
          <td>132</td>
          <td>94612</td>
        </tr>
        <tr>
          <th>429</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>25.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>other</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>875318267</td>
          <td>0</td>
          <td>342</td>
          <td>98006</td>
        </tr>
        <tr>
          <th>430</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>30.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>librarian</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>889814518</td>
          <td>0</td>
          <td>344</td>
          <td>94117</td>
        </tr>
        <tr>
          <th>431</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>28.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>librarian</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>884994119</td>
          <td>0</td>
          <td>345</td>
          <td>94143</td>
        </tr>
        <tr>
          <th>432</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>29.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>NaN</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>891216691</td>
          <td>0</td>
          <td>354</td>
          <td>48197</td>
        </tr>
        <tr>
          <th>433</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>51.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>other</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>880354315</td>
          <td>0</td>
          <td>360</td>
          <td>98027</td>
        </tr>
        <tr>
          <th>434</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>44.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>programmer</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>885063301</td>
          <td>0</td>
          <td>379</td>
          <td>98117</td>
        </tr>
        <tr>
          <th>435</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>36.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>writer</td>
          <td>2</td>
          <td>1997-07-11</td>
          <td>879440098</td>
          <td>0</td>
          <td>385</td>
          <td>10003</td>
        </tr>
        <tr>
          <th>436</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>20.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>NaN</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>893213405</td>
          <td>0</td>
          <td>416</td>
          <td>92626</td>
        </tr>
        <tr>
          <th>437</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>53.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>educator</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>891357070</td>
          <td>0</td>
          <td>420</td>
          <td>02140</td>
        </tr>
        <tr>
          <th>438</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>23.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>librarian</td>
          <td>3</td>
          <td>1997-07-11</td>
          <td>879958603</td>
          <td>0</td>
          <td>449</td>
          <td>55021</td>
        </tr>
        <tr>
          <th>439</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>51.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>lawyer</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>890247385</td>
          <td>0</td>
          <td>444</td>
          <td>53202</td>
        </tr>
        <tr>
          <th>440</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>28.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>engineer</td>
          <td>4</td>
          <td>1997-07-11</td>
          <td>875280180</td>
          <td>0</td>
          <td>468</td>
          <td>02341</td>
        </tr>
        <tr>
          <th>441</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>NaN</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>educator</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>879874582</td>
          <td>0</td>
          <td>486</td>
          <td>93101</td>
        </tr>
        <tr>
          <th>442</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>26.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>writer</td>
          <td>3</td>
          <td>1997-07-11</td>
          <td>881954219</td>
          <td>0</td>
          <td>498</td>
          <td>55408</td>
        </tr>
        <tr>
          <th>443</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>42.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>programmer</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>882996735</td>
          <td>0</td>
          <td>499</td>
          <td>75006</td>
        </tr>
        <tr>
          <th>444</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>20.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>student</td>
          <td>4</td>
          <td>1997-07-11</td>
          <td>888636374</td>
          <td>0</td>
          <td>532</td>
          <td>92705</td>
        </tr>
        <tr>
          <th>445</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>18.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>student</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>882607955</td>
          <td>0</td>
          <td>592</td>
          <td>97520</td>
        </tr>
        <tr>
          <th>446</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>50.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>healthcare</td>
          <td>3</td>
          <td>1997-07-11</td>
          <td>888984417</td>
          <td>0</td>
          <td>655</td>
          <td>60657</td>
        </tr>
        <tr>
          <th>447</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>56.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>librarian</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>880059647</td>
          <td>0</td>
          <td>707</td>
          <td>19146</td>
        </tr>
        <tr>
          <th>448</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>30.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>none</td>
          <td>4</td>
          <td>1997-07-11</td>
          <td>875129238</td>
          <td>0</td>
          <td>756</td>
          <td>90247</td>
        </tr>
        <tr>
          <th>449</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>26.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>student</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>880660087</td>
          <td>0</td>
          <td>771</td>
          <td>15232</td>
        </tr>
        <tr>
          <th>450</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>20.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>student</td>
          <td>3</td>
          <td>1997-07-11</td>
          <td>888538573</td>
          <td>0</td>
          <td>773</td>
          <td>55414</td>
        </tr>
        <tr>
          <th>451</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>21.0</td>
          <td>F</td>
          <td>Shall We Dance? (1996)</td>
          <td>artist</td>
          <td>3</td>
          <td>1997-07-11</td>
          <td>891500109</td>
          <td>0</td>
          <td>782</td>
          <td>33205</td>
        </tr>
        <tr>
          <th>452</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>22.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>engineer</td>
          <td>4</td>
          <td>1997-07-11</td>
          <td>877381484</td>
          <td>0</td>
          <td>844</td>
          <td>95662</td>
        </tr>
        <tr>
          <th>453</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>49.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>librarian</td>
          <td>5</td>
          <td>1997-07-11</td>
          <td>891692657</td>
          <td>0</td>
          <td>883</td>
          <td>50266</td>
        </tr>
        <tr>
          <th>454</th>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>1</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>0</td>
          <td>...</td>
          <td>24.0</td>
          <td>M</td>
          <td>Shall We Dance? (1996)</td>
          <td>other</td>
          <td>4</td>
          <td>1997-07-11</td>
          <td>886832134</td>
          <td>0</td>
          <td>936</td>
          <td>32789</td>
        </tr>
      </tbody>
    </table>
    <p>46 rows × 29 columns</p>
    </div>



    We have just one helpful and powerful option, `filter()`. For demonstrating how you can use it, let’s select at first new DataFrame by grouping movies by `‘age’` column.


    ```python
    age = movies[['user_id','movie_id','rating','timestamp','age','occupation','movie_title','release_date']]\
                .groupby('age')

    for k,v in list(age)[:3]:
    # if you want to see more values uncomment row below and comment the previous row
    #for key, value in age:
        print(k)
        print(v)
    ```

        7.0
               user_id  movie_id  rating  timestamp  age occupation  \
        41          30       242       5  885941156  7.0    student   
        1992        30       286       5  885941156  7.0        NaN   
        3523        30       257       4  885941257  7.0    student   
        4763        30      1007       5  885941156  7.0    student   
        17506       30       258       5  885941156  7.0    student   
        19035       30       294       4  875140648  7.0    student   
        22203       30        29       3  875106638  7.0    student   
        22293       30       683       3  885941798  7.0    student   
        22396       30       403       2  875061066  7.0    student   
        22667       30       435       5  885941156  7.0    student   
        24343       30       172       4  875060742  7.0    student   
        27656       30       231       2  875061066  7.0    student   
        30027       30       181       4  875060217  7.0    student   
        30761       30         2       3  875061066  7.0    student   
        30925       30       161       4  875060883  7.0        NaN   
        31087       30       688       3  885941492  7.0    student   
        33484       30        50       3  875061066  7.0        NaN   
        34339       30       174       5  885941156  7.0    student   
        36820       30         7       4  875140648  7.0    student   
        40317       30       164       4  875060217  7.0    student   
        41400       30       135       5  885941156  7.0        NaN   
        41935       30        69       5  885941156  7.0    student   
        43088       30       255       4  875059984  7.0    student   
        48634       30        82       4  875060217  7.0    student   
        53019       30        28       4  885941321  7.0    student   
        55562       30       751       3  884310551  7.0    student   
        55970       30       313       5  885941156  7.0    student   
        56262       30       315       4  885941412  7.0    student   
        56767       30       252       3  875140740  7.0    student   
        67378       30       259       4  875058280  7.0    student   
        71539       30       289       2  876847817  7.0    student   
        75898       30       304       4  875988548  7.0    student   
        76563       30       321       4  875988547  7.0    student   
        77168       30       538       4  885941798  7.0    student   
        77830       30       531       5  885941156  7.0    student   
        77943       30       539       3  885941454  7.0    student   
        82831       30       892       4  884310496  7.0    student   
        85338       30       678       2  885942002  7.0    student   
        85510       30       873       1  875061066  7.0        NaN   
        88479       30      1013       3  875060334  7.0    student   
        89582       30       319       4  875060217  7.0    student   

                                             movie_title release_date  
        41                                  Kolya (1996)   1997-01-24  
        1992                 English Patient, The (1996)   1996-11-15  
        3523                         Men in Black (1997)   1997-07-04  
        4763                  Waiting for Guffman (1996)   1997-01-31  
        17506                             Contact (1997)   1997-07-11  
        19035                           Liar Liar (1997)   1997-03-21  
        22203                      Batman Forever (1995)   1995-01-01  
        22293                          Rocket Man (1997)   1997-01-01  
        22396                              Batman (1989)   1989-01-01  
        22667  Butch Cassidy and the Sundance Kid (1969)   1969-01-01  
        24343            Empire Strikes Back, The (1980)   1980-01-01  
        27656                      Batman Returns (1992)   1992-01-01  
        30027                  Return of the Jedi (1983)   1997-03-14  
        30761                           GoldenEye (1995)   1995-01-01  
        30925                             Top Gun (1986)   1986-01-01  
        31087                  Leave It to Beaver (1997)   1997-08-22  
        33484                           Star Wars (1977)   1977-01-01  
        34339             Raiders of the Lost Ark (1981)   1981-01-01  
        36820                      Twelve Monkeys (1995)   1995-01-01  
        40317                          Abyss, The (1989)   1989-01-01  
        41400               2001: A Space Odyssey (1968)   1968-01-01  
        41935                        Forrest Gump (1994)   1994-01-01  
        43088            My Best Friend's Wedding (1997)   1997-06-20  
        48634                       Jurassic Park (1993)   1993-01-01  
        53019                           Apollo 13 (1995)   1995-01-01  
        55562                 Tomorrow Never Dies (1997)   1997-01-01  
        55970                             Titanic (1997)   1997-01-01  
        56262                           Apt Pupil (1998)   1998-10-23  
        56767      Lost World: Jurassic Park, The (1997)   1997-05-23  
        67378                George of the Jungle (1997)   1997-01-01  
        71539                               Evita (1996)   1996-12-25  
        75898                       Fly Away Home (1996)   1996-09-13  
        76563                              Mother (1996)   1996-12-25  
        77168                           Anastasia (1997)   1997-01-01  
        77830                               Shine (1996)   1996-11-22  
        77943                          Mouse Hunt (1997)   1997-01-01  
        82831                             Flubber (1997)   1997-01-01  
        85338                             Volcano (1997)   1997-04-25  
        85510                     Picture Perfect (1997)   1997-08-01  
        88479                            Anaconda (1997)   1997-04-11  
        89582            Everyone Says I Love You (1996)   1996-12-06  
        10.0
               user_id  movie_id  rating  timestamp   age occupation  \
        215        471       393       5  889827918  10.0    student   
        2405       471        94       5  889828081  10.0    student   
        2752       471         8       5  889827881  10.0    student   
        7790       471       588       1  889827881  10.0    student   
        9784       471        71       3  889828154  10.0    student   
        11167      471       225       5  889828026  10.0    student   
        13486      471       596       1  889827881  10.0    student   
        13648      471        95       4  889827822  10.0    student   
        17298      471       477       5  889827918  10.0    student   
        23719      471       878       4  889827710  10.0    student   
        24410      471       172       4  889827822  10.0    student   
        33593      471        50       3  889827757  10.0    student   
        42644      471       151       2  889828154  10.0    student   
        45795      471       946       2  889827982  10.0    student   
        48679      471        82       5  889827822  10.0    student   
        57260      471       432       1  889827822  10.0    student   
        57417      471       418       3  889827757  10.0    student   
        57523      471       465       5  889827822  10.0    student   
        59172      471        99       2  889827918  10.0    student   
        65113      471       969       2  889828154  10.0    student   
        77033      471       501       3  889828027  10.0    student   
        80654      471       404       2  889827757  10.0    student   
        81019      471       768       3  889827982  10.0    student   
        83814      471       420       1  889828027  10.0    student   
        83879      471       140       5  889827918  10.0    student   
        84067      471      1219       4  889828026  10.0    student   
        90293      471       627       1  889827881  10.0    student   
        93004      471       102       5  889828081  10.0        NaN   
        95199      471       422       5  889827982  10.0    student   

                                                 movie_title release_date  
        215                            Mrs. Doubtfire (1993)   1993-01-01  
        2405                               Home Alone (1990)   1990-01-01  
        2752                                     Babe (1995)   1995-01-01  
        7790                     Beauty and the Beast (1991)   1991-01-01  
        9784                           Lion King, The (1994)   1994-01-01  
        11167                          101 Dalmatians (1996)   1996-11-27  
        13486            Hunchback of Notre Dame, The (1996)   1996-06-21  
        13648                                 Aladdin (1992)   1992-01-01  
        17298                                 Matilda (1996)   1996-08-02  
        23719                          That Darn Cat! (1997)   1997-02-14  
        24410                Empire Strikes Back, The (1980)   1980-01-01  
        33593                               Star Wars (1977)   1977-01-01  
        42644   Willy Wonka and the Chocolate Factory (1971)   1971-01-01  
        45795                  Fox and the Hound, The (1981)   1981-01-01  
        48679                           Jurassic Park (1993)   1993-01-01  
        57260                                Fantasia (1940)   1940-01-01  
        57417                              Cinderella (1950)   1950-01-01  
        57523                        Jungle Book, The (1994)   1994-01-01  
        59172         Snow White and the Seven Dwarfs (1937)   1937-01-01  
        65113    Winnie the Pooh and the Blustery Day (1968)   1968-01-01  
        77033                                   Dumbo (1941)   1941-01-01  
        80654                               Pinocchio (1940)   1940-01-01  
        81019                                  Casper (1995)   1995-01-01  
        83814                     Alice in Wonderland (1951)   1951-01-01  
        83879  Homeward Bound: The Incredible Journey (1993)   1993-01-01  
        84067                          Goofy Movie, A (1995)   1995-01-01  
        90293           Robin Hood: Prince of Thieves (1991)   1991-01-01  
        93004                         Aristocats, The (1970)   1970-01-01  
        95199         Aladdin and the King of Thieves (1996)   1996-01-01  
        11.0
               user_id  movie_id  rating  timestamp   age occupation  \
        8881       289       742       4  876789463  11.0       none   
        10197      289       117       4  876789514  11.0       none   
        13936      289      1016       5  876789843  11.0       none   
        14811      289       121       3  876789736  11.0       none   
        17281      289       477       2  876790323  11.0       none   
        19923      289       405       2  876790576  11.0       none   
        20210      289       147       3  876789581  11.0       none   
        23220      289       222       2  876789463  11.0       none   
        23786      289       455       4  876790464  11.0        NaN   
        29021      289        24       4  876790292  11.0       none   
        29441      289       109       3  876789628  11.0       none   
        29723      289        21       1  876790499  11.0       none   
        33113      289       926       3  876790611  11.0       none   
        35368      289       815       3  876789581  11.0        NaN   
        36822      289         7       4  876789628  11.0       none   
        42585      289       151       2  876790499  11.0       none   
        43732      289       685       4  876789373  11.0       none   
        44908      289       410       2  876790361  11.0       none   
        50407      289         1       3  876789736  11.0       none   
        58032      289       473       1  876790576  11.0       none   
        63039      289       125       2  876789373  11.0       none   
        63931      289       282       3  876789180  11.0       none   
        68408      289        15       3  876789581  11.0       none   
        83590      289       363       3  876790653  11.0       none   
        87257      289       849       4  876789943  11.0       none   
        94296      289       254       1  876790734  11.0       none   

                                                  movie_title release_date  
        8881                                    Ransom (1996)   1996-11-08  
        10197                                Rock, The (1996)   1996-06-07  
        13936                                  Con Air (1997)   1997-06-06  
        14811                   Independence Day (ID4) (1996)   1996-07-03  
        17281                                  Matilda (1996)   1996-08-02  
        19923                      Mission: Impossible (1996)   1996-05-22  
        20210                 Long Kiss Goodnight, The (1996)   1996-10-05  
        23220                 Star Trek: First Contact (1996)   1996-11-22  
        23786               Jackie Chan's First Strike (1996)   1997-01-10  
        29021                      Rumble in the Bronx (1995)   1996-02-23  
        29441  Mystery Science Theater 3000: The Movie (1996)   1996-04-19  
        29723                   Muppet Treasure Island (1996)   1996-02-16  
        33113                           Down Periscope (1996)   1996-03-01  
        35368                             One Fine Day (1996)   1996-11-30  
        36822                           Twelve Monkeys (1995)   1995-01-01  
        42585    Willy Wonka and the Chocolate Factory (1971)   1971-01-01  
        43732                       Executive Decision (1996)   1996-03-09  
        44908                                  Kingpin (1996)   1996-07-12  
        50407                                Toy Story (1995)   1995-01-01  
        58032                James and the Giant Peach (1996)   1996-04-12  
        63039                               Phenomenon (1996)   1996-06-29  
        63931                          Time to Kill, A (1996)   1996-07-13  
        68408                       Mr. Holland's Opus (1995)   1996-01-29  
        83590                             Sudden Death (1995)   1995-01-01  
        87257                          Days of Thunder (1990)   1990-01-01  
        94296                           Batman & Robin (1997)   1997-06-20  


    Suppose you need remain only those groups where there are less than 100 items. Sure, you may hardly calculate amount of items in each group and then remove not satisfying for condition. But it can be done very easily.


    ```python
    age.filter(lambda x: len(x) < 100).head(10)
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
          <th>occupation</th>
          <th>movie_title</th>
          <th>release_date</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>28</th>
          <td>131</td>
          <td>242</td>
          <td>5</td>
          <td>883681723</td>
          <td>59.0</td>
          <td>administrator</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
        <tr>
          <th>41</th>
          <td>30</td>
          <td>242</td>
          <td>5</td>
          <td>885941156</td>
          <td>7.0</td>
          <td>student</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
        <tr>
          <th>69</th>
          <td>520</td>
          <td>242</td>
          <td>5</td>
          <td>885168819</td>
          <td>62.0</td>
          <td>healthcare</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
        <tr>
          <th>108</th>
          <td>845</td>
          <td>242</td>
          <td>4</td>
          <td>885409493</td>
          <td>64.0</td>
          <td>doctor</td>
          <td>Kolya (1996)</td>
          <td>1997-01-24</td>
        </tr>
        <tr>
          <th>215</th>
          <td>471</td>
          <td>393</td>
          <td>5</td>
          <td>889827918</td>
          <td>10.0</td>
          <td>student</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
        </tr>
        <tr>
          <th>220</th>
          <td>481</td>
          <td>393</td>
          <td>3</td>
          <td>885829045</td>
          <td>73.0</td>
          <td>retired</td>
          <td>Mrs. Doubtfire (1993)</td>
          <td>1993-01-01</td>
        </tr>
        <tr>
          <th>391</th>
          <td>819</td>
          <td>381</td>
          <td>4</td>
          <td>884105841</td>
          <td>59.0</td>
          <td>administrator</td>
          <td>Muriel's Wedding (1994)</td>
          <td>1994-01-01</td>
        </tr>
        <tr>
          <th>422</th>
          <td>131</td>
          <td>251</td>
          <td>5</td>
          <td>883681723</td>
          <td>59.0</td>
          <td>administrator</td>
          <td>Shall We Dance? (1996)</td>
          <td>1997-07-11</td>
        </tr>
        <tr>
          <th>871</th>
          <td>845</td>
          <td>306</td>
          <td>2</td>
          <td>885409374</td>
          <td>64.0</td>
          <td>doctor</td>
          <td>Mrs. Brown (Her Majesty, Mrs. Brown) (1997)</td>
          <td>1997-01-01</td>
        </tr>
        <tr>
          <th>1022</th>
          <td>481</td>
          <td>238</td>
          <td>4</td>
          <td>885828245</td>
          <td>73.0</td>
          <td>retired</td>
          <td>Raising Arizona (1987)</td>
          <td>1987-01-01</td>
        </tr>
      </tbody>
    </table>
    </div>
