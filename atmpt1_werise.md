---
title: "App to Map Tutorial Part 1"
output: html_notebook
---

<h1>App to Map Tutorial Part 1: Collecting Tweets using the REST API</h1>

In order to do a one-time collection of tweets, you will need to access Twitter's REST API.  The name of the  R package that you have to download and load in order to access the REST API is the <a href = "https://cran.r-project.org/web/packages/twitteR/twitteR.pdf">TwitteR</a> package created by Jeff Gentry. You will also have to create a Twitter app in order to access the REST API. If you haven't already made one, go to <a href = "apps.twitter.com">apps.twitter.com</a> and create an app. You will need the Consumer Key (API Key), Consumer Secret (API Secret), Access Token, and Access Token Secret.

<h3>Tutorial Objectives:</h3>

<i>1. To do a one-time collection of tweets based on user-defined search terms.</i>
<i>2. To save the tweets in a .csv file.</i>


<h3>Instructions</h3>

<b>1. Open up R Studio and go to File > New File > R Script. 

<b>2. Install and load the twitteR package.</b>
```{r, chunk-one, echo=TRUE, eval=FALSE}
install.packages("twitteR")
library(twitteR)

```

<b>3. Next, you will need to enter your API key, API secret, token, and token secret.</b>
```{r, chunk-two, echo=TRUE, eval=FALSE}
api_key <- '' #in the quotes, put your API key 
api_secret <- '' #in the quotes, put your API secret 
token <- '' #in the quotes, put your token 
token_secret <- '' #in the quotes, put your token secret

```

<b>4. You will need to connect to Twitter to access the REST API.</b>
```{r, chunk-three, echo = TRUE, eval=FALSE}
setup_twitter_oauth(api_key, api_secret, token, token_secret)

```

<b>5. Time to do a Twitter search! Let's do a Twitter search of tweets about national parks:
```{r, chunk-four, echo = TRUE, eval= FALSE}
tweets <- searchTwitter('@YellowstoneNPS OR #YellowstoneNationalPark OR Yellowstone National Park OR
 @GrandCanyonNPS OR #GrandCanyon OR Grand Canyon OR @ShenandoahNPS OR ShenandoahNationalPark
 OR Shenandoah National Park', n = 200, lang = 'en')
```
<i>This code is simply saying to search for tweets which contain the hashtags, twitter handles, and names of these national parks.</i> <font color = "blue", face = "Courier">(n = 200)</font><i>in English</i><font color = "blue", face = "Courier">(lang = “en”)</font>.

<b>8. After you have done your Twitter search, you want to save your results in a data frame.</b>
```{r, chunk-five, echo = TRUE, eval = FALSE}
tweets.df <-twListToDF(tweets)
```

<b>9. Your search results can be transferred from a data frame to a csv format so you can view in Excel.</b>
```{r, chunk-six, echo = TRUE, eval= FALSE}
write.csv(tweets.df, 'C:\Users\YourName\Documents\ApptoMap\tweets.csv') #example file extension. Add your own!
```

<b>10. Click "Run" <b>.




