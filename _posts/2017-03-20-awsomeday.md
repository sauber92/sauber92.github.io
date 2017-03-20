---
layout: post
title: '[AWSomeDay] 2017 AWSomeday 참석 후기'
tags: [Review]
description: >
  아마존 웹 서비스(AWS)의 공개 교육 이벤트 - AWSomeday 참석 후기입니다.    
---

## AWSomeDay ?  

<br/>

지난주 금요일(3월 17일, 2017) AWS(Amazon Web Service)에서 AWSomeday라는 이름으로 공개 교육 이벤트가 있었습니다. AWS를 사용해보기 위해 [인프런 강좌 - 초보자를 위한 AWS 클라우드 시작하기](https://www.inflearn.com/course/aws-%ED%81%B4%EB%9D%BC%EC%9A%B0%EB%93%9C-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0/)를 수강했던 저는 더 많은 AWS의 기능을 사용해보기 위해서 이 교육에 참여하였습니다.  

<br/>

![](/public/img/review/awsomeday-2.jpeg)  
![](/public/img/review/awsomeday-3.jpeg)  
*< AWSomeDay 가 열린 세종대학교 >*

<br/>  

***

## 무엇을 배웠나?  

<br/>

저는 지금 AWS 프리티어를 사용 중입니다. 프리티어는 회원가입을 새로한 한 계정을 1년동안 무료(특정 조건 이하의 환경에서만)로 사용할 수 있는 AWS의 정책입니다. 그 동안 EC2라는 Amazon Elastic Compute Clod만 사용해 왔는데, 이 기회에 AWS의 많은 서비스들을 알 수가 있어서 좋았습니다.  

다음은 제가 강의를 들으면서 간단하게 메모판 [AWSomeDay 강의 필기 자료](/public/img/review/AWSomeDay.pdf)입니다.  

<br/>

![](/public/img/review/awsomeday-4.jpeg)  
*< 행사장을 꽉 채울 만큼 인기가 많았다 >*

<br/>  

특히 저는 **IAM**에 큰 관심이 갔습니다. [IAM(AWS Identity and Access Management)](https://aws.amazon.com/ko/iam/?sc_channel=PS&sc_campaign=acquisition_KR&sc_publisher=google&sc_medium=english_iam_b&sc_content=aws_iam_p&sc_detail=aws%20iam&sc_category=iam&sc_segment=161194946520&sc_matchtype=p&sc_country=KR&s_kwcid=AL!4422!3!161194946520!p!!g!!aws%20iam&ef_id=WL@QwwAABdt3c-Jt:20170320125737:s)은 AWS 서비스와 리소스에 대한 접근을 안전하게 제어해 주는 서비스입니다.  

IAM가 매력적이였던 이유는 보안 정책 때문이였습니다. IAM의 보안 정책은 첫째, JSON 파일 형태로 정책을 짤 수 있어 편해보였습니다. 이는 리눅스 시스템의 방화벽인 iptables나 파일 무결성 점검 도구인 Tripwire를 사용한 경험이 있던 저에게 새롭게 다가왔습니다. 이런 보안 도구들은 정책을 정할 때, 특정한 커맨드를 사용해야 했기 때문입니다. 이와 달리 JSON의 장점인 가독성 좋고 쓰기 편하다는 장점을 IAM에서는 그대로 사용할 수 있었습니다.  

둘째, 정책을 정할 수 있는 대상은 사용자, 그룹, 역할(Role) 이렇게 세 가지 형태라는 것입니다. 물론 사용자와 그룹에 대한 정책 대상은 다른 보안도구들도 사용하고 있습니다. 하지만 역할에 대한 정책은 정말 **Awsome!** 했습니다. IAM가 말하는 역할에 대한 정책이란, 일종의 '모자'라고 생각하면 됩니다. *(강사님이 모자라고 설명을 하셨는데 정말 이해가 쉽게 되었습니다 bbb)*  

이 모자를 쓰게 되면 보안 정책에 대한 권한을 받을 수 있고, 모자를 벗으면 권한을 박탈 당합니다. 모자를 쓰는 대상은 사용자가 될 수도 있고, **리소스**가 될 수도 있습니다. *(이 리소스가 모자를 쓰는 개념이 Awsome합니다.)*  
리소스가 모자를 쓴다는 것은 소스코드에 보안 정책에 대한 권한을 부여한다는 것입니다.  

무슨 뜻이냐~하면, 기존에 개발자들은 깃헙에 소스코드를 올리거나 외부에 코드를 올릴 때, 개인정보가 입력되어 있다면 이 것을 다 지우고 올려야 했습니다. 그렇지 않으면 여기저기서 해커들의 공격을 받기 때문이죠. 실제로 깃헙에 올라와 있는 서버정보를 가지고서, 해커들이 몰래 비트코인을 채굴한 사례도 있다고 합니다. 그 만큼 깃헙에 올라와있는 개인정보는 취약하고 위험하며, 해커들의 좋은 놀이터라고 할 수 있겠습니다.  

하지만 이러한 작업은 불편하고 귀찮은 작업입니다. 개발자들은 열심히 코딩을 하고 깃에 푸쉬를 했는데, 알고보니 개인정보도 같이 올라갔다!! 하면 기록을 삭제하고, 소스코드도 고치고 힘들 것입니다. 또 여러 개발자가 같이 협업할 때는 이러한 개인정보는 깃 이그노어에 등록해서 업데이트가 안되게 하거나, 나중에 수정해야 하는 등 불편하죠. 그래서 AWS는 이러한 소스코드, 즉 리소스에 임시 보안 정책인 '모자'를 씌워서 접근 제어가 가능하게 해주는 것입니다. *(완전...똑똑하고 멋져요..bbb)*  

이외에도 많은 AWS 서비스들을 설명 받을 수 있었습니다.  

<br/>

![](/public/img/review/awsomeday-5.jpeg)  
![](/public/img/review/awsomeday-6.jpeg)  
![](/public/img/review/awsomeday-7.jpeg)  

*< AWS의 서비스들 >*  

<br/>  

***

## 느낀점  

아마존이란 회사는 기존의 e-commerce 회사로서 쭉쭉 성장을 하고 있었지만, 더 높은 곳으로 도약하기 위해 킨들, AWS와 같은 사업을 시작하였습니다. AWS를 처음 시작을 했을 땐, 많은 사람들이 그 가능성에 대해 의아해 했다고 합니다. 하지만 시간이 흐른 뒤 **클라우드**란 현대사회를 받치는 하나의 기둥이 되었다고 할 수 있을만큼 발전하였고, 이러한 클라우드 서비스를 선도하는 것이 바로 AWS가 되었습니다.  

<br/>

![](/public/img/review/awsomeday-10.jpeg)  

*< AWS의 리더쉽 원칙 >*  

<br/>  

아직도 AWS는 새로운 서비스를 계속해서 만들고 있고 그 서비스 하나하나는 사용자들을 위해 더 편리하고 의미있는 서비스들이라 생각합니다. *(기회가 된다면 AWS IoT도 꼭 이용해보고 싶어요!!!)*  

이러한 AWS의 철학이 잘 느껴지는 교육이였고 만족스러운 하루였습니다.  

<br/>

![](/public/img/review/awsomeday-8.jpeg)  
![](/public/img/review/awsomeday-11.jpeg)  

*< 행사 참석으로 받은 선물! >*  

<br/> 

![](/public/img/review/awsomeday-9.jpeg)  

*< 물론 점심 도시락의 상태도 굉장히 훌륭했다..감동... >*

***

## AWSomeDay 수료증  

![](/public/img/review/awsomeday-1.png)