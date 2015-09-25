#html+css兼容性


#识别不同浏览器中使用的样式
```js
!important
!important只有IE7，IE8，firefox可以识别，IE6不能识别。

例：
border:1px solid #eee!important;border:2px solid #eee;
//IE6不能识别important,所以会忽略前一个进而实现第二个样式。
```
```js
*
IE6、IE7、IE9都能识别*,而标准浏览器FF、IE8是不能识别*的;
border:2px solid #f00;*border:1px solid #f00;
/**
*把*放在后面是因为ff和IE8不识别*而导致只对它设置了一次border;
*而ie 其他系列进行了两次border设置后，后一个属性覆盖了前一个属性，故为1像素的边框。
*/
```
```js
_
除IE6支持_,火狐，IE7，IE8都不支持_.
例：
border:2px solid #f00;*border:1px solid #f00; _ border:3px solid #f00;
//_放在后面，只有IE6能识别，所以IE6边框为3、IE7、IE9边框为1，FF、IE8边框为2；
```
```js
hack示例
所有浏览器通用：height:100
IE6专用：_height:100
IE,IE7 :*height:100
IE7 专用 *+height: 100px;
IE7、火狐 共用 height: 100px !important;

注:CSS HACK书写顺序:先写FF(IE8)所要的样式,接着是IE7的,再接着才是IE6的!
```
#清除浮动
```js
在布局中，往往会出现因为一个div浮动，导致后来的div占据了浮动div原来的位置，这种情况一般会出现在火狐浏览器中
解决办法：在浮动div下添加一个div在样式中clear:both;

例：
<div style="float:left;height:100px; width:500px;">
<div style="clear:both;">
<div style="height:100px; width=300px">
```
