
2章

什么是面向过程引入js方法

什么是面向对象引入js方法


webpack定义是什么，

module.exports  exports   require  

export export default  import  



dev  和 prod 区别：

一个压缩，一个不压缩



3章



url-loader 和 图片加载器区别  
 limit: 2048




css-loader 和 style-loader 区别

use 中的执行顺序




postcss-loader 厂商前缀



字体文件，file-loader


	{
		test: /\.(eot|ttf|svg)$/,
		use: {
			loader: 'file-loader'
		} 
	}




source-map 作用，用于生成打包后文件和源文件之间的对应关系

dev 和 pro 环境下是不同的 



热模块更新的核心：


删除之前的dom元素，重新执行完成上次状态的代码， 看起来的样子就像：
dom没改，只改了css，只变化了你修改代码的部分，实际上浏览器重新刷新，帮你重新执行了js操作



4章

什么是tree shaking , 去掉模块没有使用的部分

3点，

1. 只支持import
2. dev下需要配置optimization 和 package.json， production环境只需要配置 package.json

sideEffect: false
useExports: true

3. import是静态导入，require是动态引入  
有啥区别？



ES6 模块的设计思想，是尽量的静态化，使得编译时就能确定模块的依赖关系，以及输入和输出的变量。

Require是CommonJS的语法，CommonJS的模块是对象，输入时必须查找对象属性。

```
// CommonJS模块
let { stat, exists, readFile } = require('fs');

// 等同于
let _fs = require('fs');
let stat = _fs.stat;
let exists = _fs.exists;
let readfile = _fs.readfile;
```


above：整体加载fs模块（即加载fs所有方法），生成一个对象"_fs"，然后再从这个对象上读取三个方法，这叫“运行时加载”，因为只有运行时才能得到这个对象，不能在编译时做到静态化。

ES6模块不是对象，而是通过export命令显示指定输出代码，再通过import输入。


[参考资料：](https://www.cnblogs.com/linziwei/p/7853305.html)



dev 和 prod 配置文件有何不同？


1. mode
2. devtool 正式环境中没有 eval
3. dev 模式下有 devServer
4. dev  usedExports tree shaking 中配置




代码分割定义：
业务代码和库代码分别打包到不同文件中
一般库代码是不会变化的的，一次加载即可，所以后面加载可以利用浏览器的缓存，提高页面加载效率


难道对页面上所有的文件都打包吗？
splitChunkPlugin

当 minSize 低于某个值，不会做代码分割

懒加载：  
执行某些操作后，再引入js文件


css代码分割：   
js和css分割到不同文件中。  
miniCssExtractPlugin 由于不支持热更新，所以在开发环境下一般不使用这个插件， 适合在线上环境下做打包使用。  




cacheGroups中配置


contenthash
























