---
layout: page
title: endlesspint
subtitle: Dutch Words
---

## Some Code, Details, & Tables in Identifying Relevant Dutch Words
<br>
<br>

### Using Vagrant for PySpark Setup

source: https://github.com/spark-mooc/mooc-setup/

source: https://spark.apache.org/docs/1.2.0/programming-guide.html

### Test synced local folder

source: https://www.vagrantup.com/docs/synced-folders/basic_usage.html

    os.listdir('/localMACHINE/STUDY/')

### Function - Remove Punctuation


```python
import re
def removePunctuation(text):
    """Removes punctuation, changes to lower case, and strips leading and trailing spaces.

    Note:
        Only spaces, letters, and numbers should be retained.  Other characters should should be
        eliminated (e.g. it's becomes its).  Leading and trailing spaces should be removed after
        punctuation is removed.

    Args:
        text (str): A string.

    Returns:
        str: The cleaned up string.
    """
    return re.sub(r'[^\w ]', '', text).strip().lower()
    
print removePunctuation('Hi, you!')
print removePunctuation(' No under_score!')
print removePunctuation(' *      Remove punctuation then spaces  * ')
```

`Out:`

    hi you
    no under_score
    remove punctuation then spaces


### Import Stop Words

```python
import csv

stopwords = []

with open(stopwordsDir + 'stopwords_table.csv', 'r') as f:
    reader = csv.reader(f, delimiter=',')
    reader.next()
    for row in reader:
        stopwords.append(row[1])
        
print len(stopwords)
print stopwords[:5]
print stopwords[-5:]
```

`Out:`

    106
    ['aan', 'af', 'al', 'alles', 'als']
    ['zij', 'zijn', 'zo', 'zonder', 'zou']


### Function - Remove Stop Words

```python
def stopwordsRemove(text):
    return ' '.join([term for term in text.split() if term not in stopwords])
```

### one day test - remove

```python
onedayRDD_witout = (sc.textFile(oneday)
                .map(removePunctuation)
                .map(stopwordsRemove)
            )

print '\n'.join(onedayRDD_witout
                .zipWithIndex()  # to (line, lineNum)
                .map(lambda (l, num): '{0}: {1}'.format(num, l))  # to 'lineNum: line'
                .take(5))
```

`Out:`

    0: update 1015 uur den bosch rechtbank den bosch maandag faillissement uitgesproken modeketen houtbrox vier aanverwante vennootschappen
    1: 
    2: bewindvoerders dienden aanvraag maandagmorgen rechtbank winkels maandag opengegaan
    3: bewindvoerder floris dix denkt vanuit faillissement betere mogelijkheid doorstart bereiken afgelopen dagen tien genteresseerden modeketen bewindvoerders gemeld dix verwacht faillissement zelfs kandidaat kopers aandienenvoor 528 medewerkers dreigt ontslag eerste tijd salarissen hetuwv betaald afgelopen dagen bewindvoerders meeste leveranciers overeenstemming bereikt kleding vanaf datum eerder uitgesproken surseance verkochtbewindvoerder dix denkt enkele weken duurt voordat overeenkomst gesloten mogelijke doorstart tijd winkels zeker open houden geeft beste garantie doorstart
    4: update 1716uur moergestel a58 tussen oirschot moergestel maandagmiddag ongeluk tussen 4 autos gebeurd verkeer richting tilburg kwam daardoor file terecht


### Function - Keep Stop Words

```python
def stopwordsKeep(text):
    return ' '.join([term for term in text.split() if term in stopwords])
```

### one day test - keep

```python
onedayRDD_wit = (sc.textFile(oneday)
                .map(removePunctuation)
                .map(stopwordsKeep)
            )

print '\n'.join(onedayRDD_wit
                .zipWithIndex()  # to (line, lineNum)
                .map(lambda (l, num): '{0}: {1}'.format(num, l))  # to 'lineNum: line'
                .take(5))
```                

`Out:`

    0: de in heeft het van en
    1: 
    2: de de in bij de de zijn wel
    3: dat een een is een te de hebben zich al in de zich bij de dat er na een nog meer zich de nu ook de worden de nog wel door in de hebben de al wel met de over de die de van de worden dat het nog wel een kan worden over een tot die wil hij de want dat de op een
    4: op de en is een het in een


### Multiple Subfolders

source: http://stackoverflow.com/questions/24029873/how-to-read-multiple-text-files-into-a-single-rdd
    
```python
subfolders = [x for x in os.listdir(baseDir2) if '2016' in x and 'csv' not in x]
sf_string = ''
for folder in subfolders:
    sf_string = sf_string + baseDir2 + '/' + folder + ','
    
sf_string = sf_string[:-1]
sf_string[:250]
```
    
