# 页面管理模块

页面管理模块中分为**dashboard页面**和**observer页面**。左侧显示页面列表，中间展示选中内容，点击右侧卡片组件可在dashboard页面中添加对应的卡片。

###1、Dashboard

dashboard页面中，通过一个`Widget`基类，用户根据`/omlab/saveLayouts`接口创建新的组件，后每次登陆会通过`register`方法注册对应的组件。并且注册的组件都会添加到`widgets`这个数组中。然后通过在`/tag/thingTree/detail`接口中得到项目点名并配置相关信息，最后完成一个完整的组件。  
在`GirdLayoutView.js`文件中将得到点位信息通过WebWorker中的`postMessage`方法交给  
`dashboard.worker.js`文件中，`dashboard.worker.js`文件中通过监听message事件触发对应的处理函数，并通过接口`/get_realtimedata`实时的将数据通过`postMessage`传回去。`handleWorkerData(e)`方法负责接收数据，并且将数据保存到全局store中的data数组中，并对比覆盖旧数据呈现在页面上，完成实时刷新数据操作.



###2、Observer

在左侧的项目菜单中，用户点击每个项目后通过项目的`projectId` 根据借口`/omlab/getPages?projectId=${projectId}`获取对应页面的数据。

