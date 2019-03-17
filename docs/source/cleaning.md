
# Cleaning Example
Let's explore ways of fixing some common issues in data. Here's a toy dataset I created for this lesson. It has eleven instances of user-product interactions online, recording whether the user liked the product, how long they viewed the product, whether it was on a website or through a mobile app, and what time they started viewing the product. Can you spot any potential issues in this data?


```python
import pandas as pd

df = pd.read_csv('product_view_data.csv')
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
      <th>user_id</th>
      <th>product_id</th>
      <th>liked</th>
      <th>view_duration</th>
      <th>source</th>
      <th>timestamp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3987</td>
      <td>997021</td>
      <td>True</td>
      <td>1.048242</td>
      <td>web</td>
      <td>2017-09-23 00:18:29.056895</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6300</td>
      <td>865003</td>
      <td>True</td>
      <td>1.688173</td>
      <td>web</td>
      <td>2017-09-21 02:20:22.022096</td>
    </tr>
    <tr>
      <th>2</th>
      <td>6451</td>
      <td>712951</td>
      <td>False</td>
      <td>NaN</td>
      <td>mobile</td>
      <td>2017-09-07 11:57:50.044683</td>
    </tr>
    <tr>
      <th>3</th>
      <td>7782</td>
      <td>283235</td>
      <td>True</td>
      <td>0.194162</td>
      <td>mobile</td>
      <td>2017-09-17 03:48:20.019677</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7782</td>
      <td>283235</td>
      <td>True</td>
      <td>0.194162</td>
      <td>mobile</td>
      <td>2017-09-17 03:48:20.019677</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5700</td>
      <td>587019</td>
      <td>False</td>
      <td>0.493194</td>
      <td>web</td>
      <td>2017-09-07 00:25:07.019097</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3400</td>
      <td>505123</td>
      <td>True</td>
      <td>NaN</td>
      <td>web</td>
      <td>2017-09-07 13:53:21.008403</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8403</td>
      <td>459916</td>
      <td>False</td>
      <td>0.675041</td>
      <td>mobile</td>
      <td>2017-09-25 21:54:00.028323</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8965</td>
      <td>943363</td>
      <td>False</td>
      <td>NaN</td>
      <td>web</td>
      <td>2017-09-17 15:12:21.059489</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9693</td>
      <td>787546</td>
      <td>True</td>
      <td>0.101743</td>
      <td>web</td>
      <td>2017-09-26 12:34:46.012559</td>
    </tr>
    <tr>
      <th>10</th>
      <td>4107</td>
      <td>811855</td>
      <td>False</td>
      <td>3.112086</td>
      <td>web</td>
      <td>2017-09-01 10:50:07.042593</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 11 entries, 0 to 10
    Data columns (total 6 columns):
    user_id          11 non-null int64
    product_id       11 non-null int64
    liked            11 non-null bool
    view_duration    8 non-null float64
    source           11 non-null object
    timestamp        11 non-null object
    dtypes: bool(1), float64(1), int64(2), object(2)
    memory usage: 531.0+ bytes
    

## Let's address three issues in this dataset that are quite common in the real world
- Missing data (in the `view_duration` columns)
- Duplicates (rows 3 and 4)
- Incorrect Datatypes (`timestamp` is represented as a string)

## Filling null values
In the dataframe above, you can see null values represented as `NaN`, which stands for not a number. From the output of `df.info()` you can see that there are 8 non-null values, which leaves 3 null values of the 11 entries. [Missing data](https://en.wikipedia.org/wiki/Missing_data) is an issue that should be handled differently depending on several factors, such as the reason those values are missing and whether the occurrences seem random. One way of handling them is [imputing](https://en.wikipedia.org/wiki/Imputation_(statistics) them with the mean. You can do this quickly and efficiently with a convenient function from Pandas.


```python
# get the mean of the column with missing data
mean = df['view_duration'].mean()
print(mean)
```

    0.9383504902905304
    


```python
# replace NaN values with the mean
df['view_duration'].fillna(mean)
```




    0     1.048242
    1     1.688173
    2     0.938350
    3     0.194162
    4     0.194162
    5     0.493194
    6     0.938350
    7     0.675041
    8     0.938350
    9     0.101743
    10    3.112086
    Name: view_duration, dtype: float64



Let's look at the dataframe now - did this fix the problem?


```python
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
      <th>user_id</th>
      <th>product_id</th>
      <th>liked</th>
      <th>view_duration</th>
      <th>source</th>
      <th>timestamp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3987</td>
      <td>997021</td>
      <td>True</td>
      <td>1.048242</td>
      <td>web</td>
      <td>2017-09-23 00:18:29.056895</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6300</td>
      <td>865003</td>
      <td>True</td>
      <td>1.688173</td>
      <td>web</td>
      <td>2017-09-21 02:20:22.022096</td>
    </tr>
    <tr>
      <th>2</th>
      <td>6451</td>
      <td>712951</td>
      <td>False</td>
      <td>NaN</td>
      <td>mobile</td>
      <td>2017-09-07 11:57:50.044683</td>
    </tr>
    <tr>
      <th>3</th>
      <td>7782</td>
      <td>283235</td>
      <td>True</td>
      <td>0.194162</td>
      <td>mobile</td>
      <td>2017-09-17 03:48:20.019677</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7782</td>
      <td>283235</td>
      <td>True</td>
      <td>0.194162</td>
      <td>mobile</td>
      <td>2017-09-17 03:48:20.019677</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5700</td>
      <td>587019</td>
      <td>False</td>
      <td>0.493194</td>
      <td>web</td>
      <td>2017-09-07 00:25:07.019097</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3400</td>
      <td>505123</td>
      <td>True</td>
      <td>NaN</td>
      <td>web</td>
      <td>2017-09-07 13:53:21.008403</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8403</td>
      <td>459916</td>
      <td>False</td>
      <td>0.675041</td>
      <td>mobile</td>
      <td>2017-09-25 21:54:00.028323</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8965</td>
      <td>943363</td>
      <td>False</td>
      <td>NaN</td>
      <td>web</td>
      <td>2017-09-17 15:12:21.059489</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9693</td>
      <td>787546</td>
      <td>True</td>
      <td>0.101743</td>
      <td>web</td>
      <td>2017-09-26 12:34:46.012559</td>
    </tr>
    <tr>
      <th>10</th>
      <td>4107</td>
      <td>811855</td>
      <td>False</td>
      <td>3.112086</td>
      <td>web</td>
      <td>2017-09-01 10:50:07.042593</td>
    </tr>
  </tbody>
