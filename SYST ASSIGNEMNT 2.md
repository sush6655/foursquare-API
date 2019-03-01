

```python
import pandas as pd
from pandas import DataFrame

df = pd.read_csv('C:/Users/akula/Downloads/AirfaresData.csv')


print(df.describe())
```

               COUPON         NEW            HI      S_INCOME      E_INCOME  \
    count  638.000000  638.000000    638.000000    638.000000    638.000000   
    mean     1.202335    2.753918   4442.141129  27759.860502  27663.727273   
    std      0.203821    0.760448   1724.267051   3596.207837   4611.325018   
    min      1.000000    0.000000   1230.480000  14600.000000  14600.000000   
    25%      1.040000    3.000000   3090.137500  24706.000000  23903.000000   
    50%      1.150000    3.000000   4208.185000  28637.000000  26409.000000   
    75%      1.297500    3.000000   5480.575000  29693.500000  31981.000000   
    max      1.940000    3.000000  10000.000000  38813.000000  38813.000000   
    
                  S_POP         E_POP     DISTANCE           PAX        FARE  
    count  6.380000e+02  6.380000e+02   638.000000    638.000000  638.000000  
    mean   4.557004e+06  3.194503e+06   975.653605  12782.214734  160.876677  
    std    3.010985e+06  2.735604e+06   646.242403  13202.228860   76.022436  
    min    2.983800e+04  1.117450e+05   114.000000   1504.000000   42.470000  
    25%    1.862106e+06  1.228816e+06   455.000000   5328.500000  106.290000  
    50%    3.532657e+06  2.195215e+06   850.000000   7792.000000  144.600000  
    75%    7.830332e+06  4.549784e+06  1306.250000  14090.500000  209.350000  
    max    9.056076e+06  9.056076e+06  2764.000000  73892.000000  402.020000  
    


```python
print(df.corr())
```

                COUPON       NEW        HI  S_INCOME  E_INCOME     S_POP  \
    COUPON    1.000000  0.020223 -0.347252 -0.088403  0.046889 -0.107763   
    NEW       0.020223  1.000000  0.054147  0.026597  0.113377 -0.016672   
    HI       -0.347252  0.054147  1.000000 -0.027382  0.082393 -0.172495   
    S_INCOME -0.088403  0.026597 -0.027382  1.000000 -0.138864  0.517187   
    E_INCOME  0.046889  0.113377  0.082393 -0.138864  1.000000 -0.144059   
    S_POP    -0.107763 -0.016672 -0.172495  0.517187 -0.144059  1.000000   
    E_POP     0.094970  0.058568 -0.062456 -0.272280  0.458418 -0.280143   
    DISTANCE  0.746805  0.080965 -0.312375  0.028153  0.176531  0.018437   
    PAX      -0.336974  0.010495 -0.168961  0.138197  0.259961  0.284611   
    FARE      0.496537  0.091730  0.025195  0.209135  0.326092  0.145097   
    
                 E_POP  DISTANCE       PAX      FARE  
    COUPON    0.094970  0.746805 -0.336974  0.496537  
    NEW       0.058568  0.080965  0.010495  0.091730  
    HI       -0.062456 -0.312375 -0.168961  0.025195  
    S_INCOME -0.272280  0.028153  0.138197  0.209135  
    E_INCOME  0.458418  0.176531  0.259961  0.326092  
    S_POP    -0.280143  0.018437  0.284611  0.145097  
    E_POP     1.000000  0.115640  0.314698  0.285043  
    DISTANCE  0.115640  1.000000 -0.102482  0.670016  
    PAX       0.314698 -0.102482  1.000000 -0.090705  
    FARE      0.285043  0.670016 -0.090705  1.000000  
    


```python
ds=list(df.corr())
ds
```




    ['COUPON',
     'NEW',
     'HI',
     'S_INCOME',
     'E_INCOME',
     'S_POP',
     'E_POP',
     'DISTANCE',
     'PAX',
     'FARE']




```python
df.corr()['FARE'].sort_values(ascending=False)

```




    FARE        1.000000
    DISTANCE    0.670016
    COUPON      0.496537
    E_INCOME    0.326092
    E_POP       0.285043
    S_INCOME    0.209135
    S_POP       0.145097
    NEW         0.091730
    HI          0.025195
    PAX        -0.090705
    Name: FARE, dtype: float64




```python
from pandas.plotting import scatter_matrix
scatter_matrix(df, figsize=(20,8))
```




    array([[<matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C36B8AC8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C36D92B0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3701518>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C372A780>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C37539E8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C377BC50>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C37A7EB8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C37D7160>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C37D7198>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3BF95F8>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3C20860>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3C49AC8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3C74D30>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3C9EF98>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3CCE240>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3CF74A8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3D1F710>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3D49978>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3D70BE0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3D9BE48>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3DCD0F0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3DF5358>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3E1E5C0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3E47828>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3E6FA90>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3E9CCF8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3EC4F60>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3EF5208>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3F1E470>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3F476D8>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3F6F940>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3F9ABA8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3FC4E10>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C3FF40B8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C401D320>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C4045588>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C406E7F0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C4096A58>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C40C1CC0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C40ECF28>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C411C358>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C41428D0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C416BE48>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C419A400>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C41C1978>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C41EBEF0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C421A4A8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C4242A20>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C4268F98>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C4298550>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C42BFAC8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C42F1080>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C43185F8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C433FB70>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C4371128>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C43986A0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C43C2C18>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C53C21D0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C53EA748>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5412CC0>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5444278>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C546B7F0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5493D68>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C54C4320>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C54EA898>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5514E10>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C55463C8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C556D940>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5596EB8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C55C7470>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C55EE9E8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5615F60>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5647518>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C566EA90>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C56A1048>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C56CA5C0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C56F0B38>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C57210F0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C574A668>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5770BE0>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C57A2198>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C57CA710>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C57F2C88>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5823240>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C584B7B8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5873D30>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C58A32E8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C58C9860>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C58F5DD8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5926390>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C594B908>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5976E80>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C59A5438>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C59CD9B0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C59F8F28>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5A274E0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5A4FA58>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5A78FD0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5AA7588>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000001D7C5ACEB00>]],
          dtype=object)




![png](output_4_1.png)


## We can infer from the above table that the value of distance has the highest correlation value of about 0.670016 while compared to other attributes in a numerical predictors. Also from the graphs the distance has points that are nearer forming a linear correlation with the fare attribute which becomes easy and better value for prediction.


```python
import random
random.seed(12345)
```


```python
df['DISTANCE'].value_counts()
```




    217     6
    723     6
    760     6
    291     6
    254     5
    539     5
    842     5
    325     5
    1103    4
    756     4
    591     4
    492     4
    457     4
    854     4
    225     3
    657     3
    183     3
    181     3
    2411    3
    673     3
    1173    3
    147     3
    1851    3
    1624    3
    2148    3
    1749    3
    736     3
    199     3
    1822    3
    2237    3
           ..
    586     1
    587     1
    590     1
    600     1
    602     1
    606     1
    614     1
    615     1
    616     1
    617     1
    1589    1
    2605    1
    1532    1
    556     1
    1539    1
    1545    1
    702     1
    2576    1
    530     1
    2579    1
    593     1
    1559    1
    542     1
    543     1
    1568    1
    546     1
    548     1
    550     1
    2603    1
    1026    1
    Name: DISTANCE, Length: 400, dtype: int64




```python
df['COUPON'].value_counts()
```




    1.00    65
    1.01    38
    1.02    35
    1.06    25
    1.05    20
    1.15    19
    1.08    19
    1.16    18
    1.04    17
    1.36    16
    1.29    16
    1.12    15
    1.10    14
    1.17    13
    1.19    13
    1.34    13
    1.07    13
    1.09    13
    1.27    12
    1.14    12
    1.11    11
    1.13    11
    1.24    10
    1.25    10
    1.22     9
    1.20     9
    1.03     9
    1.42     9
    1.28     9
    1.26     9
            ..
    1.68     3
    1.69     3
    1.64     3
    1.46     3
    1.77     3
    1.44     3
    1.58     2
    1.50     2
    1.89     2
    1.60     2
    1.43     2
    1.45     2
    1.47     2
    1.49     2
    1.59     1
    1.63     1
    1.71     1
    1.88     1
    1.67     1
    1.32     1
    1.66     1
    1.94     1
    1.70     1
    1.87     1
    1.53     1
    1.86     1
    1.38     1
    1.48     1
    1.61     1
    1.93     1
    Name: COUPON, Length: 77, dtype: int64




```python
df['DISTANCE'].value_counts().sort_index()
```




    114     2
    135     1
    138     1
    147     3
    167     2
    174     1
    177     1
    180     2
    181     3
    183     3
    184     2
    187     1
    188     1
    192     2
    194     1
    199     3
    217     6
    225     3
    226     1
    227     1
    234     1
    237     2
    238     2
    239     1
    241     1
    242     1
    244     1
    248     1
    254     5
    257     2
           ..
    2290    1
    2295    1
    2300    2
    2317    2
    2329    1
    2336    1
    2341    1
    2372    1
    2401    1
    2407    1
    2411    3
    2428    2
    2433    3
    2443    1
    2444    3
    2454    1
    2467    3
    2489    1
    2523    1
    2553    1
    2555    1
    2574    3
    2576    1
    2579    1
    2603    1
    2605    1
    2679    1
    2682    1
    2694    1
    2764    1
    Name: DISTANCE, Length: 400, dtype: int64




