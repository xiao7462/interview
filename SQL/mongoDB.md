MongoDB学习记录

# 安装
直接安装
```
sudo apt-get install mongodb
```
`pgrep mongo -l`查看是否已经启动
![enter description here](http://pxne3dnp1.bkt.clouddn.com/xiaoshujiang/1568194734282.png)



# mongodb基本操作
## database基本操作

* 创建数据库    
`use tangxing` 
* 插入数据  
`db.tangxing.insert({"name":'tangxing'})`
* 删除数据库
`db.dropDatabase()`
* 删除集合
`db.collection.drop()`

* 查看所有数据库
`show dbs`

* 插入文档
`db.test.insert({"name":"tangxing"})`
* 查找文档
`db.test.find()`
* 更新文档
![enter description here](http://pxne3dnp1.bkt.clouddn.com/xiaoshujiang/1568174313480.png)
用
使用 `$set` 来操作 
```bash
db.test100.update({"name":"xiangwang"},{"name":"xiaozhang"}) # 将name为xinagwang的数据更新为"{name:"xiazhao"}"

db.test100.update({"name":"wang"}, {$set:{name:"xiaohong"}}) # 把name为xiaowang的数据的name值更新为xiaozhang 
```
* 删除集合
`db.集合名称.remove(<query> , {justOne: ture or false})

* 比较运算符
![enter description here](http://pxne3dnp1.bkt.clouddn.com/xiaoshujiang/1568174335445.png)


![enter description here](http://pxne3dnp1.bkt.clouddn.com/xiaoshujiang/1568174354530.png)

![enter description here](http://pxne3dnp1.bkt.clouddn.com/xiaoshujiang/1568174636873.png)

![enter description here](http://pxne3dnp1.bkt.clouddn.com/xiaoshujiang/1568174798016.png)

小于等于
`db.stu.find({age:{$lte:18}})`

AND
`db.stu.find({age:18, hometown = '桃花岛'})`

* 正则表达式
![enter description here](http://pxne3dnp1.bkt.clouddn.com/xiaoshujiang/1568175487590.png)

`db.stu.find({stu:/^abc/})`

* skip() , limit()
`db.products.find().skip(2).limit(2) #skip跳过2个，limit再选择2个`

* 自定义查询
使用  $where后面写函数，返回满足条件的数据，查询年龄大于30的学生   `this.age` 代表从前往后查询    
```sql 
db.stu.find(
    $where:function(){
        return this.age>30; 
    }
)
```

只返回想要的字段
![enter description here](http://pxne3dnp1.bkt.clouddn.com/xiaoshujiang/1568176329522.png)
`db.stu.find({},{name:1 , _id:0})`   `_id`默认会显示，不显示的话设置为0

排序
![enter description here](http://pxne3dnp1.bkt.clouddn.com/xiaoshujiang/1568176531910.png)


* count 
`db.collection.find({条件}).count()`
`db.collection.count({条件})`

* distinct 
`db.stu.distinct("age")`


## 数据的备份
![enter description here](http://pxne3dnp1.bkt.clouddn.com/xiaoshujiang/1568178300223.png)