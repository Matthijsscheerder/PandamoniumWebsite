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

Now its time for this metric to shine (hopefully). We first do a linear regression using Ordinary Least squares (OLS) between the bechdel score taking it as a dependent variable and taking the actor mention score as an independent variable. We observe an adjusted R squared value of 0.112 which might not seem very high but the probability of observing the regression coefficient is significant for a p value of p=0.01

To better understand the correlation we employ the spearman correlation to that also that is not limited by linear correlations. For the latter we get a correlation coefficient of 0.35 which doesn't look bad

From these analysis we assume that this might be a good metric to predict the bechdel score.

## Gender density
Still, we are not really satisfied by the female cast ratio. If anything we think we can design some other metric that could better indicate women's representation in films. The female cast ratio only says something about the ratio of women to men, not their prominence. What sets the the Bechdel test apart from the female cast ratio is that it does require to examine the actual interaction of the actresses with actors. This does require watching the movie or reading the script however, rather time consuming efforts. We propose the metric of gender density, using natural language processing on the movie summaries we want to determine the ratio of female pronouns to male pronouns.
The proposed metric uses thus the following relation:

$$\frac{number_{female\_characters}}{number_{female\_characters} + number_{male\_characters}}$$

Since the standard simple toddler is always right, we won't bother even judging their hypothesis so we directly pass to the next part.

## What!!!!? Films really mention more males???
Here we first plot the distribution of the pronoun density versus the bechdel score. We can immediately see that a great number of films in the first bin corresponding to a she/her mention of a very low level to 0. When plotting this against the average bechdel test scores for each mean, we observe a visual correlation, meaning for low mentions of females the bechdel score is lower and for mention of females the bechdel score is higher. This result is consistent to what we saw in the beginning of this website with the evolution of the female cast ratio over the years. Finally we plot the individual occurences of each pronoun in each plot summary. We then conduct an independent t test telling us that the probability of observing male pronouns versus females are considerably different at a significance level of p=0.01
<iframe src="https://Matthijsscheerder.github.io/PandamoniumWebsite/gender_densities.html" width="800" height="600"></iframe>

## Sentiments Analyis


In this section, we obtain the mood of the summary provided, by using the Roberta model, trained on Twitter, and running the model with the tokenized summary. With this method, we do not need the  preprocessing of our summary, such as stop-word-removal, etc. In return, we get the probabilities of the following three moods:
1. Negative
2. Neutral
3. Positive

#### Oh man! That movie was really sentimental! Or is it?

When we plot the sentiment analysis results for all the movies in our initial cmu dataset, we clearly see that neutral movies make the substantial majority with the negative movies coming in for the second place and the positive movies for the last. Although the difference is visually very visible, we nevertheless perform a t test. As a result we see that the probability of having neutral scores are statistically different than observing a positive or a negative score at a significance level of p=0.01 
<iframe src="https://Matthijsscheerder.github.io/PandamoniumWebsite/sentiments.html" width="800" height="600"></iframe>

#### Roberta vs Blob Polarities

One interesting thing about our calculated roberta metric is that it doesn't account for the neutral so it tends to jiggle around a lot. Therefore we used the blob model which is a better representation of polarity since the resulting normal distribution is around 0 which makes sense since the Roberta model predicted that the majority of the movies had higher neutral scores. As seen in the interactive plot below, the roberta polarity tends to be centered around a negative value. Given our hypothesis that the blob model might more robust.
<iframe src="https://Matthijsscheerder.github.io/PandamoniumWebsite/polarities.html" width="600" height="600"></iframe>

### The light at the end of the tunnel is seen, lets put all the correlation coefficients together!
Here we visualize all the spearman correlation coefficients together even between our own metrics to understand the underlying the correlations better, for the correlation with the bechdel score we jsut look at the topmost row.


# Predict Bechdel score by random forest
![random forest](https://github.com/Matthijsscheerder/PandamoniumWebsite/raw/master/RandomForest.webp)
## Random Forest for Bechdel Score Classification

To further integrate our new features and try to develop an estimator framework to estimate Bechdel score. The reason we opt for random forest is that it can be utilized as a threshold based classifier since our new features consist of thresholdable features, such as setting a threshold for female cast ratio. Also, another important aspect is that when constructing the forest with trees, the features as ranked based on their importance, from a bottom-to-top fashion. This can be further used as a feature selection method.

$$Test Accuracy: 0.605$$

Although this test accuracy looks promising, it may be a little misleading, since the label distribution is not equal and thus majority class is more dominany. To get a better idea of our classifier, we can plot confusion matrix and get macro/micro average of our prediction metrics:

## Unequal Classes! What about undersampling?

Before inspecting and analysing our preliminary results, first, let's try to carry out the same experiment with a different approach. Since the class distribution is not equal and bechdel score = 3 is the majority class, we can try to undersample the minority class, which is bechdel_score = 0. From each label, we can try to sample 300 samples each, in total 1200 samples, before the training and test split. This way, with the test accuracy and confusion matrix, we can interpret our results more easily and safely.



Considering the model with no information gained, we would consider %25 accuracy, whereas with the random forest, we get %46 test accuracy. This can be considering promising as well, compared to the %25 accuracy. Yet, this would not considered sufficient for a robust classifier. With the undersampled version, we eliminate the differentiation for precision, recall and F1 score. However, this not being a binary classification task, it would require more in-depth analysis for the individual classes. Looking for the confusion matrix, we release a significant difference between the accuracies of label 0 & 3 versus 1 & 2. Considering the definition of the Bechdel test, it is easy to classify score-0, cast not containing 2 female actresses. This can be deducted from female cast ratio.

We can visualize the how much each feature contributes to the estimator within the same function. We can rank and visualize feature importances in a bar plot. The random forest ranks the impurity of each features. As we can see from the figure above, from the trained random forest, we can see that the most importance is put on female cast ratio, and the second is gender pronoun density. The third place goes to polarity blob. The remaining seems to have more or less the same importance.

## Opting for Binary Bechdel Test

We observe that for the cases where the movie passes 1 or 2 tests, it is hard to classify. For this reason, we may opt to look from a more rigid perspective and binarize the output labels as "Passed", or "Failed". The same analysis is carried out with the binary bechdel version.

## Binary Bechdel with Undersampling
Although this does not provide us very crucial information, we can still try to get some information on the nature of the Bechdel test. We can see that our test accuracy raises to %71, from %50 with the random guessing case. Comparing the feature importance scores with the complete Bechdel classes, we can see that the first two features are still the same. The actor mention score seems to gain more importance this time. The rest does not provide us crucial information.

## Final Recipe for Bechdel Classifier:

For the final recipe, we can eliminate the intermediate features such as positive sentiment probability, negative sentiment probability, etc. 

The final features kept are the folowings:
* Actor Mention Score
* Female Cast Ratio
* Gender Pronoun Density
* Polarity Blob

Using these features, we can train our classifier for the one last time:

We can see that we still get the same test accuracy but less features for the desired task.



## Sources
Luoying Yang, Zhou Xu, and Jiebo Luo. 2020. Measuring Female Representation and Impact in Films over Time. ACM/IMS Trans. Data Sci. 1, 4, Article 30 (November 2020), 14 pages. https://doi.org/10.1145/3411213






