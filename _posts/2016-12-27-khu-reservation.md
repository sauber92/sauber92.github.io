---
layout: post
title: '[웹 분석] 경희대 장소예약시스템의 문제점'
tags: [Study]
description: >
  경희대학교의 "장소예약시스템" 웹페이지를 이용하다 겪은 문제점을 포스팅합니다.
---

12월 31일, [넥스터즈(NEXTERS)](http://teamnexters.com/)는 10기 활동을 시작합니다. 이 날 모임에서 사용할 장소 예약을 위해 [경희대학교 장소예약시스템](https://khuis.khu.ac.kr/java/jsp/hjss/reservation/index.html)을 이용해보았습니다. 국제캠퍼스 학생인 저는 이 장소예약시스템을 사용해 본 경험이 없는데, 서울캠퍼스 학생들은 자주 이용한다고 합니다.  

하지만 제가 사용을 해본 결과, 처음 사용한 사람은 이용하기 어려울 것 같습니다. 먼저 UX(User Experience)면에서 굉장히 안좋습니다. 그리고 일시적인 문제인지...계속 이러한 문제가 있는지는 모르겠으나, 기능적으로도 치명적인 문제가 있습니다. 바로 "장소 검색"을 시도했을 때, 새로운 창이 생성되면서 무한 로딩에 빠진다는 것입니다. 그리고 이 무한 로딩에 빠지게 되면 기존 페이지의 작동이 멈춥니다. 어떠한 버튼을 눌러도 작동하지 않고, 새로고침도 안됩니다. 기존에 정보를 입력한 것이 있다면 저장도 안되고 다 날려버리는 것이죠....이러한 오류때문에 장소예약을 하는데 너무 많은 시간을 소모했네요 ㅜㅜㅜㅠ  

***

[경희대학교 장소예약시스템(https://khuis.khu.ac.kr/java/jsp/hjss/reservation/index.html)](https://khuis.khu.ac.kr/java/jsp/hjss/reservation/index.html) 일단 링크를 보니 [종합정보시스템(https://khuis.khu.ac.kr/)](https://khuis.khu.ac.kr/) 서버를 그대로 사용하는 거 같군요  


접속을 하면 다음과 같은 화면이 나옵니다. 왼쪽의 선택메뉴와 오른쪽에 해당메뉴의 대한 내용으로 구분되어 있군요  
![](/public/img/study/khureservation-1.png)  

***

저는 장소예약을 하기 위해 "예약신청" 메뉴를 들어갔고, 제 정보를 입력하여 접속을 하였습니다.  
![](/public/img/study/khureservation-2.png)  
![](/public/img/study/khureservation-3.png)  

***
  
그리고 등장한 예약신청 페이지!!! 현재는 제가 예약한 장소목록이 나오지만, 처음엔 아무것도 없습니다.  
![](/public/img/study/khureservation-4.png)  

***
 
여기서 새로운 장소예약을 하기 위해선 어떻게 해야할까요???  
![](/public/img/study/khureservation-5.png)  

***
  
제가 위 캡쳐에 써둔 거처럼 중간에 있는 "신규신청" 버튼을 눌러야 합니다. 장소검색을 하시면 다음과 같이 새로운 창이 뜨면서 무한로딩을 합니다.  
![](/public/img/study/khureservation-6.png)  

***
 
위에서 말한 거처럼, 이렇게 무한로딩에 빠지게 되어 기존 페이지로 돌아가면 기존 페이지가 어떠한 작동도 하지 않는다는 것을 볼 수 있습니다. 이는 종합정보시스템을 통해 장소예약시스템을 접속하면, 종합정보시스템도 똑같이 작동을 하지 않습니다. 아마 같은 서버를 사용하고 있는데, 그 서버에서 장소검색을 하지 못했기 때문인 것으로 파악됩니다.  

***

자, 이렇게 신규신청을 하게 되면 다음과 같은 창이 뜹니다.  
![](/public/img/study/khureservation-7.png)  

***
  
캡쳐를 보시면  

1. 시설구분, 행사구분  
2. 행사정보
3. 장소정보

위의 세가지 사항으로 구분되어 있는 것을 볼 수 있습니다. 저는 여기서 1번, 2번만 입력을 하고 3번은 입력할 게 없길래 곧장 "저장" 버튼을 눌렀더니,
![](/public/img/study/khureservation-8.png)  

***
  
선택된 장소정보가 없다는 경고가 뜨는군요... 3번의 장소정보를 입력하기 위해선 체크박스의 선택이 필요합니다.  
![](/public/img/study/khureservation-9.png)  

***
  
그런데 여기도 똑같은 장소검색 버튼이 있내요?!?!?! 이거도 역시 건들면 안됩니다!!! 근데 다른 정보를 먼저 입력하려고 해도,  
![](/public/img/study/khureservation-0000.png)  

***
  
안되네요......하지만 컴퓨터공학도로서 여기서 포기하면 안되죠
![](/public/img/study/khureservation-10.png)  
![](/public/img/study/khureservation-11.png)  

***
  
개발자도구로 확인해보니, 텍스트 입력창이 **readonly** 속성이 걸려있네요. 여기선 저희 넥스터즈의 10기 CTO님이 도움을 주셨는데 저 readonly 속성을 지워보라고 하시더라구요  
![](/public/img/study/khureservation-12.png)  

***
  
오~지우니까 입력이 가능해져요. 역시 CTO님 짱짱맨....bbb  

근데 여기엔 어떤걸 입력해야 할까요? 다행히 장소예약 홈페이지에서 [장소사용신청현황](https://khuis.khu.ac.kr/java/servlet/controllerHjss?action=51)을 보시면 **장소코드**가 나옵니다. 이걸 입력하면 되겠죠????  
![](/public/img/study/khureservation-13.png)  

***
  
하지만 예상과 달리 여전히 사용장소를 선택하라는 경고가 뜹니다.  
![](/public/img/study/khureservation-0001.png)  

***
  
다시 개발자도구를 확인하니 input type이 hidden으로 되어 있는 것이 두개가 있군요  
![](/public/img/study/khureservation-14.png)  

***
  
이 속성을 모두 display로 바꾸면 텍스트 입력창이 나오고, 아까 찾은 장소코드를 넣을 수 있습니다.  
![](/public/img/study/khureservation-15.png)  
![](/public/img/study/khureservation-16.png)  

***

이렇게 저는 장소예약에 성공하였습니다.  
![](/public/img/study/khureservation-17.png)  

***
  
실제로 이 방법을 쓰기 전에 브라우져에 문제인지, OS의 문제인지를 확인하기 위해 인터넷익스플로러, 사파리, 웨일 브라우져를 통해 확인을 해보았고, 윈도우즈 PC 환경에서도 확인을 하였으나 인터넷익스플로러의 경우, 제 정보를 입력하고 로그인 하는 것부터 안되드라구요....  

다른 방법으로 장소예약시스템을 사용하는 방법이 존재할 수 있습니다.(서울캠 학생들은 잘 사용중이니까요) 그러나  

1. 원하는 기능을 사용하기 위해 어떤 버튼을 눌러야 할지 모르겠으며  
2. 주요 기능은 작동을 하지 않고 오류가 발새하고  
3. 오류가 발생하면 기존 입력 정보가 모두 날라가는..

이러한 문제가 있는 것은 심각하다고 생각합니다. 학교에서 빨리 확인하고 고쳐주었으면 좋겠습니다.  
