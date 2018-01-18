---
layout: page
title: endlesspint
subtitle: Data Guide for the Beer Perplexed, Part V - PageRank and Lineage
---

```python
import csv, os
import numpy as np
import pandas as pd
# print pd.__version__

from datetime import datetime

import matplotlib.pyplot as plt
import matplotlib
matplotlib.style.use('ggplot')
%matplotlib inline


```

## data import


```python
cb_data = pd.read_csv('data/b_styles_expanded.csv')

print cb_data.dtypes
cb_data.tail()
```

    Unnamed: 0                    int64
    Unnamed: 0.1                  int64
    beer_style                   object
    cheese                       object
    Finish Length                object
    Phenols                      object
    Alcohol                      object
    Hops                         object
    dessert                      object
    Malt                         object
    other_styles                 object
    glass                        object
    descrip_long                 object
    Hop                          object
    Body                         object
    dish                         object
    Carbonation (Visual)         object
    category                     object
    Esters                       object
    Attenuation                  object
    temp                         object
    Yeast                        object
    Color                        object
    srm                          object
    Water                        object
    abv                          object
    Carbonation                  object
    Clarity                      object
    ibu                          object
    Fermentation By-Products     object
                                 ...   
    fruity                      float64
    hoppy                       float64
    malty                       float64
    nutty                       float64
    sour                        float64
    spicy                       float64
    abv_max                     float64
    abv_min                     float64
    ibu_max                     float64
    ibu_min                     float64
    srm_max                     float64
    srm_min                     float64
    temp_max                    float64
    temp_min                    float64
    temp_avg                    float64
    temp_range                  float64
    srm_avg                     float64
    srm_range                   float64
    abv_avg                     float64
    abv_range                   float64
    ibu_avg                     float64
    ibu_range                   float64
    Flute                       float64
    Goblet                      float64
    Nonic Pint                  float64
    Snifter                     float64
    Thistle                     float64
    Tulip                       float64
    Varies                      float64
    Vase                        float64
    Length: 66, dtype: object
    




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>Unnamed: 0.1</th>
      <th>beer_style</th>
      <th>cheese</th>
      <th>Finish Length</th>
      <th>Phenols</th>
      <th>Alcohol</th>
      <th>Hops</th>
      <th>dessert</th>
      <th>Malt</th>
      <th>...</th>
      <th>ibu_avg</th>
      <th>ibu_range</th>
      <th>Flute</th>
      <th>Goblet</th>
      <th>Nonic Pint</th>
      <th>Snifter</th>
      <th>Thistle</th>
      <th>Tulip</th>
      <th>Varies</th>
      <th>Vase</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>72</th>
      <td>72</td>
      <td>72</td>
      <td>Session Beer</td>
      <td>Varies</td>
      <td>Varies</td>
      <td>Can be present.</td>
      <td>Not Detectable to Mild</td>
      <td>Varies</td>
      <td>Varies</td>
      <td>Varies</td>
      <td>...</td>
      <td>20.0</td>
      <td>20.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>73</th>
      <td>73</td>
      <td>73</td>
      <td>Smoke Beer</td>
      <td>Parmesan</td>
      <td>Varies</td>
      <td>Can be present.</td>
      <td>Varies</td>
      <td>Varies</td>
      <td>Gingerbread Cookies</td>
      <td>Varies</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>74</th>
      <td>74</td>
      <td>74</td>
      <td>Smoke Porter</td>
      <td>Red Dragon Cheddar</td>
      <td>Medium to Long</td>
      <td>Not  common to style</td>
      <td>Varies</td>
      <td>Kent Goldings, Willamette</td>
      <td>S'mores</td>
      <td>Crystal, Chocolate, Black Patent</td>
      <td>...</td>
      <td>30.0</td>
      <td>20.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>75</th>
      <td>75</td>
      <td>75</td>
      <td>Specialty Beer</td>
      <td>Varies</td>
      <td>Varies</td>
      <td>Can be present.</td>
      <td>Varies</td>
      <td>Varies</td>
      <td>Varies</td>
      <td>Varies</td>
      <td>...</td>
      <td>50.5</td>
      <td>99.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>76</th>
      <td>76</td>
      <td>76</td>
      <td>Vienna-Style Lager</td>
      <td>Mild Cheeses</td>
      <td>Short to Medium</td>
      <td>Not common to style.</td>
      <td>Mild</td>
      <td>German Noble</td>
      <td>Almond Biscotti</td>
      <td>Vienna</td>
      <td>...</td>
      <td>25.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 66 columns</p>
</div>




```python
# cb_data.to_csv('data/cb_data.csv', sep=';')
```


```python
style_category = cb_data[['beer_style', 'category', 'other_styles']]
style_category.tail()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>beer_style</th>
      <th>category</th>
      <th>other_styles</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>72</th>
      <td>Session Beer</td>
      <td>Specialty Beers</td>
      <td>[English-Style Bitter, Irish-Style Dry Stout, ...</td>
    </tr>
    <tr>
      <th>73</th>
      <td>Smoke Beer</td>
      <td>Specialty Beers</td>
      <td>[English-Style Old Ale, American Brett, Herb a...</td>
    </tr>
    <tr>
      <th>74</th>
      <td>Smoke Porter</td>
      <td>Porters</td>
      <td>[English-Style Old Ale, American Brett, Herb a...</td>
    </tr>
    <tr>
      <th>75</th>
      <td>Specialty Beer</td>
      <td>Specialty Beers</td>
      <td>[Belgian-Style Fruit Lambic, Herb and Spice Be...</td>
    </tr>
    <tr>
      <th>76</th>
      <td>Vienna-Style Lager</td>
      <td>Dark Lagers</td>
      <td>[English-Style Bitter, German-Style Bock, Belg...</td>
    </tr>
  </tbody>
</table>
</div>




```python
style_category.other_styles[0][1:-1].split(',')
```




    ['English-Style Pale Ale/ESB', ' English-Style Mild', ' American Amber Lager']




```python
# style_category.other_styles.str.slice(1,-1)
```


```python
style_cat_dict = cb_data[['beer_style', 'category', 'other_styles']].to_dict('records')
print style_cat_dict[:3]
print ''

