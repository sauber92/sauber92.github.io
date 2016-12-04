---
layout: post
title: '[SOSCON 2016] TIZEN on ARTIK'
tags: [Review]
description: >  
    삼성에서 진행한 오픈소스 컨퍼런스 리뷰입니다.  

    **강연자 : 박지환, 삼성전자 소프트웨어센터(Tizen Platform Lab)**

---

[발표자료 링크](http://www.soscon.net/pdf/17/1520_2.pdf)

### Tizen Common  

Tizen은 2012년도 1.0 개발부터 현재(2016) 3.0까지 있다.  
2.2에서 모바일, 2.3에서는 웨어러블, 2.4에서는 티비로 확장을 하였고 3.0에서는 Tizen:Common이라는 것을 구성하여 대부분의 제품에 사용하도록 함.  
꼭 ARTIK이 아니더라도 Low-end to High-end coverage of devices를 지향  

***

### Tizen on ARTIK  

ARTIK1: 일반인이 구매할 수는 없고, 가전제품 쪽에 사용되고 있다.  
ARTIK5/10 : I/O header가 외부로 나와있어 사람들이 사용하기에 편하다.  

타이젠이 올라간 아틱은 전화만 안되는 스마트 기기라 생각하면 쉽다.  

> IoTivity가 아두이노나 라즈베리파이에서 제대로 적용이 안되어 있는데, ARTIK에서는 잘 되어 있고 특히 Tizen 기반 위에서 하는 것을 권장하는 느낌이다.  

***

### IoT Simple Aplication on ARTIK Cloud  

##### Demo  

|------------------------------|
| Smartphone(Set Rule) |
| ARTIK Cloud - ARTIK5(Sensor) |  
| ARTIK10(Actuator) |

##### Demo Contents  

* ARTIK Cloud  
* system IO  
* node.js(system IO add-on) 

Tizen Middleware 에 system IO interface가 있고, 이를 node.js를 사용하여 add-on 할 수 있게하여, sensor와 actuator를 제어하는 어플리케이션을 javascript로 짤 수 있게 한다.  

***

### Reference  

[Tizen Wiki Page](https://wiki.tizen.org/wiki/Tizen_On_ARTIK)  

***

> 느낌점 : ARTIK은 하드웨어 스펙만 보더라도 기존의 아두이노나 라즈베리파이, 인텔 에디슨에 비해 뛰어나다는 것을 알 수 있다. 하지만 학생이나 개발자들이 인식하기엔 접근하기 어렵다는 느낌이 있다. 이는 가격에 이유도 있겠고, 이미 아두이노와 라즈베리파이가 이 시장에 선두주자로 있기 때문인거 같다. Tizen에 경우, 사실 금방 사라질줄 알았다. 하지만 지속적으로 삼성 디바이스에 사용되면서 발전하고 있어 보이고, 이번 Tizen3.0의 경우 여러 디바이스를 지원하기 위해 개발된 만큼 기대가 된다. 이러한 Tizen이 ARTIK보드에 올라간다면 그 시너지가 더 커질 것으로 보이고 삼성이 하드웨어뿐만아니라 미들웨어, 나아가 소프트웨어까지 진출하려는 의지가 보이는거 같다.
