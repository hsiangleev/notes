### 1. 更新数组的某一项不确定位置的值
##### 初始
```
{
    "_id" : 1.0,
    "arr" : [ 
        3, 
        4, 
        5, 
        20
    ]
}
```
```
// 把数组arr值为20的变成10
db.getCollection('user').update(
    {"_id": 1.0, "arr": 20},
    {$set: {"arr.$": NumberInt(10)}}
)
```
##### 结果
```
{
    "_id" : 1.0,
    "arr" : [ 
        3, 
        4, 
        5, 
        10
    ]
}
```
### 2. 
```
{
    "_id" : 1.0,
    "arr" : [ 
        {
            "a" : 1,
            "b" : 10
        }, 
        {
            "a" : 2,
            "b" : 20
        }, 
        {
            "a" : 3,
            "b" : 30
        }
    ]
}
```
```
// 更新数组arr里面属性a为2的，把当前位置的b变成200
db.getCollection('user').update(
    {"_id": 1.0, "arr.a": 2},
    {$set: {"arr.$.b": NumberInt(200)}}
)
```
##### 结果
```
{
    "_id" : 1.0,
    "arr" : [ 
        {
            "a" : 1,
            "b" : 10
        }, 
        {
            "a" : 2,
            "b" : 200
        }, 
        {
            "a" : 3,
            "b" : 30
        }
    ]
}
```