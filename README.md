## Wandoujia CampaignSDK 使用文档



### 安装：

```bower install campaignSDK```

### 使用
1. 在项目中引入此 campaignSDK.js：
```
<script src="/components/campaignSDK/campaignSDK.js">
<!-- 下面是你自己的 js -->
<script src="your-js-file.js">
```

2. 调用 campaignSDK 中的各方法：
```
/*
 * 示例：
 */

// P4 中弹出提示
if (campaignTools.UA.inWDJ) {
    campaignTools.toast('success!');    
}

// 订阅某订阅源账号
campaignTools.subscribe('123456', function (resp) {
    console.log('订阅成功');
});

// 微信 webview 中启动微信右上角的分享给好友和朋友圈功能
if (campaignTools.UA.inWechat) {
    var shareTimelineObject = {
        title: '这是分享给好友的标题',
        desc: '这是分享给好友的简介',
        link: '这是分享给好友的链接',
        imgUrl: 'http://www.wandoujia.com/xxx.jpg', //配图
        successCallback: function () {
            alert('分享给微信好友成功');
        }
    };
    var shareFriendObject = {
        title: '这是分享到朋友圈标题',
        link: '这是分享到朋友圈的链接',
        imgUrl: 'http://www.wandoujia.com/xxx.jpg', //配图
        successCallback: function () {
            alert('分享到微信朋友圈成功');
        }
    };

    campaignTools.wechatWebviewShareSetup(shareTimelineObject, shareFriendObject);
}
```


### 详细文档:

##### 1. campaignTools.UA
> 用来判断当前设备，返回的是一个对象：

```
{
    inWdj:        true || false, // 是不是在豌豆荚 webview 中
    inWechat:     true || false, // 是不是在微信 webview 中
    inIos:        true || false, // 是不是在 iOS 中
    inAndroid:    true || false, // 是不是在 Android 中
    inWp:         true || false, // 是不是在 windows phone 中
    inSymbian:    true || false, // 是不是在 symbian os 中
    inMac:        true || false, // 是不是在 mac os 中
    inWindows:    true || false, // 是不是在 win os 中
    inIphone:     true || false, // 是不是在 iPhone 中
    inIpad:       true || false, // 是不是在 iPad 中
    inMobile:     true || false, // 是不是在手机中
    inPC:         true || false, // 是不是在电脑中
    isRetina:     true || false  // 是不是在高清屏中
}
```

##### 2. campaignTools.runSystemShare(title, content)
> 调起安卓系统级别分享。

**参数说明：**
* title: 分享标题
* content: 分享的内容，仅限文字

##### 3. campaignTools.runAppShare(title, content, imgUrl, shareUrl, appType)
> 调起应用级别分享。

**参数说明：**
* title: 分享标题
* content: 分享内容
* imgUrl: 享图片的地址(不建议过大)
* shareUrl: 分享 URL
* appType: 'SINA_WEIBO' || 'WECHAT' || 'WECHAT_TIMELINE'

##### 4. campaignTools.openInBrowser(url)
> 在 Androdi 外部浏览器中打开链接。

**参数说明：**
* url: 要打开的网址

##### 5. campaignTools.getUDID()
> 获取用户设备的 UDID，字符串。

##### 6. campaignTools.getUID()
> 获取已登录的豌豆荚用户 UID，字符串。

##### 7. campaignTools.getAvatar()
> 获取已登录的豌豆荚用户头像的 url 地址，字符串。

##### 8. campaignTools.getUserEmail()
> 获取已登录的豌豆荚用户头像的 url 地址，字符串。

##### 9. campaignTools.getNickName()
> 获取已登录的豌豆荚用户昵称的字符串。

##### 10. campaignTools.getUserAuth()
> 获取已登录的豌豆荚用户 auth 的字符串。

##### 11. campaignTools.isLogin()
> 判断 P4 中当前用户是否已登录
> 
> 返回 boolean: true || false 
> 
> 版本 >= 4.18 可用 

