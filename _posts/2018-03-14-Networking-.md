---
layout: post 

title: Networking  

date: 2018-03-14 09:49:47 

author: C.W.Kim 

categories: Iron

tags: networking basic 
---
### Networking Basic  ### 
>  후니의 쉽게 쓴 시스코 네트워킹을 대충 읽고
이더넷 , 토큰링, FDDI, ATM - 네트워킹 방식

CSMA/CD ( Carrier Sense Multiple Access/ Collision Detection )

 - LAN 안에서 통신하는 녀석이 있는 지 없는 지 확인하고 재빨리 보내다가 충돌이 나면 랜덤으로 잠시 쉬는 것

 - Collision Domain 에 있기 때문에 한 PC 만이 데이터를 보낼수 있음.

토큰링은 순서(토큰) 를 받아야 데이터를 전송할수 있음.

UTP 케이블 , 광케이블, 동축 케이블

RJ_45 커넥터 + UTP 케이블

MAC(Media Access Control ) 

ARP ( Address Resolution Protocol ) - IP 주소 를 MAC 어드레스로 바꿔줌.

유니캐스트  - 소스와 타겟이 있어서 지정한 타겟으로 보내는 것

브로드캐스트 - 전체 LAN에 있는 디바이스에 다 보내며, 랜카드는 반드시 CPU로 처리해줄것을 Interrupt 함.

멀티캐스트 -  다중 타겟에게 보냄. 브로드 캐스트는 아니나, 허브나 스위치가 멀티 캐스트를 지원해 주어야 함.

OSI 7 레이어 - 애 프 스 트 엔 들 피 application - presentation - session - transport - network - data link - pysical 

TCP/IP , IPX(Internetwork packet exchange) , NetBEUI, AppleTalk

TCP/IP ( Transmission Control Protocol / Internet Protocol ) - ARPANET 

IP 주소는 유일 , 공유하기 위해 NAT ( Network Address Translation ) / PAT ( Port ..)

NIC  - Network Interface Card

NIC - Network Information Center - 공인IP 주소 관리 기관

DHCP - Dynamic Host Configuration Protocol - Server/ Client 로 구성

랜카드 

허브 - 멀티포트 리피터 역할

 인텔리전트 허브 - 콜리전 발생의 경우 격리 가능 / 더미 허브

스위치 - 스패닝 트리 알고리즘 ( 루핑을 막아주고자 두개 이상의 경로가 존재하면 한 통로를 막고 다른 통로가 사용할 수 없으면 여는 방식 )

라우터 - 브로드캐스트 영역을 나눠주기 위해 필요함. 패킷 필터링 기능을 제공함, 로드를 분배하는 기능, 트래픽 전송 순서 조정 QoS

스위치 중에 라우터 기능을 포함하는 것을 L/3 스위치라고 함.

 IP 클래스 :  A : 1~126 앞자리 

​		  B : 128 ~ 191 

​		  C : 192 ~ 223

​		  10.3.4.3 의 경우 A 클래스이고 네트워크 부분은 10.0.0.0 호스트부분은 3.4.3

​		  132.12.11.4 의 경우 B  클래스이고 네트워크부분은 132.12.0.0 호스트부분은 11.4` 

콜리전 도메인을 막는 방법은 스위치로 나누는 것이고, 브로드캐스트를 막는 방법은 라우터이다.