```python
df.describe()
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
      <th>COUPON</th>
      <th>NEW</th>
      <th>HI</th>
      <th>S_INCOME</th>
      <th>E_INCOME</th>
      <th>S_POP</th>
      <th>E_POP</th>
      <th>DISTANCE</th>
      <th>PAX</th>
      <th>FARE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>638.000000</td>
      <td>638.000000</td>
      <td>638.000000</td>
      <td>638.000000</td>
      <td>638.000000</td>
      <td>6.380000e+02</td>
      <td>6.380000e+02</td>
      <td>638.000000</td>
      <td>638.000000</td>
      <td>638.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>1.202335</td>
      <td>2.753918</td>
      <td>4442.141129</td>
      <td>27759.860502</td>
      <td>27663.727273</td>
      <td>4.557004e+06</td>
      <td>3.194503e+06</td>
      <td>975.653605</td>
      <td>12782.214734</td>
      <td>160.876677</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.203821</td>
      <td>0.760448</td>
      <td>1724.267051</td>
      <td>3596.207837</td>
      <td>4611.325018</td>
      <td>3.010985e+06</td>
      <td>2.735604e+06</td>
      <td>646.242403</td>
      <td>13202.228860</td>
      <td>76.022436</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>1230.480000</td>
      <td>14600.000000</td>
      <td>14600.000000</td>
      <td>2.983800e+04</td>
      <td>1.117450e+05</td>
      <td>114.000000</td>
      <td>1504.000000</td>
      <td>42.470000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1.040000</td>
      <td>3.000000</td>
      <td>3090.137500</td>
      <td>24706.000000</td>
      <td>23903.000000</td>
      <td>1.862106e+06</td>
      <td>1.228816e+06</td>
      <td>455.000000</td>
      <td>5328.500000</td>
      <td>106.290000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1.150000</td>
      <td>3.000000</td>
      <td>4208.185000</td>
      <td>28637.000000</td>
      <td>26409.000000</td>
      <td>3.532657e+06</td>
      <td>2.195215e+06</td>
      <td>850.000000</td>
      <td>7792.000000</td>
      <td>144.600000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>1.297500</td>
      <td>3.000000</td>
      <td>5480.575000</td>
      <td>29693.500000</td>
      <td>31981.000000</td>
      <td>7.830332e+06</td>
      <td>4.549784e+06</td>
      <td>1306.250000</td>
      <td>14090.500000</td>
      <td>209.350000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.940000</td>
      <td>3.000000</td>
      <td>10000.000000</td>
      <td>38813.000000</td>
      <td>38813.000000</td>
      <td>9.056076e+06</td>
      <td>9.056076e+06</td>
      <td>2764.000000</td>
      <td>73892.000000</td>
      <td>402.020000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.drop(df.columns[[0,1,2,3]],axis=1,inplace=True)
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 638 entries, 0 to 637
    Data columns (total 14 columns):
    COUPON      638 non-null float64
    NEW         638 non-null int64
    VACATION    638 non-null object
    SW          638 non-null object
    HI          638 non-null float64
    S_INCOME    638 non-null float64
    E_INCOME    638 non-null float64
    S_POP       638 non-null int64
    E_POP       638 non-null int64
    SLOT        638 non-null object
    GATE        638 non-null object
    DISTANCE    638 non-null int64
    PAX         638 non-null int64
    FARE        638 non-null float64
    dtypes: float64(5), int64(5), object(4)
    memory usage: 69.9+ KB
    


```python
df1=df.select_dtypes(include=[object])
```


```python
df1
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
      <th>VACATION</th>
      <th>SW</th>
      <th>SLOT</th>
      <th>GATE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>1</th>
      <td>No</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>2</th>
      <td>No</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>3</th>
      <td>No</td>
      <td>Yes</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>4</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>5</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>6</th>
      <td>No</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Yes</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>8</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>9</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Yes</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>11</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>12</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>13</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>14</th>
      <td>No</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>15</th>
      <td>No</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>16</th>
      <td>No</td>
      <td>No</td>
      <td>Free</td>
      <td>Constrained</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Yes</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>18</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>19</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>20</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>21</th>
      <td>No</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>22</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Yes</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>24</th>
      <td>No</td>
      <td>Yes</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>25</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>26</th>
      <td>No</td>
      <td>Yes</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>27</th>
      <td>No</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>28</th>
      <td>No</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>29</th>
      <td>No</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>608</th>
      <td>No</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>609</th>
      <td>No</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>610</th>
      <td>No</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>611</th>
      <td>No</td>
      <td>No</td>
      <td>Free</td>
      <td>Constrained</td>
    </tr>
    <tr>
      <th>612</th>
      <td>No</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Constrained</td>
    </tr>
    <tr>
      <th>613</th>
      <td>Yes</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>614</th>
      <td>Yes</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>615</th>
      <td>No</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>616</th>
      <td>No</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>617</th>
      <td>No</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>618</th>
      <td>No</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>619</th>
      <td>No</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>620</th>
      <td>No</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>621</th>
      <td>No</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>622</th>
      <td>No</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>623</th>
      <td>No</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>624</th>
      <td>No</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>625</th>
      <td>Yes</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>626</th>
      <td>Yes</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>627</th>
      <td>Yes</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>628</th>
      <td>Yes</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>629</th>
      <td>Yes</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>630</th>
      <td>Yes</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>631</th>
      <td>Yes</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>632</th>
      <td>Yes</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>633</th>
      <td>Yes</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>634</th>
      <td>Yes</td>
      <td>No</td>
      <td>Free</td>
      <td>Constrained</td>
    </tr>
    <tr>
      <th>635</th>
      <td>Yes</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>636</th>
      <td>Yes</td>
      <td>No</td>
      <td>Free</td>
      <td>Free</td>
    </tr>
    <tr>
      <th>637</th>
      <td>Yes</td>
      <td>No</td>
      <td>Controlled</td>
      <td>Free</td>
    </tr>
  </tbody>
</table>
<p>638 rows × 4 columns</p>
</div>




```python
A1 = df['FARE'].groupby(df['VACATION']).mean()
A1
```




    VACATION
    No     173.552500
    Yes    125.980882
    Name: FARE, dtype: float64




```python
A2 = df['FARE'].groupby(df['SW']).mean()
A2
```




    SW
    No     188.182793
    Yes     98.382268
    Name: FARE, dtype: float64




```python
A3 = df['FARE'].groupby(df['SLOT']).mean()
A3
```




    SLOT
    Controlled    186.059396
    Free          150.825680
    Name: FARE, dtype: float64




```python
A4 = df['FARE'].groupby(df['GATE']).mean()
A4
```




    GATE
    Constrained    193.129032
    Free           153.095953
    Name: FARE, dtype: float64



## From the above lines of code the categorical data attributes are considered and are compared to obtain an attribute which is best predictor for the fare. The mean values for each attribute are calculated with respect to their factors in relation to fare values and we can see the the SW (south-west airlines) attribute has highest difference in mean with its factors of about 89.800525, which implies it is one of the best predictors for fare values in the categorical data.  


```python
y=df.corr()['FARE'].sort_values(ascending=False)
y
```




    FARE        1.000000
    DISTANCE    0.670016
    COUPON      0.496537
    E_INCOME    0.326092
    E_POP       0.285043
    S_INCOME    0.209135
    S_POP       0.145097
    NEW         0.091730
    HI          0.025195
    PAX        -0.090705
    Name: FARE, dtype: float64




```python
df.iloc[5]
```




    COUPON         1.01
    NEW               3
    VACATION         No
    SW              Yes
    HI          3408.11
    S_INCOME      26046
    E_INCOME      29838
    S_POP       2230955
    E_POP       7145897
    SLOT           Free
    GATE           Free
    DISTANCE        309
    PAX           13386
    FARE          56.76
    Name: 5, dtype: object




```python
cls=list(df.columns)
cls
```




    ['COUPON',
     'NEW',
     'VACATION',
     'SW',
     'HI',
     'S_INCOME',
     'E_INCOME',
     'S_POP',
     'E_POP',
     'SLOT',
     'GATE',
     'DISTANCE',
     'PAX',
     'FARE']




```python
df['SW']=df['SW'].replace("Yes",1)
```


```python
df['SW']=df['SW'].replace("No",0)
```


