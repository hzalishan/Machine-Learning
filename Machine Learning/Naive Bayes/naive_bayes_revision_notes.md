# Naive Bayes – Revision Notes (with Code)

## 1. What is Naive Bayes?

Naive Bayes is a **probabilistic classification algorithm** based on **Bayes’ Theorem**.

It assumes that all features are **independent** (naive assumption).

Common uses:

- Spam detection
- Sentiment analysis
- Document classification

---

## 2. Bayes’ Theorem

P(A|B) = (P(B|A) \* P(A)) / P(B)

In ML terms:

P(Class | Features) = (P(Features | Class) \* P(Class)) / P(Features)

Where:

- P(Class) → Prior probability
- P(Features | Class) → Likelihood
- P(Class | Features) → Posterior (what we want)

---

## 3. Why “Naive”?

It assumes features are **independent**.

Example:

For email spam detection:

Words like “free” and “win” are treated as independent (even if they are not).

---

## 4. Types of Naive Bayes

### 4.1 Gaussian Naive Bayes

- For continuous data
- Assumes normal distribution

### 4.2 Multinomial Naive Bayes

- For discrete counts (e.g., word counts)

### 4.3 Bernoulli Naive Bayes

- For binary features (0/1)

---

## 5. Simple Example

We want to classify email as Spam (S) or Not Spam (NS).

Given:

P(S) = 0.4 P(NS) = 0.6

Word = “Free”

P(Free | S) = 0.7 P(Free | NS) = 0.1

Compute:

P(S | Free) ∝ 0.7 × 0.4 = 0.28 P(NS | Free) ∝ 0.1 × 0.6 = 0.06

Since 0.28 > 0.06 → Email = **Spam**

---

## 6. Advantages

- Very fast
- Works well with text data
- Performs well on small datasets

---

## 7. Limitations

- Independence assumption is unrealistic
- Can perform poorly if features are highly correlated

---

# 8. Python Code (Important 🔥)

## 8.1 Gaussian Naive Bayes

```python
from sklearn.naive_bayes import GaussianNB
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report

# Example data
X = [[1,2],[2,3],[3,4],[4,5]]
y = [0,0,1,1]

# Split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Model
model = GaussianNB()
model.fit(X_train, y_train)

# Predict
y_pred = model.predict(X_test)

print(classification_report(y_test, y_pred))
```

---

## 8.2 Multinomial Naive Bayes (Text)

```python
from sklearn.naive_bayes import MultinomialNB
from sklearn.feature_extraction.text import CountVectorizer

# Sample text data
texts = ["free money", "win prize", "hello friend", "meeting tomorrow"]
labels = [1,1,0,0]

# Convert text to numbers
vectorizer = CountVectorizer()
X = vectorizer.fit_transform(texts)

# Train model
model = MultinomialNB()
model.fit(X, labels)

# Predict
new_text = vectorizer.transform(["free prize"])
print(model.predict(new_text))
```

---

# 9. Key Concepts Summary

Naive Bayes → probabilistic classifier

Based on → Bayes’ theorem

Assumption → features are independent

Types → Gaussian, Multinomial, Bernoulli

Best for → text classification 🚀

