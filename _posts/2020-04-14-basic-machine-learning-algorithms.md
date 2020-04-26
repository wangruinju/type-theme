---
layout: post
title: Basic Machine Learning Algorithms
tags: [NLP, machine-learning]
---

Today I will share 4 basic machine learning algorithms, which are commonly asked in machine learning interviews: 

1. **KMeans**
2. **K Nearest Neighbors (KNN)**
3. **Native Bayes** 
4. **Gradient Boosting Decision Tree (GBDT)**.

- [KMeans](https://en.wikipedia.org/wiki/K-means_clustering)

TODO: add explanation and follow up (pro and cons)

Python Code Implementation
```python
import numpy as np

class KMeans:

    def __init__(self, n_clusters=5, max_iter=300, random_state=42):
        self.n_clusters = n_clusters
        self.max_iter = max_iter
        self.random_state = random_state

    def fit(self, X):
        np.random.seed(self.random_state)
        initial = np.random.permutation(X.shape[0])[:self.n_clusters]
        self.cluster_centers_ = X[initial]

        for _ in range(self.max_iter):
            self.labels_ = [self._nearest(self.cluster_centers_, x) for x in X]
            indices = [[i for i, l in enumerate(self.labels_) if l == j]
                        for j in range(self.n_clusters)]
            X_by_cluster = [X[i] for i in indices]
            # update the clusters
            self.cluster_centers_ = [c.sum(axis=0) / len(c) for c in X_by_cluster]
        # sum of square distances from the closest cluster - WCSS
        self.inertia_ = sum(((self.cluster_centers_[l] - x)**2).sum()
                            for x, l in zip(X, self.labels_))
        return self

    def _nearest(self, clusters, x):
        return np.argmin([self._distance(x, c) for c in clusters])

    def _distance(self, a, b):
        return np.sqrt(((a - b)**2).sum())

    def predict(self, X):
        return self.labels_

    def transform(self, X):
        return [[self._distance(x, c) for c in self.cluster_centers_] for x in X]

    def fit_predict(self, X):
        return self.fit(X).predict(X)

    def fit_transform(self, X):
        return self.fit(X).transform(X)

    def score(self, X):
        return -self.inertia_

X = np.random.random((50, 10))

kmeans = KMeans(n_clusters=5, random_state=1)
kmeans.fit(X)
print(kmeans.inertia_)
```

- [K Nearest Neighbors](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm)

TODO: add explanation and follow up (pro and cons)

Python Code Implementation
```python
import numpy as np 
from collections import defaultdict
from sklearn import datasets
from sklearn.model_selection import train_test_split

class KNeighborsClassifier:

    def __init__(self, n_neighbors=5, weights='uniform', p=2):
        self.n_neighbors = n_neighbors
        self.weights = weights
        self.p = p

    def fit(self, X, y):
        self.X = X
        self.y = y
        return self

    def _distance(self, data1, data2):
        """1: Manhattan, 2: Euclidean"""
        if self.p == 1:
            return sum(abs(data1 - data2))          
        elif self.p == 2:
            return np.sqrt(sum((data1 - data2)**2))
        raise ValueError("p not recognized: should be 1 or 2")

    def _compute_weights(self, distances):
        if self.weights == 'uniform':
            return [(1, y) for d, y in distances]
        elif self.weights == 'distance':
            matches = [(1, y) for d, y in distances if d == 0]
            return matches if matches else [(1/d, y) for d, y in distances]
        raise ValueError("weights not recognized: should be 'uniform' or 'distance'")

    def _predict_one(self, test):
        distances = sorted((self._distance(x, test), y) for x, y in zip(self.X, self.y))
        weights = self._compute_weights(distances[:self.n_neighbors])
        weights_by_class = defaultdict(float)
        for d, c in weights:
            weights_by_class[c] += d
        return max(weights_by_class, key = weights_by_class.get)

    def predict(self, X):
        return [self._predict_one(x) for x in X]

    def score(self, X, y):
        return sum(1 for p, t in zip(self.predict(X), y) if p == t) / len(y)

iris = datasets.load_iris()

X_train, X_temp, y_train, y_temp = \
    train_test_split(iris.data, iris.target, test_size=.4)
X_validation, X_test, y_validation, y_test = \
    train_test_split(X_temp, y_temp, test_size=.5)

neighbor = KNeighborsClassifier().fit(X_train, y_train)

print(neighbor.score(X_train, y_train))
print(neighbor.score(X_validation, y_validation))
```

- [Native Bayes](https://en.wikipedia.org/wiki/Naive_Bayes_classifier)

TODO: add explanation and follow up (pro and cons)

Python Code Implementation
```python
import numpy as np 
from sklearn.model_selection import train_test_split
from sklearn import datasets

class GaussianNB:

    def __init__(self):
        pass

    def fit(self, X, y):
        separated = [[x for x, t in zip(X, y) if t == c] for c in np.unique(y)]
        # get the mean and std for each feature under each class data
        self.model = np.array([np.c_[np.mean(i, axis=0), np.std(i, axis=0)]
                    for i in separated])
        return self

    def _prob(self, x, mean, std):
        return np.log(1.0/ (np.sqrt(2 * np.pi) * std)) - ((x - mean)**2 / (2 * std**2))

    def predict_log_proba(self, X):
        return [[sum(self._prob(i, *s) for s, i in zip(para, x)) for para in self.model] for x in X]

    def predict(self, X):
        return np.argmax(self.predict_log_proba(X), axis=1)

    def score(self, X, y):
        return sum(self.predict(X) == y) / len(y)

iris = datasets.load_iris()
X, y = iris.data, iris.target
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=.25)
nb = GaussianNB().fit(X_train, y_train)
print(nb.score(X_train, y_train))
print(nb.score(X_test, y_test))
```

- [Gradient Boosting Decision Tree](https://en.wikipedia.org/wiki/Gradient_boosting)

TODO: add explanation and follow up (pro and cons)

Python Code Implementation
```python
from sklearn.datasets import load_boston
from sklearn.tree import DecisionTreeRegressor
from sklearn.model_selection import train_test_split
import numpy as np

class GBDT:
    
    def __init__(self, max_iter = 50, learning_rate = 0.1):
        self.max_iter = max_iter
        self.learning_rate = learning_rate
        self.f0 = None
        self.regressors = []
        
    def compute_loss(self, y, y_hat):
        # mse square loss
        return ((y-y_hat)**2)/2
    
    def loss_gradient(self, y, y_hat):
        return -(y-y_hat)
    
    def fit(self, X, y):
        y_hat = np.array([y.mean()]*len(y))
        self.f0 = y_hat
        print(self.compute_loss(y, y_hat).mean())
        for i in range(self.max_iter):
            residuals = -self.loss_gradient(y, y_hat)
            regressor = DecisionTreeRegressor(max_depth=1)
            regressor.fit(X, residuals)
            self.regressors.append(regressor)
            predictions = regressor.predict(X)
            y_hat = y_hat + self.learning_rate * predictions
            print(self.compute_loss(y, y_hat).mean())
        return self
    
    def predict(self, X):
        y_hat = np.array([self.f0[0]]*len(X))
        for regressor in self.regressors:
            y_hat = y_hat + self.learning_rate * regressor.predict(X)
        return y_hat


gbdt = GBDT(max_iter = 300, learning_rate = 0.05)
boston = load_boston()
X = boston.data
y = boston.target
X_train, X_test, y_train, y_test = train_test_split(X, y)
gbdt.fit(X_train, y_train)
y_hat = gbdt.predict(X_test)
print(np.sum((y_test-y_hat)**2)/len(y_test))
```
