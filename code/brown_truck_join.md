---
layout: page
title: endlesspint
subtitle: Causal Shmausal - GABF Medals (2016) EDA
---

```python
import numpy as np
import pandas as pd
import csv
import codecs
from bs4 import BeautifulSoup
import re
import os
import socket
import urllib
import time
import requests
```


```python
gtrend1 = pd.read_csv('timelines_brownTruckJoin/multiTimeline (1).csv', skiprows=2, index_col=0)
gtrend1.columns = [col.split(': ')[0].lower().replace(' ', '_') for col in gtrend1.columns]
gtrend1.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>millersburg_brewing</th>
      <th>bells_brewery</th>
      <th>rubicon_brewing_company_pub</th>
      <th>the_bruery</th>
      <th>brown_truck_brewery</th>
    </tr>
    <tr>
      <th>Day</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-07-01</th>
      <td>12</td>
      <td>12</td>
      <td>0</td>
      <td>37</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2016-07-02</th>
      <td>0</td>
      <td>29</td>
      <td>0</td>
      <td>14</td>
      <td>14</td>
    </tr>
    <tr>
      <th>2016-07-03</th>
      <td>0</td>
      <td>15</td>
      <td>0</td>
      <td>25</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2016-07-04</th>
      <td>0</td>
      <td>14</td>
      <td>0</td>
      <td>33</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2016-07-05</th>
      <td>0</td>
      <td>13</td>
      <td>0</td>
      <td>38</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
gtrend2 = pd.read_csv('timelines_brownTruckJoin/multiTimeline (2).csv', skiprows=2, index_col=0)
gtrend2.columns = [col.split(': ')[0].lower().replace(' ', '_') for col in gtrend2.columns]
gtrend2.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brown_truck_brewery</th>
      <th>crank_arm_brewing</th>
      <th>el_segundo_brewing</th>
      <th>iowa_brewing</th>
      <th>figueroa_mountain_brewing</th>
    </tr>
    <tr>
      <th>Day</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-07-01</th>
      <td>0</td>
      <td>0</td>
      <td>31</td>
      <td>31</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2016-07-02</th>
      <td>36</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>36</td>
    </tr>
    <tr>
      <th>2016-07-03</th>
      <td>0</td>
      <td>0</td>
      <td>74</td>
      <td>37</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2016-07-04</th>
      <td>0</td>
      <td>0</td>
      <td>35</td>
      <td>71</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2016-07-05</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
def import_gtrend(file_path):
    gtrend = pd.read_csv(file_path, skiprows=2, index_col=0)
    gtrend.columns = [col.split(': ')[0].lower().replace(' ', '_') for col in gtrend.columns]
    return gtrend

import_gtrend('timelines_brownTruckJoin/multiTimeline (3).csv').head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brown_truck_brewery</th>
      <th>bns_brewing_&amp;_distilling</th>
      <th>vintage_brewing</th>
      <th>smog_city_brewing</th>
      <th>lynnwood_brewing_concern</th>
    </tr>
    <tr>
      <th>Day</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-07-01</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>30</td>
    </tr>
    <tr>
      <th>2016-07-02</th>
      <td>34</td>
      <td>0</td>
      <td>34</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2016-07-03</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>35</td>
    </tr>
    <tr>
      <th>2016-07-04</th>
      <td>34</td>
      <td>0</td>
      <td>0</td>
      <td>34</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2016-07-05</th>
      <td>0</td>
      <td>0</td>
      <td>60</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.concat([gtrend1.brown_truck_brewery, gtrend2.brown_truck_brewery, 
           np.isfinite(gtrend1.brown_truck_brewery/gtrend2.brown_truck_brewery)
          ], axis=1).head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brown_truck_brewery</th>
      <th>brown_truck_brewery</th>
      <th>brown_truck_brewery</th>
    </tr>
    <tr>
      <th>Day</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-07-01</th>
      <td>0</td>
      <td>0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2016-07-02</th>
      <td>14</td>
      <td>36</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2016-07-03</th>
      <td>0</td>
      <td>0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2016-07-04</th>
      <td>0</td>
      <td>0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2016-07-05</th>
      <td>0</td>
      <td>0</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>




```python
np.mean((gtrend1.brown_truck_brewery/gtrend2.brown_truck_brewery)[np.isfinite(gtrend1.brown_truck_brewery/gtrend2.brown_truck_brewery)])
```




    0.4035917946776314




```python
def gtrend_norm(df_1, df_2, col='brown_truck_brewery'):
    norm_mult = np.mean((df_1.brown_truck_brewery/df_2.brown_truck_brewery)[np.isfinite(df_1.brown_truck_brewery/df_2.brown_truck_brewery)])
    return norm_mult

gtrend_norm(gtrend1, gtrend2)
```




    0.4035917946776314




```python
def df_norm(df_2, norm_mult):
    return df_2.iloc[:,1:] * norm_mult

df_norm(gtrend2, 0.4036).head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>crank_arm_brewing</th>
      <th>el_segundo_brewing</th>
      <th>iowa_brewing</th>
      <th>figueroa_mountain_brewing</th>
    </tr>
    <tr>
      <th>Day</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-07-01</th>
      <td>0.0</td>
      <td>12.5116</td>
      <td>12.5116</td>
      <td>0.0000</td>
    </tr>
    <tr>
      <th>2016-07-02</th>
      <td>0.0</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>14.5296</td>
    </tr>
    <tr>
      <th>2016-07-03</th>
      <td>0.0</td>
      <td>29.8664</td>
      <td>14.9332</td>
      <td>0.0000</td>
    </tr>
    <tr>
      <th>2016-07-04</th>
      <td>0.0</td>
      <td>14.1260</td>
      <td>28.6556</td>
      <td>0.0000</td>
    </tr>
    <tr>
      <th>2016-07-05</th>
      <td>0.0</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
    </tr>
  </tbody>
</table>
</div>




```python
gtrend1.join(gtrend2.iloc[:,1:] * gtrend_norm(gtrend1, gtrend2)).head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>millersburg_brewing</th>
      <th>bells_brewery</th>
      <th>rubicon_brewing_company_pub</th>
      <th>the_bruery</th>
      <th>brown_truck_brewery</th>
      <th>crank_arm_brewing</th>
      <th>el_segundo_brewing</th>
      <th>iowa_brewing</th>
      <th>figueroa_mountain_brewing</th>
    </tr>
    <tr>
      <th>Day</th>
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
      <th>2016-07-01</th>
      <td>12</td>
      <td>12</td>
      <td>0</td>
      <td>37</td>
      <td>0</td>
      <td>0.0</td>
      <td>12.511346</td>
      <td>12.511346</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2016-07-02</th>
      <td>0</td>
      <td>29</td>
      <td>0</td>
      <td>14</td>
      <td>14</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>14.529305</td>
    </tr>
    <tr>
      <th>2016-07-03</th>
      <td>0</td>
      <td>15</td>
      <td>0</td>
      <td>25</td>
      <td>0</td>
      <td>0.0</td>
      <td>29.865793</td>
      <td>14.932896</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2016-07-04</th>
      <td>0</td>
      <td>14</td>
      <td>0</td>
      <td>33</td>
      <td>0</td>
      <td>0.0</td>
      <td>14.125713</td>
      <td>28.655017</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2016-07-05</th>
      <td>0</td>
      <td>13</td>
      <td>0</td>
      <td>38</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
os.listdir('timelines_brownTruckJoin/')
```




    ['multiTimeline (1).csv',
     'multiTimeline (10).csv',
     'multiTimeline (11).csv',
     'multiTimeline (12).csv',
     'multiTimeline (13).csv',
     'multiTimeline (14).csv',
     'multiTimeline (15).csv',
     'multiTimeline (16).csv',
     'multiTimeline (17).csv',
     'multiTimeline (18).csv',
     'multiTimeline (19).csv',
     'multiTimeline (2).csv',
     'multiTimeline (20).csv',
     'multiTimeline (21).csv',
     'multiTimeline (22).csv',
     'multiTimeline (23).csv',
     'multiTimeline (24).csv',
     'multiTimeline (25).csv',
     'multiTimeline (26).csv',
     'multiTimeline (27).csv',
     'multiTimeline (28).csv',
     'multiTimeline (29).csv',
     'multiTimeline (3).csv',
     'multiTimeline (30).csv',
     'multiTimeline (31).csv',
     'multiTimeline (32).csv',
     'multiTimeline (33).csv',
     'multiTimeline (34).csv',
     'multiTimeline (35).csv',
     'multiTimeline (36).csv',
     'multiTimeline (37).csv',
     'multiTimeline (38).csv',
     'multiTimeline (39).csv',
     'multiTimeline (4).csv',
     'multiTimeline (40).csv',
     'multiTimeline (41).csv',
     'multiTimeline (42).csv',
     'multiTimeline (43).csv',
     'multiTimeline (44).csv',
     'multiTimeline (45).csv',
     'multiTimeline (46).csv',
     'multiTimeline (47).csv',
     'multiTimeline (48).csv',
     'multiTimeline (49).csv',
     'multiTimeline (5).csv',
     'multiTimeline (50).csv',
     'multiTimeline (51).csv',
     'multiTimeline (52).csv',
     'multiTimeline (53).csv',
     'multiTimeline (54).csv',
     'multiTimeline (55).csv',
     'multiTimeline (56).csv',
     'multiTimeline (57).csv',
     'multiTimeline (58).csv',
     'multiTimeline (59).csv',
     'multiTimeline (6).csv',
     'multiTimeline (60).csv',
     'multiTimeline (61).csv',
     'multiTimeline (62).csv',
     'multiTimeline (63).csv',
     'multiTimeline (7).csv',
     'multiTimeline (8).csv',
     'multiTimeline (9).csv']



