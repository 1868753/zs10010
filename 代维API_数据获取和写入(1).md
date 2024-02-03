

# **订单详情页 API Documentation**

---

# 标准化说明：
- 页面/JSON/TEXT 编码需要统一为UTF-8或GBK
  - 如参数值为中文的，需要进行URI编码情况时，需要对应编码
  - 如 你好，编码GBK（UTF-8），那么返回值也应当时UTF-8的URI编码
  - 并且非GBK编码参数的其他文本返回，也是UTF-8(TEXT)
---
# 一、订单状态操作 API

### 订单操作
- **API Endpoint:** [https://xuhao.lddzf.com/api/allen/daiwei/dingdancaozuo.php](https://xuhao.lddzf.com/api/allen/daiwei/dingdancaozuo.php)
- **HTTP Method:** POST

#### 参数：说明
- **必须参数:**
  - `order_code`: 订单号
  - `code`: 指令
    - 1: 回单审核
    - 2: 撤销审核<撤销回单审核
    - 3: 撤销回单
    - 4: 发起整改
    - 5: 倒装单审核
    - 6: 移至倒装单

### 请求示例
至少兼容 HTTPREQUEST 1.2以上
POST https://xuhao.lddzf.com/api/allen/daiwei/dingdancaozuo.php

DATA order_code=KH_N20240203151231&code=1

### 返回示例
- **后端处理成功:**
  ```json
  {
    "status": "success",
    "message": "订单状态修改成功",
    "order_code": "KH_N20240203151231"
  }
- **后端处理失败:**
    ```json
    {
    "status": "success",
    "message": "订单状态修改失败，XXX原因之类的",
    "order_code": "KH_N20240203151231"
  }

---

## 二、订单数据修改 API

### 订单修改
- **API Endpoint:** [https://xuhao.lddzf.com/api/allen/daiwei/change.php](https://xuhao.lddzf.com/api/allen/daiwei/change.php)
- **HTTP Method:** POST

#### 参数：说明
- **必须参数:**
  - `order_code`: 订单号
  - `code`: 1
- **可选参数:**
  - 参数(?)(动态多参数)
    - 备注：
      - 如：身份证=440123456、报装电话=123456789
      - 仅修改该订单(KH_N20240203151231)的两个参数内容，
      - 这些参数是可提供多个或一个的，这两个只是示例参数。

#### 返回示例
- **后端处理成功:**
  ```json
  {
    "status": "success",
    "message": "订单信息修改成功",
    "order_code": "KH_N20240203151231"
  }
  
- **后端处理失败:**
    ```json
    {
    "status": "success",
    "message": "订单状态修改失败，XXX原因之类的",
    "order_code": "KH_N20240203151231"
  }
