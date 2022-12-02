
# 代收结果通知(le)

| 区域 | 通道（可点击切换）                                           |
| --- |-----------------------------------------------------|
| 巴西 | [iugu](代收结果通知.html)                                 |
| 印度 | [dd](代收结果通知(dd).html)&nbsp;&nbsp; [ab](代收结果通知(ab).html) |
| 菲律宾 | [cs](代收结果通知(cs).html)&nbsp;&nbsp; [le](代收结果通知(le).html) |

## 通知地址
`此地址为商户传入的回调地址`

## 通知方式
POST

## 通知头信息
Content-Type:application/json

## 通知参数

|字段名| 参数名 | 类型  | 必填  | 示例值 | 描述  |
|-----|-------------------------|-----|-----|-----|-----|
|响应状态|code|String|是|success| success/fail|
|请求信息|msg|String|是|ok|返回的请求信息|
|数据体| data|Object|是|-|以下为数据体属性|
|商户号| data>>merchant_code | String | 是 | 100012 | 商户后台分配的商户号(商户系统->账户信息获取) |
|商户订单号|data>>merchant_order_no|String|是|20210226165044236|商户系统商户订单号，要求32个字符内|
|金额| data>>merchant_order_no |	String|	是|10|单位(元)|
|实际金额| data>>reality_amount|Number|是|100|单位(元)|
|订单状态| data>>order_status|Number|是|2|参数说明|
|下单时间戳| data>>order_time|Number|是|1663402686|精确到秒|
|签名|data>>sign|String|是|9a55c3868b414cdc740068420a2d3q00|[签名算法](../rule/签名算法.html)|

## 响应示例

```json
{
    "code": "success",
    "data": {
        "merchant_code": "100012",
        "merchant_order_no": "20221201133641400317",
        "amount": "100.00",
        "reality_amount": "100.00",
        "order_status": 1,
        "pay_data": "https://xxx.xxx.com/",
        "order_no": "20221201133714239179",
        "order_time": 1669873037,
        "sign": "f14afb862100420050fc94a04611db47"
    },
    "msg": "ok"
}
```

## 通知应答

`收到回调信息后，返回字符串‘OK’，不返回回调接口会重试三次`

示例如下：

```
OK
```