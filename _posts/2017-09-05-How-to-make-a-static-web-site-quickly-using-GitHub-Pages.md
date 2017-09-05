---
layout: post

title:  "How to make a static web site quickly using GitHub Pages"

date:   2017-09-05 14:31:10

author: C.W.Kim

categories: Iron

tags: GitHub Pages
---



### How to make a static web site quickly Using ***GitHub Pages***###

---

> 웹사이트를 만들기 위해서는 많은 것들이 필요한데, 고정된 서버 IP 내지는 도메인 ,  웹 프로토콜을 위한 웹서버, 동적인 페이지를 위해서는 웹 애플리케이션 서버, 데이터를 저장하기 위해서는 데이터베이스가 필요하게 되고 채택하는 서버에 따라 필요 기술이 달라지게 된다. 이 문서에서는 GitHub에서 제공하는 pages를 통해 빠르게 웹 사이트를 구축하는 방법을 기술하고자 한다.

GitHub에서는 MarkDown 이라는 빠른 텍스트 위주의 마크업 언어를 사용하는데  Daring Fireball  ~~(덤비는 불X)~~  이라는  우리말로는 아주 죽이는 필명(?)을 가진 분이 만드셨다는데, 글쓰기 좋아하고 퍼블리싱하는데 거리낌 없는 사람들에게 아주 괜찮은 생산성 좋은 그거다.

Mac 환경에서는 [Typora](https://typora.io/) Beta Editor 를 활용하여 MarkDown 문서를 만드니 아주 괜찮은듯 하다.

GitHub에 대해 잠깐 이야기 하면 보통 개발자의 프로젝트 소스 버저닝, 개발이슈, 협업을 위한 툴로 활용하는데  Public 버전은 공짜이고, 대신에 소스가 공개되는 Application Life Cycle Managment 도구 이다. 

GitHub에서 역시 웹페이지를 Publishing 할수 있도록 [Pages](https://pages.github.com) 를 제공하는데 이 문서에서는 Github pages를 이용하여 빠른 웹 사이트 구축을 해보고자 하고, 그 과정을 기술하고자 한다.

Github에서는 기존에 프로그램 소스와 부산물들을 올리고 내리고, 소스 콘트롤을 하는 장소 였지만, github에 올리는 컨텐트에 따라 웹 사이트로도 탈바꿈 할수 있는다는 기발한 생각이  포함되어 있다. 

기본적으로 MarkDown을 잘 보여주기 때문에, MarkDown 기반으로 컨텐트를 생산하고 HTML 형식으로 표현하기 위해 jekyll과 같은 사이트 빌딩 프레임워크(?) 와 같이 이용하면 풍성한 웹 사이트를 구축할 수 있게 된다.  

> 그림 #1 - typora ( markdown editor )를 이용하여 컨텐트 작성

[!]("https://ironhub.github.io/assets/icons/typorashot.png")

웹 서핑을 하다보니 , 웹 구축을 위한 프레임워크를 적용할 수있는 방법은 정말 많고도 많더라 아래의 주소에는 오픈소스로 만드는 정적 사이트 생성기들의 순위가 있다.

[Top Open-Source Static Site Generators](https://www.staticgen.com/)

대표적으로 아래와 같은 두 프레임워크이 1,2위를 하고 있다.

#### Web Site Building####

- jekyll   [www.jekyllrb.com](http://www.jekyllrb.com)  ( GitHub pages에 theme 적용 가능) 
- hugo  [https://gohugo.io](https://gohugo.io)

#### <u>Web Add-On</u>####

- ​Disqus [disqus.com](https://disqus.com) ( 사이트에 커멘트를 달수 있도록...)

  ​