for style in style_cat_dict:
    style['other_styles'] = style['other_styles'][1:-1].split(', ')
    if style['other_styles'] == ['']:
        style['other_styles'] = []
        
print style_cat_dict[:3]
print ''
print style_cat_dict[61]['other_styles']
```

    [{'category': 'Pale Ales', 'beer_style': 'American Amber Ale', 'other_styles': '[English-Style Pale Ale/ESB, English-Style Mild, American Amber Lager]'}, {'category': 'Dark Lagers', 'beer_style': 'American Amber Lager', 'other_styles': '[German-Style Marzen/Oktoberfest, Vienna-Style Lager, English-Style Mild]'}, {'category': 'Strong Ales', 'beer_style': 'American Barley Wine', 'other_styles': '[Imperial India Pale Ale, German-Style Doppelbock, Scotch Ale/Wee Heavy]'}]
    
    [{'category': 'Pale Ales', 'beer_style': 'American Amber Ale', 'other_styles': ['English-Style Pale Ale/ESB', 'English-Style Mild', 'American Amber Lager']}, {'category': 'Dark Lagers', 'beer_style': 'American Amber Lager', 'other_styles': ['German-Style Marzen/Oktoberfest', 'Vienna-Style Lager', 'English-Style Mild']}, {'category': 'Strong Ales', 'beer_style': 'American Barley Wine', 'other_styles': ['Imperial India Pale Ale', 'German-Style Doppelbock', 'Scotch Ale/Wee Heavy']}]
    
    []
    


```python
beer_list = cb_data.beer_style.tolist()
beer_list[-5:]
```




    ['Session Beer',
     'Smoke Beer',
     'Smoke Porter',
     'Specialty Beer',
     'Vienna-Style Lager']




```python
# possible links across all styles
77*76/2
```




    2926




```python
cb_DiLinks = []

for style in style_cat_dict:
    if len(style['other_styles']) > 0:
        for other in style['other_styles']:
            cb_DiLinks.append((style['beer_style'], other))
            
print len(cb_DiLinks)
cb_DiLinks[:10]
```

    187
    




    [('American Amber Ale', 'English-Style Pale Ale/ESB'),
     ('American Amber Ale', 'English-Style Mild'),
     ('American Amber Ale', 'American Amber Lager'),
     ('American Amber Lager', 'German-Style Marzen/Oktoberfest'),
     ('American Amber Lager', 'Vienna-Style Lager'),
     ('American Amber Lager', 'English-Style Mild'),
     ('American Barley Wine', 'Imperial India Pale Ale'),
     ('American Barley Wine', 'German-Style Doppelbock'),
     ('American Barley Wine', 'Scotch Ale/Wee Heavy'),
     ('American Black Ale', 'Robust Porter')]




```python
import networkx as nx

# colors from our friends at http://colorbrewer2.org
COLORS = ['#8dd3c7','#ffffb3','#bebada','#fb8072','#80b1d3','#fdb462',
          '#b3de69','#fccde5','#d9d9d9','#bc80bd','#ccebc5','#ffed6f']
```


```python
G_toy = nx.DiGraph()
G_toy.add_nodes_from(['Alice', 'Bob', 'Chuck', 'Dick', 'Edgar', 'Fred'])
G_toy.nodes()
```




    ['Dick', 'Alice', 'Edgar', 'Fred', 'Chuck', 'Bob']




```python
G_toy.add_edges_from([('Alice', 'Bob'), ('Alice', 'Chuck'), ('Bob', 'Alice'), ('Bob', 'Chuck'),
                      ('Chuck', 'Dick'), ('Alice', 'Dick'), ('Bob', 'Edgar'), ('Edgar', 'Bob'),
                      ('Dick', 'Fred'), ('Fred' , 'Dick')
                     ])
G_toy.edges()
```




    [('Dick', 'Fred'),
     ('Alice', 'Bob'),
     ('Alice', 'Dick'),
     ('Alice', 'Chuck'),
     ('Edgar', 'Bob'),
     ('Fred', 'Dick'),
     ('Chuck', 'Dick'),
     ('Bob', 'Alice'),
     ('Bob', 'Edgar'),
     ('Bob', 'Chuck')]




```python

```


```python
nx.draw_circular(G_toy, 
                 node_color=COLORS[0], 
                 node_size=2000, 
                 with_labels=True)
plt.axis('equal')
```




    (-1.5, 1.5, -1.5, 1.5)




<img src = "/code/beer_prplxd_V/output_15_1.png">


## Directed Graph


```python
G = nx.DiGraph()

G.add_nodes_from(beer_list)
print len(G.nodes())
G.nodes()[:3]
```

    77
    




    ['German-Style Bock', 'German-Style Dunkelweizen', 'Belgian-Style Tripel']




```python
G.add_edges_from(cb_DiLinks)
print len(G.edges())
G.edges()[:3]
```

    186
    




    [('German-Style Bock', 'Belgian-Style Dubbel'),
     ('German-Style Bock', 'American Amber Lager'),
     ('German-Style Dunkelweizen', 'English-Style Brown Ale')]




```python
# why is the edge count lower than list len?
# must be a dupe
# https://stackoverflow.com/questions/9835762/find-and-list-duplicates-in-a-list

