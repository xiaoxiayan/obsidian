1. 准备数据 
   - 内联 -- 测试单例里面直接创造数据
   - 委托 -- 利用函数封装通用数据
   - 隐式创建
     
2. 调用
3. 验证
4. 拆卸



```
 test('add todo', () => {
	 // 准备数据
	 const todoStore = useTodoStore()
	 const title = 'aa'
	// 调用
	todoStore.addTodo(title)
	// 验证
	expect(todoStore.todos[0].title).toBe(title)
	// 拆卸
	afterEach()

 })


```