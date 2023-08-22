### 1.准备TS编译环境

1. 首先你需要安装好nodejs环境

2. 安装typescript，推荐全局安装：

   > npm install  typescript -g

3. 确认下，安装是否成功

   > tsc -v

   如果能够正常输出版本号，就说明可以正常使用了

4. 为插件项目新建ts配置，在插件目录下执行初始化命令

   > tsc --init

   该命令会创建`tsconfig.json`文件，该文件可以设置`TypeScript`编译时的配置



### 2.配置tsconfig.json

```json
{
	"compilerOptions":{
		// ...
    "target": "es6",
		"outDir": "./dist",
		"sourceMap": true,
    "watch": true,
	},
	"include": [
    "src"
  ],
  "exclude": [
    "node_modules"
  ]
}
```

以上配置中：

- target：这里不需要考虑其他浏览器兼容性问题，而且插件对es6支持的也非常好

- outDir：指定编译后的js文件存放位置
- sourceMap： 编译后，有助于我们js代码的调试
- watch：实时将ts编译为js
- include：要参与编译的ts代码目录，根据设置，我们就需要将插件的代码都放在src目录中
- exclude：排除编译的ts代码目录，我们使用的`npm package`就不需要参与ts编译了

我们暂且配置这么多，更详细的配置参数，大家可以参考`TypeScript`官方文档。



### 3.修改项目