set([x for x in cb_DiLinks if cb_DiLinks.count(x) > 1])
```




    {('Rye Beer', 'Herb and Spice Beer')}



## PageRank


```python
nx.pagerank(G, max_iter=1000)
```




    {'American Amber Ale': 0.014582164068922921,
     'American Amber Lager': 0.025391424521712974,
     'American Barley Wine': 0.0020602941879801764,
     'American Black Ale': 0.03524226870144604,
     'American Brett': 0.02595062159582658,
     'American Brown Ale': 0.018426950422189954,
     'American Cream Ale': 0.0058283900725772265,
     'American Imperial Porter': 0.003514312388015356,
     'American Imperial Red Ale': 0.0029880065204832495,
     'American Imperial Stout': 0.0020602941879801764,
     'American India Pale Ale/IPA': 0.023727626131963907,
     'American Pale Ale': 0.010514226095834273,
     'American Sour': 0.05576906759108761,
     'American Stout': 0.0020602941879801764,
     'American Wheat': 0.02709132371840384,
     'American-Style Wheat Wine Ale': 0.0028094467632845087,
     'Baltic-Style Porter': 0.003274237915072287,
     'Barrel-Aged Beer': 0.05209433396378796,
     'Belgian-Style Blonde Ale': 0.0028563107818306375,
     'Belgian-Style Dubbel': 0.059656549110350024,
     'Belgian-Style Flanders': 0.0020602941879801764,
     'Belgian-Style Fruit Lambic': 0.002644044296828293,
     'Belgian-Style Golden Strong Ale': 0.009654698646410383,
     'Belgian-Style Lambic/Gueuze': 0.0165306709842972,
     'Belgian-Style Pale Ale': 0.021346693322413936,
     'Belgian-Style Quadrupel': 0.006043600643162409,
     'Belgian-Style Saison': 0.002644044296828293,
     'Belgian-Style Tripel': 0.03326817397479022,
     'Belgian-Style Wit': 0.03302477253969235,
     'Berliner-Style Weisse': 0.004614446345485116,
     'Blonde Ale': 0.006009608789874498,
     'Bohemian-Style Pilsener': 0.011416945753781337,
     'British-Style Barley Wine Ale': 0.0020602941879801764,
     'California Common': 0.0020602941879801764,
     'Chocolate Beer': 0.005131724883279979,
     'Coffee Beer': 0.005265562714559706,
     'English-Style Bitter': 0.011211835358211469,
     'English-Style Brown Ale': 0.018996373601948575,
     'English-Style Brown Porter': 0.03332469398697684,
     'English-Style India Pale Ale/IPA': 0.012999718806943639,
     'English-Style Mild': 0.018768276979798208,
     'English-Style Oatmeal Stout': 0.0020602941879801764,
     'English-Style Old Ale': 0.0095770010214148,
     'English-Style Pale Ale/ESB': 0.009850525239380759,
     'English-Style Sweet Stout (Milk Stout)': 0.015491522106287861,
     'European-Style Export': 0.0020602941879801764,
     'French-Style Biere de Garde': 0.0020602941879801764,
     'Fruit and Field Beer': 0.05107155015442901,
     'German-Style Bock': 0.016411283674223277,
     'German-Style Brown/Altbier': 0.0020602941879801764,
     'German-Style Doppelbock': 0.01492484922048327,
     'German-Style Dunkel': 0.03378873176318905,
     'German-Style Dunkelweizen': 0.0028563107818306375,
     'German-Style Hefeweizen': 0.016976287891728965,
     'German-Style Helles': 0.003807596085600591,
     'German-Style Kolsch': 0.008609285690684169,
     'German-Style Maibock': 0.01148588047023225,
     'German-Style Marzen/Oktoberfest': 0.01293765353918299,
     'German-Style Pilsener': 0.025135139197141255,
     'German-Style Schwarzbier': 0.00431511378636796,
     'German-Style Weizenbock': 0.002644044296828293,
     'Gluten Free': 0.0020602941879801764,
     'Herb and Spice Beer': 0.007018221684265235,
     'Honey Beer': 0.006166855994626241,
     'Imperial India Pale Ale': 0.012069630579080367,
     'Irish-Style Dry Stout': 0.007957892512966488,
     'Irish-Style Red': 0.0020602941879801764,
     'Pumpkin Beer': 0.0020602941879801764,
     'Robust Porter': 0.014723679453298067,
     'Rye Beer': 0.0020602941879801764,
     'Scotch Ale/Wee Heavy': 0.008993250912566685,
     'Scottish-Style Ale': 0.013249163088915621,
     'Session Beer': 0.005986237697278011,
     'Smoke Beer': 0.0020602941879801764,
     'Smoke Porter': 0.0020602941879801764,
     'Specialty Beer': 0.0020602941879801764,
     'Vienna-Style Lager': 0.026314145674263253}




```python
import operator
x = nx.pagerank(G, max_iter=1000)
sorted_x = sorted(x.items(), key=operator.itemgetter(1))
```


```python
sorted_x[-5:]
```




    [('American Black Ale', 0.03524226870144604),
     ('Fruit and Field Beer', 0.05107155015442901),
     ('Barrel-Aged Beer', 0.05209433396378796),
     ('American Sour', 0.05576906759108761),
     ('Belgian-Style Dubbel', 0.059656549110350024)]




```python
nodelist = ['Belgian-Style Dubbel']

