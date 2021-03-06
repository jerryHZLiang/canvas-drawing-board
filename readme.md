# Canvas 画板

### 这个 Canvas 画板能够适配 PC 端和移动端，功能有画图（可选择笔触颜色/粗细）、橡皮擦、一键清空、保存画图。

    在 PC 端中，保存画图直接点击“save”的 SVG 图标即可。 在移动端中，点击“save”之后，会打开此画板转换成的图片 URL 新页面。假如在 iPhone 中，用户只需用力长按当前页面即可弹出“存储图像”和“拷贝”的按钮，然后按需选择功能即可。



# 项目中出现的问题：

    项目中，运用mousemove来实现绘制圆形时，发现鼠标移动速度过快时，绘制的圆形不能连接一起，
    中间出现断点，无法形成一条完整的路径。

### 原因：
    鼠标移动时，不会存储所有的移动信息，而是通过取插值的方法取得鼠标位置信息，否则，系统会被鼠标移动拖垮。
    所以就会出现，移动过快时，出现断点的问题。

### 解决方案：

    鼠标移动过快时，不能做到移动一个像素，响应一次mousemove事件，
    所以导致，绘制的圆形不连续。直接在两次响应mousemove事件时，绘制直线，正好可以连接中间的断点, 
    可以利用lineCap属性，可以保证直线两端为圆角。
