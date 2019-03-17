

```python
import pandas as pd
```


```python
# We create a Pandas Series that stores a grocery list
groceries = pd.Series(data = [30, 6, 'Yes', 'No'], index = ['eggs', 'apples', 'milk', 'bread'])

# We display the Groceries Pandas Series
print(groceries)
print()

# We print some information about Groceries
print('Groceries has shape:', groceries.shape)
print('Groceries has dimension:', groceries.ndim)
print('Groceries has a total of', groceries.size, 'elements')
print()

# We print the index and data of Groceries
print('The data in Groceries is:', groceries.values)
print('The index of Groceries is:', groceries.index)
print()

# We check whether bananas is a food item (an index) in Groceries
x = 'bananas' in groceries

# We check whether bread is a food item (an index) in Groceries
y = 'bread' in groceries

# We print the results
print('Is bananas an index label in Groceries:', x)
print('Is bread an index label in Groceries:', y)
```

    eggs       30
    apples      6
    milk      Yes
    bread      No
    dtype: object
    
    Groceries has shape: (4,)
    Groceries has dimension: 1
    Groceries has a total of 4 elements
    
    The data in Groceries is: [30 6 'Yes' 'No']
    The index of Groceries is: Index(['eggs', 'apples', 'milk', 'bread'], dtype='object')
    
    Is bananas an index label in Groceries: False
    Is bread an index label in Groceries: True
    


```python
# We access elements in Groceries using index labels:

# We use a single index label
print('How many eggs do we need to buy:', groceries['eggs'])
print()

# we can access multiple index labels
print('Do we need milk and bread:\n', groceries[['milk', 'bread']]) 
print()

# we use loc to access multiple index labels
print('How many eggs and apples do we need to buy:\n', groceries.loc[['eggs', 'apples']]) 
print()

# We access elements in Groceries using numerical indices:

# we use multiple numerical indices
print('How many eggs and apples do we need to buy:\n',  groceries[[0, 1]]) 
print()

# We use a negative numerical index
print('Do we need bread:\n', groceries[[-1]]) 
print()

# We use a single numerical index
print('How many eggs do we need to buy:', groceries[0]) 
print()
# we use iloc to access multiple numerical indices
print('Do we need milk and bread:\n', groceries.iloc[[2, 3]])
```

    How many eggs do we need to buy: 30
    
    Do we need milk and bread:
     milk     Yes
    bread     No
    dtype: object
    
    How many eggs and apples do we need to buy:
     eggs      30
    apples     6
    dtype: object
    
    How many eggs and apples do we need to buy:
     eggs      30
    apples     6
    dtype: object
    
    Do we need bread:
     bread    No
    dtype: object
    
    How many eggs do we need to buy: 30
    
    Do we need milk and bread:
     milk     Yes
    bread     No
    dtype: object
    


```python
# We display the original grocery list
print('Original Grocery List:\n', groceries)

# We change the number of eggs to 2
groceries['eggs'] = 2

# We display the changed grocery list
print()
print('Modified Grocery List:\n', groceries)
```

    Original Grocery List:
     eggs       30
    apples      6
    milk      Yes
    bread      No
    dtype: object
    
    Modified Grocery List:
     eggs        2
    apples      6
    milk      Yes
    bread      No
    dtype: object
    


```python
# We display the original grocery list
print('Original Grocery List:\n', groceries)

# We remove apples from our grocery list. The drop function removes elements out of place
print()
print('We remove apples (out of place):\n', groceries.drop('apples'))

# When we remove elements out of place the original Series remains intact. To see this
# we display our grocery list again
print()
print('Grocery List after removing apples out of place:\n', groceries)

# We remove apples from our grocery list in place by setting the inplace keyword to True
groceries.drop('apples', inplace = True)

# When we remove elements in place the original Series its modified. To see this
# we display our grocery list again
print()
print('Grocery List after removing apples in place:\n', groceries)
```

    Original Grocery List:
     eggs        2
    apples      6
    milk      Yes
    bread      No
    dtype: object
    
    We remove apples (out of place):
     eggs       2
    milk     Yes
    bread     No
    dtype: object
    
    Grocery List after removing apples out of place:
     eggs        2
    apples      6
    milk      Yes
    bread      No
    dtype: object
    
    Grocery List after removing apples in place:
     eggs       2
    milk     Yes
    bread     No
    dtype: object
    


