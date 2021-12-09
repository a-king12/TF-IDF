install.packages('quanteda')
install.packages("stopwords")
install.packages('quanteda.textmodels')
install.packages('topicmodels')
install.packages('tidytext')

library(quanteda)
library(stopwords)
library(quanteda.textmodels)
library(topicmodels)
library(tidytext)

text <- read.csv('gastext.csv',stringsAsFactors = F)

myCorpus <- corpus(text$Comment)
summary(myCorpus)

myDfm <- dfm(myCorpus)
topfeatures(myDfm)

# Create an alternative dfm based on bigram
myTokens <- tokens(myCorpus)
bigram <- tokens_ngrams(myTokens,n=1:2)
myDfm_bigram <- dfm(bigram)
View(myDfm_bigram)

myDfm <- dfm(myCorpus, 
             remove = c(stopwords("english"),'.',',','t'),
             stem=T)
topfeatures(myDfm)
dim(myDfm)

# Weight a dfm by tf-idf
myDfm_tfidf <- dfm_tfidf(myDfm)
View(myDfm_tfidf)

# Topic modeling based on the original DFM
myLda <- LDA(myDfm,k=2,control=list(seed=101))
myLda

# Term-topic probabilities
myLda_td <- tidy(myLda)
myLda_td
