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

// 异步axios 
export fetchAge  => {
 return  new Promise(resolve, reject) => {
	  setTimeout(() => {
		  return resolve(18)
	  },  0 )
 }
}


