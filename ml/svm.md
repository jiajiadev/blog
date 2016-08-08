# SVM

```
import numpy as np
from sklearn import svm


class SVM():

    def __init__(self):
        Detector.__init__(self)
        self.clf = svm.LinearSVC(tol=0.0000001, random_state=0) # svm predictor
        self.pred = [] # svm prediction
        self.pred_ind = [] # label indices
        return

    def fit(self, X, Y):
        # training dataset
        self.X_train = np.array(X, dtype=float)
        self.Y_train = np.array(Y)

        if self.N_train != self.Y_train.shape[0]:
            raise Exception("X and Y have not the same length!")

        self.clf.fit(self.X_train, self.Y_train) # training
        return

    def detect(self, X):
        self.pred = self.clf.predict(self.X_test_scaled)
        return self.pred
```
