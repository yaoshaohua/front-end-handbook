# 第 5 章 Flexbox

弹性盒子布局（Flexible Box Layout）

通用 `flex` 布局流程：

1. 创建 `flex` 容器，给容器设置 `display: flex`

2. 如有必要，给容器设置 `flex-direction`

3. 给 `flex` 子元素设置 `margin` 或者 `flex` 属性，用来控制大小

4. 其他属性，对齐、间距、换行、顺序等

## 基本概念：弹性容器、弹性子元素、主轴、交叉轴

给元素添加 `display: flex/inline-flex`，该元素变成一个**弹性容器（`flex container`）**，它的直接子元素变成了**弹性子元素（`flex item`）**

`flex` 创建的弹性容器，行为类似于 `block` 元素，默认 `width: 100%`  

`inline-flex` 创建的弹性容器，则类似于 `inline-block` 元素，宽度由内容决定

![alt text](https://github.com/yaoshaohua/markdowndocs/blob/main/assets/css/5-1-1.png?raw=true)

## 弹性子元素的宽度

### `flex` 属性

`flex` 属性是三个属性的简写：`<flex-grow> <flex-shrink> <flex-basis>`，用来控制弹性子元素在主轴方向上的宽度

接下来看看三个属性分别表示什么。先从 `flex-basis` 开始，因为其余两个属性都基于 `flex-basis`。

### `flex-basis`

指定了弹性子元素在主轴方向上的**初始大小**

这个 `flex-basis` 属性 被指定为关键词 `content` 或者 `<'width'>`

![alt text](https://github.com/yaoshaohua/markdowndocs/blob/main/assets/css/5-2-1.png?raw=true)

### `flex-grow`

每个弹性子元素的 `flex-basis` 值计算出来后，它们（加上子元素之间的外边距）加起来会占据一定的宽度。加起来的宽度不一定正好填满弹性容器的宽度，可能会有留白（可用空间）。

**可用空间 = 弹性容器宽度 - 所有弹性子元素的 `flex-basis` - `margin` - `padding` - `border`**

可用空间会按照 `flex-grow` 的值分配给每个弹性子元素，`flex-grow` 的值为非负整数。

`flex-grow` 值为 `0`，那么它的宽度不会超过 `flex-basis` 的值

**`flex-grow` 的值越大，元素的“权重”越高，也就会占据更大的剩余宽度**

### `flex-shrink`

`flex-shrink` 属性与 `flex-grow` 遵循相似的原则。

计算出弹性子元素的初始主尺寸后，它们的累加值可能会超出弹性容器的可用宽度。如果不用 `flex-shrink`，就会导致溢出。

如果某个子元素为 `flex-shrink: 0`，则不会收缩；如果值大于0，则会收缩至不再溢出。

**`flex-shrink` 值越大的元素收缩得越多**。  
