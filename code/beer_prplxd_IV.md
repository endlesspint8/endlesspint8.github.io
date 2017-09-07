---
layout: page
title: endlesspint
subtitle: Data Guide for the Beer Perplexed, Part IV - Graphs and Paths
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
    dtype: object
    




<div>
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



## the _bright_ idea

- identify duplicate/parallel/two way edges
- remove one "copy" at random
- run `nx.dag...`
- iterate k times
    - track, count and hist
    
source: https://networkx.github.io/documentation/development/reference/classes.digraph.html#information-about-graph-structure
    
`DiGraph.nodes_with_selfloops()`	Return a list of nodes with self loops. <br>
`DiGraph.selfloop_edges([data])`	Return a list of selfloop edges. <br>
`DiGraph.number_of_selfloops()` 	Return the number of selfloop edges.


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
nx.draw_circular(G_toy, 
                 node_color=COLORS[0], 
                 node_size=2000, 
                 with_labels=True)
plt.axis('equal')
```




    (-1.5, 1.5, -1.5, 1.5)




<img src = "/code/beer_prplxd_IV/output_15_1.png">


## toy set longest with cycle (above)


```python
# from collections import Counter

# edge_count = Counter()

# for e in G_toy.edges_iter():
#     a,b = sorted(e)
#     edge_count[('_').join([a,b])] += 1
    
# edge_count
```

## parallel edge identification


```python
from collections import Counter

def pll_recreate(edge):
    a,b = edge.split('_')
    return (a,b), (b,a)

def pll_edges(G):
    
    edge_count = Counter()
    
    for e in G.edges_iter():
        a,b = sorted(e)
        edge_count[('_').join([a,b])] += 1
        
    edge_dupes = [k for k in edge_count if edge_count[k] > 1]
    return [pll_recreate(e) for e in edge_dupes]

print pll_edges(G_toy)
```

    [(('Dick', 'Fred'), ('Fred', 'Dick')), (('Bob', 'Edgar'), ('Edgar', 'Bob')), (('Alice', 'Bob'), ('Bob', 'Alice'))]
    


```python
import time
```


```python
# t1 = time.time()
# for i in range(10000):
#     H = G_toy.copy()
#     H.remove_edges_from([e[np.random.random() < .5] for e in x])
    
# time.time() - t1
```


```python
# 10x faster to remove/add edges than to copy graph
t1 = time.time()

long_paths = Counter()
x = pll_edges(G_toy)

for i in range(10000):
    pll_hold = [e[np.random.random() < .5] for e in x]
    
    G_toy.remove_edges_from(pll_hold)
    long_paths[nx.dag_longest_path_length(G_toy)] += 1
    G_toy.add_edges_from(pll_hold)
    
print long_paths
time.time() - t1
```

    Counter({4: 4968, 3: 3753, 5: 1279})
    




    0.3600001335144043




```python
plt.bar(long_paths.keys(), long_paths.values(), 0.25, color='g', align='center')
```




    <Container object of 3 artists>




<img src = "/code/beer_prplxd_IV/output_23_1.png">



```python
def lng_path(G, sim=1000):
    
    long_paths = Counter()
    parallel_e = pll_edges(G)
    
    for i in range(sim):
        pll_hold = [e[np.random.random() < .5] for e in parallel_e]

        G.remove_edges_from(pll_hold)
        long_paths[nx.dag_longest_path_length(G)] += 1
        G.add_edges_from(pll_hold)
        
    return long_paths

