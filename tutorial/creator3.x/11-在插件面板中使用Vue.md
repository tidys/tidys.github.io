## CocosCreator3D插件教程(11)：在插件面板中使用Vue



到目前为止，我们已经知道，creator插件面板的编写，使用的是web前端技术。

在web领域`Vue`是最受欢迎的构建用户界面的框架之一。

creator2d插件中我们是可以直接使用`vue`，但是creator3d插件并没有提供。

那么在creator3d插件里面，我们如何使用Vue呢？

### 1. 下载vue

这里我们不使用`npm`的方式使用`vue`，我们直接下载`vue`的构建文件：

![](image-20201025134353609.png)

我下载的是`vue.js`，当然你也可以下载压缩版本`vue.min.js`。

下载后，放到我们的插件项目里面：

![](image-20201025134937501.png)

### 2.插件里面使用Vue

`vue`的本质还是一个js library，所以，我们直接require即可使用。

我们在`panel.js`中添加如下代码：

```javascript
exports.ready = function () {
    // ...
    let Vue = require('./vue');
}
```

那么我们该如何将Vue绑定到UI上呢？web老司机肯定对下面的代码非常熟悉：

`panel.html`

```html
<div id="app">
    <button @click="onBtnClick">
        按钮
    </button>
</div>
```

`panel.js`

```javascript
// ...
exports.$ = {
    app: '#app'
}
exports.ready = function () {
    let Vue = require('./vue');
    new Vue({
        el: this.$.app, // 注意这里，没有不能使用#app，原因是ShadowDOM
        data () {
            return {}
        },
        created () {
            console.log('created');
        },
        methods: {
            onBtnClick () {
                console.log('点击按钮')
            }
        }
    });
}
```

以上代码，和之前教程`给按钮绑定点击事件`，效果一样。

我们`重新加载`下插件，点击按钮，同样的会在编辑器`控制台`打印`点击按钮`的log。

### 3.Vue的数据绑定

数据绑定，让我们更专注逻辑开发，vue会自动根据数据，同步视图。

这里总结了一些常用的小知识点，web老司机可以直接忽略：

- 给元素绑定数据：`v-bind:`可以简写为`:`

  ```html
  <input v-bind:value="name"/>
  ```

  ```html
  <input :value="name"/>
  ```

  ```javascript
  new Vue({
    // ...
  	data(){
  		return {name:'hello'};
  	}
  })
  ```

  当然我们还可以给界面这样绑定文本数据

  ```html
  <div>{{name}}</div>
  ```

- 给元素绑定事件：`v-on:`可以简写为`@`

  ```html
  <button @click="onBtnClcik"></button>
  ```

  ```html
  <button v-on:click="onBtnClcik"></button>
  ```

  ```javascript
  new Vue({
  	// ...
  	methods:{
  		onBtnClcik(){
  			// todo 
  		}
  	}
  });
  ```

以上的小总结，足够让你编写一个功能复杂的小插件，`vue`还有更多简单易学的特性等待着你学习，更多vue的使用请参考vue官方文档。


![](res/wx-guan-zhu-20201026231652837.gif)