## DOM 文档对象模型

+ document 文档，即整个页面，属于window的一个对象。文档中的所有东西都可称之为节点，包括元素，文本，属性等 (document-->html-->body-->emement)

+ 获取节点
  + document.getElementById
  + document.getElementsByClassName (返回伪数组)
  + document.getElementsByTagName (返回伪数组)
  + document.querySelector
  + document.querySelectorAll (返回伪数组)
  + element.parentNode (就近原则 获取最近一级的父节点 如果没有则返回值为null)
  + element.childNodes  (获取该元素有所的一级子节点，包括了文本节点等，是一个集合)
  + element.children (获取该元素所有的一级子元素节点，也是一个集合)
  + nextSibling (下一个兄弟节点 包含元素节点或者 文本节点等等)
  + previousSibling  (前一个兄弟节点  同样包含元素节点、文本节点)        
  + nextElementSibling (得到下一个兄弟元素节点)
  + previousElementSibling   (得到上一个兄弟元素节点)
```js
//获取body元素
var bodyEle=document.body;
console.log(bodyEle)

//获取html元素
var htmlEle=document.documentElement;     
console.log(htmlEle)
```
+ 自定义属性
  + element.setAttribute('属性名'，属性值)  （设自定义属性）
  + element.getAttribute('属性名') （获得自定义属性值）
  + element.removeAttribute('属性名) (移除元素某个属性)
  + 案例：tab栏切换
+ 排它思想
  + 在事件发生要做出改变时，先'干掉'其他兄弟节点，再让当前节点改变

+ 节点属性
  + nodeType
    + 获取节点的节点类型，用数字表示
    + nodeType===1:就表示该节点是一个元素节点
    + nodeType===2:就表示该节点是一个属性节点
    + nodeType===3:就表示该节点是一个文本节点
  + nodeName
    + 获取节点的节点名称
    + 元素节点的nodeName就是大写的标签名
    + 属性节点的nodeName就是属性名
    + 文本节点的nodeName就是#text
  + nodeValue
    + 获取节点的值
    + 元素节点没有nodeValue
    + 属性节点的nodeValue就是属性值
    + 文本节点的nodeValue就是文本内容
+ 节点操作 
  + 创建节点 (先创建，后添加)
    + document.creatElement  (创建元素节点)
    + document.createTextNode  (创建文本节点)
  + 添加节点
    + appendChild  (在指定父级元素中子节点末尾插入)
    + insertBefore('插入的元素'，在哪个子节点前插入)  两个参数
  + 删除节点
    + removeChild (删除某个节点中的指定子节点)
  + 修改节点(替代)
    + 父节点.replaceChild(新节点，旧节点) 
  + 复制节点
    + 要克隆的节点.cloneNode(是否克隆标签里面的内容，默认是false)
    + 返回值: 克隆好的节点
  + 案例：动态表格创建


+ 事件三要素: 事件源、事件、事件处理程序
+ 注册事件
  + 传统方式：
    + div.onclick=function(){}
  + 监听器方式
    + div.addEventListener('click',function(){})
  + 区别(相同事件下)：
    + 传统方式：只有一个函数会生效，后面的会覆盖前面的，前面注册的事件函数不执行。
    + 监听器方式：多个事件函数都会生效  依次生效
+ 移除事件
  + 传统方式移除事件：
    + divs[0].onclick = null;
  + 监听器方式移除事件 removeEventListener：
```js
div.addEventListener('click', fn) // 里面的fn 不需要调用加小括号
function fn() {
    alert(22);
    divs[1].removeEventListener('click', fn);
} //点击一次弹出22后事件就被移除，再次点击无法生效
```
+ 事件流
  + 三个阶段：捕获阶段、事件处理、冒泡阶段；js代码只能处于捕获和冒泡中的某一个阶段(传统事件只能得到冒泡阶段)
  + 捕获阶段：如果addEventListener 第三个参数是 true 那么则处于捕获阶段  document -> html -> body -> father -> son
  + 冒泡阶段 如果addEventListener 第三个参数是 false 或者 省略 那么则处于冒泡阶段  son -> father ->body -> html -> document
+ 事件委托
  + 事件委托原理：不要给每一个子节点单独添加侦听器（事件函数），而是直接给父节点添加侦听器，利用事件冒泡来影响子节点改变
+ 事件对象
  + 事件对象只有有了事件才会存在，它是系统给我们自动创建的，不需要我们传递参数
  + 事件对象是我们事件的一系列相关数据的集合,跟事件相关的,比如鼠标点击里面就包含了鼠标的相关信息，鼠标坐标啊，如果是键盘事件里面就包含的键盘事件的信息,比如,判断用户按下了那个键
  + 事件对象也有兼容性问题 ie678 通过 window.event 兼容性的写法  e = e || window.event;
  +  e.target 返回的是触发事件的对象（元素）  this 返回的是绑定事件的对象（元素）
  + 区别 ： e.target 点击了那个元素，就返回哪个元素 + this 哪个元素绑定了这个点击事件，那么就返回谁
```js
//  阻止默认行为   e.preventDefault()   是一个方法
    var a=document.querySelector('a')
    a.addEventListener('click',fn)
    function fn(e){
        e.preventDefault()
    }   //a链接将不会跳转

//阻止事件冒泡   e.stopPropagation()  
//ie678   e.cancelBubble;   
```
+ 关于this
  + 作为全局函数调用:this = window
  + 作为对象的方法调用:this = 方法的调用者（就是调用方法的那个对象）
  + 作为事件处理函数:this = 事件源

+ 键盘对象
  + keydown 按下 （识别功能键）
  + keypress 按下 （不识别功能键）
  + keyup 松开
  + keyCode 键盘对象的属性，返回按下键的ASCII码值，keydown和keyup不区分大小写，keypress区分大小写
  + 案例：快递单号查询

+ 鼠标对象
  + mouseover 鼠标经过
  + mouseout 鼠标滑出
  + mousemove 鼠标移动
  + mousedown 鼠标按下
  + mouseup 鼠标松开
  + 案例：拖动模块框 ， 仿京东放大镜
+ 获得焦点，失去焦点
  + onfocus事件
  + onblur事件

+ offset 系列
  + 只读属性，不能赋值，返回数值，不带单位
  + offsetTop / offsetLeft:返回元素到带有定位的父级的距离，若没有父级元素带有定位，则返回到body的距离
  + offsetWidht / offsetHeight ：返回元素大小，包含padding和border
  + offsetParent ：返回带有定位的父级，没有则返回body
  + 案例：拖动模块框 ， 仿京东放大镜
+ client 系列
  + clientHeight / clientWidth :返回元素大小，不包含边框，其他和offset相同
  + clientTop / clientLeft ：返回上左边框大小
+ scroll 系列
  + scrollHeight / scrollWidth :返回元素实际大小，不包含边框。当元素内容超出时，超出部分也会计算
  + scrollTop / scrollLeft : 页面滚动时，被卷去的距离，配合 onscroll事件使用
  + 案例：仿淘宝固定侧边栏

  