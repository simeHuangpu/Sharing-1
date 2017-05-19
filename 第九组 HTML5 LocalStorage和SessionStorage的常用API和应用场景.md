#HTML5 LocalStorage和SessionStorage
#的常用API和应用场景
***
###摘要
提到本地存储localStorage就不得不提sessionStorage和cookie这两个。其中localStorage和sessionStorage可以合成称为web Storage

HTML5的本地存储API中的localStorage与sessionStorage在使用方法上是相同的，区别在于sessionStorage在关闭页面后即被清空，而localStorage则会
***
###localStorage的使用：
#####setItem存储value

用途：将value存储到key字段
用法：.setItem( key, value)
代码示例：

	sessionStorage.setItem("key", "value"); 	localStorage.setItem("site", "js8.in");
#####getItem获取value

用途：获取指定key本地存储的值
用法：.getItem(key)
代码示例：

	var value = sessionStorage.getItem("key"); 	var site = localStorage.getItem("site");
#####removeItem删除key

用途：删除指定key本地存储的值
用法：.removeItem(key)
代码示例：

	sessionStorage.removeItem("key"); 	localStorage.removeItem("site");
#####clear清除所有的key/value

用途：清除所有的key/value
用法：.clear()
代码示例：

	sessionStorage.clear(); 	localStorage.clear();
#####其他操作方法：点操作和[]

web Storage不但可以用自身的setItem,getItem等方便存取，也可以像普通对象一样用点(.)操作符，及[]的方式进行数据存储，像如下的代码：

`var storage = window.localStorage;` 
`storage.key1 = "hello"; storage["key2"] = "world";` 
`console.log(storage.key1); console.log(storage["key2"]);`
#####localStorage和sessionStorage的key和length属性实现遍历
sessionStorage和localStorage提供的key()和length可以方便的实现存储的数据遍历，例如下面的代码：

`var storage = window.localStorage;`
`for (var i=0, len = storage.length; i  <  len; i++){     var key = storage.key(i);`     
`var value = storage.getItem(key);`     
`console.log(key + "=" + value); }`
#####storage还提供了storage事件，当键值改变或者clear的时候，就可以触发storage事件，如下面的代码就添加了一个storage事件改变的监听：

`if(window.addEventListener){ 	`
`window.addEventListener("storage",handle_storage,false); `
`}`
`else if(window.attachEvent){ 	`
`window.attachEvent("onstorage",handle_storage); `
`}` 
`function handle_storage(e){ 	if(!e){e=window.event;}	 }`
#####storage事件对象的具体属性如下表：
| Property       | Type           | Description  |
| ------------- |:-------------:| :-----|
| key      | String | The named key that was added,removed,or modified |
| oldValue| Any      |   The previous value(now overwritten), or null if a new item was added |
|newValue | Any      |   The new value, or null if an item was added |
|url/uri|String|The page that called the method that triggered this change|
***
#####应用例子
![](http://pic002.cnblogs.com/images/2012/391736/2012120815521635.png)
#####具体代码如下
`<!DOCTYPE html>`
`<html xmlns="http://www.w3.org/1999/xhtml">`
`<head>`
`   <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />`
`   <title></title>`
`   <style type="text/css">`
`   textarea {`
`   width: 300px;`
`   height: 300px;`
`   }`
``
`   .button {`
`   width: 100px;`
`   }`
`   </style>`
`</head>`
`<body onload="init()">`
`   <script type="text/javascript">`
`   //使用HTML5 Web存储的localStorage和sessionStorage方式进行Web页面数据本地存储。`
`   //页面参考如下图，能将页面上的数据进行本地存储。并能读取存储的数据显示在页面上。`
`   var t1;`
`   var t2;`
`   var oStorage;`
`   var oStorage;`
`   function init() {//初始化t1，t2`
`   t1 = document.getElementById("t1");`
`   t2 = document.getElementById("t2");`
`   sStorage = window.sessionStorage;`
`   lStorage = window.localStorage`
`   }`
`   function saveSession() {`
`   sStorage.mydata = t2.value;`
`   t1.value += "sessionStorage保存mydata:" + t2.value + "\n";`
`   }`
`   function readSession() {`
`   t1.value += "sessionStorage读取mydata:" + sStorage.mydata + "\n";`
`   }`
`   function cleanSession() {`
`   t1.value += "sessionStorage清除mydata:" + sStorage.mydata + "\n";       `      `sStorage.removeItem("mydata");`
`   }`
`   function saveStorage() {`
`   lStorage.mydata = t2.value;`
`   t1.value += "localStorage保存mydata:" + t2.value + "\n";`
`   }`
`   function readStorage() {`
`  t1.value += "localStorage读取mydata:" + lStorage.mydata + "\n";`
`   }`
`   function cleanStorage() {`
`   t1.value += "localStorage清除mydata:" + lStorage.mydata + "\n";`             
`lStorage.removeItem("mydata");`
`   }`
`   </script>`
`   <div>`
`   <textarea id="t1"></textarea><br />`
`   <label>需要保存的数据: </label>`
`   <input type="text" id="t2" /><br />`
`   <input type="button" class="button" onclick="saveSession()" name="b1" value="session保存" />`
`   <input type="button" class="button" onclick="readSession()" value="session读取" />`
`   <input type="button" class="button" onclick="cleanSession()" value="session清除" /><br />`
`   <input type="button" class="button" onclick="saveStorage()" value="local保存" />`
`   <input type="button" class="button" onclick="readStorage()" value="local读取" />`
`   <input type="button" class="button" onclick="cleanStorage()" value="local清除" />`
`   </div>`
`</body>`
`</html>`
***
#####具体应用场景
######localStorage
例如储存用户名和密码
######sessionStorage
可以跟踪用户在网站上的活动。例如：当你上网进入一个网站时，如果你没有登陆，无论你访问哪几个页面都会跳转回登陆页。还有就是你在购物时，不可能把你的东西放到别人的购物车里去，这就得用一个信息变量来判断！