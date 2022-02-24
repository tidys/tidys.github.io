# sail bundle指南
bundle的代码编写完全遵守creator的代码规范


sail bundle目前分为2类

## 对象：object
定义对象

```ts
import Prop from './prop';

const gameObject = {
    type: 'object',
    info: {
        name: '文本',
        icon: 'icon-text',
        desc: '在屏幕中显示一些文本',
        group: '常规',
    },
    
    async create(bundle: cc.AssetManager.Bundle) {
        let node = new cc.Node('sail-label');
        node.color = cc.Color.BLACK;
        const label = node.addComponent(cc.Label);
        label.string = 'test-label';
        return node;
    },
    component: Prop,
};
export default gameObject;

```
```ts
const { ccclass, property } = cc._decorator;

@ccclass
export default class Prop extends cc.Component {
    
    @property({ displayName: '透明度' })
    
    get opacity() {
        return this.node.opacity;
    }
    
    set opacity(v) {
        this.node.opacity = v;
    }
    
    @property({ displayName: '角度' })
    get angle() {
        return this.node.angle;
    }
    
    set angle(v) {
        this.node.angle = v;
    }
    
    start() {
    
    }
}

```


## 行为：behavior

定义行为
```ts
import comp from './fadeBehavior'

const gameBehavior = {
    type: 'object/behavior',
    info: {
        name: '淡入淡出',
        icon: 'icon-fade',
        desc: '在一段时间内逐渐改变对象的不透明度，适用于让对象逐渐出现消失',
        group: '常规',
    },
    component: comp,
}
export default gameBehavior;

```

行为属性
```ts

const { ccclass, property } = cc._decorator;

@ccclass
export default class FadeBehavior extends cc.Component {

    @property()
    fadeInTime = 0;

    @property({ tooltip: '启用后立即执行淡入淡出，或者等待开始的动作触发后执行', displayName: '启用' })
    fadeEnabled = true;

    start() {

    }
}


```

更多细节有待完善...