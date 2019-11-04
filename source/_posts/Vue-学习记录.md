---
title: Vue 学习记录
date: 2019-11-05 00:31:19
tags:
---
## 子组件与父组件的加载时机
parent created -> parent beforeMount -> child created -> child beforeMount -> child mounted ->  parent mounted
待补充


## vue列表v-for="(item, index) in list" :key=index 和 不绑定key的效果一样

``` javascript
//判断是否同一个vnode
function sameVnode (a, b) {
  return (
    a.key === b.key && (
      (
        a.tag === b.tag &&
        a.isComment === b.isComment &&
        isDef(a.data) === isDef(b.data) &&
        sameInputType(a, b)
      ) || (
        isTrue(a.isAsyncPlaceholder) &&
        a.asyncFactory === b.asyncFactory &&
        isUndef(b.asyncFactory.error)
      )
    )
  )
}
```

如果非要用，单独使用列表元素里面的值。
官方：
当 Vue 正在更新使用 v-for 渲染的元素列表时，它默认使用“就地更新”的策略。如果数据项的顺序被改变，Vue 将不会移动 DOM 元素来匹配数据项的顺序，而是就地更新每个元素，并且确保它们在每个索引位置正确渲染。这个类似 Vue 1.x 的 track-by="$index"。

这个默认的模式是高效的，但是只适用于不依赖子组件状态或临时 DOM 状态 (例如：表单输入值) 的列表渲染输出。

无key就地更新，直接当前元素innerText修改，
有key则对其进行匹配，进行重用或者重新排序。
