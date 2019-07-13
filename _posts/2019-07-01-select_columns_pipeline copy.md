---
layout: post
title:  "sklearn FunctionTransformer"
date:   2019-07-01
excerpt: "sklearn FunctionTransformer"
tag:
- python
- sklearn

comments: false
---

# Pipeline

scikit-learn에서 pipeline은 엄청 중요한 역할을 한다.

GridSearchCV의 핵심이며, pipeline을 통해 search할 범위의 set을 손쉽게 control이 가능하다.

맨날 이용하다가 scikit-learn에서 몇 컬럼들만 추출하여 작업하는 경우가 많았고,
이러한 기능이 있을 거 같아서 찾아보았다.

## FunctionTransformer

위 function을 통해서 생각하는 코드를 구현할 수 있다.

물론, partial function을 이용하면, pipeline을 구성할 때 원하는 컬럼을 사용자 정의에 맞게 구성이 가능하다


``` python

from sklearn.pipeline import make_union, make_pipeline
from sklearn.preprocessing import FunctionTransformer,MinMaxScaler
from functools import partial

def select_columns(dataframe=None,columns=[]):
    from functools import partial

    def _select_columns(dataframe,columns):
        return dataframe[columns]

    return partial(_select_columns,columns=columns)

vec = FunctionTransformer(select_columns(columns=["admit","gre"]), validate=False)

```

> 전체 코드


``` python

from sklearn.pipeline import make_union, make_pipeline

from sklearn.preprocessing import FunctionTransformer

def select_columns(dataframe=None,columns=[]):
    from functools import partial

    def _select_columns(dataframe,columns):
        return dataframe[columns]

    return partial(_select_columns,columns=columns)

vec = FunctionTransformer(select_columns(columns=["admit","gre"]), validate=False)

```

> partial function을 이용해 return은 function이다 따라서, callable하기 때문에
>
> pipeline을 구성하기 위한 line이 된다.
``` python

def select_columns(dataframe=None,columns=[]):
    from functools import partial

    def _select_columns(dataframe,columns):
        return dataframe[columns]

    return partial(_select_columns,columns=columns)

```

> 아래 코드는 kwargs를 통하여 columns를 지정하므로 make_pipeline 이나
>
> ``` python
> from sklearn.model_selections import Pipeline
> ```
> 의 Pipeline에서 contructor 부분에서 호출할 때도 단순히 변수 자체를 넣어주면 된다.

``` python

from sklearn.preprocessing import FunctionTransformer

vec = FunctionTransformer(select_columns(columns=["admit","gre"]), validate=False)


```