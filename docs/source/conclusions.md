
# Drawing Conclusions Example
Let's address a question we posed with this cancer data earlier in the lesson - does the size of a tumor affect its malignancy? We can use descriptive statistics and visualizations to help us.


```python
import pandas as pd

df = pd.read_csv('cancer_data_edited.csv')
df.head()
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
      <th>diagnosis</th>
      <th>radius</th>
      <th>texture</th>
      <th>perimeter</th>
      <th>area</th>
      <th>smoothness</th>
      <th>compactness</th>
      <th>concavity</th>
      <th>concave_points</th>
      <th>symmetry</th>
      <th>fractal_dimension</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>842302</td>
      <td>M</td>
      <td>17.99</td>
      <td>19.293431</td>
      <td>122.80</td>
      <td>1001.0</td>
      <td>0.118400</td>
      <td>0.27760</td>
      <td>0.3001</td>
      <td>0.14710</td>
      <td>0.2419</td>
      <td>0.07871</td>
    </tr>
    <tr>
      <th>1</th>
      <td>842517</td>
      <td>M</td>
      <td>20.57</td>
      <td>17.770000</td>
      <td>132.90</td>
      <td>1326.0</td>
      <td>0.084740</td>
      <td>0.07864</td>
      <td>0.0869</td>
      <td>0.07017</td>
      <td>0.1812</td>
      <td>0.05667</td>
    </tr>
    <tr>
      <th>2</th>
      <td>84300903</td>
      <td>M</td>
      <td>19.69</td>
      <td>21.250000</td>
      <td>130.00</td>
      <td>1203.0</td>
      <td>0.109600</td>
      <td>0.15990</td>
      <td>0.1974</td>
      <td>0.12790</td>
      <td>0.2069</td>
      <td>0.05999</td>
    </tr>
    <tr>
      <th>3</th>
      <td>84348301</td>
      <td>M</td>
      <td>11.42</td>
      <td>20.380000</td>
      <td>77.58</td>
      <td>386.1</td>
      <td>0.096087</td>
      <td>0.28390</td>
      <td>0.2414</td>
      <td>0.10520</td>
      <td>0.2597</td>
      <td>0.09744</td>
    </tr>
    <tr>
      <th>4</th>
      <td>84358402</td>
      <td>M</td>
      <td>20.29</td>
      <td>14.340000</td>
      <td>135.10</td>
      <td>1297.0</td>
      <td>0.100300</td>
      <td>0.13280</td>
      <td>0.1980</td>
      <td>0.10430</td>
      <td>0.1809</td>
      <td>0.05883</td>
    </tr>
  </tbody>
</table>
</div>



# Selecting Data with Masks
In order to do this analysis, we'd ideally compare sizes of tumors that are benign and malignant. We can use __masks__ to select all rows in the dataframe that were diagnosed as malignant.


```python
# Create new dataframe with only malignant tumors
df_m = df[df['diagnosis'] == 'M']
df_m.head()
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
      <th>diagnosis</th>
      <th>radius</th>
      <th>texture</th>
      <th>perimeter</th>
      <th>area</th>
      <th>smoothness</th>
      <th>compactness</th>
      <th>concavity</th>
      <th>concave_points</th>
      <th>symmetry</th>
      <th>fractal_dimension</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>842302</td>
      <td>M</td>
      <td>17.99</td>
      <td>19.293431</td>
      <td>122.80</td>
      <td>1001.0</td>
      <td>0.118400</td>
      <td>0.27760</td>
      <td>0.3001</td>
      <td>0.14710</td>
      <td>0.2419</td>
      <td>0.07871</td>
    </tr>
    <tr>
      <th>1</th>
      <td>842517</td>
      <td>M</td>
      <td>20.57</td>
      <td>17.770000</td>
      <td>132.90</td>
      <td>1326.0</td>
      <td>0.084740</td>
      <td>0.07864</td>
      <td>0.0869</td>
      <td>0.07017</td>
      <td>0.1812</td>
      <td>0.05667</td>
    </tr>
    <tr>
      <th>2</th>
      <td>84300903</td>
      <td>M</td>
      <td>19.69</td>
      <td>21.250000</td>
      <td>130.00</td>
      <td>1203.0</td>
      <td>0.109600</td>
      <td>0.15990</td>
      <td>0.1974</td>
      <td>0.12790</td>
      <td>0.2069</td>
      <td>0.05999</td>
    </tr>
    <tr>
      <th>3</th>
      <td>84348301</td>
      <td>M</td>
      <td>11.42</td>
      <td>20.380000</td>
      <td>77.58</td>
      <td>386.1</td>
      <td>0.096087</td>
      <td>0.28390</td>
      <td>0.2414</td>
      <td>0.10520</td>
      <td>0.2597</td>
      <td>0.09744</td>
    </tr>
    <tr>
      <th>4</th>
      <td>84358402</td>
      <td>M</td>
      <td>20.29</td>
      <td>14.340000</td>
      <td>135.10</td>
      <td>1297.0</td>
      <td>0.100300</td>
      <td>0.13280</td>
      <td>0.1980</td>
      <td>0.10430</td>
      <td>0.1809</td>
      <td>0.05883</td>
    </tr>
  </tbody>
