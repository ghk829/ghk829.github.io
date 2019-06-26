---
layout: post
title:  "pip install target"
date:   2019-06-27
excerpt: "pip target"
tag:
- python
- pip

comments: false
---

## target을 활용하는 이유

패키지를 관리한다는 측면에서 conda env를 활요하면 도움이 많이 된다.

*외장하드* 에 전적으로 용량을 제일 많이 차지하는 패키지들을 놔두고 싶을 떄 -t 옵션을 사용하면 된다


> 예제

``` sh

DIR=설치할 directory

conda activate `env_name`

pip install -t $DIR flask

export PYTHONPATH=$PYTHONPATH:$DIR

```

파이썬에서 패키지를 불러올 때 경로를 DIR까지 포함하여 가져오므로,

해당 라이브러리들을 모두 불러올 수 있다.
