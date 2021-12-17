	
<p align="center">
	<a href="https://postimg.cc/dL9WhCRB">
  		<img img src="https://i.postimg.cc/jdpBkQLG/ada-group-project-spaghetti-carbonada.png">
	</a>
</p>




<!-- [![ada-group-project-spaghetti-carbonada.png](https://i.postimg.cc/jdpBkQLG/ada-group-project-spaghetti-carbonada.png)](https://postimg.cc/dL9WhCRB) -->

# About QuoteBank
Quotebank is an open corpus of 178 million quotations extracted from 162 million English news articles published in the years between 2008 and 2020. Each quotation is extracted and attributed to the speakers who uttered them thanks to the Quobert model, which is language and corpus-agnostic.  Both Quotebank and Quobert are publicly available at :https://doi.org/10.5281/zenodo.42773118




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


We plan to investigate whether this difference is present in the US political landscape. In other words, is the language that Republicans use much different than those that Democrats use. 


# Initial exploration: what data do we have?

We can notice the politicians taken into account are balanced between Democrats and Republicans. Clearly there are many more Congressmen than Senators as it's natural given the House of Representatives is composed by 435 members, while the Senate includes only 100 individuals. Age-wise we can see that the majority of US Representatives included in our metrics were born in the 50s and 60s, and only 115 out of 539 considered were born in the 70s or later. Naturally by the way each congressman is assigned to a number of congress the 114th is the most represented. 58 is the number of politicians considered who were first elected in 2016 (first mandate during the 115th Congress), while this number increases to 77 for the midterm elections of 2018. (For the sunburst graphs, click on the charts to visualize the details!)

{% include pie_state.html %}



{% include sunburst_1.html %}



{% include sunburst_2.html %}



{% include sunburst_3.html %}



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

### Gunning Fog Index
The Gunning Fog index is yet another readability score. Very closely to the Flesch-Kincaid Grade, it tries to make an estimate of the number of years of formal education needed to understand the text when reading it for the first time. The formula for the Gunning fox index is the following, where “complex words” are defined as the words with 3 or more syllables. 



### MTLD and VOC-d
The MTLD and the VOC-d measures are lexical diversity measures.


#### MLTD

The idea behind the MTLD is a sequential evaluation of TTR, where TTR is defined as the number of unique words / total number of words. Suppose we have the text: “of the people by the people for  the people”.
We initially define a variable, factor count, to value 0.
Then, we evaluate TTR sequentially 

|words string| factor computation|
|---|---|
|“of” |1/1 = 1|
|“of the” |2 / 2 = 1|
|“of the people” | 3/3 = 1|
|“of the people by” |4/4 = 1|
|“of the people by the”| 4/5  = 0.8|
|“of the people by the people” |4 / 6 = 0.667|

Now when a value falls under a certain factor size chosen a priori (in the paper is set to 0.720), we add 1 to the factor count and we reset factor calculations. So we go on in the following way:

|words string| factor computation|
|---|---|
|“for” |1/1 = 1|
|“for the” |2/2 = 1|
|“for the people” |3/3 = 1|

When the text ends, usually we have some words left which have not reached the factor size of 0.720. For these last words, the factor size is calculated on the basis of how far the TTR value has progressed towards the designated default factor size of 0.720
When we have gone through all the text we compute MLD as number of words/factor count
The computation of MTLD is performed two times, once in left-to-right text order and once in right-to-left text order. The two results are then averaged. 



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


## An initial text comparison: victory speeches

In order to get a first taste of how the metrics work, we will analyze two famous victory speeches by Barack Obama and Donald Trump. The two speeches have one thing in common: they both shocked the world at their times. The former was pronunced in an historic moment of U.S. history, when the first afro-american president was elected. The latter rapresented the victory of one the most controversial candidate of the U.S. modern era, who a lot of people did not expect to win.
Barack Obama and Donald Trump deal with dialogue in two very different ways. What we want to show is how powerful the metrics are in order to detect this differences automatically. Here are the two extracts from the two speeches, on which we computed the metrics: 

<br><br>

> *If there is anyone out there who still doubts that America is a place where all things are possible; who still wonders if the dream of our founders is alive in our time; who still questions the power of our democracy, tonight is your answer.
It's the answer told by lines that stretched around schools and churches in numbers this nation has never seen; by people who waited three hours and four hours, many for the very first time in their lives, because they believed that this time must be different; that their voice could be that difference.
It's the answer spoken by young and old, rich and poor, Democrat and Republican, black, white, Latino, Asian, Native American, gay, straight, disabled and not disabled  Americans who sent a message to the world that we have never been a collection of red states and blue states; we are, and always will be, the United States of America.
<br><br> **Obama's Victory Speech** (2008)*

<br><br>

> *Thank you. Thank you very much, everybody. Sorry to keep you waiting. Complicated business. Complicated. Thank you very much.
I've just received a call from Secretary Clinton. She congratulated us. It's about us. On our victory, and I congratulated her and her family on a very, very hard-fought campaign.
I mean, she fought very hard. Hillary has worked very long and very hard over a long period of time, and we owe her a major debt of gratitude for her service to our country.
I mean that very sincerely. Now it is time for America to bind the wounds of division, have to get together. To all Republicans and Democrats and independents across this nation, I say it is time for us to come together as one united people.
It is time. I pledge to every citizen of our land that I will be President for all of Americans, and this is so important to me. For those who have chosen not to support me in the past, of which there were a few people, I'm reaching out to you for your guidance and your help so that we can work together and unify our great country.
<br><br> **Trump's Victory Speech** (2008)*


The following table summarizes the results for the different metrics:




| Metrics | Obama | Trump |
| --- | --- | --- |	
|Average sentence length (words) |52.67| 11.82|
| Average syllables per sentence |75.00| 17.59|
| Average syllables per word |1.42| 1.49|
| Flesch Reading Ease |32.90| 68.99|
| Flesch-Kincaid Grade |21.75| 6.57|
| Gunning Fog index |25.12| 10.10|
| Sentence Count |3| 17|
| Syllable Count |225| 299 |
|Syllables per 100 words| 142.41| 148.76|
|Type/token ratio| 0.63| 0.54|
|Words with more than 2 syllables| 16| 27|
|Words with more than 2 syllables - Percentage| 10.13| 13.43|


We can see that a lot of metrics are very different. The average sentence length is much longer for Obama. Moreover, all of the three readability metrics agree on the fact that the English level of Obama’s speech is more advanced (The Flesch Reading Ease is lower, while the Flesch-Kincaid Grade and the Gunning Fog index are higher). 
The sentence count difference is also quite stark: Obama used three sentences, while Trump used 17. However Trump used more syllables overall.  
Also, Obama has a higher type to token ratio, so that means that he used a higher proportion of unique words than Trump. 
Overall, these results show that the metrics are capable of automatically detecting the lexical differences between the two texts in an automated way.


# Let's start our investigation...
We are interested into understanding whether there is any significant difference in any of the metrics we defined across the last four presidential candidates, Joe Biden, Donald Trump, Hillary Clinton and Barack Obama. We start by analyzing the number of unique words every 100, 200, 500, 1000, 2000, 5000 and 10000 words for each of the subjects. The number of quotations used is 100000 for each candidate.


{% include freq_words.html %}

Miss Clinton has a mean number of unique words statitically larger than Donald Trump, except for when we consider a very large number of words. Instead, such metric is statistically not different between Trump and Biden. Instead, Obama always outperforms the others in terms of number of unique words.


It may be interesting to see which are the most commonly used words for these four politicians. To do so we use the cloud of words graphs.

<p align="center">
  	<img img src="https://i.postimg.cc/9X1Sh254/cloud.png">
</p>


We can notice that there are some words in common for each of them, such as "people", "president" or "country", while some others are not used by them all, for example "women" used frequently by Hillary Clinton, or "China", "border", "wall" used by Donald Trump.

Now we want to dig deeper into the most commonly used words. In particular, thanks to the word frequency dataset and the level_score funciton previously defined, we want to assess the distribution of "academic" domain words against "spoken" domain ones, among the most commonly used words.

<p align="center">
  	<img img src="https://i.postimg.cc/YqRPP1Ng/academic-spoken.png">
</p>

We now move to interactive bar charts to better show what happens.

{% include academic_words.html %}



{% include spoken_words.html %}


Finally, we use the metrics computed with the API.

{% include api_important.html %}


# Aggregate comparisons



## Democrats vs Republicans

## House vs Senate

## Grouped by age of birth

## Grouped by congress 

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







<iframe src="https://prova-robi-cera.herokuapp.com" style=" width: 800px; height: 800px;  overflow: hidden;" scrolling="no"></iframe>


# Grafici artu
{% include graph_age_flesh_ease.html %}
{% include graph_chamber_flesh_ease.html %}
{% include graph_chamber_flesh_grade.html %}
{% include graph_chamber_gunning_fox.html %}



