

```python
import urllib2
from bs4 import BeautifulSoup
import os, csv

import pandas as pd
import numpy as np

from datetime import datetime

import matplotlib.pyplot as plt
import matplotlib
matplotlib.style.use('ggplot')
%matplotlib inline
```

## import pages


```python
# urllib2.urlopen("file:///deMolen_RookVuur/Rook & Vuur _ Brouwerij De Molen _ BeerAdvocate1.html").read()

soup1 = BeautifulSoup(open("deMolen_RookVuur/Rook & Vuur _ Brouwerij De Molen _ BeerAdvocate1.html"), "lxml")
soup2 = BeautifulSoup(open("deMolen_RookVuur/Rook & Vuur _ Brouwerij De Molen _ Page 2 _ BeerAdvocate.html"), "lxml")
```

## review contents and structure


```python
print soup1.title
soup1.find_all('a')[:10]
```

    <title>Rook &amp; Vuur | Brouwerij De Molen | BeerAdvocate</title>
    




    [<a class="OverlayTrigger OverlayCloser" href="https://www.beeradvocate.com/community/lost-password/" tabindex="106">Forgot your password?</a>,
     <a class="js-panelMask uix_panelMask" href="https://www.beeradvocate.com/community/#"></a>,
     <a class="navLink" href="https://www.beeradvocate.com/">Home</a>,
     <a class="SplitCtrl" href="https://www.beeradvocate.com/"><i class="uix_icon js-offcanvasIcon uix_icon-expandDropdown"></i></a>,
     <a href="https://www.beeradvocate.com/about/">About</a>,
     <a href="https://www.beeradvocate.com/contact/">Contact</a>,
     <a href="https://www.beeradvocate.com/community/forums/help.32/">Help</a>,
     <a href="https://www.beeradvocate.com/advertise/">Advertise</a>,
     <a class="navLink" href="https://www.beeradvocate.com/mag/">Magazine</a>,
     <a class="SplitCtrl" href="https://www.beeradvocate.com/mag/"><i class="uix_icon js-offcanvasIcon uix_icon-expandDropdown"></i></a>]