```python
df2 = df[['SW','DISTANCE']]
df2
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
      <th>SW</th>
      <th>DISTANCE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>312</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>576</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>364</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>612</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>612</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1</td>
      <td>309</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0</td>
      <td>1220</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1</td>
      <td>921</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1</td>
      <td>1249</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1</td>
      <td>964</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1</td>
      <td>2104</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1</td>
      <td>2329</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1</td>
      <td>587</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1</td>
      <td>992</td>
    </tr>
    <tr>
      <th>14</th>
      <td>0</td>
      <td>181</td>
    </tr>
    <tr>
      <th>15</th>
      <td>0</td>
      <td>181</td>
    </tr>
    <tr>
      <th>16</th>
      <td>0</td>
      <td>181</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1</td>
      <td>788</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1</td>
      <td>2001</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1</td>
      <td>1866</td>
    </tr>
    <tr>
      <th>20</th>
      <td>1</td>
      <td>2290</td>
    </tr>
    <tr>
      <th>21</th>
      <td>0</td>
      <td>2454</td>
    </tr>
    <tr>
      <th>22</th>
      <td>1</td>
      <td>729</td>
    </tr>
    <tr>
      <th>23</th>
      <td>1</td>
      <td>846</td>
    </tr>
    <tr>
      <th>24</th>
      <td>1</td>
      <td>576</td>
    </tr>
    <tr>
      <th>25</th>
      <td>1</td>
      <td>576</td>
    </tr>
    <tr>
      <th>26</th>
      <td>1</td>
      <td>403</td>
    </tr>
    <tr>
      <th>27</th>
      <td>0</td>
      <td>939</td>
    </tr>
    <tr>
      <th>28</th>
      <td>0</td>
      <td>291</td>
    </tr>
    <tr>
      <th>29</th>
      <td>0</td>
      <td>291</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>608</th>
      <td>0</td>
      <td>217</td>
    </tr>
    <tr>
      <th>609</th>
      <td>0</td>
      <td>217</td>
    </tr>
    <tr>
      <th>610</th>
      <td>0</td>
      <td>217</td>
    </tr>
    <tr>
      <th>611</th>
      <td>0</td>
      <td>217</td>
    </tr>
    <tr>
      <th>612</th>
      <td>0</td>
      <td>217</td>
    </tr>
    <tr>
      <th>613</th>
      <td>0</td>
      <td>760</td>
    </tr>
    <tr>
      <th>614</th>
      <td>0</td>
      <td>760</td>
    </tr>
    <tr>
      <th>615</th>
      <td>0</td>
      <td>1970</td>
    </tr>
    <tr>
      <th>616</th>
      <td>0</td>
      <td>1970</td>
    </tr>
    <tr>
      <th>617</th>
      <td>0</td>
      <td>2259</td>
    </tr>
    <tr>
      <th>618</th>
      <td>0</td>
      <td>2259</td>
    </tr>
    <tr>
      <th>619</th>
      <td>0</td>
      <td>2428</td>
    </tr>
    <tr>
      <th>620</th>
      <td>0</td>
      <td>2428</td>
    </tr>
    <tr>
      <th>621</th>
      <td>0</td>
      <td>2317</td>
    </tr>
    <tr>
      <th>622</th>
      <td>0</td>
      <td>2317</td>
    </tr>
    <tr>
      <th>623</th>
      <td>0</td>
      <td>699</td>
    </tr>
    <tr>
      <th>624</th>
      <td>0</td>
      <td>699</td>
    </tr>
    <tr>
      <th>625</th>
      <td>0</td>
      <td>815</td>
    </tr>
    <tr>
      <th>626</th>
      <td>0</td>
      <td>815</td>
    </tr>
    <tr>
      <th>627</th>
      <td>0</td>
      <td>546</td>
    </tr>
    <tr>
      <th>628</th>
      <td>0</td>
      <td>1193</td>
    </tr>
    <tr>
      <th>629</th>
      <td>0</td>
      <td>1134</td>
    </tr>
    <tr>
      <th>630</th>
      <td>0</td>
      <td>1134</td>
    </tr>
    <tr>
      <th>631</th>
      <td>0</td>
      <td>1125</td>
    </tr>
    <tr>
      <th>632</th>
      <td>0</td>
      <td>1030</td>
    </tr>
    <tr>
      <th>633</th>
      <td>0</td>
      <td>1030</td>
    </tr>
    <tr>
      <th>634</th>
      <td>0</td>
      <td>1030</td>
    </tr>
    <tr>
      <th>635</th>
      <td>0</td>
      <td>960</td>
    </tr>
    <tr>
      <th>636</th>
      <td>0</td>
      <td>858</td>
    </tr>
    <tr>
      <th>637</th>
      <td>0</td>
      <td>858</td>
    </tr>
  </tbody>
</table>
<p>638 rows × 2 columns</p>
</div>




```python
cls=list(df2.columns)
cls
```




    ['SW', 'DISTANCE']




```python
df['FARE']=df['FARE'].astype(int)
```


```python
df['FARE'].value_counts().sort_index()
```




    42     1
    44     1
    45     2
    46     1
    47     1
    49     2
    50     2
    51     2
    52     2
    53     3
    54     2
    55     3
    56     5
    57     6
    58     3
    59     2
    60     4
    62     2
    63     6
    64     3
    65     4
    66     3
    67     5
    68     4
    69     6
    70     4
    72     4
    73     1
    74     2
    75     4
          ..
    273    8
    278    3
    279    4
    281    2
    285    1
    286    1
    287    3
    289    3
    291    4
    293    1
    294    2
    295    2
    297    4
    299    3
    301    1
    302    3
    303    2
    304    3
    311    1
    314    1
    320    1
    325    1
    326    4
    335    1
    347    2
    349    4
    353    1
    367    1
    374    3
    402    1
    Name: FARE, Length: 210, dtype: int64




```python
sz = df.index.size
tr = df[:int(sz*0.60)]
ts = df[int(sz*0.40):]
```


```python
tr_inp=tr[cls]
tr_out=tr['FARE']
ts_inp=ts[cls]
ts_out=ts['FARE']
```


```python
from sklearn.linear_model import LogisticRegression

