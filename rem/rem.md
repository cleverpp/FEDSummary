### rem
#### rem定义
rem（font size of the root element）是指相对于根元素的字体大小的单位。

em（font size of the element）是指相对于父元素的字体大小的单位。
#### 为什么要用rem
1. rem能等比例适配所有屏幕
#### UP的rem方案
原理：根据viewport宽度设置root element的font size。

实际项目应用中目前使用的是暴力的等比缩放，即无论容器大小、边距还是字号都是基于设计稿进行等比缩放。
这样做最终的效果是无论页面在PC、Pad、iPhone6 plus、iPhone6还是iPhone5上呈现的效果，缩放后都能与设计稿完全重合。
主要的就是其中这几行代码：
```
var width = docEl.getBoundingClientRect().width;
width = width > 768 ? visualWidth : width;
rem = width / (visualWidth / 100);
docEl.style.fontSize = rem + 'px';
```

#### rem遇到的坑
1. 雪碧图(Sprite)时，用rem可能会有误差
2. 图像拼接时，用rem也会有误差

### 其它屏幕适配方案

### 参考
[web app变革之rem](https://isux.tencent.com/web-app-rem.html)