</table>
</div>



Instead of making changes to the original column, it just returned a new column with the changes, which we didn't store anywhere. To keep the changes, make sure to assign it to the original like this:

`df['view_duration'] = df['view_duration'].fillna(mean)`

Alternatively, you can use an extra parameter as shown in the cell below.


```python
# replace NaN values and make changes in place
df['view_duration'].fillna(mean, inplace=True)
```


```python
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
      <th>user_id</th>
      <th>product_id</th>
      <th>liked</th>
      <th>view_duration</th>
      <th>source</th>
      <th>timestamp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3987</td>
      <td>997021</td>
      <td>True</td>
      <td>1.048242</td>
      <td>web</td>
      <td>2017-09-23 00:18:29.056895</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6300</td>
      <td>865003</td>
      <td>True</td>
      <td>1.688173</td>
      <td>web</td>
      <td>2017-09-21 02:20:22.022096</td>
    </tr>
    <tr>
      <th>2</th>
      <td>6451</td>
      <td>712951</td>
      <td>False</td>
      <td>0.938350</td>
      <td>mobile</td>
      <td>2017-09-07 11:57:50.044683</td>
    </tr>
    <tr>
      <th>3</th>
      <td>7782</td>
      <td>283235</td>
      <td>True</td>
      <td>0.194162</td>
      <td>mobile</td>
      <td>2017-09-17 03:48:20.019677</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7782</td>
      <td>283235</td>
      <td>True</td>
      <td>0.194162</td>
      <td>mobile</td>
      <td>2017-09-17 03:48:20.019677</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5700</td>
      <td>587019</td>
      <td>False</td>
      <td>0.493194</td>
      <td>web</td>
      <td>2017-09-07 00:25:07.019097</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3400</td>
      <td>505123</td>
      <td>True</td>
      <td>0.938350</td>
      <td>web</td>
      <td>2017-09-07 13:53:21.008403</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8403</td>
      <td>459916</td>
      <td>False</td>
      <td>0.675041</td>
      <td>mobile</td>
      <td>2017-09-25 21:54:00.028323</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8965</td>
      <td>943363</td>
      <td>False</td>
      <td>0.938350</td>
      <td>web</td>
      <td>2017-09-17 15:12:21.059489</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9693</td>
      <td>787546</td>
      <td>True</td>
      <td>0.101743</td>
      <td>web</td>
      <td>2017-09-26 12:34:46.012559</td>
    </tr>
    <tr>
      <th>10</th>
      <td>4107</td>
      <td>811855</td>
      <td>False</td>
      <td>3.112086</td>
      <td>web</td>
      <td>2017-09-01 10:50:07.042593</td>
    </tr>
  </tbody>
</table>
</div>



Success!

## Dropping Duplicates
There are multiple reasons you may end up with duplicated data, like combined data sources or human error. Here's a simple scenario where two rows (3 and 4) are identical. This toy dataset is small enough for us to count visually. For bigger datasets, you can use this function to see which rows are duplicates.


```python
# By default, this marks duplicates as True excluding the first instance,
# and it considers a row to be a duplicate only if the values in all
# columns match. You can change both of these with its parameters.
df.duplicated()
```




    0     False
    1     False
    2     False
    3     False
    4      True
    5     False
    6     False
    7     False
    8     False
    9     False
    10    False
    dtype: bool




```python
# For larger datasets, it would probably be more helpful to get a count
# of duplicates in the dataset like this
sum(df.duplicated())
```




    1




```python
# You can drop duplicated data with this function. Remember to use
# assigned it to the original dataframe or use inplace to keep changes!
df.drop_duplicates(inplace=True)
```


```python
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
      <th>user_id</th>
      <th>product_id</th>
      <th>liked</th>
      <th>view_duration</th>
      <th>source</th>
      <th>timestamp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3987</td>
      <td>997021</td>
      <td>True</td>
      <td>1.048242</td>
      <td>web</td>
      <td>2017-09-23 00:18:29.056895</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6300</td>
      <td>865003</td>
      <td>True</td>
      <td>1.688173</td>
      <td>web</td>
      <td>2017-09-21 02:20:22.022096</td>
    </tr>
    <tr>
      <th>2</th>
      <td>6451</td>
      <td>712951</td>
      <td>False</td>
      <td>0.938350</td>
      <td>mobile</td>
      <td>2017-09-07 11:57:50.044683</td>
    </tr>
    <tr>
      <th>3</th>
      <td>7782</td>
      <td>283235</td>
      <td>True</td>
      <td>0.194162</td>
      <td>mobile</td>
      <td>2017-09-17 03:48:20.019677</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5700</td>
      <td>587019</td>
      <td>False</td>
      <td>0.493194</td>
      <td>web</td>
      <td>2017-09-07 00:25:07.019097</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3400</td>
      <td>505123</td>
      <td>True</td>
      <td>0.938350</td>
      <td>web</td>
      <td>2017-09-07 13:53:21.008403</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8403</td>
      <td>459916</td>
      <td>False</td>
      <td>0.675041</td>
      <td>mobile</td>
      <td>2017-09-25 21:54:00.028323</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8965</td>
      <td>943363</td>
      <td>False</td>
      <td>0.938350</td>
      <td>web</td>
      <td>2017-09-17 15:12:21.059489</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9693</td>
      <td>787546</td>
      <td>True</td>
      <td>0.101743</td>
      <td>web</td>
      <td>2017-09-26 12:34:46.012559</td>
    </tr>
    <tr>
      <th>10</th>
      <td>4107</td>
      <td>811855</td>
      <td>False</td>
      <td>3.112086</td>
      <td>web</td>
      <td>2017-09-01 10:50:07.042593</td>
    </tr>
  </tbody>
