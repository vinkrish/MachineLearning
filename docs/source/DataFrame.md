

```python
import pandas as pd
import numpy as np

# We load Google stock data in a DataFrame
Google_stock = pd.read_csv('C:/Users/Vinay/Python Workspace/Nanodegree/goog-1.csv')

# We print some information about Google_stock
print('Google_stock is of type:', type(Google_stock))
print('Google_stock has shape:', Google_stock.shape)
```

    Google_stock is of type: <class 'pandas.core.frame.DataFrame'>
    Google_stock has shape: (3313, 7)
    


```python
Google_stock.head()
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
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2004-08-19</td>
      <td>49.676899</td>
      <td>51.693783</td>
      <td>47.669952</td>
      <td>49.845802</td>
      <td>49.845802</td>
      <td>44994500</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2004-08-20</td>
      <td>50.178635</td>
      <td>54.187561</td>
      <td>49.925285</td>
      <td>53.805050</td>
      <td>53.805050</td>
      <td>23005800</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2004-08-23</td>
      <td>55.017166</td>
      <td>56.373344</td>
      <td>54.172661</td>
      <td>54.346527</td>
      <td>54.346527</td>
      <td>18393200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2004-08-24</td>
      <td>55.260582</td>
      <td>55.439419</td>
      <td>51.450363</td>
      <td>52.096165</td>
      <td>52.096165</td>
      <td>15361800</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2004-08-25</td>
      <td>52.140873</td>
      <td>53.651051</td>
      <td>51.604362</td>
      <td>52.657513</td>
      <td>52.657513</td>
      <td>9257400</td>
    </tr>
  </tbody>
</table>
</div>




```python
Google_stock.head(2)
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
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2004-08-19</td>
      <td>49.676899</td>
      <td>51.693783</td>
      <td>47.669952</td>
      <td>49.845802</td>
      <td>49.845802</td>
      <td>44994500</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2004-08-20</td>
      <td>50.178635</td>
      <td>54.187561</td>
      <td>49.925285</td>
      <td>53.805050</td>
      <td>53.805050</td>
      <td>23005800</td>
    </tr>
  </tbody>
</table>
</div>




```python
Google_stock.tail()
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
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3308</th>
      <td>2017-10-09</td>
      <td>980.000000</td>
      <td>985.424988</td>
      <td>976.109985</td>
      <td>977.000000</td>
      <td>977.000000</td>
      <td>891400</td>
    </tr>
    <tr>
      <th>3309</th>
      <td>2017-10-10</td>
      <td>980.000000</td>
      <td>981.570007</td>
      <td>966.080017</td>
      <td>972.599976</td>
      <td>972.599976</td>
      <td>968400</td>
    </tr>
    <tr>
      <th>3310</th>
      <td>2017-10-11</td>
      <td>973.719971</td>
      <td>990.710022</td>
      <td>972.250000</td>
      <td>989.250000</td>
      <td>989.250000</td>
      <td>1693300</td>
    </tr>
    <tr>
      <th>3311</th>
      <td>2017-10-12</td>
      <td>987.450012</td>
      <td>994.119995</td>
      <td>985.000000</td>
      <td>987.830017</td>
      <td>987.830017</td>
      <td>1262400</td>
    </tr>
    <tr>
      <th>3312</th>
      <td>2017-10-13</td>
      <td>992.000000</td>
      <td>997.210022</td>
      <td>989.000000</td>
      <td>989.679993</td>
      <td>989.679993</td>
      <td>1157700</td>
    </tr>
  </tbody>
</table>
</div>




```python
Google_stock.tail(8)
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
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3305</th>
      <td>2017-10-04</td>
      <td>957.000000</td>
      <td>960.390015</td>
      <td>950.690002</td>
      <td>951.679993</td>
      <td>951.679993</td>
      <td>952400</td>
    </tr>
    <tr>
      <th>3306</th>
      <td>2017-10-05</td>
      <td>955.489990</td>
      <td>970.909973</td>
      <td>955.179993</td>
      <td>969.960022</td>
      <td>969.960022</td>
      <td>1213800</td>
    </tr>
    <tr>
      <th>3307</th>
      <td>2017-10-06</td>
      <td>966.700012</td>
      <td>979.460022</td>
      <td>963.359985</td>
      <td>978.890015</td>
      <td>978.890015</td>
      <td>1173900</td>
    </tr>
    <tr>
      <th>3308</th>
      <td>2017-10-09</td>
      <td>980.000000</td>
      <td>985.424988</td>
      <td>976.109985</td>
      <td>977.000000</td>
      <td>977.000000</td>
      <td>891400</td>
    </tr>
    <tr>
      <th>3309</th>
      <td>2017-10-10</td>
      <td>980.000000</td>
      <td>981.570007</td>
      <td>966.080017</td>
      <td>972.599976</td>
      <td>972.599976</td>
      <td>968400</td>
    </tr>
    <tr>
      <th>3310</th>
      <td>2017-10-11</td>
      <td>973.719971</td>
      <td>990.710022</td>
      <td>972.250000</td>
      <td>989.250000</td>
      <td>989.250000</td>
      <td>1693300</td>
    </tr>
    <tr>
      <th>3311</th>
      <td>2017-10-12</td>
      <td>987.450012</td>
      <td>994.119995</td>
      <td>985.000000</td>
      <td>987.830017</td>
      <td>987.830017</td>
      <td>1262400</td>
    </tr>
    <tr>
      <th>3312</th>
      <td>2017-10-13</td>
      <td>992.000000</td>
      <td>997.210022</td>
      <td>989.000000</td>
      <td>989.679993</td>
      <td>989.679993</td>
      <td>1157700</td>
    </tr>
  </tbody>
