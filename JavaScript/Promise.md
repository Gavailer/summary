# Promise

### 一、什么是promise？

>**promise** 用于表示一个异步操作最终完成结果（或失败）的值。
>
>一个promise对象代表这个promise在创建出来时不一定已知的值。可以使异步操作最终的返回值、失败原因和相应的处理程序相关联起来

一个promise 必然处于以下几种状态

 * *待定（pending）：*初始状态，既没有被兑现，也没有被拒绝。
 * *已兑现（fulfilled）*: 意味着操作成功完成。
 * *已拒绝（rejected）*: 意味着操作失败。

```js
let promise = new Promise((resolve,reject)=>{ // 状态：pending 创建promise实例后会立即执行
    resolve('success') // 状态：fulfilled
    reject('failed') // 状态：rejected
})
```

> 状态在改变后就不会再改变

### 二、promise解决了什么问题

* 解决回调地狱，代码难以维护
* 支持多个并发请求，获取并发请求中的数据

### 三、promise 用法

例：

```js
let promise = new Promise((resolve,reject)=>{ 
    // 执行异步操作
     setTimeout(function(){
            var num = Math.ceil(Math.random()*10); //生成1-10的随机数
            if(num <= 5){
                // success
                resolve(num);
            }
            else{
                // failed
            	reject('数字太大了');
            }
      }, 2000);
    });

    promise.then(data=>{
        // success
        console('resolved', data)
    }).catch(err=>{
        // failed
        console.log('rejected',err)
    })


```
* resolve: 异步操作执行成功后执行的回调函数
* reject：异步操作执行失败后执行的回调函数