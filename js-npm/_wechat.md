## wechat-jssdk

[npm](https://www.npmjs.com/package/wechat-jssdk)

可用于微信开发的 sdk，服务端和客户端均可

针对客户端的简单封装代码：

```js
import WechatJSSDK from 'wechat-jssdk';
import http from "./http";

async function jssdkInit(jsApiList = []) {
  const config = await http.post('wechat/jssdk', {
    url: window.location.href,
    jsApiList: jsApiList,
  })
  const wechat = new WechatJSSDK(config)
  await wechat.initialize()
  return wechat
}

export default {
  async initShare(shareConfig) {
    // https://developers.weixin.qq.com/doc/offiaccount/OA_Web_Apps/JS-SDK.html#10
    const wechat = await jssdkInit(['updateAppMessageShareData', 'updateTimelineShareData'])
    wechat.callWechatApi('updateAppMessageShareData', shareConfig)
    wechat.callWechatApi('updateTimelineShareData', shareConfig)
  }
}
```