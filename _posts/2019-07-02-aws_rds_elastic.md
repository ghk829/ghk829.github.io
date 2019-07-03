---
layout: post
title:  "AWS RDS and Elastic beanstalk"
date:   2019-07-02
excerpt: "AWS RDS and Elastic beanstalk"
tag:
- nodejs
- javascript
- swift

comments: false
---

# AUSG

오늘은 또 AWS 대학생 커뮤니티 가봤다.

주제는

client가 swift로 만들어진 앱을 통해
node로 만들어진 server(AWS) API를 호출하여
지역에 별점을 매기는 앱을 만드는 것다


[link](https://github.com/jaehui327/AUSG-iOS-MapOfRestaurant)



## 열정

앱을 잘 만들고, AWS 스터리라는 것을 떠나서 대학생들이 이렇게 열정적으로 커뮤니티를 운영하고 있다는 것이 신기했고, 심지어 가이드까지 친절하게 작성한 걸 보고 많은 걸 느꼈다.


# AWS 기능들 그리고 느낀 점

## AWS RDS

AWS RDS는 AWS에서 클라우드로 RDB를 배포할 수 있게 하는 웹 서비스다.

써보면서 웹을 통해서 인스턴스 생성/ 모니터링 등등 모든 걸 다 할 수 있다.
웹 개발을 하면서 DB 작업하는 것들을 다 할 수 있으니 편할 것 같긴 하다.


## AWS Elastic Beanstalk

얘는 소스를 배포하여 앱을 운영하는 서비스다.

heroku처럼 소스만 있으면 바로 배포해서, 운영까지 가능한 서비스다.



> 두 서비스 모두 다 있다는 것을 알고있었지만, 실제로 돈 주면서 쓰는 건 처음이다...ㅎㅎ
> EC2만 쓰다가 서비스 형태로 있는 것을 써보니 확실히 편하긴 편하다.
> 웹 개발시 많이 참고할 것 같다.
