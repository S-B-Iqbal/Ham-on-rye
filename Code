# Step 1 : Collecting the Data

sms_raw <- read.csv("sms_spam.csv", stringsAsFactors = FALSE)

#Step 2 : Exploring and preparing the data

sms_raw$type <- factor(sms_raw$type)

# Data preparation : cleaning and standardizing the data

install.packages("tm")

library(tm)

sms_corpus <- VCorpus(VectorSource(sms_raw$text))

# Transforming the corpus : to lowercase

sms_corpus_clean <- tm_map(sms_corpus, content_transformer(tolower))

# Transforming the corpus : remove the nummbers

sms_corpus_clean <- tm_map(sms_corpus_clean, removeNumbers)

# Transforming the corpus : remove the stop words

sms_corpus_clean <- tm_map(sms_corpus_clean, removeWords, stopwords())

# Transforming the corpus : remove the punctuation

sms_corpus_clean <- tm_map(sms_corpus_clean, removePunctuation)

# Transforming the corpus : Stemming

install.packages("SnowballC")

library(SnowballC)

sms_corpus_clean <- tm_map(sms_corpus_clean, stemDocument)

# Transforming the corpus : Remove white spaces

sms_corpus_clean <- tm_map(sms_corpus_clean, stripWhitespace)

# Splitting text documents into words using tokenization

sms_dtm <- DocumentTermMatrix(sms_corpus_clean)

# Data Preparation: creating training and test datasets

sms_dtm_train <- sms_dtm[1:4574,]

sms_dtm_test <- sms_dtm[4575:5574,]

sms_dtm_train_labels <- sms_raw[1:4574,]$type

sms_dtm_test_labels <- sms_raw[4575:5574,]$type

sms_freq_terms <- findFreqTerms(sms_dtm_train, 5)

sms_dtm_freq_train <- sms_dtm_train[, sms_freq_terms]

sms_dtm_freq_test <- sms_dtm_test[,sms_freq_terms]

convert_counts <- function(x) {
   x <- ifelse(x>0 , "Yes", "No")
  
}

sms_train <- apply(sms_dtm_freq_train, MARGIN = 2, convert_counts)

sms_test <- apply(sms_dtm_freq_test, MARGIN = 2, convert_counts)

# Step 3 : Training a model on the data

install.packages("e1071")

library(e1071)

sms_classifier <- naiveBayes(sms_train, sms_dtm_train_labels, laplace = 1)

sms_test_pred <- predict(sms_classifier, sms_test)

library(gmodels)

CrossTable(sms_test_pred, sms_dtm_test_labels, prop.chisq = FALSE,
           prop.t = FALSE, dnn = c('predicted', 'actual') )
