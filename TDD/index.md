1. 准备数据
   
3. 调用
4. 验证
5. 拆卸



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