# 用户登录模块

用户登录模块通过 `LoginForm`组件呈现页面。通过`container`的中间容器连接`redux`管理的数据。并且使用 `/login/2` 接口请求数据，并使用 `doLogin` 方法封装。当刷新页面时根据上一次的 **`token`** 再一次刷新数据。登录页面中有两个功能：`forgot password`会清除保存在`localStorage`中的密码 `remenber me`可以将用户名和密码保存在`localStorage`中。

