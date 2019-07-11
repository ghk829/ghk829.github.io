---
layout: post
title:  "partial fit"
date:   2019-07-11
excerpt: "partial fit"
tag:
- python
- machine learning
- sklearn
comments: false
---

# Partial Fit

partial fit이 필요하게 된 배경과 partial fit을 통해 얻을 수 있는 장점에 대해 이야기하고자 한다.


## Fitting Algorithms

Linear Regression, SVM 등 일반적인 선형 알고리즘이나

Logistic Regression, SVC와 같은 간단한 분류모형의 경우

메모리를 그렇게 많이 잡아먹진 않지만, 데이터 수가 많아지면 당연히 필요한 메모리는 증가한다.

정말 많은 데이터를 학습시키기 위하여 할 수 있는 조치는 3가지이다.

1. 서버 용량을 증설하기
2. 모델의 trainset을 batch화시키기
3. 용량을 적게 만드는 알고리즘을 개발하기...ㅎㅎ

tensorflow와 같은 딥러닝 프레임워크의 경우 일반적으로 코딩에서 mini-batch화하는게 코딩에 배기지만, ML의 경우 이러한 코딩을 잘 하지 않는 경우가 대부분이며, 빅데이터를 위해 보통의 경우 서버 용량을 증설시키거나 spark와 같은 분산처리 라이브러리를 활용헌다.

## Mini-batch

딥러닝의 경우 mini-batch화시키는 경우가 대부분이며, 그중에서 제일 많이 쓰는 optimize 방법론 중 하나가 **SGD**이다.

이를 scikit-learn에서도 사용이 가능하며 데이터를 배치화시킬 수 있다.

``` python

from sklearn.linear_model import SGDClassifier

clf = SGDClassifier(**parameters)

for X,y in zip(X_train_fold,y_train_fold):
    clf.partial_fit(X,y)

```

> SGD 모델이 지원하는 모델의 항목의 리스트는 아래에 있다.
>
> [SGD](https://scikit-learn.org/stable/modules/sgd.html)


이외의 모델은?

Ensemble 모델의 경우 scitkit-learn에서 partial_fit을 지원하는 모델은 현재 없다.

[IncremetalTrees](https://github.com/garethjns/IncrementalTrees)

위와 같은 패키지가 지원을 한다. SparkML에서 지원하는 알고리즘 정도는 대세 라이브러리
dask로 지원하는 정도인 거 같다.

이와 더불어 ensemble모델의 초기화 부분에서 warm_start 옵션이 있는데 이는 사실 partial_fit과는 다르지만, parameter 조정, 트리 수의 확장 등을 지원한다.

doc에 있는 상세내용이다.
```
When set to True, 
reuse the solution of the previous call to fit 
and add more estimators to the ensemble, 
otherwise, just fit a whole new forest.

```
실제 로직이다.

https://github.com/scikit-learn/scikit-learn/blob/14031f6/sklearn/ensemble/forest.py#L291

``` python

# Parallel loop: we use the threading backend as the Cython code
            # for fitting the trees is internally releasing the Python GIL
            # making threading always more efficient than multiprocessing in
            # that case.
            trees = Parallel(n_jobs=self.n_jobs, verbose=self.verbose,
                             backend="threading")(
                delayed(_parallel_build_trees)(
                    t, self, X, y, sample_weight, i, len(trees),
                    verbose=self.verbose, class_weight=self.class_weight)
                for i, t in enumerate(trees))

            # Collect newly grown trees
            self.estimators_.extend(trees)

```