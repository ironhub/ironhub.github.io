---
layout: post 

title: This blog template maker 

date: 2017-11-21 14:30:03 

author: C.W.Kim 

categories: Iron

tags: nodejs blog template 
---
### This Blog Markdown Template Maker implemented by Node.js ### 
> Node.JS를 이용하여 이 블로그의 마크다운 템플릿을 만들어 봤습니다.
>
> 원리는 그냥 파일에다가 쓰는것이구요. 로컬에 Node.js를 통하여 템플릿을 만드는 것으로 하였습니다.
#### Node.JS implementation #### 
* file.js 를 활용하여 파일 쓰기
* date-formatter를 활용하여 formatted date string으로 변환
* readline 을 활용하여 콘솔에서 input을 처리 
##### [Node.JS **Source Code**]#####

```javascript 
const readline = require('readline') ;
const fs = require('fs') ;
const format = require('date-format') ;

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout 
}) ;


const targetDir = "/Users/iron/_posts/" ;
var title = "Default title" ;
var sdate = new Date() ;
var date = format.asString('yyyy-MM-dd hh:mm:ss', sdate ) ; 
var author = "C.W.Kim" ;
var category = "Iron" ;
var tags = `${title}` ;

rl.question('******* Make Your Blog Template ********  \n > Title (Enter: Untitled ) :  ' , (answer) => {
    
    if (answer == "") {
        title = "Untitled" ;
    } else {
        title  = answer ;
    } 
    console.log(`.....you answered  : ${title}`) ;
        //rl.close() ;
    rl.question(' > Author (Enter: C.W.Kim ) : ', (answer) => {
        if (answer == "") {
            author = "C.W.Kim" ;
        }  else {
            author = answer ;
        }
        console.log(` .....you answered  : ${author}`) ;

        rl.question(' > Which of the following categories do you select : \n (i)ron, (s)wift , (e)nglish )  ) : ', (answer) => {
            if (answer == "s" || answer == "S" ) {
                categroy = "Swift" ;
            }  else if ( answer == "e" || answer == "E" ) {
                category = "English" ;
            }  else {
                category = "Iron" ;
            }
            console.log(`.....you answered  : ${category}`) ;
            rl.question(' > Write tags about this content  : ', (answer) => {
                if ( answer == "" ) {
                    tags = " " ;
                } else {
                    tags = answer ;
                } 
                console.log(`.....you answered  : ${tags}`) ;
                var header = `---\nlayout: post \n\ntitle: ${title} \n\ndate: ${date} \n\nauthor: ${author} \n\ncategories: Iron\n\ntags: ${tags} \n---\n` ;
                var body =  `### ${title} ### \n` +
                            "> Architecture is ... \n" +
                            "#### Microservices Architecture #### \n"+
                            "> The microservice architectural style \n" +
                            "* Independent **deployable** services \n"+
                            "* Highly decoupled \n" +
                            "```javascript \n" +
                            "// Javascript manner \n" +
                            "```\n" +
                            "![BlockChain](https://ironhub.github.io/assets/BlockChain@3x.png)\n "
                console.log(header+body) ;                
                const filename = targetDir + format.asString('yyyy-MM-dd-', sdate ) + title.replace(/ /g,"-") + ".md" ;
                fs.writeFile(filename ,header+body, (error) => {
                    if (error) {
                        console.log(error + " is occurred !!!!") ;
                    } 
                    console.log("Successfully wrote data!!! ") ;
                } ) ;

                fs.writeFile("/Users/iron/blog/current.file",filename+"\n",(error)=> {
                    if (error) {
                        console.log(error + " is occurred !!!") ;
                    }
                    console.log(" Successfully wrote meta data!!!! ") ;
                }) ;
                rl.close() ;
            } ) ;

        } ) ;
    } ) ;
    
}) ;


```

#### Shell Script ####

```sh
#!/bin/bash
cd /Users/iron/blog
npm run start
```



### 여기에서 한 걸음 더 나아가 ###

---

Mac 에서 자동으로 처리하는 앱을 **AppleScript** 를 이용하여 만들수 있음.


```applescript
display alert "마크다운 블로그 템플릿 빌더입니다. 
#MarkDown
#Jekyll 
#GitHub.io"

set tobeexecuted to "/Users/iron/blog/run.sh"

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
		set md to do shell script "tail /Users/iron/blog/current.file "

	tell application "Typora"
			open md
		end tell
	end tell
	
end tell


```
---