for n in G.neighbors('Belgian-Style Dubbel'):
    nodelist.append(n)
    nodelist.extend(G.neighbors(n))
    
nodelist = list(set(nodelist))
nodelist
```




    ['Barrel-Aged Beer',
     'Belgian-Style Dubbel',
     'Belgian-Style Lambic/Gueuze',
     'American Brown Ale',
     'German-Style Dunkel',
     'Fruit and Field Beer',
     'American Sour',
     'English-Style Brown Porter']



## Have isolated nodes, but now need their edges too


```python
nx.draw_circular(G, 
                 nodelist=nodelist,
                 node_color=COLORS[0], 
                 node_size=2000, 
                 with_labels=True)
plt.axis('equal')
```




    (-1.5, 1.5, -1.5, 1.5)




<img src = "/code/beer_prplxd_V/output_26_1.png">



```python
nx.draw_networkx_nodes(G, pos=nx.circular_layout(G), nodelist=nodelist,
                       node_color=COLORS[0], 
                       node_size=2000, 
                       with_labels=True)
plt.axis('equal')
```




    (-1.5, 1.5, -1.5, 1.5)




<img src = "/code/beer_prplxd_V/output_27_1.png">



```python
G.predecessors('Belgian-Style Dubbel')
```




    ['German-Style Bock',
     'English-Style India Pale Ale/IPA',
     'English-Style Brown Ale',
     'Irish-Style Red',
     'German-Style Dunkel',
     'German-Style Schwarzbier',
     'German-Style Brown/Altbier',
     'English-Style Brown Porter',
     'American Imperial Porter',
     'Vienna-Style Lager',
     'Irish-Style Dry Stout',
     'Scottish-Style Ale']




```python
for link in cb_DiLinks:
    if link[0] == 'Belgian-Style Dubbel':
        print link
```

    ('Belgian-Style Dubbel', 'English-Style Brown Porter')
    ('Belgian-Style Dubbel', 'German-Style Dunkel')
    ('Belgian-Style Dubbel', 'Fruit and Field Beer')
    

## features and sorting


```python
# def parent_cnt(G, style):
#     '''
#     Count of networkx predecessors.
    
#     Parameters
#     ----------
#     G     : netorkx graph
#     sytle : beer style node
    
#     Returns
#     -------
#     int
#     '''
    
#     return len(G.predecessors(style))
    
# parent_cnt(G, 'Belgian-Style Dubbel')

###

def grandpappy_cnt(G, style, unique=False):
    '''
    Count of networkx predecessors' predecessors, i.e., grandparents two levels up.
    
    Parameters
    ----------
    G      : netorkx graph
    sytle  : beer style node
    unique : whether to count unique grandparent styles; default==False
    
    Returns
    -------
    int
    '''
    gp_cnt = 0
    
    if unique:
        gp_list = []
        for parent in G.predecessors(style):
            gp_list.extend(G.predecessors(parent))
        gp_cnt = len(set(gp_list))
        
    else:        
        for parent in G.predecessors(style):
            gp_cnt += len(G.predecessors(parent))
        
    return gp_cnt
        
grandpappy_cnt(G, 'Belgian-Style Dubbel', unique=True)
```




    27




```python
len(G.neighbors('Belgian-Style Dubbel'))
```




    3




```python
[(pred) for pred in G.predecessors('American Black Ale')]
```




    ['Robust Porter',
     'Imperial India Pale Ale',
     'American India Pale Ale/IPA',
     'English-Style Sweet Stout (Milk Stout)']




```python
pr_dict = {x[0]:x[1] for x in sorted_x}
```


```python
# https://stackoverflow.com/questions/952914/making-a-flat-list-out-of-list-of-lists-in-python
# flat_list = [item for sublist in l for item in sublist]

l=[G.predecessors(pred) for pred in G.predecessors('American Sour')]
np.mean([pr_dict[pred] for pred in set([item for sublist in l for item in sublist])])
```




    0.022757348312791126




```python
feat_list = []

for k in G.nodes_iter():
    temp_dict = {}
    parents = len(G.predecessors(k))
    parent_avg = np.mean([pr_dict[pred] for pred in G.predecessors(k)])
    total_parent_links = np.sum([len(G.successors(pred)) for pred in G.predecessors(k)])
    share_of_parent_links = float(parents)/total_parent_links
    grandparents = [G.predecessors(pred) for pred in G.predecessors(k)]
    grandparent_avg = np.mean([pr_dict[pred] for pred in set([item for sublist in grandparents for item in sublist])])
    children = len(G.successors(k))
    
    if children > 0:
        ratio = float(parents)/children
    else:
        ratio = np.nan
       
    temp_dict['grandparents'], temp_dict['grandparent_PR_avg'],\
    temp_dict['parents'], temp_dict['parent_PR_avg'], temp_dict['share_of_parent_links'],\
    temp_dict['style'], temp_dict['children'], temp_dict['ratio'],\
            temp_dict['PageRank'] = grandpappy_cnt(G, k, unique=True), grandparent_avg,\
                                        parents, parent_avg, share_of_parent_links,\
                                        k, children, ratio, pr_dict[k]
        
    feat_list.append(temp_dict)

df_feat = pd.DataFrame(feat_list, columns=['style', 'PageRank', 'children',\
                                           'parents', 'parent_PR_avg', 'share_of_parent_links',\
                                           'grandparents', 'grandparent_PR_avg']).sort_values('PageRank', ascending=False)
