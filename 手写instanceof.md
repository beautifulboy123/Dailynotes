### 自创写法

```js
function _instanceof(left,right){
    //判断是不是基本数据类型
    if(typeof left !=='object'||left==null) return false
    return object.getProtypeOf(left)===right.prototype
}
```

### 标准写法

```js
function _instanceof(left, right) {
    // 判断 left 是否为对象
    if (typeof left !== 'object' || left == null) return false;
    // 使用原型链判断 left 是否是 right 的实例
    let proto=object.getProtypeOf(left);
    while(proto)
        {
            if(proto===right.prototype)
                return true;
            proto=object.getProtypeOf(proto);
        }
    return false
}

```