`Out:`    
    
    '/localMACHINE/STUDY/ep8/20160519_goingDutch/articles/20160509_0918,/localMACHINE/STUDY/ep8/20160519_goingDutch/articles/20160509_1504,/localMACHINE/STUDY/ep8/20160519_goingDutch/articles/20160510_0934,/localMACHINE/STUDY/ep8/20160519_goingDutch/artic'

## ALL without stop words
    
```python
allday_sw0_RDD = (sc.textFile(sf_string)
                .map(removePunctuation)
                .map(stopwordsRemove)
            )
            
print allday_sw0_RDD.collect()[-1]
print allday_sw0_RDD.count()
allday_sw0_WordsRDD = allday_sw0_RDD.flatMap(lambda x: x.split(' '))
allday_sw0_WordCount = allday_sw0_WordsRDD.count()
print allday_sw0_WordsRDD.top(5)
print allday_sw0_WordCount
```

`Out:`

    politie doet onderzoek alle drie incidenten hoopt hulp mensen stad tijdens incidenten actief zoek slachtoffer11 aanh 1 persoon vandoor ging parade sloeg sfeer totaal resultaat 11 aanhoudingen inzet tshoostbrabant22 verdachten zware mish opruiing voldoen vordering aanzetten wanordelijkheden drukke nacht geworden
    928
    [u'zwolle', u'zwolle', u'zwolle', u'zwolle', u'zwijgzaam']
    19354

```python
allWords_sw0_RDD = allday_sw0_WordsRDD.filter(lambda x: x != '')
allWords_sw0_Count = allWords_sw0_RDD.count()
print allWords_sw0_Count## ALL without stop words


top15BDall_sw0_WordsAndCounts = wordCount(allWords_sw0_RDD).takeOrdered(15, key=lambda x: -x[1])
print '\n'.join(map(lambda (w, c): '{0}: {1}'.format(w, c), top15BDall_sw0_WordsAndCounts))
```

`Out:`

    18953
    politie: 152
    bosch: 149
    den: 138
    tilburg: 107
    uur: 91
    volgens: 87
    jaar: 76
    mensen: 67
    gaat: 62
    man: 51
    onderzoek: 50
    twee: 47
    komen: 46
    rond: 45
    nederland: 45

```python
top100BD_nonSW = wordCount(allWords_sw0_RDD).takeOrdered(100, key=lambda x: -x[1])
top100BD_nonSW[:10]
```

`Out:`

    [(u'politie', 152),
    (u'bosch', 149),
    (u'den', 138),
    (u'tilburg', 107),
    (u'uur', 91),
    (u'volgens', 87),
    (u'jaar', 76),
    (u'mensen', 67),
    (u'gaat', 62),
    (u'man', 51)]


```python
termsDir = '/localMACHINE/STUDY/ep8/20160519_goingDutch/terms/'

with open(termsDir + 'top100_nonStopWords.txt', 'w') as f:
    for term in top100BD_nonSW:
        f.write(term[0] + ',' + str(term[1]) + '\n')
```


## ALL stop words
    
```python
allday_sw1_RDD = (sc.textFile(sf_string)
                .map(removePunctuation)
                .map(stopwordsKeep)
            )
            
print allday_sw1_RDD.collect()[-1]
print allday_sw1_RDD.count()
allday_sw1_WordsRDD = allday_sw1_RDD.flatMap(lambda x: x.split(' '))
allday_sw1_WordCount = allday_sw1_WordsRDD.count()
print allday_sw1_WordsRDD.top(5)
print allday_sw1_WordCount

allWords_sw1_RDD = allday_sw1_WordsRDD.filter(lambda x: x != '')
allWords_sw1_Count = allWords_sw1_RDD.count()
print allWords_sw1_Count

top15BDall_sw1_WordsAndCounts = wordCount(allWords_sw1_RDD).takeOrdered(15, key=lambda x: -x[1])
print '\n'.join(map(lambda (w, c): '{0}: {1}'.format(w, c), top15BDall_sw1_WordsAndCounts))
```

`Out:`

    de nog naar de en op van die in de waren de ook is zij op naar het na die er de om van niet tot toch nog een
    928
    [u'zou', u'zou', u'zou', u'zou', u'zou']
    15685
    15267
    de: 2481
    van: 1078
    het: 1063
    een: 923
    in: 861
    en: 615
    op: 544
    is: 435
    dat: 403
    te: 324
    met: 316
    zijn: 304
    voor: 278
    die: 245
    er: 239




## bigrams, baby!

