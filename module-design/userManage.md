# 用户管理模块代码流程设计

原始数据模块通过 `UserManageView`组件（/pages/userManage/components） 呈现页面。

通过 `container` 的中间容器 `UserManageContainer` \(/pages/userManage/containers\) 连接`redux`管理的数据  参考 [redux全局变量定义](/data-structure/reduxquan-ju-shu-ju-ding-yi.md)。

并且使用 `/admin/loadUsersTree` 接口请求用户列表，使用`getUserList` 方法封装。

# 用户设置功能的代码逻辑

点击用户头像后，通过`showModal`方法（/pages/userManage/moduls/UserManageModule），会展示出`UserSettingView`模态框。

使用`showUsersSettingModal`方法（/pages/userManage/moduls/UserManageModule），通过`/admin/loadUsersSetting` 接口请求到该用户的所有详细信息。

使用`getRecords` 方法（/pages/userManage/moduls/UserManageModule），通过`/admin/getRecords` 接口请求该用户的操作记录。

使用`getUserProjRecords` 方法（/pages/userManage/moduls/UserManageModule），通过`/admin/userProjRecords`接口请求该用户被分配到的项目。

使用`updataUsersSetting` 方法（/pages/userManage/moduls/UserManageModule），通过`/admin/updateUsersSetting`接口将修改后的数据发送给后台。

# 创建新用户的代码逻辑

点击新建按钮后，通过`showModal`方法（/pages/userManage/moduls/UserManageModule），会展示出`UsersInvitedModalView`模态框。

使用`inviteUsers` 方法（/pages/userManage/moduls/UserManageModule），通过`/admin/inviteUsers` 接口将修改后的数据发送给后台。

