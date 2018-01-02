---
layout: post 

title: Docker install on Oracle Linux 7 

date: 2018-01-02 09:50:12 

author: C.W.Kim 

categories: Iron

tags: OEL Docker 
---
### Docker install on Oracle Linux 7 ### 
> Oracle Linux 7 에 Docker를 인스톨하는 과정

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

[install docker on oel7 iaas](https://ironhub.github.io/assets/screenshots/install_docker_on_oel7.png)

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

[Screenshot ](https://ironhub.github.io/assets/screenshots/OracleContainerRegistry.png)

#### Oracle WebLogic Container ####



