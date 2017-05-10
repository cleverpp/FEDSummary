### rem
#### rem定义
rem（font size of the root element）是指相对于根元素的字体大小的单位。

em（font size of the element）是指相对于父元素的字体大小的单位。
#### 为什么要用rem
rem能等比例适配所有屏幕
#### UP的rem方案:resize.js
原理：根据viewport宽度设置root element的font size。

无论容器大小、边距还是字号都是基于设计稿进行等比缩放。
这样做最终的效果是无论页面在PC、Pad、iPhone6 plus、iPhone6还是iPhone5上呈现的效果，缩放后都能与设计稿完全重合。
主要的就是其中这几行代码：
```
var width = docEl.getBoundingClientRect().width;
width = width > 768 ? visualWidth : width;
rem = width / (visualWidth / 100);
docEl.style.fontSize = rem + 'px';
```
其中visualWidth是头部指定了名为“visual-width”的meta标签，则用其content作为设计稿宽度基准。
基于resize的弹性布局方案，不用考虑屏幕宽度问题，只需按照设计稿以rem进行字号、宽高等实现，不必使用百分比。

reisze.js的缺点
1. 一般2倍设计稿只要保证字号不小于24px即可（浏览器一般不支持小于12px的字号显示），但是使用类似的弹性布局方案，如果设计稿是基于750px的，那么为了保证对小于375px手机效果的兼容，设计稿字号应不小于28px（24 * 375 / 320），否则可能导致在小屏手机折行等问题。
2. 在高分辨率屏幕上可能显得“傻大”，因为是等比放大的原因，在比设计稿分辨率高的屏幕上呈现时可能显得“傻大”。

resize.js的坑
1. 雪碧图(Sprite)时，会有误差,导致偏移
2. 图像拼接时，会有误差，导致偏移
3. 1px或2px的border不要用rem，缩放后很多手机无法显示。

#### [淘宝的flexsible.js](https://github.com/amfe/lib-flexible)


### 兼容性
![](http://7jpp2v.com1.z0.glb.clouddn.com/0a269f05e4fb51f561d060eb24e864b11458889628.png)

### 其它屏幕适配方案
1. 简单一点的页面，一般高度直接设置成固定值，宽度一般撑满整个屏幕。
2. 稍复杂一些的是利用百分比设置元素的大小来进行适配，或者利用flex等css去设置一些需要定制的宽度。
3. 再复杂一些的响应式页面，需要利用css3的media query属性来进行适配，大致思路是根据屏幕不同大小，来设置对应的css样式。

### 参考
1. [web app变革之rem](https://isux.tencent.com/web-app-rem.html)
2. [TAT.tennylv移动web适配利器-rem](http://www.alloyteam.com/2016/03/mobile-web-adaptation-tool-rem/)
3. [两个viewport的故事（第一部分）](http://weizhifeng.net/viewports.html)
4. [两个viewport的故事（第二部分）](http://weizhifeng.net/viewports2.html)