print lng_path(G_toy, 10000)
```

    Counter({4: 4979, 3: 3798, 5: 1223})
    

## test (cross your fingers!)

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




```python
print pll_edges(G)
```

    [(('Belgian-Style Dubbel', 'German-Style Dunkel'), ('German-Style Dunkel', 'Belgian-Style Dubbel')), (('Chocolate Beer', 'Coffee Beer'), ('Coffee Beer', 'Chocolate Beer')), (('American Black Ale', 'American India Pale Ale/IPA'), ('American India Pale Ale/IPA', 'American Black Ale')), (('Belgian-Style Lambic/Gueuze', 'Fruit and Field Beer'), ('Fruit and Field Beer', 'Belgian-Style Lambic/Gueuze')), (('German-Style Doppelbock', 'Scotch Ale/Wee Heavy'), ('Scotch Ale/Wee Heavy', 'German-Style Doppelbock')), (('Herb and Spice Beer', 'Honey Beer'), ('Honey Beer', 'Herb and Spice Beer')), (('Belgian-Style Wit', 'German-Style Hefeweizen'), ('German-Style Hefeweizen', 'Belgian-Style Wit')), (('English-Style Old Ale', 'German-Style Doppelbock'), ('German-Style Doppelbock', 'English-Style Old Ale')), (('German-Style Schwarzbier', 'Irish-Style Dry Stout'), ('Irish-Style Dry Stout', 'German-Style Schwarzbier')), (('American Amber Lager', 'English-Style Mild'), ('English-Style Mild', 'American Amber Lager')), (('Belgian-Style Dubbel', 'English-Style Brown Porter'), ('English-Style Brown Porter', 'Belgian-Style Dubbel')), (('English-Style Brown Porter', 'German-Style Dunkel'), ('German-Style Dunkel', 'English-Style Brown Porter')), (('American Black Ale', 'Robust Porter'), ('Robust Porter', 'American Black Ale')), (('American Amber Ale', 'English-Style Pale Ale/ESB'), ('English-Style Pale Ale/ESB', 'American Amber Ale')), (('American Amber Lager', 'German-Style Marzen/Oktoberfest'), ('German-Style Marzen/Oktoberfest', 'American Amber Lager')), (('American Imperial Porter', 'Chocolate Beer'), ('Chocolate Beer', 'American Imperial Porter')), (('English-Style Bitter', 'Session Beer'), ('Session Beer', 'English-Style Bitter')), (('American Sour', 'Barrel-Aged Beer'), ('Barrel-Aged Beer', 'American Sour'))]
    


```python
edge_hold = [e[np.random.random() < .5] for e in pll_edges(G)]
edge_hold
```




    [('Belgian-Style Dubbel', 'German-Style Dunkel'),
     ('Chocolate Beer', 'Coffee Beer'),
     ('American Black Ale', 'American India Pale Ale/IPA'),
     ('Fruit and Field Beer', 'Belgian-Style Lambic/Gueuze'),
     ('Scotch Ale/Wee Heavy', 'German-Style Doppelbock'),
     ('Honey Beer', 'Herb and Spice Beer'),
     ('German-Style Hefeweizen', 'Belgian-Style Wit'),
     ('German-Style Doppelbock', 'English-Style Old Ale'),
     ('Irish-Style Dry Stout', 'German-Style Schwarzbier'),
     ('American Amber Lager', 'English-Style Mild'),
     ('Belgian-Style Dubbel', 'English-Style Brown Porter'),
     ('German-Style Dunkel', 'English-Style Brown Porter'),
     ('Robust Porter', 'American Black Ale'),
     ('American Amber Ale', 'English-Style Pale Ale/ESB'),
     ('German-Style Marzen/Oktoberfest', 'American Amber Lager'),
     ('Chocolate Beer', 'American Imperial Porter'),
     ('English-Style Bitter', 'Session Beer'),
     ('American Sour', 'Barrel-Aged Beer')]




```python
len(edge_hold)
```




    18




```python
print len(G.edges())
G.remove_edges_from(edge_hold)
print len(G.edges())
G.add_edges_from(edge_hold)
print len(G.edges())
```

    186
    168
    186
    


```python
nx.dag_longest_path_length(G)
```


    ---------------------------------------------------------------------------

    NetworkXUnfeasible                        Traceback (most recent call last)

    <ipython-input-29-f12868cc9541> in <module>()
    ----> 1 nx.dag_longest_path_length(G)
    

    <decorator-gen-224> in dag_longest_path_length(G)
    

    C:\Users\rstancut\AppData\Local\Continuum\Anaconda2\lib\site-packages\networkx\utils\decorators.pyc in _not_implemented_for(f, *args, **kwargs)
         66                                             ' '.join(graph_types))
         67         else:
    ---> 68             return f(*args,**kwargs)
         69     return _not_implemented_for
         70 
    

    C:\Users\rstancut\AppData\Local\Continuum\Anaconda2\lib\site-packages\networkx\algorithms\dag.pyc in dag_longest_path_length(G)
        454     dag_longest_path
        455     """
    --> 456     path_length = len(nx.dag_longest_path(G)) - 1
        457     return path_length
    

    <decorator-gen-222> in dag_longest_path(G)
    

    C:\Users\rstancut\AppData\Local\Continuum\Anaconda2\lib\site-packages\networkx\utils\decorators.pyc in _not_implemented_for(f, *args, **kwargs)
         66                                             ' '.join(graph_types))
         67         else:
    ---> 68             return f(*args,**kwargs)
         69     return _not_implemented_for
         70 
    

    C:\Users\rstancut\AppData\Local\Continuum\Anaconda2\lib\site-packages\networkx\algorithms\dag.pyc in dag_longest_path(G)
        416     """
        417     dist = {}  # stores [node, distance] pair
    --> 418     for node in nx.topological_sort(G):
        419         # pairs of dist,node for all incoming edges
        420         pairs = [(dist[v][0] + 1, v) for v in G.pred[node]]
    

    C:\Users\rstancut\AppData\Local\Continuum\Anaconda2\lib\site-packages\networkx\algorithms\dag.pyc in topological_sort(G, nbunch, reverse)
        155                 if n not in explored:
        156                     if n in seen:  # CYCLE !!
    --> 157                         raise nx.NetworkXUnfeasible("Graph contains a cycle.")
        158                     new_nodes.append(n)
        159             if new_nodes:   # Add new_nodes to fringe
    

    NetworkXUnfeasible: Graph contains a cycle.


## loop identification


```python
G_toy2 = nx.DiGraph()
G_toy2.add_nodes_from(['Alice', 'Bob', 'Chuck', 'Dick'])
# G_toy2.nodes()