## let's put it together
- load files in directory
- hold first file as 'node'
- cycle through other files
- match on common term/brewery
- normalize the cycled file
- join to 'node'
- suffix in case of dupes; not all bad, will allow for comparisons (dupe columns should match/be close on values)
- repeat for remaining files
- return wide df


```python
dir_trends = 'timelines_brownTruckJoin/'
node_file = os.listdir(dir_trends)[0]

def gtrend_join(file_dir = dir_trends, node_file = node_file):
    
    node_file = import_gtrend(file_dir + node_file)
    
    for i in os.listdir(file_dir)[1:]:
        
        temp_file = import_gtrend(file_dir + i)
        node_file = node_file.join(df_norm(temp_file, gtrend_norm(node_file, temp_file)),
                                   lsuffix = '', rsuffix = '_y')
#         node_file = pd.merge(node_file, df_norm(temp_file, gtrend_norm(node_file, temp_file)), 
#                              left_index=True, right_index=True, suffixes=('', '_y'))
    
    return node_file


combined_trends = gtrend_join()
print combined_trends.shape
combined_trends.head()
```

    (123, 252)
    




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>millersburg_brewing</th>
      <th>bells_brewery</th>
      <th>rubicon_brewing_company_pub</th>
      <th>the_bruery</th>
      <th>brown_truck_brewery</th>
      <th>great_notion_brewing</th>
      <th>max_lagers_wood</th>
      <th>10_barrel_brewing</th>
      <th>boise_brewing</th>
      <th>societe_brewing</th>
      <th>...</th>
      <th>coors_brewing</th>
      <th>craft_brew_alliance_y</th>
      <th>carver_brewing</th>
      <th>aeronaut_brewing</th>
      <th>pelican_brewing</th>
      <th>ska_brewing</th>
      <th>bootstrap_brewing</th>
      <th>central_coast_brewing</th>
      <th>maplewood_brewery</th>
      <th>karl_strauss_brewing_y</th>
    </tr>
    <tr>
      <th>Day</th>
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
      <th>2016-07-01</th>
      <td>12</td>
      <td>12</td>
      <td>0</td>
      <td>37</td>
      <td>0</td>
      <td>20.007564</td>
      <td>0.0</td>
      <td>9.733410</td>
      <td>9.733410</td>
      <td>9.842289</td>
      <td>...</td>
      <td>0.000000</td>
      <td>9.26641</td>
      <td>9.774888</td>
      <td>14.662332</td>
      <td>9.774888</td>
      <td>24.881533</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>9.839457</td>
    </tr>
    <tr>
      <th>2016-07-02</th>
      <td>0</td>
      <td>29</td>
      <td>0</td>
      <td>14</td>
      <td>14</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>30.281719</td>
      <td>11.355645</td>
      <td>11.482671</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>11.107827</td>
      <td>11.552140</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>11.181201</td>
    </tr>
    <tr>
      <th>2016-07-03</th>
      <td>0</td>
      <td>15</td>
      <td>0</td>
      <td>25</td>
      <td>0</td>
      <td>11.896390</td>
      <td>0.0</td>
      <td>35.689169</td>
      <td>11.896390</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>11.552140</td>
      <td>11.552140</td>
      <td>0.0</td>
      <td>11.628449</td>
      <td>0.000000</td>
      <td>11.628449</td>
    </tr>
    <tr>
      <th>2016-07-04</th>
      <td>0</td>
      <td>14</td>
      <td>0</td>
      <td>33</td>
      <td>0</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>22.711289</td>
      <td>11.355645</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>22.659967</td>
      <td>11.107827</td>
      <td>11.107827</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>11.181201</td>
      <td>11.181201</td>
    </tr>
    <tr>
      <th>2016-07-05</th>
      <td>0</td>
      <td>13</td>
      <td>0</td>
      <td>38</td>
      <td>0</td>
      <td>10.274155</td>
      <td>0.0</td>
      <td>25.415014</td>
      <td>10.274155</td>
      <td>10.252385</td>
      <td>...</td>
      <td>18.918921</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>10.219201</td>
      <td>15.106645</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 252 columns</p>
</div>




```python
from collections import Counter

cnt = Counter()

for i in os.listdir(dir_trends):
    temp_file = import_gtrend(dir_trends + i)
    for col in temp_file.columns:
        cnt[col] += 1
        
[brw for brw in cnt if cnt[brw] > 1]
```




    ['craft_brew_alliance',
     'figueroa_mountain_brewing',
     'ram/big_horn_brewery',
     'lynnwood_brewing_concern',
     'echo_brewing',
     'bjs_restaurant_&_brewery',
     'devils_backbone_brewing',
     'brown_truck_brewery',
     'karl_strauss_brewing']




