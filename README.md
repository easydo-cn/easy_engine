# edo_engine

## 使用场景
*  需要特殊的软件包：特别是用在CI/CD自动化场景
*  混合云架构：无法直接访问内网的服务
*  需要突破站点安全沙箱

## 工作原理
1. 从站点下载脚本
    * 分版本缓存编译之后的脚本
    * 自动刷新旧版本
2. 脚本安全检查
    * 可以开启安全检查开关
    * 一旦开启，需要到站点验证脚本签名合法性
3. 准备附加脚本全局变量
4. 运行脚本，返回结果

## 安装
pip安装 / 源码安装
```
pip install edo_engine / python setup.py install
```

## 创建远端引擎
创建远端引擎调用脚本
```
from edo_engine import RemoteScriptingEngine
# 创建引擎
rse = RemoteScriptingEngine(wo_client)
# 调用脚本
rse.call('xxx')
```

## 远端脚本开发
1. 创建云函数，用途选择为远端脚本
2. 开发远端脚本，远端脚本可调用所有安装的python模块
3. 调用另外的远端脚本，可调用内置的call 方法
