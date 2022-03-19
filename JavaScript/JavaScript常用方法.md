# JavaScript常用方法

### Array

* #### shift() 删除元素

  从数组最前方删除一个元素，返回值是被删除的元素，改变原数组

  ```
  let arr = [1,2,3,4,5]
  console.log(arr.unshift(2))    // 1
  console.log(arr)  //[2,3,4,5]
  ```

* #### pop() 删除元素

  从数组最后方删除一个元素，返回值是被删除的元素，改变原数组

  ``` js
  let arr = [1,2,3,4,5]
  console.log(arr.pop(2))    // 5
  console.log(arr)  //[1,2,3,4]
  ```

* #### unshift() 添加元素

  在数组最前边添加元素，返回值是添加完后数组的长度，改变原数组

  ```js
  let arr = [1,2,3,4,5]
  console.log(arr.unshift(0))    // 6
  console.log(arr)  //[0,1,2,3,4,5]
  ```

* #### push() 添加元素

  在数组最后边添加元素，返回值是添加完后数组的长度，改变原数组

  ```js
  let arr = [1,2,3,4,5]
  console.log(arr.push(6))   // 6
  console.log(arr) // [1,2,3,4,5,6]
  ```

* #### contant 连接数组

  连接两个或多个数组。该方法不会改变现有的数组，而仅仅会返回被连接数组的一个副本。在没有给 concat()方法传递参数的情况下，它只是复制当前数组并返回副本。

  ```js
  let arr=[1,2,3,4];
  let arr2=[11,12,13] 
  let arrCopy = arr.concat(arr2);
  console.log(arr.concat()); // [1, 2, 3, 4] (复制数组)
  console.log(arrCopy); // [1, 2, 3, 4, 11, 12, 13]
  console.log(arr); // [1, 2, 3, 4] (原数组未改变)
  ```

* #### splice() 数组更新

  删除、插入、替换

  删除：指定两个参数 ：开始的位置，删除的个数 arr.splice(x,y)

  ```js
  let arr = [1,3,5,7,9,11];
  let arrRemoved = arr.splice(0,2);
  console.log(arr);   //[5, 7, 9, 11]
  console.log(arrRemoved);    //[1, 3]
  ```

  替换： 指定替换的位置、删除的个数、任意要插入的元素。（插入元素的个数不必与删除的个数相等）

  ```js
  let arr = [1,2,3,4,5]
  let arrRemoved = arr.splice(0,1,'aaa','bbb'); 
  console.log(arr) // ['aaa','bbb',2,3,4,5]
  console.log(arrRemoved) //[1]
  ```

  插入：与替换同理  删除的个数为0即可

  ```
  let arr = [1,2,3,4,5]
  let arrRemoved = arr.splice(0,0,'aaa'); 
  console.log(arr) // ['aaa',1,2,3,4,5]
  console.log(arrRemoved) //[]
  ```

* #### join() 数组转换

  把数组转换成字符串，然后给他规定个连接字符，默认的是逗号(,)

  ```js
  let arr = [1,2,3];
  console.log(arr.join());    // 1,2,3
  console.log(arr.join(""));    // 123
  console.log(arr.join("-")); // 1-2-3
  console.log(arr);   // [1, 2, 3]（原数组不变）
  ```

* #### sort() 排序

* #### reverse() 数组反转

  将数组反转,返回值是反转后的数 会改变原数组

  ```js
  let arr = [1,2,3,4,5]
  console.log(arr.reverse())    // [5,4,3,2,1]
  console.log(arr)    // [5,4,3,2,1]
  ```

