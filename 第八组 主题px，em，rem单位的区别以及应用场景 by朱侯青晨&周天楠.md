# px,em,rem单位的区别以及应用场景 #
***
- ## 总体概述 ##
    - ## px ##
    **px**(Pixel，像素)是一个**绝对单位** ，用px设置字体大小时，比较稳定和精确。但是这种方法存在一个问题，当用户在浏览器中浏览我们制作的Web页面时，如果改变了浏览器的缩放，这时会使用我们的Web页面布局被打破。

    - ## em ##
    **em**就是根据基准来缩放字体的大小。em实质是一个**相对值**，而非具体的数值。这种技术需要一个参考点，一般都是以<body>的“font-size”为基准。另外，em是**相对于父元素的属性**而计算的。

    - ## rem ##
    **rem**是CSS3新增的一个**相对单位**。使用rem为元素设定字体大小时，仍然是相对大小，但**相对的只是HTML根元素**。

- ## 使用 ##
    - 任意浏览器的默认字体高都是16px。所有未经调整的浏览器都符合:`1em=16px`。那么`12px=0.75em`,`10px=0.625em`。
    
    - 为了简化font-size的换算，需要在css中的body选择器中声明` Font-size=62.5%`，这就使em值变为 `16px*62.5%=10px`, 这样`12px=1.2em`, `10px=1em`, 也就是说只需要将你的原来的px数值除以10，然后换上em作为单位就行了。
    
    - rem和em一样也是一个相对单位，为了方便理解，我们就理解rem为root em，顾名思义rem只相对跟节点<html>计算，这就是说只要在根节点设定好参考值，那么全篇的1rem都相等，计算方式同em，默认` 1rem=16px;` 同理你可以设定` html { font-size:62.5% } `那么1rem就等于10px，以此类推。

- ## 应用场景 ##
	- 对于只需要适配少部分手机设备，且分辨率对页面影响不大的，使用px即可。

	- 如果需要适配各种移动设备，字体单位推荐使用rem。它相较于px，只修改根元素就可以成比例地调整所有字体大小；相较于em，可以避免字体大小逐层复合的连锁反应。

	- rem的浏览器支持问题：除了IE8及更早版本外，所有浏览器均已支持rem。对于不支持的浏览器，解决方法很简单，就是多写一个绝对单位的声明。这些浏览器会忽略用rem设定的字体大小。比如：`p {font-size:12px; font-size:0.75rem;}`。

	- em单位则适用于在非默认字体大小的元素的padding、margin、width、height和line-height等值。

- ## 参考网站 ##
    - [彻底弄懂css中单位px，em，rem的区别](http://www.cnblogs.com/wuguoyuan/p/rem.html)
    - [px，em，rem的区别和使用案例](http://blog.csdn.net/caichang8/article/details/50113803)
    - [css中em,rem的解析成px的原理及混用场景](http://blog.csdn.net/yummy_go/article/details/50825312)
    - [CSS3的REM设置字体大小](http://www.w3cplus.com/css3/define-font-size-with-css3-rem)




