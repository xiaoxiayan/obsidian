1. 准备数据
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