</table>
</div>




```python
Google_stock.isnull().any()
```




    Date         False
    Open         False
    High         False
    Low          False
    Close        False
    Adj Close    False
    Volume       False
    dtype: bool




```python
# We get descriptive statistics on our stock data
Google_stock.describe()
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
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>3313.000000</td>
      <td>3313.000000</td>
      <td>3313.000000</td>
      <td>3313.000000</td>
      <td>3313.000000</td>
      <td>3.313000e+03</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>380.186092</td>
      <td>383.493740</td>
      <td>376.519309</td>
      <td>380.072458</td>
      <td>380.072458</td>
      <td>8.038476e+06</td>
    </tr>
    <tr>
      <th>std</th>
      <td>223.818650</td>
      <td>224.974534</td>
      <td>222.473232</td>
      <td>223.853780</td>
      <td>223.853780</td>
      <td>8.399521e+06</td>
    </tr>
    <tr>
      <th>min</th>
      <td>49.274517</td>
      <td>50.541279</td>
      <td>47.669952</td>
      <td>49.681866</td>
      <td>49.681866</td>
      <td>7.900000e+03</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>226.556473</td>
      <td>228.394516</td>
      <td>224.003082</td>
      <td>226.407440</td>
      <td>226.407440</td>
      <td>2.584900e+06</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>293.312286</td>
      <td>295.433502</td>
      <td>289.929291</td>
      <td>293.029114</td>
      <td>293.029114</td>
      <td>5.281300e+06</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>536.650024</td>
      <td>540.000000</td>
      <td>532.409973</td>
      <td>536.690002</td>
      <td>536.690002</td>
      <td>1.065370e+07</td>
    </tr>
    <tr>
      <th>max</th>
      <td>992.000000</td>
      <td>997.210022</td>
      <td>989.000000</td>
      <td>989.679993</td>
      <td>989.679993</td>
      <td>8.276810e+07</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We get descriptive statistics on a single column of our DataFrame
Google_stock['Adj Close'].describe()
```




    count    3313.000000
    mean      380.072458
    std       223.853780
    min        49.681866
    25%       226.407440
    50%       293.029114
    75%       536.690002
    max       989.679993
    Name: Adj Close, dtype: float64




