#使用方法
```js
在html的<head></head>中加入如下代码：
<meta name="viewport" content="width=device-width,initial-scale=1.0">
//viewport属性是在移动设备上设置原始大小显示和是否缩放的声明
```
#content中的参数
```js

  width    //viewport的宽度
  height  //viewport的高度
  initial-scale  //初始的缩放比例
  minimum-scale  //允许用户缩放到最小的比例
  maximum-scale  //允许用户缩放到最大的比例
  user-scalable  //用户是否可以手动缩放

```
#手机端特有

```js

<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=0">
/**
*强制让文档的宽度与设备的宽度保持 1:1，文档最大的宽度比例是1.0，且不允许用户点击屏幕放大浏览；
*/
<meta name="apple-mobile-web-app-capable" content="yes">
/**
*iphone设备中的safari私有meta标签，表示允许全屏模式浏览；
*/
<mete name="apple-mobile-web-app-status-bar-style" content="black">
/**
*iphone的私有标签，指定iphone中safair顶端的状态调的样式；
*在web app 应用下状态条（屏幕顶部条）的颜色：
*默认为default(白色)，可以定为black（黑色）和black-translucent(灰色半透明)。
*注：若值为“black-translucent”将会占据px位置，浮在页面上方（会覆盖20px,高度-iphone4和itouch4的Retiana的屏幕为40px）
*/
<mete name="format-detection" content="telephone=no">
/**
*告诉设备忽略将页面中的数字识别为电话号码。
*/

```
#样式中的媒体查询
```js
媒体查询 包含一个媒体类型，后跟一个或多个检查特定条件（如最小的屏幕宽度）的表达式。 
是评估 True 或 False 的一种表达。如果为 True，则继续使用样式表。如果为 False，则不能使用样式表。

```
```js
//使用媒体类型
<link rel="stylesheet" type="text/css" href="site.css" media="screen" />
<link rel="stylesheet" type="text/css" href="print.css" media="print" />
screen 适用于计算机彩色屏幕
print  适用于打印预览模式下查看的内容或者打印机打印的内容。
```
```js
//媒体查询规则
@media all and (min-width: 800px) { ... }
@media all是媒体类型，将此css运用于所有媒体类型
(min-width:800px) 是包含媒体查询的表达式，如果浏览器的最小宽度为 800 像素，则会告诉浏览器只运用下列 CSS。
```
```js
简写语法
@media(min-width:800px){...}
```
```js
复杂表达式
@media(min-width:800px)and(max-width:1200px)and(orientation:portrait) { ... }
/**
*媒体查询仅在宽度为 800 到 1200 像素且方向是纵向时才能激活
*orientation方向的值可以是 portrait 或 landscape
*/
```
```js
媒体查询中的中的or
@media (min-width:800px) or (orientation:portrait) { ... }
//如果宽度至少是 800 像素或方向是纵向的，则会应用该规则。
```
```js
媒体查询中的not
@media(not min-width:800px){}
//当最小宽度不是 800 像素时，会应用该CSS 规则。)
```
#常见媒体查询
```js
因为 Apple 首次向市场推出了用户智能手机和平板电脑产品，所以下列大多数媒体查询都是基于这些型号的设备。
如果目标是横向模式智能手机，则使用： @media (min-width: 321px) { ... }
如果目标是纵向模式智能手机，则使用： @media (max-width: 320px) { ... }
如果目标是横向模式 Apple iPad，则使用： @media (orientation: landscape) { ... }
如果目标是纵向模式 iPad，则使用： @media (orientation: portrait) { ... }
```
#嵌套的媒体查询
```js
#header {
  width: 400px;
  @media (min-width: 800px) {
    width: 100%;
  }
}

  #header {
    width: 400px;
  }
  @media (min-width: 800px) {
    #header {
      width: 100%;
    }
  }
```
#解决不支持媒体查询的方法
```js
Respond.js 是一个极小的增强 Web 浏览器的 JavaScript 库，使得原本不支持 CSS 媒体查询的浏览器能够支持它们。
```
#样式表中的示例
```js
@media screen and (max-width:320px) {
	body {
		font-size: 12px;
	}
}
@media screen and (min-width:320px) {
	body {
		font-size: 12px;
	}
}
@media screen and  (min-width:480px) {
	body {
		font-size: 14px;
	}
}
@media screen and  (min-width:640px) {
	body {
		font-size: 19px;
	}
}
@media screen and (min-width:720px) {
	body {
		font-size: 22px;
	}
}
@media screen and (min-width:900px) {
	body {
		font-size: 27px;
	}
}
@media screen and (min-width:1000px) {
	body {
		font-size: 30px;
	}
}
```
