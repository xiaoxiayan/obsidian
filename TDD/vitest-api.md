　 it -- describe -- test 
都是启动函数


describe.skip 
describe.only


expect  -- 断言
.toBe() ---  ===
.toEqual() --- object
.toBeTruthy(). --- haveValue --- 1 , true, '123'
.toBeFalsy() --- noValue.   --- 0, false, ''
.toContain --- contain  --- includes --- array,string
.toThrow --- isError

// 模拟数据
会全局置顶这个 操作 stub
vi.mock('./filePath',  () =>  {
	return {
		useAge: () => 2 // fetchdataFn
	}
})

vi.mock('./user')
// 需要再模拟后再导入
vi.domock('./user', () => {

})
it('dd', () => {
	vi.mocked(useAge).mockReturnValue(2)
})

// 异步  asy await
```
export function fetchAge () : Promise<number>{
 return  new Promise(resolve, reject) => {
	  setTimeout(() => {
		  return resolve(18)
	  },  0 )
 }
}

```

// 异步 axios
```
import axios from "axios"
vi.mock('axios')
test('第三方模块处理 axios', async () => {
	vi.mocked(axios).mockResolvedValue({name: 'xxp', age: 2})
vi.mocked(axios.get).mockResolvedValue({name: 'xxp', age: 2})

})



```

// 获取 export 中所有的属性 , class 类

```
vi.mock('./path', async (importOriginal) => {
	const config = await importOriginal
	 
	return {
		...config
		name: 'c'
	
	}
})



describe('使用变量的形式', () => {
	it ('tell name', () => {
		const r = fn()
		
	})

})


```


// stubEnv 可以用在环境变量
```
it("process", () => {
	// process.env.U = "2"
	vi.stubEnv("U", "2")
	const r = 2 * process.env.U
	expect(r).toBe(4)
	vi.unstubAllEnvs()
})

afterEach(() => {
	// 恢复原有的值
	vi.unstubAllEnvs()
})


```

// 全局 global -- window 
// 如 window.xx
```
 it ("double u", () => {
		vi.stubGlobal("key", { age: 12}  )
	

})

it ("innerHeight", () => {
	vi.stubGlobal("innerHeight", 100)
	
})

```


// 间接层的测试

```
 依赖底层 变量的 测试。
 可以包装成函数
 然后使用 vi.mock
funciton getInnerHeight () {
	return window.innerHeight
}

vi.mock('./path', () => {
return {
	getInnerHeight: () => 200
}
})


it('fn', () => {
	const r = getInnerHeight()
	expect(r).toBe(200)
})

```


状态验证。

行为验证。
定义：验证对象之间的交互是否按照预期进行。
行为验证背后的逻辑： 状态的改变是由交互引起的，如果所有的交互都正确，那么就可以推断最终的状态也不会错。
mock:  测试替身vi.mock，记录交互信息 , 提供数据 验证 vi.fn , vi.sypon 
缺点： 1、破坏了封装性 --> 白盒测试，暴露了内部的实现细节。2、丧失了测试的有效性。如果只改变了测试具体细节内容，测试还是通过的。但是页面逻辑就跑不通   expect(fn).toBeCalled() .. 实际fn没跑业务逻辑
使用的时机： 1 、优先是使用状态验证
2、 当测试 api.axios --？


```

class UserService {
	constructor(private datebase: Database) {}
	createUser(name: string): User {
	const id = 110
		const newUser: User = {id, name}
}



it("should create user", () => {
	const database = new Database()
	// 监听对象中的 fn\ key
	vi.syOn(database, "addUser")
	const userService = new UserService(database)
	userService.createUser('aaa')
	expect(database.addUser).toBeCalled()
	

	
	

})


```


多种API测试方案   vi.mock('../api')
1. 直接 mock axios 

```
vi.mocked(axios.post).mockResolvedValue({data:{}})
vi.mocked(axios.post).mockImplementation((path, parmas) => {
	return Promise.resolve({data:{data}}， state)
})

```
2.  mock 中间层
```
vi.mocked(fetchAddTodo).mockImplementation((title) => {
 return Promise.resolve({
	 data: {todo : {id : 1, title}}
 })
}) 

```
3. 