source: http://www.mccarroll.net/blog/pyspark2/

```python
sentences = sc.textFile(sf_string) \
    .glom() \
    .map(lambda x: " ".join(x)) \
    .flatMap(lambda x: x.split("."))


bigrams = sentences.map(removePunctuation) \
    .map(lambda x:x.split()) \
    .flatMap(lambda x: [((x[i],x[i+1]),1) for i in range(0,len(x)-1)])


freq_bigrams = bigrams.reduceByKey(lambda x,y:x+y) \
    .map(lambda x:(x[1],x[0])) \
    .sortByKey(False)


freq_bigrams.take(15)
```

`Out:`

    [(274, (u'van', u'de')),
    (227, (u'in', u'de')),
    (145, (u'de', u'politie')),
    (141, (u'op', u'de')),
    (118, (u'den', u'bosch')),
    (115, (u'van', u'het')),
    (102, (u'in', u'het')),
    (86, (u'aan', u'de')),
    (77, (u'van', u'een')),
    (73, (u'voor', u'de')),
    (71, (u'over', u'de')),
    (62, (u'in', u'een')),
    (62, (u'met', u'een')),
    (60, (u'bij', u'de')),
    (58, (u'met', u'de'))]


```python
termsDir = '/localMACHINE/STUDY/ep8/20160519_goingDutch/terms/'

with open(termsDir + 'BD_bigrams.txt', 'w') as f:
    for bi in freq_bigrams.take(50):
        count = bi[0]
        big = ' '.join([bi[1][0], bi[1][1]])
        f.write(str(count) + ',' + big + '\n')
```

## all articles via sklearn
source: http://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html<br>
http://www.markhneedham.com/blog/2015/02/15/pythonscikit-learn-calculating-tfidf-on-how-i-met-your-mother-transcripts/


```python
articleDir = 'articles/'
os.listdir(articleDir)
subfolders = [x for x in os.listdir(articleDir) if 'csv' not in x]
print len(subfolders)
subfolders[:10]
```

`Out:`

    62
    

    ['20160418_1727',
     '20160419_0923',
     '20160419_1314',
     '20160419_1643',
     '20160420_0918',
     '20160420_1305',
     '20160420_1655',
     '20160421_0916',
     '20160421_1210',
     '20160422_0955']




```python
articles = defaultdict(list)
articleCnt = 1

for sub in subfolders[:3]:
    stories = os.listdir(articleDir + sub)
    for story in stories:
        with open(articleDir + sub + '/' + story, 'r') as f:
            for line in f:
                articles[articleCnt].append(removePunctuation(line.strip()))
            articleCnt += 1
            
print len(articles)
```

`Out:`

    9


```python
for article_id, text in articles.iteritems():
    articles[article_id] = "".join(text)
    
articles[1]
```

`Out:`



    'update 1015 uur  den bosch  de rechtbank in den bosch heeft maandag het faillissement uitgesproken van modeketen houtbrox en vier aanverwante vennootschappende bewindvoerders dienden de aanvraag maandagmorgen in bij de rechtbank de winkels zijn maandag wel opengegaanbewindvoerder floris dix denkt dat vanuit een faillissement een betere mogelijkheid is een doorstart te bereiken de afgelopen dagen hebben zich al tien genteresseerden in de modeketen zich bij de bewindvoerders gemeld dix verwacht dat er na een faillissement zelfs nog meer kandidaat kopers zich aandienenvoor de 528 medewerkers dreigt nu ook ontslag de eerste tijd worden de salarissen nog wel door hetuwv betaald in de afgelopen dagen hebben de bewindvoerders al wel met de meeste leveranciers overeenstemming bereikt over de kleding die vanaf de datum van de eerder uitgesproken surseance worden verkochtbewindvoerder dix denkt dat het nog wel enkele weken duurt voordat een overeenkomst gesloten kan worden over een mogelijke doorstart tot die tijd wil hij de winkels zeker open houden want dat geeft de beste garantie op een doorstart'




```python
corpus = []
for id, article in sorted(articles.iteritems(), key=lambda t: int(t[0])):
    corpus.append(article)
    
corpus[:2]
```

