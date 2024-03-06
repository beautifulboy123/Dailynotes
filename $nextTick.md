### 应用场景

由于视图更新是异步的，	vue是数据驱动视图嘛，当我们更改数据的时候，并不能获取到更新后的dom节点，但是我们假如有一个需求，比如说我有一个div 里面是一个响应式数据value，我们现在要更改value值的时候，拿到更改以后的dom节点数据，就需要用到$nectTIck。当我们数据一变，就会触发watcher，如果页面是多个修改，最终会渲染一次，因为vue会进行一些去重和过滤操作。

```js
//去重和过滤操作
this.count=100；//
this.count=200；//
this.count=300；// 每次更改都会触发一次watcher
//实现去重和过滤操作 
const id = watcher.id
  if (has[id] != null) {
    return
  }
 //这样就会使得每个要更新的组件只会刷新一次，也是用到了nextTick方法
```

```js
export function queueWatcher(watcher: Watcher) {
  const id = watcher.id
  if (has[id] != null) {
    return
  }

  if (watcher === Dep.target && watcher.noRecurse) {
    return
  }

  has[id] = true
  if (!flushing) {
    queue.push(watcher)
  } else {
    // if already flushing, splice the watcher based on its id
    // if already past its id, it will be run next immediately.
    let i = queue.length - 1
    while (i > index && queue[i].id > watcher.id) {
      i--
    }
    queue.splice(i + 1, 0, watcher)
  }
  // queue the flush
  if (!waiting) {
    waiting = true

    if (__DEV__ && !config.async) {
      flushSchedulerQueue()
      return
    }
    nextTick(flushSchedulerQueue)
  }
```

![image-20240305104224726](C:\Users\周龙\AppData\Roaming\Typora\typora-user-images\image-20240305104224726.png)

### $nectTick

本身是一个函数，接收一个回调函数，里面的函数会放在任务队列里进行操作，会将回调延迟到下次DOM更新循环之后执行



