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





