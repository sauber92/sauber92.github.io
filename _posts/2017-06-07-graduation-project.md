---
layout: post
title: '[전자공학과 창의적설계] 전자석을 이용한 타자 연습기'
tags: [Project]
description: >
  2017-1 경희대학교 전자공학과 창의적설계(지도교수 김동한), team608의 프로젝트 포스트입니다.    
---

## 프로젝트 소개

### 프로젝트 명  
전자석을 이용한 타자 연습기   

![](https://github.com/sauber92/GraduationProject-Doc/blob/master/Documentation/Reference/TA-icon/icon.png?raw=true)  

<br/>

### 시스템 구성도  

![](https://github.com/sauber92/GraduationProject-Doc/blob/master/Documentation/Reference/Diagram/system.png?raw=true)  
<br/>

**전자석을 이용한 타자 연습기**는 컴퓨터 응용프로그램인 *Typing Assistant*와 키보드 위에 올려놓고 사용하는 *Keyboard Panel*, 장갑형태의 *FingerTip*으로 이루어져있다.  

<br/>

### 시퀀스 다이어그램  

![](https://github.com/sauber92/GraduationProject-Doc/blob/master/Documentation/Reference/Diagram/sequence.png?raw=true)  
<br/>

**과정 1,2**: 전원이 KP와 FT에 인가되면 KP와 FT은 서로 블루투스 연결을 맺는다. TA는 어플리케이션이 실행될 때 2초의 로딩시간을 거치면서 KP와 FT의 블루투스 연결이 맺어지는 것을 기다린다.  

**과정 3,4**: TA와 KP가 시리얼 연결을 맺는다.  

**과정 5,6**: TA는 입력해야 할 문자를 무작위로 생성한 후 모니터에 출력한다.  

**과정 7,8:** TA는 생성된 문자를 Character형으로 시리얼 통신을 통해 KP로 전달하고 KP는 이에 해당하는 전자석을 활성화한다.  

**과정 9,10**: KP는 TA로 부터 받은 문자를 블루투스 통신을 통해 FT으로 전달하고 FT은 이에 대항하는 전자석을 활성화한다.  

**과정 11**: 사용자가 KP와 FT의 전자석의 전자기력을 인지하고 키보드를 올바르게 입력하면 키보드 인터럽트 이벤트가 발생한다.  

**과정 12~15**: 키보드 인터럽트가 발생하면 KP와 FT의 전자석을 비활성화한다.  

**과정 16**: TA는 다시 새로운 문자를 무작위로 생성한 후 위의 과정을 반복한다.  

<br/>

***

## Typing Assistant  

### 소개  

![](https://github.com/sauber92/GraduationProject-Doc/blob/master/Documentation/Reference/Diagram/tp.png?raw=true)
<br/>

TA는 Node.js 엔진과 Chromium 브라우져을 기반으로 데스크탑 어플리케이션을 제작할 수 있는 [Electron](https://electron.atom.io/)을 사용하여 만들어졌다.  

[node-serialport 모듈](https://github.com/EmergingTechnologyAdvisors/node-serialport)을 사용하여 KP과 시리얼 통신을 할 수 있게 하였으며, 자체적으로 랜덤하게 영어 소문자 하나를 생성하고, 그에 해당하는 키보드 인터럽트 이벤트가 발생하면 다시 새로운 문자가 생성되게 하였다.  

### 개발스펙  

* IDE: WebStorm (Ver. 2016.3.2)  
* NPM: Ver 4.2.0
* Node: Ver 7.10.0  
* Electron: Ver 1.4.1  
* electron-installer-dmg: Ver 0.2.1  
* electron-rebuild: Ver 1.4.0  
* electron-winstaller: Ver 2.5.2  
* Dependencies  
	* app: 0.1.0  
	* electron-packager: 8.7.0  
	* path: 0.12.7  
	* serialport: 4.0.7  

### Release  

* Mac 버전: [dmg파일](https://github.com/sauber92/GraduationProject-TA/releases/tag/1.0.0)  
	* macOS Sierra 10.12.5에서 확인  
* Windows 버전: [exe파일](https://github.com/sauber92/GraduationProject-TA/releases/tag/1.0.1)  
	* Windows 10 Pro 1703에서 확인
	* Pre-release: 설치파일의 생성을 못해서 Pre-release 버전으로 실행파일만 배포

### Git Repository  

[https://github.com/sauber92/GraduationProject-TA](https://github.com/sauber92/GraduationProject-TA)

***

## Keyboard Panel  

### 소개  

![](https://github.com/sauber92/GraduationProject-Doc/blob/master/Documentation/Reference/Diagram/KP.png?raw=true)  
<br/>

Arduino Mega 보드와 16채널 릴레이 2개, 전자석 26개를 사용하여 구성하였다. 블루투스 모듈은 HC-06을 사용하였다.  

[SoftwareSerial 라이브러리](https://www.arduino.cc/en/Reference/softwareSerial)를 통해 FT과 블루투스 통신을 하였다.  

### 개발스펙  

* IDE: Arduino Sketch (Ver. 1.8.2)  
* Arduino Mega ADK
	* SoftwareSerail library  

### Git Repository  

[https://github.com/sauber92/GraduationProject-KP](https://github.com/sauber92/GraduationProject-KP)

***

## FingerTip

### 소개  

![](https://github.com/sauber92/GraduationProject-Doc/blob/master/Documentation/Reference/Diagram/FT.png?raw=true)  
<br/>

Arduino Uno 보드와 4채널 릴레이 2개, 전자석 8개를 사용하여 구성하였다. 블루투스 모듈은 HC-06을 사용하였다.  

[SoftwareSerial 라이브러리](https://www.arduino.cc/en/Reference/softwareSerial)를 통해 KP과 블루투스 통신을 하였다.  

### 개발스펙  

* IDE: Arduino Sketch (Ver. 1.8.2)  
* Arduino Uno
	* SoftwareSerail library  

### Git Repository  

[https://github.com/sauber92/GraduationProject-FT](https://github.com/sauber92/GraduationProject-FT)

***

## 동영상  

* Typing Assitant 유투브 영상(업로드 17년 4월 20일)  
<iframe width="560" height="315" src="https://www.youtube.com/embed/p1Mg6t1OUfo?ecver=1" frameborder="0" allowfullscreen></iframe>  

<br/>

* 전체 프로젝트 소개 유투브 영상(업로드 17년 6월 1일)  
<iframe width="560" height="315" src="https://www.youtube.com/embed/ZEWkTbEnWDc?ecver=1" frameborder="0" allowfullscreen></iframe>  

<br/>

***

## 발표자료  

### 종합설계 최종 발표자료 (17.06.01)  

<iframe src="//www.slideshare.net/slideshow/embed_code/key/6GcJ2HCHBN6JN5" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/JunyoungJung8/graduation-project-76655191" title="[Graduation Project] 전자석을 이용한 타자 연습기" target="_blank">[Graduation Project] 전자석을 이용한 타자 연습기</a> </strong> from <strong><a target="_blank" href="https://www.slideshare.net/JunyoungJung8">Junyoung Jung</a></strong> </div>

<br/>

### 창의적종합설계경진대회 발표자료 (17.07.04)  

<iframe src="//www.slideshare.net/slideshow/embed_code/key/fRsLyrmoZn0PQP" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/JunyoungJung8/team608-77488804" title="[team608] 전자석을 이용한 타자연습기" target="_blank">[team608] 전자석을 이용한 타자연습기</a> </strong> from <strong><a target="_blank" href="https://www.slideshare.net/JunyoungJung8">Junyoung Jung</a></strong> </div>

<br/>

***

## 프로젝트 관리  

[team608의 트렐로](https://trello.com/b/TO1BCMvY)  

***

## License 

* Doc: [MIT 라이센스](https://github.com/sauber92/GraduationProject-Doc/blob/master/LICENSE)  
* TA: [MIT 라이센스](https://github.com/sauber92/GraduationProject-TA/blob/master/LICENSE.md)  
* KP: [MIT 라이센스](https://github.com/sauber92/GraduationProject-KP/blob/master/LICENSE)  
* FT: [MIT 라이센스](https://github.com/sauber92/GraduationProject-FT/blob/master/LICENSE)  

***

## 제작자  

* 정준영: 경희대학교 전자공학과/컴퓨터공학과 12학번  
	* Mail: jjy920517@gmail.com  
	* Github: [https://github.com/sauber92](https://github.com/sauber92)  
	* Blog: [https://sauber92.github.io](https://sauber92.github.io)  
* 오종렬: 경희대학교 전자공학과 12학번  
	* Mail: ohjongryeol@naver.com  
	* Github: [https://github.com/JongYeolOH](https://github.com/JongYeolOH)  
* 윤상윤: 경희대학교 전자공학과 12학번  
	* Mail: sangyounyoun@naver.com  
	* Github: [https://github.com/SangyounYoun](https://github.com/SangyounYoun)  
 
 
***
 
## 느낀점  
### (17년 7월 4일 수정)  

<br/>
이 프로젝트는 **'전기적인 힘을 사용하여 사용자의 학습의 효율을 증대하고 교육을 강화시킬 수 있다'**라는 제안을 증명하기 위해 수행한 프로젝트입니다. 예를 들어 알파벳 A에 해당하는 키를 입력할 때, 기존의 타자연습기는 단순반복을 통해 A의 자판 위치를 기억할 수 있도록 학습을 시킵니다. 하지만 '전자석을 이용한 타자연습기'는 *A 자판 위에 있는 전자석* 과 *A 자판을 눌러야 할 손가락(왼손 새끼 손가락)의 전자석* 이 활성화 되어, 두 **전자석 사이의 인력을 사용자가 인지하여** 자판의 위치를 알아차릴 수 있도록 피드백을 줍니다. 이를 통해 좀 더 **효율적인 학습이 가능하다는 것을 증명**하고 싶었습니다.  

프로젝트는 성공적으로 완성이 되었고, 제안에 대한 뒷받침을 하기 위해 사용성 평가까지 시행했습니다. 모집단의 크기가 작아서 믿을만한 자료가 되지는 못하겠지만 저희 팀이 의도한대로 **'사용자에게 피드백을 준다'**라는 점과 **'HW를 같이 사용하는 것이 SW만 사용했을 때보다 효율이 높다'**라는 두 가지 점을 어느 정도 증명할 수 있었습니다.  

현재(17.07.04) 이 프로젝트는 **'경희대학교 실전문제연구단'**의 과제로 참여하게 되어 더 수정할 예정입니다. 내부적인 기능에 대한 수정보다는 외부적으로 하우징을 하는 과정을 더 깔끔하게 바꾸고 싶습니다.  

처음 종합설계(=졸업 프로젝트)의 프로젝트로서 아이디어 구상을 했을 땐 지도 교수님의 Accept을 받는 아이디어가 없어서 힘들었습니다. 하지만 계속해서 새로운 아이디어를 도출해내고, 한 학기 내에 구현 가능한지를 판단하다보니 좋은 아이디어로 진행을 할 수 있었습니다.  

일단 아이디어가 결정이 난 후, 설계에 주로 초점을 뒀습니다. 다른 어떤 팀보다 설계에 오랜 시간을 두고 깔끔한 시나리오를 만들 수 있었고 오픈소스 / 오픈하드웨어로 프로젝트 공개를 하고 싶었기 때문에, 들여쓰기 규칙부터 변수/함수명 짓는 규칙까지 정하여 팀원들과 공유하였습니다.  

저는 주로 Typing Assistant의 개발을 하였습니다. **일렉트론(Electron)**을 사용해본 경험이 있었기에 (아직 미완성 프로젝트인 Sparkling에서 일렉트론을 처음 사용하였다.) 쉽게 접근 할 수 있었고, 그 과정에서 일렉트론 오픈소스에 기여를 할 수도 있었습니다. ~~작은 오타를 수정했을 뿐입니다..~~ 그리고 오늘 일렉트론 조직으로부터 Invite를 받기도 하였습니다!! (이제 일렉트론 개발자라 불릴 수 있는 건가?!)  

일렉트론은 쉽게 데스크톱 어플리케이션을 개발할 수 있다는 점에서 큰 매력이 있고, 또 그 어플리케이션이 운영체제에 상관없이 어디에서나 실행될 수 있도록 할 수 있다는 장점이 있습니다. 앞으로도 일렉트론을 사용한 많은 프로젝트를 진행해 보고 싶습니다.  

Keyboard Panel과 FingerTip의 개발에서는 주로 팀원들에게 조원을 주는 역할을 하였습니다. 가장 기억에 남는 것은, 전송받은 문자를 판단하는 과정에서 **'바이너리 서치'**를 사용하도록 조언한 것입니다. KP의 경우 시리얼 통신을 통해 전송받은 문자가 26개의 알파벳 중 어느 것인지 찾고 해당 전자석을 활성화 시켜줘야 합니다. 이때 if-else문 26개를 통해 탐색하는 코드를 바이너리 서치로 수정하였습니다.  

종합설계에서는 우수팀으로 선정되었고 그 결과 실전문제연구단 과제로도 선정되어 학교의 지원도 받을 수 있었습니다. 아직 더 발전시킬 수 있는 아이디어니깐 앞으로 더 발전시킬 수 있도록 하겠습니다.  
