# BERT-Trump-vs-Biden-Classification
Binary Text Classification model implemented using BERT to classify whether a given text is from Trump or Biden.

## BERT
BERT is a Natural Language Processing technique developed by Google.The model was pre-trained on a large dataset to be able to perform Masked Language Modeling and Next Sentence Prediction. It can predict the next word given a sequence of words. Given two sentences, it can determine whether the second sentence follows the first sentence. [[Source]](https://yashuseth.blog/2019/06/12/bert-explained-faqs-understand-bert-working/)

Since BERT is pre-trained, implementing it for this binary text classification problem simply involved fine tuning it. 

## Data
* Model trained on 1076 Tweets from Joe Biden from 9/27/2019 to 2/2/2020 and 1045 Tweets from Donald Trump from 5/13/2020 to 7/26/2020
* Model tested on 500 Tweets from Joe Biden from  11/19/2019 to 2/2/2020 and 223 Tweets from Donald Trump from 4/24/2020 to 5/12/2020
* Tweets were scraped using [Tweepy](http://docs.tweepy.org/en/latest/#)

<img src="https://github.com/wbu2/BERT-Trump-vs-Biden-Classification/blob/master/Files/BidenWordCloud.png" width="400"/>
<img src="https://github.com/wbu2/BERT-Trump-vs-Biden-Classification/blob/master/Files/TrumpWordCloud.png" width="400"/>

* Based on the most common words from tweets scraped from Trump's and Biden's timeline, it is pretty clear who each word cloud belongs to. Political affiliation isn't very obvious from looking at the word clouds themselves, however the word clouds show a clear distinction between Trump and Biden. Looking at Trump's word cloud, there are phrases he often uses such as "Fake News" or "great". This shows that this data is fit to be used for a binary classification problem between Trump and Biden.


## Model

* BERT model was implemented based on [Chris McCormick's BERT implementation](http://mccormickml.com/2019/07/22/BERT-fine-tuning/)
* I used BertForSequenceClassification which is from the [Hugging Face PyTorch Library](https://github.com/huggingface/transformers) and is a BERT model with a classification layer on top
* I loaded the test data and prepared it for input to the Bert model. To evaluate predictions, I used Matthew's Correlation Coefficient since it is a binary classification problem. The MCC is in essence a correlation coefficient value between -1 and +1. A coefficient of +1 represents a perfect prediction, 0 an average random prediction and -1 an inverse prediction. [[Wikipedia]](https://en.wikipedia.org/wiki/Matthews_correlation_coefficient)
* Using my trained Bert model for sequence classification, I was able to obtain a MCC of **0.943** which is near perfect. My model, trained on tweets from Trump and Biden's timelines, was able to accrurately predict whether a given tweet was Trump's or Biden's.