```python
none_dupes = [brw for brw in combined_trends.columns.tolist() if '_y' not in brw]
combined_trends = combined_trends[none_dupes]
print combined_trends.shape
combined_trends.head()
```

    (123, 242)
    




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>millersburg_brewing</th>
      <th>bells_brewery</th>
      <th>rubicon_brewing_company_pub</th>
      <th>the_bruery</th>
      <th>brown_truck_brewery</th>
      <th>great_notion_brewing</th>
      <th>max_lagers_wood</th>
      <th>10_barrel_brewing</th>
      <th>boise_brewing</th>
      <th>societe_brewing</th>
      <th>...</th>
      <th>riip_beer</th>
      <th>knee_deep_brewing</th>
      <th>coors_brewing</th>
      <th>carver_brewing</th>
      <th>aeronaut_brewing</th>
      <th>pelican_brewing</th>
      <th>ska_brewing</th>
      <th>bootstrap_brewing</th>
      <th>central_coast_brewing</th>
      <th>maplewood_brewery</th>
    </tr>
    <tr>
      <th>Day</th>
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
      <th>2016-07-01</th>
      <td>12</td>
      <td>12</td>
      <td>0</td>
      <td>37</td>
      <td>0</td>
      <td>20.007564</td>
      <td>0.0</td>
      <td>9.733410</td>
      <td>9.733410</td>
      <td>9.842289</td>
      <td>...</td>
      <td>0.0</td>
      <td>13.899615</td>
      <td>0.000000</td>
      <td>9.774888</td>
      <td>14.662332</td>
      <td>9.774888</td>
      <td>24.881533</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2016-07-02</th>
      <td>0</td>
      <td>29</td>
      <td>0</td>
      <td>14</td>
      <td>14</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>30.281719</td>
      <td>11.355645</td>
      <td>11.482671</td>
      <td>...</td>
      <td>0.0</td>
      <td>21.621624</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>11.107827</td>
      <td>11.552140</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2016-07-03</th>
      <td>0</td>
      <td>15</td>
      <td>0</td>
      <td>25</td>
      <td>0</td>
      <td>11.896390</td>
      <td>0.0</td>
      <td>35.689169</td>
      <td>11.896390</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>11.552140</td>
      <td>11.552140</td>
      <td>0.0</td>
      <td>11.628449</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2016-07-04</th>
      <td>0</td>
      <td>14</td>
      <td>0</td>
      <td>33</td>
      <td>0</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>22.711289</td>
      <td>11.355645</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>22.659967</td>
      <td>11.107827</td>
      <td>11.107827</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>11.181201</td>
    </tr>
    <tr>
      <th>2016-07-05</th>
      <td>0</td>
      <td>13</td>
      <td>0</td>
      <td>38</td>
      <td>0</td>
      <td>10.274155</td>
      <td>0.0</td>
      <td>25.415014</td>
      <td>10.274155</td>
      <td>10.252385</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>18.918921</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>10.219201</td>
      <td>15.106645</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 242 columns</p>
</div>




```python
# combined_trends.to_csv('timelines_combined/combined_trends.csv', sep=';')
```

## look at trend diff for date split

- pre.period <- as.Date(c("2016-07-01", "2016-10-05"))
- post.period <- as.Date(c("2016-10-09", "2016-10-31"))


```python
import matplotlib.pyplot as plt
import matplotlib
matplotlib.style.use('ggplot')
%matplotlib inline
```


```python
pre_gabf16 = combined_trends.index <= '2016-10-05'
post_gabf16 = combined_trends.index >= '2016-10-09'
```


```python
pre_post_avgs = combined_trends[pre_gabf16].mean().to_frame(name='pre_gabf16').join(combined_trends[post_gabf16].mean().to_frame(name='post_gabf16'))
pre_post_avgs.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pre_gabf16</th>
      <th>post_gabf16</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>millersburg_brewing</th>
      <td>2.525773</td>
      <td>2.086957</td>
    </tr>
    <tr>
      <th>bells_brewery</th>
      <td>18.896907</td>
      <td>15.521739</td>
    </tr>
    <tr>
      <th>rubicon_brewing_company_pub</th>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>the_bruery</th>
      <td>28.855670</td>
      <td>33.478261</td>
    </tr>
    <tr>
      <th>brown_truck_brewery</th>
      <td>3.278351</td>
      <td>9.478261</td>
    </tr>
  </tbody>
</table>
</div>




```python
pre_post_avgs['dif_gabf16_norm'] = pre_post_avgs.post_gabf16/(pre_post_avgs.pre_gabf16 + 0.000001)
pre_post_avgs.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pre_gabf16</th>
      <th>post_gabf16</th>
      <th>dif_gabf16_norm</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>millersburg_brewing</th>
      <td>2.525773</td>
      <td>2.086957</td>
      <td>0.826264</td>
    </tr>
    <tr>
      <th>bells_brewery</th>
      <td>18.896907</td>
      <td>15.521739</td>
      <td>0.821390</td>
    </tr>
    <tr>
      <th>rubicon_brewing_company_pub</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>the_bruery</th>
      <td>28.855670</td>
      <td>33.478261</td>
      <td>1.160197</td>
    </tr>
    <tr>
      <th>brown_truck_brewery</th>
      <td>3.278351</td>
      <td>9.478261</td>
      <td>2.891167</td>
    </tr>
  </tbody>
</table>
</div>




```python
pre_post_avgs.dif_gabf16_norm.describe()
```




    count    242.000000
    mean       0.893139
    std        0.837155
    min        0.000000
    25%        0.432029
    50%        0.843814
    75%        1.115964
    max        5.504798
    Name: dif_gabf16_norm, dtype: float64




```python
plt.figure(figsize=(12, 6))
plt.hist(pre_post_avgs.dif_gabf16_norm)
plt.title('Search Engagement Ratio - Post GABF Medal (2016)')
plt.ylabel('Brewery Count')
```




    <matplotlib.text.Text at 0xb8c8048>




<img src = "/code/brown_truck_join/output_21_1.png">



```python
plt.boxplot(pre_post_avgs.dif_gabf16_norm)
```




    {'boxes': [<matplotlib.lines.Line2D at 0xbb8cd30>],
     'caps': [<matplotlib.lines.Line2D at 0xbba09b0>,
      <matplotlib.lines.Line2D at 0xbba0f28>],
     'fliers': [<matplotlib.lines.Line2D at 0xbbeea58>],
     'means': [],
     'medians': [<matplotlib.lines.Line2D at 0xbbee4e0>],
     'whiskers': [<matplotlib.lines.Line2D at 0xbb8ce10>,
      <matplotlib.lines.Line2D at 0xbba0438>]}




<img src = "/code/brown_truck_join/output_22_1.png">


## time series of non-zero averages


```python
# 1/6 of breweries have NO Google search data
np.sum(combined_trends.mean(axis=0) == 0.0)
```




    40




```python
mean_idx_trends = combined_trends.divide(combined_trends.mean(axis=0))
mean_idx_trends.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>millersburg_brewing</th>
      <th>bells_brewery</th>
      <th>rubicon_brewing_company_pub</th>
      <th>the_bruery</th>
      <th>brown_truck_brewery</th>
      <th>great_notion_brewing</th>
      <th>max_lagers_wood</th>
      <th>10_barrel_brewing</th>
      <th>boise_brewing</th>
      <th>societe_brewing</th>
      <th>...</th>
      <th>riip_beer</th>
      <th>knee_deep_brewing</th>
      <th>coors_brewing</th>
      <th>carver_brewing</th>
      <th>aeronaut_brewing</th>
      <th>pelican_brewing</th>
      <th>ska_brewing</th>
      <th>bootstrap_brewing</th>
      <th>central_coast_brewing</th>
      <th>maplewood_brewery</th>
    </tr>
    <tr>
      <th>Day</th>
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
      <th>2016-07-01</th>
      <td>4.641509</td>
      <td>0.656876</td>
      <td>NaN</td>
      <td>1.239042</td>
      <td>0.000000</td>
      <td>2.913572</td>
      <td>NaN</td>
      <td>0.447997</td>
      <td>1.112004</td>
      <td>1.101082</td>
      <td>...</td>
      <td>0.0</td>
      <td>1.673469</td>
      <td>0.000000</td>
      <td>4.609881</td>
      <td>1.706179</td>
      <td>1.210197</td>
      <td>2.085377</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.0000</td>
    </tr>
    <tr>
      <th>2016-07-02</th>
      <td>0.000000</td>
      <td>1.587450</td>
      <td>NaN</td>
      <td>0.468827</td>
      <td>3.015762</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>1.393768</td>
      <td>1.297338</td>
      <td>1.284595</td>
      <td>...</td>
      <td>0.0</td>
      <td>2.603175</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.375224</td>
      <td>0.968211</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.0000</td>
    </tr>
    <tr>
      <th>2016-07-03</th>
      <td>0.000000</td>
      <td>0.821095</td>
      <td>NaN</td>
      <td>0.837190</td>
      <td>0.000000</td>
      <td>1.732394</td>
      <td>NaN</td>
      <td>1.642655</td>
      <td>1.359116</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.430233</td>
      <td>0.968211</td>
      <td>0.0</td>
      <td>6.580247</td>
      <td>0.0000</td>
    </tr>
    <tr>
      <th>2016-07-04</th>
      <td>0.000000</td>
      <td>0.766355</td>
      <td>NaN</td>
      <td>1.105091</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>1.045326</td>
      <td>1.297338</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.636822</td>
      <td>1.375224</td>
      <td>0.930972</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>7.6875</td>
    </tr>
    <tr>
      <th>2016-07-05</th>
      <td>0.000000</td>
      <td>0.711615</td>
      <td>NaN</td>
      <td>1.272529</td>
      <td>0.000000</td>
      <td>1.496159</td>
      <td>NaN</td>
      <td>1.169769</td>
      <td>1.173782</td>
      <td>1.146960</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>1.806655</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.265206</td>
      <td>1.266122</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.0000</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 242 columns</p>
</div>




```python

