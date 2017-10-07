# SentimentalAnalysis
Sentimental Analysis  using scikit pipelines and custom featurizer 

#Feature Engineering
In many practical machine learning problems, the raw data is not provided in a format that is easily
understood by learning algorithms. To get the best performance from a machine learning model,
certain dimensions or features need to be engineered by the programmer prior to the learning phase.
These engineered features transform the data into a representation that is better understood by a
machine. For example, if we want a machine learning model to learn about natural language, it
may be better to feed in frequency counts of the words in a document, compared to just a plaintext
string.

#Classification
using scikit pipeline and feature Union to develop custom features and SGD to classify movie reviews as positive or negative

Custom features included are:
1. Counting negative words, double negative words and negating words in the corpora - NegativeWordTransformer,
corpus of negative words present in test data.
Number of negative words indicate how negative a review is and Lesser the number of negative words,more is the review polarity being positive.
This increased the accuracy by 12 on the baseline

2. Number of Quotes (double quotes) in the review
surprisingly there are 17K double quotes which add the review severity.
adding double quote Transformer gained accuracy by 6.

3. Punctuations: created PunctutationTransformer which would count ..., !!! and ??? in the
corpus.
All the corpus usually have .!? as special words which accounts to sentiment of review, but
there were most of the cases which occurred only in negative review which lead to choose
them as features. To reduce noise, considered repetition of punctuation thrice as the feature.
In particular "..." increased the performance by 6 from 77.6 to 83.

4. RateTransformer : Feature to find ratings if provided in review and classify them.
Used regex to find the ratings and took the last rating of the review assuming the last would be conclusion of the review.
Increased performance by 2 overall.
All the above features were normalized using l2 Normalization by sklearn's Normalizer

#Improvements:
1. Parts of speech 
using nltk's tagger to tag the content and nltk.sentiment.vader.SentimentIntensityAnalyzer to find the sentiment.
This increased the performance over baseline by 20.
2. nltk's porter stemmer
Used to stem the data and store stemmed words frequency for given sentence.

