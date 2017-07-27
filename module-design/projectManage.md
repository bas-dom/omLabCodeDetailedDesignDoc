# 项目管理

## 项目管理流程设计

* 项目管理由`ProjectSelectView`和`ProjectManageView`两个组件分为**项目导航**和**用户权限管理**页面。
* 项目导航通过`/login/<userId>`接口的项目数据，呈现相对应的项目。
* 项目权限管理需要点击项目导航页面中每个项目的用户图标并通过`/admin/loadProjectPermission`接口数据呈现视图。

## 项目导航页面的功能和代码逻辑

* 通过`/project/create`接口创建项目。
* 搜索项目功能使用正则匹配`projectName`和`projectId`筛选redux中保存的项目数据并存储在自己组件内的`state`中。
* 通过`/admin/setFavoriteProject`接口记住项目的选择。下次登录后通过判断项目数据的`isFavorite`属性是否为当前项目的id来确认默认进入的项目。并跳过项目导航。
* 通过`/admin/deleteProject`接口删除项目。
* 在点击进入一个项目后，浏览器会通过localStorage缓存你点击项目的次数。并且根据点击的次数自动的排序项目导航的顺序。

## 用户权限管理页面

* 进入用户权限管理页面之后，对比当前项目的id和`/admin/loadProjectPermission`接口里**projectList**数据中每一项的id 并将当前的角色分组呈现。
* 通过`/admin/addProjectRole`添加项目角色分组。`/admin/deleteProjectRole`删除项目角色分组
* 点击每一个分组时通过分组id获取到分组下的**users**用户列表。
* 添加分组用户的操作，使用了`react-dnd`插件。使用`DragDropContextProvider`容器包裹，生成一个可以接受拖拽组件的容器。将`UserListView`组件通过`DragSource`方法包裹，写入一个回调函数。监听被`connectDtagSource`包裹的组件在拖拽过程中的数据变化。并通过接口`/admin/addRoleUser`完成用户的添加。
* 删除用户通过接口`/admin/deleteRoleUser`
* 查询功能通过正则匹配用户的名称和邮箱完成搜索 



