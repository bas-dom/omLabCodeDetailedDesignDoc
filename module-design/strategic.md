# 策略管理模块

```
文件位置：/pages/strategic
```

## 策略页面代码流程设计

* 策略管理页面通过接口`/cloudDiagnosis/getCustomDiagnosis/tree`和`/v2/diagnosis/get/moduleStatus/173`获取到左侧树形结构和右侧诊断数据。将数据放在redux中管理。

* 使用`StrategicManageContainer`和`TreeContainer`\(/pages/strategic/containers\)的容器组件绑定redux中的数据渲染component

## 策略页面基本功能

* 展开一个树形节点都会使用`/cloudDiagnosis/getCustomDiagnosis/tree`接口异步加载对应节点下的数据。

* 点击每个节点，右侧的板块展示当前节点的诊断曲线图。

* 进入修改模块后可以修改诊断脚本。并且通过`/diagnosis/onlinetest`接口进行在线测试。左上角可以根据`/cloudDiagnosis/saveCustomDiagnosis`和`/cloudDiagnosis/removeCustomDiagnosis`接口完成数据节点的增加和删除。