```python
# We create a Pandas Series that stores a grocery list of just fruits
fruits= pd.Series(data = [10, 6, 3,], index = ['apples', 'oranges', 'bananas'])

# We display the fruits Pandas Series
fruits
```




    apples     10
    oranges     6
    bananas     3
    dtype: int64




```python
# We perform basic element-wise operations using arithmetic symbols
print()
print('fruits + 2:\n', fruits + 2) # We add 2 to each item in fruits
print()
print('fruits - 2:\n', fruits - 2) # We subtract 2 to each item in fruits
print()
print('fruits * 2:\n', fruits * 2) # We multiply each item in fruits by 2 
print()
print('fruits / 2:\n', fruits / 2) # We divide each item in fruits by 2
print()
```

    
    fruits + 2:
     apples     12
    oranges     8
    bananas     5
    dtype: int64
    
    fruits - 2:
     apples     8
    oranges    4
    bananas    1
    dtype: int64
    
    fruits * 2:
     apples     20
    oranges    12
    bananas     6
    dtype: int64
    
    fruits / 2:
     apples     5.0
    oranges    3.0
    bananas    1.5
    dtype: float64
    
    


```python
# We import NumPy as np to be able to use the mathematical functions
import numpy as np

# We print fruits for reference
print('Original grocery list of fruits:\n', fruits)

# We apply different mathematical functions to all elements of fruits
print()
print('EXP(X) = \n', np.exp(fruits))
print() 
print('SQRT(X) =\n', np.sqrt(fruits))
print()
print('POW(X,2) =\n',np.power(fruits,2)) # We raise all elements of fruits to the power of 2
```

    Original grocery list of fruits:
     apples     10
    oranges     6
    bananas     3
    dtype: int64
    
    EXP(X) = 
     apples     22026.465795
    oranges      403.428793
    bananas       20.085537
    dtype: float64
    
    SQRT(X) =
     apples     3.162278
    oranges    2.449490
    bananas    1.732051
    dtype: float64
    
    POW(X,2) =
     apples     100
    oranges     36
    bananas      9
    dtype: int64
    


```python
# We print fruits for reference
print('Original grocery list of fruits:\n ', fruits)
print()

# We add 2 only to the bananas
print('Amount of bananas + 2 = ', fruits['bananas'] + 2)
print()

# We subtract 2 from apples
print('Amount of apples - 2 = ', fruits.iloc[0] - 2)
print()

# We multiply apples and oranges by 2
print('We double the amount of apples and oranges:\n', fruits[['apples', 'oranges']] * 2)
print()

# We divide apples and oranges by 2
print('We half the amount of apples and oranges:\n', fruits.loc[['apples', 'oranges']] / 2)
```

    Original grocery list of fruits:
      apples     10
    oranges     6
    bananas     3
    dtype: int64
    
    Amount of bananas + 2 =  5
    
    Amount of apples - 2 =  8
    
    We double the amount of apples and oranges:
     apples     20
    oranges    12
    dtype: int64
    
    We half the amount of apples and oranges:
     apples     5.0
    oranges    3.0
    dtype: float64
    


```python
# Create a Pandas Series that contains the distance of some planets from the Sun.
# Use the name of the planets as the index to your Pandas Series, and the distance
# from the Sun as your data. The distance from the Sun is in units of 10^6 km

distance_from_sun = [149.6, 1433.5, 227.9, 108.2, 778.6]

planets = ['Earth','Saturn', 'Mars','Venus', 'Jupiter']

# Create a Pandas Series using the above data, with the name of the planets as
# the index and the distance from the Sun as your data.
dist_planets = pd.Series(distance_from_sun, planets)
print(dist_planets)

# Calculate the number of minutes it takes sunlight to reach each planet. You can
# do this by dividing the distance from the Sun for each planet by the speed of light.
# Since in the data above the distance from the Sun is in units of 10^6 km, you can
# use a value for the speed of light of c = 18, since light travels 18 x 10^6 km/minute.
time_light = dist_planets / 18

# Use Boolean indexing to select only those planets for which sunlight takes less
# than 40 minutes to reach them.
close_planets = time_light[time_light.values < 40]

print()
print('close planets\n', close_planets)
```

    Earth       149.6
    Saturn     1433.5
    Mars        227.9
    Venus       108.2
    Jupiter     778.6
    dtype: float64
    
    close planets
     Earth     8.311111
    Mars     12.661111
    Venus     6.011111
    dtype: float64
    


