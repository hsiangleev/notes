
### 删除对象的属性或把数组的其中一项变成null
##### 有以下json
```
{
    "_id" : 1.0,
    "arr" : [ 
        {
            "item" : "A",
            "score" : 5.5
        }, 
        {
            "item" : "B",
            "score" : 4.0,
            "answers" : [ 
                {
                    "q" : 1.0,
                    "a" : 0.0
                }, 
                {
                    "q" : 1.0,
                    "a" : 0.0
                }
            ]
        }
    ]
}
```
1. $unset操作符删除一个指定的字段
```
// 删除arr数组的第一项的score属性
db.getCollection('user').update(
    {"_id": 1.0},
    {$unset: {"arr.0.score": 1}}
)
```
2. 当匹配到的是数组元素，$unset替换指定的元素为null而不是删除掉指定的元素，此行为保持数组大小和位置不变；
```
// 把数组arr的第二项的answers的第二项的值变为null
db.getCollection('user').update(
    {"_id": 1.0},
    {$unset: {"arr.1.answers.1": 1}}
)
```
##### 结果为
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
                }, 
                null
            ]
        }
    ]
}
```