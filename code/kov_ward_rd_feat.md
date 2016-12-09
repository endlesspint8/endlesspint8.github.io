---
layout: page
title: endlesspint
subtitle: Kovalev Ward I - Round Features and Judge Scoring
---



```python
import csv, os, json
import numpy as np
import pandas as pd
print pd.__version__

from datetime import datetime

from collections import Counter, defaultdict

import matplotlib.pyplot as plt
import matplotlib
matplotlib.style.use('ggplot')
%matplotlib inline
```

    0.18.0
    

## import round stats and scoring (wide table)


```python
# CompuBox stats
kov_ward_bout = pd.read_excel('data/compubox_stats.xlsx', sheetname='Sheet3')

kov_ward_bout
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>round</th>
      <th>kov_pun_land</th>
      <th>kov_pun_thrw</th>
      <th>kov_pun_perc</th>
      <th>kov_jab_land</th>
      <th>kov_jab_thrw</th>
      <th>kov_jab_perc</th>
      <th>kov_pow_land</th>
      <th>kov_pow_thrw</th>
      <th>kov_pow_perc</th>
      <th>...</th>
      <th>ward_jab_land</th>
      <th>ward_jab_thrw</th>
      <th>ward_jab_perc</th>
      <th>ward_pow_land</th>
      <th>ward_pow_thrw</th>
      <th>ward_pow_perc</th>
      <th>kov_kdwns</th>
      <th>white</th>
      <th>blue</th>
      <th>pink</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>7</td>
      <td>34</td>
      <td>0.205882</td>
      <td>4</td>
      <td>22</td>
      <td>0.181818</td>
      <td>3</td>
      <td>12</td>
      <td>0.250000</td>
      <td>...</td>
      <td>4</td>
      <td>13</td>
      <td>0.307692</td>
      <td>1</td>
      <td>7</td>
      <td>0.142857</td>
      <td>0</td>
      <td>kov</td>
      <td>kov</td>
      <td>kov</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>16</td>
      <td>49</td>
      <td>0.326531</td>
      <td>5</td>
      <td>23</td>
      <td>0.217391</td>
      <td>11</td>
      <td>26</td>
      <td>0.423077</td>
      <td>...</td>
      <td>3</td>
      <td>12</td>
      <td>0.250000</td>
      <td>0</td>
      <td>4</td>
      <td>0.000000</td>
      <td>1</td>
      <td>kov</td>
      <td>kov</td>
      <td>kov</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4</td>
      <td>27</td>
      <td>0.148148</td>
      <td>2</td>
      <td>15</td>
      <td>0.133333</td>
      <td>2</td>
      <td>12</td>
      <td>0.166667</td>
      <td>...</td>
      <td>2</td>
      <td>12</td>
      <td>0.166667</td>
      <td>3</td>
      <td>10</td>
      <td>0.300000</td>
      <td>0</td>
      <td>kov</td>
      <td>kov</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>9</td>
      <td>37</td>
      <td>0.243243</td>
      <td>3</td>
      <td>22</td>
      <td>0.136364</td>
      <td>6</td>
      <td>15</td>
      <td>0.400000</td>
      <td>...</td>
      <td>4</td>
      <td>14</td>
      <td>0.285714</td>
      <td>3</td>
      <td>11</td>
      <td>0.272727</td>
      <td>0</td>
      <td>kov</td>
      <td>kov</td>
      <td>kov</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>7</td>
      <td>33</td>
      <td>0.212121</td>
      <td>3</td>
      <td>17</td>
      <td>0.176471</td>
      <td>4</td>
      <td>16</td>
      <td>0.250000</td>
      <td>...</td>
      <td>3</td>
      <td>10</td>
      <td>0.300000</td>
      <td>5</td>
      <td>14</td>
      <td>0.357143</td>
      <td>0</td>
      <td>ward</td>
      <td>ward</td>
      <td>kov</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>9</td>
      <td>36</td>
      <td>0.250000</td>
      <td>3</td>
      <td>17</td>
      <td>0.176471</td>
      <td>6</td>
      <td>19</td>
      <td>0.315789</td>
      <td>...</td>
      <td>5</td>
      <td>13</td>
      <td>0.384615</td>
      <td>3</td>
      <td>12</td>
      <td>0.250000</td>
      <td>0</td>
      <td>kov</td>
      <td>ward</td>
      <td>kov</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>7</td>
      <td>29</td>
      <td>0.241379</td>
      <td>1</td>
      <td>10</td>
      <td>0.100000</td>
      <td>6</td>
      <td>19</td>
      <td>0.315789</td>
      <td>...</td>
      <td>6</td>
      <td>12</td>
      <td>0.500000</td>
      <td>5</td>
      <td>20</td>
      <td>0.250000</td>
      <td>0</td>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>10</td>
      <td>38</td>
      <td>0.263158</td>
      <td>4</td>
      <td>20</td>
      <td>0.200000</td>
      <td>6</td>
      <td>18</td>
      <td>0.333333</td>
      <td>...</td>
      <td>1</td>
      <td>12</td>
      <td>0.083333</td>
      <td>10</td>
      <td>20</td>
      <td>0.500000</td>
      <td>0</td>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>11</td>
      <td>46</td>
      <td>0.239130</td>
      <td>4</td>
      <td>22</td>
      <td>0.181818</td>
      <td>7</td>
      <td>24</td>
      <td>0.291667</td>
      <td>...</td>
      <td>8</td>
      <td>20</td>
      <td>0.400000</td>
      <td>9</td>
      <td>18</td>
      <td>0.500000</td>
      <td>0</td>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>21</td>
      <td>58</td>
      <td>0.362069</td>
      <td>11</td>
      <td>33</td>
      <td>0.333333</td>
      <td>10</td>
      <td>25</td>
      <td>0.400000</td>
      <td>...</td>
      <td>9</td>
      <td>23</td>
      <td>0.391304</td>
      <td>7</td>
      <td>12</td>
      <td>0.583333</td>
      <td>0</td>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>10</th>
      <td>11</td>
      <td>12</td>
      <td>40</td>
      <td>0.300000</td>
      <td>5</td>
      <td>22</td>
      <td>0.227273</td>
      <td>7</td>
      <td>18</td>
      <td>0.388889</td>
      <td>...</td>
      <td>9</td>
      <td>15</td>
      <td>0.600000</td>
      <td>4</td>
      <td>11</td>
      <td>0.363636</td>
      <td>0</td>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>11</th>
      <td>12</td>
      <td>13</td>
      <td>47</td>
      <td>0.276596</td>
      <td>3</td>
      <td>19</td>
      <td>0.157895</td>
      <td>10</td>
      <td>28</td>
      <td>0.357143</td>
      <td>...</td>
      <td>1</td>
      <td>12</td>
      <td>0.083333</td>
      <td>11</td>
      <td>30</td>
      <td>0.366667</td>
      <td>0</td>
      <td>ward</td>
      <td>kov</td>
      <td>ward</td>
    </tr>
  </tbody>
</table>
<p>12 rows × 23 columns</p>
</div>




```python
kov_ward_bout['winner'] = 'split'

