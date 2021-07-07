---  
layout: post  
title:  "Rank 결과를 더 좋게하고 싶다면? Ensemble"  
date:   2020-06-13
excerpt: ""  
tag:  
- Recommender System

comments: false  
---  

# Ensemble in Machine Learning

![cycle icon 이미지 검색결과](https://upload.wikimedia.org/wikipedia/commons/thumb/d/da/Ensemble.png/180px-Ensemble.png)
모여라!~ 강해지자!~

우리가 어렸을 적 보았던 만화는 대개 이런 내용이다.

혼자서의 힘으로 적을 무찌를 수 없어 친구들의 힘을 모아 혹은 친구들의 도움을 받아서 적을 무찌른다.

머신러닝에서도 비슷하다. 거의 대부분은 base model로 단독으로 엄청난 performance를 내진 않는다.
(문제가 단순하면 어떤 모델이든 잘 풀릴 것이다)

위와 같은 접근방법으로 머신러닝에서 모델의 성능을 높이기 위하여 앙상블을 사용한다.
앙상블은 여러 개의 모델에 대한 aggregation(집약)으로 표현할 수 있는데,

- 다수결 투표
- 평균 
- Stacking 등이 기본이다.


## Ensemble in Rank Model

순위를 내는 Rank Model의 경우는 어떨까?
가장 간단하게는 순위들에 대한 총합을 구하고 그 결과에 대해서 정렬을 다시 하는 것이다.

모델에 대해서 다음과 같은 Rank가 나왔다고 해보자.

|                |Model A                          |Model B                         |
|----------------|-------------------------------|-----------------------------|
|Doc1 |1         |1    |
|Doc2          |2           |4     |
|Doc3          |3|2|
|Doc4          |4|3


그러면, 총합을 구하게 되면

|                |Model A                          | Model B | Agg|
|----------------|-------------------------------|-----------------------------|-----------------------------|
|Doc1 |1         |1    | 2|
|Doc2          |2           |4     | 6|
|Doc3          |3|2 | 5|
|Doc4          |4|3 | 7 |

다음과 같이 정렬할 수 있게 된다.

1. Doc1
2. Doc3
3. Doc2
4. Doc4

지금 사용하는 기법은 Rank를 통해서 fusion 한다는 의미에서 Rank based fusion이라 한다.
그리고 model에 대한 output(score)를 이용하여 fusion을 하는 것은 Score based fusion이라 한다.

![](https://image.slideserve.com/1386615/data-fusion-methods-l.jpg)
참고된 fusion methods에 참조하여 더욱 더 열심히 공부해보자!

