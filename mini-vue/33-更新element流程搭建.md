[[00.mini-vue]]

在 渲染 subTree 的时候 ，用  effect 包裹。
把 subTree 当依赖收集起来。这样触发  getter的时候，就会渲染。
初始化的时候不去对比，只有更新的时候对比。
