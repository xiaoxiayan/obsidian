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