# df_feat = df_feat.sort_values('page_rank', ascending=False)
df_feat.head(10)
```

    C:\Users\rstancut\AppData\Local\Continuum\Anaconda2\lib\site-packages\ipykernel\__main__.py:8: RuntimeWarning: invalid value encountered in double_scalars
    




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>style</th>
      <th>PageRank</th>
      <th>children</th>
      <th>parents</th>
      <th>parent_PR_avg</th>
      <th>share_of_parent_links</th>
      <th>grandparents</th>
      <th>grandparent_PR_avg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>39</th>
      <td>Belgian-Style Dubbel</td>
      <td>0.059657</td>
      <td>3</td>
      <td>12</td>
      <td>0.014583</td>
      <td>0.375000</td>
      <td>27</td>
      <td>0.014047</td>
    </tr>
    <tr>
      <th>71</th>
      <td>American Sour</td>
      <td>0.055769</td>
      <td>3</td>
      <td>6</td>
      <td>0.027033</td>
      <td>0.375000</td>
      <td>17</td>
      <td>0.022757</td>
    </tr>
    <tr>
      <th>59</th>
      <td>Barrel-Aged Beer</td>
      <td>0.052094</td>
      <td>2</td>
      <td>5</td>
      <td>0.033770</td>
      <td>0.357143</td>
      <td>22</td>
      <td>0.018776</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Fruit and Field Beer</td>
      <td>0.051072</td>
      <td>3</td>
      <td>7</td>
      <td>0.022776</td>
      <td>0.350000</td>
      <td>24</td>
      <td>0.014908</td>
    </tr>
    <tr>
      <th>5</th>
      <td>American Black Ale</td>
      <td>0.035242</td>
      <td>3</td>
      <td>4</td>
      <td>0.016503</td>
      <td>0.571429</td>
      <td>12</td>
      <td>0.011367</td>
    </tr>
    <tr>
      <th>8</th>
      <td>German-Style Dunkel</td>
      <td>0.033789</td>
      <td>2</td>
      <td>3</td>
      <td>0.037326</td>
      <td>0.333333</td>
      <td>16</td>
      <td>0.016987</td>
    </tr>
    <tr>
      <th>19</th>
      <td>English-Style Brown Porter</td>
      <td>0.033325</td>
      <td>3</td>
      <td>2</td>
      <td>0.046723</td>
      <td>0.400000</td>
      <td>13</td>
      <td>0.018050</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Belgian-Style Tripel</td>
      <td>0.033268</td>
      <td>3</td>
      <td>5</td>
      <td>0.016726</td>
      <td>0.384615</td>
      <td>15</td>
      <td>0.013445</td>
    </tr>
    <tr>
      <th>63</th>
      <td>Belgian-Style Wit</td>
      <td>0.033025</td>
      <td>3</td>
      <td>5</td>
      <td>0.018597</td>
      <td>0.416667</td>
      <td>18</td>
      <td>0.013387</td>
    </tr>
    <tr>
      <th>38</th>
      <td>American Wheat</td>
      <td>0.027091</td>
      <td>2</td>
      <td>5</td>
      <td>0.016703</td>
      <td>0.357143</td>
      <td>10</td>
      <td>0.022229</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_feat.sort_values('parents', ascending=False).head(5)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>style</th>
      <th>PageRank</th>
      <th>children</th>
      <th>parents</th>
      <th>parent_PR_avg</th>
      <th>share_of_parent_links</th>
      <th>grandparents</th>
      <th>grandparent_PR_avg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>39</th>
      <td>Belgian-Style Dubbel</td>
      <td>0.059657</td>
      <td>3</td>
      <td>12</td>
      <td>0.014583</td>
      <td>0.375000</td>
      <td>27</td>
      <td>0.014047</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Vienna-Style Lager</td>
      <td>0.026314</td>
      <td>3</td>
      <td>8</td>
      <td>0.010020</td>
      <td>0.380952</td>
      <td>15</td>
      <td>0.009974</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Fruit and Field Beer</td>
      <td>0.051072</td>
      <td>3</td>
      <td>7</td>
      <td>0.022776</td>
      <td>0.350000</td>
      <td>24</td>
      <td>0.014908</td>
    </tr>
    <tr>
      <th>71</th>
      <td>American Sour</td>
      <td>0.055769</td>
      <td>3</td>
      <td>6</td>
      <td>0.027033</td>
      <td>0.375000</td>
      <td>17</td>
      <td>0.022757</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Herb and Spice Beer</td>
      <td>0.007018</td>
      <td>2</td>
      <td>6</td>
      <td>0.002745</td>
      <td>0.352941</td>
      <td>2</td>
      <td>0.004831</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_feat.sort_values('children', ascending=False).head(5)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>style</th>
      <th>PageRank</th>
      <th>children</th>
      <th>parents</th>
      <th>parent_PR_avg</th>
      <th>share_of_parent_links</th>
      <th>grandparents</th>
      <th>grandparent_PR_avg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>39</th>
      <td>Belgian-Style Dubbel</td>
      <td>0.059657</td>
      <td>3</td>
      <td>12</td>
      <td>0.014583</td>
      <td>0.375000</td>
      <td>27</td>
      <td>0.014047</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Smoke Porter</td>
      <td>0.002060</td>
      <td>3</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>52</th>
      <td>American Imperial Porter</td>
      <td>0.003514</td>
      <td>3</td>
      <td>1</td>
      <td>0.005132</td>
      <td>0.333333</td>
      <td>3</td>
      <td>0.003613</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Scottish-Style Ale</td>
      <td>0.013249</td>
      <td>3</td>
      <td>3</td>
      <td>0.013163</td>
      <td>0.333333</td>
      <td>9</td>
      <td>0.011831</td>
    </tr>
    <tr>
      <th>7</th>
      <td>English-Style India Pale Ale/IPA</td>
      <td>0.013000</td>
      <td>3</td>
      <td>3</td>
      <td>0.012871</td>
      <td>0.333333</td>
      <td>5</td>
      <td>0.017641</td>
    </tr>
  </tbody>
</table>
</div>




```python
# df_feat.sort_values('ratio', ascending=False).head(5)
```


```python
# df_feat.sort_values('ratio').head(5)
```


```python
df_feat['style'].tolist()[:5]
```




    ['Belgian-Style Dubbel',
     'American Sour',
     'Barrel-Aged Beer',
     'Fruit and Field Beer',
     'American Black Ale']




```python
for style in df_feat['style'].tolist()[:5]:
    print grandpappy_cnt(G, style, unique=True)
