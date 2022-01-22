
> 记录算法学习，输出更有利于学习！
# 17. 电话号码的字母组合
###

**例子 ：**





#### 对应长度的 for 循环使用 回溯法（递归）
#### 如图：

![17.回溯算法图.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8db14c640e974060acc98e2686370e30~tplv-k3u1fbpfcp-watermark.image?)



回溯三个步骤：

- 确定传入的参数。主要是否需要传入 Index ，可以用于枝剪 、去重直接的操作（这道题没用于去重和枝剪等操作）。
主要需要的参数有 :
输入字母的长度 digits.length ，多长就递归多少层，也用于判断是否需要终止递归。 
digits。映射对应的字母
index 记录当前是第几个字母
```
function backtracking(digits, digits.length, index) {}
```
- 终止条件。
定义数组去收集结果，
当添加到数组中的字符长度 到达 digits.length 的时候说明已经到达最后一层，需要return
```
 if(path.length === digits.length) {
	res.push(path.join(""));
	return;     
}
	
```
- 单层遍历逻辑。
寻找到输入数字中对应的 字符字符串。然后对这个字符串进行递归循环。
```
for(const v of map[digits[index]]) {

	path.push(v);
	
	backtracking(digits, digits.length, index + 1);
	
	path.pop();

 }

```


#### 完整代码


```
```

