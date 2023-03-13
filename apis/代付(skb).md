# 代付

当前通道：**BR002**

| 区域 | 通道（可点击切换）|
| --- |-----------------------------------------------------|
| 巴西 | [BR001](代付.html)&nbsp;&nbsp; [BR002](代付(skb).html)|
| 印度 | [IN201](代付(201).html)&nbsp;&nbsp; [IN202](代付(202).html)&nbsp;&nbsp; [IN203](代付(203).html)&nbsp;&nbsp; [IN204](代付(204).html)&nbsp;&nbsp; [IN205](代付(205).html)&nbsp;&nbsp; [IN206](代付(206).html)&nbsp;&nbsp; [IN207](代付(207).html)|
| 菲律宾 | [PH001](代付(cs).html)&nbsp;&nbsp; [PH002](代付(lf).html) &nbsp;&nbsp; [PH003](代付(rb).html) &nbsp;&nbsp; [PH004](代付(lft1).html)&nbsp;&nbsp; [PH005](代付(PH005).html)&nbsp;&nbsp; [PH006](代付(PH006).html)|
| 墨西哥 | [MX001](代付(sp).html)|
| 越南 | [VN002](代付(ly).html)|
| 印度尼西亚 | [ID001](代付(wa).html)|

## 请求地址
https://[[域名]](../help/区域域名.html)/i/transfer/create

## 请求方式
POST

## 请求头
Content-Type:application/json

## 请求参数

| 字段名 | 参数名 | 类型 | 必填 | 示例 | 描述 |
|-----|-----|-----|-----|-----|-----|
|商户号|merchant_code|String|是|100012|商户后台分配的商户号(商户系统->账户信息获取) |
|商户订单号|merchant_order_no|String|是|456545645487|商户系统商户订单号，要求32个字符内 |
|支付通道编码|pay_type|String|是|skb|示例中的固定值|
|币种|currency|String|是|BRL|雷亚尔|
|电话号码|mobile|String|是|254743123003|收款人联系方式|
|姓名|name|String|是|Jack|收款人姓名|
|金额|amount|String|是|100.00|单位(元)，保留两位小数|
|回调地址|notify_url|String|是|https://www.xxx.com/notify|付款成功后支付系统通过该地址通知支付结果|
|下单时间戳|order_time|Number|是|1663402686|精确到秒|
|账户类型|account_type|String|是|1 - CPF，2 - CNPJ，3 - EMAIL，4 - PHONE，5 - EVP | 1-5分别对应五种账户类型|
|账户号码|account_number|String|是|56466655|根据account_type填写相应账户类型的号码；Pix号(支持格式: 用户的邮箱/带国际区号手机号(例如+55XXXXXXX)/CPF/CNPJ/EVP|
|签名|sign|String|是|9a55c3868b414cdc740068420a2d3q00|[签名算法](../rule/签名算法.html)|

## 请求示例

```json
{
  "merchant_code": "100012",
  "merchant_order_no": "20221202135223988596",
  "currency": "BRL",
  "mobile": "6456312891",
  "name": "test",
  "amount": 100,
  "notify_url": "https://www.xxx.com/notify",
  "order_time": 1669960343,
  "account_type": "1",
  "account_number": "4554654",
  "sign": "7d83d736a54f1393eae78bdbc8a3c57e"
}
```

## 返回结果

|字段名|参数名|类型|必填|示例|描述|
|-----|-------------------------|-----|-----|-----|-----|
|响应状态|code|String|是|success|success/fail/error|
|请求信息|msg|String|是|ok|返回的请求信息|
|数据体|data|Object|是|-|以下为数据体属性|
|平台订单号|data>>order_no|String|是|20210226165044236|系统生成的平台订单号|
|商户订单号|data>>merchant_order_no|String|是|10226165044236|商户系统商户订单号，要求32个字符内|
|商户号|data>>merchant_code|String|是|GKggRpDN6|商户后台分配的商户号(商户系统->账户信息获取)|
|金额|data>>amount|String|是|100.00|单位(元)，保留两位小数|
|实际金额|data>>reality_amount|String|是|100.00|单位(元)，保留两位小数|
|订单状态|data>>order_status|Number|是|2|[参数说明](../help/参数说明.html#订单状态)|
|下单时间戳|data>>order_time|Number|是|1663402686|精确到秒|
|签名|data>>sign|String|是|9a55c3868b414cdc740068420a2d3q00|[签名算法](../rule/签名算法.html)|

## 响应示例

```json
{
  "code": "success",
  "data": {
    "merchant_code": "100012",
    "merchant_order_no": "20221202135223988596",
    "amount": 100.00,
    "reality_amount": 100.00,
    "order_status": 0,
    "order_no": "20221202135231869872",
    "order_time": 1669960351,
    "sign": "55be7fc85c1a2cb4be3031303494cd5d"
  },
  "msg": "ok"
}
```
