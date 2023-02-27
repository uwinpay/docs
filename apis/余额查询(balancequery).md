---
sort: 7
show: 1
---

# 余额查询

## 请求地址
https://[[域名]](../help/区域域名.html)/i/balance/info

## 请求方式
POST

## 请求头
Content-Type:application/json

## 请求参数

| 字段名 | 参数名 | 类型  | 必填  | 示例值 | 描述  |
|--|-----|-----|-----|-----|-----|
|商户号 |	merchant_code	|String	|是	|100012	|商户后台分配的商户号(商户系统->账户信息获取)|
|签名|	sign|	String|	是|	9a55c3868b414cdc740068420a2d3q00|[签名算法](../rule/签名算法.html)|

## 请求示例

```json
{
  "merchant_code": 100012,
  "sign": "f4d528b624fc455601d9bc0949ea5e5b"
}
```

## 返回结果

|字段名| 参数名 | 类型  | 必填  | 示例值 | 描述  |
|-----|-------------------------|-----|-----|-----|-----|
|响应状态|code|String|是|success| success/fail/error|
|请求信息|msg|String|是|ok|返回的请求信息|
|数据体| data|Object|是|-|以下为数据体属性|
|可提现余额| data>>available_balance | String | 是 |
|待结算金额|data>>unsettled_balance|String|是|
|今日代收成功金额|data>>payment_amount|String|是|
|今日代收成功单数| data>>payment_succ_total|String|是|
|今日代收总单数| data>>payment_total|String|是|
|今日代收成功率| data>>payment_succ_rate|String|是|

|今日代付成功金额| data>>transfer_amount|String|是|
|今日代付成功单数|data>>transfer_succ_total|String|是|
|今日代付总单数|data>>transfer_total|String|是|
|今日代付成功率|data>>transfer_succ_rate|String|是|
|代付中单数|data>>transfering_total|String|是|
|代付中金额|data>>transfering_amount|String|是|

## 响应示例

```json
{
    "code": "success",
    "data": {
        "payment_amount": 1600,
        "payment_succ_total": 8,
        "payment_total": 39,
        "payment_succ_rate": "20.51",
        "transfer_amount": 0,
        "transfer_succ_total": 0,
        "transfer_total": 0,
        "transfer_succ_rate": 0,
        "transfering_total": 0,
        "transfering_amount": 0,
        "available_balance": "35801.1550",
        "unsettled_balance": "0.0000"
    },
    "msg": "ok"
}
```
