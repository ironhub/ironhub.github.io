---
layout: post 

title: Docker install on Oracle Linux 7 

date: 2018-01-02 09:50:12 

author: C.W.Kim 

categories: Iron

tags: OEL Docker 
---
### Docker install on Oracle Linux 7 ### 
> Oracle Linux 7 에 Docker를 인스톨하는 과정과 http://container-registry.oracle.com/ 에 등록되어 있는 이미지를 가져와서 - WebLogic Server - running 해보는 것까지 .

[참고 문서](https://blogs.oracle.com/hlsu/install-docker-on-oracle-linux-7)

#### yum.conf ####

```bash

# cd /etc/yum.repos.d/
# wget http://yum.oracle.com/public-yum-ol7.repo
# vi public-yum-ol7.repo

[ol7_latest]
name=Oracle Linux $releasever Latest ($basearch)
baseurl=http://yum.oracle.com/repo/OracleLinux/OL7/latest/$basearch/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
gpgcheck=1
enabled=1

[ol7_UEKR4]
name=Latest Unbreakable Enterprise Kernel Release 4 for Oracle Linux $releasever ($basearch)
baseurl=http://yum.oracle.com/repo/OracleLinux/OL7/UEKR4/$basearch/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
gpgcheck=1
enabled=1

[ol7_addons]
name=Oracle Linux $releasever Add ons ($basearch)
baseurl=http://yum.oracle.com/repo/OracleLinux/OL7/addons/$basearch/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
gpgcheck=1
enabled=1

```

* 기본으로 ol7_addons 에 enabled=0 으로 세팅되어 있어서 enable=1로 세팅했음

![install docker on oel7 iaas](https://ironhub.github.io/assets/screenshots/install_docker_on_oel7.png)

```bash
[opc@iaas yum.repos.d]$ sudo systemctl start docker
[opc@iaas yum.repos.d]$ sudo systemctl enable docker
Created symlink from /etc/systemd/system/multi-user.target.wants/docker.service to /usr/lib/systemd/system/docker.service.
[opc@iaas yum.repos.d]$ sudo systemctl status docker
● docker.service - Docker Application Container Engine
   Loaded: loaded (/usr/lib/systemd/system/docker.service; enabled; vendor preset: disabled)
  Drop-In: /etc/systemd/system/docker.service.d
           └─docker-sysconfig.conf
   Active: active (running) since 화 2018-01-02 01:20:41 UTC; 43s ago
     Docs: https://docs.docker.com
 Main PID: 24434 (dockerd)
   CGroup: /system.slice/docker.service
           ├─24434 /usr/bin/dockerd --selinux-enabled --storage-driver devicemapper --storage-opt...
           └─24440 docker-containerd -l unix:///var/run/docker/libcontainerd/docker-containerd.so...

 1월 02 01:20:40 iaas dockerd[24434]: time="2018-01-02T01:20:40.466692570Z" level=warning ms...tem"
 1월 02 01:20:40 iaas dockerd[24434]: time="2018-01-02T01:20:40.503277853Z" level=info msg="...nds"
 1월 02 01:20:40 iaas dockerd[24434]: time="2018-01-02T01:20:40.503629138Z" level=warning ms...und"
 1월 02 01:20:40 iaas dockerd[24434]: time="2018-01-02T01:20:40.503770904Z" level=info msg="...rt."
 1월 02 01:20:40 iaas dockerd[24434]: time="2018-01-02T01:20:40.932805359Z" level=info msg="...ess"
 1월 02 01:20:41 iaas dockerd[24434]: time="2018-01-02T01:20:41.217849290Z" level=info msg="...ne."
 1월 02 01:20:41 iaas dockerd[24434]: time="2018-01-02T01:20:41.227594625Z" level=info msg="...ion"
 1월 02 01:20:41 iaas dockerd[24434]: time="2018-01-02T01:20:41.227643779Z" level=info msg="...2-ol
 1월 02 01:20:41 iaas dockerd[24434]: time="2018-01-02T01:20:41.247707919Z" level=info msg="...ock"
 1월 02 01:20:41 iaas systemd[1]: Started Docker Application Container Engine.
Hint: Some lines were ellipsized, use -l to show in full.
[opc@iaas yum.repos.d]$
```



#### Oracle Container Registry - Registration ####

[Oracle Container Registry - Registration ](http://container-registry.oracle.com/)

![Screenshot ](https://ironhub.github.io/assets/screenshots/OracleContainerRegistry.png)



#### Oracle WebLogic Container ####

[문서 참조](https://container-registry.oracle.com/pls/apex/f?p=113:4:9610497423608::NO::P4_REPOSITORY,AI_REPOSITORY,AI_REPOSITORY_NAME,P4_REPOSITORY_NAME:5,5,Oracle%20WebLogic%20Server,Oracle%20WebLogic%20Server&cs=3KrCuLJnkxQpwyy5R6Z7CC9kF1eB73ZOh5dggblvKtxibM8R05OCLZoOIIRXL_u3R2kRvYktA4pK0putUcyxiAw)

```bash
# docker run -d -p 7001:7001 container-registry.oracle.com/middleware/weblogic:12.2.1.3


[root@iaas 8aa9a970ed1fe75fd3a525efd09c4829b12f7e5f7ad64609f8bdd57a3b5b6c6e]# docker ps -a
CONTAINER ID        IMAGE                                                        COMMAND                  CREATED             STATUS                           PORTS                    NAMES
8aa9a970ed1f        container-registry.oracle.com/middleware/weblogic:12.2.1.3   "/u01/oracle/creat..."   About an hour ago   Created                                                   gifted_newton
3e58f8f7e424        container-registry.oracle.com/middleware/weblogic:12.2.1.3   "/u01/oracle/creat..."   About an hour ago   Up About an hour                 0.0.0.0:7001->7001/tcp   dreamy_mayer
f1433ae0820c        container-registry.oracle.com/middleware/weblogic:12.2.1.3   "/u01/oracle/creat..."   About an hour ago   Exited (137) About an hour ago                            keen_easley

# cd /var/lib/docker/containers

[root@iaas containers]# ls -alrt
total 16
drwx--x--x 11 root root  130 Jan  2 01:20 ..
drwx------  5 root root 4096 Jan  2 05:32 .
drwx------  3 root root 4096 Jan  2 05:34 
drwx------  4 root root 4096 Jan  2 06:09 3e58f8f7e4244739ed75ce4bedebc629af80685f15022d4474da6ba526bd837d

[root@iaas containers]# docker logs 3e58f8f7e4244739ed75ce4bedebc629af80685f15022d4474da6ba526bd837d | grep password
      ----> 'weblogic' admin password: cxQ7FWgV
admin password  : [cxQ7FWgV]
*  password assigned to an admin-level user.  For *

-----------  admin user 가 weblogic 이고, password 는 cxQ7FWgV 임을 확인할수 있다.

```

#### WebLogic Console ####

* http://<your_host>:7001/console 
*  admin user : weblogic
* password : cxQ7FWgV

![Weblogic Console](https://ironhub.github.io/assets/screenshots/WeblogicConsole.png)