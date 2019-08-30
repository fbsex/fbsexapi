# Fbsex.co API 文档
# HTTP API
## 基本信息
* 接口的base url: https://api.fbsex.co。
* 每种类型的接口（除基础信息，行情数据外）都需要做签名认证，不同类型的接口需要的权限不同，在申请API Key时确认好需要的权限。
* 调用接口时，除了接口本身所需的参数外，还需要传递accessKey(API accessKey)、timestamp(时间戳，请求发送时间)和signature(签名参数)。
* 服务器访问频率限制：100次 / 1分钟。