G_toy2.add_edges_from([('Alice', 'Bob'), ('Bob', 'Chuck'), ('Chuck', 'Dick'), ('Dick', 'Alice')])
G_toy2.edges()
```




    [('Bob', 'Chuck'), ('Dick', 'Alice'), ('Alice', 'Bob'), ('Chuck', 'Dick')]




```python
nx.draw_circular(G_toy2, 
                 node_color=COLORS[0], 
                 node_size=2000, 
                 with_labels=True)
plt.axis('equal')
```




    (-1.5, 1.5, -1.5, 1.5)




<img src = "/code/beer_prplxd_IV/output_37_1.png">


## next _bright_ idea

- _after_ removing parallel edges (at random)
- shuffle nodes, find _loop_ edges, and remove
- run `nx.dag...`
---
- add back all removed edges, parallel & loop
- iterate process


```python
# Think Complexity2, ch2

def reachable_nodes(G, start):
    seen = set()
    stack = [start]
    while stack:
        node = stack.pop()
        if node not in seen:
            seen.add(node)
            stack.extend(G.neighbors(node))
    return seen

reachable_nodes(G_toy2, 'Alice')
```




    {'Alice', 'Bob', 'Chuck', 'Dick'}




```python
def loop_edge(G, start):
    seen = set()
    stack = [start]
    loops = []
    while stack:
        node = stack.pop()
        if node not in seen:
            seen.add(node)
            stack.extend(G.neighbors(node))

            for n in G[node]:
                if n in seen:
                    loops.append((node, n))
            

    return loops

loop_edge(G_toy2, 'Dick')
```




    [('Chuck', 'Dick')]




```python
for n in G_toy2.nodes():
    print n, loop_edge(G_toy2,n)
```

    Bob [('Alice', 'Bob')]
    Dick [('Chuck', 'Dick')]
    Alice [('Dick', 'Alice')]
    Chuck [('Bob', 'Chuck')]
    


```python
# G_toy2 = nx.DiGraph()
# G_toy2.add_nodes_from(['Alice', 'Bob', 'Chuck', 'Dick'])
# # G_toy2.nodes()

