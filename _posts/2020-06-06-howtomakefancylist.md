---  
layout: post  
title:  "어떻게 리스트를 개선할 수 있을까? Part 1"  
date:   2020-06-06
excerpt: ""  
tag:  
- Redis  
- UX
- Recommender System

comments: false  
---  

# Redis로 리스팅 개선하기

![cycle icon 이미지 검색결과](https://blog.hubspot.com/hubfs/best-mobile-websites.jpg)

우리가 상품을 여러 유저에게 보여주기 위해서 많은 노력을 한다.
예쁜 UI를 구상하고, userflow를 그려보며 많은 시나리오를 구상한다.

추천 시스템에서 추천을 하는데 가장 먼저 해결할 수 있는 심플하면서도 가장 영향력이 있는 프로젝트는
리스팅 개선 프로젝트일 것이다.

## UI만 예뻐진다면?

UI가 개선되면 당연히 유저는 페이지 자체에 대한 좋은 이미지를 갖게 될 것이며,
유저가 페이지를 지속적으로 이용할 가능성이 높아질 것이다.
하지만, 봤던 영상이 또 나오고, 앱을 껐다가 켰을 떄 동일한 게 또 나온다면?
일정 session 내 활동하는 유저는 수 많은 상품들을 놓칠 수밖에 없고, 그렇기에 유저는 지속적으로 앱을 사용할 요인이 적게 된다.

![hey](https://media.vingle.net/images/ca_l/47q48rm04h.jpg)

## 안 본 것들을 보여주자!

많은 스타트업이 고질적으로 갖게될 문제는 다음과 같다.
1. 보여준 것 또 보여주기.
2. 업로드된 순서로 보여주기

왜냐하면, 개발과정에서 last item은 당연히 upload된 item 중 마지막일 것이고,
유저는 last item만 계속 보게 될 것이다.

마치, 끝나지 않는 stack pop이랄까?...

![](https://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Data_stack.svg/1200px-Data_stack.svg.png)


## Redis로 리스팅 개선하기?

Redis에 대한 조작은 다음 포스팅을 통해서 이야기하고자 한다.
(사실 친구와 매일 블로그를 작성하기로 했는데, 처음부터 꼬여서 부랴부랴 작성중이다.)

그러면 어떻게 Redis로 개선할 수 있을까?
오늘 블로그는 흥미만 주기 위하여 작성되었기 때문에(기간 내 부랴부랴 작성하는 것은 안 비밀)

![](https://upload.wikimedia.org/wikipedia/commons/5/5b/KeyValue.PNG)

**위 그림을 보면 바로 이해할 수 도 있다.**

유저에 대해서 보여줄 영상들을 미리 담아두는 것이다.

즉, 유저를 Key로 하여 보여줄 영상들은 value들로 담아두는 것이다.

### 엥?

![](https://pbs.twimg.com/profile_images/990944360203145217/y5MdOHGV_400x400.jpg)

보게 되는 순간 바로 생각드는 물음들은 다음과 같을 것이다.

1. 이렇게 간단히?
> 네, 너무 간단하죠?
2. 성능에는 문제가 없어요?
> 걱정하지마세요. Redis는 생각보다 강력합니다.
3. 다 보면 어떡해요?
> 완료되는 시점에 다시 쌓아줍니다.

<img src="https://www.pngjoy.com/pngm/272/5202376_cycle-icon-lifecycle-icon-transparent-png.png" alt="drawing" width=300 />



### 약간 정리

일단 Redis로 리스팅을 개선할 수 있는 작은 아이디어를 제시하였다.
key-value store에서 user를 key로 하여 user를 조회할 시점에 남아있는 item들을 조회하는 것이다.

다음 포스팅은 이를 위해 어떻게 redis를 조작하는 지에 대해 다루고자 한다.

안 보여준 것들을 보여주기. 이를 해결하는 건 생각보다 상당히 어려운 문제다. 나중의 추천 시스템이 들어가는 경우 다양성을 챙기는 것은 또 다른 task다. 
그리고 우리는 그 문제를 해결해나갈 수 있는 아이디러를 얻었다.
