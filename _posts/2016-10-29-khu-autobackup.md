---
layout: post
title: '[KHU-Unix System Programming] auto_backup'
tags: [Project]
description: >
  이 프로그램은 경희대학교 컴퓨터공학과 Unix System Programming 수업에서 사용하는 서버에서 예비서버버로 파일을 백업하기 위해 만들어진 bash shell program입니다.
---

## 1. 기능

이 프로그램은 현재 디렉토리의 있는 모든 내용을 tar를 통해 묶은 후, sftp를 통해 원격 서버로 전송하는 프로그램입니다.  
백업은 3분에 한번씩 이루어지며, 90분(수업시간)동안 동작 후 종료 됩니다.  
백업 파일의 이름은 "백업시간(year+month+day).tar" 로 되어있습니다.  

***

## 2. 사용법

### 2-1. rsa 키 생성

local server에서 rsa 키를 생성 하여, remote server에 등록을 해야 자동 로그인이 됩니다.  
rsa 키 생성은 local server에서  

```
id@local:~$ ssh-keygen -t rsa  
```

라 입력하면 되고, **~/.ssh/id_rsa.pub** 내용을 확인합니다.

```
id@local:~$ cat ~/.ssh/id_rsa.pub
```

이 내용을 복사 후 remote server의 **~/.ssh/authorized_keys** 에 입력하면 됩니다.

```
id@remote:~$ vi ~/.ssh/authorized_keys
```

***

### 2-2. 다운로드 및 권한 부여

backup.sh를 다운 받은 후, shell에서  

```
id@local:~$ chmod 755 backup.sh
```

와 같이 실행권한을 부여합니다.  

***

### 2-3. 코드 수정

vi editor와 같은 편집기를 사용하여 backup.sh를 수정합니다.  

```
HOST='User remote server ip'   
USER='User id'
```

위의 변수를 사용자에 맞게 수정하면 됩니다.  

만약, 전체 폴더의 백업을 원하지 않는다면 다음 코드에서  

```
tar -cvzf $NAME.tar *
```

`*` 을 지우고 자신이 원하는 파일의 명을 입력하면 됩니다.  

***

### 2-4. 실행

```
id@local:~$ ./backup.sh &
```

와 같이 실행을 하면 됩니다.  

***

## 3. 제작

* 제작자 : 정준영(경희대학교 전자전파공학과, 컴퓨터공학과 학부)    
* 연락 : jjy920517@gmail.com, [github](https://github.com/sauber92), [Facebook](https://www.facebook.com/profile.php?id=100003258917365), [Blog](https://sauber92.github.io)  
* 언어 : bash shell script language
* 실행 환경 : Ubuntu 12.04.5 LTS
