---
layout: post
title: '[KHU-Embedded System Design] Avoid Balls!!!'
tags: [Project]
description: >
  이 프로젝트는 경희대학교 전자전파공학과 임베디드시스템설계 수업의 기말 프로젝트로 만들었습니다.
---

## 0. 개요

Atmega128과 HC-06 Bluetooth module을 사용한, 안드로이드 스마트폰 게임

* Hardware Embedded board  
	* 개발보드 : Atmega128  
	* 개발언어 : C, Assembly  

* Android Smart phone  
	* Android version : Android 6.0 Marshmallow  
	* Tool : App Inventor

***

## 1. 설계 내용  

### 1-1. 기능 설명  

Atmega128에 UART1에 해당하는 PD2(RXD1), PD3(TXD1) 포트에 HC-06 Bluetooth module을 연결한다. 또한, 키보드와 LCD도 연결한다. 이렇게 구성된 임베디드 보드는 안드로이드 스마트폰 어플리케이션과 블루투스 통신을 한다. 임베디드 보드의 키패드 "2, 8, 4, 6"번 키는 각각 "위, 아래, 왼쪽, 오른쪽"에 맵핑되어, 안드로이드 어플리케이션에 전달되고 안드로이드에선느 이를 이용하여 공 피하기 게임이 진행된다.  

### 1-2. Embedded Board  

1. LCD : 기본 정보(개발자 이름, 어플리케이션 명) 출력  
2. 키패드 : "Avoid Balls!!!" 에서 유저를 움직일 수 있는 방향키  
3. HC-06 : 블루투스 모듈. UART1을 통해 Atmega128이 안드로이드 스마트폰과 블루투스 통신  

![](/public/img/project/esd-1.png)  

### 1-3. App Inventor

![](/public/img/project/esd-2.png)  
![](/public/img/project/esd-3.png)

***  

## 2. 실행결과 

<div>
<iframe width="100%" height="315" src="https://www.youtube.com/embed/-eO0VZtBdYg" frameborder="0" allowfullscreen></iframe>
</div>

***

## 3. Github 저장소

[suaber92/khu_EmbeddedSystemDesign](https://github.com/sauber92/khu_EmbeddedSystemDesign)