mean_idx_trends.plot(legend=False, figsize=(16, 8))
plt.title('Brewery Search Hits (indexed)')
plt.ylabel('relative to own avg')
```




    <matplotlib.text.Text at 0xbd35748>




<img src = "/code/brown_truck_join/output_26_1.png">



```python
mean_idx_trends[pre_gabf16].max().sort_values(ascending=False)[:10]
```




    two_kilts_brewing              123.000000
    12degree_brewing                61.500000
    ghostfish_brewing_company       60.701299
    high_heel_brewing               49.785714
    zwanzigz_brewing                27.954545
    auburn_alehouse                 25.408451
    black_tooth_brewing             25.408451
    logsdon_farmhouse_ales          23.697248
    grimm_brothers_brewhouse        23.455814
    taps_fish_house_and_brewery     22.932203
    dtype: float64




```python
mean_idx_trends[post_gabf16].max().sort_values(ascending=False)[:10]
```




    12degree_brewing               61.500000
    zwanzigz_brewing               31.448864
    logsdon_farmhouse_ales         22.004587
    taps_fish_house_and_brewery    21.889831
    pizza_port_san_clemente        20.856522
    auburn_alehouse                19.056338
    morgan_territory_brewing       17.571429
    solid_rock_brewing             17.253394
    gibbs_hundred_brewing          16.400000
    ardent_craft_ales              15.216495
    dtype: float64



### IQR


```python
(mean_idx_trends[pre_gabf16].sum(axis=1)).describe()
```




    count     97.000000
    mean     201.333917
    std       48.543656
    min      127.849023
    25%      160.680484
    50%      191.979998
    75%      231.980401
    max      350.348231
    dtype: float64




```python
(mean_idx_trends[post_gabf16].sum(axis=1)).describe()
```




    count     23.000000
    mean     196.012536
    std       39.039190
    min      116.992323
    25%      160.378756
    50%      201.091106
    75%      231.406028
    max      252.729727
    dtype: float64



## import brewery type, state, and medal count


```python
gabf16_type = pd.read_excel('comp_breweries/gabf16_type.xlsx', index_col=0)

print gabf16_type.shape
gabf16_type.tail()
```

    (303, 16)
    




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>medal</th>
      <th>beer_name</th>
      <th>brewery</th>
      <th>city</th>
      <th>state</th>
      <th>category</th>
      <th>year</th>
      <th>medal_cnt</th>
      <th>brewery_name2</th>
      <th>brewery_type</th>
      <th>name_brewassoc</th>
      <th>name_Gtrends</th>
      <th>FAM</th>
      <th>PARENT</th>
      <th>DUPE</th>
      <th>RETAIN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>302</th>
      <td>Silver</td>
      <td>MÃ©lange A Trois</td>
      <td>Nebraska Brewing Co. - Papillion</td>
      <td>Papillion</td>
      <td>NE</td>
      <td>Wood- and Barrel-Aged Strong Beer</td>
      <td>2016</td>
      <td>2</td>
      <td>nebraska brew</td>
      <td>Brewpub</td>
      <td>Nebraska Brewing Co</td>
      <td>nebraska_brewing</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>303</th>
      <td>Bronze</td>
      <td>15th Anniversary Ale</td>
      <td>Island Brewing Co.</td>
      <td>Carpinteria</td>
      <td>CA</td>
      <td>Wood- and Barrel-Aged Strong Beer</td>
      <td>2016</td>
      <td>1</td>
      <td>island brew</td>
      <td>Micro</td>
      <td>Island Brewing Co</td>
      <td>island_brewing</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>304</th>
      <td>Gold</td>
      <td>Barrel-Aged Darkness</td>
      <td>Surly Brewing Co.</td>
      <td>Brooklyn Center</td>
      <td>MN</td>
      <td>Wood- and Barrel-Aged Strong Stout</td>
      <td>2016</td>
      <td>1</td>
      <td>surly brew</td>
      <td>Regional</td>
      <td>Surly Brewing Company</td>
      <td>surly_brewing</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>305</th>
      <td>Silver</td>
      <td>The Event Horizon</td>
      <td>Olde Hickory Brewery</td>
      <td>Hickory</td>
      <td>NC</td>
      <td>Wood- and Barrel-Aged Strong Stout</td>
      <td>2016</td>
      <td>2</td>
      <td>olde hickory brew</td>
      <td>Micro</td>
      <td>Olde Hickory Brewery - Production</td>
      <td>olde_hickory_brewery</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>306</th>
      <td>Bronze</td>
      <td>Little Nonsense</td>
      <td>Verboten Brewing</td>
      <td>Loveland</td>
      <td>CO</td>
      <td>Wood- and Barrel-Aged Strong Stout</td>
      <td>2016</td>
      <td>1</td>
      <td>verboten brew</td>
      <td>Micro</td>
      <td>Verboten Brewing</td>
      <td>verboten_brewing</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>




```python
gabf16_new = gabf16_type[gabf16_type.RETAIN == True]

print gabf16_new.shape
gabf16_new.tail()
```

    (286, 16)
    




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>medal</th>
      <th>beer_name</th>
      <th>brewery</th>
      <th>city</th>
      <th>state</th>
      <th>category</th>
      <th>year</th>
      <th>medal_cnt</th>
      <th>brewery_name2</th>
      <th>brewery_type</th>
      <th>name_brewassoc</th>
      <th>name_Gtrends</th>
      <th>FAM</th>
      <th>PARENT</th>
      <th>DUPE</th>
      <th>RETAIN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>302</th>
      <td>Silver</td>
      <td>MÃ©lange A Trois</td>
      <td>Nebraska Brewing Co. - Papillion</td>
      <td>Papillion</td>
      <td>NE</td>
      <td>Wood- and Barrel-Aged Strong Beer</td>
      <td>2016</td>
      <td>2</td>
      <td>nebraska brew</td>
      <td>Brewpub</td>
      <td>Nebraska Brewing Co</td>
      <td>nebraska_brewing</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>303</th>
      <td>Bronze</td>
      <td>15th Anniversary Ale</td>
      <td>Island Brewing Co.</td>
      <td>Carpinteria</td>
      <td>CA</td>
      <td>Wood- and Barrel-Aged Strong Beer</td>
      <td>2016</td>
      <td>1</td>
      <td>island brew</td>
      <td>Micro</td>
      <td>Island Brewing Co</td>
      <td>island_brewing</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>304</th>
      <td>Gold</td>
      <td>Barrel-Aged Darkness</td>
      <td>Surly Brewing Co.</td>
      <td>Brooklyn Center</td>
      <td>MN</td>
      <td>Wood- and Barrel-Aged Strong Stout</td>
      <td>2016</td>
      <td>1</td>
      <td>surly brew</td>
      <td>Regional</td>
      <td>Surly Brewing Company</td>
      <td>surly_brewing</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>305</th>
      <td>Silver</td>
      <td>The Event Horizon</td>
      <td>Olde Hickory Brewery</td>
      <td>Hickory</td>
      <td>NC</td>
      <td>Wood- and Barrel-Aged Strong Stout</td>
      <td>2016</td>
      <td>2</td>
      <td>olde hickory brew</td>
      <td>Micro</td>
      <td>Olde Hickory Brewery - Production</td>
      <td>olde_hickory_brewery</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>306</th>
      <td>Bronze</td>
      <td>Little Nonsense</td>
      <td>Verboten Brewing</td>
      <td>Loveland</td>
      <td>CO</td>
      <td>Wood- and Barrel-Aged Strong Stout</td>
      <td>2016</td>
      <td>1</td>
      <td>verboten brew</td>
      <td>Micro</td>
      <td>Verboten Brewing</td>
      <td>verboten_brewing</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>




```python
gabf16_new[['name_Gtrends', 'state', 'brewery_type', 'medal_cnt']].head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name_Gtrends</th>
      <th>state</th>
      <th>brewery_type</th>
      <th>medal_cnt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>millersburg_brewing</td>
      <td>OH</td>
      <td>Brewpub</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>bells_brewery</td>
      <td>MI</td>
      <td>Regional</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>rubicon_brewing_company_pub</td>
      <td>CA</td>
      <td>n/a</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>the_bruery</td>
      <td>CA</td>
      <td>Micro</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>brown_truck_brewery</td>
      <td>NC</td>
      <td>Micro</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>



