# Sentiment Analysis

- Sentiment analysis is contextual mining of text

| Basic pipeline                      |
|-------------------------------------|
| train test split the data           |
| clean the train data                |
| vectorize the data                  |
| classify the data (eg. naive bayes) |

---
```python
from nltk.corpus import stopwords
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.model_selection import train_test_split
from sklearn import naive_bayes

# tf1dvectorizer, also cleans the data little
vectorizer = TfidfVectorizer(use_idf=True, lowercase=True, strip_accents='ascii', stop_words=stopset)

# split to avoid data leakage
X_train, X_test, y_train, y_test = train_test_split(X=df['text'], y=df['target'], random_state=42)

# get X, y, vectorize X
y = y_train
X = vectorizer.fit_transform(X_train)

# instantiate classifier, fit, and test
clf = naive_bayes.MultinomialNB()
clf.fit(X_train, y_train)
roc_auc_score(y_test, clf.predict(X_test))
```