`Out:`



    ['update 1015 uur  den bosch  de rechtbank in den bosch heeft maandag het faillissement uitgesproken van modeketen houtbrox en vier aanverwante vennootschappende bewindvoerders dienden de aanvraag maandagmorgen in bij de rechtbank de winkels zijn maandag wel opengegaanbewindvoerder floris dix denkt dat vanuit een faillissement een betere mogelijkheid is een doorstart te bereiken de afgelopen dagen hebben zich al tien genteresseerden in de modeketen zich bij de bewindvoerders gemeld dix verwacht dat er na een faillissement zelfs nog meer kandidaat kopers zich aandienenvoor de 528 medewerkers dreigt nu ook ontslag de eerste tijd worden de salarissen nog wel door hetuwv betaald in de afgelopen dagen hebben de bewindvoerders al wel met de meeste leveranciers overeenstemming bereikt over de kleding die vanaf de datum van de eerder uitgesproken surseance worden verkochtbewindvoerder dix denkt dat het nog wel enkele weken duurt voordat een overeenkomst gesloten kan worden over een mogelijke doorstart tot die tijd wil hij de winkels zeker open houden want dat geeft de beste garantie op een doorstart',
     'update 1716uur moergestel  op de a58 tussen oirschot en moergestel is maandagmiddag een ongeluk tussen 4 autos gebeurd het verkeer richting tilburg kwam daardoor in een file terechteen tijd lang was alleen de vluchtstrook open rond 1645 uur werd de weg weer vrijgegeven de file was op dat moment13kilometer langer is een omleiding ingesteldhet is niet bekend of er gewonden zijn gevallen en hoe het ongeluk heeft kunnen gebeurenkijkersfilein de tegengestelde richting eindhoven ontstond een kijkersfile van 6 kilometer tussen tilburg centrumoost en oirschot dat leverde10 minuten vertraging opa58 eindhoventilburg file door ongeval verkeer richting tilburgbreda volg vanaf knooppunt batadorp den bosch a2a65botsing met 4 autos op a58 eindhoven tilburg tussen oirschot en moergestel 4 km file alleen de vluchtstrook is nog open']




```python
from sklearn.feature_extraction.text import TfidfVectorizer

tf = TfidfVectorizer(analyzer='word', ngram_range=(1,3), 
                     min_df = 0, stop_words = list(set(stopwords)), smooth_idf=False)

tfidf_matrix =  tf.fit_transform(corpus)
feature_names = tf.get_feature_names() 
len(feature_names)
```

`Out:`

    2031




```python
feature_names[90:100]
```

`Out:`



    [u'aanwezig',
     u'aanwezig tilburgse',
     u'aanwezig tilburgse wijk',
     u'absoluut',
     u'absoluut vrij',
     u'absoluut vrij surfen',
     u'achterhoek',
     u'achterhoek zutphen',
     u'achterhoek zutphen verwacht',
     u'achtjaar']




```python
dense = tfidf_matrix.todense()
len(dense[0].tolist()[0])
```

`Out:`

    2031

## reviewing one article


```python
article1 = dense[0].tolist()[0]
phrase_scores = [pair for pair in zip(range(0, len(article1)), article1) if pair[1] > 0]
 
len(phrase_scores)
```

`Out:`

    242


```python
sorted(phrase_scores, key=lambda t: t[1] * -1)[:5]
```

`Out:`

    [(245, 0.17863433615755836),
     (555, 0.17863433615755836),
     (108, 0.11908955743837224),
     (396, 0.11908955743837224),
     (473, 0.11908955743837224)]




```python
for scores in sorted(phrase_scores, key=lambda t: t[1] * -1)[:5]:
    print scores[0], feature_names[scores[0]]
```

`Out:`

    245 bewindvoerders
    555 faillissement
    108 afgelopen dagen
    396 dagen
    473 dix denkt
    


```python
sorted_phrase_scores = sorted(phrase_scores, key=lambda t: t[1] * -1)
for phrase, score in [(feature_names[word_id], score) for (word_id, score) in sorted_phrase_scores][:20]:
   print('{0: <20} {1}'.format(phrase, score))
```

`Out:`

    bewindvoerders       0.178634336158
    faillissement        0.178634336158
    afgelopen dagen      0.119089557438
    dagen                0.119089557438
    dix denkt            0.119089557438
    maandag              0.119089557438
    modeketen            0.119089557438
    rechtbank            0.119089557438
    uitgesproken         0.119089557438
    dix                  0.117253012408
    doorstart            0.117253012408
    tijd                 0.093271355127
    afgelopen            0.0781686749388
    bosch                0.0781686749388
    den                  0.0781686749388
    den bosch            0.0781686749388
    denkt                0.0781686749388
    winkels              0.0781686749388
    1015                 0.0595447787192
    1015 uur             0.0595447787192
    

## all word scores exported (subset)


