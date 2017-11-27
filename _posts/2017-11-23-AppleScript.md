---
layout: post 

title: AppleScript 

date: 2017-11-23 18:00:26 

author: C.W.Kim 

categories: Iron

tags:   
---
### AppleScript ### 
> AppleScript 는 Mac 앱 혹은 기능을 마치  쉘 스크립트 처럼 자동화하여 사용하는 방법이다.
>
> AppleScript는 최종으로 실행형 App으로 변환이 가능하다.
#### Examples #### 
> 하루 정도 걸린것 같음. - 애플스크립트 매뉴얼 대충 보고 아래와 같은 코드 짜는 것.

```applescript
-- iTerm , Typora 앱이 있다고 가정
-- alert 메시지 
-- => iTerm run script 수행 
-- => 쉘스크립트가 다 수행되고 iterm의 tab 이 닫힐때까지 looping 
-- => 파일을 읽는 쉘 스크립트를 수행하면 typora에 로딩할 파일을 읽는다
-- ==> typora 앱 + 로딩할 파일 수행 


display alert "마크다운 블로그 템플릿 빌더입니다. 
#MarkDown
#Jekyll 
#GitHub.io"
set tobeexecuted to "run.sh"
tell application "iTerm"
	open tobeexecuted
	set cwindow to get current window of application "iTerm"
	set ctab to get current tab of cwindow
	repeat
		try
			delay 3
			set otab to get get current tab of cwindow
			if otab is not equal to ctab then
				break
			end if
		on error
			exit repeat
		end try
	end repeat
	
	tell application "System Events"
		set md to do shell script "tail current.file "
		tell application "Typora"
			open md
		end tell
	end tell
	
end tell


```