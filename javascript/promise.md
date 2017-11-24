## promise

![](/assets/Promises.png)

## 语法 {#语法}

```
new Promise( function(resolve, reject) {...} /* executor */  );
```

参数： executor是一个带有`resolve` 和 `reject` 两个参数的函数 。

`executor`函数在Promise构造函数执行时同步执行，被传递 `resolve` 和 `reject` 函数（executor 函数在Promise构造函数返回新建对象前被调用）。

