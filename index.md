<head>

<title>My Site</title>

<style>

.site-header{

height:400px;

}

</style>

</head>

<header class="site-header">

<img src="http://bit.ly/1ZK2tfG" height="300px" width="100%"/>

</header>
	
	


<p align="center">
	<a href="https://postimg.cc/dL9WhCRB">
  		<img img src="https://i.postimg.cc/jdpBkQLG/ada-group-project-spaghetti-carbonada.png">
	</a>
</p>

<!-- [![ada-group-project-spaghetti-carbonada.png](https://i.postimg.cc/jdpBkQLG/ada-group-project-spaghetti-carbonada.png)](https://postimg.cc/dL9WhCRB) -->

# About QuoteBank
MISSING


# Framing our research


<p align="center">
	<a href="https://i.postimg.cc/JzRhLGmp/matteo-vs-matteo.png">
  		<img width="600" height="400" src="https://i.postimg.cc/JzRhLGmp/matteo-vs-matteo.png">
	</a>
</p>





In the new technology and social media era we are constantly exposed to politics, and thus political speech. One thing that’s easy to notice is that some politicians have a more refined speech than others. 
One very famous example of this phenomenon struck our attention some time ago in the quiet turbulent context of Italian politics: Porta a Porta, a very famous Italian talk show on politics, hosted a debate between politicians Matteo Renzi and Matteo Salvini. Soon after the beginning of the debate, viewers started noticing the stark difference in the way the politicians talked: Renzi used long sentences, used a varied lexicon while Salvini did the opposite: he used simpler words in a repetitive manner, keeping the phrases more simple than Renzi’s.
Renzi and Salvini are not alone, indeed we found that such differences can be found while considering many other politicians from the two sides of the political spectrum.

<!--- [![trump-youtube.png](https://i.postimg.cc/GmFFmBZV/trump-youtube.png)](https://www.youtube.com/watch?v=phsU1vVHOQI) -->

<p align="center">
	<a href="https://www.youtube.com/watch?v=phsU1vVHOQI">
  		<img width="600" height="400" alt="trump-youtube" src="https://i.postimg.cc/GmFFmBZV/trump-youtube.png">
	</a>
</p>


# What are we looking for? Research question


Our supposition is that there is a difference in the linguistic usage between the two sides of the political spectrum. We suspect this difference to be found in the 

number of different words while speaking (variety of lexicon)
different length of phrases
number of repetitions
different structuring of the phrases (number of subordinate vs coordinate phrases)

{% include figchemical_2.html %}

{% include figchemical_3.html %}

We plan to investigate whether this difference is present in the US political landscape. In other words, is the language that Republicans use much different than those that Democrats use. 

# How do we measure?
The question is: how can we measure the lexical level of a person from their quotes? Basically we aggregated many quotes (2000 on average!) for each politician, extracted randomly if they had more than that, in order to create a text. Then, we used some metrics to evaluate the text. To conduct our analysis on the politicians' words we will use seven different metrics.

The metrics we used are the following:
Flesch reading-ease
Flesch-Kincaid Grade
Gunning Fog Index
MTLD
VOC-d
CEFR Level
Number of unique words in a certain word window

The first three metrics estimate very similar things, using them all together allowed us to build a more robust measure. 

### Flesch reading-ease
The Flesch reading-ease index is a measure for the “readability” of a text. The higher the score, the “simpler” the text, and the easier it is to read. (Hence, in our analysis, a high score indicates that the politician has a very simple language. It can be correlated either with a lack of education or with a willingness to be understood by everybody!).
The formula for the Flesch reading-ease score is the following: 

To provide the reader with an intuition of the meaning of the values, this is a rough correspondence between the values of the index with the school level at which that property of speech is achieved.

| Command | Description |
| --- | --- |
| `git status` | List all *new or modified* files |
| `git diff` | Show file differences that **haven't been** staged |
	
	
| Score | School level (US) | Notes |
| --- | --- | --- |
| `git status` | List all *new or modified* files | bla |
| `git diff` | Show file differences that **haven't been** staged | bla |
	
| Score | School level (US) | Notes |
| --- | --- | --- |	
|100.00–90.00	| 5th grade	|Very easy to read. Easily understood by an average 11-year-old student.|
|90.0–80.0	|6th grade	|Easy to read. Conversational English for consumers.|
|80.0–70.0	|7th grade       |	Fairly easy to read.|
|70.0–60.0	|8th & 9th grade|	Plain English. Easily understood by 13- to 15-year-old students.|
|60.0–50.0	|10th to 12th grade|	Fairly difficult to read.|
|50.0–30.0	|College	|   Difficult to read.|
|30.0–10.0	|College graduate|	Very difficult to read. Best understood by university graduates.|
|10.0–0.0	|Professional	|Extremely difficult to read. Best understood by university graduates.|


### Flesch-Kincaid Grade
The Flesch-Kincaid Grade is a modification of the Flesch Reading Ease index, and has a nice straightforward interpretation: its output represents roughly the number of years of education required to understand the text provided. The formula for the grade is the following:

{% include porco.html %} 
### Gunning Fog Index
The Gunning Fog index is yet another readability score. Very closely to the Flesch-Kincaid Grade, it tries to make an estimate of the number of years of formal education needed to understand the text when reading it for the first time. The formula for the Gunning fox index is the following, where “complex words” are defined as the words with 3 or more syllables. 


<iframe src="https://prova-robi-cera.herokuapp.com" style=" width: 800px; height: 800px;  overflow: hidden;" scrolling="no"></iframe>


Again, to provide the intuition of the correspondence between the score and the grade level needed to understand the text, we provide the following table:
%INSERIRE TABELLA

### MTLD and VOC-d
The MTLD and the VOC-d measures are lexical diversity measures.


### Unique words
This is yet another diversity metric that we implemented from scratch. Given a certain window of words taken into consideration, for instance 1000 words, how many unique words does the person use? This measure gives a rough estimate of the lexical diversity of the speaker. 

### CEFR Level
Finally, thanks to the help of an API, we managed also to estimate the English level of the speaker (CEFR Level) in a scale from 
The computation takes into account around 30 different metrics, from…


## EXAMPLE
As an example, let’s consider for instance a small text from Donald Trump and one from Barack Obama and let’s compute the metrics for both. 
TODO
- Choose text of Trump
- Choose text of Obama
- Apply scripts

# Map test

{% include map_test.html %} 

# Graph test

{% include graph_test.html %} 

# Academic Prova

{% include academic_prova.html %} 

# Othe tests

{% include graph_party_test.html %} 
{% include graph_age_test.html %} 
{% include graph_congress_test.html %} 
{% include graph_chamber_test.html %} 


# Let's start our investigation...

ONE VS ONE COMPARISON

CLOUDS OF WORDS

FAMOUS POLITICIANS

# Aggregate comparisons

MAP, AGE, PARTY ...


Bla bla
Bla bla

{% include porco.html %}

Bla bla DIO BONO


