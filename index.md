	


<p align="center">
	<a href="https://postimg.cc/dL9WhCRB">
  		<img img src="https://i.postimg.cc/jdpBkQLG/ada-group-project-spaghetti-carbonada.png">
	</a>
</p>

<!-- [![ada-group-project-spaghetti-carbonada.png](https://i.postimg.cc/jdpBkQLG/ada-group-project-spaghetti-carbonada.png)](https://postimg.cc/dL9WhCRB) -->

# About QuoteBank
MISSING
# An initial text comparison: victory speeches

In order to get a first taste of how the metrics work, we will analyze two famous victory speeches by Barack Obama and Donald Trump. The two speeches have one thing in common: they both shocked the world at their times. The former was pronunced in an historic moment of U.S. history, when the first afro-american president was elected. The latter rapresented the victory of one the most controversial candidate of the U.S. modern era, who a lot of people did not expect to win.
Barack Obama and Donald Trump deal with dialogue in two very different ways. What we want to show is how powerful the metrics are in order to detect this differences automatically. Here are the two extracts from the two speeches, on which we computed the metrics: 

> *If there is anyone out there who still doubts that America is a place where all things are possible; who still wonders if the dream of our founders is alive in our time; who still questions the power of our democracy, tonight is your answer.
It's the answer told by lines that stretched around schools and churches in numbers this nation has never seen; by people who waited three hours and four hours, many for the very first time in their lives, because they believed that this time must be different; that their voice could be that difference.
It's the answer spoken by young and old, rich and poor, Democrat and Republican, black, white, Latino, Asian, Native American, gay, straight, disabled and not disabled — Americans who sent a message to the world that we have never been a collection of red states and blue states; we are, and always will be, the United States of America.
<br><br> **Obama's Victory Speech** (2008)*

<br><br>

> *Thank you. Thank you very much, everybody. Sorry to keep you waiting. Complicated business. Complicated. Thank you very much.
I've just received a call from Secretary Clinton. She congratulated us. It's about us. On our victory, and I congratulated her and her family on a very, very hard-fought campaign.
I mean, she fought very hard. Hillary has worked very long and very hard over a long period of time, and we owe her a major debt of gratitude for her service to our country.
I mean that very sincerely. Now it is time for America to bind the wounds of division, have to get together. To all Republicans and Democrats and independents across this nation, I say it is time for us to come together as one united people.
It is time. I pledge to every citizen of our land that I will be President for all of Americans, and this is so important to me. For those who have chosen not to support me in the past, of which there were a few people, I'm reaching out to you for your guidance and your help so that we can work together and unify our great country.
<br><br> **Trump's Victory Speech** (2008)*





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


### MTLD and VOC-d
The MTLD and the VOC-d measures are lexical diversity measures.

#### VOC-d
In order to calculate the VOC-d metric we follow the following steps:
1. From the text, we take 100 samples made of 35 tokens.
2. For each of these samples, we compute the Type-to-Token ratio (TTR). TTR is the ratio obtained by dividing the types (the total number of different words) occurring in a text by  its tokens (the total number of words).
3. We calculate the mean TTR of the the 100 samples.
4. We repeat the steps 1,2,3 , and each time we increase by 1 the number of tokens we take, for values 36 to 50.
5. We create a curve with the mean values of the TTR.
6. We approximate the empirical TTR curve by defining a new curve which depends on a parameter we call D coefficient.
7. We choose the optimal D coefficient which fits the curve and we store it.
8. We run procedure 1-7 for 2 more times, such that in the end we have 3 optimal D values.
9. We compute the mean of the D values, this is the final score (which ranges from 10 to 100).


### Unique words
This is yet another diversity metric that we implemented from scratch. Given a certain window of words taken into consideration, for instance 1000 words, how many unique words does the person use? This measure gives a rough estimate of the lexical diversity of the speaker. 

### CEFR Level
Finally, thanks to the help of an API, we managed also to estimate the English level of the speaker (CEFR Level) in a scale from A1 to B2.
The metric for the CEFR level is computed by analyzing the level of each word used in a text.  The same word might also have different levels based on how it is used. For example, hunt as a verb for killing animals is B1, hunt as a verb for searching someone or something is B2, while hunt as a noun is C2. In this case, we consider each word for the lowest level (in the case of the example, B1). Once the level of each word is determined, this information is aggregated and used to produce the final estimate of the language level of the text. The computation takes into account around 30 different metrics, metrics such as:

* Statistics/Syllables
* Lexical diversity
* Lexical Sophistication: English Vocabulary Profile (incl. % of words at each level)
* Lexical Sophistication: British National Corpus
* Lexical Sophistication: Corpus of Contemporary American English
* Lexical Sophistication: Academic Word List
* Metadiscourse markers


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

### Hypothesis Testing

In this section, we check whether there is a significant difference in language within these 6 different groupings:

1. Democrats vs Repubblicans
2. House members vs Senate member
3. House Democrats vs House Repubblicans
4. Senate Democrats vs Sanate Repubblicans
5. House Democrats vs Senate Democrats
6. House Repubblicans vs Senate Repubblicans


All the three metrics agreed on the significance for all groupings. The results of the tests are:

1. Democrats vs Repubblicans:                 **significant**
2. House members vs Senate member:              non-significant
3. House Democrats vs House Repubblicans:     **significant**
4. Senate Democrats vs Sanate Repubblicans:     non-significant
5. House Democrats vs Senate Democrats:         non-significant
6. House Repubblicans vs Senate Repubblicans:   non-significant