# G_toy2.add_edges_from([('Alice', 'Bob'), ('Bob', 'Chuck'), ('Chuck', 'Dick'), ('Dick', 'Alice')])
# G_toy2.edges()

long_paths = Counter()
loop_hold = []

for n in np.random.permutation(G_toy2.nodes()):
    print n
    print loop_edge(G_toy2,n)
    loop_hold.extend(loop_edge(G_toy2,n))
    
    G_toy2.remove_edges_from(loop_hold)
    long_paths[nx.dag_longest_path_length(G_toy2)] += 1
#     G_toy2.add_edges_from(loop_hold)

print loop_hold
print long_paths
print len(G_toy2.edges())
G_toy2.add_edges_from(loop_hold)
print len(G_toy2.edges())
```

    Chuck
    [('Bob', 'Chuck')]
    Bob
    []
    Dick
    []
    Alice
    []
    [('Bob', 'Chuck')]
    Counter({3: 4})
    3
    4
    


```python
def lng_path_cnt(G, sim=1000):
    
    long_paths = Counter()
    parallel_e = pll_edges(G)
    print len(G), len(G.edges())
    
    for i in range(sim):
        pll_hold = [e[np.random.random() < .5] for e in parallel_e]
        G.remove_edges_from(pll_hold)
        
        loop_hold = []
        
        for n in np.random.permutation(G.nodes()):
            loop_hold.extend(loop_edge(G,n))
            G.remove_edges_from(loop_hold)
        
        long_paths[nx.dag_longest_path_length(G)] += 1
        G.add_edges_from(pll_hold)
        G.add_edges_from(loop_hold)
        
    print len(G), len(G.edges())
    return long_paths

long_paths2 = lng_path_cnt(G)
print long_paths2
print np.max([k for k in long_paths2])
```

    77 186
    77 186
    Counter({9: 165, 10: 150, 12: 131, 8: 124, 11: 115, 13: 86, 7: 44, 15: 43, 14: 38, 16: 28, 19: 20, 18: 19, 17: 15, 20: 11, 21: 5, 6: 4, 22: 2})
    22
    


```python
# now run it 10k times

long_paths2 = lng_path_cnt(G, 20000)
plt.bar(long_paths2.keys(), long_paths2.values(), 0.25, color='g', align='center')
lp = np.max([k for k in long_paths2])
plt.vlines(lp,0, 2000, color='r', linestyles=':')
plt.text(lp-1, 1000, "long path count: %d" % lp, rotation=90, verticalalignment='center')
```

    77 186
    77 186
    




    <matplotlib.text.Text at 0xbbda2b0>




<img src = "/code/beer_prplxd_IV/output_44_2.png">



```python
def lng_path_list(G, sim=1000):
    
    long_paths = []
    path_count = 0
    
    parallel_e = pll_edges(G)
    print len(G), len(G.edges())
    
    for i in range(sim):
        pll_hold = [e[np.random.random() < .5] for e in parallel_e]
        G.remove_edges_from(pll_hold)
        
        loop_hold = []
        
        for n in np.random.permutation(G.nodes()):
            loop_hold.extend(loop_edge(G,n))
            G.remove_edges_from(loop_hold)
        
        temp_path = nx.dag_longest_path(G)
        if len((nx.dag_longest_path(G))) >= path_count:
            long_paths.append(temp_path)
            path_count = len(temp_path)
#         long_paths[nx.dag_longest_path_length(G)] += 1

        G.add_edges_from(pll_hold)
        G.add_edges_from(loop_hold)
        
    print len(G), len(G.edges())
    return long_paths

