# 用户登录

## 用户正常登录模块代码流程设计

* 用户登录模块通过 `LoginForm`组件（/pages/login/components）呈现页面。
* 通过`container`的中间容器`LoginContainer`\(/pages/login/containers\) 连接`redux`管理的数据  [参考 redux全局变量定义](/data-structure/reduxquan-ju-shu-ju-ding-yi.md)。
* 并且使用 `/login/<userId>` 接口请求数据，并使用 `doLogin` 方法封装。

## 用户登录后浏览过程中强制刷新时的代码逻辑

* 当刷新页面时根据上一次的 `token` 再一次刷新数据。
* /login/&lt;userId&gt; \(token放入cookie传回服务器验证\)

## 登录页面中的两个辅助功能

* `forgot password`会清除保存在`localStorage`中的密码
* `remenber me`可以将用户名和密码保存在`localStorage`中。