```python
# We create a dictionary of Pandas Series 
items = {'Bob' : pd.Series(data = [245, 25, 55], index = ['bike', 'pants', 'watch']),
         'Alice' : pd.Series(data = [40, 110, 500, 45], index = ['book', 'glasses', 'bike', 'pants'])}

# We print the type of items to see that it is a dictionary
print(type(items))
```

    <class 'dict'>
    


```python
# We create a Pandas DataFrame by passing it a dictionary of Pandas Series
shopping_carts = pd.DataFrame(items)

# We display the DataFrame
shopping_carts
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
      <th>Bob</th>
      <th>Alice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We create a dictionary of Pandas Series without indexes
data = {'Bob' : pd.Series([245, 25, 55]),
        'Alice' : pd.Series([40, 110, 500, 45])}

# We create a DataFrame
df = pd.DataFrame(data)

# We display the DataFrame
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
      <th>Bob</th>
      <th>Alice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>245.0</td>
      <td>40</td>
    </tr>
    <tr>
      <th>1</th>
      <td>25.0</td>
      <td>110</td>
    </tr>
    <tr>
      <th>2</th>
      <td>55.0</td>
      <td>500</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>45</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We print some information about shopping_carts
print('shopping_carts has shape:', shopping_carts.shape)
print('shopping_carts has dimension:', shopping_carts.ndim)
print('shopping_carts has a total of:', shopping_carts.size, 'elements')
print()
print('The data in shopping_carts is:\n', shopping_carts.values)
print()
print('The row index in shopping_carts is:', shopping_carts.index)
print()
print('The column index in shopping_carts is:', shopping_carts.columns)
```

    shopping_carts has shape: (5, 2)
    shopping_carts has dimension: 2
    shopping_carts has a total of: 10 elements
    
    The data in shopping_carts is:
     [[245. 500.]
     [ nan  40.]
     [ nan 110.]
     [ 25.  45.]
     [ 55.  nan]]
    
    The row index in shopping_carts is: Index(['bike', 'book', 'glasses', 'pants', 'watch'], dtype='object')
    
    The column index in shopping_carts is: Index(['Bob', 'Alice'], dtype='object')
    


```python
# We Create a DataFrame that only has Bob's data
bob_shopping_cart = pd.DataFrame(items, columns=['Bob'])

# We display bob_shopping_cart
bob_shopping_cart
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
      <th>Bob</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We Create a DataFrame that only has selected items for both Alice and Bob
sel_shopping_cart = pd.DataFrame(items, index = ['pants', 'book'])

# We display sel_shopping_cart
sel_shopping_cart
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
      <th>Bob</th>
      <th>Alice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We Create a DataFrame that only has selected items for Alice
alice_sel_shopping_cart = pd.DataFrame(items, index = ['glasses', 'bike'], columns = ['Alice'])

# We display alice_sel_shopping_cart
alice_sel_shopping_cart
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
      <th>Alice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>glasses</th>
      <td>110</td>
    </tr>
    <tr>
      <th>bike</th>
      <td>500</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We create a dictionary of lists (arrays)
data = {'Integers' : [1,2,3],
        'Floats' : [4.5, 8.2, 9.6]}

# We create a DataFrame 
df = pd.DataFrame(data)

# We display the DataFrame
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
      <th>Integers</th>
      <th>Floats</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>4.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>8.2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>9.6</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We create a DataFrame and provide the row index
df = pd.DataFrame(data, index = ['label 1', 'label 2', 'label 3'])

# We display the DataFrame
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
      <th>Integers</th>
      <th>Floats</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>label 1</th>
      <td>1</td>
      <td>4.5</td>
    </tr>
    <tr>
      <th>label 2</th>
      <td>2</td>
      <td>8.2</td>
    </tr>
    <tr>
      <th>label 3</th>
      <td>3</td>
      <td>9.6</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We create a list of Python dictionaries
items2 = [{'bikes': 20, 'pants': 30, 'watches': 35}, 
          {'watches': 10, 'glasses': 50, 'bikes': 15, 'pants':5}]

# We create a DataFrame 
store_items = pd.DataFrame(items2)

# We display the DataFrame
store_items
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20</td>
      <td>NaN</td>
      <td>30</td>
      <td>35</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We create a DataFrame  and provide the row index
store_items = pd.DataFrame(items2, index = ['store 1', 'store 2'])

# We display the DataFrame
store_items
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>NaN</td>
      <td>30</td>
      <td>35</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We print the store_items DataFrame
print(store_items)

# We access rows, columns and elements using labels
print()
print('How many bikes are in each store:\n', store_items[['bikes']])
print()
print('How many bikes and pants are in each store:\n', store_items[['bikes', 'pants']])
print()
print('What items are in Store 1:\n', store_items.loc[['store 1']])
print()
print('How many bikes are in Store 2:', store_items['bikes']['store 2'])
```

             bikes  glasses  pants  watches
    store 1     20      NaN     30       35
    store 2     15     50.0      5       10
    
    How many bikes are in each store:
              bikes
    store 1     20
    store 2     15
    
    How many bikes and pants are in each store:
              bikes  pants
    store 1     20     30
    store 2     15      5
    
    What items are in Store 1:
              bikes  glasses  pants  watches
    store 1     20      NaN     30       35
    
    How many bikes are in Store 2: 15
    


