# 记账本

本项目使用[`fastapi-start`](https://github.com/ibbd-dev/fastapi-start)工具进行初始化，该工具的帮助可以使用命令：`fas --help`。

记账本项目

## 1. 功能介绍

### 类型管理模块

- 添加、删除、修改记账类型。

### 手动记账功能

- 输入`金额`、`类型`、`时间`、`备注`等信息，进行记账。
- 选择一项记账记录，可以进行编辑、删除操作。

### 自动记账功能

- 基于**无障碍功能**，获取支付结算界面的信息，（可能需要调用接口识别），自动填充`金额`、`时间`，识别`类型`，自动进行记账。
- `淘宝`、`京东`、`拼多多`等**电商平台**的订单导入自动化记账（需要通过订单列表或订单详情页截图，识别），自动填充`金额`、`时间`，识别`类型`，自动进行记账。
- 定时任务，设置`每天`、`每个工作日`、`每周`、`每月`、`每季度`的自动记账任务。

### 数据统计功能

- 月度统计
- 季度统计
- 年度统计
  - 类型统计
  - 金额范围统计

## 2. 安装与部署

部署前需要先复制配置文件：

```sh
cd app/
cp settings-example.py settings.py

# 根据实际情况修改配置文件
vim settings.py

# 启动
# FastAPI文档：https://fastapi.tiangolo.com/
uvicorn main:app --reload
```

## 3. fas工具使用说明

```sh
# 添加一个模块
# test是模块名称，可以设定
fas module new --name=test

# 添加模块之后，要使模块生效，需要手动在app/main.py文件中注册该路由
# prefix: 该参数定义路由的前缀，每个模块的路由前缀必须是唯一的
from test_module.router import router as test_router
app.include_router(test_router, prefix="/test", tags=["测试模块"])

# 在当前目录增加一个test.py文件
# python是文件类型，test是文件名
fas file python test
```

fas也支持一些内置模块：

```sh
# 支持的内置模块列表
fas module list

# 查看某内置模块的帮助文档
fas module help captcha
```

## 4. 附录

## 5. 项目相关人员

- AlphonseLuca
