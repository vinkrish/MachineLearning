

```python
import pandas as pd

filename = 'chicago.csv'

# load data file into a dataframe
df = pd.read_csv('data/chicago.csv')
```


```python
df['Start Time'].head()
```




    0    2017-05-29 18:36:27
    1    2017-06-12 19:00:33
    2    2017-02-13 17:02:02
    3    2017-04-24 18:39:45
    4    2017-01-26 15:36:07
    Name: Start Time, dtype: object




```python
# convert the Start Time column to datetime
df['Start Time'] = pd.to_datetime(df['Start Time'])
df['Start Time'].dt.date.head()
```




    0    2017-05-29
    1    2017-06-12
    2    2017-02-13
    3    2017-04-24
    4    2017-01-26
    Name: Start Time, dtype: object




```python
df['Start Time'].dt.time.head()
```




    0    18:36:27
    1    19:00:33
    2    17:02:02
    3    18:39:45
    4    15:36:07
    Name: Start Time, dtype: object




```python
# extract hour from the Start Time column to create an hour column
df['hour'] = df['Start Time'].dt.hour
df['hour'].head()
```




    0    18
    1    19
    2    17
    3    18
    4    15
    Name: hour, dtype: int64




```python
# find the most popular hour
print(df['hour'].mode())
popular_hour = df['hour'].mode()[0]
print(popular_hour)
```

    0    17
    dtype: int64
    17
    


```python
# find the most common hour (from 0 to 23)
popular_hour = df.groupby(['hour']).size().reset_index(name='count')
print()
print(popular_hour)
print()
print(popular_hour['count'].idxmax())
print()
print(popular_hour.loc[popular_hour['count'].idxmax()])
print()
print('Most Frequent Start Hour:', popular_hour.loc[popular_hour['count'].idxmax()].hour)
```

    
        hour  count
    0      0      4
    1      5      2
    2      6     14
    3      7     23
    4      8     22
    5      9     20
    6     10     16
    7     11     19
    8     12     31
    9     13     26
    10    14     21
    11    15     25
    12    16     29
    13    17     53
    14    18     36
    15    19     26
    16    20     11
    17    21     11
    18    22      7
    19    23      4
    
    13
    
    hour     17
    count    53
    Name: 13, dtype: int64
    
    Most Frequent Start Hour: 17
    


```python
CITY_DATA = { 'chicago': 'chicago.csv',
              'new york city': 'new_york_city.csv',
              'washington': 'washington.csv' }

def load_data(city, month, day):    
    # load data file into a dataframe
    df = pd.read_csv('data/' + CITY_DATA[city])

    # convert the Start Time column to datetime
    df['Start Time'] = pd.to_datetime(df['Start Time'])

    # extract month and day of week from Start Time to create new columns
    df['month'] = df['Start Time'].dt.month
    df['day_of_week'] = df['Start Time'].dt.weekday_name


    # filter by month if applicable
    if month != 'all':
        # use the index of the months list to get the corresponding int
        months = ['january', 'february', 'march', 'april', 'may', 'june']
        month = months.index(month) + 1
    
        # filter by month to create the new dataframe
        df = df[df['month'] == month]

    # filter by day of week if applicable
    if day != 'all':
        # filter by day of week to create the new dataframe
        df = df[df['day_of_week'] == day.title()]
    
    return df
```


```python
load_data('chicago', 'march', 'friday')
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
      <th>Start Time</th>
      <th>End Time</th>
      <th>Trip Duration</th>
      <th>Start Station</th>
      <th>End Station</th>
      <th>User Type</th>
      <th>Gender</th>
      <th>Birth Year</th>
      <th>month</th>
      <th>day_of_week</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>40</th>
      <td>2017-03-24 13:06:37</td>
      <td>2017-03-24 13:10:44</td>
      <td>247</td>
      <td>Broadway &amp; Berwyn Ave</td>
      <td>Clark St &amp; Berwyn Ave</td>
      <td>Subscriber</td>
      <td>Female</td>
      <td>1961.0</td>
      <td>3</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>59</th>
      <td>2017-03-03 07:55:48</td>
      <td>2017-03-03 07:57:41</td>
      <td>113</td>
      <td>Clark St &amp; Chicago Ave</td>
      <td>Wells St &amp; Huron St</td>
      <td>Subscriber</td>
      <td>Male</td>
      <td>1981.0</td>
      <td>3</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>68</th>
      <td>2017-03-17 12:14:50</td>
      <td>2017-03-17 12:22:38</td>
      <td>468</td>
      <td>Dearborn Pkwy &amp; Delaware Pl</td>
      <td>State St &amp; Randolph St</td>
      <td>Subscriber</td>
      <td>Female</td>
      <td>1984.0</td>
      <td>3</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>75</th>
      <td>2017-03-10 13:40:54</td>
      <td>2017-03-10 13:45:09</td>
      <td>255</td>
      <td>Clark St &amp; Lake St</td>
      <td>Rush St &amp; Hubbard St</td>
      <td>Subscriber</td>
      <td>Female</td>
      <td>1983.0</td>
      <td>3</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>83</th>
      <td>2017-03-24 14:15:43</td>
      <td>2017-03-24 14:27:04</td>
      <td>681</td>
      <td>Sheridan Rd &amp; Lawrence Ave</td>
      <td>Broadway &amp; Thorndale Ave</td>
      <td>Subscriber</td>
      <td>Male</td>
      <td>1984.0</td>
      <td>3</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>126</th>
      <td>2017-03-24 12:39:19</td>
      <td>2017-03-24 12:52:11</td>
      <td>772</td>
      <td>Michigan Ave &amp; Oak St</td>
      <td>Cannon Dr &amp; Fullerton Ave</td>
      <td>Subscriber</td>
      <td>Male</td>
      <td>1993.0</td>
      <td>3</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>224</th>
      <td>2017-03-31 19:11:12</td>
      <td>2017-03-31 19:18:53</td>
      <td>461</td>
      <td>Damen Ave &amp; Cortland St</td>
      <td>Damen Ave &amp; Pierce Ave</td>
      <td>Subscriber</td>
      <td>Male</td>
      <td>1989.0</td>
      <td>3</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>247</th>
      <td>2017-03-10 08:21:05</td>
      <td>2017-03-10 08:23:28</td>
      <td>143</td>
      <td>Damen Ave &amp; Division St</td>
      <td>Ashland Ave &amp; Division St</td>
      <td>Subscriber</td>
      <td>Male</td>
      <td>1991.0</td>
      <td>3</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>290</th>
      <td>2017-03-24 10:55:53</td>
      <td>2017-03-24 11:01:27</td>
      <td>334</td>
      <td>Wacker Dr &amp; Washington St</td>
      <td>LaSalle St &amp; Jackson Blvd</td>
      <td>Subscriber</td>
      <td>Male</td>
      <td>1961.0</td>
      <td>3</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>343</th>
      <td>2017-03-17 17:51:31</td>
      <td>2017-03-17 18:00:16</td>
      <td>525</td>
      <td>Milwaukee Ave &amp; Grand Ave</td>
      <td>State St &amp; Pearson St</td>
      <td>Subscriber</td>
      <td>Male</td>
      <td>1989.0</td>
      <td>3</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>348</th>
      <td>2017-03-31 07:47:14</td>
      <td>2017-03-31 07:55:38</td>
      <td>504</td>
      <td>Canal St &amp; Madison St</td>
      <td>Wabash Ave &amp; Adams St</td>
      <td>Subscriber</td>
      <td>Male</td>
      <td>1953.0</td>
      <td>3</td>
      <td>Friday</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