## combine craft brewery data


```python
gabf16_eda = pd.merge(gabf16_new[['brewery', 'name_Gtrends', 'state', 'brewery_type', 'medal_cnt']], pre_post_avgs, 
                      left_on='name_Gtrends', right_index=True).drop_duplicates()

print gabf16_eda.shape
gabf16_eda.head()
```

    (249, 8)
    




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brewery</th>
      <th>name_Gtrends</th>
      <th>state</th>
      <th>brewery_type</th>
      <th>medal_cnt</th>
      <th>pre_gabf16</th>
      <th>post_gabf16</th>
      <th>dif_gabf16_norm</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Millersburg Brewing</td>
      <td>millersburg_brewing</td>
      <td>OH</td>
      <td>Brewpub</td>
      <td>1</td>
      <td>2.525773</td>
      <td>2.086957</td>
      <td>0.826264</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bell's Brewery, Inc</td>
      <td>bells_brewery</td>
      <td>MI</td>
      <td>Regional</td>
      <td>1</td>
      <td>18.896907</td>
      <td>15.521739</td>
      <td>0.821390</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Rubicon Brewing Company Pub</td>
      <td>rubicon_brewing_company_pub</td>
      <td>CA</td>
      <td>n/a</td>
      <td>1</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>The Bruery</td>
      <td>the_bruery</td>
      <td>CA</td>
      <td>Micro</td>
      <td>2</td>
      <td>28.855670</td>
      <td>33.478261</td>
      <td>1.160197</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Brown Truck Brewery</td>
      <td>brown_truck_brewery</td>
      <td>NC</td>
      <td>Micro</td>
      <td>3</td>
      <td>3.278351</td>
      <td>9.478261</td>
      <td>2.891167</td>
    </tr>
  </tbody>
</table>
</div>




```python
gabf16_eda['multiple_wins'] = 0
gabf16_eda.loc[gabf16_eda.medal_cnt>1, 'multiple_wins'] = 1

gabf16_eda.multiple_wins.value_counts()
```




    0    220
    1     29
    Name: multiple_wins, dtype: int64




```python
gabf16_eda.pivot_table(index='brewery_type', columns='multiple_wins', values='brewery', aggfunc='count')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>multiple_wins</th>
      <th>0</th>
      <th>1</th>
    </tr>
    <tr>
      <th>brewery_type</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Brewpub</th>
      <td>59.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>Contract</th>
      <td>2.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Large</th>
      <td>6.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>Micro</th>
      <td>127.0</td>
      <td>13.0</td>
    </tr>
    <tr>
      <th>Proprietor</th>
      <td>1.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Regional</th>
      <td>24.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>n/a</th>
      <td>1.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
gabf16_eda.pivot_table(index='brewery_type', columns='multiple_wins', values='dif_gabf16_norm', aggfunc='mean')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>multiple_wins</th>
      <th>0</th>
      <th>1</th>
    </tr>
    <tr>
      <th>brewery_type</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Brewpub</th>
      <td>0.730805</td>
      <td>0.978195</td>
    </tr>
    <tr>
      <th>Contract</th>
      <td>0.519592</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Large</th>
      <td>0.912032</td>
      <td>1.145409</td>
    </tr>
    <tr>
      <th>Micro</th>
      <td>0.940714</td>
      <td>1.083965</td>
    </tr>
    <tr>
      <th>Proprietor</th>
      <td>2.194376</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Regional</th>
      <td>0.774173</td>
      <td>1.130548</td>
    </tr>
    <tr>
      <th>n/a</th>
      <td>0.000000</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



## brewpub, micro, & regional (single and multi wins)


```python
gabf16_eda[(gabf16_eda.multiple_wins==0) & (gabf16_eda.brewery_type=='Brewpub')].nlargest(3,'dif_gabf16_norm')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brewery</th>
      <th>name_Gtrends</th>
      <th>state</th>
      <th>brewery_type</th>
      <th>medal_cnt</th>
      <th>pre_gabf16</th>
      <th>post_gabf16</th>
      <th>dif_gabf16_norm</th>
      <th>multiple_wins</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>86</th>
      <td>12Degree Brewing</td>
      <td>12degree_brewing</td>
      <td>CO</td>
      <td>Brewpub</td>
      <td>1</td>
      <td>0.102369</td>
      <td>0.431731</td>
      <td>4.217350</td>
      <td>0</td>
    </tr>
    <tr>
      <th>301</th>
      <td>Taps Fish House and Brewery - Corona</td>
      <td>taps_fish_house_and_brewery</td>
      <td>CA</td>
      <td>Brewpub</td>
      <td>1</td>
      <td>0.412732</td>
      <td>0.859309</td>
      <td>2.081998</td>
      <td>0</td>
    </tr>
    <tr>
      <th>122</th>
      <td>Pizza Port San Clemente</td>
      <td>pizza_port_san_clemente</td>
      <td>CA</td>
      <td>Brewpub</td>
      <td>1</td>
      <td>0.472705</td>
      <td>0.926952</td>
      <td>1.960948</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
gabf16_eda[(gabf16_eda.multiple_wins==0) & (gabf16_eda.brewery_type=='Micro')].nlargest(3,'dif_gabf16_norm')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brewery</th>
      <th>name_Gtrends</th>
      <th>state</th>
      <th>brewery_type</th>
      <th>medal_cnt</th>
      <th>pre_gabf16</th>
      <th>post_gabf16</th>
      <th>dif_gabf16_norm</th>
      <th>multiple_wins</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>202</th>
      <td>Hardywood Park Craft Brewery</td>
      <td>hardywood_park_craft_brewery</td>
      <td>VA</td>
      <td>Micro</td>
      <td>1</td>
      <td>0.785911</td>
      <td>4.326285</td>
      <td>5.504798</td>
      <td>0</td>
    </tr>
    <tr>
      <th>101</th>
      <td>Ardent Craft Ales</td>
      <td>ardent_craft_ales</td>
      <td>VA</td>
      <td>Micro</td>
      <td>1</td>
      <td>0.456800</td>
      <td>2.288627</td>
      <td>5.010123</td>
      <td>0</td>
    </tr>
    <tr>
      <th>80</th>
      <td>Logsdon Farmhouse Ales</td>
      <td>logsdon_farmhouse_ales</td>
      <td>OR</td>
      <td>Micro</td>
      <td>1</td>
      <td>0.337216</td>
      <td>1.345986</td>
      <td>3.991448</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
