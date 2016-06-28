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

## As Easy as 1-2-3 (Een-twee-drie)?

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

[table of three columns]

[simple math w/resulting scores]

Helpful in identifying key terms for each article, or day or whatever your choice of unit. Typically a good step towards getting a better representation of what the topic (of the article) is and prepares the way for future clustering possibilities, a topic for another day.

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

World cloud with apologies to <a href="https://twitter.com/dataskeptic" target="_blank">Kyle</a> at <a href="http://dataskeptic.com/epnotes/kill-the-word-cloud.php" target="_blank">Data Skeptic</a>.

<img src="/gallery/2016/dutch/tf_idf9.png">

<p align="center">
  <b>tf-idf</b><br>
  <a href="/code/dutch_words/#all-articles-via-sklearn" target="_blank">Code</a> |
  <a href="/datasets/dutch/article_tfidf_merge.csv" target="_blank">Data Set</a>
  <br><br>
  <img src="/gallery/2016/dutch/output_4tfidf.gif">
</p>

## Conclusion



How far along has this excercise gotten us to deciphering Dutch? I took some random sentences and ran them against our numerous word collections <a href="https://gist.github.com/endlesspint8/5078720acd978067e7ddafc4e8e0fbd8#file-translate-py" target="_blank">to get an idea</a>. Let's just say it wasn't pretty and that maybe I need more tijd en werk.<sup id="a3">[3](#f3)</sup> 

Below you can see the original content, my best approximation (I was lenient on the grammar aspect), and Google translate's take.

[table of sentence with (partial) translations]

[concluding comments]


<br>

---

**Left Out**

- **Mapping** locations of news stories to review geographical/temporal/subject locations or trends.
- **Clustering** of news stories.
- **Sentiment Analysis** - should be a bit odd for news articles, but potentially interesting.
- **Comments/Tweets** - perhaps more appropriate for SA
- **Classification** - based on the findings, some possible examples would have been for determining articles related to traffic (“bus”), crime (“politie”), or sports (“PSV” [link]); could have implemented <a href="https://en.wikipedia.org/wiki/Bag-of-words_model" target="_blank">bag of words</a>.

All of the above, and more, can be performed on any number of text-based data sets. Look out for most of these to begin appearing in the posts to come.

<br>

---

**Notes**

<b id="f1">1</b> Honestly, have a Dutch person speak to you in English; more than half the time it is adorable. [↩](#a1) <br>

<b id="f2">2</b> Sources listed below with identified contacts:

1. http://snowball.tartarus.org/algorithms/dutch/stop.txt; http://www.patrickmileswriter.co.uk/ \ mail@patrickmiles.co.uk
2. http://www.ranks.nl/stopwords/dutch; damian@ranks.nl
3. http://www.damienvanholten.com/blog/dutch-stop-words/; http://twitter.com/damienvanholten [↩](#a2) <br>

<b id="f3">3</b> time and work [↩](#a3) <br>

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
