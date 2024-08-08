## CocosCreator3D插件教程(6)：给插件添加UI面板

有时我们的插件需要UI面板，进行一些简单的人机交互，使插件的使用更加简单、方便。

那么在creator3D插件中，如何添加UI面板呢？

### 1.配置插件UI面板

如下所示，修改`package.json`文件，插件的所有面板，都是在`panels`字段定义：

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
}
```

- `type`：定义了插件面板类型，dockable类型就是可悬浮停靠，creator3d编辑器内置的面板就是这种类型。
- `main`：UI面板的逻辑入口。

### 2.给UI面板添加打开入口

在第一步中，已经定义了一个UI面板，我们需要提供一个打开面板的入口，还记得之前的插件菜单么？

- 在`package.json`增加一个`打开面板`菜单：

```json
{
  // ...
  "main": "./main.js",
	"contributions": {
		"menu": [
      // ...
      {
        "path": "插件",
        "label": "打开面板",
        "message": "openPanel"
      }
    ],
    "messages":{
      // ...
      "openPanel": {
        "methods": [
          "openPanel"
        ]
      }
    }
	}
}
```

- 在`main.js`中实现`openPanel`消息，通过调用`Editor.Panel.open("插件名字.面板名字")`接口来打开面板：

```javascript
exports.methods={
		// ...
	  openPanel () {
        Editor.Panel.open('hello-world');
    }
}
```

>Editor.Panel.open('hello-world')，默认会打开配置的"default"面板。
>
>如果要打开配置的其他面板，比如配置了"game"面板，需要Editor.Panel.open("hello-world.game")来打开"game"面板。

### 3. 编辑器中测试下

回到编辑器中，和之前一样，我们需要在`扩展面板`中`重启`并`启用`下插件(必要情况下，可能得重启下编辑器)。

我们点击菜单栏的`插件`/`打开面板`

![](image-20201024213714405.png)

编辑器就会打开一个新的面板

![](image-20201024213830059.png)

我们也可以将该UI面板拖拽到编辑器主窗口中：

![](image-20201024214344871.png)

> 请注意拖拽部位，拖拽的不是窗口的标题栏，而是窗口内的tap栏，也就是"UI面板"的部位

现在我们插件的UI面板中还没有任何UI元素，接下来，就让我们给界面添加一些按钮、文本吧

![](res/wx-guan-zhu-20201026231652837.gif)