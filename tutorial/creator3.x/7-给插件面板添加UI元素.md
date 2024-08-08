## CocosCreator3D插件教程(7)：给插件面板添加UI元素

在上节教程中，我们给插件添加了UI面板，一般UI都会有按钮、输入框，那么我们如何给面板添加一些元素呢？

我们再熟悉下`package.json`里面的`panels`：

```json
{
	// ...
	"panels": {
    "default": {
      "title": "UI面板",
      "type": "dockable",
      "main": "./panel.js"
    }
}
```

- `main`指向的`panel.js`，就是插件面板的入口逻辑，所有的面板逻辑也都需要写在这里。

### 1.编写插件面板逻辑，并添加一个按钮

我们在插件目录新建一个`panel.js`

![](image-20201024215713213.png)

并在`panel.js`中添加以下代码：

```javascript
exports.template = `<button>按钮</button>`;
```

有没有很熟悉的感觉，没错，这就是HTML，你可以在里面使用html的任何标签！

### 2.刷新插件面板，查看按钮效果

代码编写完毕，我们该如何刷新面板呢？

这里我们就不需要在`扩展管理器`中`重启`插件，

只需要激活插件面板窗口，然后`重新加载`下就能看到刚才添加的按钮，如下图所示：

![](image-20201024220455302.png)

> 重新加载 时，请注意你当前激活的窗口。

### 3.美化UI界面

添加的按钮似乎有点丑，我们希望他更加个性化，这里就需要使用到了`css`

```javascript
exports.template = `<button class="btn">按钮</button>`;
exports.style= `
.btn{
    width:100px;
    height:100px;
}`;

```

熟悉web前端的小伙伴对这个应该不会陌生，我们还可以这么写，都是同样的效果：

```javascript
exports.template = `
<button style="width: 100px;height: 100px;">
    按钮
</button>`;

```

我们再刷新下界面，就会看到按钮已经发生了变化：

![](image-20201024221939171.png)

这里我就抛砖引玉，不再赘述`输入框`怎么添加了，对web前端不熟悉的小伙伴，咱就花点时间学习学习。

![](res/wx-guan-zhu-20201026231652837.gif)