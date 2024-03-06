### 直接上代码

```js
 const obj = { a: 1, b: 2, c: 3 };
  const arr = [1, 2, 3];

//问题一
  for (const value in obj) {
  console.log(value);
} 
//问题二
  for (const value in arr) {
  console.log(value);
}
//问题三
  for (const value of obj) {
  console.log(value);
} 
//问题二
  for (const value of arr) {
  console.log(value);
}

结果
//a b c
//0 1 2

//报错
//1 2 3
```

### 结论

- for in 用于遍历对象
- for of 遍历数组