```

    27
    17
    22
    24
    12
    

## sub graphing


```python
cb_BSD_parents = []

for link in cb_DiLinks:
    if link[1] == 'Belgian-Style Dubbel':
        cb_BSD_parents.append(link)
        
cb_BSD_parents
```




    [('American Imperial Porter', 'Belgian-Style Dubbel'),
     ('English-Style Brown Ale', 'Belgian-Style Dubbel'),
     ('English-Style Brown Porter', 'Belgian-Style Dubbel'),
     ('English-Style India Pale Ale/IPA', 'Belgian-Style Dubbel'),
     ('German-Style Bock', 'Belgian-Style Dubbel'),
     ('German-Style Brown/Altbier', 'Belgian-Style Dubbel'),
     ('German-Style Dunkel', 'Belgian-Style Dubbel'),
     ('German-Style Schwarzbier', 'Belgian-Style Dubbel'),
     ('Irish-Style Dry Stout', 'Belgian-Style Dubbel'),
     ('Irish-Style Red', 'Belgian-Style Dubbel'),
     ('Scottish-Style Ale', 'Belgian-Style Dubbel'),
     ('Vienna-Style Lager', 'Belgian-Style Dubbel')]




```python
cb_BSD_nodes = ['Belgian-Style Dubbel']
cb_BSD_nodes.extend([x[0] for x in cb_BSD_parents])
cb_BSD_nodes
```




    ['Belgian-Style Dubbel',
     'American Imperial Porter',
     'English-Style Brown Ale',
     'English-Style Brown Porter',
     'English-Style India Pale Ale/IPA',
     'German-Style Bock',
     'German-Style Brown/Altbier',
     'German-Style Dunkel',
     'German-Style Schwarzbier',
     'Irish-Style Dry Stout',
     'Irish-Style Red',
     'Scottish-Style Ale',
     'Vienna-Style Lager']




```python
G_bsd = nx.DiGraph()

G_bsd.add_nodes_from(cb_BSD_nodes)

G_bsd.add_edges_from(cb_BSD_parents)

nx.draw_circular(G_bsd, 
                 node_color=COLORS[0], 
                 node_size=2000, 
                 with_labels=True)
plt.axis('equal')
```




    (-1.5, 1.5, -1.5, 1.5)




<img src = "/code/beer_prplxd_V/output_46_1.png">



```python
nx.draw_spring(G_bsd, 
                 node_color=COLORS[0], 
                 node_size=2000, 
                 with_labels=True)
```


<img src = "/code/beer_prplxd_V/output_47_0.png">



```python
plt.figure(figsize=(12,12))
nx.draw_spring(G_bsd, 
                 node_color=range(len(cb_BSD_nodes)),
                 node_size=2000,
                 cmap=plt.cm.BrBG,
                 with_labels=True)
```


<img src = "/code/beer_prplxd_V/output_48_0.png">


## grandparents


```python
cb_BSD_parents
```




    [('American Imperial Porter', 'Belgian-Style Dubbel'),
     ('English-Style Brown Ale', 'Belgian-Style Dubbel'),
     ('English-Style Brown Porter', 'Belgian-Style Dubbel'),
     ('English-Style India Pale Ale/IPA', 'Belgian-Style Dubbel'),
     ('German-Style Bock', 'Belgian-Style Dubbel'),
     ('German-Style Brown/Altbier', 'Belgian-Style Dubbel'),
     ('German-Style Dunkel', 'Belgian-Style Dubbel'),
     ('German-Style Schwarzbier', 'Belgian-Style Dubbel'),
     ('Irish-Style Dry Stout', 'Belgian-Style Dubbel'),
     ('Irish-Style Red', 'Belgian-Style Dubbel'),
     ('Scottish-Style Ale', 'Belgian-Style Dubbel'),
     ('Vienna-Style Lager', 'Belgian-Style Dubbel')]




```python
G.predecessors('American Imperial Porter')
```




    ['Chocolate Beer']




```python
cb_BSD_grandparents = []

for parent in cb_BSD_parents:
#     print G.predecessors(parent[0])
    for link in cb_DiLinks:
        if link[1] == parent[0]:
            cb_BSD_grandparents.append(link)
            
