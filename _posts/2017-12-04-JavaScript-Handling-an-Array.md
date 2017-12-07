---
layout: post 

title: JavaScript Handling an Array 

date: 2017-12-04 14:47:27 

author: C.W.Kim 

categories: Iron

tags: Javascript, Array , Removing 
---
### JavaScript Handling an Array ### 
> An example of Handling an array in JavaScript


```javascript 
// Removing elements
// splice(인덱스,1) 이면 removing , splice(인덱스,0,item) 이면 업데이트네

var myList = ["Hello","World","Good","Morning"]

myList.splice(1,1) // 인덱스 1에 1개만큼 World가 사라짐.

// shift() : removing, unshift() : adding - 배열의 첫머리에 
myList.shift() // 배열의 첫번째가 사라짐. Hello 

// pop() : removing , push() : adding - 배열의 끝자락에 
myList.pop() // 배열의 마지막 요소가 사라짐 . Morning

// indexOf
list.splice( myList.indexOf('Good'), 1 );

```

