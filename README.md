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


## The Bechdel test analysed among countries
As the world progresses, so does the lens through which we view gender representation. A historical analysis of cinematic trends shows a shift towards more inclusive and complex characterizations of women. Films that score high on newer metrics often resonate with contemporary societal values, achieving critical acclaim and commercial success. Intriguingly, these trends also vary geographically, with noticeable differences in countries based on their GII scores.

# Introducing new metrics
We now want to also look at other metrics to measure women's representation in cinema. First we look into a metric introduced recently in 2020, before proposing some of our own metrics.

## Female cast ratio
As we have seen up until now, the Bechdel test has some pretty significant limitations. Therefore we wanted to look at other metrics. The first metric, the female cast ratio, introduced by Yang et al. in 2020 seems to be a first candidate to look into.   
![Bechdel and female cast ratio](https://github.com/Matthijsscheerder/PandamoniumWebsite/blob/master/BechdelFemaleCastRatio.png?raw=true)

## Gender density
Still, we are not really satisfied by the female cast ratio. If anything we think we can design some other metric that could better indicate women's representation in films. The female cast ratio only says something about the ratio of women to men, not their prominence. What sets the the Bechdel test apart from the female cast ratio is that it does require to examine the actual interaction of the actresses with actors. This does require watching the movie or reading the script however, rather time consuming efforts. We propose the metric of gender density, using natural language processing on the movie summaries we want to determine the ratio of female pronouns to male pronouns.
The proposed metric uses thus the following relation:

$$\frac{number_{female\_characters}}{number_{female\_characters} + number_{male\_characters}}$$



## Actor mention score

![Bechdel and actor mention](https://github.com/Matthijsscheerder/PandamoniumWebsite/blob/master/BechdelActorMention.png?raw=true)


<iframe src="https://github.com/Matthijsscheerder/PandamoniumWebsite/master/polarities.html" width="600" height="400"></iframe>
<iframe src="https://Matthijsscheerder.github.io/PandamoniumWebsite/polarities.html" width="600" height="600"></iframe>


## Sources
Luoying Yang, Zhou Xu, and Jiebo Luo. 2020. Measuring Female Representation and Impact in Films over Time. ACM/IMS Trans. Data Sci. 1, 4, Article 30 (November 2020), 14 pages. https://doi.org/10.1145/3411213






