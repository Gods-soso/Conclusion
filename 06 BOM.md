## BOM 浏览器对象模型

+ Browser Object Model,顶级对象window
    + 可以获取浏览器的相关信息(窗口大小)
      + window.innerHeight
      + window.innerWidth
    + 操作浏览器进行页面跳转
      + history对象
        + history.back() 回退
        + history.forward() 前进
    + 获取浏览器地址栏的信息
      + location对象
        + location.href:浏览器里面完整的url地址，会把中文编程url编码的格式，也可以赋值
        + location.hash:浏览器里面url地址里面#后面的部分 (onhashchange事件)
        + location.reload():重新加载一遍页面，就相当于刷新,不能再全局调用
        + location.assign():加载指定页面，加载当前页面就相当于刷新
        + location.replace():指定页面替换掉当前的页面
    + 操作浏览器的滚动条
      + onscroll 浏览器滚动事件
      + scrollTop的获取方法
        + document.body.scrollTop
        + document.documentElement.scrollTop
        + IE浏览器
            + 没有DOCTYPE声明的时候，用这两个都行
            + 有DOCTYPE声明的时候，只能用document.documentElement.scrollTop
        + Chrome和FireFox
          + 没有DOCTYPE声明的时候,用document.bdoy.scrollTop
          + 有DOCTYPE声明的时候，用document.documentElement.scrollTop
        + Safari
          + 两个都不用，使用一个单纯的方法：window.pageYOffset
```js
 // 封装一个方法用来获取页面滚动的距离
function getScroll(){
    if(window.pageYOffset){
        return {
            top:window.pageYOffset
            left:window.pageXOffset
        }
    }else if(document.documentElement.scrollTop){
        return {
            top:document.documentElement.scrollTop
        left:document.documentElement.scrollLeft
        }
    }else{
        return {
            top:document.body.scrollTop
            left:document.body.scrollLeft
        }
    }
}
```
+ 浏览器的信息
    + navigator对象
    + navigator.userAgent
                ==> 获取浏览器的整体信息
    + navigator.appName
                ==> 获取浏览器的名称
    + navigator.appVersion
                ==> 获取浏览器的版本号
    + navigator.platform
                ==> 获取的是当前计算机的操作系统
+ 让浏览器出现一个弹框(alert/confirm/prompt)


+ 定时器 ：setTimeout 和 setInterval
```js
//1.setTimeout 倒计时定时器
var timer1 = setTimeout(function(){},time)
//time时间到后执行函数，只执行一次
//返回值：页面中的第几个定时器
clearTimeout(timer1); // 关闭定时器
//2.setInterval 间隔定时器
var timer2 = setInterval(function(){},time)
//每间隔time时间就执行一次
clearInterval(timer2) 
```

  