# v2 监听的缺陷
vue2  的双向数据绑定，使用的 `Object.defineProperty(obj, key , GetAndSet)` ,
Vue2 数组的监听， vue 通过 Object.create让arrayMethods 继承了数组的原型， 然后在调用响应式对象方法的时候，去调用了apply ，调用数组的真正方法，并且去 get, set 监听对应的变化数据
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

# 生命周期的改变


# Composition Api + setup 语法糖。
  优化逻辑组织
	  在`vue2`中，我们是通过`mixin`实现功能混合，如果多个`mixin`混合，会存在两个非常明显的问题：命名冲突和数据来源不清晰。
	  而通过`composition`这种形式，可以将一些复用的代码抽离出来作为一个函数，只要的使用的地方直接进行调用即可。


# 性能优化

编译阶段。对diff算法优化、静态提升、事件监听缓存、SSR优化等。

> vue3 的 diff算法 相比 v2 加入了静态标记， 文本类的 vnode直接渲染
> 响应式系统。。 proxy 替代了 object.defineProperty , 监听对象不再需要深度遍历。
> 
> 体积包减少，Compostion API 的写法，可以更好的进行tree shaking，减少上下文没有引入的代码，减少打包后的文件体积。 判断的话，就是出现
> 

#  对typeScript的支持更加友好


	`Vue3`是基于`typeScript`编写的，提供了更好的类型检查，能支持复杂的类型推导。