1：webpack多入口时候，打包时候怎么打包成单独的chunk；
	配置多入口， entry : { a: 'app1', b: 'app2'  }



2：module和chunk的区别；
module 相当于源文件， chunk 是指 多个具有引用关系的module 生成的一个 图形结构
我们直接写出来的是 module，webpack 处理时是 chunk，最后生成浏览器可以直接运行的 bundle
3：webpack打包原理；
	最终输出的JS 文件， 内容是多个function ， 里面是对应的每个模块的 function 
mini-webpack : 
流程：
	1. 获取入口文件， 例如 main.js 
	2. 分析文件，获取文件module之间的依赖关系。 生成 ast语法树， 也就是对应的 chunk .
		1.  获取module 可以用  fs 去读取module， 读取内容是 filePath, code , 获取依赖关系，  一般是 ESM 的模块引入，但是生成函数的时候，需要去转成 COMMONJS 的 require， 可以使用 babel插件
	3. 根据ast 语法树， 处理成最后的 bundle