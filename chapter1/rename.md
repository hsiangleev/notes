### 重新命名属性名(不能操作数组)
##### 如下json
```
{
    "_id" : 1.0,
    "name" : {
        "gge" : 18
    }
}
```

```
db.getCollection('user').update(
    {"_id": 1.0},
    {$rename: {"name.gge": "name.age"}}
)
```
##### 结果
```
{
    "_id" : 1.0,
    "name" : {
        "age" : 18
    }
}
```