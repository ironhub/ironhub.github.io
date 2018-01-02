---
layout: post 

title: docker basic 

date: 2018-01-02 16:03:26 

author: C.W.Kim 

categories: Iron

tags: docker basic command 
---

### docker basic ### 
> 간단한 명령어에 대해 알아본다.

#### docker hub 등록 ####

hub.docker.com 에 sign up 한다.

hub.docker.com 에 sign in 한다.

![Docker Hub](https://ironhub.github.io/assets/screenshots/dockerhub.png)



```bash
# dockerhub 에 접근하기
# hub.docker.com 에 가입한다.

[root@iaas ~]# docker images
REPOSITORY                                          TAG                 IMAGE ID            CREATED             SIZE
container-registry.oracle.com/middleware/weblogic   12.2.1.3            1fcee95cc21b        3 weeks ago         1.14GB
iamairon/docker-turtle                              latest              410c53e188b6        10 months ago       256MB
iamairon/docker-turkey                              latest              92fa7430d592        10 months ago       256MB

[root@iaas ~]# docker ps -a
CONTAINER ID        IMAGE                                                        COMMAND                  CREATED             STATUS                      PORTS                    NAMES
3f205cf446f5        iamairon/docker-turkey                                       "/bin/sh -c '/usr/..."   31 minutes ago      Exited (0) 31 minutes ago                            sharp_curie
e1c518f30493        iamairon/docker-turtle                                       "/bin/sh -c '/usr/..."   37 minutes ago      Exited (0) 37 minutes ago                            elastic_gates
8aa9a970ed1f        container-registry.oracle.com/middleware/weblogic:12.2.1.3   "/u01/oracle/creat..."   2 hours ago         Created                                              gifted_newton
3e58f8f7e424        container-registry.oracle.com/middleware/weblogic:12.2.1.3   "/u01/oracle/creat..."   2 hours ago         Up 2 hours                  0.0.0.0:7001->7001/tcp   dreamy_mayer
f1433ae0820c        container-registry.oracle.com/middleware/weblogic:12.2.1.3   "/u01/oracle/creat..."   3 hours ago         Exited (137) 2 hours ago                             keen_easley



[root@iaas ~]# docker run iamairon/docker-turtle
 _________________________________________
/ Was my SOY LOAF left out in th'RAIN? It \
\ tastes REAL GOOD!!                      /
 -----------------------------------------
    \                                  ___-------___
     \                             _-~~             ~~-_
      \                         _-~                    /~-_
             /^\__/^\         /~  \                   /    \
           /|  O|| O|        /      \_______________/        \
          | |___||__|      /       /                \          \
          |          \    /      /                    \          \
          |   (_______) /______/                        \_________ \
          |         / /         \                      /            \
           \         \^\\         \                  /               \     /
             \         ||           \______________/      _-_       //\__//
               \       ||------_-~~-_ ------------- \ --/~   ~\    || __/
                 ~-----||====/~     |==================|       |/~~~~~
                  (_(__/  ./     /                    \_\      \.
                         (_(___/                         \_____)_)
                         
                         
[root@iaas ~]# docker login
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username (iamairon): iamairon
Password:
Login Succeeded

[root@iaas ~]# docker run iamairon/docker-turkey
 ____________________________________
/ "An ounce of prevention is worth a \
\ pound of purge."                   /
 ------------------------------------
  \                                  ,+*^^*+___+++_
   \                           ,*^^^^              )
    \                       _+*                     ^**+_
     \                    +^       _ _++*+_+++_,         )
              _+^^*+_    (     ,+*^ ^          \+_        )
             {       )  (    ,(    ,_+--+--,      ^)      ^\
            { (@)    } f   ,(  ,+-^ __*_*_  ^^\_   ^\       )
           {:;-/    (_+*-+^^^^^+*+*<_ _++_)_    )    )      /
          ( /  (    (        ,___    ^*+_+* )   <    <      \
           U _/     )    *--<  ) ^\-----++__)   )    )       )
            (      )  _(^)^^))  )  )\^^^^^))^*+/    /       /
          (      /  (_))_^)) )  )  ))^^^^^))^^^)__/     +^^
         (     ,/    (^))^))  )  ) ))^^^^^^^))^^)       _)
          *+__+*       (_))^)  ) ) ))^^^^^^))^^^^^)____*^
          \             \_)^)_)) ))^^^^^^^^^^))^^^^)
           (_             ^\__^^^^^^^^^^^^))^^^^^^^)
             ^\___            ^\__^^^^^^))^^^^^^^^)\\
                  ^^^^^\uuu/^^\uuu/^^^^\^\^\^\^\^\^\^\
                     ___) >____) >___   ^\_\_\_\_\_\_\)
                    ^^^//\\_^^//\\_^       ^(\_\_\_\)
                      ^^^ ^^ ^^^ ^
                      
[root@iaas ~]# docker stop `docker ps -a -q`
500a6f1a0d72
b3d090b24ae9
3f205cf446f5
e1c518f30493
8aa9a970ed1f
3e58f8f7e424
f1433ae0820c


```

