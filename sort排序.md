#sort排序

`sort() 方法用于对数组的元素进行排序`
`语法: arrayObject.sort(sortby)`
`参数:sortby,可选.规定排序顺序。必须是函数`
`返回值:对数组的引用。注意:数组在原数组上进行排序，不生成副本`
> 说明：
> 如果调用该方法时没有使用参数，将按字母顺序对数组中的元素进行排序，说得更精确点，是按照字符编码的顺序进行排序。
> 如果想按照其他标准进行排序，就需要提供比较函数，该函数要比较两个值，然后返回一个用于说明这两个值的相对顺序的数字。比较函数应该具有两个参数 a 和 b，其返回值如下
> - 若 a 小于 b，在排序后的数组中 a 应该出现在 b 之前，则返回一个小于 0 的值。
> - 若 a 等于 b，则返回 0。
> - 若 a 大于 b，则返回一个大于 0 的值。

```
按字母顺序排序
var arr =["George","John","Thomas","James","Adrew","Martin"]
arr.sort();
```
![Alt text](./1615278199976.png)
```
按数字大小排序
var arr = ["10","5","40","25","1000","1"]
arr.sort(function(a,b){return a-b})
```
![Alt text](./1615343366281.png)

###localeCompare() 方法
`用本地特定的顺序来比较两个字符串`
`语法: stringObject.localeCompare(target)`
`参数:target,要以本地特定的顺序与 stringObject 进行比较的字符串。`
`返回值:说明比较结果的数字。`
> 说明：
> 此方法将一个字符串与另一个字符串进行比较，返回一个数字(负数，0，正数)，该数字指示当前字符串是小于，等于还是大于根据语言环境传递的字符串。
> 如果 stringObject 小于 target，则 localeCompare() 返回小于 0 的数。如果 stringObject 大于 target，则该方法返回大于 0 的数。如果两个字符串相等，或根据本地排序规则没有区别，该方法返回 0。
> a.localCompare(b) – 升序 ; b.localCompare(a) – 降序
![Alt text](./1615346723600.png)
