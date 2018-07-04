---
layout: post
title:  "Sentiment Analysis 'AMLO' en twitter"
date:   2018-07-03

categories: ML

tags:
  - Machine Learning
  - Python
  - twitter
  - tweepy
  - textblob
---

## Aplicando "Sentiment Analysis" en Twitter a AMLO

Como resultado de la pasada elección del 1ro de Julio 2018 en México, se dió a conocer al nuevo Presidente electro
Andrés Manuel Lopez Obrador (AMLO).
Tomando este suceso como ejemplo me di a la tarea de revisar las opiniones en twitter del nuevo presidente de México.
 

## Herramientas utilizadas
* [tweepy](http://www.tweepy.org/)
* [TextBlob](https://textblob.readthedocs.io/en/dev/)
* [Siraj Repo](https://github.com/llSourcell/twitter_sentiment_challenge)

El análisis se llevo acabo con tweets en inglés, la libreria TextBlob soporta solo el idioma inglés,
en su versión más reciente tiene soporte para la traducción de otro idioma al inglés, pero de ultimo momento dejó de funcionar 
la traducción, así que me tuve que limitar a revisar solo tweets en inglés.

<!-- more -->

## El codigo del programa
```python
from textblob import TextBlob
import nltk
import tweepy

consumer_key = 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXx'
consumer_secret = 'XXXXXXXXXXXXXXXXXXXXXXXXXXXX'
access_token = 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'
access_token_secret = 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'

auth = tweepy.OAuthHandler(consumer_key,consumer_secret)
auth.set_access_token(access_token,access_token_secret)
api = tweepy.API(auth)

searched_tweets = []
last_id = -1
while len(searched_tweets) < 10000:
  counting = 1000 - len(searched_tweets)
  new_tweets = api.search('AMLO',count=count, max_id=str(last_id - 1),lang='en')
  if not new_tweets:
    break
  searched_tweets.extend(new_tweets)
  last_id = new_tweets[-1].id

printing = 100 
for tweets in searched_tweets:
  if printing <= 0:
    break;
  printing = printing -1
  nword = TextBlob(tweets.text)
  ##if nword.detect_language() != 'en':
    ##nword = nword.translate(to='en')
  print(nword)

mean = 0
count = 0
for tweets in searched_tweets:
  word = TextBlob(tweets.text)
  ##if word.detect_language() != 'en':
   ## word = word.translate(to='en')

  #print(word.sentiment)
  mean = mean + word.sentiment.polarity
  count = count + 1
mean = mean/count
print("\nAnalysis based on: ",count," tweets")
print("Sentiment Mean value:  ",mean)

```


> Se analizan 10,000 tweets, el código solo imprime 100 por cuestiones de espacio.

## Los resultados:
* Se analizaron:  10,093  tweets
* El valor promedio de sentimiento fue: 0.1291160151209013

Donde el valor del sentimiento está entre -1 y 1. Valores positivos significan opiniones positivas y los valores negativos
corresponden a opiniones negativas.

* [Link al repo](https://github.com/forcesk/ML-ForFun/tree/master/AMLO-twitter)
* [Para ver los resultados AQUI.](https://github.com/forcesk/ML-ForFun/blob/master/AMLO-twitter/AMLO_TwitterSentimentAnalysis.ipynb)

![GraphAmlo](https://github.com/forcesk/forcesk.github.io/blob/master/public/EC/GraphAMLO.png)

