---
layout: post
title: '[토이프로젝트] Smart Farm 모니터링 시스템 (feat. NODEMCU, Firebase)'
tags: [Project]
description: >
  외주를 맡아서 진행한 프로젝트입니다. NODEMCU-ESP8266 보드와 구글 Firebase를 사용하였습니다.  
---

## 프로젝트 소개  

### 프로젝트 명: Smart Farm 모니터링 시스템   

<br/>
### Github Repository  
<br/>
[https://github.com/sauber92/toyproject-firebase2esp8266](https://github.com/sauber92/toyproject-firebase2esp8266)  

<br/>
### System Architecture  
![](/public/img/project/toy-1.png)  
![](/public/img/project/toy-2.png)  
![](/public/img/project/toy-3.png)  

각 농장은 여러 대의 Node devices를 가지고 있고, 각 Device는 FARMID와 EQUIPID를 가지고 있습니다.  
동작은 **1. 디바이스 조작**과 **2. 디바이스 모니터링**으로 구분됩니다.  

Node device는 세 가지 Task(*getDataTask, runCommnadTask, readSensorTask*)가 Multitasking하며 동작하고, Firebase로 부터 값을 Read/Write하며 동작합니다.  

<br/>
### 개발 환경  
* Node device  
	* MCU: ESP8266  
	* Sensor: 온습도 센서(DHT11)  
	* 사용 라이브러리  
		* [Firebase-Arduino](https://github.com/FirebaseExtended/firebase-arduino)  
		* [ArduinoJson](https://github.com/bblanchon/ArduinoJson)  
		* [DHT11](https://github.com/beegee-tokyo/DHTesp)  

![](https://github.com/sauber92/toyproject-firebase2esp8266/raw/master/README/esp8266_img.jpg){: width="80%"}{: .center}  

<br/>

* Monitoring Webapp
	* 사용 라이브러리
		* firebase.js (ver3.6.9)  
		* jQuery (ver2.1.1)  
		* Material Design (ver0.100.2)  
	* 테스팅 디바이스  
		* iPhone XS  
		* iPhone 6  

![](https://github.com/sauber92/toyproject-firebase2esp8266/raw/master/README/webapp_img.png){: width="50%"}{: .center}  

***  

## 느낀점  
<br/>  
이 프로젝트는 2018년 12월에 진행하였으며, 수산양식분야에 ICT 기술 도입을 원하는 회사에서 **'수질 관리 모니터링 시스템'**의 필요성으로 인해 외주를 부탁하였고 진행하게 되었습니다.  

> 석사 과정 중에 무슨 외주 프로젝트야~라고 넘기려 하였으나...  
> ~~블로그 업데이트도 못하도록 바쁜데...~~  

설명을 들어보니 몇 시간 투자하면 금방 만들 수 있을거 같았고, IoT 개발 보드(e.g., 아두이노, 라즈베리파이)와 Firebase의 연동을 한번 시켜보고 싶어서 도전하게 되었습니다.  

처음 요구사항은 **아두이노에 Ethernet Shield를 사용하여 Firebaes와 연동**하는 프로젝트였으나, 아두이노 Ethernet shield가 SSL 통신을 지원하지 않으므로 Firebase와 연결하기엔 추가 작업이 많아질 것 같았습니다.  

그래서 **NODEMCU-ESP8266 보드와 Firebase의 연동**으로 수정하여 프로젝트를 진행하였고, 추가적으로 간단한 웹앱도 만들어 데모를 할 수 있게 하였습니다.  

결과적으로 큰 시간을 할애하지도 않고(이틀!!!) 재밌게 개발할 수 있었습니다.  