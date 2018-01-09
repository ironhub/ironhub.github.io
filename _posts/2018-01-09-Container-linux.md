---
layout: post 

title: Container linux 

date: 2018-01-09 11:10:09 

author: C.W.Kim 

categories: Iron

tags: coreos rkt kubernetes 
---
### Container linux ### 
>
> Container Linux by CoreOS, originally named CoreOS Linux, is an open source operating system (OS) that provides the functionality required to deploy and manage applications within [containers](http://searchservervirtualization.techtarget.com/definition/container-based-virtualization-operating-system-level-virtualization).Based on the [Linux](http://searchenterpriselinux.techtarget.com/definition/Linux) kernel, Container Linux by CoreOS is designed for massive scale, with management features to ensure minimal operational overhead.
>CoreOS uses systemd -- another central daemon in the OS package -- for initialization and process management. CoreOS recommends that the user rely on Rkt or on open source [Kubernetes](http://searchitoperations.techtarget.com/definition/Google-Kubernetes) for cluster management.



---

>rkt (pronounced like a "rocket") is a CLI for running application containers on Linux. rkt is designed to be secure, composable, and standards-based.
>
>A Security-minded , standards-based container engine .
>
>

Some of rkt's key features and goals include:

Pod-native: rkt's basic unit of execution is a pod, linking together resources and user applications in a self-contained environment.
Security: rkt is developed with a principle of "secure-by-default", and includes a number of important security features like support for SELinux, TPM measurement, and running app containers in hardware-isolated VMs.
Composability: rkt is designed for first-class integration with init systems (like systemd, upstart) and cluster orchestration tools (like Kubernetes and Nomad), and supports swappable execution engines.
Open standards and compatibility: rkt implements the appc specification, supports the Container Networking Interface specification, and can run Docker images and OCI images. Broader native support for OCI images and runtimes is in development.