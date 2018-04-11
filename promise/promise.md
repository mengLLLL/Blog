### promise快速扫盲

> 基于promise迷你书做的读书笔记加个人理解

#### promise是什么

> 处理异步操作用的，官方一点讲就是抽象**异步处理对象**以及对其进行各种操作的组件。

#### promise怎么用

- 代码示例
 
```javascript
var promise = new Promise(function(resolve, reject) {
    // 异步处理
    // 处理结束后、调用resolve 或 reject
});

promise.then(onResolved) // 此时resolve函数生效
promise.catch(onRejected) // 此时reject函数生效

// 等同于以下写法
promise.then(onResolved, onRejected) // 顺序不要错
```

- 代码解释

    1. 通过new的方式，创建一个promise对象
    2. 同时给构造函数传入一个函数，传入的函数接受两个函数作为参数，分别作为异步操作成功、失败的时候进行的操作 
    3. promise.then接受一个函数，此函数即创建promise对象时形参所接受的resolve函数

#### promise的状态

- Fulfilled, 成功
- Rejected， 失败
- Pending，既不成功，也不失败，即promise对象刚被创建后的初始化状态等

> 从Pending转换为Fulfilled或Rejected之后， 这个promise对象的状态就**不会再发生任何变化**。当promise的对象状态发生变化时，用`.then` 来定义只会被调用一次的函数。

#### promise实战

- 语法糖(快速创建promise对象)

    > `Promise.resolve(value)`、`Promise.reject(value)`, 是 `new Promise()`的简写，在测试的时候可以快速的编写测试代码

- promise链式调用，怎么就厉害了啊？

    > 来一起探索下吧

    ```javascript
    var promise = new Promise()
    ```

- Promise.all

    > 接受一个promise对象组成的数组，当数组的所有promise对象都成功才会调用onResolved

    ```javascript
    Promise.all([pro1, pro2])
    ```
- Promise.race

    > 接受一个promise对象组成的数组，当数组钟有一个promise对象成功/失败就会调用onResolved/onRejected