lr = LogisticRegression()
lr.fit(tr_inp, tr_out)
```

    C:\Users\akula\Anaconda3\lib\site-packages\sklearn\linear_model\logistic.py:433: FutureWarning: Default solver will be changed to 'lbfgs' in 0.22. Specify a solver to silence this warning.
      FutureWarning)
    C:\Users\akula\Anaconda3\lib\site-packages\sklearn\linear_model\logistic.py:460: FutureWarning: Default multi_class will be changed to 'auto' in 0.22. Specify the multi_class option to silence this warning.
      "this warning.", FutureWarning)
    




    LogisticRegression(C=1.0, class_weight=None, dual=False, fit_intercept=True,
              intercept_scaling=1, max_iter=100, multi_class='warn',
              n_jobs=None, penalty='l2', random_state=None, solver='warn',
              tol=0.0001, verbose=0, warm_start=False)




```python
probs=lr.predict_proba(ts_inp)[:,1]
probs
```




    array([4.69498297e-07, 4.27341263e-07, 4.27341263e-07, 4.27341263e-07,
           8.38502409e-05, 8.38502409e-05, 8.38502409e-05, 6.54460565e-09,
           6.54460565e-09, 6.54460565e-09, 6.46472636e-06, 6.46472636e-06,
           6.46472636e-06, 3.10912182e-07, 3.10912182e-07, 3.10912182e-07,
           2.96313529e-13, 2.96313529e-13, 2.96313529e-13, 1.64277203e-14,
           1.64277203e-14, 1.64277203e-14, 1.84170293e-06, 1.84170293e-06,
           1.84170293e-06, 3.33707568e-07, 3.33707568e-07, 3.33707568e-07,
           8.73930108e-07, 8.73930108e-07, 8.73930108e-07, 1.35795150e-07,
           1.35795150e-07, 1.35795150e-07, 2.22039701e-03, 2.22039701e-03,
           2.22039701e-03, 3.05152451e-03, 1.43790863e-03, 2.81959468e-03,
           9.14192898e-03, 1.39716810e-03, 1.17406721e-03, 1.17406721e-03,
           3.68950513e-04, 7.53108186e-04, 2.57401024e-07, 2.41670652e-06,
           2.41670652e-06, 1.71581829e-05, 3.24620445e-06, 2.19129106e-05,
           1.25484670e-06, 1.54452656e-09, 1.60215160e-06, 9.48041426e-03,
           6.15063276e-07, 1.19056186e-05, 1.08321901e-06, 3.69302822e-12,
           3.85480345e-13, 5.10646604e-03, 5.10646604e-03, 2.71099664e-08,
           3.74994602e-04, 1.92917559e-06, 1.92917559e-06, 1.92917559e-06,
           4.28884801e-05, 2.79934099e-03, 4.33659908e-05, 4.33659908e-05,
           2.52268404e-08, 1.16709037e-09, 4.72611322e-04, 1.07837858e-06,
           1.69693047e-08, 6.12505841e-13, 3.50027181e-14, 7.68415686e-07,
           1.33008535e-06, 4.58444812e-06, 2.99864584e-03, 8.81583082e-10,
           9.48403138e-06, 1.43153965e-13, 2.17172462e-03, 1.15850039e-08,
           1.15850039e-08, 2.91449104e-10, 7.38054964e-10, 4.69092529e-06,
           1.07660493e-04, 6.61271223e-10, 2.37879151e-03, 1.93883735e-06,
           1.33628791e-06, 5.72846274e-03, 2.11276328e-03, 3.83758600e-08,
           9.02433327e-13, 9.02433327e-13, 9.02433327e-13, 1.33904184e-04,
           1.59127280e-06, 8.33262124e-11, 2.03110020e-12, 2.16084226e-04,
           3.35992456e-04, 6.95105328e-04, 6.95105328e-04, 1.62219871e-03,
           1.62219871e-03, 1.62219871e-03, 1.62219871e-03, 7.33009905e-06,
           2.82394468e-03, 2.57959022e-03, 1.27185110e-10, 1.27185110e-10,
           1.14313633e-06, 2.94377500e-15, 3.50666030e-05, 1.58027337e-05,
           2.19572520e-14, 2.19572520e-14, 2.19572520e-14, 3.67263079e-04,
           2.25440799e-06, 6.66478761e-04, 1.41327281e-04, 4.94116951e-06,
           1.80358179e-04, 2.79664405e-04, 7.63255642e-03, 4.42223201e-03,
           1.57704597e-03, 6.46472636e-06, 6.46472636e-06, 7.05526499e-03,
           7.05526499e-03, 7.05526499e-03, 4.32398333e-07, 1.20726252e-03,
           9.04935950e-05, 6.52010751e-05, 6.52010751e-05, 4.86348714e-07,
           6.03581352e-04, 6.03581352e-04, 6.03581352e-04, 1.32913727e-03,
           3.93112154e-03, 3.93112154e-03, 2.96776486e-10, 2.96776486e-10,
           2.57959022e-03, 1.72191202e-03, 9.14192898e-03, 2.19232189e-04,
           1.00377157e-03, 6.46538582e-04, 8.69792175e-03, 2.79664405e-04,
           2.30212936e-03, 2.30212936e-03, 2.30212936e-03, 3.08003700e-03,
           3.08003700e-03, 3.08003700e-03, 2.46630304e-03, 1.73817053e-03,
           2.21182955e-03, 1.47551854e-04, 7.59767856e-04, 1.66071626e-04,
           9.14458495e-10, 1.08726420e-07, 1.08726420e-07, 8.82959080e-04,
           2.25258118e-03, 2.38664131e-04, 7.13753591e-12, 7.13753591e-12,
           7.13753591e-12, 2.33655956e-04, 6.02178677e-04, 4.42696780e-04,
           1.67862775e-04, 1.04217008e-04, 7.11936412e-05, 1.46678609e-06,
           1.46678609e-06, 5.99219667e-03, 9.31062349e-03, 9.63785328e-07,
           1.76896700e-07, 1.04579175e-09, 1.04579175e-09, 1.04579175e-09,
           1.57286852e-06, 2.34638209e-11, 4.14340122e-15, 3.95787538e-10,
           3.95787538e-10, 1.52902627e-07, 6.61419548e-06, 5.30675752e-03,
           8.68440441e-03, 8.68440441e-03, 1.80929538e-09, 2.52237809e-14,
           2.52237809e-14, 2.52237809e-14, 9.64930026e-04, 3.94152320e-03,
           9.00300116e-04, 1.18922764e-06, 1.03536546e-12, 9.28558126e-16,
           1.51860141e-03, 3.61689864e-11, 3.61689864e-11, 4.18192637e-09,
           1.65897903e-06, 2.00593649e-12, 1.14475204e-09, 2.66955587e-09,
           1.31882561e-03, 1.39418888e-03, 3.98903141e-15, 9.03366595e-10,
           4.24961210e-15, 4.24961210e-15, 4.24961210e-15, 2.22358850e-14,
           8.09945248e-15, 1.22808117e-04, 4.19488509e-05, 8.36520245e-09,
           1.08131721e-15, 3.90882275e-03, 4.29966234e-11, 4.29966234e-11,
           5.79905660e-09, 2.02075617e-06, 1.73817053e-03, 3.62413698e-03,
           1.73349200e-04, 1.28117838e-03, 6.66515555e-05, 6.37085046e-07,
           6.37085046e-07, 6.37085046e-07, 5.32806869e-09, 5.89947491e-13,
           1.24445425e-14, 4.40461067e-06, 1.58689816e-10, 1.58689816e-10,
           3.70022901e-10, 7.50635281e-07, 1.32735185e-11, 1.02705921e-05,
           3.74886902e-06, 8.74605903e-09, 3.32826348e-14, 3.32826348e-14,
           3.32826348e-14, 8.76614783e-05, 5.54285326e-15, 6.86340334e-07,
           6.78198336e-03, 3.80607563e-04, 5.34791741e-03, 5.34791741e-03,
           6.20826040e-04, 1.55290067e-04, 1.23657113e-05, 9.74507369e-04,
           8.29989225e-05, 5.90339976e-03, 2.59283071e-08, 1.75268221e-09,
           4.39813777e-04, 4.32858406e-06, 4.32858406e-06, 4.32858406e-06,
           1.02705921e-05, 9.31457887e-08, 4.83846618e-03, 4.83846618e-03,
           4.83846618e-03, 5.53424423e-07, 7.91631831e-04, 6.81274796e-04,
           1.20589492e-07, 2.07864800e-06, 2.07864800e-06, 1.52757639e-05,
           2.19148425e-06, 1.11678366e-06, 8.75293104e-03, 2.93101075e-07,
           1.51837156e-11, 7.38873451e-13, 5.02887552e-03, 9.37407828e-07,
           9.37407828e-07, 9.37407828e-07, 2.29536934e-06, 4.48035812e-06,
           1.07485686e-05, 2.29398703e-03, 9.74507369e-04, 2.27320185e-03,
           6.12704128e-03, 1.00377157e-03, 4.66936543e-10, 4.66936543e-10,
           1.86217964e-04, 1.86217964e-04, 7.83782572e-04, 7.83782572e-04,
           1.06500549e-04, 1.06500549e-04, 1.06500549e-04, 1.06500549e-04,
           1.86577499e-03, 1.86577499e-03, 1.17757687e-07, 1.17757687e-07,
           3.84174783e-09, 3.84174783e-09, 8.57122679e-04, 8.57122679e-04,
           3.47862953e-06, 3.47862953e-06, 1.78119047e-03, 1.78119047e-03,
           8.43968624e-08, 8.43968624e-08, 2.21701112e-06, 2.21701112e-06,
           1.34443416e-13, 1.34443416e-13, 2.51796718e-06, 2.51796718e-06,
           2.76188615e-06, 2.76188615e-06, 1.73786233e-06, 1.73786233e-06,
           4.19551498e-03, 4.19551498e-03, 4.19551498e-03, 4.19551498e-03,
           4.19551498e-03, 4.19551498e-03, 1.64019349e-05, 1.64019349e-05,
           8.28439833e-12, 8.28439833e-12, 2.24893743e-13, 2.24893743e-13,
           2.68647133e-14, 2.68647133e-14, 1.08595291e-13, 1.08595291e-13,
           3.24914465e-05, 3.24914465e-05, 8.79630131e-06, 8.79630131e-06,
           1.72821867e-04, 1.07075758e-07, 2.15575225e-07, 2.15575225e-07,
           2.39783016e-07, 7.33262606e-07, 7.33262606e-07, 7.33262606e-07,
           1.65897903e-06, 5.38302187e-06, 5.38302187e-06])




```python
probs1=lr.predict_proba(tr_inp)[:,1]
probs1
```




    array([3.41447985e-03, 1.25247717e-04, 1.11722943e-03, 1.77102850e-04,
           1.77102850e-04, 3.50309008e-03, 7.76441709e-08, 5.67078263e-06,
           1.22449812e-07, 3.45817392e-06, 3.64946785e-12, 2.20699227e-13,
           2.31190023e-04, 2.50213735e-06, 5.54760420e-03, 5.54760420e-03,
           5.54760420e-03, 2.56423048e-05, 1.30886058e-11, 6.92805921e-11,
           3.59437579e-13, 1.93555323e-14, 4.94812302e-05, 1.33354574e-05,
           2.59751256e-04, 2.59751256e-04, 1.49390845e-03, 2.11663501e-06,
           2.22039701e-03, 2.22039701e-03, 2.22039701e-03, 6.44895931e-05,
           6.44895931e-05, 6.44895931e-05, 3.86706095e-03, 2.51340358e-05,
           1.08832718e-04, 1.08832718e-04, 2.09225161e-06, 1.86217964e-04,
           1.86217964e-04, 1.86217964e-04, 1.01981119e-04, 1.01981119e-04,
           3.08115835e-06, 3.08115835e-06, 5.63540505e-06, 5.63540505e-06,
           3.08003700e-03, 3.08003700e-03, 1.04356323e-03, 1.47182878e-04,
           3.29919529e-03, 3.29919529e-03, 1.05352761e-04, 8.59829772e-06,
           9.45170950e-05, 7.16468112e-06, 5.08692163e-10, 5.08692163e-10,
           5.08692163e-10, 1.65590626e-04, 3.57217797e-09, 3.57217797e-09,
           4.97447622e-04, 6.73818119e-05, 4.24560642e-03, 4.24560642e-03,
           2.68112454e-04, 2.19722373e-05, 8.91881962e-03, 1.30238907e-09,
           9.85574549e-06, 9.85574549e-06, 2.35733894e-03, 9.85218962e-08,
           1.18135674e-10, 3.24620445e-06, 3.24620445e-06, 6.37856939e-05,
           9.65936291e-05, 8.11508290e-05, 6.21803044e-03, 6.21803044e-03,
           1.02919929e-06, 2.03191241e-07, 3.48596019e-04, 1.22574329e-04,
           6.97451093e-08, 3.19523094e-07, 3.19523094e-07, 2.60459730e-07,
           2.31428114e-07, 5.76230631e-08, 2.93101075e-07, 2.93101075e-07,
           3.71043918e-07, 4.39813777e-04, 4.39813777e-04, 4.39813777e-04,
           5.63540505e-06, 1.32346215e-05, 1.32346215e-05, 3.81578255e-16,
           5.40439631e-15, 3.77505351e-14, 1.12327490e-15, 3.17756478e-05,
           1.15781104e-02, 7.43064863e-10, 4.61195233e-06, 4.61195233e-06,
           5.82374977e-07, 8.91881962e-03, 6.35614033e-03, 4.91125791e-06,
           6.94434228e-07, 5.79597410e-04, 9.88048066e-03, 9.88048066e-03,
           6.03692553e-03, 2.02075617e-06, 9.14458495e-10, 5.64098608e-11,
           5.17526621e-05, 5.17526621e-05, 5.17526621e-05, 1.63475854e-05,
           6.73080281e-09, 1.18720589e-11, 1.36410873e-05, 2.45141741e-03,
           4.96791871e-06, 4.96791871e-06, 1.99016169e-03, 3.79640626e-05,
           1.43790863e-03, 1.43790863e-03, 4.35309124e-04, 1.82291349e-04,
           1.32465674e-04, 1.15077786e-04, 4.44416518e-07, 3.06679974e-08,
           7.08109795e-04, 1.35251547e-10, 8.27831259e-07, 5.43849132e-14,
           6.73382739e-03, 4.79740677e-09, 4.79740677e-09, 1.06560470e-10,
           9.94378364e-11, 5.66569841e-07, 7.93984795e-05, 1.16691085e-10,
           1.68705271e-07, 6.17242700e-03, 6.17242700e-03, 3.53303967e-03,
           9.15744678e-05, 1.11582579e-11, 2.87014601e-15, 1.24094397e-10,
           1.24094397e-10, 2.63866477e-12, 5.99808676e-12, 6.57072409e-08,
           5.63540505e-06, 6.62492310e-12, 8.03189473e-14, 2.59283071e-08,
           1.70003458e-03, 6.02178677e-04, 4.60441495e-03, 4.60441495e-03,
           4.35091739e-03, 1.53302662e-03, 1.01981119e-04, 4.87482721e-08,
           1.14991921e-07, 1.14991921e-07, 2.66685734e-07, 1.76275802e-07,
           8.55295298e-14, 2.06829940e-09, 2.14847018e-05, 2.14847018e-05,
           2.14847018e-05, 4.80666331e-07, 4.28451259e-09, 3.17219333e-06,
           2.73059362e-07, 1.38095165e-03, 1.38095165e-03, 5.44505168e-06,
           3.47350283e-05, 2.04922266e-04, 7.76006179e-04, 2.94841895e-08,
           1.66155878e-09, 1.52264352e-03, 1.52264352e-03, 6.66471042e-05,
           8.06839645e-04, 9.35942798e-05, 1.59823008e-10, 1.64019349e-05,
           1.64019349e-05, 1.64019349e-05, 1.71501375e-04, 6.47822448e-04,
           1.61639450e-05, 1.61639450e-05, 9.00300116e-04, 3.21485202e-03,
           6.94362510e-10, 5.17424389e-11, 5.17424389e-11, 5.17424389e-11,
           1.71581829e-05, 1.71581829e-05, 1.71581829e-05, 2.22480187e-09,
           2.22480187e-09, 2.22480187e-09, 5.46560374e-03, 5.46560374e-03,
           5.46560374e-03, 2.48543251e-05, 2.48543251e-05, 2.48543251e-05,
           2.48543251e-05, 2.48543251e-05, 2.48543251e-05, 1.17392799e-04,
           1.17392799e-04, 1.17392799e-04, 7.23561516e-04, 7.23561516e-04,
           7.23561516e-04, 3.65141235e-04, 3.65141235e-04, 3.65141235e-04,
           1.02316038e-08, 1.02316038e-08, 1.02316038e-08, 5.89102816e-10,
           5.89102816e-10, 5.89102816e-10, 3.05864491e-04, 3.05864491e-04,
           3.05864491e-04, 4.69498297e-07, 4.69498297e-07, 4.69498297e-07,
           4.27341263e-07, 4.27341263e-07, 4.27341263e-07, 8.38502409e-05,
           8.38502409e-05, 8.38502409e-05, 6.54460565e-09, 6.54460565e-09,
           6.54460565e-09, 6.46472636e-06, 6.46472636e-06, 6.46472636e-06,
           3.10912182e-07, 3.10912182e-07, 3.10912182e-07, 2.96313529e-13,
           2.96313529e-13, 2.96313529e-13, 1.64277203e-14, 1.64277203e-14,
           1.64277203e-14, 1.84170293e-06, 1.84170293e-06, 1.84170293e-06,
           3.33707568e-07, 3.33707568e-07, 3.33707568e-07, 8.73930108e-07,
           8.73930108e-07, 8.73930108e-07, 1.35795150e-07, 1.35795150e-07,
           1.35795150e-07, 2.22039701e-03, 2.22039701e-03, 2.22039701e-03,
           3.05152451e-03, 1.43790863e-03, 2.81959468e-03, 9.14192898e-03,
           1.39716810e-03, 1.17406721e-03, 1.17406721e-03, 3.68950513e-04,
           7.53108186e-04, 2.57401024e-07, 2.41670652e-06, 2.41670652e-06,
           1.71581829e-05, 3.24620445e-06, 2.19129106e-05, 1.25484670e-06,
           1.54452656e-09, 1.60215160e-06, 9.48041426e-03, 6.15063276e-07,
           1.19056186e-05, 1.08321901e-06, 3.69302822e-12, 3.85480345e-13,
           5.10646604e-03, 5.10646604e-03, 2.71099664e-08, 3.74994602e-04,
           1.92917559e-06, 1.92917559e-06, 1.92917559e-06, 4.28884801e-05,
           2.79934099e-03, 4.33659908e-05, 4.33659908e-05, 2.52268404e-08,
           1.16709037e-09, 4.72611322e-04, 1.07837858e-06, 1.69693047e-08,
           6.12505841e-13, 3.50027181e-14, 7.68415686e-07, 1.33008535e-06,
           4.58444812e-06, 2.99864584e-03, 8.81583082e-10, 9.48403138e-06,
           1.43153965e-13, 2.17172462e-03, 1.15850039e-08, 1.15850039e-08,
           2.91449104e-10, 7.38054964e-10, 4.69092529e-06, 1.07660493e-04,
           6.61271223e-10, 2.37879151e-03, 1.93883735e-06, 1.33628791e-06,
           5.72846274e-03, 2.11276328e-03, 3.83758600e-08, 9.02433327e-13,
           9.02433327e-13, 9.02433327e-13, 1.33904184e-04, 1.59127280e-06,
           8.33262124e-11, 2.03110020e-12, 2.16084226e-04, 3.35992456e-04,
           6.95105328e-04, 6.95105328e-04, 1.62219871e-03, 1.62219871e-03,
           1.62219871e-03, 1.62219871e-03, 7.33009905e-06, 2.82394468e-03,
           2.57959022e-03, 1.27185110e-10, 1.27185110e-10, 1.14313633e-06,
           2.94377500e-15, 3.50666030e-05, 1.58027337e-05, 2.19572520e-14,
           2.19572520e-14, 2.19572520e-14])




```python
from sklearn.metrics import mean_squared_error
mean_squared_error(tr_out,probs1)
```




    30793.92989251856




```python
tr_inp.size
```




    764




```python
import statsmodels.api as sm
import statsmodels.formula.api as smf 