</table>
</div>



Let's break down how we got `df_m`.

`df['diagnosis'] == 'M'` returns a Pandas Series of booleans indicating whether the value in the `diagnosis` columns is equal to `M`.


```python
mask = df['diagnosis'] == 'M'
print(mask)
```

    0       True
    1       True
    2       True
    3       True
    4       True
    5       True
    6       True
    7       True
    8       True
    9       True
    10      True
    11      True
    12      True
    13      True
    14      True
    15      True
    16      True
    17      True
    18      True
    19     False
    20     False
    21     False
    22      True
    23      True
    24      True
    25      True
    26      True
    27      True
    28      True
    29      True
           ...  
    534    False
    535    False
    536    False
    537    False
    538    False
    539    False
    540    False
    541    False
    542    False
    543    False
    544    False
    545    False
    546    False
    547    False
    548    False
    549    False
    550    False
    551    False
    552    False
    553    False
    554    False
    555    False
    556    False
    557     True
    558     True
    559     True
    560     True
    561     True
    562     True
    563    False
    Name: diagnosis, Length: 564, dtype: bool
    

And indexing the dataframe with this mask will return all rows where the value in `mask` is True (ie. where `diagnosis == 'M'`).


```python
df_m = df[mask]
df_m
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
      <th>diagnosis</th>
      <th>radius</th>
      <th>texture</th>
      <th>perimeter</th>
      <th>area</th>
      <th>smoothness</th>
      <th>compactness</th>
      <th>concavity</th>
      <th>concave_points</th>
      <th>symmetry</th>
      <th>fractal_dimension</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>842302</td>
      <td>M</td>
      <td>17.99</td>
      <td>19.293431</td>
      <td>122.80</td>
      <td>1001.0</td>
      <td>0.118400</td>
      <td>0.27760</td>
      <td>0.30010</td>
      <td>0.14710</td>
      <td>0.241900</td>
      <td>0.07871</td>
    </tr>
    <tr>
      <th>1</th>
      <td>842517</td>
      <td>M</td>
      <td>20.57</td>
      <td>17.770000</td>
      <td>132.90</td>
      <td>1326.0</td>
      <td>0.084740</td>
      <td>0.07864</td>
      <td>0.08690</td>
      <td>0.07017</td>
      <td>0.181200</td>
      <td>0.05667</td>
    </tr>
    <tr>
      <th>2</th>
      <td>84300903</td>
      <td>M</td>
      <td>19.69</td>
      <td>21.250000</td>
      <td>130.00</td>
      <td>1203.0</td>
      <td>0.109600</td>
      <td>0.15990</td>
      <td>0.19740</td>
      <td>0.12790</td>
      <td>0.206900</td>
      <td>0.05999</td>
    </tr>
    <tr>
      <th>3</th>
      <td>84348301</td>
      <td>M</td>
      <td>11.42</td>
      <td>20.380000</td>
      <td>77.58</td>
      <td>386.1</td>
      <td>0.096087</td>
      <td>0.28390</td>
      <td>0.24140</td>
      <td>0.10520</td>
      <td>0.259700</td>
      <td>0.09744</td>
    </tr>
    <tr>
      <th>4</th>
      <td>84358402</td>
      <td>M</td>
      <td>20.29</td>
      <td>14.340000</td>
      <td>135.10</td>
      <td>1297.0</td>
      <td>0.100300</td>
      <td>0.13280</td>
      <td>0.19800</td>
      <td>0.10430</td>
      <td>0.180900</td>
      <td>0.05883</td>
    </tr>
    <tr>
      <th>5</th>
      <td>843786</td>
      <td>M</td>
      <td>12.45</td>
      <td>15.700000</td>
      <td>82.57</td>
      <td>477.1</td>
      <td>0.127800</td>
      <td>0.17000</td>
      <td>0.15780</td>
      <td>0.08089</td>
      <td>0.208700</td>
      <td>0.07613</td>
    </tr>
    <tr>
      <th>6</th>
      <td>844359</td>
      <td>M</td>
      <td>18.25</td>
      <td>19.980000</td>
      <td>119.60</td>
      <td>1040.0</td>
      <td>0.094630</td>
      <td>0.10900</td>
      <td>0.11270</td>
      <td>0.07400</td>
      <td>0.181091</td>
      <td>0.05742</td>
    </tr>
    <tr>
      <th>7</th>
      <td>84458202</td>
      <td>M</td>
      <td>13.71</td>
      <td>20.830000</td>
      <td>90.20</td>
      <td>577.9</td>
      <td>0.118900</td>
      <td>0.16450</td>
      <td>0.09366</td>
      <td>0.05985</td>
      <td>0.219600</td>
      <td>0.07451</td>
    </tr>
    <tr>
      <th>8</th>
      <td>844981</td>
      <td>M</td>
      <td>13.00</td>
      <td>21.820000</td>
      <td>87.50</td>
      <td>519.8</td>
      <td>0.127300</td>
      <td>0.19320</td>
      <td>0.18590</td>
      <td>0.09353</td>
      <td>0.235000</td>
      <td>0.07389</td>
    </tr>
    <tr>
      <th>9</th>
      <td>84501001</td>
      <td>M</td>
      <td>12.46</td>
      <td>24.040000</td>
      <td>83.97</td>
      <td>475.9</td>
      <td>0.118600</td>
      <td>0.23960</td>
      <td>0.22730</td>
      <td>0.08543</td>
      <td>0.203000</td>
      <td>0.08243</td>
    </tr>
    <tr>
      <th>10</th>
      <td>845636</td>
      <td>M</td>
      <td>16.02</td>
      <td>23.240000</td>
      <td>102.70</td>
      <td>797.8</td>
      <td>0.082060</td>
      <td>0.06669</td>
      <td>0.03299</td>
      <td>0.03323</td>
      <td>0.152800</td>
      <td>0.05697</td>
    </tr>
    <tr>
      <th>11</th>
      <td>84610002</td>
      <td>M</td>
      <td>15.78</td>
      <td>17.890000</td>
      <td>103.60</td>
      <td>781.0</td>
      <td>0.097100</td>
      <td>0.12920</td>
      <td>0.09954</td>
      <td>0.06606</td>
      <td>0.184200</td>
      <td>0.06082</td>
    </tr>
    <tr>
      <th>12</th>
      <td>846226</td>
      <td>M</td>
      <td>19.17</td>
      <td>24.800000</td>
      <td>132.40</td>
      <td>1123.0</td>
      <td>0.097400</td>
      <td>0.24580</td>
      <td>0.20650</td>
      <td>0.11180</td>
      <td>0.239700</td>
      <td>0.07800</td>
    </tr>
    <tr>
      <th>13</th>
      <td>846381</td>
      <td>M</td>
      <td>15.85</td>
      <td>19.293431</td>
      <td>103.70</td>
      <td>782.7</td>
      <td>0.084010</td>
      <td>0.10020</td>
      <td>0.09938</td>
      <td>0.05364</td>
      <td>0.184700</td>
      <td>0.05338</td>
    </tr>
    <tr>
      <th>14</th>
      <td>84667401</td>
      <td>M</td>
      <td>13.73</td>
      <td>22.610000</td>
      <td>93.60</td>
      <td>578.3</td>
      <td>0.113100</td>
      <td>0.22930</td>
      <td>0.21280</td>
      <td>0.08025</td>
      <td>0.206900</td>
      <td>0.07682</td>
    </tr>
    <tr>
      <th>15</th>
      <td>84799002</td>
      <td>M</td>
      <td>14.54</td>
      <td>27.540000</td>
      <td>96.73</td>
      <td>658.8</td>
      <td>0.113900</td>
      <td>0.15950</td>
      <td>0.16390</td>
      <td>0.07364</td>
      <td>0.181091</td>
      <td>0.07077</td>
    </tr>
    <tr>
      <th>16</th>
      <td>848406</td>
      <td>M</td>
      <td>14.68</td>
      <td>20.130000</td>
      <td>94.74</td>
      <td>684.5</td>
      <td>0.098670</td>
      <td>0.07200</td>
      <td>0.07395</td>
      <td>0.05259</td>
      <td>0.158600</td>
      <td>0.05922</td>
    </tr>
    <tr>
      <th>17</th>
      <td>84862001</td>
      <td>M</td>
      <td>16.13</td>
      <td>19.293431</td>
      <td>108.10</td>
      <td>798.8</td>
      <td>0.117000</td>
      <td>0.20220</td>
      <td>0.17220</td>
      <td>0.10280</td>
      <td>0.216400</td>
      <td>0.07356</td>
    </tr>
    <tr>
      <th>18</th>
      <td>849014</td>
      <td>M</td>
      <td>19.81</td>
      <td>22.150000</td>
      <td>130.00</td>
      <td>1260.0</td>
      <td>0.098310</td>
      <td>0.10270</td>
      <td>0.14790</td>
      <td>0.09498</td>
      <td>0.158200</td>
      <td>0.05395</td>
    </tr>
    <tr>
      <th>22</th>
      <td>8511133</td>
      <td>M</td>
      <td>15.34</td>
      <td>14.260000</td>
      <td>102.50</td>
      <td>704.4</td>
      <td>0.107300</td>
      <td>0.21350</td>
      <td>0.20770</td>
      <td>0.09756</td>
      <td>0.252100</td>
      <td>0.07032</td>
    </tr>
    <tr>
      <th>23</th>
      <td>851509</td>
      <td>M</td>
      <td>21.16</td>
      <td>23.040000</td>
      <td>137.20</td>
      <td>1404.0</td>
      <td>0.094280</td>
      <td>0.10220</td>
      <td>0.10970</td>
      <td>0.08632</td>
      <td>0.176900</td>
      <td>0.05278</td>
    </tr>
    <tr>
      <th>24</th>
      <td>852552</td>
      <td>M</td>
      <td>16.65</td>
      <td>21.380000</td>
      <td>110.00</td>
      <td>904.6</td>
      <td>0.112100</td>
      <td>0.14570</td>
      <td>0.15250</td>
      <td>0.09170</td>
      <td>0.199500</td>
      <td>0.06330</td>
    </tr>
    <tr>
      <th>25</th>
      <td>852631</td>
      <td>M</td>
      <td>17.14</td>
      <td>16.400000</td>
      <td>116.00</td>
      <td>912.7</td>
      <td>0.096087</td>
      <td>0.22760</td>
      <td>0.22290</td>
      <td>0.14010</td>
      <td>0.304000</td>
      <td>0.07413</td>
    </tr>
    <tr>
      <th>26</th>
      <td>852763</td>
      <td>M</td>
      <td>14.58</td>
      <td>21.530000</td>
      <td>97.41</td>
      <td>644.8</td>
      <td>0.105400</td>
      <td>0.18680</td>
      <td>0.14250</td>
      <td>0.08783</td>
      <td>0.225200</td>
      <td>0.06924</td>
    </tr>
    <tr>
      <th>27</th>
      <td>852781</td>
      <td>M</td>
      <td>18.61</td>
      <td>20.250000</td>
      <td>122.10</td>
      <td>1094.0</td>
      <td>0.094400</td>
      <td>0.10660</td>
      <td>0.14900</td>
      <td>0.07731</td>
      <td>0.169700</td>
      <td>0.05699</td>
    </tr>
    <tr>
      <th>28</th>
      <td>852973</td>
      <td>M</td>
      <td>15.30</td>
      <td>25.270000</td>
      <td>102.40</td>
      <td>732.4</td>
      <td>0.108200</td>
      <td>0.16970</td>
      <td>0.16830</td>
      <td>0.08751</td>
      <td>0.192600</td>
      <td>0.06540</td>
    </tr>
    <tr>
      <th>29</th>
      <td>853201</td>
      <td>M</td>
      <td>17.57</td>
      <td>15.050000</td>
      <td>115.00</td>
      <td>955.1</td>
      <td>0.096087</td>
      <td>0.11570</td>
      <td>0.09875</td>
      <td>0.07953</td>
      <td>0.173900</td>
      <td>0.06149</td>
    </tr>
    <tr>
      <th>30</th>
      <td>853401</td>
      <td>M</td>
      <td>18.63</td>
      <td>25.110000</td>
      <td>124.80</td>
      <td>1088.0</td>
      <td>0.096087</td>
      <td>0.18870</td>
      <td>0.23190</td>
      <td>0.12440</td>
      <td>0.218300</td>
      <td>0.06197</td>
    </tr>
    <tr>
      <th>31</th>
      <td>853612</td>
      <td>M</td>
      <td>11.84</td>
      <td>18.700000</td>
      <td>77.93</td>
      <td>440.6</td>
      <td>0.110900</td>
      <td>0.15160</td>
      <td>0.12180</td>
      <td>0.05182</td>
      <td>0.230100</td>
      <td>0.07799</td>
    </tr>
    <tr>
      <th>32</th>
      <td>85382601</td>
      <td>M</td>
      <td>17.02</td>
      <td>19.293431</td>
      <td>112.80</td>
      <td>899.3</td>
      <td>0.119700</td>
      <td>0.14960</td>
      <td>0.24170</td>
      <td>0.12030</td>
      <td>0.224800</td>
      <td>0.06382</td>
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
    </tr>
    <tr>
      <th>438</th>
      <td>909445</td>
      <td>M</td>
      <td>17.27</td>
      <td>25.420000</td>
      <td>112.40</td>
      <td>928.8</td>
      <td>0.083310</td>
      <td>0.11090</td>
      <td>0.12040</td>
      <td>0.05736</td>
      <td>0.146700</td>
      <td>0.05407</td>
    </tr>
    <tr>
      <th>441</th>
      <td>9110127</td>
      <td>M</td>
      <td>18.03</td>
      <td>16.850000</td>
      <td>117.50</td>
      <td>990.0</td>
      <td>0.089470</td>
      <td>0.12320</td>
      <td>0.10900</td>
      <td>0.06254</td>
      <td>0.172000</td>
      <td>0.05780</td>
    </tr>
    <tr>
      <th>443</th>
      <td>9110732</td>
      <td>M</td>
      <td>17.75</td>
      <td>28.030000</td>
      <td>117.30</td>
      <td>981.6</td>
      <td>0.099970</td>
      <td>0.13140</td>
      <td>0.16980</td>
      <td>0.08293</td>
      <td>0.171300</td>
      <td>0.05916</td>
    </tr>
    <tr>
      <th>446</th>
      <td>911157302</td>
      <td>M</td>
      <td>21.10</td>
      <td>20.520000</td>
      <td>138.10</td>
      <td>1384.0</td>
      <td>0.096840</td>
      <td>0.11750</td>
      <td>0.15720</td>
      <td>0.11550</td>
      <td>0.155400</td>
      <td>0.05661</td>
    </tr>
    <tr>
      <th>448</th>
      <td>9111805</td>
      <td>M</td>
      <td>19.59</td>
      <td>25.000000</td>
      <td>127.70</td>
      <td>1191.0</td>
      <td>0.103200</td>
      <td>0.09871</td>
      <td>0.16550</td>
      <td>0.09063</td>
      <td>0.166300</td>
      <td>0.05391</td>
    </tr>
    <tr>
      <th>457</th>
      <td>911296201</td>
      <td>M</td>
      <td>17.08</td>
      <td>27.150000</td>
      <td>111.20</td>
      <td>930.9</td>
      <td>0.098980</td>
      <td>0.11100</td>
      <td>0.10070</td>
      <td>0.06431</td>
      <td>0.179300</td>
      <td>0.06281</td>
    </tr>
    <tr>
      <th>458</th>
      <td>911296202</td>
      <td>M</td>
      <td>27.42</td>
      <td>26.270000</td>
      <td>186.90</td>
      <td>2501.0</td>
      <td>0.108400</td>
      <td>0.19880</td>
      <td>0.36350</td>
      <td>0.16890</td>
      <td>0.206100</td>
      <td>0.05623</td>
    </tr>
    <tr>
      <th>465</th>
      <td>9113538</td>
      <td>M</td>
      <td>17.60</td>
      <td>23.330000</td>
      <td>119.00</td>
      <td>980.5</td>
      <td>0.092890</td>
      <td>0.20040</td>
      <td>0.21360</td>
      <td>0.10020</td>
      <td>0.169600</td>
      <td>0.07369</td>
    </tr>
    <tr>
      <th>476</th>
      <td>911916</td>
      <td>M</td>
      <td>16.25</td>
      <td>19.510000</td>
      <td>109.80</td>
      <td>815.8</td>
      <td>0.102600</td>
      <td>0.18930</td>
      <td>0.22360</td>
      <td>0.09194</td>
      <td>0.215100</td>
      <td>0.06578</td>
    </tr>
    <tr>
      <th>484</th>
      <td>913505</td>
      <td>M</td>
      <td>19.44</td>
      <td>18.820000</td>
      <td>128.10</td>
      <td>1167.0</td>
      <td>0.108900</td>
      <td>0.14480</td>
      <td>0.22560</td>
      <td>0.11940</td>
      <td>0.182300</td>
      <td>0.06115</td>
    </tr>
    <tr>
      <th>488</th>
      <td>914062</td>
      <td>M</td>
      <td>18.01</td>
      <td>20.560000</td>
      <td>118.40</td>
      <td>1007.0</td>
      <td>0.100100</td>
      <td>0.12890</td>
      <td>0.11700</td>
      <td>0.07762</td>
      <td>0.211600</td>
      <td>0.06077</td>
    </tr>
    <tr>
      <th>494</th>
      <td>914769</td>
      <td>M</td>
      <td>18.49</td>
      <td>17.520000</td>
      <td>121.30</td>
      <td>1068.0</td>
      <td>0.101200</td>
      <td>0.13170</td>
      <td>0.14910</td>
      <td>0.09183</td>
      <td>0.183200</td>
      <td>0.06697</td>
    </tr>
    <tr>
      <th>495</th>
      <td>91485</td>
      <td>M</td>
      <td>20.59</td>
      <td>21.240000</td>
      <td>137.80</td>
      <td>1320.0</td>
      <td>0.096087</td>
      <td>0.16440</td>
      <td>0.21880</td>
      <td>0.11210</td>
      <td>0.184800</td>
      <td>0.06222</td>
    </tr>
    <tr>
      <th>497</th>
      <td>91504</td>
      <td>M</td>
      <td>13.82</td>
      <td>24.490000</td>
      <td>92.33</td>
      <td>595.9</td>
      <td>0.116200</td>
      <td>0.16810</td>
      <td>0.13570</td>
      <td>0.06759</td>
      <td>0.227500</td>
      <td>0.07237</td>
    </tr>
    <tr>
      <th>499</th>
      <td>915143</td>
      <td>M</td>
      <td>23.09</td>
      <td>19.830000</td>
      <td>152.10</td>
      <td>1682.0</td>
      <td>0.093420</td>
      <td>0.12750</td>
      <td>0.16760</td>
      <td>0.10030</td>
      <td>0.150500</td>
      <td>0.05484</td>
    </tr>
    <tr>
      <th>505</th>
      <td>915460</td>
      <td>M</td>
      <td>15.46</td>
      <td>23.950000</td>
      <td>103.80</td>
      <td>731.3</td>
      <td>0.118300</td>
      <td>0.18700</td>
      <td>0.20300</td>
      <td>0.08520</td>
      <td>0.180700</td>
      <td>0.07083</td>
    </tr>
    <tr>
      <th>508</th>
      <td>915691</td>
      <td>M</td>
      <td>13.40</td>
      <td>20.520000</td>
      <td>88.64</td>
      <td>556.7</td>
      <td>0.110600</td>
      <td>0.14690</td>
      <td>0.14450</td>
      <td>0.08172</td>
      <td>0.211600</td>
      <td>0.07325</td>
    </tr>
    <tr>
      <th>510</th>
      <td>91594602</td>
      <td>M</td>
      <td>15.05</td>
      <td>19.070000</td>
      <td>97.26</td>
      <td>701.9</td>
      <td>0.092150</td>
      <td>0.08597</td>
      <td>0.07486</td>
      <td>0.04335</td>
      <td>0.156100</td>
      <td>0.05915</td>
    </tr>
    <tr>
      <th>512</th>
      <td>916799</td>
      <td>M</td>
      <td>18.31</td>
      <td>20.580000</td>
      <td>120.80</td>
      <td>1052.0</td>
      <td>0.106800</td>
      <td>0.12480</td>
      <td>0.15690</td>
      <td>0.09451</td>
      <td>0.186000</td>
      <td>0.05941</td>
    </tr>
    <tr>
      <th>513</th>
      <td>916838</td>
      <td>M</td>
      <td>19.89</td>
      <td>20.260000</td>
      <td>130.50</td>
      <td>1214.0</td>
      <td>0.103700</td>
      <td>0.13100</td>
      <td>0.14110</td>
      <td>0.09431</td>
      <td>0.180200</td>
      <td>0.06188</td>
    </tr>
    <tr>
      <th>517</th>
      <td>91762702</td>
      <td>M</td>
      <td>24.63</td>
      <td>21.600000</td>
      <td>165.50</td>
      <td>1841.0</td>
      <td>0.103000</td>
      <td>0.21060</td>
      <td>0.23100</td>
      <td>0.14710</td>
      <td>0.199100</td>
      <td>0.06739</td>
    </tr>
    <tr>
      <th>529</th>
      <td>91930402</td>
      <td>M</td>
      <td>20.47</td>
      <td>20.670000</td>
      <td>134.70</td>
      <td>1299.0</td>
      <td>0.096087</td>
      <td>0.13130</td>
      <td>0.15230</td>
      <td>0.10150</td>
      <td>0.216600</td>
      <td>0.05419</td>
    </tr>
    <tr>
      <th>531</th>
      <td>919555</td>
      <td>M</td>
      <td>20.55</td>
      <td>20.860000</td>
      <td>137.80</td>
      <td>1308.0</td>
      <td>0.104600</td>
      <td>0.17390</td>
      <td>0.20850</td>
      <td>0.13220</td>
      <td>0.212700</td>
      <td>0.06251</td>
    </tr>
    <tr>
      <th>532</th>
      <td>91979701</td>
      <td>M</td>
      <td>14.27</td>
      <td>22.550000</td>
      <td>93.77</td>
      <td>629.8</td>
      <td>0.103800</td>
      <td>0.11540</td>
      <td>0.14630</td>
      <td>0.06139</td>
      <td>0.192600</td>
      <td>0.05982</td>
    </tr>
    <tr>
      <th>557</th>
      <td>925622</td>
      <td>M</td>
      <td>15.22</td>
      <td>30.620000</td>
      <td>103.40</td>
      <td>716.9</td>
      <td>0.104800</td>
      <td>0.20870</td>
      <td>0.25500</td>
      <td>0.09429</td>
      <td>0.181091</td>
      <td>0.07152</td>
    </tr>
    <tr>
      <th>558</th>
      <td>926125</td>
      <td>M</td>
      <td>20.92</td>
      <td>25.090000</td>
      <td>143.00</td>
      <td>1347.0</td>
      <td>0.109900</td>
      <td>0.22360</td>
      <td>0.31740</td>
      <td>0.14740</td>
      <td>0.214900</td>
      <td>0.06879</td>
    </tr>
    <tr>
      <th>559</th>
      <td>926424</td>
      <td>M</td>
      <td>21.56</td>
      <td>22.390000</td>
      <td>142.00</td>
      <td>1479.0</td>
      <td>0.111000</td>
      <td>0.11590</td>
      <td>0.24390</td>
      <td>0.13890</td>
      <td>0.172600</td>
      <td>0.05623</td>
    </tr>
    <tr>
      <th>560</th>
      <td>926682</td>
      <td>M</td>
      <td>20.13</td>
      <td>28.250000</td>
      <td>131.20</td>
      <td>1261.0</td>
      <td>0.097800</td>
      <td>0.10340</td>
      <td>0.14400</td>
      <td>0.09791</td>
      <td>0.175200</td>
      <td>0.05533</td>
    </tr>
    <tr>
      <th>561</th>
      <td>926954</td>
      <td>M</td>
      <td>16.60</td>
      <td>28.080000</td>
      <td>108.30</td>
      <td>858.1</td>
      <td>0.084550</td>
      <td>0.10230</td>
      <td>0.09251</td>
      <td>0.05302</td>
      <td>0.159000</td>
      <td>0.05648</td>
    </tr>
    <tr>
      <th>562</th>
      <td>927241</td>
      <td>M</td>
      <td>20.60</td>
      <td>29.330000</td>
      <td>140.10</td>
      <td>1265.0</td>
      <td>0.117800</td>
      <td>0.27700</td>
      <td>0.35140</td>
      <td>0.15200</td>
      <td>0.239700</td>
      <td>0.07016</td>
    </tr>
  </tbody>
</table>
<p>210 rows × 12 columns</p>
</div>



Now that we have all the malignant tumors together in a dataframe, let's see summary statistics about the `area` feature, which offers a good metric for size.


```python
# Display summary statistics for area of malignant tumors
df_m['area'].describe()
```




    count     210.000000
    mean      976.582857
    std       365.494289
    min       361.600000
    25%       706.850000
    50%       932.000000
    75%      1200.750000
    max      2501.000000
    Name: area, dtype: float64



Let's do the same for all the benign tumors.


```python
# Create new dataframe with only benign tumors
df_b = df[df['diagnosis'] == 'B']

