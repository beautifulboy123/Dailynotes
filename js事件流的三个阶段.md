### 三个阶段

#### 捕获阶段

#### 目标阶段

#### 冒泡阶段

事件是从冒泡阶段开始的

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <div class="big">
    <div class="center">
      <div class="small">

      </div>
    </div>
  </div>
</body>
<script>
const big=document.querySelector(".big")
const center=document.querySelector(".center")
const small=document.querySelector(".small")
big.onclick=function(e){
 console.log(e.target);
}
center.onclick=function(e){
 console.log(e.target);
}
small.onclick=function(e){
 console.log(e.target);
}
</script>
<style>
  .big{
    width: 300px;
    height: 300px;
    background-color: aqua;
  }
  .center{
    width: 200px;
    height: 200px;
    background-color: orange;
  }
  .small{
    width: 100px;
    height: 100px;
    background-color: yellow;
  }
</style>
</html>
当我点击smll的时候 会打印三个small 当我点击center的时候，会打印俩个small 是因为捕获是从外到内的
```

### 题目

```html
<div onclick="console.log('first div')">
    <div onclick="console.log('second div')">
      <button onclick="console.log('button')">Click!</button>
    </div>
  </div>
结果是 button second first
因为第一个题目是捕获 注意关键字(e.target) 所以会打印三个small
而第二个题目是冒泡 触发s
```

