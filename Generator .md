### Generator 

Generator 函数是 ES6 提供的一种异步编程解决方案,可以把它理解为一个机器，里面封装了很多状态。执行Generator函数会返回一个遍历器的对象

### 特征

1. function* helloWorldGenerator 函数名字前有*
2. 关键词yield

### 代码

```js
function* helloWorldGenerator() {
  yield 'hello';
  yield 'world';
  return 'ending';
}

var hw = helloWorldGenerator();
hw.next()
// { value: 'hello', done: false }

hw.next()
// { value: 'world', done: false }

hw.next()
// { value: 'ending', done: true }

hw.next()
// { value: undefined, done: true }
```

### 特点

1. **惰性求值：** Generator 函数可以实现惰性求值，即按需生成数据，节省内存空间。通过在循环中使用 yield 关键字，可以在每次迭代时生成一个值，并在下一次迭代时继续执行，避免一次性生成所有数据。
