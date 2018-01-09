---
layout: post 

title: Common Log Format 

date: 2018-01-09 09:46:10 

author: C.W.Kim 

categories: Iron

tags: NCSA_Common_Log_Format 
---
### Common Log Format ### 
> Common Log format is a.k.a NCSA Common log format is standardized text file format used by web servers when generating server log files - Wikipedia
* NCSA HTTPd - 1993~5 년쯤에는 웹서버 점유율 1위 하고 있었다가 Apache 의 등장으로 빠르게 대체됨.

* NCSA HTTPd 의 서버 로그파일 포맷이 현재의 Common Log Format 의 원형 

* 다음과 같은 형식
 ```apache
    remotehost rfc931 authuser [date] "request" status bytes
    
    remotehost : 원격 호스트 이름
    rfc931 : 사용자의 원격 로그 이름
    authuser: 인증 유저 이름
    [date] : request 의 날짜와 시간
    "request" : 클라이언트로부터 온 그대로의 request line 
    status : HTTP Status Code 
    bytes : 전달 받은 다큐먼트의 컨텐트 길이
 ```

* ​