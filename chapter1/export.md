### 进入mongodb的bin目录
##### 1. 数据导出
+ -d: 数据库名称
+ -c: 表名
+ -o: 存储路径
+ --type: 导出类型
+ -f: 导出的数据
```
mongoexport -d test -c blog -o G:\users.json --type json -f  "_id,data,user"
```
##### 2. 数据导入
+ -d: 数据库名称
+ -c: 表名
+ --file: 路径
+ --type: 导出类型
```
mongoimport -d test -c us --file G:\users.json --type json
```