```python
with open("terms/tfidf_scikit.csv", "wb") as file:
    writer = csv.writer(file, delimiter=",")
    writer.writerow(["ArticleId", "Phrase", "Score"])
 
    doc_id = 0
    for doc in tfidf_matrix.todense():
        print "Document %d" %(doc_id)
        word_id = 0
        for score in doc.tolist()[0]:
            if score > 0:
                word = feature_names[word_id]
                writer.writerow([doc_id+1, word.encode("utf-8"), score])
            word_id +=1
        doc_id +=1
```

`Out:`

    Document 0
    Document 1
    Document 2
    Document 3
    Document 4
    Document 5
    Document 6
    Document 7
    Document 8
    

## top word/article by tf-idf (subset)


```python
with open("terms/tfidf_scikit_top_word.csv", "wb") as file:
    writer = csv.writer(file, delimiter=",")
    writer.writerow(["ArticleId", "Phrase", "Score"])
 
    doc_id = 0
    for doc in tfidf_matrix.todense():
        word_id = 0
        top_score = 0
        for score in doc.tolist()[0]:
            if score > top_score:
                word = feature_names[word_id]
                top_score = score
            word_id +=1
        print "article %d\t tf-idf score: %f\t\t top word: %s" % (doc_id, top_score, word)
        writer.writerow([doc_id+1, word.encode("utf-8"), top_score])
        doc_id +=1
```

`Out:`

    article 0	 tf-idf score: 0.178634		 top word: bewindvoerders
    article 1	 tf-idf score: 0.234007		 top word: file
    article 2	 tf-idf score: 0.267838		 top word: turnhout
    article 3	 tf-idf score: 0.122609		 top word: 15
    article 4	 tf-idf score: 0.185682		 top word: waspik
    article 5	 tf-idf score: 0.192862		 top word: gedetineerden
    article 6	 tf-idf score: 0.204391		 top word: maart
    article 7	 tf-idf score: 0.122609		 top word: 15
    article 8	 tf-idf score: 0.266699		 top word: scooter
    

## all articles


```python
articles = defaultdict(list)
articleCnt = 1

for sub in subfolders:
    stories = os.listdir(articleDir + sub)
    for story in stories:
        with open(articleDir + sub + '/' + story, 'r') as f:
            for line in f:
                articles[articleCnt].append(removePunctuation(line.strip()))
            articleCnt += 1
            
print len(articles)
```

`Out:`

    185
    
```python
for article_id, text in articles.iteritems():
    articles[article_id] = "".join(text)
    
corpus = []
for id, article in sorted(articles.iteritems(), key=lambda t: int(t[0])):
    corpus.append(article)
    
corpus[-2:]
```

`Out:`



    ['tilburg  er is met mijn gezondheid en die van anderen gespeeldmustafa el mahdioui uit tilburg is ervan overtuigd dat hij kanker kreeg doordat hij treinen moest schuren met verf met chroom 6de tilburger werkte van 2004 tot 2011 met tussenpozen veelvuldig bij trom het reintegratiebedrijf van de gemeente dat vijftien treinen opknapte voor met name het spoorwegmuseum in utrechtel mahdioui kreeg in 2014 de diagnose lymfklierkanker na een aantal chemobehandelingen is hij inmiddels schoon verklaard maar het blijft als een sluipmoordenaar op je schouder zitten de tilburger gaf herhaaldelijk te kennen dat hij niet tegen het stof kon maar werd gedreigd met korting op zijn uitkeringde tilburger werkte van 2004 tot 2011 met tussenpozen veelvuldig bij trom het reintegratiebedrijf van de gemeente dat vijftien treinen opknapte voor met name het spoorwegmuseum in utrechtel mahdioui kreeg in 2014 de diagnose lymfklierkanker na een aantal chemobehandelingen is hij inmiddels schoon verklaard maar het blijft als een sluipmoordenaar op je schouder zitten de tilburger gaf herhaaldelijk te kennen dat hij niet tegen het stof kon maar werd gedreigd met korting op zijn uitkeringheeft u tussen 2004 en 2011 via integratiebedrijf trom in de nswerkplaats tilburg gewerkt met chroom 6 beschilderde treinen of heeft u als nswerknemer in de tilburgse werkplaats met de verf gewerkthet brabants dagblad wil graag met u in contact komen stuur ons een bericht via oproepbdnl',
     'den bosch  tilburg  jongerenwerk dat zich richt op het ontwikkelen van talenten voor bijvoorbeeld sport of muziek helpt bij het voorkomen van jeugdcriminaliteit bij jongerendat blijkt uit onderzoek in den bosch en tilburg van avansdocente maike kooijmans waarmee ze vrijdag 13 mei promoveert aan de universiteit van amsterdamvolgens kooijmans helpt het echter alleen bij jongeren die nog geen delicten plegen of die alleen beginnend crimineel gedrag vertonen bij jongeren die al op het criminele pad zijn sorteren de talentenontwikkelingprogrammas weinig effectde avansdocente en senior onderzoekster volgde samen met jongerenwerkers en medeonderzoekers van avansdrie jaar lang een groep van 50 jongerendie jongens namen deel aanhet voetbalproject doelbewust van welzijnsorganisatie divers uit den bosch en artistieke talentprojecten van het jongerenwerk rnewt van contourdetwern in tilburgexplosieve toenamede afgelopen jaren nam het aantal talentprogrammas door het jongerenwerk explosief toe maar f en hoe talentprogrammas werken werd volgens kooijmansniet eerder onderzocht twee getallen inhet onderzoek van kooijmans zetten de toonbij aanvang van het project blijkt 50 procent van de groep ooit een delict te hebben gepleegd maar in de eindfase van het onderzoek wist 78 procent uit de criminaliteit te kunnen blijven alleen lijken de projecten het risico op delinquentie niet te verminderen voor jongens die al meerdere delicten hebben gepleegdmaike kooijmans beschrijft haar resultaten en concrete tips in het boek talent van de straat hoe je jongeren kunt verleiden uit de criminaliteit te blijven het boek is vanaf 13 mei verkrijgbaar']




