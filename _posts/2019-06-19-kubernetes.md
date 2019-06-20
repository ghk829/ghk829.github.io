---
layout: post
title:  "IBM DevOps study"
date:   2019-06-19
excerpt: "IBM DevOps meetup"
project: false
tag:
- kubernetes
- devops
- IBM
comments: false
---

# IBM DevOps & K8S
[link](ibm.biz/201906dw)

**DevOps 3가지 중요 요소**

devpos : 운영 철학

cloud : devops arhi

microservice : 배포
alcatraz : 샌프란시스코 감옥

## Escaping alcatraz

Monolith - data (Centralization)
에서
Containerization (Modern Apps)

DevOps : 문화 , 같은 목표를 가지고 좀 더 빨리 어플리케이션 배포

> 예전 : multiple toolchain backbone tools : automation tools
-  앱이 많이 생길 수록 병목이 생김

> Modern DevOps: Many but Single-tenant toolchains 독립적인 App Build
- 스쿼드 : 계층적인 하이아키가 아니라 프로젝트 기준의 팀 ( 8 명정도 : 피자 두 판을 배부르게 먹을 수 있는)
- SaaS multi-cloud deployment
- Day 1 automation : 기본적인 template을 적용할 수 있게 하는 것
필요한 만큼 컨테이너로 개발 환경 제공

Saas : SmartBearReadyAPI
Trello : issue managemen
deploy : urban code
JMeter : performance test
terraform : K8S 운영
Slack : Interation

CI/CD란 배포까지 이루어져야 함
microservice 하나 당 하나의 repository로
> 공통 라이브러리의 경우는 어떻게 할 것인가?

- 장애 : 스쿼드는 같은 KPI를 공유해야 함

Multi-speed IT enablement : API 테스팅
Feature toggling


## Trial Period is Over

MSA에서 실제로 적용할만한

### SOA vs MSA

SOA를 하더라도 결국 DB는 같은 걸 쓰게 됨
MSA는 다른 툴 체인을 통해 deploy된다 / function단위로 쪼갠다

> MSA 장점

1. scale
2. fault isolation : 해당 이벤트 사이트만 죽을 것 - 장애의 전파를 막아준다
3. Agility : 민첩도가 높아짐
4. Flexiblity : 다른 언어나 다른 DB 적용 가능 - 분리돼서 일할 수 있다.

> Tenets of MSA
 1. 서비스는 하나의 컨테이너 하나의 pod은 여러개의 container (process 하나는 하나의 container)
 2. 어떻게 쪼개야 하는가?  하나의 비즈니스 기능으로 쪼갠다
 3. REST API and message brokers를 통해 Communication : 표준화된 프로토콜로
 4. clustering decisions

**MSA 장점 :  서비스가 계속 업데이트가 되어야 할 때**

> MSA를 적용하지 않아야 할 때
1. financial business case의 경우 쪼개기 힘듦
2. 업데이트가 자주 일어나지 않는 경우
3. 고객이 얼마나 될 지 예측가능한 서비스  : auto-scale이 그다지 필요없기 때문에
4. 관리할 수 있는 **기술 및 툴, 문화**가 없는 경우 MSA로 가기 힘들다

> GreenField (New) VS BrownField (Existing)

BrownField의 경우 한 번에 MSA로 가기는 힘들다.
필요한 부분들만 떼어내서 micro화 해야 함 over time (strangle)

- ACID에 대해서 엄밀했지만, **loose하게 쿼리를 가져오는 비즈니스 로직이 생각보다 많다** : BASE
Ex ) 상품평의 경우 RDB에 넣을 필요없이 Nosql로 넣고 API로 get
Saga Pattern : Transaction 처리 방법

- Distributed Data Management : cli / event driven

Master Data : Redis에다가 넣어서 관리한다.

lift-shift : iaas onpremise --> cloud machine

**복잡도 / 코스트 / 밸류 / 오더**


Issue에 대한 레포지토리?

- 우리나라가 DevOps가 힘든 경우 : SI

- **Agile** : Learning Organization이지만, 정규직...은 과연 배울까? 슈퍼스타만 있으면 됨 ㅠㅠㅠㅠㅠ
- 실패 사례의 경우 공유하는 문화가 있어야 함
- HELM : 배포 표준
- terraform : k8s를 배포하는 opensource
- k8s도 management 서비스를 이용하면서 어떤 것이 매니지먼트가 필요한 지 확인하는 것도 좋음


