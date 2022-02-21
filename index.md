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

      因为**第二条：BFC区域是一个独立的区域，不会影响外面的元素**。

  	2. **举例2 BFC区域不与float区域重叠**

      

