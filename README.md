BFC神奇背后的原理
===============

## BFC是什么？

BFC就是Box、Formatting Context 的概念。

### Box：CSS布局的基本单位

Box是css布局的对象和基本单位，直观点说，就是一个页面是由很多歌Box组成的。元素的类型和display属性，决定了这个Box的类型。不同类型的Box,会参与不同的Formatting Context(一个决定如何渲染文档的容器)，因此Box内的元素会以不同的方式渲染。让我们看看有哪些盒子：

*	**block-level box** `display`属性为block，list-item，table的元素，会生成block-level box并参与block fomatting context；
*	**inline-level box** `display`属性为inline, inline-block, inline-table的元素，会生成inline-level box并参与inline fomatting context；
*	**run-in box** css3中才有

### Formatting context

Formatting context是W3C css2.0规范中的一个概念。它是页面中的一块如黯然区域，并且有一套渲染规则，它决定了其子元素将如何定位，以及和其他元素的关系和相互作用。最常见的Formatting context有Block formatting context（简称BFC）和Inline formatting context（简称IFC）。

css2.1中只有BFC和IFC，css3中还增加了GFC和FFC。

### BFC定义

BFC（Block formatting context）直译为“块级格式化上下文”。它是一个独立的渲染区域，只有Block-level box参与，它规定了内部的Block-level Box如何布局，并且与这个区域外部毫不相干。

### BFC布局规则：

*	内部的BOX会在垂直方向上，一个接着一个地放置
*	BOX垂直方向的距离由margin决定。术语同一个BFC的两个相邻BOX的margin会发生重叠
*	每个元素的margin box的左边，与包含块border box的左边相接触（对于从左往右的格式化，否则相反）。及时存在浮动也是如此。
*	BFC的区域不会与float box重叠
*	BFC就是页面上的一个隔离独立容器，容器里面的子元素不会影响到外部的元素。反之也是如此。
*	计算BFC的高度时，浮动元素也参与计算

## 那些元素会生成BFC？

*	根元素
*	float属性不为none
*	position为absolute或fixed
*	display为inline-block、table-cell、table-caption、flex、inline-flex
*	overflow不为visible

## BFC的作用及原理

1.	自适应两栏布局

```html

<style>
    body {
        width: 300px;
        position: relative;
    }
 
    .aside {
        width: 100px;
        height: 150px;
        float: left;
        background: #f66;
    }
 
    .main {
        height: 200px;
        background: #fcc;
    }
</style>
<body>
    <div class="aside"></div>
    <div class="main"></div>
</body>

```

未完待续...[http://www.cnblogs.com/lhb25/p/inside-block-formatting-ontext.html](http://www.cnblogs.com/lhb25/p/inside-block-formatting-ontext.html)