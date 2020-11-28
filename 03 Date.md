## 日期对象

```js
var date = new Date()
// 不传参数时 返回当前时间
//传参数时  返回你设置的时间
var nowTime = +new Date()
//不传参数 返回当前时间的时间戳
//传参数 返回指定时间的时间戳
```
+ getFullYear() 得到年份
+ getMonth() 得到月份 月份从0开始计算表示1月,11表示12月
+ getDate() 得到日期，该月的几号
+ getDay() 星期几，0表示星期天
+ getHours()  getMinutes  getSeconds  时分秒
+ getTime() 获得该日期的时间戳
  
```js
//倒计时案例
 function countDown(time){
     //获取当前时间的时间戳（总毫秒数）
    var nowTime= +new Date();      
    //获取输入时间的时间戳     
    var inputTime= +new Date(time);   
    // 剩余时间的总秒数        
    var times=(inputTime-nowTime)/1000;  
    //剩余的天数       
    var day=parseInt(times/60/60/24);          
    day=day<10? '0'+day : day;

    //剩余的小时
    var hour=parseInt(times/60/60%24);      
    hour=hour<10? '0'+hour : hour;

    //剩余的分钟
    var minute=parseInt(times/60%60);          
    minute=minute<10? '0'+minute : minute;

    //剩余的秒数
    var second=parseInt(times%60);             
    second=second<10? '0'+second : second;

    return  '倒计时：'+day+'天'+hour+'小时'+minute+'分钟'+second+'秒'
}
console.log(+new Date());
console.log(countDown('2021-2-12'))
```