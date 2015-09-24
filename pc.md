#html+css兼容性

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