reg1 = smf.ols(formula = ' tr_out ~ probs1' , data= tr_inp).fit()

print (reg1.summary())
```

                                OLS Regression Results                            
    ==============================================================================
    Dep. Variable:                 tr_out   R-squared:                       0.193
    Model:                            OLS   Adj. R-squared:                  0.190
    Method:                 Least Squares   F-statistic:                     90.60
    Date:                Thu, 28 Feb 2019   Prob (F-statistic):           2.09e-19
    Time:                        23:22:12   Log-Likelihood:                -2120.4
    No. Observations:                 382   AIC:                             4245.
    Df Residuals:                     380   BIC:                             4253.
    Df Model:                           1                                         
    Covariance Type:            nonrobust                                         
    ==============================================================================
                     coef    std err          t      P>|t|      [0.025      0.975]
    ------------------------------------------------------------------------------
    Intercept    174.3699      3.481     50.085      0.000     167.524     181.215
    probs1     -1.638e+04   1721.239     -9.518      0.000   -1.98e+04    -1.3e+04
    ==============================================================================
    Omnibus:                       23.271   Durbin-Watson:                   1.127
    Prob(Omnibus):                  0.000   Jarque-Bera (JB):               26.483
    Skew:                           0.643   Prob(JB):                     1.77e-06
    Kurtosis:                       2.891   Cond. No.                         539.
    ==============================================================================
    
    Warnings:
    [1] Standard Errors assume that the covariance matrix of the errors is correctly specified.
    


```python
import seaborn as sns
sns.residplot(ts_out,probs, data=df)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1d7c64d5710>




![png](output_36_1.png)



```python
tr_out.size
```




    382




```python
ts_out.size
```




    383




```python
df['FARE'].size
```




    638




```python
import matplotlib.pyplot as plt
plt.scatter(ts_out,probs)
```




    <matplotlib.collections.PathCollection at 0x1d7c34c4ac8>




![png](output_40_1.png)


## Yes, there is voilation in the residual plot when compared with the predicted plot. In residual plot it has the negative values of the testing fare values where as the predicted values never had a single negative values. 


```python
df['VACATION']=df['VACATION'].replace("No",0)
df['VACATION']=df['VACATION'].replace("Yes",1)
df['VACATION']
```




    0      0
    1      0
    2      0
    3      0
    4      0
    5      0
    6      0
    7      1
    8      0
    9      0
    10     1
    11     0
    12     0
    13     0
    14     0
    15     0
    16     0
    17     1
    18     0
    19     0
    20     0
    21     0
    22     0
    23     1
    24     0
    25     0
    26     0
    27     0
    28     0
    29     0
          ..
    608    0
    609    0
    610    0
    611    0
    612    0
    613    1
    614    1
    615    0
    616    0
    617    0
    618    0
    619    0
    620    0
    621    0
    622    0
    623    0
    624    0
    625    1
    626    1
    627    1
    628    1
    629    1
    630    1
    631    1
    632    1
    633    1
    634    1
    635    1
    636    1
    637    1
    Name: VACATION, Length: 638, dtype: int64




```python
df['SLOT']=df['SLOT'].replace("Free",0)
df['SLOT']=df['SLOT'].replace("Controlled",1)
df['SLOT']
```




    0      0
    1      0
    2      0
    3      1
    4      0
    5      0
    6      0
    7      0
    8      0
    9      0
    10     0
    11     0
    12     0
    13     0
    14     1
    15     1
    16     0
    17     0
    18     0
    19     0
    20     0
    21     0
    22     0
    23     0
    24     1
    25     0
    26     0
    27     0
    28     1
    29     1
          ..
    608    1
    609    1
    610    1
    611    0
    612    1
    613    0
    614    1
    615    0
    616    1
    617    0
    618    1
    619    0
    620    1
    621    0
    622    1
    623    0
    624    1
    625    0
    626    1
    627    0
    628    0
    629    1
    630    0
    631    0
    632    1
    633    1
    634    0
    635    0
    636    0
    637    1
    Name: SLOT, Length: 638, dtype: int64




```python
df['GATE']=df['GATE'].replace("Free",0)
df['GATE']=df['GATE'].replace("Constrained",1)
df['GATE']
```




    0      0
    1      0
    2      0
    3      0
    4      0
    5      0
    6      0
    7      0
    8      0
    9      0
    10     0
    11     0
    12     0
    13     0
    14     0
    15     0
    16     1
    17     0
    18     0
    19     0
    20     0
    21     0
    22     0
    23     0
    24     0
    25     0
    26     0
    27     0
    28     0
    29     0
          ..
    608    0
    609    0
    610    0
    611    1
    612    1
    613    0
    614    0
    615    0
    616    0
    617    0
    618    0
    619    0
    620    0
    621    0
    622    0
    623    0
    624    0
    625    0
    626    0
    627    0
    628    0
    629    0
    630    0
    631    0
    632    0
    633    0
    634    1
    635    0
    636    0
    637    0
    Name: GATE, Length: 638, dtype: int64




