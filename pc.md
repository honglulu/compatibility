#html+css兼容性

- [识别不同浏览器中使用的样式](#识别不同浏览器中使用的样式)
- [清除浮动](#清除浮动)
- [标签初始化](#标签初始化)
- [css样式兼容](#css样式兼容)

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
#标签初始化
```js

html开头对标签进行初始化{margin：0px；padding：0px；}能有效解决各浏览器某些标签的默认值不同问题；

```
```js

ul 标签在火狐下面默认有 list-style 和 padding . 最好事先声明list-style：none, 以避免不必要的麻烦
(常见于导航标签和内容列表)；
 
```
#css样式兼容
```js

外部div宽度不定死，采用自适应

```
```js

无任何的内容的td标签设置的边框的样式在IE6中无效，但在火狐和谷歌中正常。
若要无内容的td边框样式在IE下也有效，那么设置样式：table{border-collapse:collapse;}还
可以在设置了table的前提下设置td{empty-cells:show;}

```
```js

块属性标签float后，又有横行的margin情况下，在IE6显示margin比设置的大
常见症状是:IE6中后面的一块被顶到下一行
解决方法：在float的标签样式控制中加入 display:inline;将其转化为行内属性

```
```js

设置较小高度标签（一般小于10px），在IE6，IE7，遨游中高度超出自己设置高度
问题症状：IE6、7和遨游里这个标签的高度不受控制，超出自己设置的高度
解决方案：给超出高度的标签设置overflow:hidden;或者设置行高line-height 小于你设置的高度。

```
```js
行内属性标签，设置display:block后采用float布局，又有横行的margin的情况，IE6间距bug
问题症状：IE6里的间距比超过设置的间距
解决方案：在display:block;后面加入display:inline;display:table;
/**
*行内属性标签，为了设置宽高，我们需要设置display:block;(除了input标签比较特殊)。在用float布局并有横向的margin后，
*在IE6下，他就具有了块属性float后的横向margin的bug。不过因为它本身就是行内属性标签，所以我们再加上display:inline的话，
*它的高宽就不可设了。这时候我们还需要在display:inline后面加入display:talbe。
*/
```
```js

图片默认有间距
问题症状：几个img标签放在一起的时候，有些浏览器会有默认的间距，加了问题一中提到的通配符也不起作用。
解决方案：使用float属性为img布局

```
```js

标签最低高度设置min-height不兼容
问题症状：min-height本身就是一个不兼容的CSS属性，所以设置min-height时不能很好的被各个浏览器兼容
解决方法：如果我们要设置一个标签的最小高度200px，
需要进行的设置为：{min-height:200px; height:auto !important; height:200px; overflow:visible;}

```
