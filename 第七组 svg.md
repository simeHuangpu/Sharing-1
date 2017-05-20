# SVG基础概念

1. 什么是SVG？
 
    1. SVG 指可伸缩矢量图形 (Scalable Vector Graphics)
    2. SVG 用来定义用于网络的基于矢量的图形
    3. SVG 使用 XML 格式定义图形
    4. SVG 图像在放大或改变尺寸的情况下其图形质量不会有所损失
    5. SVG 是万维网联盟的标准
    6. SVG 与诸如 DOM 和 XSL 之类的 W3C 标准是一个整体

2. SVG 的优势

    1. SVG 可被非常多的工具读取和修改（比如记事本）
    2. SVG 与 JPEG和GIF图像比起来，尺寸更小，且可压缩性更强。
   3. SVG 是可伸缩的
   4. SVG 图像可在任何的分辨率下被高质量地打印
   5. SVG 可在图像质量不下降的情况下被放大
   6. SVG 图像中的文本是可选的，同时也是可搜索的（很适合制作地图）
   7. SVG 可以与 Java 技术一起运行
   8. SVG 是开放的标准
   9. SVG 文件是纯粹的 XML

# SVG实例
### 一个最简单的例子
``` 
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN"
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <circle cx="100" cy="50" r="40" stroke="black"
  stroke-width="2" fill="red" />
</svg> 
```
### SVG 代码解析：

-  第一行包含了 XML 声明。请注意 standalone 属性！该属性规定此 SVG 文件是否是"独立的"，或含有对外部文件的引用。 在这里，是 DTD 文件。

- standalone="no" 意味着 SVG 文档会引用一个外部文件。

- 第二和第三行引用了这个外部的 SVG DTD。该 DTD 位于 "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd"。该 DTD 位于 W3C，含有所有允许的 SVG 元素。

- SVG 代码以 <svg> 元素开始，包括开启标签 <svg> 和关闭标签 </svg> 。这是根元素。width 和 height 属性可设置此 SVG 文档的宽度和高度。version 属性可定义所使用的 SVG 版本，xmlns 属性可定义 SVG 命名空间。

- SVG 的 <circle> 用来创建一个圆。cx 和 cy 属性定义圆中心的 x 和 y 坐标。如果忽略这两个属性，那么圆点会被设置为 (0, 0)。r 属性定义圆的半径。

- stroke 和 stroke-width  属性控制如何显示形状的轮廓。我们把圆的轮廓设置为 2px 宽，黑边框。

- fill 属性设置形状内的颜色。我们把填充颜色设置为红色。

- 关闭标签的作用是关闭 SVG 元素和文档本身。

- 注释：所有的开启标签必须有关闭标签！


## 其他的一些例子萌：
### 矩形
```
<!DOCTYPE html>
<html>
<body>

<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <rect width="300" height="100" style="fill:rgb(0,0,255);stroke-width:1;stroke:rgb(0,0,0)" />
</svg>
 
</body>
</html>
```
### 多边形
```
<!DOCTYPE html>
<html>
<body>

<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <polygon points="200,10 250,190 160,210" style="fill:lime;stroke:purple;stroke-width:1" />
</svg>

</body>
</html>
```
### 模糊效果
```
<!DOCTYPE html>
<html>
<body>

<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <defs>
    <filter id="f1" x="0" y="0">
      <feGaussianBlur in="SourceGraphic" stdDeviation="15" />
    </filter>
  </defs>
  <rect width="90" height="90" stroke="green" stroke-width="3" fill="yellow" filter="url(#f1)" />
</svg>

</body>
</html>
```
### 线性渐变
```
<!DOCTYPE html>
<html>
<body>

<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <defs>
    <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <ellipse cx="200" cy="70" rx="85" ry="55" fill="url(#grad1)" />
</svg>

</body>
</html>
```
## 其他形状
- 圆形 <circle>
- 椭圆 <ellipse>
- 线 <line>
- 折线 <polyline>
- 多边形 <polygon>
- 路径 <path>
## 特别说下path
- M = moveto
- L = lineto
- H = horizontal lineto
- V = vertical lineto
- C = curveto
- S = smooth curveto
- Q = quadratic Bézier curve
- T = smooth quadratic Bézier curveto
- A = elliptical Arc
- Z = closepath

```
 <svg viewBox='0 0 80 76' x='0px' y='0px'>
        <g>
          <path d='M 68.9708 24.8623 L 60.4554 2.3018 C 59.9641 0.7017 58.1628 -0.2583 56.5252 0.3817 L 1.9822 20.2222 C 0.3822 20.7022 -0.4179 22.6222 0.2222 24.2223 L 8.8624 47.7797 L 8.8624 35.1484 C 8.8624 29.5024 13.3425 24.8623 18.8857 24.8623 L 32.9442 24.8623 L 50.63 12.862 L 60.7829 24.8623 L 68.9708 24.8623 L 68.9708 24.8623 ZM 77.098 32.0625 L 18.8857 32.0625 C 17.2512 32.0625 16.0625 33.4511 16.0625 35.1484 L 16.0625 72.8491 C 16.0625 74.5477 17.2512 75.9375 18.8857 75.9375 L 77.098 75.9375 C 78.742 75.9375 79.9376 74.5477 79.9376 72.8491 L 79.9376 35.1484 C 79.9376 33.4511 78.742 32.0625 77.098 32.0625 L 77.098 32.0625 ZM 73.0626 68.0625 L 23.9375 68.0625 L 23.9375 61.0852 L 31.4704 43.7232 L 42.7696 57.6777 L 53.4138 46.8062 L 67.1695 41.9375 L 73.0626 55.0815 L 73.0626 68.0625 L 73.0626 68.0625 Z'></path>
        </g>
      </svg>
```


```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <path d="M150 0 L75 200 L225 200 Z" />
</svg>
```
[我们试试](https://jsbin.com/vuhigodogu/edit?html,output)


## 动画简介

### 移动

```
<!DOCTYPE html>
<html>
<body>

<p><b>Note:</b> This example only works in Firefox and Google Chrome.</p>

<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <g transform="translate(100,100)">
    <text id="TextElement" x="0" y="0" style="font-family:Verdana;font-size:24"> It's SVG!
      <animateMotion path="M 0 0 L 100 100" dur="5s" fill="freeze" />
    </text>
  </g>
</svg>

</body>
</html>
```
### 变化

```
<!DOCTYPE html>
<html>
<body>

<p><b>Note:</b> This example only works in Firefox and Google Chrome.</p>

<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <rect id="rec" x="300" y="100" width="300" height="100" style="fill:lime"> 
    <animate attributeName="x" attributeType="XML" begin="0s" dur="6s" fill="freeze" from="300" to="0" /> 
    <animate attributeName="y" attributeType="XML" begin="0s" dur="6s" fill="freeze" from="100" to="0" /> 
    <animate attributeName="width" attributeType="XML" begin="0s" dur="6s" fill="freeze" from="300" to="800" /> 
    <animate attributeName="height" attributeType="XML" begin="0s" dur="6s" fill="freeze" from="100" to="300" /> 
    <animateColor attributeName="fill" attributeType="CSS" from="lime" to="red" begin="2s" dur="4s" fill="freeze" />
  </rect>
</svg>

</body>
</html>
```
