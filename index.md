	
<p align="center">
	<a href="https://postimg.cc/dL9WhCRB">
  		<img img src="https://i.postimg.cc/jdpBkQLG/ada-group-project-spaghetti-carbonada.png">
	</a>
</p>






<!-- [![ada-group-project-spaghetti-carbonada.png](https://i.postimg.cc/jdpBkQLG/ada-group-project-spaghetti-carbonada.png)](https://postimg.cc/dL9WhCRB) -->

# About QuoteBank
Quotebank is an open corpus of 178 million quotations extracted from 162 million English news articles published in the years between 2008 and 2020. Each quotation is extracted and attributed to the speakers who uttered them thanks to the Quobert model, which is language and corpus-agnostic.  Both Quotebank and Quobert are publicly available [here](https://doi.org/10.5281/zenodo.42773118)








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


Our supposition is that there is a difference in the linguistic usage between the two sides of the political spectrum. We suspect this difference to be found in the number of different words while speaking (variety of lexicon), different length of phrases, number of repetitions and different structuring of the phrases (number of subordinate vs coordinate phrases).
We plan to investigate whether this difference is present in the US political landscape. In other words, is the language that Republicans use much different than those that Democrats use. 


# Initial exploration: what data do we have?

We can notice the politicians taken into account are balanced between Democrats and Republicans. Clearly there are many more Congressmen than Senators as it's natural given the House of Representatives is composed by 435 members, while the Senate includes only 100 individuals. Age-wise we can see that the majority of US Representatives included in our metrics were born in the 50s and 60s, and only 115 out of 539 considered were born in the 70s or later. Naturally by the way each congressman is assigned to a number of congress the 114th is the most represented. 58 is the number of politicians considered who were first elected in 2016 (first mandate during the 115th Congress), while this number increases to 77 for the midterm elections of 2018. (For the sunburst graphs, click on the charts to visualize the details!)

### Proportion of politicians in each state
{% include pie_state.html %} 
### Proportion of politicians by party, chamber and birth date (40s = born in the 1940s)
{% include sunburst_1.html %}
### Proportion of politicians by chamber and birth date
{% include sunburst_2.html %}
### Proportion of politicians by chamber, party and birth date
{% include sunburst_3.html %}

We can notice various things: 
1. From the first graph we notice that the percentage of members of each party belonging to the House of Representatives is mostly consistent between Democrats and Republicans 224 to 218, while Republicans count 56 senators v. 41 for the Dem in our dataset. 
Democrats in both chambers seem to have a younger range of representatives. for example those born after the 60s represent the most popoulous group at the House of Representatives among Democrats, while they only figure on 3rd place for Republicans (57 v. 49)
2. The Senate is composed (naturally given the Corsus Honorum strongly felt in the US) by older people. In particular people born in the 40s or earlier represent just 17% in the House of Representatives versus one third of the Senate. 
3. In this last one we can see even more clearly what said for the first suburst graph. Especially if we select by clicking on the particular sections of the circle Democrats>House and compare to Republicans>House

# How do we measure?
The question is: how can we measure the lexical level of a person from their quotes? Basically we aggregated many quotes (2000 on average!) for each politician, extracted randomly if they had more than that, in order to create a text. Then, we used some metrics to evaluate the text. To conduct our analysis on the politicians' words we will use six different metrics.

The metrics we used are the following:

* Flesch reading-ease
* Flesch-Kincaid Grade
* Gunning Fog Index
* MTLD
* VOC-d
* Number of unique words in a certain word window

The first three metrics estimate very similar things, using them all together allowed us to build a more robust measure. 

### Flesch reading-ease
The Flesch reading-ease index is a measure for the “readability” of a text. The higher the score, the “simpler” the text, and the easier it is to read. (Hence, in our analysis, a high score indicates that the politician has a very simple language. It can be correlated either with a lack of education or with a willingness to be understood by everybody!).
<br>
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

<br>
The formula to compute the is Flesch reading-ease: 

<br><br>

<p align="center">
	<a href="https://www.codecogs.com/eqnedit.php?latex=206.835&space;-&space;1.015&space;\Bigg(\frac{total&space;\;&space;words}{total&space;\;&space;sentences}\Bigg)&space;-&space;84.6\Bigg(\frac{total&space;\;&space;syllables}{total&space;\;&space;words}\Bigg)" target="_blank">
		<img src="https://latex.codecogs.com/gif.latex?206.835&space;-&space;1.015&space;\Bigg(\frac{total&space;\;&space;words}{total&space;\;&space;sentences}\Bigg)&space;-&space;84.6\Bigg(\frac{total&space;\;&space;syllables}{total&space;\;&space;words}\Bigg)" title="206.835 - 1.015 \Bigg(\frac{total \; words}{total \; sentences}\Bigg) - 84.6\Bigg(\frac{total \; syllables}{total \; words}\Bigg)" />
	</a>
</p>



### Flesch-Kincaid Grade
The Flesch-Kincaid Grade is a modification of the Flesch Reading Ease index, and has a nice straightforward interpretation: its output represents roughly the number of years of education required to understand the text provided. The formula for the grade is the following:

<br><br>

<p align="center">
	<a href="https://www.codecogs.com/eqnedit.php?latex=0.39&space;\Bigg(\frac{total&space;\;&space;words}{total&space;\;&space;sentences}\Bigg)&space;&plus;&space;11.8&space;\Bigg(\frac{total&space;\;&space;syllables}{total&space;\;&space;words}\Bigg)&space;-15.59" target="_blank">
		<img src="https://latex.codecogs.com/gif.latex?0.39&space;\Bigg(\frac{total&space;\;&space;words}{total&space;\;&space;sentences}\Bigg)&space;&plus;&space;11.8&space;\Bigg(\frac{total&space;\;&space;syllables}{total&space;\;&space;words}\Bigg)&space;-15.59" title="0.39 \Bigg(\frac{total \; words}{total \; sentences}\Bigg) + 11.8 \Bigg(\frac{total \; syllables}{total \; words}\Bigg) -15.59" />
	</a>
</p>


### Gunning Fog Index
The Gunning Fog index is yet another readability score. Very closely to the Flesch-Kincaid Grade, it tries to make an estimate of the number of years of formal education needed to understand the text when reading it for the first time. The formula for the Gunning fox index is the following, where “complex words” are defined as the words with 3 or more syllables. 


<br><br>

<p align="center">
	<a href="https://www.codecogs.com/eqnedit.php?latex=0.4\Bigg[\Bigg(\frac{words}{sentences}\Bigg)&plus;100\Bigg(\frac{complex&space;\;&space;words}{words}\Bigg)\Bigg]" target="_blank">
		<img src="https://latex.codecogs.com/gif.latex?0.4\Bigg[\Bigg(\frac{words}{sentences}\Bigg)&plus;100\Bigg(\frac{complex&space;\;&space;words}{words}\Bigg)\Bigg]" title="0.4\Bigg[\Bigg(\frac{words}{sentences}\Bigg)+100\Bigg(\frac{complex \; words}{words}\Bigg)\Bigg]" />
	</a>
</p>

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

Now when a value falls under a certain factor size chosen a priori (in [this](https://pubmed.ncbi.nlm.nih.gov/20479170/) famous paper it is set to 0.720), we add 1 to the factor count and we reset factor calculations. So we go on in the following way:

|words string| factor computation|
|---|---|
|“for” |1/1 = 1|
|“for the” |2/2 = 1|
|“for the people” |3/3 = 1|

When the text ends, usually we have some words left which have not reached the factor size of 0.720. For these last words, the factor size is calculated on the basis of how far the TTR value has progressed towards the designated default factor size of 0.720
When we have gone through all the text we compute MLD as number of words/factor count
The computation of MTLD is performed two times, once in left-to-right text order and once in right-to-left text order. The two results are then averaged. 



#### VOC-d
In order to calculate the VOC-d metric, the following steps are taken:
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
The scope of our analysis is to apply a quantitative approach to the analysis of lexical levels of various prominent U.S. politicians. In particular we firstly applied the above-mentioned metrics to understand whether there is any significant difference in the lexical level of the last four presidential candidates, Joe Biden, Donald Trump, Hillary Clinton and Barack Obama. We start by analyzing the number of unique words every 100, 200, 500, 1000, 2000, 5000 and 10000 words for each of the subjects. The number of quotations used is 5000 for each candidate.

{% include freq_words.html %}

Miss Clinton has a mean number of unique words statitically larger than Donald Trump, except for when we consider a very large number of words. Instead, such metric is statistically not different between Trump and Biden. Instead, Obama always outperforms the others in terms of number of unique words.


It may be interesting to see which are the most commonly used words for these four politicians. To do so we use the cloud of words graphs.

<p align="center">
  	<img img src="https://i.postimg.cc/9X1Sh254/cloud.png">
</p>


We can notice that there are some words in common for each of them, such as "people", "president" or "country", while some others are not used by them all, for example "women" used frequently by Hillary Clinton, or "China", "border", "wall" used by Donald Trump.

Now we want to dig deeper into the most commonly used words. In particular, thanks to the word frequency dataset and the level_score function previously defined, we want to assess the distribution of "academic" domain words against "spoken" domain ones, among the most commonly used words. The graphs below show for each of the four personalities considered the number of words belonging to an academic or spoken domain included in the top n most used words by each.

<p align="center">
  	<img img src="https://i.postimg.cc/YqRPP1Ng/academic-spoken.png">
</p>

We now move to interactive bar charts to better show what happens.

{% include academic_words.html %}

Also here, Obama is the one with the highest average number of academic words in every case. Also we notice that from considering the most used 100 words and above, the relative frequency among the politicians seems to converge in this order of frequency of academic words: Obama, Biden, Clinton, Trump.

{% include spoken_words.html %}
Also considering spoken domain words, apart from the first case with the top 25 words, Obama is clearly the one farthest from the others, with a lower frequency of spoken domain words. Joe Biden is quite steadily the one with the highest average number of spoken language words, while for Clinton and Trump after having performed a Wald test to assess when their results are statistically different, we found that they are always statistically not different a part when considering the 200 and 250 most used words, for which the average for Trump is higher.

DISCLAIMER: the dataset we used to label the words either "academic" or "spoken" language, contains also many other tags. It is not true that a word is either academic or spoken. Moreover, the dataset contains 5000 words, so it may be that a word is not found in the dataset.


Finally, we compute also the following five metrics. Flesch Reading Ease, Flesch Kincaid Grade, Gunning Fog Index, the MTLD and the VOC-d.

{% include api_important.html %}

The results coming from the first three metrics provided by the API confirm what we guessed from the words frequency and most used words: Barack Obama is the one with the most complex communication style and the widest words spectrum, while Donald Trump and Joe Biden are those with the worst results. Regarding the MTLD and VOCD metrics there is a high variability depending on the subset of quotations analyzed, showing the little robustness of the metric used on such data (random quotations aggregated to form texts), therefore they do not show reliable results. For more accurate results regarding the lexical spectrum refer to the unique words graphs.

# Aggregate comparisons


## Democrats vs Republicans

We now want to shift our attention to comparing groups of politicians, which was essentially the goal of this whole project. We would like to investigate whether the trends seen in the individual comparisons we draw in the previous section can be extended to more general tendencies. We will compare aggregate measures of Senators and Congressmen (with quotes included inside Quotebank) grouped by party, branch of Congress, age, state of election and other...
We start by analyzing the distribution of `Flesh_Reading_Ease` scores across the two major parties.

{% include hist_party.html %}

We can notice that the distribution of the scores are shifted to the right for Republicans, which can be interpreted (using the definition of the Flesh Reading Ease Score) by saying that Republicans in general use more simple sentences constructions. To verify the soundness of such hypothesis we ran a t-test.

With a p-value of 0.0003 we can safely reject the null-hypothesis stating there is no statistical difference between the Flesh Reading Ease scores of Republicans and Democrats. We would like to know if the other two metric are consistent, to do that we run other two t-test which confirm the same hypothesis on Flesch-Kincaid Grade and Gunning Fog Index scores; in general Democrats appear to use more structured phrase constructions.

## House vs Senate

Now that we have confirmed that there is indeed a significant difference between Republicans and Democrats we asked ourselves whether there other significant differences besides the one between parties. 

To do so we first need to create the necessary datasets to analyse the data aggregated in different ways, which we do in the cell below.

In particular we want to analyse possible differences between the two branches of the Congress, between age groups and for first appearance in Congress. Given we rejected the null hypothesis stating that there is no difference in the lexic of Democrats and Republicans, in all analyses we will take into account the difference between Republicans and Democrats and therefore analyse possible differences only across individuals of the same party. 
We start by analyzing possible differences between the two branches of Congress: Senate and House of Representatives. Here below we plot barcharts for the three readibility metrics.

{% include graph_chamber_flesh_ease.html %}
{% include graph_chamber_flesh_grade.html %}
{% include graph_chamber_gunning_fox.html %}

From the 3 graphs above we can see that the only difference remain between the two different parties while for all three measure of lexical level there is no difference between Senators and Representatives inside the same party.

As shown above and confirmed by our experiments on the following comparisons the three lexical metrics returned extremly consistent results, hence from now on we will only show the values from Flesh Reading Ease to avoid repeting ourselves.

## Is there a difference between age groups?

The next questions we asked ourselves was: is there any significant difference between age groups? To answer that we used the same approach as done with parliament branches and compared values for each age group splitted between Democrats and Republicans.

{% include graph_age_flesh_ease.html %}

Firs, from the graph above we can notice that Democrats keep recording lower Flesh Reading Ease values in all age groups, confirming this is not a case of Simpson's Paradox. But what we are more intrested in analysing possible trends among age groups for each party. So we replot the same graph now grouping bars by party, such graph is shown below:

{% include graph_age_flesh_ease_2.html %}

From this second graph we can notice a steady trend among Republicans. It seems that younger Republican congressmen progressively adopted a more simple lexic. Even though differences seem really small and looking at confidence intervals we could not clearly reject null hypothesis of averages being identical. 
The other thing we noticed from the previous graph is that Democrats born in 1970 or later score statistically significant higher Flesh Reading Ease scores that older colleagues. While all other Democrats across the remaining age groups seem to score consistently.

## Is there a difference between the Old Guard and Newcomers?

Next questions we asked ourselves is: is there a statistically significant difference in lexical complexity for politicians who entered in Congress during recent elections? 
To reply to such question we plot the same graphs as above this time differentiating for the congress of first appearance.


{% include graph_congress_flesh_ease.html %}
{% include graph_congress_flesh_ease_2.html %}

From the two graphs above we can notice that the difference between Democrats and Republicans remain true for each sub group of politician who entered the congress in 2015, 2017 or 2019, corresponding respectively to the 114th, 115th and 116th congresses. 

In addition we can notice that the lexic chosen by politicians who more recently entered in congress is generally more simple, less refined. This can be seen both among Republicans as well as Democrats.

## Map

Finally, we asked ourselves if we could notice some significant differences for politicians elected in different US states. To do so we show an interactive map where we can visualize the aggregated values for each state of Flesh Reading Ease, Flesch Kincaid Grade and the number of unique words / 1000 words. 
You can play around with the map by selecting only one of the two major parties or the entire political specturm as well as selcting just one or both branches of Congress. 
Focusing on the aggregated Flesch Reading Ease scores we noticed a slight tendency of the Mid-West states to score lower than more populous costal states. 

<iframe src="https://prova-robi-cera.herokuapp.com" style=" width: 800px; height: 800px;  overflow: hidden;" scrolling="no"></iframe>

We also created a discrete score for each state for Flesch Reading Ease distinguishing between low and high average scores, setting the threshold as the average Flesch Reading Ease for Democrats. We plot these values in the map below.

{% map_discrete.html %}

If we compare the map we've just shown with the result of the 2016 presidential election we can draw an interesting parallel between the states where the candidates speak good english and those where Democrats have won. 

<p align="center">
	<a href="https://www.youtube.com/watch?v=phsU1vVHOQI">
  		<img width="600" height="400" alt="trump-youtube" src="https://i.postimg.cc/QVGYgbNz/Whats-App-Image-2021-12-17-at-23-52-15.jpg">
	</a>
</p>



### Hypothesis Testing

In this section, we check whether there is a significant difference in language within these 6 different groupings:

1. Democrats vs Republicans
2. House members vs Senate member
3. House Democrats vs House Republicans
4. Senate Democrats vs Sanate Republicans
5. House Democrats vs Senate Democrats
6. House Repubblicans vs Senate Republicans


All the three metrics agreed on the significance for all groupings. The results of the tests, run on the Notebook, are the following:

1. Democrats vs Republicans:                 **significant**
2. House members vs Senate member:              non-significant
3. House Democrats vs House Republicans:     **significant**
4. Senate Democrats vs Sanate Republicans:     non-significant
5. House Democrats vs Senate Democrats:         non-significant
6. House Repubblicans vs Senate Republicans:   non-significant
