lng_path_list(G,50)[-1]
```

    77 186
    77 186
    




    ['European-Style Export',
     'Belgian-Style Saison',
     'American Pale Ale',
     'Belgian-Style Pale Ale',
     'American Amber Ale',
     'American Amber Lager',
     'Vienna-Style Lager',
     'English-Style Bitter',
     'Scottish-Style Ale',
     'Belgian-Style Dubbel',
     'English-Style Brown Porter',
     'American Brown Ale',
     'Fruit and Field Beer',
     'American Sour',
     'Belgian-Style Wit',
     'Bohemian-Style Pilsener',
     'American Wheat',
     'Belgian-Style Tripel',
     'German-Style Maibock',
     'Belgian-Style Golden Strong Ale']




```python
lng_path_names = lng_path_list(G,10000)[-1]
print len(lng_path_names)
lng_path_names
```

    77 186
    77 186
    26
    




    ['European-Style Export',
     'Belgian-Style Saison',
     'Session Beer',
     'English-Style Bitter',
     'Belgian-Style Pale Ale',
     'American Amber Ale',
     'American Amber Lager',
     'Vienna-Style Lager',
     'Belgian-Style Dubbel',
     'English-Style Brown Porter',
     'American Brown Ale',
     'Scottish-Style Ale',
     'Barrel-Aged Beer',
     'American Brett',
     'German-Style Pilsener',
     'Belgian-Style Tripel',
     'German-Style Maibock',
     'Belgian-Style Golden Strong Ale',
     'American Wheat',
     'Fruit and Field Beer',
     'American Sour',
     'Belgian-Style Wit',
     'Bohemian-Style Pilsener',
     'German-Style Kolsch',
     'English-Style Pale Ale/ESB',
     'German-Style Bock']



---

## add surrounding beers for context


```python
G2 = nx.DiGraph()

for style in lng_path_names:
    G2.add_node(style)
    G2.add_nodes_from(G.neighbors(style))
    G2.add_edges_from([(style, n) for n in G.neighbors_iter(style)])
    
print len(G2)
G2.nodes()
```

    37
    




    ['German-Style Bock',
     'Belgian-Style Tripel',
     'American Brett',
     'Scottish-Style Ale',
     'German-Style Marzen/Oktoberfest',
     'English-Style India Pale Ale/IPA',
     'German-Style Dunkel',
     'Bohemian-Style Pilsener',
     'Belgian-Style Lambic/Gueuze',
     'American Amber Lager',
     'Irish-Style Dry Stout',
     'English-Style Brown Porter',
     'German-Style Pilsener',
     'English-Style Bitter',
     'Fruit and Field Beer',
     'Imperial India Pale Ale',
     'Session Beer',
     'Belgian-Style Pale Ale',
     'Belgian-Style Saison',
     'German-Style Hefeweizen',
     'American Wheat',
     'Belgian-Style Dubbel',
     'English-Style Brown Ale',
     'American Amber Ale',
     'American Brown Ale',
     'Vienna-Style Lager',
     'American Pale Ale',
     'European-Style Export',
     'Belgian-Style Golden Strong Ale',
     'Barrel-Aged Beer',
     'German-Style Maibock',
     'Belgian-Style Wit',
     'English-Style Pale Ale/ESB',
     'American Sour',
     'English-Style Mild',
     'Blonde Ale',
     'German-Style Kolsch']




```python
nx.draw_spring(G2, 
                 node_color=COLORS[0], 
                 node_size=200, 
                 with_labels=True)
# plt.axis('equal')
```


<img src = "/code/beer_prplxd_IV/output_49_0.png">



```python
for n in G.neighbors_iter('Belgian-Style Wit'):
    print ('Belgian-Style Wit', n)
```

    ('Belgian-Style Wit', 'Bohemian-Style Pilsener')
    ('Belgian-Style Wit', 'Fruit and Field Beer')
    ('Belgian-Style Wit', 'German-Style Hefeweizen')
    


```python
[('Belgian-Style Wit', n) for n in G.neighbors_iter('Belgian-Style Wit')]
```




    [('Belgian-Style Wit', 'Bohemian-Style Pilsener'),
     ('Belgian-Style Wit', 'Fruit and Field Beer'),
     ('Belgian-Style Wit', 'German-Style Hefeweizen')]



## PageRank


```python
nx.pagerank(G)
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

```