kov_ward_bout.loc[((kov_ward_bout.white=='kov') & 
                   (kov_ward_bout.blue=='kov') & 
                   (kov_ward_bout.pink=='kov')), 'winner' ] = 'kov'

kov_ward_bout.loc[((kov_ward_bout.white=='ward') & 
                  (kov_ward_bout.blue=='ward') & 
                  (kov_ward_bout.pink=='ward')), 'winner' ] = 'ward'

kov_ward_bout[['white', 'blue', 'pink', 'winner']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>white</th>
      <th>blue</th>
      <th>pink</th>
      <th>winner</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>kov</td>
      <td>kov</td>
      <td>kov</td>
      <td>kov</td>
    </tr>
    <tr>
      <th>1</th>
      <td>kov</td>
      <td>kov</td>
      <td>kov</td>
      <td>kov</td>
    </tr>
    <tr>
      <th>2</th>
      <td>kov</td>
      <td>kov</td>
      <td>ward</td>
      <td>split</td>
    </tr>
    <tr>
      <th>3</th>
      <td>kov</td>
      <td>kov</td>
      <td>kov</td>
      <td>kov</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ward</td>
      <td>ward</td>
      <td>kov</td>
      <td>split</td>
    </tr>
    <tr>
      <th>5</th>
      <td>kov</td>
      <td>ward</td>
      <td>kov</td>
      <td>split</td>
    </tr>
    <tr>
      <th>6</th>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>7</th>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>8</th>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>9</th>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>10</th>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>11</th>
      <td>ward</td>
      <td>kov</td>
      <td>ward</td>
      <td>split</td>
    </tr>
  </tbody>
</table>
</div>



## exploratory vis analysis


```python
nrows=2; ncols=3
fig, axes = plt.subplots(nrows=nrows, ncols=ncols, figsize=(16,10))

x = [-5, 50]; y = [-5, 50]

kov_ward_bout.plot.scatter('ward_jab_land', 'kov_jab_land', ax=axes[0,0])
axes[0,0].set_title('jabs')
axes[0,0].set_xlim([-1,12])
axes[0,0].set_ylim([-1,12])

kov_ward_bout.plot.scatter('ward_pow_land', 'kov_pow_land', ax=axes[0,1])
axes[0,1].set_title('power')
axes[0,1].set_xlim([-1,12])
axes[0,1].set_ylim([-1,12])
kov_ward_bout.plot.scatter('ward_pun_land', 'kov_pun_land', ax=axes[0,2])
axes[0,2].set_title('total')
axes[0,2].set_xlim([-1,24])
axes[0,2].set_ylim([-1,24])

kov_ward_bout.plot.scatter('ward_jab_perc', 'kov_jab_perc', ax=axes[1,0])
axes[1,0].set_xlim([-0.05,.65])
axes[1,0].set_ylim([-0.05,.65])
kov_ward_bout.plot.scatter('ward_pow_perc', 'kov_pow_perc', ax=axes[1,1])
axes[1,1].set_xlim([-0.05,.65])
axes[1,1].set_ylim([-0.05,.65])
kov_ward_bout.plot.scatter('ward_pun_perc', 'kov_pun_perc', ax=axes[1,2])
axes[1,2].set_xlim([-0.05,.65])
axes[1,2].set_ylim([-0.05,.65])
axes[1,2].text(0.6, 0., 'endlesspint.com',
               fontsize=12, color='gray',
               ha='right', va='bottom', alpha=0.3)

for row in range(nrows):
    for col in range(ncols):
        axes[row, col].set_aspect('equal')
        axes[row, col].plot(x,y,'--')
        axes[row, col].grid(False, which='both')
        
### save file localy w high resolution
# plt.savefig('img/fight_hour_tweets.PNG', dpi=1200)
```


<img src = "/code/kov_ward_rd_feat/output_5_0.png"  >


## same as above but with dots colored by round winner/split


```python
nrows=2; ncols=3
fig, axes = plt.subplots(nrows=nrows, ncols=ncols, figsize=(16,10))

x_line = [-5, 50]; y_line = [-5, 50]

kov_ward_bout[kov_ward_bout.winner=='kov'].plot.scatter('ward_jab_land', 'kov_jab_land', ax=axes[0,0], c='r', s=50)
kov_ward_bout[kov_ward_bout.winner=='ward'].plot.scatter('ward_jab_land', 'kov_jab_land', ax=axes[0,0], c='b', s=50)
kov_ward_bout[kov_ward_bout.winner=='split'].plot.scatter('ward_jab_land', 'kov_jab_land', ax=axes[0,0], c='g', s=50)
axes[0,0].set_title('jabs')
axes[0,0].set_xlim([-1,12]); axes[0,0].set_ylim([-1,12])
axes[0,0].set_xlabel(''); axes[0,0].set_ylabel('Kovalev')

kov_ward_bout[kov_ward_bout.winner=='kov'].plot.scatter('ward_pow_land', 'kov_pow_land', ax=axes[0,1], c='r', s=50)
kov_ward_bout[kov_ward_bout.winner=='ward'].plot.scatter('ward_pow_land', 'kov_pow_land', ax=axes[0,1], c='b', s=50)
kov_ward_bout[kov_ward_bout.winner=='split'].plot.scatter('ward_pow_land', 'kov_pow_land', ax=axes[0,1], c='g', s=50)
axes[0,1].set_title('power punches')
axes[0,1].set_xlim([-1,12]); axes[0,1].set_ylim([-1,12])
axes[0,1].set_xlabel(''); axes[0,1].set_ylabel('')

kov_ward_bout[kov_ward_bout.winner=='kov'].plot.scatter('ward_pun_land', 'kov_pun_land', ax=axes[0,2], c='r', s=50)
kov_ward_bout[kov_ward_bout.winner=='ward'].plot.scatter('ward_pun_land', 'kov_pun_land', ax=axes[0,2], c='b', s=50)
kov_ward_bout[kov_ward_bout.winner=='split'].plot.scatter('ward_pun_land', 'kov_pun_land', ax=axes[0,2], c='g', s=50)
axes[0,2].set_title('total')
axes[0,2].set_xlim([-1,24]); axes[0,2].set_ylim([-1,24])
axes[0,2].set_xlabel(''); axes[0,2].set_ylabel('')

kov_ward_bout[kov_ward_bout.winner=='kov'].plot.scatter('ward_jab_perc', 'kov_jab_perc', ax=axes[1,0], c='r', s=50)
kov_ward_bout[kov_ward_bout.winner=='ward'].plot.scatter('ward_jab_perc', 'kov_jab_perc', ax=axes[1,0], c='b', s=50)
kov_ward_bout[kov_ward_bout.winner=='split'].plot.scatter('ward_jab_perc', 'kov_jab_perc', ax=axes[1,0], c='g', s=50)
axes[1,0].set_xlim([-0.05,.65]);axes[1,0].set_ylim([-0.05,.65])
axes[1,0].set_xlabel('Ward'); axes[1,0].set_ylabel('Kovalev')

kov_ward_bout[kov_ward_bout.winner=='kov'].plot.scatter('ward_pow_perc', 'kov_pow_perc', ax=axes[1,1], c='r', s=50)
kov_ward_bout[kov_ward_bout.winner=='ward'].plot.scatter('ward_pow_perc', 'kov_pow_perc', ax=axes[1,1], c='b', s=50)
kov_ward_bout[kov_ward_bout.winner=='split'].plot.scatter('ward_pow_perc', 'kov_pow_perc', ax=axes[1,1], c='g', s=50)
axes[1,1].set_xlim([-0.05,.65]); axes[1,1].set_ylim([-0.05,.65])
axes[1,1].set_xlabel('Ward'); axes[1,1].set_ylabel('')

kov_ward_bout[kov_ward_bout.winner=='kov'].plot.scatter('ward_pun_perc', 'kov_pun_perc', ax=axes[1,2], c='r', s=50)
kov_ward_bout[kov_ward_bout.winner=='ward'].plot.scatter('ward_pun_perc', 'kov_pun_perc', ax=axes[1,2], c='b', s=50)
kov_ward_bout[kov_ward_bout.winner=='split'].plot.scatter('ward_pun_perc', 'kov_pun_perc', ax=axes[1,2], c='g', s=50)
axes[1,2].set_xlim([-0.05,.65]); axes[1,2].set_ylim([-0.05,.65])
axes[1,2].set_xlabel('Ward'); axes[1,2].set_ylabel('')
axes[1,2].text(0.6, 0., 'endlesspint.com',
               fontsize=12, color='gray',
               ha='right', va='bottom', alpha=0.3)

for row in range(nrows):
    for col in range(ncols):
        axes[row, col].set_aspect('equal')
        axes[row, col].plot(x_line,y_line,'c--')
        
plt.tight_layout(h_pad=1.0)

### save file localy w high resolution
# plt.savefig('img/fight_hour_tweets.PNG', dpi=1200)
```


<img src = "/code/kov_ward_rd_feat/output_7_0.png"  >


**notes**
- calculate perp dist to 45 degree line for each fighter; get an idea of "distance from parity"
- Kov had 7 rounds with power shots landed, two dots/rounds (4 & 6) fall in same location (3,6)
- Ward was better marksmans in all but the round he was floored in
- Round 10 is curious one:
    - Twitter saw it for Kov, Judges for Ward
    - Kov landed his most jabs & total punches, throwing his most for the fight in that round
    - his power shots were tied for his best performance of the fight
    


```python
kov_ward_bout.kov_pun_perc > kov_ward_bout.ward_pun_perc
```




    0     False
    1      True
    2     False
    3     False
    4     False
    5     False
    6     False
    7     False
    8     False
    9     False
    10    False
    11    False
    dtype: bool




```python
ax = kov_ward_bout.plot.scatter(x='kov_jab_land', y='kov_pow_land', color='DarkBlue', label='Kov');
kov_ward_bout.plot.scatter(x='ward_jab_land', y='ward_pow_land', color='DarkGreen', label='Ward', title='Nom', ax=ax);
```


<img src = "/code/kov_ward_rd_feat/output_10_0.png"  >



```python
plt.figure(figsize=(8,8))
plt.scatter(x=kov_ward_bout.kov_jab_land, y=kov_ward_bout.kov_pow_land, c='r')
plt.scatter(x=kov_ward_bout.ward_jab_land, y=kov_ward_bout.ward_pow_land)
plt.plot(x_line,y_line,'--')
plt.xlim((-1,12))
plt.ylim((-1,12))
plt.axes().set_aspect('equal')
```


<img src = "/code/kov_ward_rd_feat/output_11_0.png"  >



```python
f, ((ax1, ax2), (ax3, ax4)) = plt.subplots(2,2, figsize=(15,15))

Kov1 = ax1.scatter(x=kov_ward_bout[kov_ward_bout['round']<=6]['kov_jab_land'], 
                  y=kov_ward_bout[kov_ward_bout['round']<=6]['kov_pow_land'], 
                  c='r', s=50, alpha=.7)
Kov2 = ax1.scatter(x=kov_ward_bout[kov_ward_bout['round']>6]['kov_jab_land'], 
                  y=kov_ward_bout[kov_ward_bout['round']>6]['kov_pow_land'], 
                  c='r', marker='s', s=50, alpha=.7)
Ward1 = ax1.scatter(x=kov_ward_bout[kov_ward_bout['round']<=6]['ward_jab_land'], 
                   y=kov_ward_bout[kov_ward_bout['round']<=6]['ward_pow_land'], 
                   c='b', s=50, alpha=.7)
Ward2 = ax1.scatter(x=kov_ward_bout[kov_ward_bout['round']>6]['ward_jab_land'], 
                   y=kov_ward_bout[kov_ward_bout['round']>6]['ward_pow_land'], 
                   c='b', marker='s', s=50, alpha=.7)
ax1.set_xlim((-1,12))
ax1.set_ylim((-1,12))
ax1.set_xlabel('jab count')
ax1.set_ylabel('power count')

ax2.scatter(x=kov_ward_bout[kov_ward_bout['round']<=6]['kov_jab_perc'], 
            y=kov_ward_bout[kov_ward_bout['round']<=6]['kov_pow_perc'], 
            c='r', s=50, alpha=.7)
ax2.scatter(x=kov_ward_bout[kov_ward_bout['round']>6]['kov_jab_perc'], 
            y=kov_ward_bout[kov_ward_bout['round']>6]['kov_pow_perc'], 
            c='r', marker='s', s=50, alpha=.7)
ax2.scatter(x=kov_ward_bout[kov_ward_bout['round']<=6]['ward_jab_perc'], 
            y=kov_ward_bout[kov_ward_bout['round']<=6]['ward_pow_perc'], 
            c='b', s=50, alpha=.7)
ax2.scatter(x=kov_ward_bout[kov_ward_bout['round']>6]['ward_jab_perc'], 
            y=kov_ward_bout[kov_ward_bout['round']>6]['ward_pow_perc'], 
            c='b', marker='s', s=50, alpha=.7)
ax2.set_xlim((-0.05,.65))
ax2.set_ylim((-0.05,.65))
ax2.set_xlabel('jab percent')
ax2.set_ylabel('power percent')


ax3.scatter(x=kov_ward_bout[kov_ward_bout.winner=='kov']['kov_jab_land'], 
            y=kov_ward_bout[kov_ward_bout.winner=='kov']['kov_pow_land'], c='r', marker='o', s=80, alpha=.7)
ax3.scatter(x=kov_ward_bout[kov_ward_bout.winner=='split']['kov_jab_land'], 
            y=kov_ward_bout[kov_ward_bout.winner=='split']['kov_pow_land'], c='g', marker='o', s=50, alpha=.7)
ax3.scatter(x=kov_ward_bout[kov_ward_bout.winner=='ward']['kov_jab_land'], 
            y=kov_ward_bout[kov_ward_bout.winner=='ward']['kov_pow_land'], c='r', marker='x', s=50, alpha=.7)

ax3.scatter(x=kov_ward_bout[kov_ward_bout.winner=='ward']['ward_jab_land'], 
            y=kov_ward_bout[kov_ward_bout.winner=='ward']['ward_pow_land'], c='b', marker='s', s=80, alpha=.7)
ax3.scatter(x=kov_ward_bout[kov_ward_bout.winner=='split']['ward_jab_land'], 
            y=kov_ward_bout[kov_ward_bout.winner=='split']['ward_pow_land'], c='g', marker='s', s=50, alpha=.7)
ax3.scatter(x=kov_ward_bout[kov_ward_bout.winner=='kov']['ward_jab_land'], 
            y=kov_ward_bout[kov_ward_bout.winner=='kov']['ward_pow_land'], c='b', marker='x', s=50, alpha=.7)
ax3.set_xlim((-1,12))
ax3.set_ylim((-1,12))
ax3.set_xlabel('jab count')
ax3.set_ylabel('power count')

# ax4.scatter(x=kov_ward_bout.kov_jab_perc, y=kov_ward_bout.kov_pow_perc, c='r', marker='D', s=50, alpha=.7)
# ax4.scatter(x=kov_ward_bout.ward_jab_perc, y=kov_ward_bout.ward_pow_perc, c='b', marker='s', s=50, alpha=.7)
ax4.scatter(x=kov_ward_bout[kov_ward_bout.winner=='kov']['kov_jab_perc'], 
            y=kov_ward_bout[kov_ward_bout.winner=='kov']['kov_pow_perc'], c='r', marker='o', s=80, alpha=.7)
ax4.scatter(x=kov_ward_bout[kov_ward_bout.winner=='split']['kov_jab_perc'], 
            y=kov_ward_bout[kov_ward_bout.winner=='split']['kov_pow_perc'], c='g', marker='o', s=50, alpha=.7)
ax4.scatter(x=kov_ward_bout[kov_ward_bout.winner=='ward']['kov_jab_perc'], 
            y=kov_ward_bout[kov_ward_bout.winner=='ward']['kov_pow_perc'], c='r', marker='x', s=50, alpha=.7)

ax4.scatter(x=kov_ward_bout[kov_ward_bout.winner=='ward']['ward_jab_perc'], 
            y=kov_ward_bout[kov_ward_bout.winner=='ward']['ward_pow_perc'], c='b', marker='s', s=80, alpha=.7)
ax4.scatter(x=kov_ward_bout[kov_ward_bout.winner=='split']['ward_jab_perc'], 
            y=kov_ward_bout[kov_ward_bout.winner=='split']['ward_pow_perc'], c='g', marker='s', s=50, alpha=.7)
ax4.scatter(x=kov_ward_bout[kov_ward_bout.winner=='kov']['ward_jab_perc'], 
            y=kov_ward_bout[kov_ward_bout.winner=='kov']['ward_pow_perc'], c='b', marker='x', s=50, alpha=.7)
ax4.set_xlim((-0.05,.65))
ax4.set_ylim((-0.05,.65))
ax4.set_xlabel('jab percent')
ax4.set_ylabel('power percent')
ax4.text(0.6, 0., 'endlesspint.com',
         fontsize=12, color='gray',
         ha='right', va='bottom', alpha=0.3)

for ax in [ax1, ax2, ax3, ax4]:
    ax.plot(x_line,y_line,'c--')
    ax.set_aspect('equal')

f.legend((Kov1, Ward1, Kov2, Ward2), 
         ('Kov Rd 1-6', 'Ward Rd 1-6', 'Kov Rd 7-12', 'Ward Rd 7-12'), 'right')

### save file localy w high resolution
# plt.savefig('img/fight_hour_tweets.PNG', dpi=1200)
```




    <matplotlib.legend.Legend at 0xa634160>




<img src = "/code/kov_ward_rd_feat/output_12_1.png"  >


**notes**
- there are two Kov rounds with (nearly) same stats, but diff results (1 win, 1 split)
- all unanimous Ward rounds showed him scoring at 50% in at least one punch stat


```python
ax = kov_ward_bout.plot.scatter(x='kov_jab_perc', y='kov_pow_perc', color='Red', label='Kov');
kov_ward_bout.plot.scatter(x='ward_jab_perc', y='ward_pow_perc', color='Blue', label='Ward', title='Per', ax=ax);
```


<img src = "/code/kov_ward_rd_feat/output_14_0.png"  >


## round stats and scoring (long table)


```python
kov_ward_bout.columns
```




    Index([        u'round',  u'kov_pun_land',  u'kov_pun_thrw',  u'kov_pun_perc',
            u'kov_jab_land',  u'kov_jab_thrw',  u'kov_jab_perc',  u'kov_pow_land',
            u'kov_pow_thrw',  u'kov_pow_perc', u'ward_pun_land', u'ward_pun_thrw',
           u'ward_pun_perc', u'ward_jab_land', u'ward_jab_thrw', u'ward_jab_perc',
           u'ward_pow_land', u'ward_pow_thrw', u'ward_pow_perc',     u'kov_kdwns',
                   u'white',          u'blue',          u'pink',        u'winner'],
          dtype='object')




```python
cols_non_perc = ['kov_pun_land', 'kov_pun_thrw', 'kov_jab_land', 'kov_jab_thrw', 'kov_pow_land', 'kov_pow_thrw',
                 'ward_pun_land', 'ward_pun_thrw', 'ward_jab_land', 'ward_jab_thrw', 'ward_pow_land', 'ward_pow_thrw', 
                 'kov_kdwns']

kov_ward_bout[cols_non_perc].head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>kov_pun_land</th>
      <th>kov_pun_thrw</th>
      <th>kov_jab_land</th>
      <th>kov_jab_thrw</th>
      <th>kov_pow_land</th>
      <th>kov_pow_thrw</th>
      <th>ward_pun_land</th>
      <th>ward_pun_thrw</th>
      <th>ward_jab_land</th>
      <th>ward_jab_thrw</th>
      <th>ward_pow_land</th>
      <th>ward_pow_thrw</th>
      <th>kov_kdwns</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7</td>
      <td>34</td>
      <td>4</td>
      <td>22</td>
      <td>3</td>
      <td>12</td>
      <td>5</td>
      <td>20</td>
      <td>4</td>
      <td>13</td>
      <td>1</td>
      <td>7</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>16</td>
      <td>49</td>
      <td>5</td>
      <td>23</td>
      <td>11</td>
      <td>26</td>
      <td>3</td>
      <td>16</td>
      <td>3</td>
      <td>12</td>
      <td>0</td>
      <td>4</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>27</td>
      <td>2</td>
      <td>15</td>
      <td>2</td>
      <td>12</td>
      <td>5</td>
      <td>22</td>
      <td>2</td>
      <td>12</td>
      <td>3</td>
      <td>10</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9</td>
      <td>37</td>
      <td>3</td>
      <td>22</td>
      <td>6</td>
      <td>15</td>
      <td>7</td>
      <td>25</td>
      <td>4</td>
      <td>14</td>
      <td>3</td>
      <td>11</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7</td>
      <td>33</td>
      <td>3</td>
      <td>17</td>
      <td>4</td>
      <td>16</td>
      <td>8</td>
      <td>24</td>
      <td>3</td>
      <td>10</td>
      <td>5</td>
      <td>14</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
tup_non_perc = ('kov_pun_land', 'kov_pun_thrw', 'kov_jab_land', 'kov_jab_thrw', 'kov_pow_land', 'kov_pow_thrw',
                 'ward_pun_land', 'ward_pun_thrw', 'ward_jab_land', 'ward_jab_thrw', 'ward_pow_land', 'ward_pow_thrw', 
                 'kov_kdwns')

judges = ['white', 'blue', 'pink']
kov_ward_long = pd.DataFrame()

for judge in judges:
    temp_df = pd.melt(kov_ward_bout, id_vars=tup_non_perc, value_vars=[judge])
    kov_ward_long = kov_ward_long.append(temp_df)
    
kov_ward_long.reset_index(drop=True, inplace=True)
kov_ward_long.drop('variable', axis=1, inplace=True)
print kov_ward_long.shape
kov_ward_long.head(12)
```

    (36, 14)
    




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>kov_pun_land</th>
      <th>kov_pun_thrw</th>
      <th>kov_jab_land</th>
      <th>kov_jab_thrw</th>
      <th>kov_pow_land</th>
      <th>kov_pow_thrw</th>
      <th>ward_pun_land</th>
      <th>ward_pun_thrw</th>
      <th>ward_jab_land</th>
      <th>ward_jab_thrw</th>
      <th>ward_pow_land</th>
      <th>ward_pow_thrw</th>
      <th>kov_kdwns</th>
      <th>value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7</td>
      <td>34</td>
      <td>4</td>
      <td>22</td>
      <td>3</td>
      <td>12</td>
      <td>5</td>
      <td>20</td>
      <td>4</td>
      <td>13</td>
      <td>1</td>
      <td>7</td>
      <td>0</td>
      <td>kov</td>
    </tr>
    <tr>
      <th>1</th>
      <td>16</td>
      <td>49</td>
      <td>5</td>
      <td>23</td>
      <td>11</td>
      <td>26</td>
      <td>3</td>
      <td>16</td>
      <td>3</td>
      <td>12</td>
      <td>0</td>
      <td>4</td>
      <td>1</td>
      <td>kov</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>27</td>
      <td>2</td>
      <td>15</td>
      <td>2</td>
      <td>12</td>
      <td>5</td>
      <td>22</td>
      <td>2</td>
      <td>12</td>
      <td>3</td>
      <td>10</td>
      <td>0</td>
      <td>kov</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9</td>
      <td>37</td>
      <td>3</td>
      <td>22</td>
      <td>6</td>
      <td>15</td>
      <td>7</td>
      <td>25</td>
      <td>4</td>
      <td>14</td>
      <td>3</td>
      <td>11</td>
      <td>0</td>
      <td>kov</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7</td>
      <td>33</td>
      <td>3</td>
      <td>17</td>
      <td>4</td>
      <td>16</td>
      <td>8</td>
      <td>24</td>
      <td>3</td>
      <td>10</td>
      <td>5</td>
      <td>14</td>
      <td>0</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>5</th>
      <td>9</td>
      <td>36</td>
      <td>3</td>
      <td>17</td>
      <td>6</td>
      <td>19</td>
      <td>8</td>
      <td>25</td>
      <td>5</td>
      <td>13</td>
      <td>3</td>
      <td>12</td>
      <td>0</td>
      <td>kov</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>29</td>
      <td>1</td>
      <td>10</td>
      <td>6</td>
      <td>19</td>
      <td>11</td>
      <td>32</td>
      <td>6</td>
      <td>12</td>
      <td>5</td>
      <td>20</td>
      <td>0</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>7</th>
      <td>10</td>
      <td>38</td>
      <td>4</td>
      <td>20</td>
      <td>6</td>
      <td>18</td>
      <td>11</td>
      <td>32</td>
      <td>1</td>
      <td>12</td>
      <td>10</td>
      <td>20</td>
      <td>0</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>8</th>
      <td>11</td>
      <td>46</td>
      <td>4</td>
      <td>22</td>
      <td>7</td>
      <td>24</td>
      <td>17</td>
      <td>38</td>
      <td>8</td>
      <td>20</td>
      <td>9</td>
      <td>18</td>
      <td>0</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>9</th>
      <td>21</td>
      <td>58</td>
      <td>11</td>
      <td>33</td>
      <td>10</td>
      <td>25</td>
      <td>16</td>
      <td>35</td>
      <td>9</td>
      <td>23</td>
      <td>7</td>
      <td>12</td>
      <td>0</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>10</th>
      <td>12</td>
      <td>40</td>
      <td>5</td>
      <td>22</td>
      <td>7</td>
      <td>18</td>
      <td>13</td>
      <td>26</td>
      <td>9</td>
      <td>15</td>
      <td>4</td>
      <td>11</td>
      <td>0</td>
      <td>ward</td>
    </tr>
    <tr>
      <th>11</th>
      <td>13</td>
      <td>47</td>
      <td>3</td>
      <td>19</td>
      <td>10</td>
      <td>28</td>
      <td>12</td>
      <td>42</td>
      <td>1</td>
      <td>12</td>
      <td>11</td>
      <td>30</td>
      <td>0</td>
      <td>ward</td>
    </tr>
  </tbody>
</table>
</div>



## sklearn ensemble techniques
source: http://scikit-learn.org/stable/modules/ensemble.html

source: http://machinelearningmastery.com/ensemble-machine-learning-algorithms-python-scikit-learn/

**Bagging**


```python
from sklearn import cross_validation
from sklearn.ensemble import BaggingClassifier
from sklearn.tree import DecisionTreeClassifier
```


```python
array = kov_ward_long.values
X = array[:,0:13]
y = array[:,13]
```


```python
num_folds = 10
num_instances = len(X)
seed = 7
kfold = cross_validation.KFold(n=num_instances, n_folds=num_folds, random_state=seed)
cart = DecisionTreeClassifier()
num_trees = 100
```


```python
clf_bgg = BaggingClassifier(base_estimator=cart, n_estimators=num_trees, random_state=seed)
results = cross_validation.cross_val_score(clf_bgg, X, y, cv=kfold)
print(results.mean())
```

    0.858333333333
    


```python
clf_bgg.fit(X, y)
```




    BaggingClassifier(base_estimator=DecisionTreeClassifier(class_weight=None, criterion='gini', max_depth=None,
                max_features=None, max_leaf_nodes=None, min_samples_leaf=1,
                min_samples_split=2, min_weight_fraction_leaf=0.0,
                presort=False, random_state=None, splitter='best'),
             bootstrap=True, bootstrap_features=False, max_features=1.0,
             max_samples=1.0, n_estimators=100, n_jobs=1, oob_score=False,
             random_state=7, verbose=0, warm_start=False)




```python
print clf_bgg.predict(X[:12])
print clf_bgg.predict_proba(X[:12])
```

    [u'kov' u'kov' u'kov' u'kov' u'ward' u'kov' u'ward' u'ward' u'ward' u'ward'
     u'ward' u'ward']
    [[ 0.998       0.002     ]
     [ 0.99404762  0.00595238]
     [ 0.74559524  0.25440476]
     [ 0.98216667  0.01783333]
     [ 0.38943651  0.61056349]
     [ 0.66216667  0.33783333]
     [ 0.0075      0.9925    ]
     [ 0.015       0.985     ]
     [ 0.          1.        ]
     [ 0.00833333  0.99166667]
     [ 0.03        0.97      ]
     [ 0.28569048  0.71430952]]
    


```python
pd.DataFrame(np.hstack((np.reshape(clf_bgg.predict(X[:12]), (12,1)), clf_bgg.predict_proba(X[:12]))), 
             columns=['winner', 'prob_kov', 'prob_ward'])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>winner</th>
      <th>prob_kov</th>
      <th>prob_ward</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>kov</td>
      <td>0.998</td>
      <td>0.002</td>
    </tr>
    <tr>
      <th>1</th>
      <td>kov</td>
      <td>0.994048</td>
      <td>0.00595238</td>
    </tr>
    <tr>
      <th>2</th>
      <td>kov</td>
      <td>0.745595</td>
      <td>0.254405</td>
    </tr>
    <tr>
      <th>3</th>
      <td>kov</td>
      <td>0.982167</td>
      <td>0.0178333</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ward</td>
      <td>0.389437</td>
      <td>0.610563</td>
    </tr>
    <tr>
      <th>5</th>
      <td>kov</td>
      <td>0.662167</td>
      <td>0.337833</td>
    </tr>
    <tr>
      <th>6</th>
      <td>ward</td>
      <td>0.0075</td>
      <td>0.9925</td>
    </tr>
    <tr>
      <th>7</th>
      <td>ward</td>
      <td>0.015</td>
      <td>0.985</td>
    </tr>
    <tr>
      <th>8</th>
      <td>ward</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>9</th>
      <td>ward</td>
      <td>0.00833333</td>
      <td>0.991667</td>
    </tr>
    <tr>
      <th>10</th>
      <td>ward</td>
      <td>0.03</td>
      <td>0.97</td>
    </tr>
    <tr>
      <th>11</th>
      <td>ward</td>
      <td>0.28569</td>
      <td>0.71431</td>
    </tr>
  </tbody>
</table>
</div>



**Random Forest**


```python
from sklearn import cross_validation
from sklearn.ensemble import RandomForestClassifier

array = kov_ward_long.values
X = array[:,0:13]
y = array[:,13]

num_folds = 10
num_instances = len(X)
seed = 7
num_trees = 100
max_features = 3
kfold = cross_validation.KFold(n=num_instances, n_folds=num_folds, random_state=seed)

clf_RF = RandomForestClassifier(n_estimators=num_trees, max_features=max_features)
results = cross_validation.cross_val_score(clf_RF, X, y, cv=kfold)
print(results.mean())
```

    0.8
    


```python
clf_RF.fit(X,y)
```




    RandomForestClassifier(bootstrap=True, class_weight=None, criterion='gini',
                max_depth=None, max_features=3, max_leaf_nodes=None,
                min_samples_leaf=1, min_samples_split=2,
                min_weight_fraction_leaf=0.0, n_estimators=100, n_jobs=1,
                oob_score=False, random_state=None, verbose=0,
                warm_start=False)




```python
print clf_RF.predict(X[:12])
print clf_RF.predict_proba(X[:12])
```

    [u'kov' u'kov' u'kov' u'kov' u'ward' u'kov' u'ward' u'ward' u'ward' u'ward'
     u'ward' u'ward']
    [[ 0.98933333  0.01066667]
     [ 0.97083333  0.02916667]
     [ 0.6694881   0.3305119 ]
     [ 0.99333333  0.00666667]
     [ 0.35454762  0.64545238]
     [ 0.70514286  0.29485714]
     [ 0.          1.        ]
     [ 0.00991667  0.99008333]
     [ 0.          1.        ]
     [ 0.00333333  0.99666667]
     [ 0.035       0.965     ]
     [ 0.2872619   0.7127381 ]]
    


```python
print kov_ward_long.columns[:13]
print np.sum(clf_RF.feature_importances_)
clf_RF.feature_importances_
```

    Index([u'kov_pun_land', u'kov_pun_thrw', u'kov_jab_land', u'kov_jab_thrw',
           u'kov_pow_land', u'kov_pow_thrw', u'ward_pun_land', u'ward_pun_thrw',
           u'ward_jab_land', u'ward_jab_thrw', u'ward_pow_land', u'ward_pow_thrw',
           u'kov_kdwns'],
          dtype='object')
    1.0
    




    array([ 0.03661623,  0.03374295,  0.00706595,  0.02572995,  0.03433428,
            0.06633053,  0.19602896,  0.14064   ,  0.07438218,  0.03191946,
            0.27581351,  0.07112938,  0.00626662])




```python
rf_feat_imp = pd.DataFrame(zip(kov_ward_long.columns[:13], clf_RF.feature_importances_), columns=['feature', 'importance'])
rf_feat_imp.sort_values('importance', ascending=False, inplace=True)
rf_feat_imp
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>feature</th>
      <th>importance</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>10</th>
      <td>ward_pow_land</td>
      <td>0.275814</td>
    </tr>
    <tr>
      <th>6</th>
      <td>ward_pun_land</td>
      <td>0.196029</td>
    </tr>
    <tr>
      <th>7</th>
      <td>ward_pun_thrw</td>
      <td>0.140640</td>
    </tr>
    <tr>
      <th>8</th>
      <td>ward_jab_land</td>
      <td>0.074382</td>
    </tr>
    <tr>
      <th>11</th>
      <td>ward_pow_thrw</td>
      <td>0.071129</td>
    </tr>
    <tr>
      <th>5</th>
      <td>kov_pow_thrw</td>
      <td>0.066331</td>
    </tr>
    <tr>
      <th>0</th>
      <td>kov_pun_land</td>
      <td>0.036616</td>
    </tr>
    <tr>
      <th>4</th>
      <td>kov_pow_land</td>
      <td>0.034334</td>
    </tr>
    <tr>
      <th>1</th>
      <td>kov_pun_thrw</td>
      <td>0.033743</td>
    </tr>
    <tr>
      <th>9</th>
      <td>ward_jab_thrw</td>
      <td>0.031919</td>
    </tr>
    <tr>
      <th>3</th>
      <td>kov_jab_thrw</td>
      <td>0.025730</td>
    </tr>
    <tr>
      <th>2</th>
      <td>kov_jab_land</td>
      <td>0.007066</td>
    </tr>
    <tr>
      <th>12</th>
      <td>kov_kdwns</td>
      <td>0.006267</td>
    </tr>
  </tbody>
</table>
</div>



how about that round 10? maybe one more go

**kNN**


```python
from sklearn.ensemble import BaggingClassifier
from sklearn.neighbors import KNeighborsClassifier
bagging = BaggingClassifier(KNeighborsClassifier(), max_samples=0.5, max_features=0.5)
```


```python
array = kov_ward_long.values
X = array[:,0:13]
y = array[:,13]

num_folds = 10
num_instances = len(X)
seed = 7

kfold = cross_validation.KFold(n=num_instances, n_folds=num_folds, random_state=seed)
results = cross_validation.cross_val_score(bagging, X, y, cv=kfold)
print(results.mean())
```

    0.666666666667
    


```python
bagging.fit(X, y)

print bagging.predict(X[:12])
print bagging.predict_proba(X[:12])
```

    [u'kov' u'kov' u'kov' u'kov' u'kov' u'kov' u'ward' u'ward' u'ward' u'ward'
     u'ward' u'ward']
    [[ 0.86  0.14]
     [ 0.56  0.44]
     [ 0.62  0.38]
     [ 0.7   0.3 ]
     [ 0.68  0.32]
     [ 0.64  0.36]
     [ 0.3   0.7 ]
     [ 0.26  0.74]
     [ 0.14  0.86]
     [ 0.18  0.82]
     [ 0.36  0.64]
     [ 0.2   0.8 ]]
    


```python
zip(bagging.predict(X[:12]), bagging.predict_proba(X[:12]))
```




    [(u'kov', array([ 0.86,  0.14])),
     (u'kov', array([ 0.56,  0.44])),
     (u'kov', array([ 0.62,  0.38])),
     (u'kov', array([ 0.7,  0.3])),
     (u'kov', array([ 0.68,  0.32])),
     (u'kov', array([ 0.64,  0.36])),
     (u'ward', array([ 0.3,  0.7])),
     (u'ward', array([ 0.26,  0.74])),
     (u'ward', array([ 0.14,  0.86])),
     (u'ward', array([ 0.18,  0.82])),
     (u'ward', array([ 0.36,  0.64])),
     (u'ward', array([ 0.2,  0.8]))]




```python
from sklearn.cross_validation import train_test_split
from sklearn.neighbors import KNeighborsClassifier
from sklearn import metrics
```


```python
array = kov_ward_long.values
X = array[:,0:13]
y = array[:,13]
```


```python
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=8)

# check classification accuracy of KNN with K=5
knn = KNeighborsClassifier(n_neighbors=5)
knn.fit(X_train, y_train)
y_pred = knn.predict(X_test)
print metrics.accuracy_score(y_test, y_pred)
```

    0.777777777778
    


```python
from sklearn.cross_validation import cross_val_score

# 10-fold cross-validation with K=5 for KNN (the n_neighbors parameter)
knn = KNeighborsClassifier(n_neighbors=5)
scores = cross_val_score(knn, X, y, cv=10, scoring='accuracy')
print scores
```

    [ 0.6         0.75        0.75        0.25        0.75        1.
      0.33333333  1.          0.66666667  0.66666667]
    


```python
# use average accuracy as an estimate of out-of-sample accuracy
print scores.mean()
```

    0.676666666667
    


```python
# search for an optimal value of K for KNN
k_range = range(1, 31)
k_scores = []
for k in k_range:
    knn = KNeighborsClassifier(n_neighbors=k)
    scores = cross_val_score(knn, X, y, cv=10, scoring='accuracy')
    k_scores.append(scores.mean())
# print k_scores

# plot the value of K for KNN (x-axis) versus the cross-validated accuracy (y-axis)
plt.plot(k_range, k_scores)
plt.xlabel('Value of K for KNN')
plt.ylabel('Cross-Validated Accuracy')
```




    <matplotlib.text.Text at 0xbeb65c0>




<img src = "/code/kov_ward_rd_feat/output_44_1.png"  >



```python
# 10-fold cross-validation with the best KNN model
knn = KNeighborsClassifier(n_neighbors=13)
print cross_val_score(knn, X, y, cv=10, scoring='accuracy').mean()
```

    0.871666666667
    


```python
knn.fit(X, y)

zip(knn.predict(X[:12]), knn.predict_proba(X[:12]))
```




    [(u'kov', array([ 0.69230769,  0.30769231])),
     (u'kov', array([ 0.69230769,  0.30769231])),
     (u'kov', array([ 0.69230769,  0.30769231])),
     (u'kov', array([ 0.69230769,  0.30769231])),
     (u'kov', array([ 0.69230769,  0.30769231])),
     (u'kov', array([ 0.53846154,  0.46153846])),
     (u'ward', array([ 0.30769231,  0.69230769])),
     (u'ward', array([ 0.46153846,  0.53846154])),
     (u'ward', array([ 0.07692308,  0.92307692])),
     (u'ward', array([ 0.15384615,  0.84615385])),
     (u'ward', array([ 0.46153846,  0.53846154])),
     (u'ward', array([ 0.07692308,  0.92307692]))]




```python
# avg Kov proba round
np.mean(knn.predict_proba(X[:12])[:6,0])
```




    0.66666666666666663




```python
# avg Ward proba round
np.mean(knn.predict_proba(X[:12])[6:,1])
```




    0.74358974358974361



## ... and KMeans (why not?)


```python
from sklearn.cluster import KMeans
```


```python
# identify the twelve rounds as 'X'
X_12rds = X[:12,]
X_12rds
```




    array([[7L, 34L, 4L, 22L, 3L, 12L, 5L, 20L, 4L, 13L, 1L, 7L, 0L],
           [16L, 49L, 5L, 23L, 11L, 26L, 3L, 16L, 3L, 12L, 0L, 4L, 1L],
           [4L, 27L, 2L, 15L, 2L, 12L, 5L, 22L, 2L, 12L, 3L, 10L, 0L],
           [9L, 37L, 3L, 22L, 6L, 15L, 7L, 25L, 4L, 14L, 3L, 11L, 0L],
           [7L, 33L, 3L, 17L, 4L, 16L, 8L, 24L, 3L, 10L, 5L, 14L, 0L],
           [9L, 36L, 3L, 17L, 6L, 19L, 8L, 25L, 5L, 13L, 3L, 12L, 0L],
           [7L, 29L, 1L, 10L, 6L, 19L, 11L, 32L, 6L, 12L, 5L, 20L, 0L],
           [10L, 38L, 4L, 20L, 6L, 18L, 11L, 32L, 1L, 12L, 10L, 20L, 0L],
           [11L, 46L, 4L, 22L, 7L, 24L, 17L, 38L, 8L, 20L, 9L, 18L, 0L],
           [21L, 58L, 11L, 33L, 10L, 25L, 16L, 35L, 9L, 23L, 7L, 12L, 0L],
           [12L, 40L, 5L, 22L, 7L, 18L, 13L, 26L, 9L, 15L, 4L, 11L, 0L],
           [13L, 47L, 3L, 19L, 10L, 28L, 12L, 42L, 1L, 12L, 11L, 30L, 0L]], dtype=object)




```python
# identify unanimous rounds for training
X_unanm = X_12rds[np.array(kov_ward_bout['winner']!='split')]
kmeans = KMeans(n_clusters=2, random_state=0).fit(X_unanm)
kmeans.labels_
```




    array([0, 0, 0, 0, 0, 1, 1, 0])




```python
# predict on split rounds
X_split = X_12rds[np.array(kov_ward_bout['winner']=='split')]
kmeans.predict(X_split)
```
  




    array([0, 0, 0, 1])




```python
kmeans.cluster_centers_
```




    array([[ 10.16666667,  37.83333333,   3.66666667,  19.83333333,
              6.5       ,  18.        ,   8.33333333,  25.16666667,
              4.5       ,  13.        ,   3.83333333,  12.16666667,
              0.16666667],
           [ 16.        ,  52.        ,   7.5       ,  27.5       ,
              8.5       ,  24.5       ,  16.5       ,  36.5       ,
              8.5       ,  21.5       ,   8.        ,  15.        ,   0.        ]])



**maybe too many features, let's go with the three most important as identified by RF**


```python
X_impFeat = X[:12,[6,7,10]]
X_impFeat
```




    array([[5L, 20L, 1L],
           [3L, 16L, 0L],
           [5L, 22L, 3L],
           [7L, 25L, 3L],
           [8L, 24L, 5L],
           [8L, 25L, 3L],
           [11L, 32L, 5L],
           [11L, 32L, 10L],
           [17L, 38L, 9L],
           [16L, 35L, 7L],
           [13L, 26L, 4L],
           [12L, 42L, 11L]], dtype=object)




```python
# identify unanimous rounds for training
X_unanm = X_impFeat[np.array(kov_ward_bout['winner']!='split')]
kmeans = KMeans(n_clusters=2, random_state=0).fit(X_unanm)
kmeans.labels_
```




    array([1, 1, 1, 0, 0, 0, 0, 0])




```python
# predict on split rounds
X_split = X_impFeat[np.array(kov_ward_bout['winner']=='split')]
kmeans.predict(X_split)
```
   




    array([1, 1, 1, 0])




```python
# just run on all 12 at once
kmeans = KMeans(n_clusters=2, random_state=0).fit(X_impFeat)
kmeans.labels_
```




    array([0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 0, 1])



source: http://matplotlib.org/mpl_toolkits/mplot3d/tutorial.html; http://scikit-learn.org/stable/auto_examples/cluster/plot_cluster_iris.html#sphx-glr-auto-examples-cluster-plot-cluster-iris-py


```python
print(plt.style.available)
```

    [u'seaborn-darkgrid', u'seaborn-notebook', u'classic', u'seaborn-ticks', u'grayscale', u'bmh', u'seaborn-talk', u'dark_background', u'ggplot', u'fivethirtyeight', u'seaborn-colorblind', u'seaborn-deep', u'seaborn-whitegrid', u'seaborn-bright', u'seaborn-poster', u'seaborn-muted', u'seaborn-paper', u'seaborn-white', u'seaborn-pastel', u'seaborn-dark', u'seaborn-dark-palette']
    


```python
X_impFeat[np.array(kov_ward_bout['winner']=='split'),0]
```




    array([5L, 8L, 8L, 12L], dtype=object)




```python
for i in zip(['kov', 'ward', 'split'],['red', 'blue', 'green']):
    print i[0]
```

    kov
    ward
    split
    


```python
from mpl_toolkits.mplot3d import Axes3D

plt.style.use(u'seaborn-colorblind')

fig = plt.figure(figsize=(10,10))
ax = fig.add_subplot(111, projection='3d')

# ADD COLOR by round win/split
# ax.scatter(X_impFeat[:,0], X_impFeat[:,1], X_impFeat[:,2])
for i in zip(['kov', 'ward', 'split'],['red', 'blue', 'green']):
    ax.scatter(X_impFeat[np.array(kov_ward_bout['winner']==i[0]),0], 
               X_impFeat[np.array(kov_ward_bout['winner']==i[0]),1], 
               X_impFeat[np.array(kov_ward_bout['winner']==i[0]),2],
               c=i[1], s=50
              )

ax.set_xlabel('ward_pun_land')
ax.set_ylabel('ward_pun_thrw')
ax.set_zlabel('ward_pow_land')

ax.text(27, 8, 0, 'endlesspint.com',
               fontsize=12, color='gray',
               ha='right', va='bottom', rotation=180, alpha=0.3)

plt.show()

### save file localy w high resolution
# plt.savefig('img/fight_hour_tweets.PNG', dpi=1200)
```


<img src = "/code/kov_ward_rd_feat/output_64_0.png"  >



```python

```


```python

```


```python

```
