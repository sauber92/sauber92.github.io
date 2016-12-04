---
layout: post
title: '[SOSCON 2016] IoTivity 기반 헬스케어 디바이스 구현사례 및 이유'
tags: [Review]
description: >  
    삼성에서 진행한 오픈소스 컨퍼런스 리뷰입니다.  

    **강연자 : 이원석,이주철, ETRI 표준연구센터**

---

[발표자료 링크](http://www.soscon.net/pdf/17/1420_2.pdf)

### 개념

스마트폰(IoTivity Stack) 등을 사용하여 OCF표준기반을 통해 디바이스(IoTivity Stack) 제어  
ETRI : 내년 상반기 즈음 최종 표준화를 목표로 하고있음  
IoTivity가 정형화가 잘 되어있어서 개발에 큰 도움이 될 것이다.  


##### 구조  

| Data Models |  
|-----------------|  
| Core Framework |  
| Transports |  

##### IoTivity Stack  

고사양 기기를 위한 Stack vs 저사양 기기를 위한 Stack  

***

### OCF Healthcare 표준  

* 피트니스/헬스케어 리소스 모델 개발  
* 피트니스/헬스케어 디바이스 스펙 개발  

***

### 헬스케어 디바이스 구현 내용 소개  

##### Trivia of IoTivity  

Wiki 사이트를 통해 개발하면 좋다.  
퍼블릭키를 등록하고 소스를 받는 것을 가장 추천! (다른 방법으로는 github을 통한 것과 홈페이지에 있는 tar를 받는 것)  
빌드는 scons로 할 수 있는데 깔끔하게 잘 된다.  

> 음...라즈베리파이에서 IoTivity를 빌드하기 위해 wiki 봤었는데 별로였음...결국 빌드도 실패!!! 근데 나머지 부분은 잘 되어 있나보다.  

사실 Wiki에는 빠진 내용이 많은데 소스 안에 들어간 정보는 굉장히 자세히 되어있다. 참고바람!! 

Product 개발을 위해선 Conformance Test Tool을 사용하는 걸 추천!  
ITT(IoTivity Test Tool), CTT(Conformance Test Tool) 등이 있다.  

**ITT** : https://wiki.iotivity.org/conformance_test_tool (공식은 아님. 보기는 CTT보다 편하다)  
**CTT** : https://workspace.openconnectivity.org/kws/test_tools (공식 툴)  

##### Healthcare data model 구현 사례 소개  

**스펙**  
HW : Arduino Due  
Host : Ubuntu PC  
IoTivity : ver 1.1.0  

* HW Platform 변경 : 아두이노 메가 -> 아두이노 듀 (메모리 부족의 원인)  
* scons script 수정 : 아두이노 라이브러리 추가, 컴파일 어파일케이션 변경(빌드와 업로드를 한꺼번에 쉽게 하기 위해)  

**API**  
C++ API, C API, CA(Connectivity Abstraction)  
고사양(리눅스)은 C++, 저사양(아두이노)은 C를 추천 / CA는 코드가 별로야 비추천  

### 이슈 - IoTivity에서의 BLE 지원  

OCF의 기본 철학 : 플랫폼에 상관없이 공통된 인터페이스로 통신이 가능하게 한다.  

하지만 실제로는...  
BLE를 지원하지 않음. Wifi/Ethernet를 선호. Smart home을 기본으로 생각하여 개발하였기 때문  
또한 IPv6를 사용하는 것을 표준으로 정했다.  
하지만 삼성과 같은 기업은 BLE를 사용한 제품 생산도 해야하므로 BLE를 지원할 수 있도록 제안  

***

### 이슈 - IoTivity에서의 아두이노 지원   

OCF의 기본 철학 : 다양한 운영체제에서 공통된 인터페이스로 가능하게 한다.  

하지만 실제로는...  
IoTivity가 아두이노를 제대로 지원하지 않음  
Security 관련 기능의 구현이 아두이노 지원코드에서 빠져 있음  
추후 아두이노에서 지원할 계획은 없다.(by Intel) 아두이노가 재밌는 플랫폼은 맞지만 제품을 개발하기 위한 보드는 아니라 생각하고 취미용이라 판단  

***

### 결론  

IoTivity가 까다롭다고 생각되지만 아직 진행 중인 오픈소스 프로젝트이므로 향후 OCF의 철학에 맞는 IoTivity가 될 것으로 예상.  

***

> 느낀점 : IoTivity가 아두이노, 라즈베리파이 등에 제대로 적용이 안되었고 이를 사용하기에 어려움이 있다는 것은 사실이다. 삼성 측에서는 ARTIK보드에서 IoTivity의 사용이 자유로울수 있게 대처한 것으로 보이지만, 기존의 시장에 나와있는 아두이노와 라즈베리파이의 지원이 제대로 안되었다는 것은 문제가 있는 것 같다. 또한 IoTivity가 IoT 디바이스에서 필요한 존재로 발전될 것같아 기대가 된다.   
