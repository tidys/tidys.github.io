# 插件说明

众所周知，AppStore对应用有查重，当我们手里有一套源码时，为了能成功上架，我们需要对源码进行简单的修改，比如给prefab加点"垃圾"，一些空节点之类的内容。

类似这样的修改对游戏的副作用最小，如果项目prefab数量比较少，手动修改下也不是太麻烦，但是如果有1000多个prefab，这件事就有点考验耐心了。

该插件可以自动对prefab添加指定的prefab，支持批量随机添加、一键解放你的双手。

适配的creator版本2.4.5
# 使用细节
- 在db://assets/ignore/目录下的资源不会被插件检索
- 建议将noise prefab放在db://assets/noise/，插件会自动检索分类
- 因为切换prefab时，会先退出到scene，再打开新的pref，这是creator的实现机制，为了加快切换prefab的速度，建议scene尽可能简单，或者直接使用新建的空scene
- 添加等量的noise节点：从noise prefab中随机N个prefab，并添加这N个prefab，使得N个prefab的节点数量大于目标prefab节点的数量。

暂时只支持creator2.x

# 视频教程

... 待完善


