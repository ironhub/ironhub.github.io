---
layout: post 

title: Docker NodeJS Image  

date: 2018-02-20 15:26:45 

author: C.W.Kim 

categories: Iron

tags: docker nodejs 
---
### Making Docker NodeJS Image  ### 
> Node.JS Application을 포함하는 도커 이미지를 만들고,  dockerhub.com 에 public으로 발행하고
>
> Oracle Container Cloud Service Classic 에 올려보는 것 까지.
#### Node.JS 도커 이미지 만들기 #### 
> 잘 만들어진 Node.JS 애플리케이션을 준비한다.
* 튜토리얼 URL [NodeJS Docker Image 만들기](https://nodejs.org/en/docs/guides/nodejs-docker-webapp/)
  ![예제 디렉토리 구조](https://ironhub.github.io/assets/screeenshots/nodejsDockerDirectory.png)

  그림과 같이 잘 돌아가는 Node.JS 애플리케이션 디렉토리에

  Dockerfile 을 만든다

### DockerFile ###

```sh
> Dockerfile

FROM node:carbon

#Create app directory
WORKDIR /usr/src/app

#npm install 을 실행하여 node_modules 를 만들기 위해
COPY package*.json ./
RUN npm install 

COPY . .
#외부에 공개하는 포트
EXPOSE 8080
CMD ["npm", "start"]


```

```sh
> .dockerignore
node_modules
npm-debug.log
```

Dockerfile이 있는 해당 디렉토리에서

```sh
> docker build --tag iamairon/node-web-app
> docker images
iamairon/node-web-app         latest              69c69164d76c        26 minutes ago      698MB

> docker run -p 8080:3000 -d iamairon/node-web-app
    -p 8080(외부포트):3000(내부포트)
	docker run -p 8080:3000 -d iamairon/node-web-app
	8bcf114ff25a65447b9baede61d1e02a6ccd1ab3bd07f8af166f0bb4954714d3

> docker logs 8bcf114ff25a65447b9baede61d1e02a6ccd1ab3bd07f8af166f0bb4954714d3

> expressjs@1.0.0 start /usr/src/app
> node app/app.js

Listening on port 3000


```
###Docker Hub에 올리기 ###
```sh
> docker login
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username (iamairon):
Password:
Login Succeeded
> docker push iamairon/node-web-app:latest
The push refers to repository [docker.io/iamairon/node-web-app]
fc198206b3c9: Pushed
3b2c25edc456: Pushed
8f2f41483350: Pushed
f79293fc11b5: Pushed
8e3a6d61dcdb: Mounted from library/node
3a19394b2eae: Mounted from library/node
2e1fd498af59: Mounted from library/node
daa6e91e491c: Mounted from library/node
6b60013e5875: Mounted from library/node
d6335a641f5e: Mounted from library/node
5c33df241050: Mounted from library/node
ffc4c11463ee: Mounted from library/node
latest: digest: sha256:8114a3f2bef02c47c74e811001f5a0155854c014cc1aa0b842a9259335b1096d size: 2845


```
![도커 허브 등록 모습](https://ironhub.github.io/assets/screeenshots/dockerhubRegistration.png)

### Oracle Container Cloud Service 에 등록 ###

OCCS Create Instance 를 하면 , Manager/ Worker 기본 두개의 OCPU를 점유하는 서비스가 만들어진다.
만들어진 manager public ip 로 접근하면
다음과 같은 예로 https://129.157.187.109/#/dashboard  

![OCCS 서비에서 콘솔 열기](https://ironhub.github.io/assets/screeenshots/OCCS01.png)
다음과 같은 id/pwd 로긴 창이 뜨고 인스턴스 만들때 지정했던 admin / pwd 로 접근하면 다음과 같은 대시보드가 열린다. 
![OCCS 관리자 콘솔 로그인](https://ironhub.github.io/assets/screeenshots/OCCS02.png)
![OCCS 관리자 콘솔 대시보드](https://ironhub.github.io/assets/screeenshots/OCCS03.png)
####서비스 등록 ####
왼쪽 메뉴의 Services 를 눌러
![OCCS Services](https://ironhub.github.io/assets/screeenshots/OCCS04.png)
![OCCS Services -> New Service  서비스 등록](https://ironhub.github.io/assets/screeenshots/OCCS05.png)
docker run 추가 커맨드를 작성한다. 그림의 예는  외부포트/내부포트 지정
![서비스 등록 - 도커 커맨드](https://ironhub.github.io/assets/screeenshots/OCCS06.png)
####Deployment ####
![디플로이](https://ironhub.github.io/assets/screeenshots/OCCS07.png)
![디플로이 상태](https://ironhub.github.io/assets/screeenshots/OCCS08.png)
