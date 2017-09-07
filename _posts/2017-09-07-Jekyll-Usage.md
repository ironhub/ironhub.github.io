---
layout: post

title:  "Jekyll 사용"

date:   2017-09-07 10:53:59

author: C.W.Kim

categories: Iron

tags: Jekyll Usage
---

### Jekyll 사용###



> Jekyll + github pages 를 활용하기전에 Jekyll에 대해 알아보자

* install 

* jekyll new ***sitename***

* jekyll serve  or bundle exec jekyll serve

  ![jekyllServe]({{site.url}}/assets/jekyllServe.png)

  ​

##### Jekyll Directory Structure#####

```markdown
[친절한링크](http://jekyllrb.com/docs/structure/) 에서 따옴.

├── _config.yml
├── _data
|   └── members.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.md
|   └── on-simplicity-in-technology.md
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.md
|   └── 2009-04-26-barcamp-boston-4-roundup.md
├── _sass
|   ├── _base.scss
|   └── _layout.scss
├── _site
├── .jekyll-metadata
└── index.html # can also be an 'index.md' with valid YAML Frontmatter
```

##### jekyll Directory Structure 설명#####

| ile/Directory                            | Description                              |
| ---------------------------------------- | ---------------------------------------- |
| `_config.yml`                            | 설정 데이터를 저장 [설정상세](http://jekyllrb.com/docs/configuration/) |
| `_drafts`                                | 퍼블리싱 안할 포스트를 저장하며, 날짜 없이 `title.MARKUP` 이런식으로 쓴다. |
| `_include`                               | 레이아웃과 포스트에서 재사용하는 공통부분 리퀴드 태그 {% include file.ext %} 는 _includes/file.ext 를 포함할 수 있다. |
| `_layouts`                               | 포스트를 감싸는 템플릿들. YAML Front Matter 안에서 설정하는 바로 그 레이아웃 . 리퀴드 태그 ( liquid tag) 인 {{content}} 가 웹페이지의 주입 컨텐트로 활용된다. |
| `_posts`                                 | 동적 컨텐트 - ~~과연동적이냐마는~~  - 를 넣는 곳이며, 네이밍 컨벤션을 지켜야 한다. YEAR-MONTH-DAY-Title.MARKUP `2017-09-07-이런저런자질구레한포스트.md` 이런 식으로 컨벤션을 지켜야 함 `permalinks` 는 각 포스트마다 커스터마이징 할수 있으며 날짜와 마크업 언어는 단지 파일 이름으로 결정된다. |
| `_data`                                  | 잘 포맷화된 사이트 데이터를 여기에 넣는다. Jekyll 엔진이 이 디렉토리에 있는 데이터파일 - 예: `.yml``.yaml` `.json` `.csv`  을 자동 로딩하게 될 것이고, `site.data`  라는 이름으로 접근 가능하고,그 디렉토리에  `members.yml`이 있다면  `site.data.members`라는 이름으로 접근할 수 있다. |
| `_sass`                                  | 사이트에 사용하는 스타일을 정의하는 싱글 스타일 시트인 main.css 에서 처리하게 될 main.scss 안으로 임포트할수 있는  sass 부분들을 넣어 놓는 곳이다.   ~~아놔 해석하기 싫다.~~ |
| `_site`                                  | jekyll 이 처음에  변환하여 생성한 사이트를 가져다 놓는곳인데 .gitignore 에 놓는게  좋다. |
| `.jekyll-metadata`                       | jekyll 엔진이 사이트 빌드할때 파일 수정이 있었는지 무시할수 있게 … .gitignore에 놓는게 좋다. |
| `index.html` or `index.md` 와 다른 HTML, Markdown, Textile 파일들 | YAML Front Matter 섹션을 포함하여 제공하면, Jekyll에 의해 변환될것이고 , 사이트 루트디렉토리 혹은 위에 명시 안된 다른 디렉토리에 있는 다른 `.html` `.markdown`  `.textile`  파일도 똑같은 룰이 적용된다. |
| 다른 파일과 폴더들                               | 위에 언급안된 기타 다른 파일과 폴더 - `css` `images` `favicon.ico` - 기타 jekyll을 적용한 사이트들이 제 맘대로 써왔던것... |




