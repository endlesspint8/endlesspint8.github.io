---
layout: page
title: endlesspint
subtitle: Dutch Stop Words
---

## Table of Stop Words

Three sources hyperlinked in column names.<sup id="a1">[1](#f1)</sup>

Translations by <a href="https://www.google.com/search?q=google+translate&oq=goog&aqs=chrome.0.69i59l3j69i60l3.826j0j4&sourceid=chrome&ie=UTF-8" target="_blank">Google</a>, except where noted.

|idx|words|<a href="http://snowball.tartarus.org/algorithms/dutch/stop.txt" target="_blank">01a_stop</a><sup id="a2">[2](#f2)</sup>|<a href="http://www.ranks.nl/stopwords/dutch" target="_blank">02_ranks_nl</a>|<a href="http://www.damienvanholten.com/blog/dutch-stop-words" target="_blank">03_dutch-stop-words</a>|translation|BD count|
|---|---|---|---|---|---|---|
|0|aan|1|1|1|to|213|
|1|af|0|1|1|down|19|
|2|al|1|1|1|already|82|
|3|alles|1|0|1|all|9|
|4|als|1|1|1|as|97|
|5|altijd|1|0|1|always|10|
|6|andere|1|0|1|other|37|
|7|ben|1|0|1|am|14|
|8|bij|1|1|1|at|175|
|9|daar|1|0|1|over there|43|
|10|dan|1|1|1|than|64|
|11|dat|1|1|1|it|403|
|12|de|1|0|1|the|2481|
|13|der|1|0|1|of|29|
|14|deze|1|0|1|this|66|
|15|die|1|1|1|that|245|
|16|dit|1|1|1|this|68|
|17|doch|1|0|1|but||
|18|doen|1|0|1|do|25|
|19|door|1|0|1|by|125|
|20|dus|1|0|1|so|20|
|21|een|1|1|1|a|923|
|22|eens|1|0|1|once|14|
|23|en|1|1|1|and|615|
|24|er|1|1|1|there|239|
|25|ge|1|0|1|'thou'<sup id="a3">[3](#f3)</sup>||
|26|geen|1|0|1|no|69|
|27|geweest|1|0|1|been|7|
|28|haar|1|0|1|its|35|
|29|had|1|1|1|had|43|
|30|heb|1|1|1|have|10|
|31|hebben|1|0|1|have|107|
|32|heeft|1|0|1|has|149|
|33|hem|1|1|1|him|31|
|34|het|1|1|1|the|1063|
|35|hier|1|0|1|here|15|
|36|hij|1|1|1|he|141|
|37|hoe|1|1|1|how|21|
|38|hun|1|1|1|their|40|
|39|iemand|1|0|1|someone|2|
|40|iets|1|0|1|something|13|
|41|ik|1|1|1|I|66|
|42|in|1|1|1|in|861|
|43|is|1|1|1|is|435|
|44|ja|1|0|1|yes|3|
|45|je|1|1|1|you|57|
|46|kan|1|1|1|can|59|
|47|kon|1|0|1|could|20|
|48|kunnen|1|0|1|can|47|
|49|maar|1|0|1|but|150|
|50|me|1|1|1|me|10|
|51|meer|1|0|1|(1) more|101|
|52|men|1|1|1|one||
|53|met|1|1|1|with|316|
|54|mij|1|1|1|me|8|
|55|mijn|1|0|1|my|16|
|56|moet|1|0|1|must|42|
|57|na|1|0|1|after|62|
|58|naar|1|0|1|to|153|
|59|niet|1|0|1|not|226|
|60|niets|1|0|1|nothing|6|
|61|nog|1|1|1|yet|156|
|62|nu|1|1|1|now|43|
|63|of|1|1|1|whether|61|
|64|om|1|0|1|to|218|
|65|omdat|1|0|1|because|27|
|66|onder|1|0|0|below|67|
|67|ons|1|1|1|us / our|16|
|68|ook|1|1|1|also|149|
|69|op|1|0|1|on|544|
|70|over|1|0|1|about|140|
|71|reeds|1|0|1|already||
|72|te|1|1|1|too|324|
|73|tegen|1|0|1|against|46|
|74|toch|1|0|1|nevertheless|17|
|75|toen|1|0|1|when|38|
|76|tot|1|1|1|until|85|
|77|u|1|0|1|you|9|
|78|uit|1|1|1|from|158|
|79|uw|1|0|1|your|2|
|80|van|1|1|1|from|1078|
|81|veel|1|0|1|many|42|
|82|voor|1|0|1|in front of|278|
|83|want|1|0|1|because|13|
|84|waren|1|0|1|goods|53|
|85|was|1|1|1|was|133|
|86|wat|1|1|1|what|46|
|87|we|0|1|1|we|39|
|88|wel|0|1|1|well|59|
|89|werd|1|0|1|became|99|
|90|wezen|1|0|1|being||
|91|wie|1|0|1|who|13|
|92|wij|0|1|1|we|19|
|93|wil|1|0|1|want|33|
|94|worden|1|0|1|be|94|
|95|wordt|1|0|0|is|82|
|96|zal|1|1|1|shall|28|
|97|ze|1|1|1|she|90|
|98|zei|0|1|1|said|13|
|99|zelf|1|0|1|self|12|
|100|zich|1|0|1|himself|73|
|101|zij|1|1|1|they|40|
|102|zijn|1|0|1|his|304|
|103|zo|1|1|1|so|45|
|104|zonder|1|0|1|without|14|
|105|zou|1|1|1|would|67|

<br>

---

## Code

```python
import pandas as pd
import os
```

```python
stop_files = os.listdir('stopwords/')
stop_files.pop(1)
stop_files
```


`Out:`

['01a_stop.txt', '02_ranks_nl.txt', '03_dutch-stop-words.txt']




```python
stop_list = []
stopwords = []

for stop in stop_files:
    with open('stopwords/'+stop, 'r') as f:
        temp_list = []
        for line in f:
            temp_list.append(line.strip())
            stopwords.append(line.strip())
        temp_dict = {'file': stop, 'words': temp_list}
        stop_list.append(temp_dict)
        
print [len(d['words']) for d in stop_list]
print len(stopwords)
print len(set(stopwords))
```
`Out:`

[101, 48, 104]

253

106
    


```python
stopwords_idx = pd.DataFrame(list(set(stopwords)))
print stopwords_idx.shape
stopwords_idx.columns = ['words']
stopwords_idx.head()
```

`Out:`

(106, 1)
    

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>words</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>andere</td>
    </tr>
    <tr>
      <th>1</th>
      <td>deze</td>
    </tr>
    <tr>
      <th>2</th>
      <td>over</td>
    </tr>
    <tr>
      <th>3</th>
      <td>zei</td>
    </tr>
    <tr>
      <th>4</th>
      <td>zal</td>
    </tr>
  </tbody>
</table>
</div>



```python
stopwords_full = stopwords_idx
print stopwords_full.shape

for i in range(len(stop_list)):
    df = pd.DataFrame(stop_list[i]['words'], columns=['words'])
    df[stop_list[i]['file'].replace('.txt', '')] = 1
    stopwords_temp = pd.merge(stopwords_idx, df, on='words')
    stopwords_full = pd.merge(stopwords_full, stopwords_temp, on='words', how='outer')

print stopwords_full.shape
stopwords_full = stopwords_full.fillna(0)
stopwords_full = stopwords_full.sort(columns='words', axis=0)
stopwords_full = stopwords_full.reset_index(drop=True)
stopwords_full.head()
```

`Out:`

(106, 1)

(106, 4)
    
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>words</th>
      <th>01a_stop</th>
      <th>02_ranks_nl</th>
      <th>03_dutch-stop-words</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>aan</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>af</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>al</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>alles</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>als</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



```python
stopwords_full.to_csv('stopwords/stopwords_table.csv', encoding='utf8')
```


<br>

---

**Notes**

<b id="f1">1</b> And listed below with identified contacts:

1. http://snowball.tartarus.org/algorithms/dutch/stop.txt; http://www.patrickmileswriter.co.uk/ \ mail@patrickmiles.co.uk
2. http://www.ranks.nl/stopwords/dutch; damian@ranks.nl
3. http://www.damienvanholten.com/blog/dutch-stop-words/; http://twitter.com/damienvanholten [↩](#a1) <br>

<b id="f2">2</b> Modified to remove provided translations. [↩](#a2) <br>
<b id="f3">3</b> According to http://snowball.tartarus.org/algorithms/dutch/stop.txt: <i>"'thou', still used in Belgium and south Netherlands"</i> [↩](#a3) <br>