```python
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
      <th>COUPON</th>
      <th>NEW</th>
      <th>VACATION</th>
      <th>SW</th>
      <th>HI</th>
      <th>S_INCOME</th>
      <th>E_INCOME</th>
      <th>S_POP</th>
      <th>E_POP</th>
      <th>SLOT</th>
      <th>GATE</th>
      <th>DISTANCE</th>
      <th>PAX</th>
      <th>FARE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.00</td>
      <td>3</td>
      <td>0</td>
      <td>1</td>
      <td>5291.99</td>
      <td>28637.0</td>
      <td>21112.0</td>
      <td>3036732</td>
      <td>205711</td>
      <td>0</td>
      <td>0</td>
      <td>312</td>
      <td>7864</td>
      <td>64</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.06</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>5419.16</td>
      <td>26993.0</td>
      <td>29838.0</td>
      <td>3532657</td>
      <td>7145897</td>
      <td>0</td>
      <td>0</td>
      <td>576</td>
      <td>8820</td>
      <td>174</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.06</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>9185.28</td>
      <td>30124.0</td>
      <td>29838.0</td>
      <td>5787293</td>
      <td>7145897</td>
      <td>0</td>
      <td>0</td>
      <td>364</td>
      <td>6452</td>
      <td>207</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1.06</td>
      <td>3</td>
      <td>0</td>
      <td>1</td>
      <td>2657.35</td>
      <td>29260.0</td>
      <td>29838.0</td>
      <td>7830332</td>
      <td>7145897</td>
      <td>1</td>
      <td>0</td>
      <td>612</td>
      <td>25144</td>
      <td>85</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1.06</td>
      <td>3</td>
      <td>0</td>
      <td>1</td>
      <td>2657.35</td>
      <td>29260.0</td>
      <td>29838.0</td>
      <td>7830332</td>
      <td>7145897</td>
      <td>0</td>
      <td>0</td>
      <td>612</td>
      <td>25144</td>
      <td>85</td>
    </tr>
  </tbody>
</table>
</div>




```python
for i in range(13):
    df=df.iloc[::,1:]
    df.head()
```


```python
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
      <th>FARE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>64</td>
    </tr>
    <tr>
      <th>1</th>
      <td>174</td>
    </tr>
    <tr>
      <th>2</th>
      <td>207</td>
    </tr>
    <tr>
      <th>3</th>
      <td>85</td>
    </tr>
    <tr>
      <th>4</th>
      <td>85</td>
    </tr>
  </tbody>
</table>
</div>




```python
cls1=list(df.columns)
cls1
```




    ['FARE']




```python

```


```python
sz = df.index.size
tr = df[:int(sz*0.6)]
ts = df[int(sz*0.4):]
```


```python
tr_inp=tr[cls1]
tr_out=tr['FARE']
ts_inp=ts[cls1]
ts_out=ts['FARE']
```


```python
from sklearn.linear_model import LogisticRegression

lr = LogisticRegression()
lr.fit(tr_inp, tr_out)
```

    C:\Users\akula\Anaconda3\lib\site-packages\sklearn\linear_model\logistic.py:433: FutureWarning: Default solver will be changed to 'lbfgs' in 0.22. Specify a solver to silence this warning.
      FutureWarning)
    C:\Users\akula\Anaconda3\lib\site-packages\sklearn\linear_model\logistic.py:460: FutureWarning: Default multi_class will be changed to 'auto' in 0.22. Specify the multi_class option to silence this warning.
      "this warning.", FutureWarning)
    




    LogisticRegression(C=1.0, class_weight=None, dual=False, fit_intercept=True,
              intercept_scaling=1, max_iter=100, multi_class='warn',
              n_jobs=None, penalty='l2', random_state=None, solver='warn',
              tol=0.0001, verbose=0, warm_start=False)




```python
lr.coef_
```




    array([[-0.07375011],
           [-0.07062536],
           [-0.07013088],
           [-0.06283332],
           [-0.06160175],
           [-0.06099986],
           [-0.05739725],
           [-0.06732276],
           [-0.06687788],
           [-0.0553435 ],
           [-0.05756639],
           [-0.06473547],
           [-0.06432316],
           [-0.05544208],
           [-0.04737092],
           [-0.05442291],
           [-0.04737614],
           [-0.06233346],
           [-0.06157071],
           [-0.05152959],
           [-0.04356417],
           [-0.05061553],
           [-0.05973517],
           [-0.04972645],
           [-0.05902817],
           [-0.05868018],
           [-0.05833577],
           [-0.03543012],
           [-0.04161598],
           [-0.0459946 ],
           [-0.05570713],
           [-0.04446339],
           [-0.04409177],
           [-0.05446755],
           [-0.03704499],
           [-0.03666227],
           [-0.04160739],
           [-0.05212027],
           [-0.05183837],
           [-0.03419317],
           [-0.03385466],
           [-0.02739345],
           [-0.05046455],
           [-0.05019677],
           [-0.04992761],
           [-0.03813702],
           [-0.04940492],
           [-0.04914708],
           [-0.02512454],
           [-0.02480929],
           [-0.04840344],
           [-0.02099023],
           [-0.0238908 ],
           [-0.02983435],
           [-0.04715602],
           [-0.02526505],
           [-0.04668812],
           [-0.01694653],
           [-0.02818646],
           [-0.046003  ],
           [-0.04577324],
           [-0.04554529],
           [-0.04509471],
           [-0.02239391],
           [-0.02215169],
           [-0.0219124 ],
           [-0.02144241],
           [-0.02475519],
           [-0.02452974],
           [-0.04273654],
           [-0.01292316],
           [-0.02341736],
           [-0.04152974],
           [-0.04113905],
           [-0.01844229],
           [-0.02181252],
           [-0.01785862],
           [-0.01766826],
           [-0.03981479],
           [-0.02720475],
           [-0.01710929],
           [-0.01438854],
           [-0.01084737],
           [-0.01621617],
           [-0.03837845],
           [-0.03820405],
           [-0.03803165],
           [-0.02538082],
           [-0.03768917],
           [-0.02503477],
           [-0.00799063],
           [-0.03701751],
           [-0.0368523 ],
           [-0.00977795],
           [-0.02390921],
           [-0.0235782 ],
           [-0.03572493],
           [-0.01074118],
           [-0.01686025],
           [-0.01284818],
           [-0.03479732],
           [-0.03464604],
           [-0.03434624],
           [-0.01557121],
           [-0.02143582],
           [-0.03361247],
           [-0.00876264],
           [-0.02061242],
           [-0.02020281],
           [-0.03249771],
           [-0.03236089],
           [-0.03222488],
           [-0.01967346],
           [-0.00992011],
           [-0.01333383],
           [-0.00258008],
           [-0.01308997],
           [-0.01890952],
           [-0.00437946],
           [-0.02987888],
           [-0.01147533],
           [-0.02939206],
           [-0.01682307],
           [-0.02894888],
           [-0.01072341],
           [-0.02871596],
           [-0.02860044],
           [-0.01041121],
           [-0.00422702],
           [-0.02803198],
           [-0.01553515],
           [-0.01513352],
           [-0.02715297],
           [-0.01493647],
           [-0.0267269 ],
           [-0.00881635],
           [-0.02600166],
           [-0.0138039 ],
           [-0.02471961],
           [-0.00698829],
           [-0.02444495],
           [-0.00674024],
           [-0.00633516],
           [-0.01193055],
           [-0.02312864],
           [-0.00563073],
           [-0.02272183],
           [-0.02255011],
           [-0.01065019],
           [-0.02187994],
           [-0.00452564],
           [-0.00438127],
           [-0.02106948],
           [-0.02037078],
           [-0.00290238],
           [-0.01930323],
           [ 0.00202101],
           [-0.0180156 ]])