gabf16_eda[(gabf16_eda.multiple_wins==0) & (gabf16_eda.brewery_type=='Regional')].nlargest(3,'dif_gabf16_norm')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brewery</th>
      <th>name_Gtrends</th>
      <th>state</th>
      <th>brewery_type</th>
      <th>medal_cnt</th>
      <th>pre_gabf16</th>
      <th>post_gabf16</th>
      <th>dif_gabf16_norm</th>
      <th>multiple_wins</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>81</th>
      <td>Two Roads Brewing Co.</td>
      <td>two_roads_brewing</td>
      <td>CT</td>
      <td>Regional</td>
      <td>1</td>
      <td>9.442060</td>
      <td>12.075778</td>
      <td>1.278935</td>
      <td>0</td>
    </tr>
    <tr>
      <th>304</th>
      <td>Surly Brewing Co.</td>
      <td>surly_brewing</td>
      <td>MN</td>
      <td>Regional</td>
      <td>1</td>
      <td>15.677050</td>
      <td>17.159652</td>
      <td>1.094571</td>
      <td>0</td>
    </tr>
    <tr>
      <th>79</th>
      <td>Sun King Brewing Co.</td>
      <td>sun_king_brewing</td>
      <td>IN</td>
      <td>Regional</td>
      <td>1</td>
      <td>6.952078</td>
      <td>7.491808</td>
      <td>1.077636</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
gabf16_eda[(gabf16_eda.multiple_wins==1) & (gabf16_eda.brewery_type=='Brewpub')].nlargest(3,'dif_gabf16_norm')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brewery</th>
      <th>name_Gtrends</th>
      <th>state</th>
      <th>brewery_type</th>
      <th>medal_cnt</th>
      <th>pre_gabf16</th>
      <th>post_gabf16</th>
      <th>dif_gabf16_norm</th>
      <th>multiple_wins</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>109</th>
      <td>ZwanzigZ Brewing</td>
      <td>zwanzigz_brewing</td>
      <td>IN</td>
      <td>Brewpub</td>
      <td>2</td>
      <td>0.117996</td>
      <td>0.559839</td>
      <td>4.744525</td>
      <td>1</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Uberbrew</td>
      <td>uberbrew</td>
      <td>MT</td>
      <td>Brewpub</td>
      <td>4</td>
      <td>1.152701</td>
      <td>1.283407</td>
      <td>1.113390</td>
      <td>1</td>
    </tr>
    <tr>
      <th>76</th>
      <td>Nebraska Brewing Co. - Papillion</td>
      <td>nebraska_brewing</td>
      <td>NE</td>
      <td>Brewpub</td>
      <td>2</td>
      <td>12.617107</td>
      <td>12.913848</td>
      <td>1.023519</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
gabf16_eda[(gabf16_eda.multiple_wins==1) & (gabf16_eda.brewery_type=='Micro')].nlargest(3,'dif_gabf16_norm')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brewery</th>
      <th>name_Gtrends</th>
      <th>state</th>
      <th>brewery_type</th>
      <th>medal_cnt</th>
      <th>pre_gabf16</th>
      <th>post_gabf16</th>
      <th>dif_gabf16_norm</th>
      <th>multiple_wins</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>71</th>
      <td>2SP Brewing Co.</td>
      <td>2sp_brewing</td>
      <td>PA</td>
      <td>Micro</td>
      <td>2</td>
      <td>1.755364</td>
      <td>6.395837</td>
      <td>3.643594</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Brown Truck Brewery</td>
      <td>brown_truck_brewery</td>
      <td>NC</td>
      <td>Micro</td>
      <td>3</td>
      <td>3.278351</td>
      <td>9.478261</td>
      <td>2.891167</td>
      <td>1</td>
    </tr>
    <tr>
      <th>275</th>
      <td>Neshaminy Creek Brewing Co.</td>
      <td>neshaminy_creek_brewing</td>
      <td>PA</td>
      <td>Micro</td>
      <td>2</td>
      <td>3.785876</td>
      <td>4.727902</td>
      <td>1.248826</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
gabf16_eda[(gabf16_eda.multiple_wins==1) & (gabf16_eda.brewery_type=='Regional')].nlargest(3,'dif_gabf16_norm')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brewery</th>
      <th>name_Gtrends</th>
      <th>state</th>
      <th>brewery_type</th>
      <th>medal_cnt</th>
      <th>pre_gabf16</th>
      <th>post_gabf16</th>
      <th>dif_gabf16_norm</th>
      <th>multiple_wins</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>26</th>
      <td>Georgetown Brewing Co.</td>
      <td>georgetown_brewing</td>
      <td>WA</td>
      <td>Regional</td>
      <td>2</td>
      <td>2.236994</td>
      <td>4.012087</td>
      <td>1.793516</td>
      <td>1</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Fat Head's Brewery</td>
      <td>fat_heads_brewery</td>
      <td>OH</td>
      <td>Regional</td>
      <td>2</td>
      <td>3.218342</td>
      <td>3.636321</td>
      <td>1.129874</td>
      <td>1</td>
    </tr>
    <tr>
      <th>41</th>
      <td>Karl Strauss Brewing Co. - San Diego</td>
      <td>karl_strauss_brewing</td>
      <td>CA</td>
      <td>Regional</td>
      <td>3</td>
      <td>6.549709</td>
      <td>5.653187</td>
      <td>0.863120</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



## select a few from above

- definitely want a CA, CO, OR, & WA... so:
    * CA: taps_fish_house_and_brewery (brewpub, 1)
    * CO: 12degree_brewing (brewpub, 1)
    * OR: logsdon_farmhouse_ales (mirco, 1)
    * WA: georgetown_brewing (regional, 2)


- some compliments:
    * uberbrew (MT; brewpub, 4 wins!)
    * hardywood_park_craft_brewery (VA; micro, 1; largest post GABF uptick!)
    * brown_truck_brewery (NC; micro, 3; the joining brewery, why not?)
    

## find comparable (type & state) non-GABF16 winners


```python
brw_assoc = pd.read_csv('comp_breweries/brw_assoc_usa_gabf16.csv', sep=';', index_col=0)

print brw_assoc.shape
brw_assoc.head()
```

    (7429, 12)
    




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>brewery_type</th>
      <th>address</th>
      <th>city</th>
      <th>state</th>
      <th>z_code</th>
      <th>ownership</th>
      <th>telephone</th>
      <th>url</th>
      <th>brewery_name2</th>
      <th>name_short</th>
      <th>gabf16_win</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Bradley Farm / RB Brew, LLC</td>
      <td>Micro</td>
      <td>317 Springtown Rd</td>
      <td>New Paltz</td>
      <td>NY</td>
      <td>12561-3020</td>
      <td>NaN</td>
      <td>(845) 255-8769</td>
      <td>www.raybradleyfarm.com</td>
      <td>bradley farm / rb brew</td>
      <td>Bradley Farm</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Kona Brewing Co</td>
      <td>Regional</td>
      <td>74-5612 Pawai Pl</td>
      <td>Kailua Kona</td>
      <td>HI</td>
      <td>96740-</td>
      <td>Greater than 25% ownership by Anheuser-Busch I...</td>
      <td>(808) 334-1133</td>
      <td>www.konabrewingco.com</td>
      <td>kona brew</td>
      <td>Kona Brewing</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>(405) Brewing Co</td>
      <td>Micro</td>
      <td>1716 Topeka St</td>
      <td>Norman</td>
      <td>OK</td>
      <td>73069-8224</td>
      <td>NaN</td>
      <td>(405) 816-0490</td>
      <td>www.405brewing.com</td>
      <td>(405) brew</td>
      <td>(405) Brewing</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>(512) Brewing Co</td>
      <td>Micro</td>
      <td>407 Radam Ln Ste F200</td>
      <td>Austin</td>
      <td>TX</td>
      <td>78745-1197</td>
      <td>NaN</td>
      <td>(512) 921-1545</td>
      <td>www.512brewing.com</td>
      <td>(512) brew</td>
      <td>(512) Brewing</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10 Barrel Brewing Co</td>
      <td>Large</td>
      <td>62970 18th St</td>
      <td>Bend</td>
      <td>OR</td>
      <td>97701-9847</td>
      <td>Greater than 25% ownership by Anheuser-Busch I...</td>
      <td>(541) 585-1007</td>
      <td>www.10barrel.com</td>
      <td>10 barrel brew</td>
      <td>10 Barrel</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
