---
layout: post

title:  "도메인 등록과 github page 연결"

date:   2017-09-06 13:07:10

author: C.W.Kim

categories: Iron

tags: GitHub Pages Domain Regitration 도메인등록
---

### 도메인 등록과 페이지 연결 ###

>  도메인 등록 업체에서 도메인 확인하던중 가격이 싼 xyz 도메인 ( 96%  할인) 하길래 
>
>  가차없이 샀습니다. 1년 한시로 싸긴 하지만, 그때까지라도 어딥니까?
>
>  Github pages를 연결하는 부분을 작성합니다.



우선 구글 검색을 해서 gabia라는 도메인 및 호스팅 등록 업체를 찾아 들어갑니다.

![도메인 등록 검색 화면](https://ironhub.github.io/assets/DomainReg.png)

도메인 샀다고 치고 www.mydomain.xyz     CNAME 설정을 위하여 부가서비스를 클릭

![부가서비스클릭](https://ironhub.github.io/assets/DomainReg02.png)

부가서비스 설정 화면에서 DNS 레코드 설정을 클릭합니다.

![DNS레코드설정클릭](https://ironhub.github.io/assets/DomainReg03.png)

CNAME 레코드에서 www.mydomain.xyz 와 github 페이지와 매핑해줍니다.

![GitHub페이지와연결](https://ironhub.github.io/assets/DomainReg04.png)

값/위치 항목에서 마지막에  `.`  찍는 것을 잊지 말기를



**이제는 GitHub 에서 Custom domain을 설정해야 합니다.**

GitHub/**user**.github.io Repository에서 `Settings` 항목에서  

![깃허브 설정에서 custom domain 설정](https://ironhub.github.io/assets/DomainReg05.png)  

제대로 매핑되었는지 확인하는 방법은 

터미널을 여시고 dig  **yourdomain**.xyz 하면 CNAME 으로 매핑된 github page를 확인할 수 있습니다.

![터미널 확인](https://ironhub.github.io/assets/DomainReg06.png)