</table>
</div>



Awesome! You can see we've dropped row 4 - the row marked as a duplicate. This was a simple situation where the entire row was identical. You could imagine duplicated data scenarios that are a bit more complicated.

For example, let's say we had data on patients from a hospital. What happens when you come across two rows with the same patient id but different data on medical exam results? Do you combine them? Only keep the latest one? This is a situation you'd have to investigate more. For this scenario, you'd likely identify duplicates only based on the column recording the patient's id. You can use the `subset` paramater in [duplicated()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.duplicated.html) and [drop_duplicates()](http://pandas.pydata.org/pandas-docs/version/0.17.1/generated/pandas.DataFrame.drop_duplicates.html) to do this.

## Converting to datetime
Incorrect datatypes is also a problem data analysts frequently come across. In this case, the timestamps are represented as strings instead of datetimes. This isn't critical, but datetimes are much more convenient to work with if you want to extract specific information from them or filter them more easily.


```python
# This shows the datatype of timestamp is not yet datetime
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 10 entries, 0 to 10
    Data columns (total 6 columns):
    user_id          10 non-null int64
    product_id       10 non-null int64
    liked            10 non-null bool
    view_duration    10 non-null float64
    source           10 non-null object
    timestamp        10 non-null object
    dtypes: bool(1), float64(1), int64(2), object(2)
    memory usage: 490.0+ bytes
    


```python
# Let's use this awesome function to convert this column to datetime
df['timestamp'] = pd.to_datetime(df['timestamp'])
```


```python
# Now we can see timestamp is represented as a datetime
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 10 entries, 0 to 10
    Data columns (total 6 columns):
    user_id          10 non-null int64
    product_id       10 non-null int64
    liked            10 non-null bool
    view_duration    10 non-null float64
    source           10 non-null object
    timestamp        10 non-null datetime64[ns]
    dtypes: bool(1), datetime64[ns](1), float64(1), int64(2), object(1)
    memory usage: 490.0+ bytes
    

Note that even if you save this to a csv file after making this change, it will be read as a string by default the next time you open it. You'll still have to convert it after opening the csv file, or use parameters like `parse_dates` in the [read_csv()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_csv.html) function. [to_datetime()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.to_datetime.html) provides parameters for more options if the strings you have to parse are formatted unconventionally.
