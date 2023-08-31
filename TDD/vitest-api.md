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