##### 11. campaignTools.getPhoneNumber()
> 获取用户手机号码, 字符串。 +8618518281xxx

##### 12. campaignTools.openUserDetail(uid)
> 调起 P4 内的用户个人主页

**参数说明：**
* uid: 用户的 UID，字符串，如 '4383987'。

##### 13. campaignTools.isInstalled(packageName)
> 判断某应用是否已经安装
> 
> 返回 boolean: true || false

**参数说明：**
* packageName: 应用包名，字符串。

##### 14. campaignTools.isUpgradable(packageName)
> 判断某应用是否可升级
> 
> 返回 boolean: true || false

**参数说明：**
* packageName: 应用包名，字符串。

##### 15. campaignTools.getAppState(packageName)
> 获取应用状态
> 
> 返回 int: 

```
0 -- Waiting install 等待安装
1 -- Installed 已经安装
2 -- Not exist 不存在
3 -- Uninstalling 正在卸载
4 -- Patching ? 未知
```

**参数说明：**
* packageName: 应用包名，字符串。

##### 16. campaignTools.getAppVersionCode(packageName)
> 获取某应用版本号
> 
> 返回字符串类型的版本号，如 '100'

**参数说明：**
* packageName: 应用包名，字符串。

##### 17. campaignTools.getAppVersionName(packageName)
> 获取某应用的版本名称
> 
> 返回字符串类型的版本名称，如 '5.2.8'

**参数说明：**
* packageName: 应用包名，字符串。


##### 18. campaignTools.openApp(packageName)

##### 19. campaignTools.openAppDetail(packageName)

##### 20. campaignTools.openAppDetailWithoutAward(packageName)

##### 21. campaignTools.sendIntent(serializedIntent)

##### 22. campaignTools.openVideoDetail(id)

##### 23. campaignTools.openEbookDetail(id)

##### 24. campaignTools.searchWords(str)

##### 25. campaignTools.openSubscribeDetail(id, type)

##### 26. campaignTools.openSubscribePublisher(uid)

##### 27. campaignTools.openSubscribeSubset(id)

##### 28. campaignTools.loginAccount()

##### 29. campaignTools.choseLoginAccount()

##### 30. campaignTools.installApp(app, callback)

##### 31. campaignTools.reload()

##### 32. campaignTools.setOrientation(isVertical)

##### 33. campaignTools.download(url, title, type)

##### 34. campaignTools.closeWebView()

##### 35. campaignTools.openNewWebView(url, title, showActionBar, isPortrait, isFullScreen)

##### 36. campaignTools.getVersionCode()

##### 37. campaignTools.getVersionName()

##### 38. campaignTools.getFullVersionName()

##### 39. campaignTools.getIMEI()

##### 40. campaignTools.getBrand()

##### 41. campaignTools.getNetworkType()

##### 42. campaignTools.getLocaleLanguage()

##### 43. campaignTools.getLocaleCountry()

##### 44. campaignTools.getSDKVersion()

##### 45. campaignTools.setClipboardText(string)

##### 46. campaignTools.toast(string)




##### 47. campaignTools.constant

##### 48. campaignTools.api

##### 49. campaignTools.getFeedListData(id, callback)

##### 50. campaignTools.getFeedItemsData(id, callback)

##### 51. campaignTools.getSubscribeStatus(uid, callback)

##### 52. campaignTools.subscribe(uid, callback)

##### 53. campaignTools.unsubscribe(uid, callback)

##### 54. campaignTools.pushGaEvent(category, action, label, value)

##### 55. campaignTools.setFullScreenHeight(minHeight)

##### 56. campaignTools.parseQueryString()




##### 57. campaignTools.wechatWebviewShareSetup(shareTimelineObject, shareFriendObject)



##### 58. campaignTools.shareButtonSetup(weibo, wechatFriend, wechatTimeline)







