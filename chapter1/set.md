### 更新或添加属性
##### 初始json
```
{
    "_id" : 1.0,
    "arr" : [ 
        {
            "item" : "A"
        }, 
        {
            "item" : "B",
            "score" : 4.0,
            "answers" : [ 
                {
                    "q" : 1.0,
                    "a" : 0.0
                }
            ]
        }
    ]
}
```
##### 添加属性
```
db.getCollection('user').update(
    {"_id": 1.0},
    {$set: {"arr.0.score": 10}}
)
```
##### 更新属性
```
db.getCollection('user').update(
    {"_id": 1.0},
    {$set: {"arr.1.score": 10}}
)
```
##### 结果
```
{
    "_id" : 1.0,
    "arr" : [ 
        {
            "item" : "A",
            "score" : 10.0
        }, 
        {
            "item" : "B",
            "score" : 10.0,
            "answers" : [ 
                {
                    "q" : 1.0,
                    "a" : 0.0
                }
            ]
        }
    ]
}
```