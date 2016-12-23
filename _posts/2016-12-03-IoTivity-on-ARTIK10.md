---
layout: post
title: 'IoTivity on ARTIK10'
tags: [Study]
description: >
  **Samsung ARTIK10** 보드에 **Yocto Linux**와 **IoTivity**를 빌드하면서 겪은 어려움을 공유하고, 과정을 하나씩 살펴보겠습니다.
---

## 개요

 저는 ARTIK 보드가 처음 공개 되었을 때 굉장히 기대가 컸습니다. 이미 Arduino, Raspberry Pi는 일반인들도 많이 사용하는 개발보드가 되었으나, Intel Edison이나 Beagle Bone Black과 같은 보드는 상대적으로 사용 경험이 있는 사람은 수가 적었기 때문이죠. 이렇게 개발보드 시장(?)을 Arduino와 Raspberry Pi가 독점하는 상황에서 삼성전자가 만든 개발보드인 ARTIK이 공개가 되었고, 과연 성공을 할지 궁금했습니다.  
 
 하지만 IoT 시대에 맞춰 독자적인 개발보드를 만들었다는 점에선 좋은 판단이라 생각했어요. 그리고 이 ARTIK을 쓰임새에 맞게 여러 버전으로 만든 것과, IoTivity를 접목시킨 것이 ARTIK의 장점과 특징이라고 생각합니다. IoTivity Wiki에 들어가 보면 Arduino와 Raspberry Pi에서도 IoTivity를 사용할 수 있다고 명시되어 있으나([IoTivity Wiki - Hardware](https://wiki.iotivity.org/hardware)), SOSCON 2016에서 듣기론 *Arduino는 전문적인 개발보드가 아니기 때문에 IoTivity를 지원하지 않을 예정이다* 라는 말을 듣기도 하였고, Raspberry Pi에서는 제가 직접 IoTivity의 빌드를 시도했으나 실패한 경험이 있습니다. 아직 IoTivity Wiki가 자세한 설명을 해주는 친절한 Wiki page가 아니라 어려웠던거 같아요.*(2016년 11월 기준)* 하지만 ARTIK 보드에 IoTivity를 빌드하는 방법은 Samsung Open Source Group에 친절히 설명이 나와 있드라구요!! ~~그래도 엄청해맸습니다 ㅜㅜㅜㅠ~~  
 
 따라서 지난 SOSCON 2016에서도 ARTIK과 IoTivity에 대한 강연을 집중적으로 듣고 왔고([SOSCON2016 리뷰글](https://sauber92.github.io/2016/11/17/soscon-iotivity-bigpicture/)), 연구실에서도 한 번 해보라는 지시가 있어서 **ARTIK10 보드에 IoTivity를 빌드**하는 것을 시도했습니다.  
   
 저는 [IoTivity Wiki](https://wiki.iotivity.org/), [TIZEN Wiki](https://wiki.tizen.org/wiki/Tizen_On_ARTIK), [Samsung Open Source Group](https://blogs.s-osg.org/)에 포스팅 되어 있는 자료를 통해 정보를 얻었으며 실제로 해보면서 겪은 문제점을 공유하겠습니다. 

***

*주의할 점*  

하나의 명령어로 다음 패키지들을 설치할 수도 있다. Host PC에서는 문제가 되지 않지만 이상하게 ARTIK10에서는 하나의 명령어로 패키지를 설치를 하면, Install이 되지 않는 패키지가 있었다. 따라서 이 포스팅에서는 하나씩 따로 설치를 하도록 하겠습니다.  

***

## Step1. Yocto Build

 먼저 Yocto Linux란, Open source로 공개되어 있는 Embedded linux system입니다. 저는 Intel Edison을 사용했을 때, Yocto를 접해봤습니다.([(2015 한이음 공모전 BKBK)](http://localhost:4000/2015/12/30/haneium/))  그러나 그 당시엔 Intel에서 미리 만든 Yocto 이미지를 사용하였고, 이번엔 아예 Yocto를 빌드하는 하는 것부터 시작해 보겠습니다.  
 
### 1-0. 크로스 컴파일 환경
 
 * **Host PC** : Ubuntu 14.03 LTS  
 * **필요 패키지**
		* git  
		* gawk  
		* chrpath  
		* texinfo  
		* qemu  

```
ubuntu@ubuntu:~$ sudo apt-get install git
ubuntu@ubuntu:~$ sudo apt-get install gawk
ubuntu@ubuntu:~$ sudo apt-get install chrpath
ubuntu@ubuntu:~$ sudo apt-get install texinfo
ubuntu@ubuntu:~$ sudo apt-get install qemu qemu-user qemu-user-static
```  

### 1-1. git clone poky  

* **Poky** : Yocto project의 레퍼런스 시스템, Poky를 빌드하여 리눅스 이미지를 생성하거나 필요한 애플리케이션을 추가할 수 있다.  

```
ubuntu@ubuntu:~$ git clone -b jethro http://git.yoctoproject.org/git/poky  
```  


### 1-2. Poky 디렉토리 이동, git clone meta-artik  

```
ubuntu@ubuntu:~$ cd poky  
ubuntu@ubuntu:~/poky$ git clone -b master https://github.com/resin-os/meta-artik    
```  

### 1-3. reular image 빌드  

```
ubuntu@ubuntu:~/poky$ .. /oe-init-build-env  
```  

![](/public/img/study/iotivity-1.png)  

### 1-4. conf/bblayers.conf 수정  

```
ubuntu@ubuntu:~/poky/build$ vi conf/bblayers.conf  
```  

```
TIVE_DIR := "${@os.path.abspath(os.path.dirname(d.getVar('FILE', True)) + '/../../..')}"  
# LAYER_CONF_VERSION is increased each time build/conf/bblayers.conf  
# changes incompatibly  
LCONF_VERSION = "6"  
 
BBPATH = "${TOPDIR}"  
BBFILES ?= ""  
 
BBLAYERS ?= " \  
  ${RELATIVE_DIR}/poky/meta \  
  ${RELATIVE_DIR}/poky/meta-yocto \  
  ${RELATIVE_DIR}/poky/meta-yocto-bsp \  
  "  
BBLAYERS_NON_REMOVABLE ?= " \  
  ${RELATIVE_DIR}/poky/meta \  
  ${RELATIVE_DIR}/poky/meta-yocto \  
  "  
 
BBLAYERS += "${RELATIVE_DIR}/poky/meta-artik“  
```  

### Yocto Build  

```
ubuntu@ubuntu:~/poky/build$ MACHINE=artik10 bitbake core-image-minimal  
``` 

![](/public/img/study/iotivity-2.png)  

***

## Step2. IoTivity 추가  

### 2-1. git clone meta-oic  

```
ubuntu@ubuntu:~/poky/build$ cd ../../poky  
ubuntu@ubuntu:~/poky$ git clone -b 1.1.0 http://git.yoctoproject.org/cgit/cgit.cgi/meta-oic  
``` 

### build/conf/bblayers.conf 에 추가  

```
ubuntu@ubuntu:~/poky$ vi build/conf/bblayers.conf  
``` 
```
...  

# IoTivity 추가  
BBLAYERS += "${RELATIVE_DIR}/poky/meta-oic“    
``` 

### build/conf/local.conf 에 다음 문장 추가  

```
ubuntu@ubuntu:~/poky$ vi build/conf/local.conf  
``` 
```
...  

# IoTivity  
IMAGE_INSTALL_append = " iotivity iotivity-resource iotivity-service"  
# IoTivity Sample application  
IMAGE_INSTALL_append = " iotivity-resource-samples iotivity-service-samples"     
```  

### regular image 빌드  

```
ubuntu@ubuntu:~/poky$ ../oe-init-build-env  
```  

![](/public/img/study/iotivity-3.png)  

### Rebuild  

```
ubuntu@ubuntu:~/poky/build$ MACHINE=artik10 bitbake core-image-minimal  
```  

![](/public/img/study/iotivity-4.png)  

***

## Step3. SD카드에 이미지 옮기기  

### 3-1. SD카드 위치 확인  

```
ubuntu@ubuntu:~/poky/build$ lsblk  
```  

### 3-2. disk 변수 등록  

```
ubuntu@ubuntu:~/poky/build$ disk=/dev/sd[SD카드 위치]  
```  

### 3-3. qemu를 통한 이미지 변환  

* **qemu** : 가상 아키텍쳐 에뮬레이션  

```
ubuntu@ubuntu:~/poky/build$ sudo dd if=tmp/deploy/images/artik10/core-image-minimal-artik10.artik-sdimg bs=32M oflag=sync of=$disk  
```  

***

## Step4. ARTIK10 부팅  

### 4-0. ARTIK10 모습  

![](/public/img/study/iotivity-5.png)  

* 초기 상태 : SW2 = 모두 왼쪽 / PSW1 = Off  

### 4-1. ARTIK10을 SD카드 부팅모드로 변경  

* SD카드를 넣고, SW2를 모두 오른쪽으로 옮김  

![](/public/img/study/iotivity-6.png)  

* PSW1을 ON  

![](/public/img/study/iotivity-7.png)  

### 4-2. Debug USB를 컴퓨터와 연결 후, 연결 포트를 찾음  

* Windows 컴퓨터의 경우 : 장치관리자 > 포트(COM&LPT) > USP Serial Port  

### 4-3. 터미널 프로그램(ex. putty, xshell, etc)을 통한 Serial 연결  

![](/public/img/study/iotivity-8.png)  

### 4-4. SD카드 이미지로 ARTIK10 부팅  

* SW3를 잠시 눌러주면, 부팅과정이 터미널에 보임  

![](/public/img/study/iotivity-9.png)  
![](/public/img/study/iotivity-10.png)  

* login
	* ID : root

![](/public/img/study/iotivity-11.png)  