cb_BSD_grandparents
```




    [('Chocolate Beer', 'American Imperial Porter'),
     ('Belgian-Style Pale Ale', 'English-Style Brown Ale'),
     ('German-Style Dunkelweizen', 'English-Style Brown Ale'),
     ('German-Style Marzen/Oktoberfest', 'English-Style Brown Ale'),
     ('Irish-Style Dry Stout', 'English-Style Brown Ale'),
     ('Scottish-Style Ale', 'English-Style Brown Ale'),
     ('Belgian-Style Dubbel', 'English-Style Brown Porter'),
     ('German-Style Dunkel', 'English-Style Brown Porter'),
     ('Bohemian-Style Pilsener', 'English-Style India Pale Ale/IPA'),
     ('California Common', 'English-Style India Pale Ale/IPA'),
     ('German-Style Pilsener', 'English-Style India Pale Ale/IPA'),
     ('Belgian-Style Golden Strong Ale', 'German-Style Bock'),
     ('English-Style Pale Ale/ESB', 'German-Style Bock'),
     ('Vienna-Style Lager', 'German-Style Bock'),
     ('Belgian-Style Dubbel', 'German-Style Dunkel'),
     ('English-Style Brown Ale', 'German-Style Dunkel'),
     ('English-Style Brown Porter', 'German-Style Dunkel'),
     ('Irish-Style Dry Stout', 'German-Style Schwarzbier'),
     ('American Stout', 'Irish-Style Dry Stout'),
     ('Coffee Beer', 'Irish-Style Dry Stout'),
     ('German-Style Schwarzbier', 'Irish-Style Dry Stout'),
     ('Session Beer', 'Irish-Style Dry Stout'),
     ('American Brown Ale', 'Scottish-Style Ale'),
     ('English-Style Bitter', 'Scottish-Style Ale'),
     ('English-Style Pale Ale/ESB', 'Scottish-Style Ale'),
     ('American Amber Lager', 'Vienna-Style Lager'),
     ('American Brown Ale', 'Vienna-Style Lager'),
     ('American Cream Ale', 'Vienna-Style Lager'),
     ('American Imperial Red Ale', 'Vienna-Style Lager'),
     ('Belgian-Style Flanders', 'Vienna-Style Lager'),
     ('Belgian-Style Pale Ale', 'Vienna-Style Lager'),
     ('California Common', 'Vienna-Style Lager'),
     ('French-Style Biere de Garde', 'Vienna-Style Lager')]




```python
cb_BSD_nodes2 = list(cb_BSD_nodes)
cb_BSD_nodes2.extend([x[0] for x in cb_BSD_grandparents])
cb_BSD_nodes2 = set(cb_BSD_nodes2)
cb_BSD_nodes2 = list(cb_BSD_nodes2)
cb_BSD_nodes2
```




    ['German-Style Bock',
     'German-Style Dunkelweizen',
     'Scottish-Style Ale',
     'English-Style India Pale Ale/IPA',
     'German-Style Dunkel',
     'Bohemian-Style Pilsener',
     'California Common',
     'Session Beer',
     'Chocolate Beer',
     'American Amber Lager',
     'Irish-Style Dry Stout',
     'German-Style Pilsener',
     'English-Style Bitter',
     'English-Style Brown Porter',
     'French-Style Biere de Garde',
     'Belgian-Style Pale Ale',
     'Vienna-Style Lager',
     'German-Style Marzen/Oktoberfest',
     'Belgian-Style Dubbel',
     'English-Style Brown Ale',
     'American Cream Ale',
     'American Brown Ale',
     'German-Style Schwarzbier',
     'American Imperial Porter',
     'Coffee Beer',
     'Belgian-Style Flanders',
     'Belgian-Style Golden Strong Ale',
     'Irish-Style Red',
     'German-Style Brown/Altbier',
     'English-Style Pale Ale/ESB',
     'American Stout',
     'American Imperial Red Ale']




```python
G_bsd2 = nx.DiGraph()


G_bsd2.add_nodes_from(cb_BSD_nodes2)

G_bsd2.add_edges_from(cb_BSD_parents)
G_bsd2.add_edges_from(cb_BSD_grandparents)
```


```python
plt.figure(figsize=(16,16))
nx.draw_spring(G_bsd2, 
                 node_color=range(len(cb_BSD_nodes2)),
                 node_size=2000,
                 cmap=plt.cm.BrBG,
                 with_labels=True)
```


<img src = "/code/beer_prplxd_V/output_55_0.png">



```python
plt.figure(figsize=(16,16))
nx.draw_circular(G_bsd2, 
                 node_color=range(len(cb_BSD_nodes2)),
                 node_size=2000,
                 cmap=plt.cm.BrBG,
                 with_labels=True)
```


<img src = "/code/beer_prplxd_V/output_56_0.png">



```python
plt.figure(figsize=(16,16))
nx.draw_random(G_bsd2, 
                 node_color=range(len(cb_BSD_nodes2)),
                 node_size=2000,
                 cmap=plt.cm.BrBG,
                 with_labels=True)
```


<img src = "/code/beer_prplxd_V/output_57_0.png">



```python
plt.figure(figsize=(16,16))
nx.draw_spectral(G_bsd2, 
                 node_color=range(len(cb_BSD_nodes2)),
                 node_size=2000,
                 cmap=plt.cm.BrBG,
                 with_labels=True)
