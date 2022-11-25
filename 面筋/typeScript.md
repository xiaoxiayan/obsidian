对比 js 优缺点， 泛型，
JS 是动态语言， 在编译的时候不做类型检查，只有在运行的时候才会去检查，
而ts 恰恰相反，在编译的时候就对类型做检查，所以在运行的时候会不报错
类型检查可以在运行时做，叫做动态类型检查，也可以在编译时做，叫做静态类型检查。

## interface 与 type 异同点

在对象扩展情况下，interface 使用 extend来继承，而type 使用 & 
同名的 interface 会自动合并，并且在合并时会要求兼容原接口的结构。
interface 与 type 都可以描述对象类型，函数类型和 class类型， 但是无法 像type 一样去表达 元祖， 一组联合型
interface 无法使用映射类型等类型工具，也就意味着在类型编程场景中我们还是应该使用 type 。


# TS中any的作用是什么？

为编程阶段还不清楚的变量一个类型，这些值可能来自于动态的内容，比如来自用户输入或第三方代码库。这种情况下，我们不希望类型检查器对这些值进行检查而是直接让他们通过编译阶段的检查

# any、 never 、 unknown 、 null、 undefined、 void

any:  动态的变量类型， 会丢失 类型检查的作用
never: 永远不存在值的类型
unknown: 任何类型的值都可以赋值给 unknown , 但是 unknown只能赋值给 unknown 本身和 any 类型。如果赋值给其他类型前面需要断言 as 
null 和 undefined ：默认情况下是所有类型的子类型。可以把这两个类型赋值给number类型。 但是当我们指定 strictNullChecks： tru标记的时候， 只能赋值给自身。
void： 没有任何类型。一般用在 fun没有返回值的时候定义void


#  keyof和typeof关键字的作用

keyof 是 索引类型查询操作符， 获取索引的 key, 构成联合类型
相当于 object.keys
```
type MyPick <T, k extends keyof T> = {
	[P in K] : T [P]
}

// 过滤出内容

type obj = {
	age: Number;
	name: String;
}
type pickObj = MyPick<obj, 'age'>
```

typeof  获取一个变量或对象的类型

```
type Person = {
	
}


```