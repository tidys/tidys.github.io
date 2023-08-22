## CocosCreator3D插件教程(10)：使用UI框架快速编写UI

在任何技术领域，编写UI界面，始终是一件比较繁琐的事情，不过creator3d插件也内置了大量内部UI组件，可以方便我们快速编写UI。

### 使用插件内置UI组件

我们可以在菜单`开发者`/`UI组件`中，查看现有的内置组件：

![](image-20201024234056906.png)

面板中展示了很多已有的UI组件，我们都可以在插件面板中直接使用，无需引入，示例中也给出了使用代码，非常方便，具体的UI组件细节，可以在文档中查阅。

![](image-20201024234258489.png)

使用插件内置UI组件：

#### 优点：

- UI风格和整个编辑器非常协调。
- `ui-asset`， `ui-node`，`ui-component` 等组件，和编辑器器功能联动，算是插件UI特有的功能点。

```html
  <ui-asset id="asset" droppable="cc.ImageAsset"></ui-asset>
  <ui-node></ui-node>
```

```js
exports.$ = {asset:'#asset'}
exports.ready = function(){
	this.$.asset.value = "asset-uuid";
}
```

![](image-20201025125336645.png)

#### 缺点：

- 相关使用教程，除了文档，少之又少。
- 如果编辑器UI风格发生调整，插件也会受影响。



当然，你也可以使用其他第三方web-ui框架，后续我会单独来一篇教程讲解如何引入，目前不在本教程范围内。


![](res/wx-guan-zhu-20201026231652837.gif)
