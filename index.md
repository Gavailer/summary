## Css ＆ HTML

### 盒模型

* **标准盒模型 ：**height、width指内容区域的高度和宽度，增加padding、margin、border不会影响内容区域的宽度、高度的尺寸，但会影响元素框的尺寸。
* **IE盒模型：** height、width指内容区域的高度、宽度+padding+border

```css
 /* 设置当前盒子为 标准盒模型（默认） */
  box-sizing: content-box;

 /* 设置当前盒子为 IE盒模型 */
  box-sizing: border-box;
```

---

### BFC

* #### BFC概念：

	BFC（Block Formatting Context）：块级格式化上下文。你可以把它理解成一个独立的区域。
	
	参考链接：[BFC原理详解](https://segmentfault.com/a/1190000006740129)、[BFC详解](https://www.jianshu.com/p/bf927bc1bed4)、[BFC 神奇背后的原理](https://www.cnblogs.com/lhb25/p/inside-block-formatting-ontext.html)

* #### BFC原理：

  1. BFC在页面中是独立的元素，外面的元素不会影响里边的元素，反之亦然
  2. BFC区域不会与旁边的 **float box** 区域重叠
  3. 计算BFC高度时 浮动的子元素也参与计算
  4. BFC **内部的** 子元素在**垂直方向**边距会发生重叠

* #### 如何生成BFC：

   1. overflow属性值不为visible 可以是hidden、auto

   2. float属性值不为 none

      > 当前元素设置了浮动，就创建了BFC

    	3. posiiton属性值不为static、relative；可以是absoult、fixed

    	4. display属性值为inline-block, table-cell, table-caption, flex, inline-flex

* #### BFC应用：

   1. **举例1 解决margin 重叠**

      当父元素和子元素发生 margin 重叠时，解决办法：**给子元素或父元素创建BFC**。

      比如说，针对下面这样一个 div 结构：

      ```html
      <div class="father">
          <p class="son">
          </p>
      </div>
      ```

      上面的div结构中，如果父元素和子元素发生margin重叠，我们可以给子元素创建一个 BFC，就解决了：

      ```html
      <div class="father">
          <p class="son" style="overflow: hidden">
          </p>
      </div>
      ```

      因为**BFC区域是一个独立的区域，不会影响外面的元素**。

     2. **举例2 BFC区域不与float区域重叠**

           ```html
         <!DOCTYPE html>
         <html lang="en">
         <head>
             <meta charset="UTF-8">
             <title>Document</title>
             <style>
         
                 .father-layout {
                     background: pink;
                 }
         
                 .father-layout .left {
                     float: left;
                     width: 100px;
                     height: 100px;
                     background: green;
                 }
         
                 .father-layout .right {
                     height: 150px;  /*右侧标准流里的元素，比左侧浮动的元素要高*/
                     background: red;
                 }
         
             </style>
         </head>
         <body>
         
         <section class="father-layout">
             <div class="left">
                 左侧
             </div>
             <div class="right">
                 右侧
             </div>
         </section>
         
         </body>
         </html>
         ```

         效果如下：

         ![举例2](.\img\Css\example2.png)

         上图中，由于右侧标准流里的元素，比左侧浮动的元素要高，导致右侧有一部分会跑到左边的下面去。

         **如果要解决这个问题，可以将右侧的元素创建BFC**，因为**BFC区域不与`float box`区域重叠**。解决办法如下：（将right区域添加overflow属性）

         ```html
         <div class="right" style="overflow: hidden">
            右侧
          </div>
         ```

         

         ![举例2_已解决](.\img\Css\example2_done.png)
         
   3. **举例3 清除浮动** 

         结构如下

         ```html
         <!DOCTYPE html>
         <html lang="en">
         <head>
             <meta charset="UTF-8">
             <title>Document</title>
             <style>
         
                 .father {
                     background: pink;
                 }
         
                 .son {
                     float: left;
                     background: green;
                 }
         
             </style>
         </head>
         <body>
         
         <section class="father">
             <div class="son">
                 Hello word
             </div>
         
         </section>
         </body>
         </html>
         ```

         效果如下：

         ![](.\img\Css\example3.png)

         **原因：** 子元素浮动，但父元素没有设置高度，导致看不到父元素的背景色（父元素高度为0）

         > 有高度的盒子，才能关住浮动

         **解决方式：**

         ​	方法1：给父元素添加高度

         ​	方法2：给父元素添加overflow：hidden（**计算BFC高度时，子元素的float box区域也会参与计算**）

---

### 元素隐藏的方法

	* opacity：0，元素设置透明，不会影响页面布局，仍然可以触发绑定的事件
	* visibility:hidden,不会影响页面布局，但不会触发绑定的事件
	* display:none, 会影响页面布局
	* z-index设置为负值

---

### 重绘和回流

	* **重绘：**当元素样式的改变不影响布局时，浏览器将使用重绘对元素进行更新，此时由于只需要UI层面的重新像素绘制
	* **回流：** 当元素的尺寸、结构或触发某些属性时，浏览器会重新渲染页面，称为回流。

**回流触发情况：**

 * 页面首次加载

 * 浏览器窗口尺寸改变

 * 元素尺寸、内容、位置发生改变

 * 元素字体样式改变

 * 添加或删除dom节点

 * 触发css伪类（如：hover）

 * 查询某些属性或调用某些方法

   > offsetWidth、offsetHeight、offsetTop、offsetLeft
   > scrollWidth、scrollHeight、scrollTop、scrollLeft
   > getComputedStyle()
   > getBoundingClientRect()
   > scrollTo()

**回流必定触发重绘，重绘不一定触发回流。重绘的开销较小，回流的代价较高**

---

### href 和 src 的区别

href是Hypertext Reference的简写，表示超文本**引用**，指向网络资源所在位置。  
常见场景:  

```
<a href="http://www.baidu.com"></a> 
<link type="text/css" rel="stylesheet" href="common.css">
```

src是source的简写，目的是要把文件**下载**到html页面中去。  

常见场景:

```
<img src="img/girl.jpg"> 
<iframe src="top.html"> 
<script src="show.js">
```

两者作用：

	*	href用于当前文档和引用资源之间建立联系
	*	src用于替换当前内容

----

### Css中link和@import 的区别是什么

	* link属于html标签，而@import是Css提供的方法
	* 页面加载时，link会同时被加载，@import引用的css会等到页面加载完再执行
	* @import只有在ie5以上才能被识别，link无兼容问题
	* link方式引用的样式的权重 高于 @import引用的样式

---

### Css 权重

​	**权重排序**	!important > 行内样式 > id选择器 > 类选择器 > 元素选择器 > 通配符 > 继承 > 浏览器默认属性  

---

### flex布局

Flex（Flexible Box）布局 称为 "弹性布局"，可以为网页的布局提供最大的灵活性，取代了往常的 浮动（float） 布局，并且任何一个容器都可以设置 Flex 布局。    

> 注：设置 Flex 布局后，子元素的 Float 布局将失效     

参考链接:[Flex 布局教程](https://juejin.im/post/5cdfc6ade51d4510a9276955)

```
主轴方向：水平排列（默认） | 水平反向排列 | 垂直排列 | 垂直反向排列
flex-direction: row | row-reverse | column | column-reverse;

换行：不换行（默认） | 换行 | 反向换行(第一行在最后面)
flex-wrap: nowrap | wrap | wrap-reverse;

flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap
flex-flow: <flex-direction> || <flex-wrap>;

主轴对齐方式：起点对齐（默认） | 终点对齐 | 居中对齐 | 两端对齐 | 分散对齐
justify-content: flex-start | flex-end | center | space-between | space-around;

交叉轴对齐方式：拉伸对齐（默认） | 起点对齐 | 终点对齐 | 居中对齐 | 第一行文字的基线对齐
align-items: stretch | flex-start | flex-end | center | baseline;

多根轴线对齐方式：拉伸对齐（默认） | 起点对齐 | 终点对齐 | 居中对齐 | 两端对齐 | 分散对齐
align-content: stretch | flex-start | flex-end | center | space-between | space-around;

```

---

