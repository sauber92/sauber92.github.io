---
layout: post
title: '[SOSCON 2016] IoTivity Bigpicture'
tags: [Review]
description: >  
    삼성에서 진행한 오픈소스 컨퍼런스 리뷰입니다.  

    **강연자 : 정명기, 삼성전자 Software R&D center**

---

[발표자료 링크](http://www.soscon.net/pdf/17/1330_2.pdf)

### Overview  

Resource는 공통적으로 가져야하는 Property, 타입별로 고유하게 가져야 하는 Attribute로 구성  
이러한 Resource가 여러개 포함되어 있는 Collection. 이것들을 통해 다양한 Things를 정의  

***

### Features  

* Base layer  
* Service Layer  
* Cloud Interface    

OCF Server : 작은 Things  
OCF Client : 모바일이나 PC와 같이 Server를 제어  

**CoAP Messaging**이라는 표준을 사용하여 메세지를 주고받음  
Application 상에서는 Reliable/Unreliale Message Transmission을 지원 (Reliable은 메세지 보내면 ACK, Unreliable은 응답이 없으면 말고~)  
토큰.....알아두면 코드 분석이 좋을것이다. IoTivity는 토큰을 통해 메세지를 주고받으므로....  
Piggybacked Responses 같은게 IoTivity에 적용되어있다.  

**Block-wise Transfer**가 적용되어 있음.  
IoTivity를 실행해보면 Block-wise 메세지가 보일텐데, 계속 체크하고 있다는 것이다.  

**Resource Directory!!**  
저사양 디바이스가 제한이 많으므로, Directory의 역할을 하는 디바이스에 디바이스 정보를 저장해두고, 이를 다른 고사양 디바이스에서 사용가능하게 할 수 있다. 이는, 같은 공간에 존재하는 디바이스 뿐만 아니라, Cloud를 통해 리모트 디바이스도 가능하다. 이때 보안에 신경쓸 수 있게 OAuth Provider를 이용하고 Account Server를 두어 관리한다.  

**Message Switching!!**  
라우팅을 어플리케이션 레벨에서 가능하게 하여, 서로 다른 형식의 디바이스를 연결  

**Security!!**  
Ownership을 얻은 Admin 디바이스가 존재하고, 다른 디바이스들은 이 Admin 디바이스에게 권한을 요청하여 어세스할 수 있게 한다.  

**Resource Container!!**  
다른 프로토콜을 사용하는 Things와의 연결  

**Scene Manager!!**  
여러 디바이스를 하나의 집합으로 뭉치게 하여, 상황을 지정하여 한꺼번에 제어할 수 있도록 한다.  
ex) 영화감상모드, 독서모드 등을 설정하고 조명이나 티비등을 한꺼번에 제어  

**Notification!!**  
ex) PC와 모바일을 같이 쓴다고 했을 때, 모바일에 오는 알람을 PC에서도 받을 수 있게..  

**Simulator!!**  
Server나 Client를 시뮬레이션 할 수 있도록 만들어둠  

> 현재 IoTivity는 계속 업데이트 중이며 Wiki도 함께 업데이트되고 있으니, 살펴보면 될 것 

***

> 느낀점 : IoTivity의 특징을 빠르게 설명하다보니 따라가기 힘들었다. 이미 IoTivity가 없더라도 이러한 역할은 다양한 디바이스에서 사용가능하고 개발 가능했다. 하지만 IoTivity를 통해 정형화 된다면 좀 더 편하고 빠른 개발이 가능할 것은 기대된다. 최근에 라즈베리파이에 IoTivity를 빌드하기 위해 IoTivity Wiki를 살펴본 경험이 있다. 하지만 자세한 설명이 되어 있지 않아 많이 실망했다. 아직 초기 단계이니 더 발전할 것이라 믿는다.  
