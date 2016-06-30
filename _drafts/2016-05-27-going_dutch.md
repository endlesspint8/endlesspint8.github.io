---
layout: post
title: Going Dutch ...but I digress
subtitle: Learning a Language with Modern Tools
---


## Are we really only going to talk about one issue? 

Please, that's tedious, leaves you open to some <a href="https://www.youtube.com/watch?v=JcRHUOTNobE" target="_blank">well deserved ribbing</a>, and <a href="https://en.wikipedia.org/wiki/Prohibition_Party" target="_blank">it's how Prohibition was passed</a> (I think we've all learned from that mistake). Like most of us are wont to do <a href="https://youtu.be/-jqCqvGuutQ?t=110" target="_blank">in real life</a> let us jump from subject to subject, share stories, describe our dreams and brilliant ideas that only an ample amount of drinking would allow us to divulge and share with another. That's what this post is and, similarly to a regular conversation, feel free to change the subject and browse to another more beer-centric posting, whether through poking around or following one of several links sprinkled through the text (here’s an interesting tie-in with <a href="http://www.theguardian.com/world/2016/apr/25/amsterdam-kings-day-urine-plan" target="_blank">beer and the Dutch</a>).

I don’t know about you but after a six pack (or six posts in this case) I usually deem myself witty, engaging, and a purveyor of interesting stories and amusing anecdotes. I become loquacious and expansive in my insightful commentary. It is also clear that those around me share this outlook, that they are more easily swayed by my charm which I normally, responsibly, and modestly keep at bay for fear of misusing its power. Dare I say that the barriers of language appear to melt away and those fortunate enough to be present in my company communicate as if by thought alone with words discarded nearly as soon as they’re spoken, disappearing leaving only <a href="https://www.youtube.com/watch?v=CSaFgAwnRSc&feature=youtu.be&t=25" target="_blank">the meaning behind</a>.

But in recent months I’ve encountered an obstacle: actually living abroad. The <a href="https://www.youtube.com/watch?v=VEsrYaQYQSo" target="_blank">mind meld</a> I have grown accustomed to has been more difficult to come by. Forget for a moment that <a href="https://www.quora.com/Why-do-Dutch-people-speak-English-so-well" target="_blank">the Dutch all speak English</a> (and without the unnecessary shithead attitude <a href="https://books.google.nl/books?id=E5fotqsglPEC&pg=PA119&lpg=PA119&dq=french+attitude+towards+english&source=bl&ots=TfR2ooBxS5&sig=s-Z2HvgUHrKO3_BlvxM2wT_qQNo&hl=en&sa=X&ved=0ahUKEwjHvZ2ovsvNAhXDthQKHVrLBdgQ6AEIMTAD#v=onepage&q=french%20attitude%20towards%20english&f=false" target="_blank">so finely cultivated by the French</a>), which helps lighten the burden and ensures some exchange of earth shattering insights, one cannot help but feel bad that these people are not more fully exposed to my genius.

> There is no off position on the genius switch. - David Letterman

It turns out that language remains a necessary bridge. I cannot bear the thought of withholding from these good people any longer. It is time I make a stronger effort at making myself understandable more completely and attempt to meet the adorably accented people of the Netherlands halfway.<sup id="a1">[1](#f1)</sup> Afterall, the Dutch founded NYC, make damn good beer themselves, & having recently/temporarily/in-denial-about-the-whole-finality-of-the-prospect relocated to the land of various combinations of <a href="https://www.youtube.com/watch?v=_LlPU6KenjU" target="_blank">smoking and breakfast pastries</a> I sorta, kinda, wanna, needta do this.

The objective: to learn some of the language and a bit about contemporary Dutch life. Where to turn? How about that item that was nearly killed off by the Internet: the newspaper? I'm in a particular part of the country, which translated to American-ese means “not in Amsterdam”, and I wanted to take that into consideration. Why not use another resource, one that replaced an actual internet casualty: Wikipedia.

**Regional Dutch newspapers**:

<img src="/gallery/2016/dutch/wiki_newspapersNL.PNG" alt="Wikipedia Regional Dutch Newspapers" />

<sub>Data Source: <a href="https://en.wikipedia.org/wiki/List_of_newspapers_in_the_Netherlands#Regional_newspapers" target="_blank">Wikipedia</a></sub>

I volunteered one of the above publications to be my vic-, source, and proceeded to pull three front page stories each day, 2-3 times a day, for 4 weeks. The idea was to capture all article text plus some metadata characteristics: date, time, subject classification, and map coordinates where applicable. 

## As Easy as 1-2-3 (een-twee-drie)?

Simple and <a href="https://www.youtube.com/watch?v=IIf9diK-6wk" target="_blank">too easy</a>? Not completely. There was a good amount of legwork needed. My three-pronged approach to this exercise: <a href="https://en.wikipedia.org/wiki/Word_count" target="_blank">word count</a>, <a href="https://en.wikipedia.org/wiki/Bigram" target="_blank">bigrams</a>, and term frequency - inverse document frequency (<a href="https://en.wikipedia.org/wiki/Tf%E2%80%93idf" target="_blank">tf-idf</a>). I thought each of these methods would be helpful in finding out more about Dutch and possibly where to start with the language. But before all that I would need to identify <a href="https://en.wikipedia.org/wiki/Stop_words" target="_blank">stop words</a>. 

Stop words are typically the most common words in use over a collection of documents. They are neither surprising in their frequency nor very informative when it comes to recognizing subjects covered. They are of course critical to being understood in normal communication, being the glue that helps string words into sentences (conjunctions, prepositions, and pronouns). The purpose for my identifying Dutch stop words was thus two-fold: to use them as a screen to get to the more interesting words and to keep them around for my own elucidation. While not computationaly interesting they could still prove to be a meaningful resource to my learning ambitions.

Where to find stop words? <a href="http://vignette1.wikia.nocookie.net/logopedia/images/b/bb/Jeeves_too.jpg/revision/latest?cb=20110511061243" target="_blank">AskJeeves</a>! Na, I’m just kidding. I asked Uncle Google, of course. I thought that I may get an English list of words and translate those into Dutch, but that turned out to be unncessary. Instead, I took three results from <a href="https://www.google.nl/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=dutch%20stop%20words" target="_blank">the first search page returned</a>, made <a href="/code/dutch_stop_words" target="_blank">a superset of the words from each list</a>, and then had something to screen against.<sup id="a2">[2](#f2)</sup> 

<p align="center">
  <b>Stop Words</b><br>
  <a href="/code/dutch_stop_words" target="_blank">Code</a> |
  <a href="/datasets/dutch/stopwords_table_wTransCount2.csv" target="_blank">Data Set</a>
  <br><br>
  <img src="/gallery/2016/dutch/output_1sw.gif">
</p>

**Top-10 Stop Words**

|term|translation|count|
|---|---|---|
|de|the|2481|
|van|from|1078|
|het|the|1063|
|een|a|923|
|in|in|861|
|en|and|615|
|op|on|544|
|is|is|435|
|dat|it|403|
|te|too|324|

For those who've done the “<a href="http://www.learnpython.org/en/Hello,_World!" target="_blank">Hello world</a>” of big data you can anticipate my next steps. Get a word count across all articles, filter out stop words, and sort in descending order of <a href="https://xkcd.com/1331/" target="_blank">frequency</a>. I figured <a href="/datasets/dutch/top100_nonStopWords.csv" target="_blank">the top 50-100 words</a> would be a strong place to start for any future flash cards, at least before the Internet destroys them as well. 

Though I want to be absolutely clear about two things: this is NOT big data AND I know that. I simply wanted an excuse to get some more practice with <a href="https://spark.apache.org/docs/1.2.0/programming-guide.html" target="_blank">Spark</a> and running <a href="https://www.vagrantup.com/" target="_blank">Vagrant</a> (partial nerd talk for data tools).

**Top-10 Non-Stop Words**

|term|translation|count|
|---|---|---|
|politie|police|152|
|bosch|bosch|149|
|den|pine|138|
|tilburg|tilburg|107|
|uur|hour|91|
|volgens|according to|87|
|jaar|year|76|
|mensen|people|67|
|gaat|going|62|
|man|man|51|

<p align="center">
  <b>Top Words</b><br>
  <a href="/code/dutch_words/#all-without-stop-words" target="_blank">Code</a> |
  <a href="/datasets/dutch/top100_nonStopWords.csv" target="_blank">Data Set</a>
  <br><br>
  <img src="/gallery/2016/dutch/output_2top.gif">
</p>


## Hello World 2,  or better yet… Hallo Wereld Twee

Single words were a good start but how about something a bit more interesting, perhaps <a href="https://en.wikipedia.org/wiki/Bigram" target="_blank">bigrams</a>. It'd be nice to start stringing words together, especially inspired by an authoritative source.

The process was similar to the above with the obvious addition of taking two words and punctuation into consideration. We only string two words together that are within the same sentence. It would be troublesome to take the last word of one sentence and combine it with the first word of the following sentence. That would result in some odd, though perhaps poetic & <a href="https://www.youtube.com/watch?v=CjfSGPJo-cg&list=PLfpbZvWz5uKsMnGlsoDUnXjn_TfrGBJKO" target="_blank">deep combinations</a>. Maybe an exercise for another time. 

**Top-10 Bigrams**

|terms|translation|count|
|---|---|---|
|van de|of the|274|
|in de|in the|227|
|de politie|the police|145|
|op de|on the|141|
|den bosch|bosch|118|
|van het|from the|115|
|in het|in the|102|
|aan de|to the|86|
|van een|of a|77|
|voor de|for the|73|

<p align="center">
  <b>Bigrams</b><br>
  <a href="/code/dutch_words/#bigrams-baby" target="_blank">Code</a> |
  <a href="/datasets/dutch/BD_bigrams.csv" target="_blank">Data Set</a>
  <br><br>
  <img src="/gallery/2016/dutch/output_3bi.gif">
</p>


## TF-IDF: 

The final approach covered was yet one step of sophistication further but still a simple concept. We wish to identify words that are often used but balance that out by overly common words that appear in many articles. For instance, we would expect large counts for stop words but if we had a way for penalizing words as common as these we should be able to find article-specific interesting terms. 

An example of how this works will go a long way to explaining its power. Suppose three articles with the following words:

| article | beer | hops | malt | ipa | stout |
| ------- | ---- | ---- | ---- | --- | ----- |
| 1 | 3 | 4 | 0 | 2 | 0 |
| 2 | 5 | 2 | 1 | 3 | 0 |
| 3 | 2 | 1 | 1 | 0 | 2 |

To determine the importance of a term using tf-idf we will need to first count three things: the number of times a word appears in a document/article, the total of documents the term appears in, and the total number of documents. Lastly we will combine these counts so as to get a final score (the higher the more important the term). Let us take the term "beer" which you may intuitatively be able to see, forgive me for saying it,  is not important in this data set, since it appears in each document.

> document: 2
>
> term: "beer"
>
> tf: 5
>
> idf: 3/3 = 1 (numerator: # of all docs, denominator: # of docs "beer" appears in, NOT using log for simplicity)
>
> tf-idf: 5 * 1 = 5

Now let us look at "stout". It appears just twice and in only one article but perhaps you can see where this is going and also intuit that "stout" says more in this collection than the more common "beer".

> document: 3
>
> term: "stout"
>
> tf: 2
>
> idf: 3/1 = 3 (numerator: # of all docs, denominator: # of docs "stout" appears in, NOT using log for simplicity)
>
> tf-idf: 5 * 3 = 15

Hopefully the above examples help to highlight how the process works in identifying key terms for each article, or day, or whatever your choice of unit. 

**Top-10 tf-idf**

|term|translation|score|
|---|---|---|
|weekmarkten|weekly markets|0.455494961|
|turkse|Turkish|0.420251094|
|lintjes|ribbons|0.39047604|
|jongeren|youth|0.370535377|
|autobranden|vehicle fires|0.369480315|
|groei|growth|0.326314964|
|yenice|yenice|0.323526478|
|psv|pSV|0.318184196|
|hoorn|Horn|0.312658317|
|volkel|volkel|0.312110305|

**Top-10 tf-idf World Cloud** (with apologies to <a href="https://twitter.com/dataskeptic" target="_blank">Kyle</a> at <a href="http://dataskeptic.com/epnotes/kill-the-word-cloud.php" target="_blank">Data Skeptic</a>)

<img src="/gallery/2016/dutch/tf_idf9.png">

## Conclusion

How far along has this excercise gotten us to deciphering Dutch? I took some random sentences and ran them against our numerous word collections <a href="https://gist.github.com/endlesspint8/5078720acd978067e7ddafc4e8e0fbd8#file-translate-py" target="_blank">to get an idea</a>. Let's just say it wasn't pretty and that maybe I need more tijd en werk.<sup id="a3">[3](#f3)</sup> The next thought was to translate the respective article titles to see if there was any better luck. In een werd: <a href="https://gist.github.com/endlesspint8/5078720acd978067e7ddafc4e8e0fbd8#file-translate_titles-py" target="_blank">nee</a>.<sup id="a4">[4](#f4)</sup> 

Below you can see the original content, my best approximation (I was lenient on the grammar aspect), and Google translate's take.

Searched articles for highest word percentage match: 64%

    HAAREN - In een woning aan de Blazeveldweg in het gebied de Noenes bij Haaren is maandag een overleden vrouw aangetroffen
    HAAREN - in a house to the Blazeveldweg in the gebied the Noenes at Haaren is maandag a overleden woman aangetroffen
    
    Een ambulance ging rond 10.30 uur al op de melding af van de Blazeveldweg
    according to the Police his there no aanwijzingen that the woman by a misdrijf to the leven is gekomen. because the police echter nevertheless a misdrijf not want uitsluiten, is uitgebreid research gedaan to the doodsoorzaak.Melding a ambulance went around 10.30 hour already on the melding down of the
    
    Destijds was het volgens de politie nog niet duidelijk wat er aan de hand was
    Destijds was the according to the Police not yet duidelijk What there to the hand was
    
    Rond 12.30 uur meldt zij dat ze de vrouw hebben aangetroffen.
    around 12.30 hour reports they it she the woman have aangetroffen.

[table of sentence with (partial) translations]

I'm cleary not going to become fluent just yet with the work to date. I suppose the best I could hope for is some sort of beautiful Dutchlish monster. However, it is a start and that was my general intention. While my newly acquired vocabulary will get me into the pergatory of language understandability (https://www.youtube.com/watch?v=Vt4Dfa4fOEY), leaving me out of touch, as far as
this excersise is concerned I'm also out of time (https://www.youtube.com/watch?v=s_8KR-n2fBQ).


<br>

---

**Left Out**

- **Mapping** locations of news stories to review geographical/temporal/subject locations or trends.
- **Clustering** of news stories.
- **Sentiment Analysis** - should be a bit odd for news articles, but potentially interesting.
- **Comments/Tweets** - perhaps more appropriate for SA
- **Classification** - based on the findings, some possible examples would have been for determining articles related to traffic (“bus”), crime (“politie”), or sports (“<a href="https://www.psv.nl/" target="_blank">PSV</a>”); could have implemented <a href="https://en.wikipedia.org/wiki/Bag-of-words_model" target="_blank">bag of words</a>.

All of the above, and more, can be performed on any number of text-based data sets. Look out for most of these to begin appearing in the posts to come.

<br>

---

**Notes**

<b id="f1">1</b> Honestly, have a Dutch person speak to you in English; more than half the time _it is_ adorable. [↩](#a1) <br>

<b id="f2">2</b> Sources listed below with identified contacts:

1. http://snowball.tartarus.org/algorithms/dutch/stop.txt; http://www.patrickmileswriter.co.uk/ \ mail@patrickmiles.co.uk
2. http://www.ranks.nl/stopwords/dutch; damian@ranks.nl
3. http://www.damienvanholten.com/blog/dutch-stop-words/; http://twitter.com/damienvanholten [↩](#a2) <br>

<b id="f3">3</b> time and work [↩](#a3) <br>

<b id="f4">4</b> In a word: <a href="https://www.youtube.com/watch?v=9o19CaOSuD8" target="_blank">oh, hell no</a>!<sup id="a4a">[4a](#f4a)</sup>  [↩](#a4) <br>
  <b id="f4a">4a</b> Just a little American exageration.  [↩](#a4a) <br>

Tools

1. PySpark via Vagrant from Berkely by way of edX; https://twitter.com/atalwalkar
2. <a href="https://www.vagrantup.com/docs/synced-folders/basic_usage.html" target="_blank">Sync folders</a> in Vagrant; https://twitter.com/vagrantup
3. Create <a href="http://gifmaker.me/" target="_blank">gif</a>; gifmaker.me
4. Word cloud at http://www.wordle.net/advanced

Techniques

1. https://spark.apache.org/docs/1.2.0/programming-guide.html; https://twitter.com/ApacheSpark; #Spark
2. http://www.mccarroll.net/blog/pyspark2/; esp for <a href="http://en.wikipedia.org/wiki/Bigram" target="_blank">bigram</a>
3. tf-idf w/sklearn; http://www.markhneedham.com/blog/2015/02/15/pythonscikit-learn-calculating-tfidf-on-how-i-met-your-mother-transcripts/; https://twitter.com/markhneedham; #sklearn

Normal Text
Source for centering: https://coderwall.com/p/iftc1q/centered-text-and-images-in-github-markdown; https://twitter.com/CleverWebStaff