* #### slice(start，end) 截取

  提取start到end之间的元素，start闭区间，end开区间

  返回值：含有被提取元素的新数组 不改变原数组

  ```js
  let arr = [1,2,3,4,5]
  console.log(arr.slice(1,3))   // [2,3]
  console.log(arr)    //  [1,2,3,4,5]
  ```

  `start` 可选

  提取起始处的索引（从 `0` 开始），从该索引开始提取原数组元素。如果该参数为负数，则表示从原数组中的倒数第几个元素开始提取，`slice(-2)` 表示提取原数组中的倒数第二个元素到最后一个元素（包含最后一个元素）。如果省略 `start`，则 `slice` 从索引 `0` 开始。如果 `begin` 超出原数组的索引范围，则会返回空数组。

  `end` 可选

  提取终止处的索引（从 `0` 开始），在该索引处结束提取原数组元素。`slice` 会提取原数组中索引从 `begin` 到 `end` 的所有元素（包含 `begin`，但不包含 `end`）。`slice(1,4)` 会提取原数组中从第二个元素开始一直到第四个元素的所有元素 （索引为 1, 2, 3的元素）。如果该参数为负数， 则它表示在原数组中的倒数第几个元素结束抽取。 `slice(-2,-1)` 表示抽取了原数组中的倒数第二个元素到最后一个元素（不包含最后一个元素，也就是只有倒数第二个元素）。如果 `end` 被省略，则 `slice` 会一直提取到原数组末尾。如果 `end` 大于数组的长度，`slice` 也会一直提取到原数组末尾。

* #### every(condition) 数组判别

  依据判断条件，数组的元素**是否全满足**，若满足则返回ture

  ```js
  let arr = [1,2,3,4,5]
  let arr1 = arr.every( (i, v) => i < 3)
  console.log(arr1)    // false
  let arr2 = arr.every( (i, v) => i < 10)
  console.log(arr2)    // true
  ```

* #### some(condition) 数组判别

  依据判断条件，数组的元素是否有一个满足，若有一个满足则返回ture

  ```js
  let arr = [1,2,3,4,5]
  let arr1 = arr.some( (i, v) => i < 3)
  console.log(arr1)    // true
  let arr2 = arr.some( (i, v) => i > 10)
  console.log(arr2)    // false
  ```

* #### find(condition) 查找元素

  找到第一个符合条件的数组成员

  ```js
  let arr = [1,2,3,4,5,2,4]
  let arr1 = arr.find((value, index, array) =>value > 2)
  console.log(arr1)   // 3
  ```

* #### findIndex(condition) 查找元素

  找到第一个符合条件的数组成员的索引值

  ```js
  let arr = [1,2,3,4,5]
  let arr1 = arr.findIndex((value, index, array) => value > 3)
  console.log(arr1)  // 3
  ```

* #### includes() 判断元素

  判断数中是否包含给定的值

  ```
  let arr = [1,2,3,4,5]
  let arr1 = arr.includes(2)  
  console.log(arr1)   // ture
  let arr2 = arr.includes(9) 
  console.log(arr2)    // false
  let arr3 = [1,2,3,NaN].includes(NaN)
  console.log(arr3)  // true
  复制代码
  ```

  与indexOf()的区别：

  - indexOf()返回的是数值，而includes()返回的是布尔值
  - indexOf() 不能判断NaN，返回为-1 ，includes()则可以判断

* #### reduce()

  逐个遍历数组元素，每一步都将当前元素的值与上一步的计算结果相加（上一步的计算结果是当前元素之前所有元素的总和）——直到没有更多的元素被相加。

   ```js
   reduce(function(previousValue, currentValue) { /* ... */ })
   reduce(function(previousValue, currentValue, currentIndex) { /* ... */ })
   reduce(function(previousValue, currentValue, currentIndex, array) { /* ... */ })
   reduce(function(previousValue, currentValue, currentIndex, array) { /* ... */ }, initialValue)
   ```

  一个 “reducer” 函数，包含四个参数：

  - `previousValue`：上一次调用 `callbackFn` 时的返回值。在第一次调用时，若指定了初始值 `initialValue`，其值则为 `initialValue`，否则为数组索引为 0 的元素 `array[0]`。
  - `currentValue`：数组中正在处理的元素。在第一次调用时，若指定了初始值 `initialValue`，其值则为数组索引为 0 的元素 `array[0]`，否则为 `array[1]`。
  - `currentIndex`：数组中正在处理的元素的索引。若指定了初始值 `initialValue`，则起始索引号为 0，否则从索引 1 起始。
  - `array`：用于遍历的数组。

  `initialValue` 可选

  作为第一次调用 `callback` 函数时参数 *previousValue* 的值。若指定了初始值 `initialValue`，则 `currentValue` 则将使用数组第一个元素；否则 `previousValue` 将使用数组第一个元素，而 `currentValue` 将使用数组第二个元素。

  ```JavaScript
  // 简单用法
  // 累加
  const arr = [3,4,4,5,4,6,5,7];
  const a = arr.reduce((pre, cur) => {return pre+cur})
  // 数组去重
  const b = arr.reduce((pre, cur) => {
  	if(!pre.includes(cur)) {
  		return pre.concat(cur)
      } else {
  		return pre
      }
  }, [])
  // [3, 4, 5, 6, 7]
  // 数组扁平化
  const arrs = [[2,3,2], [3,4,5]]
  const c = arrs.reduce((pre, cur) => {
  	return pre.concat(cur)
  }, [])
  // [2, 3, 2, 3, 4, 5]
  ```



