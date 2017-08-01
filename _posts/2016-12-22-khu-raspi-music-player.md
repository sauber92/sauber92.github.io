---
layout: post
title: '[KHU-Unix System Programming] Raspberry Pi Music Player'
tags: [Project]
description: >
  이 프로젝트는 경희대학교 컴퓨터공학과 유닉스시스템프로그래밍 수업의 설계 프로젝트로 만들었습니다.
---

## 0. 개요

Linux server와  Raspberry Pi의 TCP Socket 통신을 통한 음악 플레이어  

* 조원  
	* 컴퓨터공학과 오xx
	* 컴퓨터공학과 장xx
	* 컴퓨터공학과 하xx
	* 컴퓨터공학과/전자전파공학과 정준영

***

## 1. 프로젝트 내용

본 프로젝트는 Linux서버와 Raspberry Pi의 Socket 통신을 통해 음악 파일을 전달 받고, IR Remote Controller를 사용하여 음악의 재생이 가능하도록 한 “라즈베리파이 뮤직 플레이어”이다. Raspberry Pi에는 LCD 모듈과 IR 센서가 연결되어 있으며 IR Remote Controller의 Play 버튼을 누르게 되면, LCD 모듈의 글씨가 변하면서 노래가 재생된다.  

### Server  

|:----:|:------:|
| OS | Ubuntu 12.04.05 LTS |   
| Program Language | C     |  

### Cleint  

|:----:|:-------:|
| Device | Raspberry Pi 3 |
| OS | Raspbian GNU/Linux 8 |
| LCD Module | QAPASS 1602A |
| IR Sensor | CHQ 1838 |
| Speaker | Hamburger mini speaker |
| Program Language | C |  

Client에 전원이 인가되면 “Hello USP”라는 문구를 LCD Module에 출력한다. 이 후, Server로 부터 TCP Socket 통신을 통해 음악 파일(example.wav)를 받게 되면, IR Remote Controller의 신호를 기다린다.  

![](/public/img/project/usp-1.png)  
![](/public/img/project/usp-2.png)  
![](/public/img/project/usp-3.png)  

***  

## 2. 실행결과 

<iframe width="100%" height="315" src="https://www.youtube.com/embed/IBv3-7qRPxQ" frameborder="0" allowfullscreen></iframe>

***

## 3. Github 저장소

[suaber92/khu_USP_RaspPiMusicPlayer](https://github.com/sauber92/khu_USP_RaspPiMusicPlayer)