```python
probs=lr.predict_proba(ts_inp)[:,1]
probs
```




    array([1.44905414e-04, 4.94716247e-05, 4.94716247e-05, 4.94716247e-05,
           4.68293752e-05, 4.68293752e-05, 4.68293752e-05, 1.60228021e-10,
           1.60228021e-10, 1.60228021e-10, 5.13129479e-06, 5.13129479e-06,
           5.13129479e-06, 4.73794835e-07, 4.73794835e-07, 4.73794835e-07,
           1.15155291e-05, 1.15155291e-05, 1.15155291e-05, 7.18633150e-10,
           7.18633150e-10, 7.18633150e-10, 2.42124614e-07, 2.42124614e-07,
           2.42124614e-07, 1.37478825e-04, 1.37478825e-04, 1.37478825e-04,
           1.55981874e-08, 1.55981874e-08, 1.55981874e-08, 1.17099805e-06,
           1.17099805e-06, 1.17099805e-06, 3.36186141e-05, 3.36186141e-05,
           3.36186141e-05, 3.34155708e-03, 3.08735997e-03, 3.75406143e-03,
           2.22441714e-03, 5.68496410e-04, 2.13253284e-03, 2.13253284e-03,
           6.15540703e-05, 6.89180463e-04, 1.98148347e-04, 1.60921941e-04,
           1.60921941e-04, 6.49930480e-05, 5.82908191e-05, 3.83616288e-04,
           2.84474626e-05, 1.77821274e-06, 4.23680965e-04, 5.04681572e-03,
           2.31286397e-04, 3.36186141e-05, 1.60921941e-04, 1.98148347e-04,
           5.48274912e-08, 5.68496410e-04, 5.68496410e-04, 1.48726464e-06,
           6.89180463e-04, 1.44905414e-04, 1.44905414e-04, 1.44905414e-04,
           1.30416399e-04, 6.49930480e-05, 7.68884491e-07, 7.68884491e-07,
           9.59950792e-08, 4.00189260e-10, 8.15874469e-06, 8.98510638e-05,
           1.23231275e-10, 1.44664898e-05, 6.01383437e-09, 3.00789866e-05,
           5.29285916e-09, 2.31286397e-04, 3.21242199e-03, 1.88709949e-06,
           3.64939990e-04, 2.25456658e-06, 3.21242199e-03, 3.00789866e-05,
           3.00789866e-05, 1.36661692e-05, 2.14954737e-05, 3.28776341e-07,
           8.51535329e-05, 3.21246851e-06, 2.84916664e-03, 3.75603901e-05,
           9.58301390e-04, 3.75406143e-03, 4.05056383e-03, 2.53767355e-06,
           2.13903772e-08, 2.13903772e-08, 2.13903772e-08, 1.00371875e-03,
           1.15187023e-03, 1.71511823e-05, 6.83203616e-09, 6.56976700e-04,
           4.30708200e-06, 1.17099805e-06, 1.17099805e-06, 1.15155291e-05,
           1.15155291e-05, 1.15155291e-05, 1.15155291e-05, 1.52713692e-04,
           8.06923840e-05, 2.22441714e-03, 1.46417919e-08, 1.46417919e-08,
           3.83120115e-06, 1.40110169e-06, 1.95849873e-03, 7.22828769e-04,
           3.38137902e-09, 3.38137902e-09, 3.38137902e-09, 2.52055401e-03,
           2.31286397e-04, 2.31965926e-03, 1.26125988e-03, 5.68496410e-04,
           2.04392163e-03, 2.31965926e-03, 8.33008844e-04, 4.20541193e-03,
           7.70126611e-06, 6.03834289e-07, 6.03834289e-07, 3.47118090e-04,
           3.47118090e-04, 3.47118090e-04, 3.13896344e-04, 1.44905414e-04,
           5.82908191e-05, 2.85558390e-06, 2.85558390e-06, 3.09294836e-07,
           2.69019328e-05, 2.69019328e-05, 2.69019328e-05, 4.68293752e-05,
           2.98429052e-04, 2.98429052e-04, 1.30416399e-04, 1.30416399e-04,
           3.61231481e-03, 2.84916664e-03, 4.69675211e-03, 1.72051472e-03,
           5.22859891e-03, 2.04392163e-03, 5.60555318e-03, 5.04681572e-03,
           6.41490180e-07, 6.41490180e-07, 6.41490180e-07, 1.17317565e-04,
           1.17317565e-04, 1.17317565e-04, 3.90012801e-03, 3.34155708e-03,
           3.34155708e-03, 1.31936080e-03, 3.21242199e-03, 2.41834360e-03,
           6.47414021e-06, 4.56627202e-06, 4.56627202e-06, 1.95849873e-03,
           3.21242199e-03, 2.22441714e-03, 5.15079939e-08, 5.15079939e-08,
           5.15079939e-08, 1.95849873e-03, 1.64700200e-03, 1.72051472e-03,
           2.31965926e-03, 9.58301390e-04, 1.31936080e-03, 1.11249660e-04,
           1.11249660e-04, 2.52055401e-03, 2.52055401e-03, 9.14754067e-04,
           1.00003092e-04, 2.13903772e-08, 2.13903772e-08, 2.13903772e-08,
           1.88141279e-04, 1.48726464e-06, 6.83203616e-09, 6.03834289e-07,
           6.03834289e-07, 7.96783632e-08, 8.06923840e-05, 3.75406143e-03,
           1.87617946e-03, 1.87617946e-03, 8.47870712e-08, 4.09810736e-09,
           4.09810736e-09, 4.09810736e-09, 3.21242199e-03, 4.20541193e-03,
           3.08735997e-03, 4.67623271e-04, 1.02136000e-07, 4.89996650e-11,
           1.05107330e-03, 6.83203616e-09, 6.83203616e-09, 4.65765610e-09,
           1.21928954e-05, 1.56247633e-09, 1.57442006e-07, 2.08659123e-04,
           1.72051472e-03, 1.26125988e-03, 4.54538779e-08, 4.45861133e-07,
           3.08391597e-11, 3.08391597e-11, 3.08391597e-11, 4.54538779e-08,
           7.18633150e-10, 9.58301390e-04, 1.15187023e-03, 1.88709949e-06,
           4.78159200e-12, 2.96629962e-03, 5.64194261e-09, 5.64194261e-09,
           7.66815156e-10, 4.01044902e-08, 3.47483329e-03, 3.08735997e-03,
           6.89180463e-04, 2.52055401e-03, 2.52055401e-03, 6.86167353e-05,
           6.86167353e-05, 6.86167353e-05, 5.22575908e-05, 1.88709949e-06,
           4.65765610e-09, 5.41542369e-04, 4.83873816e-08, 4.83873816e-08,
           1.78086992e-07, 1.15155291e-05, 1.00084108e-08, 1.87617946e-03,
           4.45147116e-04, 4.30708200e-06, 7.76042974e-09, 7.76042974e-09,
           7.76042974e-09, 2.52055401e-03, 1.89389697e-07, 2.83681204e-04,
           4.05056383e-03, 2.00252762e-06, 1.44275454e-03, 1.44275454e-03,
           1.37983326e-03, 3.83120115e-06, 1.24323559e-06, 1.37983326e-03,
           3.64939990e-04, 3.34155708e-03, 5.51947201e-05, 1.03868592e-06,
           1.67550401e-06, 4.54538779e-08, 4.54538779e-08, 4.54538779e-08,
           5.22575908e-05, 6.86167353e-05, 1.69549229e-04, 1.69549229e-04,
           1.69549229e-04, 1.78615435e-04, 3.64939990e-04, 8.73011213e-04,
           1.37478825e-04, 1.17317565e-04, 1.17317565e-04, 3.47118090e-04,
           1.88709949e-06, 3.30114987e-04, 4.86952990e-03, 1.30416399e-04,
           1.11249660e-04, 4.45861133e-07, 9.58301390e-04, 1.44905414e-04,
           1.44905414e-04, 1.44905414e-04, 1.52713692e-04, 1.78615435e-04,
           7.64563191e-05, 4.36470846e-03, 4.36470846e-03, 3.61231481e-03,
           2.41834360e-03, 4.67623271e-04, 7.68884491e-07, 7.68884491e-07,
           1.36661692e-05, 1.36661692e-05, 8.98510638e-05, 8.98510638e-05,
           4.43237411e-05, 4.43237411e-05, 4.43237411e-05, 4.43237411e-05,
           4.67623271e-04, 4.67623271e-04, 6.21139420e-08, 6.21139420e-08,
           1.67450678e-07, 1.67450678e-07, 1.40110169e-06, 1.40110169e-06,
           1.17317565e-04, 1.17317565e-04, 1.98148347e-04, 1.98148347e-04,
           4.65765610e-09, 4.65765610e-09, 5.43892445e-06, 5.43892445e-06,
           3.17127647e-09, 3.17127647e-09, 3.96955514e-05, 3.96955514e-05,
           2.27719730e-07, 2.27719730e-07, 1.53124042e-05, 1.53124042e-05,
           2.31286397e-04, 2.31286397e-04, 2.31286397e-04, 2.31286397e-04,
           2.31286397e-04, 2.31286397e-04, 1.30416399e-04, 1.30416399e-04,
           1.46417919e-08, 1.46417919e-08, 2.13903772e-08, 2.13903772e-08,
           1.82673447e-10, 1.82673447e-10, 1.28998337e-08, 1.28998337e-08,
           5.48274912e-08, 5.48274912e-08, 8.98510638e-05, 8.98510638e-05,
           3.83616288e-04, 1.17317565e-04, 4.43237411e-05, 4.43237411e-05,
           1.00003092e-04, 1.05482876e-04, 1.05482876e-04, 1.05482876e-04,
           1.37478825e-04, 1.05482876e-04, 1.05482876e-04])