```python
tf = TfidfVectorizer(analyzer='word', ngram_range=(1,3), 
                     min_df = 0, stop_words = list(set(stopwords)), smooth_idf=False)

tfidf_matrix =  tf.fit_transform(corpus)
feature_names = tf.get_feature_names() 
len(feature_names)
```

`Out:`

    37952


```python
with open("terms/tfidf_scikit_top_word_ALL.csv", "wb") as file:
    writer = csv.writer(file, delimiter=",")
    writer.writerow(["ArticleId", "Phrase", "Score"])
 
    doc_id = 0
    for doc in tfidf_matrix.todense():
        word_id = 0
        top_score = 0
        for score in doc.tolist()[0]:
            if score > top_score:
                word = feature_names[word_id]
                top_score = score
            word_id +=1
#         print "article %d\t tf-idf score: %f\t\t top word: %s" % (doc_id, top_score, word)
        writer.writerow([doc_id+1, word.encode("utf-8"), top_score])
        doc_id +=1
```

`Out:`

## import article metadata and join with top tf-idf data


```python
articleDir = 'articles/'
os.listdir(articleDir)
metafiles = [x for x in os.listdir(articleDir) if 'csv' in x]
print len(metafiles)
metafiles[:10]
```

`Out:`

    62
    

    ['20160418_1727.csv',
     '20160419_0923.csv',
     '20160419_1314.csv',
     '20160419_1643.csv',
     '20160420_0918.csv',
     '20160420_1305.csv',
     '20160420_1655.csv',
     '20160421_0916.csv',
     '20160421_1210.csv',
     '20160422_0955.csv']




```python
articles_df = pd.DataFrame()

for f in metafiles:
    temp_df = pd.read_csv(articleDir + f, encoding='utf8')
    articles_df = articles_df.append(temp_df)
    
print articles_df.shape
articles_df.drop('Unnamed: 0', axis=1, inplace=True)
articles_df['ArticleId'] = range(1, (articles_df.shape[0] + 1))
# articles_df.set_index('ArticleId', drop=True, inplace=True)
articles_df.head()
```

