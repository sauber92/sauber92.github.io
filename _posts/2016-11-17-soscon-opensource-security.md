---
layout: post
title: '[SOSCON 2016] 오픈소스에서의 취약점 분석'
tags: [Review]
description: >  
    삼성에서 진행한 오픈소스 컨퍼런스 리뷰입니다.  

    **강연자 : 조시행, (주)인사이너리**

---

[발표자료 링크](http://www.soscon.net/pdf/17/1610_2.pdf)

### 컴퓨팅 환경의 변화  

* 1984 - PC 등장  
* 1989 - PC 통신  
* 1994 - Desktop PC  
* 1999 - Portable PC  
* 2004 - Netbook  
* 2009 - iPhone  
* 2014 - IoT  

앞으론 Connected car 등이 나올 것이다.  

***

### Open Source is Everywhere  

78%의 회사에서 오픈소스를 사용하고 있다. 그리고 이런 회사들의 소스를 보면 30%가 오픈소스이다.  

***

### 오픈소스와 주요 취약점  

오픈소스가 늘어나면서 취약점도 많이 발견되고 있는데, 툴을 통해 발견되는 것으 10%밖에 없다.  

2015년 국내 인터넷 10대 산업 이슈 전망 중, 오픈소스 취약점에 관한 내용이 포함되기 시작  

2014년에 Heartbleed라는 OpenSSL 라이브러리에서 나타나는 버그, Shellshock이라는 bash쉘과 인터프리터에 있는 취약점이 발견되어 심각성을 느낌  

국내 금융권의 Heartbleed 영향 조사 결과를 보면 발빠르게 대처를 하였다. 이는 좋게 보고있다.  
Shellshock에 경우, 유럽에서는 발견 후 조치를 잘했지만 나머지 지역에서는 제대로 못했다.  

이렇듯 보안취약점들은 시한폭탄과 같이 언제 터질지 모르는 사항이다.  

***

### Open source security is a big deal  

Open source Licensing Compliance와 달리 Open source security의 경우 이제 막 만들어지기 시작했다.  

오픈 소스 보안취약점의 책임 : 사용자에게 있음  
(사용 코드에 경우 전담 보안 전문가와 팀이 있으므로 체계가 잘 되어있고 패치 업데이트도 정기적으로 이루어지고 있다.)  

***

### Automation Supports Compliance Teams  

* Automation tools  
* Source code  
* Binary Code  

위의 세가지 자동화 방법이 있지만, 많이는 없다.  

***

> 느낀점 : 오픈소스의 보안취약점에 대해 인식은 하고 있지만, 현실적으로 관리하기 어려운게 사실이다. 유명한 오픈소스의 경우 많은 개발자들이 참여하면서 취약점을 고치고 있지만 완벽하지는 못하다. 보안쪽에서 완벽은 있을 수 없지만 이를 효율적으로 관리하는게 필요하다.   
