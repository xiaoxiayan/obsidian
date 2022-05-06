# v2 监听的缺陷
vue2  的双向数据绑定，使用的 `Object.defineProperty(obj, key , GetAndSet)` ,
需要传三个参数， 对象，监听的 key， handle 
proxy  是监听整个 对象，只要有变动就可以操作

# v2 - v3 v-model 的改动
v2 : @input :value  @change
v3: @update: modelvalue @change

如果你不想用 value呢
props 接受，然后 emit('update: msg', event)


# toRefs 的妙用
[Vue3 学习笔记 —— toRefs_tanleiDD的博客-CSDN博客_...torefs](https://blog.csdn.net/TL18382950497/article/details/116427498)


# Vue2 如何把响应式转成非响应式，

# vue3 Hooks
相当于一个 mixin 

# vue3 hook 监听生命周期

## v2 
```
<template>
  <child-component @hook:updated="onUpdated">
</template>
```

## v3
```
<template>
  <child-component @vnode-updated="onUpdated">
</template>
```

# 异步组件，
v3 中新增了  `defineAsyncComponent`