```


<img src = "/code/beer_prplxd_V/output_58_0.png">


## let's try one more time with color, size/pagerank, dict


```python
BSD_grandpappies = pd.read_excel('cb_data.xlsx', sheetname='node_size_color')
BSD_grandpappies
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>node</th>
      <th>PageRank</th>
      <th>srm_avg</th>
      <th>hex</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Session Beer</td>
      <td>0.005986</td>
      <td>2.50</td>
      <td>#F8F753</td>
    </tr>
    <tr>
      <th>1</th>
      <td>German-Style Pilsener</td>
      <td>0.025135</td>
      <td>3.50</td>
      <td>#F6F513</td>
    </tr>
    <tr>
      <th>2</th>
      <td>American Cream Ale</td>
      <td>0.005828</td>
      <td>3.50</td>
      <td>#F6F513</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Bohemian-Style Pilsener</td>
      <td>0.011417</td>
      <td>5.00</td>
      <td>#ECE61A</td>
    </tr>
    <tr>
      <th>4</th>
      <td>English-Style Bitter</td>
      <td>0.011212</td>
      <td>8.50</td>
      <td>#BF923B</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Belgian-Style Pale Ale</td>
      <td>0.021347</td>
      <td>9.00</td>
      <td>#BF923B</td>
    </tr>
    <tr>
      <th>6</th>
      <td>German-Style Marzen/Oktoberfest</td>
      <td>0.012938</td>
      <td>9.50</td>
      <td>#BF923B</td>
    </tr>
    <tr>
      <th>7</th>
      <td>English-Style India Pale Ale/IPA</td>
      <td>0.013000</td>
      <td>10.00</td>
      <td>#BF813A</td>
    </tr>
    <tr>
      <th>8</th>
      <td>American Amber Lager</td>
      <td>0.025391</td>
      <td>10.00</td>
      <td>#BF813A</td>
    </tr>
    <tr>
      <th>9</th>
      <td>English-Style Pale Ale/ESB</td>
      <td>0.009851</td>
      <td>10.75</td>
      <td>#BF813A</td>
    </tr>
    <tr>
      <th>10</th>
      <td>California Common</td>
      <td>0.002060</td>
      <td>11.50</td>
      <td>#BF813A</td>
    </tr>
    <tr>
      <th>11</th>
      <td>French-Style Biere de Garde</td>
      <td>0.002060</td>
      <td>11.50</td>
      <td>#BF813A</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Scottish-Style Ale</td>
      <td>0.013249</td>
      <td>12.50</td>
      <td>#BF813A</td>
    </tr>
    <tr>
      <th>13</th>
      <td>American Imperial Red Ale</td>
      <td>0.002988</td>
      <td>13.00</td>
      <td>#BC6733</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Vienna-Style Lager</td>
      <td>0.026314</td>
      <td>14.00</td>
      <td>#BC6733</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Irish-Style Red</td>
      <td>0.002060</td>
      <td>14.50</td>
      <td>#BC6733</td>
    </tr>
    <tr>
      <th>16</th>
      <td>German-Style Brown/Altbier</td>
      <td>0.002060</td>
      <td>15.00</td>
      <td>#BC6733</td>
    </tr>
    <tr>
      <th>17</th>
      <td>German-Style Dunkelweizen</td>
      <td>0.002856</td>
      <td>17.50</td>
      <td>#8D4C32</td>
    </tr>
    <tr>
      <th>18</th>
      <td>German-Style Dunkel</td>
      <td>0.033789</td>
      <td>17.50</td>
      <td>#8D4C32</td>
    </tr>
    <tr>
      <th>19</th>
      <td>English-Style Brown Ale</td>
      <td>0.018996</td>
      <td>18.50</td>
      <td>#8D4C32</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Belgian-Style Flanders</td>
      <td>0.002060</td>
      <td>18.50</td>
      <td>#8D4C32</td>
    </tr>
    <tr>
      <th>21</th>
      <td>American Brown Ale</td>
      <td>0.018427</td>
      <td>20.50</td>
      <td>#5D341A</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Belgian-Style Golden Strong Ale</td>
      <td>0.009655</td>
      <td>22.00</td>
      <td>#5D341A</td>
    </tr>
    <tr>
      <th>23</th>
      <td>German-Style Bock</td>
      <td>0.016411</td>
      <td>25.00</td>
      <td>#261716</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Belgian-Style Dubbel</td>
      <td>0.059657</td>
      <td>26.00</td>
      <td>#261716</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Coffee Beer</td>
      <td>0.005266</td>
      <td>27.00</td>
      <td>#261716</td>
    </tr>
    <tr>
      <th>26</th>
      <td>English-Style Brown Porter</td>
      <td>0.033325</td>
      <td>27.50</td>
      <td>#261716</td>
    </tr>
    <tr>
      <th>27</th>
      <td>German-Style Schwarzbier</td>
      <td>0.004315</td>
      <td>27.50</td>
      <td>#261716</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Chocolate Beer</td>
      <td>0.005132</td>
      <td>32.50</td>
      <td>#0F0B0A</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Irish-Style Dry Stout</td>
      <td>0.007958</td>
      <td>37.50</td>
      <td>#080707</td>
    </tr>
    <tr>
      <th>30</th>
      <td>American Imperial Porter</td>
      <td>0.003514</td>
      <td>39.50</td>
      <td>#080707</td>
    </tr>
    <tr>
      <th>31</th>
      <td>American Stout</td>
      <td>0.002060</td>
      <td>39.50</td>
      <td>#080707</td>
    </tr>
  </tbody>
</table>
</div>




```python
ns = BSD_grandpappies.PageRank * 100000


plt.figure(figsize=(12,12))
nx.draw_spring(G_bsd2, 
                 nodelist=BSD_grandpappies.node.tolist(),
                 node_color = BSD_grandpappies.hex.tolist(),
                 node_size=ns.tolist(),
                 font_color = 'g',
                 with_labels=True)


```


<img src = "/code/beer_prplxd_V/output_61_0.png">



```python

```


```python

```