```python
# We print information about our DataFrame  
print()
print('Maximum values of each column:\n', Google_stock.max())
print()
print('Minimum Close value:', Google_stock['Close'].min())
print()
print('Average value of each column:\n', Google_stock.mean())
```

    
    Maximum values of each column:
     Date         2017-10-13
    Open                992
    High             997.21
    Low                 989
    Close            989.68
    Adj Close        989.68
    Volume         82768100
    dtype: object
    
    Minimum Close value: 49.681866
    
    Average value of each column:
     Open         3.801861e+02
    High         3.834937e+02
    Low          3.765193e+02
    Close        3.800725e+02
    Adj Close    3.800725e+02
    Volume       8.038476e+06
    dtype: float64
    


```python
# We display the correlation between columns
Google_stock.corr()
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
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Open</th>
      <td>1.000000</td>
      <td>0.999904</td>
      <td>0.999845</td>
      <td>0.999745</td>
      <td>0.999745</td>
      <td>-0.564258</td>
    </tr>
    <tr>
      <th>High</th>
      <td>0.999904</td>
      <td>1.000000</td>
      <td>0.999834</td>
      <td>0.999868</td>
      <td>0.999868</td>
      <td>-0.562749</td>
    </tr>
    <tr>
      <th>Low</th>
      <td>0.999845</td>
      <td>0.999834</td>
      <td>1.000000</td>
      <td>0.999899</td>
      <td>0.999899</td>
      <td>-0.567007</td>
    </tr>
    <tr>
      <th>Close</th>
      <td>0.999745</td>
      <td>0.999868</td>
      <td>0.999899</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>-0.564967</td>
    </tr>
    <tr>
      <th>Adj Close</th>
      <td>0.999745</td>
      <td>0.999868</td>
      <td>0.999899</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>-0.564967</td>
    </tr>
    <tr>
      <th>Volume</th>
      <td>-0.564258</td>
      <td>-0.562749</td>
      <td>-0.567007</td>
      <td>-0.564967</td>
      <td>-0.564967</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We load Fake Company data in a DataFrame
data = pd.read_csv('C:/Users/Vinay/Python Workspace/Nanodegree/fake_company.csv')
data
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
      <th>Year</th>
      <th>Name</th>
      <th>Department</th>
      <th>Age</th>
      <th>Salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1990</td>
      <td>Alice</td>
      <td>HR</td>
      <td>25</td>
      <td>50000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1990</td>
      <td>Bob</td>
      <td>RD</td>
      <td>30</td>
      <td>48000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1990</td>
      <td>Charlie</td>
      <td>Admin</td>
      <td>45</td>
      <td>55000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1991</td>
      <td>Alice</td>
      <td>HR</td>
      <td>26</td>
      <td>52000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1991</td>
      <td>Bob</td>
      <td>RD</td>
      <td>31</td>
      <td>50000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1991</td>
      <td>Charlie</td>
      <td>Admin</td>
      <td>46</td>
      <td>60000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1992</td>
      <td>Alice</td>
      <td>HR</td>
      <td>27</td>
      <td>60000</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1992</td>
      <td>Bob</td>
      <td>RD</td>
      <td>32</td>
      <td>52000</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1992</td>
      <td>Charlie</td>
      <td>Admin</td>
      <td>47</td>
      <td>62000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We display the total amount of money spent in salaries each year
data.groupby(['Year'])['Salary'].sum()
```




    Year
    1990    153000
    1991    162000
    1992    174000
    Name: Salary, dtype: int64




```python
# We display the average salary per year
data.groupby(['Year'])['Salary'].mean()
```




    Year
    1990    51000
    1991    54000
    1992    58000
    Name: Salary, dtype: int64




```python
# We display the total salary each employee received in all the years they worked for the company
data.groupby(['Name'])['Salary'].sum()
```




    Name
    Alice      162000
    Bob        150000
    Charlie    177000
    Name: Salary, dtype: int64




```python
# We display the salary distribution per department per year.
data.groupby(['Year', 'Department'])['Salary'].sum()
```




    Year  Department
    1990  Admin         55000
          HR            50000
          RD            48000
    1991  Admin         60000
          HR            52000
          RD            50000
    1992  Admin         62000
          HR            60000
          RD            52000
    Name: Salary, dtype: int64




```python

```
