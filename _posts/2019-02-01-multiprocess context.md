---
layout: post
title:  "manager & serialization"
date:   2019-01-03
excerpt: "Mutlprocess Manager"
tag:
- python
- Flask
- Spring boot
comments: false
---
### Multi-process in python Part 2 : manager 작동 원리 및 serialization 문제

프로세스끼리 데이터를 주고받기 위한 방법은 다음과 같다


* SIGNAL
* pipe
* socket
* IPC


그중에서 socket이 제일 많이 쓰이는 방법이다.

Python에서 프로세스끼리 통신하는 방법도 socket을 이용한다.



### 1. Manager : Server

``` Python
from multiprocessing import Manager

with Manager() as manager:
     context_manager = manager.dict()

```

데이터를 Key/Value 형태로 관리하는 것이 가능하기 때문에,
부모 프로세스와 자식 프로세스는 manager를 통해서 데이터의 교환이 가능하다.

그러나, manager를 사용하면서 주의할 점은 이 manager는 server처럼 데이터를 옮겨주고 받기 위해 process가 항상 떠있다는 것이다.

Multi User(N) 및 Multi Workflow(M)를 지원하는 우리 플랫폼에선
N*M개만큼의 프로세스가 생성된다는 것이다.

하지만, 하나의 프로세스로 전부관리하는 것은 문제점이 있는데, 프로세스 간의 데이터 교환의 성능이 그 문제다.
겨

결국, UI에서 유저마다의 워크플로우의 개수를 제한함으로써 이 한계를 한계로 규정지었다.

### 2. Serialization : pickle

multiprocessing간의 통신은 socket으로 이루어지기 때문에 binary 형태의 데이터까지 교환은 가능하다.

하지만, multiprocessing에서 데이터를 넘겨주고 받을 때 *Python Object* 를 넘겨주고 받을땐 pickle을 통해 de-serialization을 하게 되는데, 오픈소스 라이브러리 중에 H2O 같은 경우는 복원할 수 없는 데이터이다.

이 문제를 H2O JVM을 활용하여 해결하였다.

JVM에 올라오는 객체 ID를 참조하여

``` mermaid
Python Object (process 1) --> H2O JVM

H2O JVM --> Python Object (process 2)

```

위와 같은 형식으로 데이터를 복원하였다.


<script>
setTimeout(function() {
		$(function(){
        var element = document.querySelector(".language-mermaid");

        var insertSvg = function(svgCode, bindFunctions){
            element.innerHTML = svgCode;
        };

        var graphDefinition = element.textContent;
        var graph = mermaid.mermaidAPI.render('graphDiv', graphDefinition, insertSvg);
    });
}, 1500)
</script>
