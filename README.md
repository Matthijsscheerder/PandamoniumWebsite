# Beyond the Bechdel Test: A New Era of Measuring Women's Representation in Cinema
*By Pandamonium: Tiago Freitas, Deniz Kasap, Riza Arseven, Eren Saydar and Matthijs Scheerder*
![us crancking out work for the project](https://github.com/Matthijsscheerder/PandamoniumWebsite/raw/master/PandamoniumPanda.webp)


# Introduction
In a world where cinema is not just entertainment but a mirror to society, understanding the representation of women on screen is paramount. For the last decades, the Bechdel test has been a cornerstone in assessing this representation, yet its simplicity often overshadows its limitations. This narrative ventures beyond the Bechdel test, unveiling a new landscape of metrics that offer a richer, more nuanced view of women in cinema.

# The Bechdel test
## The Bechdel test explained
Before we can really assess the strengths and weaknesses of the Bechdel we need to define for the reader what it exactly entails. Conceived by Alison Bechdel in 1985, the Bechdel Test asks a straightforward question: does a movie feature at least two women who talk to each other about something besides a man? More specifically the test consists of the following three conditions:

1. The movie has to have at least two women in it,
2. who talk to each other,
3. about something other than a man

This thus means that the Bechdel test can be considered as a discrete scoring from 0 (complete fail) to 3 (pass). 

## The Bechdel test analysed
Given the advent of spoken cinema in the early 1930s, one might assume that women's representation in film would have progressed alongside growing gender equality and women's involvement in society at large, potentially resulting in higher Bechdel test scores. However, we need to investigate whether this assumption holds true or if it is merely a perception. The following analysis aims to address this question directly. 

![image](https://github.com/Matthijsscheerder/PandamoniumWebsite/assets/71981923/4ffb13bc-e65e-4a9c-abcc-e3bf64da226b)


# Introducing new metrics, why is it costly? Can we do better?
In our bechdel dataset that we scraped from the web, we have a categorical score between 0 and 3 for each movie indicating how many tests a single movie passes. We then take the intersection between the CMU movie data and the created bechdel dataset.

Although it seems like a good feature for gender representation, getting the data might be very costly!! This is primarily because it involves processing the entire movie script either by humans or complex natural language processing models. In this project, we will introduce new metrics that can be gotten just from the movie summaries, therefore reducing the dramatically the complexity of the latter task. We will then try to see the possible correlations between these metrics and the bechdel score determining the importance of each metric. By doing this, we aim to come up with a new simpler to get formula that may be a better gender representer by combining our new metrics. We will finally observe these new metrics' evolution with each country
We now want to also look at other metrics to measure women's representation in cinema. First we look into a metric introduced recently in 2020, before proposing some of our own metrics.

## Female cast ratio
As we have seen up until now, the Bechdel test has some pretty significant limitations. Therefore we wanted to look at other metrics. The first metric, the female cast ratio, introduced by Yang et al. in 2020 seems to be a first candidate to look into.

Looking at the distribution below, the standard toddler would see a linear pattern with increasing female cast ratio. Therefore in first glance, we expect a correlation but that's to see for later.

![Bechdel and female cast ratio](https://github.com/Matthijsscheerder/PandamoniumWebsite/blob/master/BechdelFemaleCastRatio.png?raw=true)

### Are females casted less???!!
In this plot, we see the evolution by years the female cast ratio and the bechdel scores. It is apparent that the female cast ratio is much lower than 0.5 meaning there is less casted females than males. To confirm the latter, we apply an independent t test. The results show that the probability of observing a female cast ratio is significantly different (lower in our case) than 0.5. There is indeed more males casted than females :(

<iframe src="https://Matthijsscheerder.github.io/PandamoniumWebsite/female_cast_ratio_first_plot.html" width="800" height="600"></iframe>

Here the data looks normally distributed. However we observe an apparent correlation between the female cast ratio and the bechdel score mean for each bin. This makes sense as well, when more females are casted, they tend to conversate more to each other hence having a higher bechdel score!

<iframe src="https://Matthijsscheerder.github.io/PandamoniumWebsite/female_cast_ratio.html" width="800" height="600"></iframe>

Now its time for the other metric to shine. We do the Ordinary Least Squares (OLS) linear regression between the bechdel score taking it as a dependent variable and taking the female cast ratio as an independent variable. We observe an adjusted R squared value of 0.204 which is alright and the probability of observing the regression coefficient is significant for a p value of p=0.01.

To better understand the correlation we employ the spearman correlation and we get a significant correlation with a coefficient of 0.46 which is really not bad!!!.
##### It turns out that the simple standard toddler is right!!!
![Toddler is right](https://github.com/Matthijsscheerder/PandamoniumWebsite/raw/master/Toddler.webp)
## Actor mention score
We calculate the following simple ratio:
$$\frac{number_{female\_characters}}{number_{female\_characters} + number_{male\_characters}}$$

For each unique movie, we access its relative character dataframe and the summary provided. By comparing every name in the summary, we get their genders and calculate the abovementioned score.

In the barplot below, the simple toddler would again see that with increasing actor mention scores, the bechdel score also improves. We will try to see if that correlation is significant in the later steps as well. The toddler is a toddler afterall.

![Bechdel and actor mention](https://github.com/Matthijsscheerder/PandamoniumWebsite/blob/master/BechdelActorMention.png?raw=true)

Furthering our analysis, we now plot the distribution again the bechdel score by taking the mean bechdel score of each bin of the actor mention score. Now the correlation is now much more visible and understandable. We have lower bechdel scores for cases where female characters were less mentioned and higher bechdel scores when they are mentioned more.
<iframe src="https://Matthijsscheerder.github.io/PandamoniumWebsite/actor_mention.html" width="800" height="600"></iframe>


<iframe src="https://Matthijsscheerder.github.io/PandamoniumWebsite/polarities.html" width="600" height="600"></iframe>

## Gender density
Still, we are not really satisfied by the female cast ratio. If anything we think we can design some other metric that could better indicate women's representation in films. The female cast ratio only says something about the ratio of women to men, not their prominence. What sets the the Bechdel test apart from the female cast ratio is that it does require to examine the actual interaction of the actresses with actors. This does require watching the movie or reading the script however, rather time consuming efforts. We propose the metric of gender density, using natural language processing on the movie summaries we want to determine the ratio of female pronouns to male pronouns.
The proposed metric uses thus the following relation:

$$\frac{number_{female\_characters}}{number_{female\_characters} + number_{male\_characters}}$$

<iframe src="https://Matthijsscheerder.github.io/PandamoniumWebsite/gender_densities.html" width="800" height="600"></iframe>

## The Bechdel test analysed among countries
As the world progresses, so does the lens through which we view gender representation. A historical analysis of cinematic trends shows a shift towards more inclusive and complex characterizations of women. Films that score high on newer metrics often resonate with contemporary societal values, achieving critical acclaim and commercial success. Intriguingly, these trends also vary geographically, with noticeable differences in countries based on their GII scores.

# Predict Bechdel score by random forest
![random forest](https://github.com/Matthijsscheerder/PandamoniumWebsite/raw/master/RandomForest.webp)




## Sources
Luoying Yang, Zhou Xu, and Jiebo Luo. 2020. Measuring Female Representation and Impact in Films over Time. ACM/IMS Trans. Data Sci. 1, 4, Article 30 (November 2020), 14 pages. https://doi.org/10.1145/3411213






