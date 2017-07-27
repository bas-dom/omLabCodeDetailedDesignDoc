# 数据管理模块

```
数据管理模块分为原始数据和云数据
```

# 原始数据模块代码流程设计

原始数据模块通过 `OriginDataView`组件以及`TableView` 表格模块（/pages/originData/componets） 呈现页面。

通过 container 的中间容器 `OriginDataContainer` 以及 `TableContainer` \(/pages/originData/containers\) 连接`redux`管理的数据  参考 [redux全局变量定义](/data-structure/reduxquan-ju-shu-ju-ding-yi.md)。

并且使用 `/admin/dataPointManager/search` 接口请求原始数据，使用`reloadTable` 方法封装。

# 原始数据的搜索功能代码逻辑

选择搜索类型，在输入框里输入的内容会放到`condition.searchText`变量里。

然后传给`reloadTable` 方法中的 `test`变量，使用`/admin/dataPointManager/search` 接口即可请求到对应的数据。

# 原始数据的历史趋势图代码逻辑

在`OriginDataView`组件中加入 `HistoryModal` 组件，通过`showHistoryModal`方法（/pages/originData/moduls/OriginDataModual）将选择的点名传给`HistoryModal` 组件并使其显示出来。

# 云数据模块代码流程设计

云数据模块通过 `CloudDataView`组件、`TableView` 表格组件（/pages/cloudData/componets） 呈现页面。

通过 `container` 的中间容器 `CloudDataContainer` 以及 `TableContainer` \(/pages/cloudData/containers\) 连接`redux`管理的数据  参考 [redux全局变量定义](/data-structure/reduxquan-ju-shu-ju-ding-yi.md)。

并且使用 `/point_tool/getCloudPointTable` 接口请求云数据，使用`reloadTable` 方法封装。

# 云数据的模糊搜索功能代码逻辑

选择搜索类型，在输入框里输入的内容会放到`baseState.condition.searchText`变量里。

然后传给`reloadTable` 方法中的 `searchText`变量，使用`/point_tool/getCloudPointTable` 接口即可请求到对应的数据。

# 云数据的计算点及虚拟点代码逻辑

当点击新建计算点或虚拟点时，通过`showModal` 方法展示出`CalcPointModalView` 计算点模态框、`VirtalPointModalView`虚拟点模态框（/pages/cloudData/componets）。

输入对应数据后，通过 `addCalcPoint` 、`addVirtualPoint`方法（/pages/cloudData/moduls/CloudDataModual\)将内容传给`/point_tool/addCloudPoint` 接口。

修改数据，使用`createEditPointFunction`方法，通过`/point_tool/editCloudPoint`接口将修改后的数据传给后台。

# 云数据的历史趋势图代码逻辑

在`OriginDataView`组件中加入 `HistoryModal` 组件，通过`showHistoryModal`方法（/pages/originData/moduls/OriginDataModual）将选择的点名传给`HistoryModal` 组件并使其显示出来。

