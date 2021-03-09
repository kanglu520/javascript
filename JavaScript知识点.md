#JavaScript知识点

####this
> EC（执行上下文）：当前代码执行的环境
>  + 全局执行上下文
>  + 私有执行上下文（函数执行）
>  + 块级作用域（let / const）
>  this ：执行主体（谁吧这个函数执行的）
>  三思而后型：函数的执行主体是谁，和在哪定义的，以及在那执行的都没有必然的联系
>  this：执行主体事对象数据类型的（特殊情况：null / undefined）
>  函数在那定义决定他的scope，执行决定他的上下文，但影响不了他的this

**1.给元素的某个事件行为绑定方法，当行为触发，方法执行的时候，方法中的this一般都是元素本身**
```
<div id="box"></div>
let box = document.getElementById("box");
box.onclick = function(){
	//事件绑定期间，函数是不执行的，只是创建了一个函数，只有当事件触发，浏览器才会把绑定的方法执行（不是自己执行的，是浏览器帮我们执行的，所以我们无法直接传递一些实参信息给函数）
	console.log(this); => 但函数执行的时候，this是#box元素对象
}
```
```
<div id="box"></div>
let box = document.getElementById("box");
function func(){
	console.log(this);
	return function anonymous(){};
}
box.onclick = func; // 把func函数本身复制给元素的事件行为，从而完成事件绑定；当点击元素的时候，执行的是func这个方法
box.onclick = func(); // 先把func执行，把函数执行返回的结果赋值给元素的点击行为 => box.onclick = function anonymous(){} 点击元素执行的是anonymous方法
```
```
IE6-8低版本浏览器中,基于attachEvent实现DOM2的事件绑定，方法执行，方法中的this不是元素本身，而是window
box.attachEvent("onclick",function(){
	console.log(this === window);
})
```
**2.方法执行，看方法前面是否有“点”，“点”前面是谁，this是谁，没有“点”，this一般指向的是window / undefined**
```
function func(){
	console.log(this)
}
var obj = {
	fn:func
}
func(); // 方法中的this是undefined
obj.fn(); //方法中的this是obj
```
```
如果是严格模式下（“use strict”），方法执行，前面没有点，也就是没有执行的主体，所以this是undefined；在非严格模式下，没有点认为执行主体都是全局对象window
```
![Alt text](./1604298278624.png)

####document.getElementById()
```
let box = document.getElementById('box')
#box{
    box-sizing: border-box;
    width: 200px;
    height: 200px;
    border: 3px solid lightblue;
}
```
> ![Alt text](./1604539747856.png)
> 通过方法获取的元素是对象数据类型的值
> console.log(typeof box);  //=> object
> 用console.dir();可以看到很全的信息
> ![Alt text](./1604540438065.png)

####console.dir
```
console.dir(box); //基于dir,可以看到一个对象的详细信息
 - id：操作元素的id值
 -  className：操作元素的class样式类的值
 -  innerHTML：操作元素的内容（可以识别标签）
 -  innerText：和innerHTML的区别是不能识别标签
 -  style：操作元素行内样式
 -  tagName： 获取元素的标签名（一般大写）
```


