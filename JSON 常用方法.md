#JSON 常用方法

`概念`
>JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式，采用完全独立于语言的文本格式，是理想的数据交换格式。同时， JSON是 JavaScript 原生格式，这意味着在 JavaScript 中处理 JSON数据不须要任何特殊的 API 或工具包

`基础结构`
```
// 键值对的集合，值的有序列表 **必须用双引号包含键值**
var JsonObj = {"name":"Hannah", "like":["看书", "电影", "晨跑"]}; 

//数组
var jsonArr = [
  {
    "name": "tom",
    "type": "cat"
  },
  {
    "name": "jack",
    "type": "mouse"
  }
]

//对象
var jsonObj = {
  "like": ["看书", "电影", "晨跑"],
  "book": ["数字城堡", "刻意练习", "老人与海"]
}
```
**1.JSON对象和JSON字符串的转换**
`字符串转对象`
```
var jsonObject= JSON.parse(jsonstr);
```
`对象转字符串`
```
var jsonstr =JSON.stringify(jsonObject);
```
> JSON.stringify() 方法的可选参数space，可以指定缩进用的空白字符串，用于美化输出(pretty-print)。
 > space参数是个数字，它代表有多少的空格；上限为10。该值若小于1，则意味着没有空格；如果该参数没有提供（或者为null）将没有空格。
 > var formatJsonStr=JSON.stringify(jsonObject,undefined, 2);

**2.JSON字符串替换**
```
将所有的’ \" ’ 替换成’ " ’这里的gm是固定的，g表示global，m表示multiple
var jsonStr=jsonStr.replace(new RegExp('\\(要替换的内容)"',"gm"), '"(替换成的内容)' );
```
**3.遍历JSON对象和JSON数组**
`遍历JSON对象`
```
var packJson  = {
  "name":"Liza", 
  "password":"123"
};
for(var k in packJson ){  //遍历packJson 对象的每个key/value对,k为key
  alert(k + " " + packJson[k]);
}
```
`遍历JSON数组`
```
var packJson = [
  {
    "name":"Liza", 
    "password":"123"
  },
  {
    "name":"Mike", 
    "password":"456"
  }
];
for(var i in packJson){  //遍历packJson 数组时，i为索引
  alert(packJson[i].name + " " + packJson[i].password);
}
```

