# v2 监听的缺陷
vue2  的双向数据绑定，使用的 `Object.defineProperty(obj, key , GetAndSet)` ,
需要传三个参数， 对象，监听的 key， handle 
proxy  是监听整个 对象，只要有变动就可以操作

# v2 - v3 v-model 的改动
v2 : @input :value  @change
v3: @update: modelvalue @change

如果你不想用 value呢
props 接受，然后 emit('update: msg', event)




