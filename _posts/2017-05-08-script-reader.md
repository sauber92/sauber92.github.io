---
layout: post
title: '[토이프로젝트] Script Reader'
tags: [Project]
description: >
  휴일동안 토이프로젝트로 만든 스크립트 리더기입니다.    
---

## 개요

<br/>
저희 연구실은 하나의 프로젝트가 완료되면 그 소개 영상을 만들어서 공개를 합니다. [유튜브](https://www.youtube.com/channel/UCyjP9QQoKEOBftVLhtNZy2Q)에 업로드하고, [연구실 홈페이지](http://mesl.khu.ac.kr/index.php?mid=page_SeTQ31)에도 게시하죠.  

지금까지(17년 5월 8일) 공개된 영상은 [SecurePi 소개 영상](https://youtu.be/jgB5OKd6EME)뿐이지만, 아직 공개를 안한 영상 두개가 더 있어요. 저도 준비하고 있는 프로젝트가 완성이 되면 이런 영상을 촬영해야 해서 미리 시나리오를 짜놓았습니다. 그런데 매번 영상 제작을 할 때 마다 불편한 점이 있었습니다.  

1. 영상에 집어 넣을 음성을 녹음하는데 있어 잡음이 섞인다.  
2. 'ㅅ, ㅌ, ㅍ'과 같은 센 소리가 나는 단어들(~~이런걸 뭐라하는지 배웠는데 기억이 안나네요~~)을 말할 때 소리가 튀는게(?) 느껴진다.  
2. 영상과 음성의 싱크를 맞추기가 어렵다.  
3. 동영상 제작 툴인 'Adobe 프리미어'를 사용해도, 음성의 편집엔 한계가 있다.  

이런 문제점들이 있었습니다. 따라서 목소리 크기, 속도, 발음 다 신경을 쓰면서 한 문장, 한 문장 녹음을 하고 편집해야 했습니다. 그러다보니 영상제작을 하는데 시간이 오래걸리고(녹음/녹화 -> 편집 -> 확인 -> 피드백의 반복) 스트레스로 다가왔습니다. 그러다 제 머리속을 스친 생각은 TTS(Text To Speech; 음성합성시스템)입니다.

***

<br/>

## 어떻게 만들까?

<br/>

제가 TTS를 맨 처음 사용했던 것은 [BKBK](http://localhost:4000/2015/12/30/haneium/)의 [소개 동영상](https://youtu.be/rTMsQeGkx3I)을 제작하면서 입니다. 이 영상을 보면 **Bring your key?! Band your key!!**라는 음성을 만드는데 TTS 서비스를 이용했습니다.  

<br/>

![](/public/img/project/scriptreader-1.png)  
*< 이 부분의 음성은 TTS 서비스, 영상은 포토샵과 iMovie를 사용하여 만들었습니다 >*  

<br/>

하지만 이때 사용한 TTS 서비스는 영어만 사용가능해서, 저희 연구실이 사용하기엔 문제가 있었습니다. 하지만 [Mingginyu](http://localhost:4000/2016/08/06/unithon-mingginyu/)를 개발하면서 **네이버 음성인식 API**를 봤던 기억이 있어서 찾아봤습니다(~~밍기뉴때 저는 임베디드 개발만 해서 '음성인식 API를 사용했다' 정도밖에 몰랐습니다~~)  

역시, [네이버 음성합성 API](https://developers.naver.com/docs/labs/tts/)가 **Clova Speech Synthesis**라는 이름으로 공개되어 있었습니다. 따라서 이번 기회에 네이버 오픈 API도 사용해보고, 개발자로서 불편한 점(영상제작의 어려움 ㅜㅠ)을 극복하자! 라는 생각에 도전했습니다.  

다음은 Github에 공개한 [Scirpt-reader 리파지토리](https://github.com/sauber92/Script-reader)의 README 내용입니다.

***

<br/>

## 개발환경  

<br/>

* Server : Node.js, Express.js  
* Client : EJS template, Bootstrap    
* Host PC
	* OS : Ubuntu 16.04 LTS  
	* IP : 163.180.142.73  
	* Port : 7000

***
<br/>

## 사용법
<br/>

1) 본 리파지토리를 클론한다. (* 터미널에서 실행)  

```
git clone https://github.com/sauber92/Script-reader.git  
cd Script-reader  
```

<br/>
2) 네이버 API를 등록한다.  

참고 링크 : [네이버 개발자 센터 > 애플리케이션 등록](https://developers.naver.com/apps/#/register?defaultScope=tts) (* 네이버 로그인 필요)  

<br/>
3) Script-reader 디렉토리 안에 *config/password.js* 파일을 만든다. (* 터미널에서 실행)  

```
(현재경로 : ~/Script-reader)  
mkdir config  
vi config/password.js  
```

<br/>
4) password.js에 네이버 Client ID와 Client Secret ID를 다음과 같이 넣어준다.  
(* Client ID, Client Secret ID는 [여기](https://developers.naver.com/docs/common/register/)를 참고하면 된다.)  

```js
// password.js
module.exports = {
  client_id : '네이버 Client ID',
  client_secret : '네이버 Client Secret ID'
}

```  

<br/>
5) Script-reader 디렉토리에서 npm install을 통해 모듈을 설치하고 실행한다. (* 터미널에서 실행)  

```  
(현재경로 : ~/Script-reader)  
npm install  
npm start  
```  

<br/>
6) 웹 브라우져에서 확인을 한다.  

URL : http://localhost:7000  

***  

<br/>

## 데모  
<br/>

[http://163.180.142.73:7000](http://163.180.142.73:7000)  

<br/>
*네이버 음성합성 API의 하루 사용량이 1000자로 지정되어 있습니다.*  
*1000자가 넘어가면 동작하지 않으니 참고해주세요.*  

***
<br/> 


## License  
<br/>

[MIT License](https://github.com/sauber92/Script-reader/blob/master/LICENSE)

***

<br/>

## 느낀점

<br/>

처음 네이버 개발자센터에 나와있는 예제를 봤을 땐 너무 쉬웠습니다. 그래서 10분도 안되서 사용해볼 수 있었죠...  
그런데 예제는 GET 방식으로, 미리 입력되어 있는 문자열을 음성으로 변경하고 있었습니다. 저는 마음대로 문자를 입력하고 쉽게 변경하고 싶었기 때문에, POST로 바꾸고 Form에서 입력받아 전달하길 원했죠. 그런데 여기서 문제가 발생하였습니다. 바로...오타!!!!!!!!! 이 프로젝트를 5월 1일에 시작하여 하루면 완성할 줄 알았는데ㅜㅜㅠ 결국 오타를 보지 못하고 뭐가 문제일지 고민하다가 3일이 지나서야 오타를 발견했습니다.  

그런데! 합성된 음성이 뛰어나진 않군요... 네이버 웨일 브라우져에서 읽어주는 음성은 자연스럽지만, 오픈 API로 공개된 것은 너무 딱딱하길래 조사해보니 웨일에서 사용하는 TTS는 아직 공개할 계획이 없다고 하네요ㅜㅠㅜㅜ 실제로 이 서비스를 사용할 일이 얼마나 많을지는 모르겠으나, 휴일동안 재밌게 진행한 프로젝트였습니다.  

저는 웹 개발자가 아닌데... 너무 재밌네요 ㅎㅎㅎㅎ