```python
probs1=lr.predict_proba(tr_inp)[:,1]
probs1
```




    array([2.41834360e-03, 8.64273848e-06, 1.24323559e-06, 9.58301390e-04,
           9.58301390e-04, 3.34155708e-03, 3.49466820e-07, 2.08659123e-04,
           9.69631606e-06, 2.31286397e-04, 2.14954737e-05, 3.49466820e-07,
           1.26125988e-03, 8.98510638e-05, 1.98148347e-04, 1.98148347e-04,
           1.98148347e-04, 3.47118090e-04, 5.76458088e-06, 2.27386581e-05,
           1.88709949e-06, 1.15605478e-07, 4.91151771e-04, 3.47118090e-04,
           2.43452612e-04, 2.43452612e-04, 1.95849873e-03, 1.03868592e-06,
           8.06923840e-05, 8.06923840e-05, 8.06923840e-05, 1.88141279e-04,
           1.88141279e-04, 1.88141279e-04, 5.41542369e-04, 2.01399891e-07,
           2.42124614e-07, 2.42124614e-07, 1.57862964e-06, 9.02192463e-08,
           9.02192463e-08, 9.02192463e-08, 3.47118090e-04, 3.47118090e-04,
           7.24345413e-05, 7.24345413e-05, 3.09294836e-07, 3.09294836e-07,
           6.10929149e-06, 6.10929149e-06, 7.68884491e-07, 2.25456658e-06,
           1.95849873e-03, 1.95849873e-03, 7.22828769e-04, 2.69622063e-04,
           3.21242199e-03, 3.83616288e-04, 2.69019328e-05, 2.69019328e-05,
           2.69019328e-05, 1.37983326e-03, 2.27386581e-05, 2.27386581e-05,
           2.43452612e-04, 4.94716247e-05, 1.50820314e-03, 1.50820314e-03,
           1.00371875e-03, 2.43452612e-04, 2.13253284e-03, 1.06024534e-09,
           1.30826865e-07, 1.30826865e-07, 1.31936080e-03, 1.03868592e-06,
           1.89595511e-09, 8.64273848e-06, 8.64273848e-06, 2.54380274e-05,
           3.47118090e-04, 2.83681204e-04, 1.57625871e-03, 1.57625871e-03,
           1.22983788e-07, 6.21139420e-08, 1.00371875e-03, 3.64939990e-04,
           1.60921941e-04, 2.84474626e-05, 2.84474626e-05, 1.24323559e-06,
           2.43452612e-04, 1.23701342e-04, 7.24345413e-05, 7.24345413e-05,
           3.13896344e-04, 6.10929149e-06, 6.10929149e-06, 6.10929149e-06,
           8.15874469e-06, 1.67450678e-07, 1.67450678e-07, 5.13129479e-06,
           1.29090589e-05, 7.26888849e-06, 5.34935513e-07, 2.57427785e-07,
           2.13253284e-03, 1.60228021e-10, 6.15540703e-05, 6.15540703e-05,
           3.21246851e-06, 2.31965926e-03, 2.13253284e-03, 1.48726464e-06,
           7.26888849e-06, 2.98429052e-04, 2.62637356e-03, 2.62637356e-03,
           1.15155291e-05, 3.64939990e-04, 2.31286397e-04, 2.84474626e-05,
           2.53767355e-06, 2.53767355e-06, 2.53767355e-06, 5.41542369e-04,
           6.49930480e-05, 2.27386581e-05, 4.91151771e-04, 8.73011213e-04,
           2.14954737e-05, 2.14954737e-05, 2.31286397e-04, 2.08659123e-04,
           1.50820314e-03, 1.50820314e-03, 2.08659123e-04, 2.83681204e-04,
           1.44905414e-04, 1.17317565e-04, 1.31936080e-03, 2.08659123e-04,
           1.72051472e-03, 4.94716247e-05, 1.20545456e-03, 8.51535329e-05,
           3.90012801e-03, 1.44905414e-04, 1.44905414e-04, 2.03184553e-05,
           2.19697018e-04, 1.53124042e-05, 7.94684572e-04, 1.62064214e-05,
           2.56222029e-04, 3.47483329e-03, 3.47483329e-03, 2.96629962e-03,
           1.44275454e-03, 4.19551884e-07, 3.60527745e-09, 2.57427785e-07,
           2.57427785e-07, 2.90952721e-07, 6.47414021e-06, 2.27821974e-08,
           1.05482876e-04, 5.29285916e-09, 2.85558390e-06, 2.53767355e-06,
           4.45147116e-04, 2.84916664e-03, 2.04392163e-03, 2.04392163e-03,
           2.84916664e-03, 1.87617946e-03, 5.41542369e-04, 2.14954737e-05,
           1.21928954e-05, 1.21928954e-05, 4.56627202e-06, 8.51535329e-05,
           1.24323559e-06, 4.19479512e-05, 3.40696057e-06, 3.40696057e-06,
           3.40696057e-06, 3.83616288e-04, 2.69019328e-05, 2.75183259e-08,
           5.48274912e-08, 2.40515880e-05, 2.40515880e-05, 3.09294836e-07,
           8.51535329e-05, 9.39224644e-09, 2.73684347e-07, 1.02691278e-05,
           1.15605478e-07, 1.00371875e-03, 1.00371875e-03, 5.76458088e-06,
           1.36661692e-05, 3.30114987e-04, 5.76458088e-06, 7.68884491e-07,
           7.68884491e-07, 7.68884491e-07, 8.73011213e-04, 1.69549229e-04,
           8.98510638e-05, 8.98510638e-05, 1.00371875e-03, 1.44275454e-03,
           1.67550401e-06, 1.17099805e-06, 1.17099805e-06, 1.17099805e-06,
           1.71511823e-05, 1.71511823e-05, 1.71511823e-05, 8.81368754e-09,
           8.81368754e-09, 8.81368754e-09, 2.08659123e-04, 2.08659123e-04,
           2.08659123e-04, 2.03184553e-05, 2.03184553e-05, 2.03184553e-05,
           2.03184553e-05, 2.03184553e-05, 2.03184553e-05, 1.40110169e-06,
           1.40110169e-06, 1.40110169e-06, 4.94716247e-05, 4.94716247e-05,
           4.94716247e-05, 8.64273848e-06, 8.64273848e-06, 8.64273848e-06,
           2.97412706e-09, 2.97412706e-09, 2.97412706e-09, 2.58402964e-08,
           2.58402964e-08, 2.58402964e-08, 1.10289216e-06, 1.10289216e-06,
           1.10289216e-06, 1.44905414e-04, 1.44905414e-04, 1.44905414e-04,
           4.94716247e-05, 4.94716247e-05, 4.94716247e-05, 4.68293752e-05,
           4.68293752e-05, 4.68293752e-05, 1.60228021e-10, 1.60228021e-10,
           1.60228021e-10, 5.13129479e-06, 5.13129479e-06, 5.13129479e-06,
           4.73794835e-07, 4.73794835e-07, 4.73794835e-07, 1.15155291e-05,
           1.15155291e-05, 1.15155291e-05, 7.18633150e-10, 7.18633150e-10,
           7.18633150e-10, 2.42124614e-07, 2.42124614e-07, 2.42124614e-07,
           1.37478825e-04, 1.37478825e-04, 1.37478825e-04, 1.55981874e-08,
           1.55981874e-08, 1.55981874e-08, 1.17099805e-06, 1.17099805e-06,
           1.17099805e-06, 3.36186141e-05, 3.36186141e-05, 3.36186141e-05,
           3.34155708e-03, 3.08735997e-03, 3.75406143e-03, 2.22441714e-03,
           5.68496410e-04, 2.13253284e-03, 2.13253284e-03, 6.15540703e-05,
           6.89180463e-04, 1.98148347e-04, 1.60921941e-04, 1.60921941e-04,
           6.49930480e-05, 5.82908191e-05, 3.83616288e-04, 2.84474626e-05,
           1.77821274e-06, 4.23680965e-04, 5.04681572e-03, 2.31286397e-04,
           3.36186141e-05, 1.60921941e-04, 1.98148347e-04, 5.48274912e-08,
           5.68496410e-04, 5.68496410e-04, 1.48726464e-06, 6.89180463e-04,
           1.44905414e-04, 1.44905414e-04, 1.44905414e-04, 1.30416399e-04,
           6.49930480e-05, 7.68884491e-07, 7.68884491e-07, 9.59950792e-08,
           4.00189260e-10, 8.15874469e-06, 8.98510638e-05, 1.23231275e-10,
           1.44664898e-05, 6.01383437e-09, 3.00789866e-05, 5.29285916e-09,
           2.31286397e-04, 3.21242199e-03, 1.88709949e-06, 3.64939990e-04,
           2.25456658e-06, 3.21242199e-03, 3.00789866e-05, 3.00789866e-05,
           1.36661692e-05, 2.14954737e-05, 3.28776341e-07, 8.51535329e-05,
           3.21246851e-06, 2.84916664e-03, 3.75603901e-05, 9.58301390e-04,
           3.75406143e-03, 4.05056383e-03, 2.53767355e-06, 2.13903772e-08,
           2.13903772e-08, 2.13903772e-08, 1.00371875e-03, 1.15187023e-03,
           1.71511823e-05, 6.83203616e-09, 6.56976700e-04, 4.30708200e-06,
           1.17099805e-06, 1.17099805e-06, 1.15155291e-05, 1.15155291e-05,
           1.15155291e-05, 1.15155291e-05, 1.52713692e-04, 8.06923840e-05,
           2.22441714e-03, 1.46417919e-08, 1.46417919e-08, 3.83120115e-06,
           1.40110169e-06, 1.95849873e-03, 7.22828769e-04, 3.38137902e-09,
           3.38137902e-09, 3.38137902e-09])




```python
from sklearn.metrics import mean_squared_error
mean_squared_error(ts_out,probs)
```




    33506.713134688616




```python
import statsmodels.api as sm
import statsmodels.formula.api as smf 

reg2 = smf.ols(formula = 'tr_inp ~ probs1' , data= tr_inp).fit()

print(reg2.summary())
```

                                OLS Regression Results                            
    ==============================================================================
    Dep. Variable:                 tr_inp   R-squared:                       0.382
    Model:                            OLS   Adj. R-squared:                  0.380
    Method:                 Least Squares   F-statistic:                     234.4
    Date:                Thu, 28 Feb 2019   Prob (F-statistic):           1.47e-41
    Time:                        23:24:45   Log-Likelihood:                -2069.4
    No. Observations:                 382   AIC:                             4143.
    Df Residuals:                     380   BIC:                             4151.
    Df Model:                           1                                         
    Covariance Type:            nonrobust                                         
    ==============================================================================
                     coef    std err          t      P>|t|      [0.025      0.975]
    ------------------------------------------------------------------------------
    Intercept    181.9477      3.107     58.559      0.000     175.838     188.057
    probs1     -5.034e+04   3287.479    -15.311      0.000   -5.68e+04   -4.39e+04
    ==============================================================================
    Omnibus:                       54.686   Durbin-Watson:                   1.233
    Prob(Omnibus):                  0.000   Jarque-Bera (JB):               74.469
    Skew:                           1.057   Prob(JB):                     6.75e-17
    Kurtosis:                       3.461   Cond. No.                     1.18e+03
    ==============================================================================
    
    Warnings:
    [1] Standard Errors assume that the covariance matrix of the errors is correctly specified.
    [2] The condition number is large, 1.18e+03. This might indicate that there are
    strong multicollinearity or other numerical problems.
    


```python
import seaborn as sns
sns.residplot(ts_out,probs, data=df)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1d7c6085048>




![png](output_58_1.png)



```python
import matplotlib.pyplot as plt
plt.scatter(ts_out,probs)
```




    <matplotlib.collections.PathCollection at 0x1d7c60e72e8>




![png](output_59_1.png)


## From the above Logistic Regression models the values of the R-square, MSE, AIC, BIC vales the better  results of the models generted can be predicted better. 
- The MSE value: It is the average of square root of errors. So the higher the MSE value the more is error and the model generated is not good one. Thuse comparing the values of MSE of the model one and model two regression analysis the MSE value of the second model with backward selection has slightly lesser MSE value than the first model. Thus the model with the highly correlated predictors is a better model for analysis. The second model is better one.

- R-square value: It is the propotion of the varience of the outcome that is explained by predictor variable. Thus greater the R-square value, better is the model. Thus compring the R-square of the model one has 0.193 while the second model had 0.389 which is slightly higher, thus proving model-2 is better than model one. 

- BIC value: The cretrian of the different parameter for better model.This BIC value depends on the AIC where it is greater in model one than in model two thus indicating the model two is better than model one. The AIC value of model two is 4143 where as the AIC value is 4245. Thus the BIC values are 4151 for model two where as 4253 for model one thus proving model two is better than model one.

# Model two (d) is better predictor than model one (c)



```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```
