---
layout: post
title: '[대학생 연합 해커톤 UNITHON 5TH] KOK - 프로귀찮러를 위한 지출관리 시스템'
tags: [Project]
description: >
  UNITHON 5TH(2017.07.25~27)에 참가한 팀 UNI77의 프로젝트입니다.    
---

## 프로젝트 소개  

### 프로젝트 명: KOK 
<br/>
![](/public/img/project/kok-1.png)

<br/>
### 발표자료  
<div>
<iframe src="//www.slideshare.net/slideshow/embed_code/key/nQ3jJEfABYIkfK" width="100%" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/JunyoungJung8/unithon-5th-kok" title="[UNITHON 5TH] KOK - 프로귀찮러를 위한 지출관리 서비스" target="_blank">[UNITHON 5TH] KOK - 프로귀찮러를 위한 지출관리 서비스</a> </strong> </div>
</div>

<br/>
### 시연영상
<div>
<iframe width="100%" height="315" src="https://www.youtube.com/embed/80MWKoK_LUw?list=PLTj4ip-QW96vjFo_UbMcP9qv7Ne7OVDKL" frameborder="0" allowfullscreen></iframe>
</div>

<br/>
### Github Repository  
<br/>
[https://github.com/sauber92/unithon7team](https://github.com/sauber92/unithon7team)

***

## 느낀점
<br/>
작년 유니톤에 참가한 후, 1년 뒤 다시 유니톤에 참가하였습니다. 작년엔 IoT 분야가 있어서 임베디드 개발자로 참가하였지만 올해 행사에는 IoT가 사라졌더군요 :-( [(UNITHON 3RD 게시물 바로가기)](https://sauber92.github.io/2016/08/06/unithon-mingginyu/)  
그래서 이번 유니톤의 참가는 고민됐습니다. IoT / Embeded 개발이 아니면 제가 할 수 있는 것은 웹인데 빠르게 개발해야하는 해커톤에서 잘할 수 있을지 걱정됐습니다.  

지난 1년 동안 서버, 클라이언트를 가리지않고 웹 공부를 하며 프로젝트를 해왔지만, 제 전공은 웹이 아니니깐요... 하지만 한편으로는 기대도 됐습니다. 1년 동안 넥스터즈 활동을 하면서 익숙해진 팀원들과는 좋은 결과물을 내고 있는데, 처음 만나는 사람들과도 팀웤을 이루며 프로젝트 수행을 할 수 있을지 궁금했습니다.  
<br/>

![](/public/img/project/kok-2.jpeg)
<p style="text-align: center;font-style:italic;"> < 해커톤때 발휘하는 집중력을 평소에도 발휘하면 크게 성공할 텐데... > </p>  


<br/>
저희 팀은 다른 팀보다 아이디어가 늦게 나온 편이였습니다. 만족스러운 아이디어가 없어서 다른 팀이 이미 개발을 시작하였을 때도 아이디어 회의를 하고 있었죠. 하지만 힘들게 나온 아이디어는 재밌으면서 실용적인! 대상을 노려볼 만한 아이디어였습니다.  

**KOK**은 웹앱 형태의 서비스로서 기존의 가계부 어플이 소비 항목과 시간, 지출액을 하나하나 적는 방면, KOK은 카드를 긁은 후 사진만 찍으면 되는 서비스입니다. 카드를 긁은 시간과 가장 유사한 시간에 찍힌 사진을 자동으로 매칭해주기 때문이죠.  
<br/>

![](/public/img/project/kok-6.png)
<p style="text-align: center;font-style:italic;"> < 간단 간단, 사진버튼만 콕 누르세요 > </p>  

<br/>
이때 찍힌 물품이 무엇인지에 대해서는 **Amazon Rekognition API**를 사용해서 자동으로 판단합니다. 

> Recognition이 아니라 Rekognition으로 정한 아마존의 의도가 궁금하다.  
<br/>

![](/public/img/project/kok-5.jpeg)
<p style="text-align: center;font-style:italic;"> < KOK의 시스템 구성도 > </p>  

<br/>
이 외에도 KOK은 **AWS의 EC2와 S3**를 통해 배포하며, **Naver OAuth Login API**를 통한 로그인과, **은행권공동플랫폼의 계좌조회 API**를 통해 사용자의 계좌정보를 받습니다. 그리고 이 사용자 정보는 **Firebase**에 저장됩니다. 

> 처음엔 농협핀테크 API를 써서 계좌정보를 가져오려했지만, 농협에서는 기업과 기관에만 API 사용권한을 부여하였기 때문에 해커톤에서 사용하기엔 무리가 있었다. 힘들게 나온 아이디어를 변경할 뻔했지만, 다행히 '이러한 API를 사용할 계획이다'라고 발표하면 된다는 운영측의 배려 덕분에 주제를 바꾸지 않고 진행할 수 있었다.  

<br/>
하지만 프로젝트의 완성은 할 수가 없었습니다. Frontend와 Backend 사이의 연결을 하지 못했으며, 웹앱에서 디바이스의 카메라 접근을 하지못하였죠... 가장 핵심적인 부분을 개발하지 못해서 아쉬웠지만..!  
<br/>

![](/public/img/project/kok-3.jpeg)
<p style="text-align: center;font-style:italic;"> < 무려 AWS 특별상!!! > </p>  
<br/>

![](/public/img/project/kok-4.jpeg)
<p style="text-align: center;font-style:italic;"> < UNI77 팀 모두 고생하셨습니다 > </p>  

<br/>
KOK은 아마존웹서비스 특별상을 수상하였고 전제민 PS팀 리더님께서 역삼역에 있는 아마존웹서비스 코리아에 초대도 해주셨습니다 bbbbb 빨리가서 구경해보고 싶네요.  

> 리더님 멋져요!

<br/>
이 외에도 유니톤 행사를 통해 [아마존 웹 서비스 인 액션](http://book.naver.com/bookdb/book_detail.nhn?bid=11983439), [더부스 맥주](http://thebooth.co.kr/), 안대, 귀마개 같은 사은품도 받을 수 있었습니다. 처음 걱정과 달리 너무 좋게 행사를 마칠 수 있어서 기뻤습니다.

> 다시는 해커톤 안하겠다고 다짐했는데 이렇게 상도 받고 사은품도 받으면 또 고민되잖아...ㅎㅎㅎㅎㅎ