brewery_combos = [('CA', 'Brewpub'), ('CO', 'Brewpub'), ('OR', 'Micro'), ('WA', 'Regional'),
                  ('MT', 'Brewpub'), ('VA', 'Micro'), ('NC', 'Micro')
                  ]
```


```python
np.random.seed(8)

for combo in brewery_combos:
    candidates = brw_assoc[(brw_assoc.state==combo[0]) & 
                           (brw_assoc.brewery_type==combo[1]) & 
                           (brw_assoc.gabf16_win==0)
                          ]['name']
    print combo
    print np.random.choice(candidates, 4, replace=False), '\n'
```

    ('CA', 'Brewpub')
    ['Downtown Joes Brewery and Restaurant' 'Taplands Brewery'
     'Woods Bar & Brewery' 'Miner\xe2\x80\x99s Alley Brewing Company'] 
    
    ('CO', 'Brewpub')
    ['Oskar Blues Brewery - Lyons' 'Whistle Pig Brewing Company'
     'Brix Taphouse and Brewery' 'Moonlight Pizza'] 
    
    ('OR', 'Micro')
    ['Mazama Brewing Co' 'Siuslaw Brewing'
     "Krauski's Brewskis / The Hoppy Brewer" 'Red Ox Brewing'] 
    
    ('WA', 'Regional')
    ['Fremont Brewing Co' 'Redhook Brewery' 'Mac and Jacks Brewery Inc'
     'Iron Horse Brewery'] 
    
    ('MT', 'Brewpub')
    ['Bridger Brewing Company' 'Cabinet Mountain Brewing Co'
     'The Front Brewing Company' 'Backslope Brewing '] 
    
    ('VA', 'Micro')
    ['Lickinghole Creek Craft Brewery' 'Barrel Oak Farm Taphouse'
     'Sunken City Brewing Co' 'New District Brewing Company'] 
    
    ('NC', 'Micro')
    ['Good Hops Brewing LLC' 'Preyer Brewing Company'
     'Fortnight Brewing Company' 'Burial Beer Co Forestry Camp'] 
    
    

## some last minute eda by segment


```python
single_medals = gabf16_new[gabf16_new.medal_cnt==1][['brewery', 'name_Gtrends', 'state', 'brewery_type', 'medal', 'category']]
single_medals.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brewery</th>
      <th>name_Gtrends</th>
      <th>state</th>
      <th>brewery_type</th>
      <th>medal</th>
      <th>category</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Millersburg Brewing</td>
      <td>millersburg_brewing</td>
      <td>OH</td>
      <td>Brewpub</td>
      <td>Gold</td>
      <td>Aged Beer</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bell's Brewery, Inc</td>
      <td>bells_brewery</td>
      <td>MI</td>
      <td>Regional</td>
      <td>Silver</td>
      <td>Aged Beer</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Rubicon Brewing Company Pub</td>
      <td>rubicon_brewing_company_pub</td>
      <td>CA</td>
      <td>n/a</td>
      <td>Bronze</td>
      <td>Aged Beer</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Crank Arm Brewing Co.</td>
      <td>crank_arm_brewing</td>
      <td>NC</td>
      <td>Micro</td>
      <td>Bronze</td>
      <td>American-Belgo-Style Ale</td>
    </tr>
    <tr>
      <th>6</th>
      <td>El Segundo Brewing Co.</td>
      <td>el_segundo_brewing</td>
      <td>CA</td>
      <td>Micro</td>
      <td>Gold</td>
      <td>American-Style Amber Lager or Dark Lager</td>
    </tr>
  </tbody>
</table>
</div>




```python
gold = [s for s in single_medals[single_medals.medal=='Gold']['name_Gtrends'].tolist() if s != u'n/a']
mean_idx_trends[gold].plot(legend=False, figsize=(16, 8))
plt.title('Gold Medal Brewery Search Hits (indexed)')
plt.ylabel('relative to own avg')
```




    <matplotlib.text.Text at 0xf84a748>




<img src = "/code/brown_truck_join/output_55_1.png">



```python
silver = [s for s in single_medals[single_medals.medal=='Silver']['name_Gtrends'].tolist() if s != u'n/a']
mean_idx_trends[silver].plot(legend=False, figsize=(16, 8))
plt.title('Silver Medal Brewery Search Hits (indexed)')
plt.ylabel('relative to own avg')
```




    <matplotlib.text.Text at 0xfbf3208>




<img src = "/code/brown_truck_join/output_56_1.png">



```python
bronze = [s for s in single_medals[single_medals.medal=='Bronze']['name_Gtrends'].tolist() if s != u'n/a']
mean_idx_trends[bronze].plot(legend=False, figsize=(16, 8))
plt.title('Bronze Medal Brewery Search Hits (indexed)')
plt.ylabel('relative to own avg')
```




    <matplotlib.text.Text at 0x10f0ecc0>




<img src = "/code/brown_truck_join/output_57_1.png">


## IQR by medal (single medal winners)


```python
mean_idx_trends[gold].sum(axis=1)[pre_gabf16].describe(), mean_idx_trends[gold].sum(axis=1)[post_gabf16].describe()
```




    (count     97.000000
     mean      57.907986
     std       17.754784
     min       32.077572
     25%       45.378124
     50%       52.536740
     75%       66.628534
     max      112.251168
     dtype: float64, count    23.000000
     mean     57.466237
     std      18.771940
     min      24.325076
     25%      45.764013
     50%      58.324900
     75%      72.582052
     max      98.950253
     dtype: float64)




```python
mean_idx_trends[silver].sum(axis=1)[pre_gabf16].describe(), mean_idx_trends[silver].sum(axis=1)[post_gabf16].describe()
```




    (count     97.000000
     mean      60.439844
     std       22.552839
     min       28.589938
     25%       45.640806
     50%       56.970620
     75%       70.268552
     max      195.875898
     dtype: float64, count    23.000000
     mean     57.492863
     std      14.953135
     min      30.036341
     25%      47.732232
     50%      61.927325
     75%      69.956782
     max      80.223873
     dtype: float64)




```python
mean_idx_trends[bronze].sum(axis=1)[pre_gabf16].describe(), mean_idx_trends[bronze].sum(axis=1)[post_gabf16].describe()
```




    (count     97.000000
     mean      62.787726
     std       22.994400
     min       27.376774
     25%       46.681124
     50%       57.716062
     75%       70.865554
     max      145.357013
     dtype: float64, count    23.000000
     mean     60.411436
     std      17.978898
     min      29.892762
     25%      47.813260
     50%      60.287267
     75%      68.125172
     max      97.718445
     dtype: float64)




```python
single_medals_idx = pd.DataFrame({'gold': mean_idx_trends[gold].sum(axis=1),
                                  'silver': mean_idx_trends[silver].sum(axis=1),
                                  'bronze': mean_idx_trends[bronze].sum(axis=1),
                                  'gabf': 'GABF'
                                 })

single_medals_idx.loc[pre_gabf16, 'gabf']  = 'pre'
single_medals_idx.loc[post_gabf16, 'gabf']  = 'post'
single_medals_idx = single_medals_idx[['gold', 'silver', 'bronze', 'gabf']]

single_medals_idx.tail()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>gold</th>
      <th>silver</th>
      <th>bronze</th>
      <th>gabf</th>
    </tr>
    <tr>
      <th>Day</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-10-27</th>
      <td>36.031479</td>
      <td>51.258344</td>
      <td>60.137878</td>
      <td>post</td>
    </tr>
    <tr>
      <th>2016-10-28</th>
      <td>52.193937</td>
      <td>79.114118</td>
      <td>60.287267</td>
      <td>post</td>
    </tr>
    <tr>
      <th>2016-10-29</th>
      <td>83.409933</td>
      <td>64.636172</td>
      <td>67.456476</td>
      <td>post</td>
    </tr>
    <tr>
      <th>2016-10-30</th>
      <td>46.589409</td>
      <td>63.336685</td>
      <td>33.481906</td>
      <td>post</td>
    </tr>
    <tr>
      <th>2016-10-31</th>
      <td>46.590061</td>
      <td>59.287918</td>
      <td>54.354502</td>
      <td>post</td>
    </tr>
  </tbody>
</table>
</div>




```python
import seaborn as sns
sns.set_style("whitegrid")
```


```python
df = single_medals_idx[single_medals_idx.gabf!='GABF'].set_index('gabf', append=True).stack().to_frame().reset_index()\
.rename(columns={'level_2': 'medal', 0: 'value'}) 

