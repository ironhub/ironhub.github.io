---
layout: post 

title: mongo db update 

date: 2018-01-10 14:53:20 

author: C.W.Kim 

categories: Iron

tags: mongodb 
---
### mongo db update ### 
> Mongodb 를 default 로 설치 , 설정했더니, 
>
> 중국의 어떤 넘이 들어와서 데이터를 날리더라.
>
> 그래서......

#### port & authentication 추가 ####

```bash
mongod --port 23232 --auth  --dbpath=/home/opc/node/mongodb --logpath=/home/opc/log/mongo.log 

mongo --port 23232 -u adminx -p admin123 
```



```bash
db.createUser({
user:"adminx",pwd:"admin123",roles:[{role:"userAdminAnyDatabase",db:"admin"}]})

db.createUser({
user:"adminx",pwd:"admin123",roles:[{role:"userAdminAnyDatabase",db:"admin"}]})

use yourdb
db.createUser({ user:"realuser", pwd:"real123", roles: [ {role: "readWrite", db:"yourdb"}, {role:"read",db:"admin"}]})


# superuser role is "root" ....


```




