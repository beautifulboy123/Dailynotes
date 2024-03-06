### 疑惑

- 如何传不确定个数的参数
- 如何遍历对象中的属性
- 如何执行构造函数

### 解答

...args

for in  （不过也用不到）

fn.apply(fn,...args)

### 思路

创建一个新对象obj

让obj拥有构造函数的原型对象

让obj拥有原型属性

返回obj

### 实现

```js
   function Person(firstName,lastName){
        this.firstName=firstName
        this.lastName=lastName
    }
    Person.prototype.age=12;
    function _new(fn,...args){
        let obj={}
        obj.__proto__=fn.prototype;
        fn.apply(obj,args)
        return obj
    }
```

