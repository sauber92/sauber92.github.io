---
layout: post
title: '[대학생 연합 해커톤 UNITHON 3RD] Mingginyu(밍기뉴)'
tags: [Project]
description: >
  이 프로젝트는 2016년 7월 30일부터 31일까지 진행된 해커톤, UNITHON에 참가하여 완성한 프로젝트입니다.
---

[Github Repository](https://github.com/Nexters/mingginyu)  

***

<iframe src="//www.slideshare.net/slideshow/embed_code/key/LzOtRphboungv" width="100%" height="714" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/JunyoungJung8/unithon-3rd-mingginyu" title="[대학생 연합 해커톤 UNITHON 3RD] Mingginyu_서비스 소개서" target="_blank">[대학생 연합 해커톤 UNITHON 3RD] Mingginyu_서비스 소개서</a> </strong> </div>

***

<iframe src="//www.slideshare.net/slideshow/embed_code/key/lAH7ULRKC4AoWS" width="100%" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/JunyoungJung8/unithon-3rd-mingginyuppt" title="[대학생 연합 해커톤 UNITHON 3RD] Mingginyu_ppt" target="_blank">[대학생 연합 해커톤 UNITHON 3RD] Mingginyu_ppt</a> </strong> </div>

***

첫 해커톤에 나가서 수상까지한 프로젝트입니다. 해커톤의 팀은 제가 활동 중인 [Nexters(넥스터즈)](http://teamnexters.com/) 사람들과 연결되었고 저희는 IoT 개발을 하기로 하였습니다.  

![](/public/img/project/mingginyu-4.jpeg)

저는 팀에서 임베디드 개발자로 역할을 부여받아, 아두이노와 라즈베리파이에 센서를 연결하여 웹서버(MS Azure, ~~발표 피피티에는 AWS로 되어있는데 잘못되었습니다~~)로 전달하는 것을 개발하였습니다. 그리고 웹 클라이언트를 라즈베리에 연결된 모니터를 통해 보여주는 것을 하였습니다.  

아두이노는 토양수분센서를 연결하여 라즈베리파이에 센서 측정값을 전달하게 하였고, 라즈베리파이는 온습도센서, 초음파센서의 센서 측정값과 아두이노에서 받은 토양수분센서 측정값을 phthon으로 Azure에 보냈습니다. 아두이노만 토양수분센서를 사용한 이유는 라즈베리파이가 아날로그 핀을 사용할 수 없는데, 토양수분센서가 아날로그 핀을 사용하기 때문입니다.

***

**Mingginyu(밍기뉴)**는 스마트 화분입니다. 하지만 기존의 스마트 화분과의 차이점은, 기존 스마트화분이 *자동으로 물을 주는 기능*을 중요시하는 반면, 밍기뉴는 *사용자와 교감하는 스마트화분*입니다.  

밍기뉴는 평소엔 오늘의 날씨정보만을 보여주지만, 사용자가 가까이 다가가면 현재 화분 속 토양에 수분량을 그림과 감정표현을 통해 알려줘 사용자에게 물 주는 시기를 알려줍니다. 또한 식물을 몇일 동안 키웠는지, 현재 방 안의 온도와 습도는 어느정도인지 파악이 쉽도록 UI가 구성되어 있습니다.  

![](/public/img/project/mingginyu-2.jpeg)

또한, 가까이 다가간 상태에서 밍기뉴에게 인사를 하면 이를 인지하여 대답을 해줍니다.  
~~하지만 이 기능은 완벽하게 작동하지 않습니다ㅜㅜㅠ~~  

![](/public/img/project/mingginyu-3.jpeg)  

***

<div>
<iframe width="100%" height="315" src="https://www.youtube.com/embed/RAKVhlfUBJU" frameborder="0" allowfullscreen></iframe>
</div>