# 第 5 章 Flexbox

弹性盒子布局（`Flexible Box Layout`）

一维布局，一次只能处理一个维度上的元素布局，一行或者一列

二维布局，`Grid Layout`，可以同时处理行和列上的布局

## flex 容器、flex 子元素

给元素添加 `display: flex/inline-flex`，该元素变成一个**弹性容器（`flex container`）**，它的直接子元素变成了**弹性子元素（`flex item`）**

![alt text](https://github.com/yaoshaohua/markdowndocs/blob/main/assets/css/5-1-1.png?raw=true)

`flex` 创建的弹性容器，行为类似于 `block` 元素，**默认 `width: 100%`**

`inline-flex` 创建的弹性容器，则类似于 `inline-block` 元素，**宽度由元素内容决定**

## 主轴、交叉轴

`flex-direction` 指定主轴方向，交叉轴垂直于主轴

`flex-direction` 的 4 个取值：

- `row` 文本排成行的方向，`ltr` 从左到右

- `row-reverse`

- `column` 文本行堆叠的方向，从上到下

- `column-reverse`

`row` 或者 `row-reverse`，主轴将沿**行向**延伸，`column` 或者 `column-reverse`，主轴将沿**块向**延伸。

![alt text](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox/basics1.svg)

![alt text](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox/basics3.svg)

![alt text](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox/basics2.svg)

![alt text](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox/basics4.svg)

**默认情况下，flex 子元素被拉伸来填充交叉轴大小**

## 起始线、终止线

如果 `flex-direction: row`，并且 `ltr`，那么主轴的起始线是左边，终止线是右边，交叉轴的起始线是 flex 容器的顶部，终止线是底部。

![alt text](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox/basics5.svg)

## 多行 flex 容器

是否允许换行，如果允许换行，控制行的堆叠方向

`flex-wrap` 的 3 个取值：`nowrap`、`wrap`、`wrap-reverse`

![alt text](https://github.com/yaoshaohua/markdowndocs/blob/main/assets/css/5-4-1.png?raw=true)

![alt text](https://github.com/yaoshaohua/markdowndocs/blob/main/assets/css/5-4-2.png?raw=true)

## flex 子元素大小（在主轴上的比例）

`flex` 属性是三个属性的简写：`<flex-grow> <flex-shrink> <flex-basis>`

### `flex-basis`

指定了 flex 子元素在主轴方向上的**初始大小**

**初始值为 `auto`，在 `flex` 属性中省略时默认值为 `0%`**

**当 `flex-basis` 为 `auto` 时，`flex-basis = width || 元素内容大小`，其他情况，忽略 `width` 属性**

**`flex-basis`优先级高于 `width` 属性**

取值：

- <'width'>

    **`auto`**，`px`、`em`、百分比（相对于 flex 容器主轴尺寸）

- 关键词 `content`

    基于 flex 子元素的内容自动调整大小

### 可用空间

**可用空间：flex 容器里除了元素所占的空间以外的富余空间**

**可用空间 = flex 容器宽度 - 所有 flex 子元素的 `flex-basis` - `margin` - `padding` - `border`**

- 可用空间为正（没填满），按照 `flex-grow` ，将可用空间分配给每个 flex 子元素

- 可用空间为负（溢出），按照 `flex-shrink` 收缩每个 flex 子元素

### `flex-grow`

非负整数，`0`：不增长。值越大，元素的“权重”越高，占据更大的可用空间

**初始值为 `0`，在 `flex` 属性中省略时默认值为 `1`**

### `flex-shrink`

非负整数，`0`：不收缩。值越大，收缩得越多

**初始值为 `1`，在 `flex` 属性中省略时默认值为 `1`**
