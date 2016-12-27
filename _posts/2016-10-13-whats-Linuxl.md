---
layout: post
title: 'Linux 사용법 & Raspberry Pi 사용하기 (for Club. MARO_KHU Univ.)'
tags: [Study]
description: >
  이 문서는 경희대학교 전자∙전파공학과 **학술동아리 마로**의 교육 자료입니다.  
  리눅스의 간단한 소개와 기초명령어를 알아보고, 나아가 **라즈베리파이** 를 통한 임베디드 시스템 개발의 도움이 되고자 제작하였습니다.  
---

## 0.1 Linux란?

운영체제는 컴퓨터 하드웨어 자원을 제어하는 역할을 수행하며, 커널과 시스템 프로그램으로 구성되어 있다. 커널이란 항상 수행되는 프로그램으로서 컴퓨터의 하드웨어 자원들을 제어하고 다른 프로그램이 실행될 환경을 제공한다. 리눅스 커널은 리누스 토발즈라는(Linus Torvalds) 핀란드 대학생이 1991년 유즈넷 뉴스그룹에 미닉스(Minix)를 대체하는 커널의 초기 버전을 발표하면서 처음으로 그 모습을 세상에 드러냈다 [1](http://www.cs.cmu.edu/~awb/linux.history.html).  
엄밀한 용어로서 리눅스는 커널을 의미하지만, 리눅스 커널 그 자체만으로는 시스템을 구성할 수 없기 때문에, 흔히 리눅스 커널과 시스템 프로그램으로 구성된 운영체제를 리눅스라고 부른다.  
다른 운영체제와 차별되는 리눅스의 특징은 다중작업, 다중 사용자 시스템이라는 것과 어느 누구도 리눅스를 소유하지 않는 오픈 소프트웨어라는 점, 다중 스레드가 가능한 점 등을 들 수 있다 [2](http://www.debian.org/releases/stable/armel/ch01s02.html.ko).  

***

## 0.2 Linux의 종류

![리눅스 종류](http://cfs14.tistory.com/image/36/tistory/2009/07/25/12/37/4a6a7de60be48)  

GNU/Linux라고 불리게 된 시스템의 개발은 1984년에 시작되었으며, 자유 소프트웨어 재단(FSF)은 유닉스와 유사한 운영체제의 개발을 시작하면서 그 이름을 GNU라고 했다. 이후 GNU/Linux를 수정한 약 300개의 배포판이 등장하였으며, 대표적으로는 Debian과 Fedora가 있으며 이로부터 파생된 Ubuntu, Kali linux, RedHat 등이 있다.  
  
  
* **Debian** : 데비안 프로젝트에서 만들어 배포하는 공개 운영체제로서 패키지 매니저인 apt등의 사용으로 패키지 설치 및 업그레이드가 간편하다는 특징이 있다.  
* **Ubuntu** : Debian GNU/Linux에 기초한 컴퓨터 운영체제로서 Debian과 견주어 볼 때 사용자 편의성에 많은 초점을 맞추고 있다. 시스템 관리 작업에서 sudo 도구를 사용하여 사용자가 자신의 암호를 이용해 시스템 관리 권한을 얻어 작업을 진행할 수 있도록 인증한다. 따라서 관리 작업을 하기 위해 root 사용자의 암호를 따로 만들지 않아도 되고, 여러 사용자가 관리를 위해 root 암호를 공유함으로써 생길 수 있는 잠재적인 보안문제를 예방할 수 있는 특징이 있다.  
* **Fedora** : 페도라 프로젝트가 이끌고 레드햇의 후원으로 만들어 배포되는 운영체제이다. 6개월 간격으로 새로운 버전이 배포되며 지원기간은 각 버전마다 13개월씩으로 상대적으로 짧은 교환주기를 갖는 특징이 있다. 또한 리눅스의 여러 보안 기능을 종합한 SELinux를 내장하고 있다.  


> 마로 너네 지금 뭔 개소리인가 하고 있지? 위에꺼 다 몰라도 괜찮아~ 그러면 나는 왜 저걸 써놨을까?? 데비안, 우분투 라는 리눅스 커널을 알기 위해서야 이건 뒤에서(2.1장) 더 알아보자

***

## 1.1 Linux 시스템 구조

![Linux System Architecture](http://cfile21.uf.tistory.com/image/1702053A50573F2818EA4E)

***

## 1.2 Linux 파일시스템

![Linux File System](http://cfile29.uf.tistory.com/image/255A113E54D31E23139F6B)

***

## 1.3 Linux 기본 명령어

리눅스는 기본적으로 [CUI](https://ko.wikipedia.org/wiki/%EB%AA%85%EB%A0%B9_%EC%A4%84_%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4)기반이다.  
리눅스 사용시 자주 사용하는 간단한 명령어는 다음과 같다.  
[참고 사이트](http://www.mireene.com/webimg/linux_tip1.htm) <del>솔직히 이 사이트 별로임. 걍 구글에 하나씩 쳐봐</del>

| 명 령 어 | 사 용 법 |  
|--------|---------|
| **login** | 사용자 인증과정  |
| **passwd** | 패스워드 변경 |  
| **ls**     | 파일 리스트 보기 |
|            | 예) ls -a : 숨김 파일 보기  ls -l : 파일 리스트 자세히 보기 |
| **cd**     | 디렉토리 변경 |
| **cp**     | 파일 복사 |
|            | 예) cp a.old a.new : a.old 라는 파일을 a.new 란 이름으로 복사 |
| **mv**     | 파일이름(rename) / 위치(move) 변경 |
|            | 예1) mv a.old b.new : a.old 라는 파일을 b.new 란 이름으로 변경 |
|            | 예2) mv /old/a /new : /old 디렉토리 안의 a 라는 파일을 /new 디렉토리로 이동 |
| **mkdir**  | 디렉토리 생성 |
| **rm**     | 파일 삭제 |
| **pwd**    | 편재 디렉토리 경로 보여주기 |
| **chmod**  | permission 변경 |
| **cat**    | 파일의 내용을 화면 출력 / 파일을 만드는 명령 |

***

## 1.4 vi 편집기 사용하기

vi 편집기는 유닉스/리눅스에서 가장 오래, 많이 사용된 문서 편집기이다. 라즈베리파이에는 [nano 편집기](https://ko.wikipedia.org/wiki/GNU_%EB%82%98%EB%85%B8)도 있지만 nano 편집기는 사용하기 쉬우므로 vi 편집기에 대해 알아보겠다. <del>내가 애용해서 쓰는 거니까 어려우면 nano 써</del>  
[참고 사이트](https://www.linux.co.kr/linux/vi/vi.html)

vi편집기에는 명령어 모드(command mode)와 편집모드(edit mode)가 있다. 명령어 모드에서는 vi편집기를 다루는 모드이며, 편집모드는 문자를 입력하는 모드이다. 편집모드에서 명령어모드로 전환할때는 Esc키를 누르면 된다. 편집모드는 단순히 입력을 하면 되니, 명령어 모드에서의  **간단한 명령어만**<del>자세한건 알아서 찾아봐</del> 알아보겠다.  

#### 커서이동

* **h** : 왼쪽으로 커서 이동  
* **j** : 위쪽으로 커서 이동  
* **k** : 아래쪽으로 커서 이동  
* **l** : 오른쪽으로 커서 이동  

#### 삽입  

* **i** : 현재 커서 위치부터 편집모드(edit mode) 실행  
* **a** : 현재 커서의 다음 위치부터 편집모드(edit mode) 실행  
* **o** : 현재 커서의 아래 행 부터 편집모드(edit mode) 실행  

#### 삭제  

* **x** : 현재 커서 부터 *문자* 삭제  
* **dw** : 현재 커서 부터 *단어* 삭제  
* **dd** : 현재 커서 위치의 *한 행* 삭제  

#### 기타 중요 명령어

* **u** : 되돌리기
* **/** : 탐색
* **n** : 탐색 계속
* **.** : 반복 수행

#### 저장 및 종료

* **:w** : 변경사항 저장
* **:q** : 종료
* **:q!** : 강제종료
* **:wq!** : 저장 후 강제종료

***

## 1.5 리눅스에서 C/C++ 코딩하기

![Program Development in Unix/Linux](/public/img/20161013.jpg)

#### vi editor
vi 편집기를 사용하여 프로그램 소스 코드 작성

#### gcc : GNU C Compiler
gcc 를 통해 컴파일, 플래그를 추가하여 링킹까지도 가능하다.  

* gcc [options] source-files
* g++ [options] source-files


* Option
	* -c : compile only
	* <del>일단 -c 옵션 하나만 이라도 알고있자!</del>  


* 사용예시
	 * gcc test.c
	  * gcc -c test test.c 


> Compile? Linking?  
> 설마 컴파일과 링킹의 차이점을 모르진 않지?????? 이거 플밍기초시간에 배운거야 기억을 더듬어봐  
> 기억안나는 사람들을 위해...


#### 소스 코드 작성부터 실행까지의 과정 정리 [3](http://seohs.tistory.com/259)

> 코드 작성 --(컴파일)--> 오브젝트 파일 --(링킹)--> 실행 파일 --(로드)--> 메모리 적재 및 수행  

흔히 말하는 프로그래래밍(=코딩)을 하여 만드는 파일이 바로 * .c 혹은 * .cpp 파일이다. 이 파일을 소스 파일이라 하고, 이렇게 작성한 코드는 **컴파일(Compile)**과정을 거쳐 컴퓨터가 이해할 수 있는 언어로 변환된다. 이렇게 컴파일된 파일을 **오브젝트 파일(Object File)**이라고 한다.  
일반적으로 하나의 프로그램은 "여러 개의 오브젝트 파일" + "공용 라이브러리" 로 구성되어 있다. 따라서 "공용 라이브러리"를 오브젝트 파일과 합쳐주는 과정이 필요하며, 이를 **링킹(Linking)**이라고 한다.  
컴파일과 링킹을 거치면 최종적으로 상용자가 실행할 수 있는 실행파일(* .exe)이 생성되는 것이다.  
완성된 실행파일을 사용자가 실행하게 되면, 컴퓨터는 해당 프로그램의 내용을 메모리에 **적재(Load)**시키고 소스코드에 따라 프로그램이 수행된다.  

***

## 2.1 Raspberry Pi란?

> 라즈베리파이에 대해선 기존에 많이 설명했으니 생략하고, 리눅스 관점에서 라즈베리에 대해 알아보자  

#### Raspbian
라즈비안은 라즈베리파이 재단이 만든 라즈베리파이 전용 리눅스 커널이다.  
라즈비안은 이름에서 보듯이 데비안 계열의 커널이며, 기본적인 데비안, 우분투 명령어를 모두 사용할 수 있다.  

> 그럼 라즈베리파이를 하다가 모르는게 나오면 구글에 어떻게 검색해야할 지 알겠지?  
> 우분투 어쩌구, 데비안 어쩌구 이렇게 검색하면 훨씬 많은 자료를 얻을 수 있을 꺼야  

***

## 2.2 Raspberry Pi에서 코딩하기

#### C/C++

라즈베리에서 C/C++ 언어로 코딩 후 실행 파일을 만드는 것은 리눅스 환경에서의 프로그래밍과 같다.  

1. vi 편집기를 통해 소스 코드 작성
2. gcc를 통한 컴파일
3. 실행 

  
#### Python

파이썬과 같은 스크립트 언어(컴파일 과정을 거치지 않아도 실행할 수 있는 언어)도 마찬가지로 코딩하면 된다.  

> 임베디드 프로젝트를 할때도 같아~ 그냥 코딩하고 실행하면 됨! 근데 문제가 있어  
> 라즈베리파이를 끄고 새로 전원을 공급했을 때!!!! 이때는 너희가 만든 프로그램이 실행이 안되잖아  
> 이럴땐 어떻게 해야할까? 라즈베리파이에 접속 후, 실행하라는 명령어를 입력해서 실행시킬까?  
> 자동으로 전원이 들어오면 실행되게 할 수는 없을까?  


## 데몬(Daemon) 만들기

  
먼저 프로세스와 데몬의 차이점을 간단하게 알아보자.

* 프로세스(process) : 메모리에 로딩 된 프로그램(그럼 프로그램은? 하드디스크에 저장 된 파일 중 실행 가능한 파일)
* 데몬(daemon) : 특정 서비스를 위해 백그라운드 상태에서 계속 실행되는 서버 프로세스  

윈도우에서 작업관리자(ctrl + alt + del)에 들어가보면 프로세스 창이 있다. 이곳에 있는 것을 프로세스라 생각하면 되며,  
그 중 Naver updater, Adobe Acrobat Update Service 와 같은 프로세스를 데몬이라 생각하면 된다.  

  
#### init daemon  

데몬 중에서도 특별한 데몬들이 존재한다. 대표적인 것이 바로 **init daemon**이다. init daemon은 이름에서도 알 수 있듯이, Initializationo 과정, 즉 리눅스 커널이 시작되면서 작동하는 데몬이다. 이 데몬들은 /etc/init.d 경로에 있으며(라즈비안 기준, 다른 리눅스 커널에서는 다를 수 있다.) 이 경로에 데몬을 만들어 권한을 주면, init daemon으로 동작한다.  

> 그럼 답이 나왔지? init daemon을 하나 만들고 이 init daemon이 너희 프로젝트의 프로그램을 실행시키도록 하면 되는거야  

  
#### 프로세스/데몬의 종료

이 부분은 실습을 통해 알아보겠다.  

***

## 마무리

장황한 설명이 끝났다. 겉보기엔 굉장히 어려워 보이는데, 실제로 해보면 별거 아니라는걸 알게 될 것이다. 윈도우즈를 사용할 때 따로 공부를 해가며 사용하지는 않을 것이다. 리눅스도 윈도우즈와 같이 하나의 운영체제이기 때문에 계속 사용해보면 저절로 익힐 수 있다. 물론 CUI로 되어있기 때문에 약간의 공부가 필요하지만, 요즘 리눅스는 윈도우즈처럼 GUI도 지원하기 때문에 더욱 쉽게 익힐 수 있다. </del>하지만 나는 CUI를 추천한다.</del>  
이 문서에는 라즈베리파이 초기설정을 비롯한, gpio 사용법, 프로세스 실행/종료 등의 내용은 빠져있다. 이러한 사항은 검색하면 쉽게 찾을 수 있으니 구글링을 해보자! <del>네이버는 아니야! 네이버는 웹툰을 보기 위해 존재하는거지 검색을 위해 존재하는게 아니야...네이버 입사하고싶다</del>  

> 문서를 보고 질문사항이 있다면, 혹은 잘못된 사항이 있다면 연락주세요 >-<