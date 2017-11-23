---
layout: post 

title: Go Lang Getting started 

date: 2017-11-23 16:43:37 

author: C.W.Kim 

categories: Iron

tags: golang setup 
---
### Go Lang Getting started ### 
> GoLang is an open source, compiled and statically typed programming language created by Google. 
### Why Golang ###

Here are some of the pros which I found in choosing Go

- Concurrency is an inherent part of the language. As a result writing multithreaded programs is a piece of cake. This is achieved by Goroutines and channels which we will discuss later in the upcoming tutorials.
- Golang is a compiled language. The source code is compiled to native binary. This is missing in interpreted languages such as JavaScript used in nodejs.
- The language spec is pretty simple. The [entire spec](https://golang.org/ref/spec) fits in a page and you can even use it to write your own compiler :)
- The go compiler supports static linking. All the go code can be statically linked into one big fat binary and it can be deployed in cloud servers easily without worrying about dependencies.

### Installation ###

[Download here](https://golang.org/dl/)

> On Linux  / Command Line 
>
> curl -O https://storage.googleapis.com/golang/go1.9.2.linux-amd64.tar.gz -k
>
> sudo tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz
>
> 
>
> vi ~/.bashrc
>
> export PATH=.:/usr/local/go/bin:$PATH
>
> export GOPATH=$HOME/go
>
> export GOBIN=$HOME/go/bin
>
> 

### Hello, World ###

$GOPATH/src/hello/helloworld.go

```go
// Go Lang
package main

import "fmt"

func main() {
	fmt.Println("Hello, World!~")

}
```
- 모든 go 파일에는 package <name> 으로 시작해야 한다.
- "fmt" 패키지가 import된다.
- func main()은 프로그램 실행을 시작하는 펑션이고, main() 은 main package 에 있어야 한다

#### Go 프로그램 실행 ####

- go run $GOPATH/src/hello/helloworld.go
- go install hello
- go build -o hellox $GOPATH/src/hello/helloworld.go ( 이것은 마치 gcc)

---

```sh
$GOPATH 
	|- bin 
	|- - hello
	|- src
	|- - hello
	|- - - helloworld.go
```

 