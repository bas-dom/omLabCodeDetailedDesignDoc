# 页面管理模块

```
页面管理模块中分为dashboard页面和observer页面。
左侧显示页面列表，中间展示选中内容，点击右侧卡片组件可在dashboard页面中添加对应的卡片。
```

### Dashboard页面

#### 用户查看dashboard页面代码流程设计

1）登录进入页面管理，并根据接口`/omlab/getLayouts?pageId=<pageId>}`获取到对应的页面信息。并且通过`register`方法注册组件。

#### dashborad页面功能

1）dashboard页面中，点击右侧卡片组件通过一个`Widget`基类\(/pages/dashboard/components/widgets\)创建新的卡片组件。

2）生成空白卡片的右上角通过配置，根据`/tag/thingTree/detail`接口中得到项目点名并配置相关信息。然后点击保存，则通过`/omlab/saveLayouts`接口保存对应的数据。

3）点击卡片右上方删除按钮，，则通过`/omlab/removeLayouts`接口删除数据

4）在`GirdLayoutView.js`文件中将得到点位信息通过WebWorker中的`postMessage`方法传给`dashboard.worker.js`文件，`dashboard.worker.js`文件中通过监听message事件触发对应的处理函数，并通过接口`/get_realtimedata`每两秒将数据通过`postMessage`传回去。`handleWorkerData(e)`方法负责接收数据，并且将数据保存到全局store中的data数组中，并对比覆盖旧数据呈现在页面上，完成实时刷新数据操作.

### Observer页面

1\)在左侧的项目菜单中，用户点击每个项目后通过项目的`projectId` 根据借口`/omlab/getPages?projectId=${projectId}`获取对应Observer页面的数据。

