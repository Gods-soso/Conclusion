## 数组的常用方法  

+ push ==> 在数组末尾追加元素，返回值是追加元素以后数组的长度，改变的是原数组
 + pop ==> 用来删除数组末尾的一个元素，返回值是被删除的那个元素，改变的是原数组
 + unshift ==> 在数组最前面添加元素，返回值时添加元素以后数组的长度，改变的是原数组
 + shift ==> 删除数组最前面的一个元素，返回值是被删除的元素，改变原数组
 + splice
    + 截取数组中的某些内容，按照数组的索引来截取
    + 语法 : splice(从哪一个索引位置开始，截取多少个[，替换的新元素])
    + []里面的参数不是必须的，可选可不选
    + arr.splice(0,2) 表示从第0个开始截取，截取2个
    + arr.splice(0,2,"laoyi","laoer","laosan") 表示从第0个开始截取，截取2个，替换成"laoyi","laoer","laosan"
    + 返回值是被截取的元素的集合，是一个数组
    + 改变的是原数组
```js
    var arr = [1,2,3,4]
    arr.splice(3,0,5) 
    console.log(arr) //[1,2,3,5,4]
```

+ reverse ==> 反转数组，返回值是反转以后的数组，改变的是原数组
+ sort ==> 数组排序
```js
arr.sort(function(a,b){
    return a-b  //从小到大
    return b-a  //从大到小
})
```
+ concat ==> 把多个数组进行拼接，不会改变原数组,而是返回一个新的数组
+ join 
    + 把数组里面的每一项内容链接起来，变成一个字符串
    + 可以自己定义每一项内容之间的连接符
    + 不会改变原数组
    + 语法： arr.join('链接数组的符号')
    + 如果不指定连接符，默认使用逗号链接
+ indexOf
    + 用来找到数组中某一项的索引
    + 语法: arr.indexOf("字符串")
    + 如果找到了，返回索引，number类型
    + 如果没有找到，返回-1
+ forEach
    + 和for循环一样，就是用来遍历数组的
    + 语法: arr.forEach(function(item,index,array){
        // 数组里面有多少个元素，函数就执行多少次
        // 参数
        //第一个形参：item表示，本次循环到的数组元素的值
        //第二个形参: index表示，本次循环到是第几个数组元素
        //第三个形参: array表示当前正在循环的数组
    })
+ map
    + 和forEach类似，只不过可以对数组中的每一项进行操作，返回一个新的数组
    + 语法：
    arr.map(function(item,index,array){
        // 数组里面有多少个元素，函数就执行多少次
        // 参数同forEach
        // 返回值：一个新的数组
    })
```js
var numbers = [1, 4, 9];
var doubles = numbers.map(function(num) {
  return num * 2;
});

// doubles数组的值为： [2, 8, 18]
// numbers数组未被修改： [1, 4, 9]
```
+ filter
    + 和map使用方式类似，按照我们的条件进行筛选数组
    + 把原始数组中符合条件的筛选出来，组成一个新的数组返回
    + 语法：
        arr.filter(function(item,index,array){
        // 数组里面有多少个元素，函数就执行多少次
        // 参数同forEach
        // 返回值：一个新的数组，里面都是符合条件的数组元素
        // 当遍历到一个元素item，如果本次return true说明符合条件
        // 当遍历到一个元素item，如果本次return false说明不符合条件
        })
```js
function isBigEnough(element) {
  return element >= 10;
}
var filtered = [12, 5, 8, 130, 44].filter(isBigEnough);
// filtered is [12, 130, 44] 
```
+ slice
  + 返回一个新的数组，新数组由 begin 和 end 决定（包括 start，不包括end）。原始数组不会被改变。
```js
var arr=[1,2,3,4,5]
var newArr=arr.slice(1,3)
console.log(newArr) //[2,3]
```