```python
# We add a new column named shirts to our store_items DataFrame indicating the number of
# shirts in stock at each store. We will put 15 shirts in store 1 and 2 shirts in store 2
store_items['shirts'] = [15,2]

# We display the modified DataFrame
store_items
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>NaN</td>
      <td>30</td>
      <td>35</td>
      <td>15</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>10</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We make a new column called suits by adding the number of shirts and pants
store_items['suits'] = store_items['pants'] + store_items['shirts']

# We display the modified DataFrame
store_items
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>NaN</td>
      <td>30</td>
      <td>35</td>
      <td>15</td>
      <td>45</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>10</td>
      <td>2</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We create a dictionary from a list of Python dictionaries that will number of items at the new store
new_items = [{'bikes': 20, 'pants': 30, 'watches': 35, 'glasses': 4}]

# We create new DataFrame with the new_items and provide and index labeled store 3
new_store = pd.DataFrame(new_items, index = ['store 3'])

# We display the items at the new store
new_store
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>4</td>
      <td>30</td>
      <td>35</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We append store 3 to our store_items DataFrame
store_items = store_items.append(new_store, sort=False)

# We display the modified DataFrame
store_items
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>NaN</td>
      <td>30</td>
      <td>35</td>
      <td>15.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>10</td>
      <td>2.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>4.0</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We add a new column using data from particular rows in the watches column
store_items['new watches'] = store_items['watches'][1:]

# We display the modified DataFrame
store_items
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>suits</th>
      <th>new watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>NaN</td>
      <td>30</td>
      <td>35</td>
      <td>15.0</td>
      <td>45.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>10</td>
      <td>2.0</td>
      <td>7.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>4.0</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>35.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We insert a new column with label shoes right before the column with numerical index 4
store_items.insert(4, 'shoes', [8,5,0])

# we display the modified DataFrame
store_items
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>watches</th>
      <th>shoes</th>
      <th>shirts</th>
      <th>suits</th>
      <th>new watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>NaN</td>
      <td>30</td>
      <td>35</td>
      <td>8</td>
      <td>15.0</td>
      <td>45.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>10</td>
      <td>5</td>
      <td>2.0</td>
      <td>7.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>4.0</td>
      <td>30</td>
      <td>35</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>35.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We remove the new watches column
store_items.pop('new watches')

# we display the modified DataFrame
store_items
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>watches</th>
      <th>shoes</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>NaN</td>
      <td>30</td>
      <td>35</td>
      <td>8</td>
      <td>15.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>10</td>
      <td>5</td>
      <td>2.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>4.0</td>
      <td>30</td>
      <td>35</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We remove the watches and shoes columns
store_items = store_items.drop(['watches', 'shoes'], axis = 1)

# we display the modified DataFrame
store_items
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>NaN</td>
      <td>30</td>
      <td>15.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>2.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>4.0</td>
      <td>30</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We remove the store 2 and store 1 rows
store_items = store_items.drop(['store 2', 'store 1'], axis = 0)

# we display the modified DataFrame
store_items
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>4.0</td>
      <td>30</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We change the column label bikes to hats
store_items = store_items.rename(columns = {'bikes': 'hats'})

# we display the modified DataFrame
store_items
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
      <th>hats</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>4.0</td>
      <td>30</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We change the row label from store 3 to last store
store_items = store_items.rename(index = {'store 3': 'last store'})

# we display the modified DataFrame
store_items
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
      <th>hats</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>last store</th>
      <td>20</td>
      <td>4.0</td>
      <td>30</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We change the row index to be the data in the pants column
store_items = store_items.set_index('pants')

# we display the modified DataFrame
store_items
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
      <th>hats</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
    <tr>
      <th>pants</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>30</th>
      <td>20</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We create a list of Python dictionaries
items2 = [{'bikes': 20, 'pants': 30, 'watches': 35, 'shirts': 15, 'shoes':8, 'suits':45},
{'watches': 10, 'glasses': 50, 'bikes': 15, 'pants':5, 'shirts': 2, 'shoes':5, 'suits':7},
{'bikes': 20, 'pants': 30, 'watches': 35, 'glasses': 4, 'shoes':10}]

# We create a DataFrame  and provide the row index
store_items = pd.DataFrame(items2, index = ['store 1', 'store 2', 'store 3'])

# We display the DataFrame
store_items
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>NaN</td>
      <td>30</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>35</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>10</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>4.0</td>
      <td>30</td>
      <td>NaN</td>
      <td>10</td>
      <td>NaN</td>
      <td>35</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We count the number of NaN values in store_items
x =  store_items.isnull().sum().sum()

# We print x
print('Number of NaN values in our DataFrame:', x)
```

    Number of NaN values in our DataFrame: 3
    


