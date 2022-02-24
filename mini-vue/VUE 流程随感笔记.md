create(app).mount('#root')
create(app) 会 返回一个 APP dom. mount挂在到 根节点上，
APP -> 会经过处理，收集 effect 。 分为初始化 和 更新
流程：初始化 -> 渲染 render -> 调用 patch 解析
1. 核心
 patch (vnode ， rootContainer)  ：基于 vnode 的类型进行不同类型的组件处理 。 

根据 vnode的 类型 分为2种，
#### 1 、element 型， 就是当前 vnode 中的 div 等标签
  * 初始化步骤：
	  1. 创建 真实元素， document.createElement(type);
	  2. 判断要渲染的内容类型， text（文本） 直接渲染SetElementText , 如果是 array， 循环调用 patch
	  3. 设置元素 props
	  4. beforeMount 
	  5. 渲染，插入 insert 到 创建的元素中
	  6. mounted
  * 更新步骤：
	  1. 对比 props ， 更新 props.
	  2. 对比children ， 遍历 patch 渲染。 有几种情况。textTotext , textToArray, arrayToText , ArrayToArray( 比较特殊， 需要使用 diff 算法去 对比，性能优化)

	
#### 2、component 型， component 组件
 * 组件初始化：
	1. 创建 component instance 对象 ， 实例对象，
	2. 
	