```python
soup1.find(id="rating_fullview_content_2")
```




    <div id="rating_fullview_content_2"><span class="BAscore_norm">4</span><span class="rAvg_norm">/5</span>\xa0\xa0rDev <span style="color:#006600;">+9.3%</span><br/><span class="muted">look: 4 | smell: 4 | taste: 4 | feel: 4 |  overall: 4</span><br/><br/>An impressive (and very underrated) beer.  A solid Rauchbier, and one of the few beers in which chili is a welcome ingredient.  De Molen seems to have found the sweet spot in which a subtle touch of chili adds to the beer (I've yet to try a beer before this one in which the spicy heat did anything but detract from an otherwise well-done base beer).  Dark, with a good malt body, and just the right amount of heat.<br/><br/><span style="color:#CC8A00;">\u2605</span>\xa0<span class="muted">415 characters</span><br/><br/><div><span class="muted"><a class="username" href="https://www.beeradvocate.com/community/members/lap.1041594/">LAp</a>, <a href="https://www.beeradvocate.com/beer/profile/11031/57357/?ba=LAp#review">May 30, 2016</a></span></div></div>




```python
# <span> are part of reviews and pollute the text
# identify <span> classes for filtering

rev_span_classes = []
# rev_span_styles = []

for span in soup1.find(id="rating_fullview_content_2").find_all('span'):
    print span
    try:
        rev_span_classes.append(span['class'][0])
    except:
        pass
    

rev_span_classes = set(rev_span_classes)

print ''
print rev_span_classes
# print rev_span_styles
```

    <span class="BAscore_norm">4</span>
    <span class="rAvg_norm">/5</span>
    <span style="color:#006600;">+9.3%</span>
    <span class="muted">look: 4 | smell: 4 | taste: 4 | feel: 4 |  overall: 4</span>
    <span style="color:#CC8A00;">★</span>
    <span class="muted">415 characters</span>
    <span class="muted"><a class="username" href="https://www.beeradvocate.com/community/members/lap.1041594/">LAp</a>, <a href="https://www.beeradvocate.com/beer/profile/11031/57357/?ba=LAp#review">May 30, 2016</a></span>
    
    set(['muted', 'BAscore_norm', 'rAvg_norm'])
    

## extract desired data


```python
reviews = []

for soup in [soup1, soup2]:

    for rev in soup.find_all(id="rating_fullview_content_2"):

        current_rev = {}

        for span_class in rev_span_classes:
            current_rev[span_class] = []
            for cl in rev.find_all('span', {'class': span_class}):
                current_rev[span_class].append(cl.get_text())
    #             current_rev[span_class] = cl.get_text()
                cl.replace_with('')


        rev_span_styles = []

        for span in rev.find_all('span'):
            try:
                rev_span_styles.append(span['style'])
            except:
                pass

        for span_style in rev_span_styles:
            current_rev[span_style] = []
            for st in rev.find_all('span', {'style': span_style}):
    #             current_rev[span_style].append(st.get_text())
                current_rev[span_style] = st.get_text()
                st.replace_with('')

        # remove 'rDev' beginning to review
        current_rev['review'] = rev.get_text()[7:]

        reviews.append(current_rev)
    
print len(reviews), '\n'
reviews[-1]
```

    41 
    
    




    {'BAscore_norm': [u'4.72'],
     'color:#006600;': u'+29%',
     'color:#CC8A00;': u'\u2605',
     'muted': [u'look: 4.5 | smell: 5 | taste: 5 | feel: 4.5 |  overall: 4',
      u'374 characters',
      u'johnnybravo, Apr 06, 2010'],
     'rAvg_norm': [u'/5'],
     'review': u"I had it in a side by side tasting with Schlenkerla Rauch M\xe4rzen. It's the same quality but the Rook & Vuur is so more intense in many ways. More smoke, better smoke if you'd ask me as in the side by side Schlenkerla tasted more like an ashtray and the Rook & Vuur like smoked sausage. It has way more body, but of course a higher ABV as well. Looked great, when down easy.\xa0"}



## taking a peak at what we have


```python
pd.DataFrame(reviews).head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>BAscore_norm</th>
      <th>color:#006600;</th>
      <th>color:#990000;</th>
      <th>color:#CC8A00;</th>
      <th>muted</th>
      <th>rAvg_norm</th>
      <th>review</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>[4]</td>
      <td>+9.3%</td>
      <td>NaN</td>
      <td>★</td>
      <td>[look: 4 | smell: 4 | taste: 4 | feel: 4 |  ov...</td>
      <td>[/5]</td>
      <td>An impressive (and very underrated) beer.  A s...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>[3.71]</td>
      <td>+1.4%</td>
      <td>NaN</td>
      <td>★</td>
      <td>[look: 3.5 | smell: 3.75 | taste: 3.75 | feel:...</td>
      <td>[/5]</td>
      <td>330ml bottle - dubbed a smoked/spiced stout, w...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>[4.26]</td>
      <td>+16.4%</td>
      <td>NaN</td>
      <td>★</td>
      <td>[look: 3.75 | smell: 4.5 | taste: 4.25 | feel:...</td>
      <td>[/5]</td>
      <td>Poured into pint.\nPours opaque dark brown wit...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>[4.21]</td>
      <td>+15%</td>
      <td>NaN</td>
      <td>★</td>
      <td>[look: 4 | smell: 4.25 | taste: 4.25 | feel: 4...</td>
      <td>[/5]</td>
      <td>330 ml bottle, dated 25/06/2012, so about 3.5 ...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>[4.11]</td>
      <td>+12.3%</td>
      <td>NaN</td>
      <td>★</td>
      <td>[look: 4.5 | smell: 3.5 | taste: 4.25 | feel: ...</td>
      <td>[/5]</td>
      <td>L:\n-pours the darkest of brown with no light ...</td>
    </tr>
  </tbody>
</table>
</div>



## modify contents for better use


```python
for rev in reviews:
    rev['BAscore_norm'] = float(rev['BAscore_norm'][0])
    rev['rAvg_norm'] = float(rev['rAvg_norm'][0][1:])
    
    if 'look' in rev['muted'][0]:
        for feat in rev['muted'][0].split(' | '):
            feature, score = feat.split(': ')
            feature = feature.strip()
            score = float(score.strip())
            rev[feature] = score
            
    if len(rev['muted']) == 3:
        user = rev['muted'][2].split(', ')[0]
        date = ' '.join(rev['muted'][2].split(', ')[1:])
        date = datetime.strptime(date, "%b %d %Y")
    rev['user'] = user
    rev['datetime'] = date
            
df_reviews = pd.DataFrame(reviews)
df_reviews[:3]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>BAscore_norm</th>
      <th>color:#006600;</th>
      <th>color:#990000;</th>
      <th>color:#CC8A00;</th>
      <th>datetime</th>
      <th>feel</th>
      <th>look</th>
      <th>muted</th>
      <th>overall</th>
      <th>rAvg_norm</th>
      <th>review</th>
      <th>smell</th>
      <th>taste</th>
      <th>user</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4.00</td>
      <td>+9.3%</td>
      <td>NaN</td>
      <td>★</td>
      <td>2016-05-30</td>
      <td>4.0</td>
      <td>4.00</td>
      <td>[look: 4 | smell: 4 | taste: 4 | feel: 4 |  ov...</td>
      <td>4.00</td>
      <td>5.0</td>
      <td>An impressive (and very underrated) beer.  A s...</td>
      <td>4.00</td>
      <td>4.00</td>
      <td>LAp</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3.71</td>
      <td>+1.4%</td>
      <td>NaN</td>
      <td>★</td>
      <td>2016-02-20</td>
      <td>3.5</td>
      <td>3.50</td>
      <td>[look: 3.5 | smell: 3.75 | taste: 3.75 | feel:...</td>
      <td>3.75</td>
      <td>5.0</td>
      <td>330ml bottle - dubbed a smoked/spiced stout, w...</td>
      <td>3.75</td>
      <td>3.75</td>
      <td>biboergosum</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.26</td>
      <td>+16.4%</td>
      <td>NaN</td>
      <td>★</td>
      <td>2016-02-12</td>
      <td>4.0</td>
      <td>3.75</td>
      <td>[look: 3.75 | smell: 4.5 | taste: 4.25 | feel:...</td>
      <td>4.25</td>
      <td>5.0</td>
      <td>Poured into pint.\nPours opaque dark brown wit...</td>
      <td>4.50</td>
      <td>4.25</td>
      <td>Dentist666</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_reviews['perc_diff'] = ''
df_reviews.loc[df_reviews['color:#006600;'].notnull(), 'perc_diff'] = df_reviews[df_reviews['color:#006600;'].notnull()]['color:#006600;']
df_reviews.loc[df_reviews['color:#990000;'].notnull(), 'perc_diff'] = df_reviews[df_reviews['color:#990000;'].notnull()]['color:#990000;']

print np.sum(df_reviews['perc_diff'].isnull())

df_reviews.perc_diff.describe()
```




    count        41
    unique       38
    top       +2.5%
    freq          2
    Name: perc_diff, dtype: object



## choose final dataframe columns


```python
df_reviews.columns
```




    Index([  u'BAscore_norm', u'color:#006600;', u'color:#990000;',
           u'color:#CC8A00;',       u'datetime',           u'feel',
                     u'look',          u'muted',        u'overall',
                u'rAvg_norm',         u'review',          u'smell',
                    u'taste',           u'user',      u'perc_diff'],
          dtype='object')




```python
df_reviews = df_reviews[[u'datetime', u'user', u'BAscore_norm', u'look', u'smell', u'taste', u'feel', u'overall',
                         u'rAvg_norm', u'perc_diff', u'review']]

print df_reviews.head(3)
df_reviews.describe()
```

        datetime         user  BAscore_norm  look  smell  taste  feel  overall  \
    0 2016-05-30          LAp          4.00  4.00   4.00   4.00   4.0     4.00   
    1 2016-02-20  biboergosum          3.71  3.50   3.75   3.75   3.5     3.75   
    2 2016-02-12   Dentist666          4.26  3.75   4.50   4.25   4.0     4.25   
    
       rAvg_norm perc_diff                                             review  
    0        5.0     +9.3%  An impressive (and very underrated) beer.  A s...  
    1        5.0     +1.4%  330ml bottle - dubbed a smoked/spiced stout, w...  
    2        5.0    +16.4%  Poured into pint.\nPours opaque dark brown wit...  
    




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>BAscore_norm</th>
      <th>look</th>
      <th>smell</th>
      <th>taste</th>
      <th>feel</th>
      <th>overall</th>
      <th>rAvg_norm</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>41.000000</td>
      <td>39.000000</td>
      <td>39.000000</td>
      <td>39.000000</td>
      <td>39.000000</td>
      <td>39.000000</td>
      <td>41.0</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>3.664878</td>
      <td>3.807692</td>
      <td>3.685897</td>
      <td>3.692308</td>
      <td>3.557692</td>
      <td>3.608974</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.624284</td>
      <td>0.542477</td>
      <td>0.660736</td>
      <td>0.759721</td>
      <td>0.710498</td>
      <td>0.830731</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2.330000</td>
      <td>2.500000</td>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>1.500000</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>3.500000</td>
      <td>3.500000</td>
      <td>3.500000</td>
      <td>3.500000</td>
      <td>3.000000</td>
      <td>3.500000</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>3.900000</td>
      <td>4.000000</td>
      <td>4.000000</td>
      <td>4.000000</td>
      <td>3.500000</td>
      <td>4.000000</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>4.050000</td>
      <td>4.000000</td>
      <td>4.000000</td>
      <td>4.000000</td>
      <td>4.000000</td>
      <td>4.000000</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>max</th>
      <td>4.720000</td>
      <td>5.000000</td>
      <td>5.000000</td>
      <td>5.000000</td>
      <td>4.500000</td>
      <td>5.000000</td>
      <td>5.0</td>
    </tr>
  </tbody>
</table>
</div>



## exploratory plots

source: http://pandas.pydata.org/pandas-docs/stable/visualization.html


```python
categories = [u'look', u'smell', u'taste', u'feel', u'overall']
```


```python
plt.figure(figsize=(10,6))
plt.plot(df_reviews.datetime, df_reviews.BAscore_norm)
```




    [<matplotlib.lines.Line2D at 0x26466ba8>]




![png](output_19_1.png)



```python
df_reviews[categories].hist(figsize=(10,6))
```




    array([[<matplotlib.axes._subplots.AxesSubplot object at 0x00000000255130F0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x00000000258AAB70>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x0000000025971390>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x0000000025A93A90>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x0000000025B7D438>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x0000000025AAEEB8>]], dtype=object)




![png](output_20_1.png)



```python
df_reviews[categories].plot.box(figsize=(10,6))
```




    <matplotlib.axes._subplots.AxesSubplot at 0xd0a4080>




![png](output_21_1.png)



```python
from pandas.tools.plotting import scatter_matrix
```


```python
scatter_matrix(df_reviews[categories], figsize=(12, 12), s=50, diagonal='kde')
```




    array([[<matplotlib.axes._subplots.AxesSubplot object at 0x0000000020FFB7F0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x00000000211335F8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x00000000212AB400>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000000002134D668>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x0000000021451198>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x000000002136A908>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x00000000215B9B00>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x00000000216C04A8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x00000000217A3AC8>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x00000000218AA470>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x000000002191D588>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x0000000021A11FD0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x0000000021A23D68>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x0000000021BC7860>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x0000000021CBF208>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x0000000021DA3400>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x0000000021E59D68>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x0000000021F019B0>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000000002201E588>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x0000000022115EF0>],
           [<matplotlib.axes._subplots.AxesSubplot object at 0x00000000203C2518>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000000001BC1B128>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000000002220EF28>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x0000000022368780>,
            <matplotlib.axes._subplots.AxesSubplot object at 0x000000002246E208>]], dtype=object)




![png](output_23_1.png)



```python
df_reviews.BAscore_norm.describe()
```




    count    41.000000
    mean      3.664878
    std       0.624284
    min       2.330000
    25%       3.500000
    50%       3.900000
    75%       4.050000
    max       4.720000
    Name: BAscore_norm, dtype: float64



## create categories based on IQR


```python
df_reviews['verdict'] = 'aight'
df_reviews.loc[df_reviews['BAscore_norm'] <= 3.5, 'verdict'] = 'meh'
df_reviews.loc[df_reviews['BAscore_norm'] >= 4.05, 'verdict'] = 'solid'
df_reviews['verdict'].value_counts()
```

    C:\Users\rstancut\AppData\Local\Continuum\Anaconda2\lib\site-packages\ipykernel\__main__.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      if __name__ == '__main__':
    




    aight    19
    meh      11
    solid    11
    Name: verdict, dtype: int64




```python
from pandas.tools.plotting import parallel_coordinates
```


```python
plt.figure(figsize=(10,6))
parallel_coordinates(df_reviews[['look', 'smell', \
                                 'taste', 'feel', \
                                 'overall', 'verdict']],
                     'verdict')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x248826a0>




![png](output_28_1.png)


## now for some text analysis


```python
# but first we export what we've got so far
df_reviews.to_csv('deMolen_RookVuur/df_reviews.csv', encoding='utf8')
```


```python
rookvuur_reviews = []

for i in range(df_reviews.shape[0]):
    rookvuur_reviews.append(df_reviews.iloc[i, df_reviews.shape[1]-2])
    
print len(rookvuur_reviews)
print rookvuur_reviews[0][:150]
print rookvuur_reviews[-1][:150]
```

    41
    An impressive (and very underrated) beer.  A solid Rauchbier, and one of the few beers in which chili is a welcome ingredient.  De Molen seems to have
    I had it in a side by side tasting with Schlenkerla Rauch Märzen. It's the same quality but the Rook & Vuur is so more intense in many ways. More smok
    

## extend sklearn vectorizer with NLTK's stemmer

source: http://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.CountVectorizer.html


```python
from sklearn.feature_extraction.text import TfidfVectorizer
import nltk.stem

english_stemmer = nltk.stem.SnowballStemmer('english')

class StemmedTfidfVectorizer(TfidfVectorizer):
    def build_analyzer(self):
        analyzer = super(StemmedTfidfVectorizer, self).build_analyzer()
        return lambda doc: (english_stemmer.stem(w) for w in analyzer(doc))
```


```python
vectorizer = StemmedTfidfVectorizer(min_df=10, max_df=0.5,
                                    stop_words='english', 
                                    decode_error='ignore'
                                    )
```


```python
vectorized = vectorizer.fit_transform(rookvuur_reviews)
num_samples, num_features = vectorized.shape

print("#samples: %d, #features: %d" % (num_samples, num_features))
```

    #samples: 41, #features: 27
    


```python
print vectorizer.get_feature_names()
```

    [u'aroma', u'bit', u'bitter', u'black', u'bottl', u'chili', u'color', u'finish', u'flavor', u'glass', u'good', u'heat', u'just', u'light', u'like', u'medium', u'nice', u'nose', u'note', u'peat', u'pepper', u'realli', u'roast', u'smell', u'smoki', u'sweet', u'tan']
    


```python
vectorized.toarray()
```




    array([[ 0.        ,  0.        ,  0.        , ...,  0.        ,
             0.28498526,  0.        ],
           [ 0.        ,  0.27316199,  0.        , ...,  0.335601  ,
             0.29111453,  0.        ],
           [ 0.        ,  0.        ,  0.        , ...,  0.48909962,
             0.        ,  0.48909962],
           ..., 
           [ 0.        ,  0.        ,  0.        , ...,  0.25520435,
             0.44275013,  0.25520435],
           [ 0.1347047 ,  0.        ,  0.34123204, ...,  0.        ,
             0.14799957,  0.        ],
           [ 0.        ,  0.        ,  0.        , ...,  0.        ,
             0.        ,  0.        ]])




```python
# a peak at the scores for the first training post

xfeat_tfidf = zip([vectorizer.get_feature_names()[idx] for idx in [vectorized.toarray()[0].nonzero()][0][0]],
                  vectorized.toarray()[0][vectorized.toarray()[0].nonzero()])

print sorted(xfeat_tfidf, key=lambda t: t[-1], reverse=True)
```

    [(u'heat', 0.65707019256392507), (u'chili', 0.53482142551512724), (u'just', 0.32853509628196254), (u'good', 0.30507850530983954), (u'sweet', 0.2849852644662344)]
    

## hoping to find 'smoke' and 'spice' pairs

not so much


```python
from collections import Counter

cnt = Counter()

for i in range(41):

    xfeat_tfidf = zip([vectorizer.get_feature_names()[idx] for idx in [vectorized.toarray()[i].nonzero()][0][0]],
                      vectorized.toarray()[0][vectorized.toarray()[0].nonzero()])


    stuff = [t[0] for t in xfeat_tfidf]
#     print stuff

    for i in range(len(stuff)):
        for j in range(i+1):
            if stuff[i] == stuff[j]:
                pass
            else:
                pair = [stuff[i], stuff[j]]
                pair.sort()
                cnt['_'.join(pair)] += 1
            
cnt.most_common(10)

```




    [(u'aroma_bottl', 11),
     (u'bottl_finish', 10),
     (u'aroma_finish', 8),
     (u'bit_finish', 7),
     (u'bottl_chili', 7),
     (u'bit_chili', 7),
     (u'chili_finish', 7),
     (u'bitter_finish', 7),
     (u'aroma_chili', 7),
     (u'aroma_bit', 6)]




```python
# using k==3 due to previous `verdict` on BAscore above

num_clusters = 3
from sklearn.cluster import KMeans

km = KMeans(n_clusters=num_clusters, init='random', n_init=1, verbose=1)
km.fit(vectorized)
```

    Initialization complete
    Iteration  0, inertia 49.319
    Iteration  1, inertia 26.682
    Iteration  2, inertia 26.313
    Iteration  3, inertia 26.093
    Converged at iteration 3
    




    KMeans(copy_x=True, init='random', max_iter=300, n_clusters=3, n_init=1,
        n_jobs=1, precompute_distances='auto', random_state=None, tol=0.0001,
        verbose=1)




```python
my_review = "This beer was bottled in January 2015 I am now enjoying \
            it a year and half into its four year recommended window. \
            The nose is what you would expect from a rauchbier. It pours \
            enticingly dark with a thin head that does not build. \
            There is still some carbonation within the bottle witnessed \
            by bubbles casually drifting to the top. This beer is packing \
            an expected punch in both alcohol and flavor. I definitely \
            took the precaution of having a meal before, more for the \
            flavor than the solid ABV (8.5%). It packs such a flavor punch \
            that any food would have to accommodate itself to the beer, and \
            not the other way around. Initially coming out of the bottle the \
            smoke is most present in the nose and taste. However, as the beer \
            warms and we continue to sip from it we begin to get the spicy tingle."
```

## my review against clusters and find best label


```python
new_rev_vec = vectorizer.transform([my_review])
new_rev_label = km.predict(new_rev_vec)[0]
print new_rev_label
```

    0
    

## compare my review only against reviews in "best" cluster


```python
import scipy as sp

similar_indices = (km.labels_==new_rev_label).nonzero()[0]

similar = []
for i in similar_indices:
    dist = sp.linalg.norm((new_rev_vec - vectorized[i]).toarray())
    similar.append((dist, rookvuur_reviews[i], i))
    
similar = sorted(similar)
print(len(similar))
```

    13
    


```python
print similar_indices
print similar[0][2]
```

    [ 3  4  8  9 10 15 16 18 21 27 30 33 40]
    33
    


```python
# quick idea of kind of similar reviews, 
# present the most similar post (show_at_1), 
# the least similar one (show_at_3), and 
# an in-between post (show_at_2), 
# all of which are from the same cluster as follows:

show_at_1 = similar[0]
show_at_2 = similar[len(similar)/2]
show_at_3 = similar[-1]
```


```python
print show_at_1[1]
```

    Bottle purchased at Maruhn's in Darmstadt, Hessen. Brewed on January 20, 2011, bottled February 18, 2011, tasted January 5, 2012.
    
    Bottle number 167/432
    
    Pours a dark, nearly black color with an enormous head; the beer completely gushed out of the bottle when I opened it.
    
    Aromas of red peppers, green olives, chocolate and sea salt. There is something definitely salty about the nose.
    
    The flavor nearly knocked me over. Very intense with tremendous complexity, I could easily sip and analyze this all night. It starts a little sour with a cherry fruit flavor, progresses to a nicely hoppy bitter taste, evolves into chocolate, oak, and smoke flavors, finally finishing with chilis and an overriding peat. This is definitely a dark roasted beer, but what surprises me is how balanced the smoke and peat flavors are. This isn't a smoked beer, nor does it taste like it was aged in oak barrels (which it wasn't). But their peat smoked malts add just the right amount of extra character to really take this beer up to the next level.
    
    This beer really blew me away for all its complexity and uniqueness, while constantly maintaining the perfect balance of all its flavors. My particular bottle almost had a brett flavor to it's sourness; it makes me wonder if they did any natural fermentation.
    
    Certainly worth drinking; track it down if you can.
    
    As an aside, I enjoyed half the bottle with chicken molé, and the combination was fabulous. 
    


```python
print show_at_2[1]
```

    in my eyes these guys are becoming one of the kings, and frankly have been for some time, ahead of their time really, and i am only just discovering so many of their awesome beers now. just fantastic stuff here, smoked imperial porter with chili peppers. not sure how old this is, but the peppers must have faded off a bit, as they are there in faint flavor, accent notes, but no heat at all, and its all way back. crazy pour like a lot of their other stuff, with a super tall mocha head of large soda bubbles and a dense chocolate brown color to the beer itself. the nose shows a lot of smoke right up front, almost peaty for a moment, wet and musky, with their familiar high gravity yeast in there as well. the peppers are way back, like in a dark chocolate bar, and bring out nuance without being a chili beer as most americans think of them. the flavor is really balanced between the smoke and the fire, which is what this label means. the booze serves to cut the intensity, and unite the elements. the yeast is again the star of another de molen beer, this time drying it out with a day old bread crust complexion and impossibly high carbonation. one of the things i like about these guys is their use of subtle european hops usually seen in pilsener types in these huge imperial stouts and porters. it gives the beers a very unique hop character and feel, and its common in several of their beers. these guys are pioneers, and while this one isnt my favorite that they do, its certainly up to the very high standards they have established with their other stuff. 
    


```python
print show_at_3[1]
```

    Maybe the one I got was bad, but it tasted like sour cigarette smoke. I like sour beers and I like smoked beers. The problem is this taste like it shouldn't be sour. 
    

## look at same reviews from above in dataframe


```python
print [show_at_1[2], show_at_2[2], show_at_3[2]]

df_reviews.iloc[[show_at_1[2], show_at_2[2], show_at_3[2]]]
```

    [33, 9, 10]
    




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>datetime</th>
      <th>user</th>
      <th>BAscore_norm</th>
      <th>look</th>
      <th>smell</th>
      <th>taste</th>
      <th>feel</th>
      <th>overall</th>
      <th>rAvg_norm</th>
      <th>perc_diff</th>
      <th>review</th>
      <th>verdict</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>33</th>
      <td>2012-01-08</td>
      <td>rinhaak</td>
      <td>4.60</td>
      <td>4.00</td>
      <td>4.00</td>
      <td>5.00</td>
      <td>4.00</td>
      <td>5.00</td>
      <td>5.0</td>
      <td>+25.7%</td>
      <td>Bottle purchased at Maruhn's in Darmstadt, Hes...</td>
      <td>solid</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2015-06-30</td>
      <td>StonedTrippin</td>
      <td>4.25</td>
      <td>4.25</td>
      <td>4.25</td>
      <td>4.25</td>
      <td>4.25</td>
      <td>4.25</td>
      <td>5.0</td>
      <td>+16.1%</td>
      <td>in my eyes these guys are becoming one of the ...</td>
      <td>solid</td>
    </tr>
    <tr>
      <th>10</th>
      <td>2014-12-24</td>
      <td>Cheebacheebs</td>
      <td>2.61</td>
      <td>3.50</td>
      <td>3.75</td>
      <td>2.00</td>
      <td>2.00</td>
      <td>2.50</td>
      <td>5.0</td>
      <td>-28.7%</td>
      <td>Maybe the one I got was bad, but it tasted lik...</td>
      <td>meh</td>
    </tr>
  </tbody>
</table>
</div>


