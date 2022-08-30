[[00.mini-vue]]

自定义渲染器， 把自己的渲染逻辑 渲染到不用的平台，dom ，canvas
封装渲染逻辑达到
实现 基于 dom 的渲染， 基于canvs 渲染

实现：
dom -->  mountElement () {
   创建真实元素
   docment.createElement(vnode.type)
   元素添加属性
   el.setAttribute()
  把元素 添加到 容器中 ，body
  container.append(el)
}

canvas  --> new Element() , el.x = 10,   container.addChild()


把他变成封装的稳定的接口， 直接调用。根据type , 去走对应的API
如何让用户传入渲染的接口，创建 runtime-dom 
输出fun
创建元素：createElement()
设置属性：patchProp(el, key, val )
插入父级： insert(el, container)


createRenderer（ {
	createElement, 
	patchProp,
	insert
}）

传入 options 

步骤：
创建 render-dom --> index ， 实现函数
createElement，patchProp， insert

采用闭包 包裹render.ts 中函数 作为一个整体的输出
createRenderer,
函数中返回一个 createApp, 调用 createApp.ts 中输出的 createAppAPI 去保证了之前的完整，在正常渲染dom 都是使用 createApp. 
自定义的话使用 createRenderer （options) 传入 自定义的函数去渲染。

创建 runtimer-dom 作为最上一层去输出函数，