```python
store_items.isnull()
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items.isnull().sum()
```




    bikes      0
    glasses    1
    pants      0
    shirts     1
    shoes      0
    suits      1
    watches    0
    dtype: int64




```python
# We print the number of non-NaN values in our DataFrame
print()
print('Number of non-NaN values in the columns of our DataFrame:\n', store_items.count())
```

    
    Number of non-NaN values in the columns of our DataFrame:
     bikes      3
    glasses    2
    pants      3
    shirts     2
    shoes      3
    suits      2
    watches    3
    dtype: int64
    


```python
# We drop any rows with NaN values
store_items.dropna(axis = 0)
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We drop any columns with NaN values
store_items.dropna(axis = 1)
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
      <th>bikes</th>
      <th>pants</th>
      <th>shoes</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>30</td>
      <td>8</td>
      <td>35</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>5</td>
      <td>5</td>
      <td>10</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>30</td>
      <td>10</td>
      <td>35</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We replace all NaN values with 0
store_items.fillna(0)
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>0.0</td>
      <td>30</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>35</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>10</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>4.0</td>
      <td>30</td>
      <td>0.0</td>
      <td>10</td>
      <td>0.0</td>
      <td>35</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We replace NaN values with the previous value in the column
store_items.fillna(method = 'ffill', axis = 0)
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>NaN</td>
      <td>30</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>35</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>10</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>4.0</td>
      <td>30</td>
      <td>2.0</td>
      <td>10</td>
      <td>7.0</td>
      <td>35</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We replace NaN values with the previous value in the row
store_items.fillna(method = 'ffill', axis = 1)
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20.0</td>
      <td>20.0</td>
      <td>30.0</td>
      <td>15.0</td>
      <td>8.0</td>
      <td>45.0</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15.0</td>
      <td>50.0</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>5.0</td>
      <td>7.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20.0</td>
      <td>4.0</td>
      <td>30.0</td>
      <td>30.0</td>
      <td>10.0</td>
      <td>10.0</td>
      <td>35.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We replace NaN values with the next value in the column
store_items.fillna(method = 'backfill', axis = 0)
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>50.0</td>
      <td>30</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>35</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>10</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>4.0</td>
      <td>30</td>
      <td>NaN</td>
      <td>10</td>
      <td>NaN</td>
      <td>35</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We replace NaN values with the next value in the row
store_items.fillna(method = 'backfill', axis = 1)
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20.0</td>
      <td>30.0</td>
      <td>30.0</td>
      <td>15.0</td>
      <td>8.0</td>
      <td>45.0</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15.0</td>
      <td>50.0</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>5.0</td>
      <td>7.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20.0</td>
      <td>4.0</td>
      <td>30.0</td>
      <td>10.0</td>
      <td>10.0</td>
      <td>35.0</td>
      <td>35.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We replace NaN values by using linear interpolation using column values
store_items.interpolate(method = 'linear', axis = 0)
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>NaN</td>
      <td>30</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>35</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>50.0</td>
      <td>5</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>10</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>4.0</td>
      <td>30</td>
      <td>2.0</td>
      <td>10</td>
      <td>7.0</td>
      <td>35</td>
    </tr>
  </tbody>
</table>
</div>




```python
# We replace NaN values by using linear interpolation using row values
store_items.interpolate(method = 'linear', axis = 1)
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
      <th>bikes</th>
      <th>glasses</th>
      <th>pants</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20.0</td>
      <td>25.0</td>
      <td>30.0</td>
      <td>15.0</td>
      <td>8.0</td>
      <td>45.0</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15.0</td>
      <td>50.0</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>5.0</td>
      <td>7.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20.0</td>
      <td>4.0</td>
      <td>30.0</td>
      <td>20.0</td>
      <td>10.0</td>
      <td>22.5</td>
      <td>35.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Since we will be working with ratings, we will set the precision of our 
