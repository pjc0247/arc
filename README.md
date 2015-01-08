# ARC

ActiveRecord on C++

모델 정의
----
```C++
arc::model ("account")
  .has_n("post")
  .has_n("comment")
  .finalize();

arc::model ("post")
  .has_n("comment")
  .belongs_to("account")
  .finalize();
  
arc::model ("comment")
  .belongs_to("account")
  .belongs_to("post")
  .finalize();
```

쿼리
----
```C++
auto rows = arc::model::begin("account")
  .all();
```
```C++
auto posts = some_account
  .n("post")
    .all();
```
```C++
auto post = 
  arc::model::begin("post").get(1); // 1번째 글 가져오기
  
auto author = post
  .o("account");
```


* [choco::orm](https://github.com/pjc0247/choco_for_nnext/tree/master/src/choco_2/choco/orm)