`Out:`

    (185, 9)
    

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>link</th>
      <th>location_main</th>
      <th>locations</th>
      <th>map</th>
      <th>timestamp</th>
      <th>title</th>
      <th>txt_file</th>
      <th>ArticleId</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18 april 2016</td>
      <td>http://www.bd.nl/regio/oss-uden-veghel-e-o/ude...</td>
      <td>Uden</td>
      <td>[Home, Regio, Oss, Uden, Veghel e.o., Uden]</td>
      <td>[http://maps.google.com/maps?q=51.6631071,+5.6...</td>
      <td>20160418_1727</td>
      <td>Faillissement HoutBrox uitgesproken</td>
      <td>20160418/story1.txt</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18 april 2016</td>
      <td>http://www.bd.nl/regio/112-nieuws/ongeluk-tuss...</td>
      <td>112 Nieuws</td>
      <td>[Home, Regio, 112 Nieuws]</td>
      <td>NaN</td>
      <td>20160418_1727</td>
      <td>Ongeluk tussen 4 auto's op A58 zorgt voor file...</td>
      <td>20160418/story2.txt</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18 april 2016</td>
      <td>http://www.bd.nl/regio/boxtel-schijndel-e-o/ha...</td>
      <td>Haaren</td>
      <td>[Home, Regio, Boxtel, Schijndel e.o., Haaren]</td>
      <td>[http://maps.google.com/maps?q=51.6268095,+5.2...</td>
      <td>20160418_1727</td>
      <td>Zelfs stuntman had auto met moeite zo in huis ...</td>
      <td>20160418/story3.txt</td>
      <td>3</td>
    </tr>
    <tr>
      <th>0</th>
      <td>19 april 2016</td>
      <td>http://www.bd.nl/regio/economie/15-kandidaat-k...</td>
      <td>Economie</td>
      <td>[Home, Regio, Economie ]</td>
      <td>NaN</td>
      <td>20160419_0923</td>
      <td>Al 15 kandidaat-kopers voor failliete modekete...</td>
      <td>20160419/story1.txt</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>19 april 2016</td>
      <td>http://www.bd.nl/regio/112-nieuws/5-gewonden-b...</td>
      <td>112 Nieuws</td>
      <td>[Home, Regio, 112 Nieuws]</td>
      <td>[http://maps.google.com/maps?q=51.6843118,+4.9...</td>
      <td>20160419_0923</td>
      <td>5 gewonden bij ongeluk Waspik</td>
      <td>20160419/story2.txt</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
tfidf_df = pd.read_csv('terms/tfidf_scikit_top_word_ALL.csv', encoding='utf8')
# tfidf_df.set_index('ArticleId', drop=True, inplace=True)
tfidf_df.head()
```

`Out:`

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ArticleId</th>
      <th>Phrase</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>bewindvoerders</td>
      <td>0.186731</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>file</td>
      <td>0.191202</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>turnhout</td>
      <td>0.281711</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>succesvolle doorstart</td>
      <td>0.127030</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>waspik</td>
      <td>0.174633</td>
    </tr>
  </tbody>
</table>
</div>




```python
article_merge = pd.merge(articles_df, tfidf_df, how='outer', on='ArticleId')
print article_merge.columns
article_merge.head()
```

`Out:`

    Index([         u'date',          u'link', u'location_main',     u'locations',
                     u'map',     u'timestamp',         u'title',      u'txt_file',
               u'ArticleId',        u'Phrase',         u'Score'],
          dtype='object')
    




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>link</th>
      <th>location_main</th>
      <th>locations</th>
      <th>map</th>
      <th>timestamp</th>
      <th>title</th>
      <th>txt_file</th>
      <th>ArticleId</th>
      <th>Phrase</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18 april 2016</td>
      <td>http://www.bd.nl/regio/oss-uden-veghel-e-o/ude...</td>
      <td>Uden</td>
      <td>[Home, Regio, Oss, Uden, Veghel e.o., Uden]</td>
      <td>[http://maps.google.com/maps?q=51.6631071,+5.6...</td>
      <td>20160418_1727</td>
      <td>Faillissement HoutBrox uitgesproken</td>
      <td>20160418/story1.txt</td>
      <td>1</td>
      <td>bewindvoerders</td>
      <td>0.186731</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18 april 2016</td>
      <td>http://www.bd.nl/regio/112-nieuws/ongeluk-tuss...</td>
      <td>112 Nieuws</td>
      <td>[Home, Regio, 112 Nieuws]</td>
      <td>NaN</td>
      <td>20160418_1727</td>
      <td>Ongeluk tussen 4 auto's op A58 zorgt voor file...</td>
      <td>20160418/story2.txt</td>
      <td>2</td>
      <td>file</td>
      <td>0.191202</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18 april 2016</td>
      <td>http://www.bd.nl/regio/boxtel-schijndel-e-o/ha...</td>
      <td>Haaren</td>
      <td>[Home, Regio, Boxtel, Schijndel e.o., Haaren]</td>
      <td>[http://maps.google.com/maps?q=51.6268095,+5.2...</td>
      <td>20160418_1727</td>
      <td>Zelfs stuntman had auto met moeite zo in huis ...</td>
      <td>20160418/story3.txt</td>
      <td>3</td>
      <td>turnhout</td>
      <td>0.281711</td>
    </tr>
    <tr>
      <th>3</th>
      <td>19 april 2016</td>
      <td>http://www.bd.nl/regio/economie/15-kandidaat-k...</td>
      <td>Economie</td>
      <td>[Home, Regio, Economie ]</td>
      <td>NaN</td>
      <td>20160419_0923</td>
      <td>Al 15 kandidaat-kopers voor failliete modekete...</td>
      <td>20160419/story1.txt</td>
      <td>4</td>
      <td>succesvolle doorstart</td>
      <td>0.127030</td>
    </tr>
    <tr>
      <th>4</th>
      <td>19 april 2016</td>
      <td>http://www.bd.nl/regio/112-nieuws/5-gewonden-b...</td>
      <td>112 Nieuws</td>
      <td>[Home, Regio, 112 Nieuws]</td>
      <td>[http://maps.google.com/maps?q=51.6843118,+4.9...</td>
      <td>20160419_0923</td>
      <td>5 gewonden bij ongeluk Waspik</td>
      <td>20160419/story2.txt</td>
      <td>5</td>
      <td>waspik</td>
      <td>0.174633</td>
    </tr>
  </tbody>
</table>
</div>




```python
article_merge.to_csv('terms/article_meta_merge.csv', encoding='utf8')
```

`Out:`

```python
article_merge2 = article_merge[['ArticleId', 'timestamp', 'title', 'location_main', 'Phrase', 'Score']]
article_merge2.head()
```

`Out:`



<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ArticleId</th>
      <th>timestamp</th>
      <th>title</th>
      <th>location_main</th>
      <th>Phrase</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>20160418_1727</td>
      <td>Faillissement HoutBrox uitgesproken</td>
      <td>Uden</td>
      <td>bewindvoerders</td>
      <td>0.186731</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>20160418_1727</td>
      <td>Ongeluk tussen 4 auto's op A58 zorgt voor file...</td>
      <td>112 Nieuws</td>
      <td>file</td>
      <td>0.191202</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>20160418_1727</td>
      <td>Zelfs stuntman had auto met moeite zo in huis ...</td>
      <td>Haaren</td>
      <td>turnhout</td>
      <td>0.281711</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>20160419_0923</td>
      <td>Al 15 kandidaat-kopers voor failliete modekete...</td>
      <td>Economie</td>
      <td>succesvolle doorstart</td>
      <td>0.127030</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>20160419_0923</td>
      <td>5 gewonden bij ongeluk Waspik</td>
      <td>112 Nieuws</td>
      <td>waspik</td>
      <td>0.174633</td>
    </tr>
  </tbody>
</table>
</div>




```python
article_merge2.to_csv('terms/article_tfidf_merge.csv', encoding='utf8')
```

`Out:`

```python
article_merge2.groupby('location_main').count().sort('ArticleId', ascending=False)
```

`Out:`
    C:\Anaconda2\lib\site-packages\ipykernel\__main__.py:1: FutureWarning: sort(columns=....) is deprecated, use sort_values(by=.....)
      if __name__ == '__main__':
    




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ArticleId</th>
      <th>timestamp</th>
      <th>title</th>
      <th>Phrase</th>
      <th>Score</th>
    </tr>
    <tr>
      <th>location_main</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>112 Nieuws</th>
      <td>40</td>
      <td>40</td>
      <td>40</td>
      <td>40</td>
      <td>40</td>
    </tr>
    <tr>
      <th>Brabant</th>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
    </tr>
    <tr>
      <th>Tilburg</th>
      <td>25</td>
      <td>25</td>
      <td>25</td>
      <td>25</td>
      <td>25</td>
    </tr>
    <tr>
      <th>'s-Hertogenbosch</th>
      <td>22</td>
      <td>22</td>
      <td>22</td>
      <td>22</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Binnenland</th>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
    </tr>
    <tr>
      <th>Sport</th>
      <td>7</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
    </tr>
    <tr>
      <th>Hilvarenbeek</th>
      <td>6</td>
      <td>6</td>
      <td>6</td>
      <td>6</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Oss</th>
      <td>6</td>
      <td>6</td>
      <td>6</td>
      <td>6</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Uden</th>
      <td>5</td>
      <td>5</td>
      <td>5</td>
      <td>5</td>
      <td>5</td>
    </tr>
    <tr>
      <th>Vught</th>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Sint-Michielsgestel</th>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Zaltbommel</th>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Haaren</th>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Economie</th>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Willem II</th>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Loon op Zand</th>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Schijndel</th>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Buitenland</th>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Heusden</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Waalwijk</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Boekel</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Voetbal</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>FC Oss</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>FC Den Bosch</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>PSV</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Gemert-Bakel</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Oisterwijk</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Goirle</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Lintjes</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
article_titles = list(article_merge2.title)
article_titles[:5]
```

`Out:`



    [u'Faillissement HoutBrox uitgesproken',
     u"Ongeluk tussen 4 auto's op A58 zorgt voor file richting Tilburg",
     u'Zelfs stuntman had auto met moeite zo in huis Helvoirt gekregen',
     u'Al 15 kandidaat-kopers voor failliete modeketen HoutBrox',
     u'5 gewonden bij ongeluk Waspik']



