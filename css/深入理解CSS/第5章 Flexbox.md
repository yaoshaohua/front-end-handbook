# 第 5 章 Flexbox

弹性盒子布局（Flexible Box Layout）

给元素添加 `display: flex/inline-flex`，该元素变成一个**弹性容器（`flex container`）**，它的直接子元素变成了**弹性子元素（`flex item`）**

`flex` 创建的弹性容器，行为类似 `block` 元素，默认 `width: 100%`，`inline-flex` 则类似 `inline-block`，宽度由内容决定

![alt text](https://github.com/yaoshaohua/markdowndocs/blob/main/assets/css/5-1-1.png?raw=true)

补充：

**行内元素，设置 `line-height`，最终作用的地方不是自身，而是自身所在的行框盒子**

**行内元素，它给父元素贡献的高度会根据行高计算**

![alt text](https://github.com/yaoshaohua/markdowndocs/blob/main/assets/css/5-1-2.png?raw=true)

![alt text](https://github.com/yaoshaohua/markdowndocs/blob/main/assets/css/5-1-3.png?raw=true)