df.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Day</th>
      <th>gabf</th>
      <th>medal</th>
      <th>value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2016-07-01</td>
      <td>pre</td>
      <td>gold</td>
      <td>87.037179</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2016-07-01</td>
      <td>pre</td>
      <td>silver</td>
      <td>88.758016</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016-07-01</td>
      <td>pre</td>
      <td>bronze</td>
      <td>65.273149</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2016-07-02</td>
      <td>pre</td>
      <td>gold</td>
      <td>103.857065</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2016-07-02</td>
      <td>pre</td>
      <td>silver</td>
      <td>59.777300</td>
    </tr>
  </tbody>
</table>
</div>




```python
fig, ax = plt.subplots()
fig.set_size_inches(11.7, 8.27)
sns.boxplot(x='medal', y='value', hue='gabf', data=df, palette="Set3")

sns.despine(trim=True)

```


<img src = "/code/brown_truck_join/output_65_0.png">


## misc


```python
pre_post_avgs.sort_values('dif_gabf16_norm', ascending=False)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pre_gabf16</th>
      <th>post_gabf16</th>
      <th>dif_gabf16_norm</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>hardywood_park_craft_brewery</th>
      <td>0.785911</td>
      <td>4.326285</td>
      <td>5.504798</td>
    </tr>
    <tr>
      <th>ardent_craft_ales</th>
      <td>0.456800</td>
      <td>2.288627</td>
      <td>5.010123</td>
    </tr>
    <tr>
      <th>zwanzigz_brewing</th>
      <td>0.117996</td>
      <td>0.559839</td>
      <td>4.744525</td>
    </tr>
    <tr>
      <th>12degree_brewing</th>
      <td>0.102369</td>
      <td>0.431731</td>
      <td>4.217350</td>
    </tr>
    <tr>
      <th>logsdon_farmhouse_ales</th>
      <td>0.337216</td>
      <td>1.345986</td>
      <td>3.991448</td>
    </tr>
    <tr>
      <th>2sp_brewing</th>
      <td>1.755364</td>
      <td>6.395837</td>
      <td>3.643594</td>
    </tr>
    <tr>
      <th>solid_rock_brewing</th>
      <td>0.443389</td>
      <td>1.376959</td>
      <td>3.105527</td>
    </tr>
    <tr>
      <th>brown_truck_brewery</th>
      <td>3.278351</td>
      <td>9.478261</td>
      <td>2.891167</td>
    </tr>
    <tr>
      <th>gibbs_hundred_brewing</th>
      <td>0.398042</td>
      <td>1.091153</td>
      <td>2.741297</td>
    </tr>
    <tr>
      <th>hi-wire_brewing</th>
      <td>0.676520</td>
      <td>1.830562</td>
      <td>2.705844</td>
    </tr>
    <tr>
      <th>14er_brewing</th>
      <td>1.291659</td>
      <td>3.212589</td>
      <td>2.487178</td>
    </tr>
    <tr>
      <th>blackberry_farm_brewery</th>
      <td>1.422047</td>
      <td>3.246674</td>
      <td>2.283097</td>
    </tr>
    <tr>
      <th>high_water_brewing</th>
      <td>3.014830</td>
      <td>6.615672</td>
      <td>2.194376</td>
    </tr>
    <tr>
      <th>taps_fish_house_and_brewery</th>
      <td>0.412732</td>
      <td>0.859309</td>
      <td>2.081998</td>
    </tr>
    <tr>
      <th>second_chance_beer</th>
      <td>1.447585</td>
      <td>2.986046</td>
      <td>2.062776</td>
    </tr>
    <tr>
      <th>riip_beer</th>
      <td>1.229949</td>
      <td>2.450898</td>
      <td>1.992682</td>
    </tr>
    <tr>
      <th>pizza_port_san_clemente</th>
      <td>0.472705</td>
      <td>0.926952</td>
      <td>1.960948</td>
    </tr>
    <tr>
      <th>verboten_brewing</th>
      <td>1.848623</td>
      <td>3.439574</td>
      <td>1.860613</td>
    </tr>
    <tr>
      <th>slo_brew</th>
      <td>2.113737</td>
      <td>3.836893</td>
      <td>1.815217</td>
    </tr>
    <tr>
      <th>spencer_devon_brewing</th>
      <td>1.122478</td>
      <td>2.014437</td>
      <td>1.794633</td>
    </tr>
    <tr>
      <th>georgetown_brewing</th>
      <td>2.236994</td>
      <td>4.012087</td>
      <td>1.793516</td>
    </tr>
    <tr>
      <th>la_cumbre_brewing</th>
      <td>2.591634</td>
      <td>4.635861</td>
      <td>1.788779</td>
    </tr>
    <tr>
      <th>daredevil_brewing</th>
      <td>1.829192</td>
      <td>3.206119</td>
      <td>1.752751</td>
    </tr>
    <tr>
      <th>propolis_brewing</th>
      <td>1.460230</td>
      <td>2.514240</td>
      <td>1.721810</td>
    </tr>
    <tr>
      <th>alvarado_street_brewery</th>
      <td>5.433718</td>
      <td>9.260751</td>
      <td>1.704312</td>
    </tr>
    <tr>
      <th>pollyanna_brewing</th>
      <td>1.975679</td>
      <td>3.269762</td>
      <td>1.655006</td>
    </tr>
    <tr>
      <th>4_noses_brewing</th>
      <td>0.783885</td>
      <td>1.272879</td>
      <td>1.623806</td>
    </tr>
    <tr>
      <th>morgan_territory_brewing</th>
      <td>0.494651</td>
      <td>0.784530</td>
      <td>1.586024</td>
    </tr>
    <tr>
      <th>echo_brewing</th>
      <td>4.451411</td>
      <td>6.996020</td>
      <td>1.571641</td>
    </tr>
    <tr>
      <th>revolver_brewing</th>
      <td>9.335360</td>
      <td>14.266856</td>
      <td>1.528260</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>altitude_chophouse_and_brewery</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>missoula_brewing</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>two_kilts_brewing</th>
      <td>0.111016</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>high_heel_brewing</th>
      <td>0.501533</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>ram/big_horn_brewery</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>the_packinghouse_brewing</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>coopersmiths_pub_&amp;_brewing</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>bns_brewing_&amp;_distilling</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>no_clue_craft_brewery</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>emmetts_tavern_&amp;_brewing</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>black_tooth_brewing</th>
      <td>1.152725</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>iron_springs_pub_&amp;_brewery</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>colorado_boy_pub</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>brewers_alley_restaurant_&amp;_brewery</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>redwood_curtain_brewing</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>horse_thief_hollow_brewery</th>
      <td>0.569610</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>ghostfish_brewing_company</th>
      <td>0.097172</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>fiction_beer</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>philipsburg_brewing</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>three_creeks_production</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>alesong_brewing_&amp;_blending</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>hop_dogma_brewing</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>swamp_rabbit_brewery_&amp;_taproom</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>glenwood_canyon_brewing</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>kootenai_river_brewing</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>greenview_brewing</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>big_dogs_brewing</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>rivers_edge_brewing</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>maize_valley_craft_brewery</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>grimm_brothers_brewhouse</th>
      <td>0.518925</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
  </tbody>
</table>
<p>242 rows × 3 columns</p>
</div>




```python

```
