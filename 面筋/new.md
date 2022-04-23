new做了什么事情呢，
1. 创建一个空对象。并且 this 变量引用该对象， 同事还继承了该函数的原型
2. 属性和方法被加到 this 引用的对象中
3. 新创建的对象由 this 所引用， 并且最后隐式的返回 this

```
function create() {
	// 创建一个空对象
	let obj = new Object()
	//  获得构造函数
	let Con = [].shift.call(arguments)
	
	// 
	



}


```
   