# dataframes to one decimal place.
pd.set_option('precision', 1)

# Create a Pandas DataFrame that contains the ratings some users have given to a
# series of books. The ratings given are in the range from 1 to 5, with 5 being
# the best score. The names of the books, the authors, and the ratings of each user
# are given below:

books = pd.Series(data = ['Great Expectations', 'Of Mice and Men', 'Romeo and Juliet', 'The Time Machine', 'Alice in Wonderland' ])
authors = pd.Series(data = ['Charles Dickens', 'John Steinbeck', 'William Shakespeare', ' H. G. Wells', 'Lewis Carroll' ])

user_1 = pd.Series(data = [3.2, np.nan ,2.5])
user_2 = pd.Series(data = [5., 1.3, 4.0, 3.8])
user_3 = pd.Series(data = [2.0, 2.3, np.nan, 4])
user_4 = pd.Series(data = [4, 3.5, 4, 5, 4.2])

# Users that have np.nan values means that the user has not yet rated that book.
# Use the data above to create a Pandas DataFrame that has the following column
# labels: 'Author', 'Book Title', 'User 1', 'User 2', 'User 3', 'User 4'. Let Pandas
# automatically assign numerical row indices to the DataFrame. 

# Create a dictionary with the data given above
dat = {'Author': authors, 'Book Title': books, 'User 1': user_1, 'User 2': user_2, 'User 3': user_3, 'User 4': user_4}

# Use the dictionary to create a Pandas DataFrame
book_ratings = pd.DataFrame(dat)

# If you created the dictionary correctly you should have a Pandas DataFrame
# that has column labels: 'Author', 'Book Title', 'User 1', 'User 2', 'User 3',
# 'User 4' and row indices 0 through 4.

# Now replace all the NaN values in your DataFrame with the average rating in
# each column. Replace the NaN values in place. HINT: you can use the fillna()
# function with the keyword inplace = True, to do this. Write your code below:
book_ratings.fillna(book_ratings.mean(), inplace=True)
print(book_ratings)
```

                    Author           Book Title  User 1  User 2  User 3  User 4
    0      Charles Dickens   Great Expectations     3.2     5.0     2.0     4.0
    1       John Steinbeck      Of Mice and Men     2.9     1.3     2.3     3.5
    2  William Shakespeare     Romeo and Juliet     2.5     4.0     2.8     4.0
    3          H. G. Wells     The Time Machine     2.9     3.8     4.0     5.0
    4        Lewis Carroll  Alice in Wonderland     2.9     3.5     2.8     4.2
    


```python

```
