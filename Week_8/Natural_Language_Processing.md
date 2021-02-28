# Natural Language Processing 
- focuses on how programs and computers process and analyze large amounts of natural language data.
---
| Pipeline to process text data                   |
|-------------------------------------------------|
| split into words                                |
| convert to lowercase                            |
| remove punctuation                              |
| remove remaining tokens that are not alphabetic |
| filterout stopwords                             |
| stem (lemmatize) words                          |
---
- all done to clean text data before it is processed even further into numerical data for the algorithms
---
# Data preperation
### Tokenization
- Manual tokenization
```python
# split by whitespace
words = text.split()

# select words with regex
import re
words = re.split(r'\W+', text)

# remove punctuation
import string
table = str.maketrans('','', string.punctuation)

stripped = [w.translate(table) for w in words]

# Normalizing Case
words = [word.lower() for word in words]
```
- Tokenization and Cleaning with NLTK

```python
import nltk

# split into sentences
from nltk import sent_tokenize
sentences = sent_tokenize(text)

# split into words
from nltk.tokenize import word_tokenize
tokens = word_tokenize(text)

# filter out punctuation
words = [word for word in tokens if word.isalpha()]

# filter out stop words
from nltk.corpus import stopwords
stop_words = set(stopwords.words('english'))
words = [w for w in words if not w in stop_words]

# stem words
from nltk.stem.porter import PorterStemmer
porter = PorterStemmer()

stemmed = [porter.stem(word) for word in tokens]
```
---
# feature extraction with text data 

## Bag of Words (BOW)
- get vocablulary of known unique words in model 
    -  each index will correspond to one word and each word is a different dimension
- make a sparse vector of d-unique words 
    - fill it with number of times the corresponding word occurs in a document.
- commonly used when frequency of words is a feature 
- text cleaning is recommended to rudece size of vocabulary 
### N-grams model
- more sophisicated version of BOW
- vocabulary is changed to containt `n` number of words, instead of individual words
-  capture a little  more meaning4

## TF-IDF (term frequency-inverse document frequency)
- statistic intended to reflect word importance
    - increase proportionaly with number of times it appears in document
    - decreases by the number of documents that contain word
- Term frequency:
    - TF(w, d) = # of times w occurs in d / # of words in d
- inverse document frequency
    - idf(w, D) = log(number of documents in corpus / number of documents where w appears)

## Word2Vec
- trains words against other words that neighbor them in the input corpus
    -  either using context to predict a target word (a method known as continuous bag of words, or CBOW), 
    - or using a word to predict a target context, which is called skip-gram. (more accurate results on large datasets.)
- distributed representation of a word is used
    - a vector with several dimensions
    - each word is represented by a distribution of weights across those elements.
    - each element in the vector contributes to the definition of many words

<img src="https://miro.medium.com/max/704/1*VE6e-n7Ot2cy3N6PVnibAw.png">

[source](https://medium.com/@zafaralibagh6/a-simple-word2vec-tutorial-61e64e38a6a1)