# Display summary statistics for area of benign tumors
df_b['area'].describe()
```




    count    354.000000
    mean     462.712429
    std      134.769158
    min      143.500000
    25%      374.975000
    50%      458.150000
    75%      551.550000
    max      992.100000
    Name: area, dtype: float64




```python
print('The mean area of malignant tumors is {0:.4f} while that of benign \
tumors is {1:.4f}.'.format(df_m['area'].mean(), df_b['area'].mean()))
```

    The mean area of malignant tumors is 976.5829 while that of benign tumors is 462.7124.
    

Although summary statistics like the mean are helpful, it would be nice to be able to compare the distributions of the areas of malignant and benign tumors visually. Let's see a simple example of using matplotlib to create histograms for both distributions on the same plot.

(We'll learn how to use matplotlib in the next lesson.)


```python
import matplotlib.pyplot as plt
%matplotlib inline

# Plot histogram of benign and malignant tumor areas on the same axes
fig, ax = plt.subplots(figsize=(8, 6))
ax.hist(df_b['area'], alpha=0.5, label='benign')
ax.hist(df_m['area'], alpha=0.5, label='malignant')
ax.set_title('Distributions of Benign and Malignant Tumor Areas')
ax.set_xlabel('Area')
ax.set_ylabel('Count')
ax.legend(loc='upper right')
plt.show()
```


![conclusion](images/output_14_0.png)


The visual above suggests that there is a difference between the distribution of areas for benign and malignant tumors. We don't yet have the tools to conclude that these distributions are different or whether the size definitely affects a tumor's malignancy. However, we can observe from summary statistics and these histograms that malignant tumors are generally larger in size than benign tumors.
