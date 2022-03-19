# new

### 基本原理

`new` 命令的作用就是执行一个`构造函数`，并返回一个`对象实例`。new命令会依次执行下列操作：

* 创建一个空对象
* 将空对象的原型指向构造函数的`prototype`属性，从而从原型上继承方法
* 将空对象赋值给构造函数内部的`this`，执行构造函数中的代码，以获取私有属性
* 判断构造函数的返回值res是否为对象，是则返回res，否则返回创建的对象

### 基本用法

new命令的作用，就是调用一个构造函数，并且返回一个对象实例。

```js
function Person(){
    this.name = 'Jack'
}
let boy = new Person();
console.log(boy.name) // Jack
```

使用`new`命令时，构造函数也可接受参数

```js
function Person(name,age){
    this.name = name;
    this.age = age;
}
let boy = new Person('Jack',12);
console.log(boy.name,boy.age) // Jack,12
```

### 实现一个new方法

```js
function myNew(fn,...args){
    // 创建一个空对象
    const obj = {};
    // 将对象的__proto__指向构造函数的prototype
    obj._proto_ = fn.prototype;
    // 将空对象赋值给构造函数内部的this，并获取返回值
   	const res = fn.apply(obj,args)
    // 判断返回值
    return res instanceof Object ? res : obj
}
```

