---
layout: post

title:  "Jekyll install on macOS Sierra"

date:   2017-09-07 10:53:59

author: C.W.Kim

categories: Iron

tags: Jekyll Install Mac
---

### Jekyll 을 macOS Sierra에 인스톨하기###

> jekyll 을 macOS Sierra에 인스톨하려니, 
>
> 인터넷에서 가져온 바이너리는 실행을 할 수 없어서 제대로 인스톨이 불가해서
>
> 찾아보니 …. Homebrew 인스톨 -> Ruby 인스톨 -> Jekyll 인스톨 
>
> [jekyll 인스톨 문제 해결 ](https://github.com/jekyll/jekyll/issues/4093)

* Homebrew Install

  > /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

* Jekyll Install - 루비 인스톨 후 jekyll 인스톨 

  > $ brew remove ruby
  >
  > $ brew install ruby
  >
  > $ brew link libyaml
  >
  > $ sudo gem install jekyll bundler





