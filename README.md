# Fbsex.co API 文档
# HTTP API
## 基本信息
* 接口的base url: https://api.fbsex.co。
* 每种类型的接口（除基础信息，行情数据外）都需要做签名认证，不同类型的接口需要的权限不同，在申请API Key时确认好需要的权限。
* 调用接口时，除了接口本身所需的参数外，还需要传递accessKey(API accessKey)、timestamp(时间戳，请求发送时间)和signature(签名参数)。
* 服务器访问频率限制：100次 / 1分钟。
## 签名规则
* 首先将接口所需的参数加上accessKey和timestamp后进行ASCII排列。
* 然后使用secretKey将排列后的结果进行HMAC SHA256加密，得到signature结果。
* 将signature结果作为请求参数发送请求。
## 基础信息API
交易规范信息
```
GET /v1/exchange/info
```
返回结果：
```json
{
    "msg": "success",
    "code": 0,
    "data": {
        "coinTypes": [
            {
                "coinType": "EOS",
                "minWithdrawSingle": 1,
                "maxWithdrawSingle": 10000,
                "maxWithdrawOneDay": 50000,
                "withdrawFee": 0.1,
                "supportTrade": true,
                "supportDeposit": true,
                "supportWithdraw": true
            }
        ],
        "pairs": [
            {
                "pair": "ETH_USDT",
                "pricePrecision": 4,
                "amountPrecision": 4,
                "minTradeAmount": 0.001,
                "supportTrade": true
            }
        ]
    }
}
```
## 行情API
24小时价格变动情况
```
GET /v1/quote/ticker/24hr
```
请求参数：

| Name | Type | Required | Default | Description  |
| ---- | ---- | -------- | ------- | ------------ |
| pair | string | true | | |

返回结果：
```javascript
{
    "msg": "success",
    "code": 0,
    "data": {
        "pair": "BTC_USDT",
        "open": null, // 开盘价
        "close": null, // 收盘价
        "high": null, // 最高价
        "low": null, // 最低价
        "amount": null // 交易量
    }
}
```
最新价格
```
GET /v1/quote/ticker/price
```
请求参数：

| Name | Type | Required | Default | Description  |
| ---- | ---- | -------- | ------- | ------------ |
| pair | string | true | | |

返回结果：
```javascript
{
    "msg": "success",
    "code": 0,
    "data": {
        "pair": "BTC_USDT",
        "price": null
    }
}
```
深度数据
```
GET /v1/quote/depth
```
请求参数：

| Name | Type | Required | Default | Description  |
| ---- | ---- | -------- | ------- | ------------ |
| pair | string | true | | |
| size | integer | false | 50 | |
| precision | string | false | | |

返回结果：
```javascript
{
    "msg": "success",
    "code": 0,
    "data": {
        "asks": [],
        "bids": []
    }
}
```