---

### String

* #### replace() 

  替换匹配的字符串

  ```
  const str = 'hello guys';
  console.log(str.replace('guys', 'man'))  // hello man
  ```

* #### split() 

  将字符串转为数组

  ````js
  const str = 'abcdefg'
  console.log(str.split('')) //['a', 'b', 'c', 'd', 'e', 'f', 'g']
  console.log(str.split(''),3) //['a', 'b', 'c']
  
  const str1 = 'a,b,c,d,e'
  console.log(str1.split('')) // ['a', ',', 'b', ',', 'c', ',', 'd', ',', 'e']
  console.log(str1.split(',')) // ['a', 'b', 'c', 'd', 'e']
  ````

* #### substr(start,length)

  `start`开始提取字符的位置。如果为负值，则被看作 `strLength + ``start，其中` `strLength` 为字符串的长度（例如，如果 `start` 为 `-3，则被看作` `strLength + (-3)）。`

  `length`可选。提取的字符数。

  **注意事项**

  `start` 是一个字符的索引。首字符的索引为 0，最后一个字符的索引为 字符串的长度减去1。`substr` 从 `start` 位置开始提取字符，提取 `length` 个字符（或直到字符串的末尾）。

  如果 `start` 为正值，且大于或等于字符串的长度，则 `substr` 返回一个空字符串。

  如果 `start` 为负值，则 `substr` 把它作为从字符串末尾开始的一个字符索引。如果 `start` 为负值且 `abs(start)` 大于字符串的长度，则 `substr` 使用 0 作为开始提取的索引。注意负的 `start` 参数不被 Microsoft JScript 所支持。

  如果 `length` 为 0 或负值，则 `substr` 返回一个空字符串。如果忽略 `length`，则 `substr` 提取字符，直到字符串末尾。

  ```js
  //示例：
  var str = "abcdefghij";
  
  console.log("(1,2): "    + str.substr(1,2));   // (1,2): bc
  console.log("(-3,2): "   + str.substr(-3,2));  // (-3,2): hi
  console.log("(-3): "     + str.substr(-3));    // (-3): hij
  console.log("(1): "      + str.substr(1));     // (1): bcdefghij
  console.log("(-20, 2): " + str.substr(-20,2)); // (-20, 2): ab
  console.log("(20, 2): "  + str.substr(20,2));  // (20, 2):
  ```

* #### substring(indexStart,indexEnd)

  方法返回一个字符串在开始索引到结束索引之间的一个子集, 或从开始索引直到字符串的末尾的一个子集。

  `indexStart`需要截取的第一个字符的索引，该索引位置的字符作为返回的字符串的首字母。

  `indexEnd`可选。一个 0 到字符串长度之间的整数，以该数字为索引的字符不包含在截取的字符串内。

  **注意事项**

  `substring` 提取从 `indexStart` 到 `indexEnd`（不包括）之间的字符。特别地：

  - 如果 `indexStart` 等于 `indexEnd`，`substring` 返回一个空字符串。
  - 如果省略 `indexEnd`，`substring` 提取字符一直到字符串末尾。
  - 如果任一参数小于 0 或为 [`NaN`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/NaN)，则被当作 0。
  - 如果任一参数大于 `stringName.length`，则被当作 `stringName.length`。
  - 如果 `indexStart` 大于 `indexEnd`，则 `substring` 的执行效果就像两个参数调换了一样。见下面的例子。

* #### trim()

  去掉字符两端的空格

  ```js
  cosnt str = '   Hello    '
  console.log(str.trim()) // Hello
  ```

  

---

