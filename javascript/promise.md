## promise

![](/assets/Promises.png)

#### 语法

```
new Promise( function(resolve, reject) {...} /* executor */  );
```

参数： executor是一个带有`resolve` 和 `reject` 两个参数的函数 。

`executor`函数在Promise构造函数执行时同步执行，被传递 `resolve` 和 `reject` 函数（executor 函数在Promise构造函数返回新建对象前被调用）。`resolve` 和 `reject` 函数被调用时，分别将promise的状态改为_fulfilled（_完成）或rejected（失败）。executor 内部通常会执行一些异步操作，一旦完成，可以调用resolve函数来将promise状态成_fulfilled_，或者在发生错误时将它的状态改为rejected。

#### 方法：

[`Promise.all(iterable)`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)

这个方法返回一个新的promise对象，该promise对象在iterable参数对象里所有的promise对象都成功的时候才会触发成功。

[`Promise.race(iterable)`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/race)

当iterable参数里的任意一个子promise被成功或失败后，父promise马上也会用子promise的成功返回值或失败详情作为参数调用父promise绑定的相应句柄，并返回该promise对象。

[`Promise.reject(reason)`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/reject)

返回一个状态为失败的Promise对象，并将给定的失败信息传递给对应的处理方法

[`Promise.resolve(value)`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve)

返回一个状态由给定value决定的Promise对象。

#### 示例：

说明：promise向下传参，promise通过resolve， then通过return。

```js
   let myFirstPromise = new Promise(function(resolve, reject){
	    //当异步代码执行成功时，我们才会调用resolve(...), 当异步代码失败时就会调用reject(...)
	    //在本例中，我们使用setTimeout(...)来模拟异步代码，实际编码时可能是XHR请求或是HTML5的一些API方法.
	    setTimeout(function(){
		    //reject("失败");
		    resolve("成功!"); //代码正常执行！
	    }, 250);
    });

    myFirstPromise.then(function(successMessage){
	    //successMessage的值是上面调用resolve(...)方法传入的值.
	    //successMessage参数不一定非要是字符串类型，这里只是举个例子
	    console.log("Yay! " + successMessage);
	    return 'secMsg';
    }).then(function (secMsg) {
	    console.log(secMsg);
    }).catch(function (error) {
	    console.log(error);
    });
```



