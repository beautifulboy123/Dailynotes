### 手写Call

```js
//相当于在对象上先新增调用的函数，然后再调用完以后再进行删除
Function.prototype.myCall=function(context =window,args){
    let key=Symbol();
    args=args?args:[]
    context[key]=this;// this指向调用的函数
    let result=context[key](...args)
    delete context[key]
    return result
}
```

### 手写apply

```js
Function.prototype.myCall=function(context =window,args=[]){
    let key=Symbol();
    context[key]=this;// this指向调用的函数
    let result=context[key](...args)
    delete context[key]
    return result
}
```

