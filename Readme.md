# ![title](title.png)

## **写在最前面**
> 本项目 fork 了 `github.com/medivhzhan/qqapp`
> 仅修改 host 地址为 `https://api.q.qq.com`，并没有进行详细测试。


- **生产环境请慎用。**
- **生产环境请慎用。**
- **生产环境请慎用。**

## `注意` ⚠️

- [v1 版本入口](https://github.com/medivhzhan/qqapp/tree/v1)
- v2 暂时不包含支付相关内容
- 为了保证大家及时用上新功能，已发布 v2 版本，请大家使用经过线上认证 ✅ 的接口。
- 所有接口均已完成，其他接口将在经过线上测试后在新版本中提供给大家。
- 大部分接口需要去线上测试。最近一直比较忙，有条件的朋友可以帮忙一起测试，我代表所有使用者谢谢你：）

## 获取代码

```sh

go get -u github.com/llqgit/qqapp/v2

```

## `目录`

> 文档按照[小程序服务端官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/)排版，方便您一一对照查找相关内容。

✅：代表已经通过线上测试
⚠️：代表还没有或者未完成

- [登录](#登录)
  - [code2Session](#code2Session) ✅
- [用户信息](#用户信息)
  - [getPaidUnionId](#getPaidUnionId) 
- [接口调用凭证](#接口调用凭证)
  - [getAccessToken](#getAccessToken) ✅
- [数据分析](#数据分析)
  - [访问留存](#访问留存)
    - [getDailyRetain](#getDailyRetain) 
    - [getWeeklyRetain](#getWeeklyRetain) 
    - [getMonthlyRetain](#getMonthlyRetain) 
  - [getDailySummary](#getDailySummary) 
  - [访问趋势](#访问趋势)
    - [getDailyVisitTrend](#getDailyVisitTrend) 
    - [getWeeklyVisitTrend](#getWeeklyVisitTrend) 
    - [getMonthlyVisitTrend](#getMonthlyVisitTrend) 
  - [getUserPortrait](#getUserPortrait) 
  - [getVisitDistribution](#getVisitDistribution) 
  - [getVisitPage](#getVisitPage) 
- [客服消息](#客服消息)
  - [getTempMedia](#getTempMedia) 
  - [sendCustomerServiceMessage](#sendCustomerServiceMessage) 
  - [setTyping](#setTyping) 
  - [uploadTempMedia](#uploadTempMedia) 
- [模板消息](#模板消息)(腾讯将于 2020 年 1 月 10 日下线该接口，请使用 [`订阅消息`](#订阅消息))
- [统一服务消息](#统一服务消息)
  - [sendUniformMessage](#sendUniformMessage) 
- [动态消息](#动态消息)
  - [createActivityId](#createActivityId)
  - [setUpdatableMsg](#setUpdatableMsg)
- [插件管理](#插件管理)
  - [applyPlugin](#applyPlugin)
  - [getPluginDevApplyList](#getPluginDevApplyList)
  - [getPluginList](#getPluginList)
  - [setDevPluginApplyStatus](#setDevPluginApplyStatus)
  - [unbindPlugin](#unbindPlugin)
- [附近的小程序](#附近的小程序)
  - [addNearbyPoi](#addNearbyPoi)
  - [deleteNearbyPoi](#deleteNearbyPoi)
  - [getNearbyPoiList](#getNearbyPoiList)
  - [setNearbyPoiShowStatus](#setNearbyPoiShowStatus)
- [小程序码](#小程序码) 
  - [createQRCode](#createQRCode) 
  - [get](#get) 
  - [getUnlimited](#getUnlimited) 
- [内容安全](#内容安全)
  - [imgSecCheck](#imgSecCheck) ✅
  - [mediaCheckAsync](#mediaCheckAsync) ✅
  - [msgSecCheck](#msgSecCheck) ✅
- [图像处理](#图像处理)
  - [aiCrop](#aiCrop) 
  - [scanQRCode](#scanQRCode) 
  - [superResolution](#superResolution)
- [及时配送](#及时配送) ⚠️
  - [小程序使用](#小程序使用)
    - [abnormalConfirm](#abnormalConfirm)
    - [addDeliveryOrder](#addDeliveryOrder)
    - [addDeliveryTip](#addDeliveryTip)
    - [cancelDeliveryOrder](#cancelDeliveryOrder)
    - [getAllImmediateDelivery](#getAllImmediateDelivery)
    - [getBindAccount](#getBindAccount)
    - [getDeliveryOrder](#getDeliveryOrder)
    - [mockUpdateDeliveryOrder](#mockUpdateDeliveryOrder)
    - [onDeliveryOrderStatus](#onDeliveryOrderStatus)
    - [preAddDeliveryOrder](#preAddDeliveryOrder)
    - [preCancelDeliveryOrder](#preCancelDeliveryOrder)
    - [reDeliveryOrder](#reDeliveryOrder)
  - [服务提供方使用](#服务提供方使用)
    - [updateDeliveryOrder](#updateDeliveryOrder)
    - [onAgentPosQuery](#onAgentPosQuery)
    - [onAuthInfoGet](#onAuthInfoGet)
    - [onCancelAuth](#onCancelAuth)
    - [onDeliveryOrderAdd](#onDeliveryOrderAdd)
    - [onDeliveryOrderAddTips](#onDeliveryOrderAddTips)
    - [onDeliveryOrderCancel](#onDeliveryOrderCancel)
    - [onDeliveryOrderConfirmReturn](#onDeliveryOrderConfirmReturn)
    - [onDeliveryOrderPreAdd](#onDeliveryOrderPreAdd)
    - [onDeliveryOrderPreCancel](#onDeliveryOrderPreCancel)
    - [onDeliveryOrderQuery](#onDeliveryOrderQuery)
    - [onDeliveryOrderReAdd](#onDeliveryOrderReAdd)
    - [onPreAuthCodeGet](#onPreAuthCodeGet)
    - [onRiderScoreSet](#onRiderScoreSet)
- [物流助手](#物流助手) ⚠️
  - [小程序使用](#小程序使用)
    - [addExpressOrder](#addExpressOrder)
    - [cancelExpressOrder](#cancelExpressOrder)
    - [getAllDelivery](#getAllDelivery)
    - [getExpressOrder](#getExpressOrder)
    - [getExpressPath](#getExpressPath)
    - [getExpressPrinter](#getExpressPrinter)
    - [getExpressQuota](#getExpressQuota)
    - [onExpressPathUpdate](#onExpressPathUpdate)
    - [testUpdateExpressOrder](#testUpdateExpressOrder)
    - [updateExpressPrinter](#updateExpressPrinter)
  - [服务提供方使用](#服务提供方使用)
    - [getExpressContact](#getExpressContact)
    - [onAddExpressOrder](#onAddExpressOrder)
    - [onCancelExpressOrder](#onCancelExpressOrder)
    - [onCheckExpressBusiness](#onCheckExpressBusiness)
    - [onGetExpressQuota](#onGetExpressQuota)
    - [previewExpressTemplate](#previewExpressTemplate)
    - [updateExpressBusiness](#updateExpressBusiness)
    - [updateExpressPath](#updateExpressPath)
- [OCR](#OCR)
  - [bankcard](#bankcard) 
  - [businessLicense](#businessLicense) 
  - [driverLicense](#driverLicense) 
  - [idcard](#idcard) 
  - [printedText](#printedText) 
  - [vehicleLicense](#vehicleLicense) 
- [运维中心](#运维中心) ⚠️
  - [realTimeLogSearch](#realTimeLogSearch)
- [生物认证](#生物认证)
  - [verifySignature](#verifySignature)
- [订阅消息](#订阅消息)
  - [sendSubscribeMessage](#sendSubscribeMessage) 
- [解密](#解密)
  - [解密手机号码](#解密手机号码) ✅
  - [解密分享内容](#解密分享内容)
  - [解密用户信息](#解密用户信息) ✅

---

## 登录

### code2Session

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/login/auth.code2Session.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.Login("appid", "secret", "code")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 用户信息

### getPaidUnionId

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/user-info/auth.getPaidUnionId.html)

```go
import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetPaidUnionID("access-token", "open-id", "transaction-id")
// 或者
res, err := qqapp.GetPaidUnionIDWithMCH("access-token", "open-id", "out-trade-number", "mch-id")

if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 接口调用凭证

### getAccessToken

> 调用次数有限制 请注意缓存

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/access-token/auth.getAccessToken.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetAccessToken("appid", "secret")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 数据分析

### 访问留存

#### getDailyRetain

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/visit-retain/analysis.getDailyRetain.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetDailyRetain("access-token", "begin-date", "end-date")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### getWeeklyRetain

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/visit-retain/analysis.getWeeklyRetain.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetWeeklyRetain("access-token", "begin-date", "end-date")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### getMonthlyRetain

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/visit-retain/analysis.getMonthlyRetain.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetMonthlyRetain("access-token", "begin-date", "end-date")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### getDailySummary

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/analysis.getDailySummary.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetDailySummary("access-token", "begin-date", "end-date")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### 访问趋势

#### getDailyVisitTrend

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/visit-trend/analysis.getDailyVisitTrend.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetDailyVisitTrend("access-token", "begin-date", "end-date")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### getWeeklyVisitTrend

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/visit-trend/analysis.getWeeklyVisitTrend.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetWeeklyVisitTrend("access-token", "begin-date", "end-date")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### getMonthlyVisitTrend

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/visit-trend/analysis.getMonthlyVisitTrend.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetMonthlyVisitTrend("access-token", "begin-date", "end-date")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### getUserPortrait

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/analysis.getUserPortrait.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetUserPortrait("access-token", "begin-date", "end-date")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### getVisitDistribution

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/analysis.getVisitDistribution.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetVisitDistribution("access-token", "begin-date", "end-date")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### getVisitPage

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/analysis.getVisitPage.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetVisitPage("access-token", "begin-date", "end-date")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 客服消息

### getTempMedia

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/customer-message/customerServiceMessage.getTempMedia.html)

```go

import "github.com/llqgit/qqapp/v2"

resp, res, err := qqapp.GetTempMedia("access-token", "media-id")
if err != nil {
    // 处理一般错误信息
    return
}
defer resp.Close()

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### sendCustomerServiceMessage

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/customer-message/customerServiceMessage.send.html)

```go

import "github.com/llqgit/qqapp/v2"


// 文本消息
msg := qqapp.CSMsgText{
    Content: "content",
}
// 或者
// 图片消息
msg := qqapp.CSMsgImage{
    MediaID: "media-id",
}
// 或者
// 链接消息
msg := qqapp.CSMsgLink{
    Title:       "title",
    Description: "description",
    URL:         "url",
    ThumbURL:    "thumb-url",
}
// 或者
// 小程序卡片消息
msg := qqapp.CSMsgMPCard{
    Title:        "title",
    PagePath:     "page-path",
    ThumbMediaID: "thumb-media-id",
}

res, err := msg.SendTo("open-id", "access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### setTyping

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/customer-message/customerServiceMessage.setTyping.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.SetTyping("access-token", "open-id", qqapp.SetTypingCommandTyping)
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### uploadTempMedia

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/customer-message/customerServiceMessage.uploadTempMedia.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.UploadTempMedia("access-token", qqapp.TempMediaTypeImage, "media-filename")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 统一服务消息

### sendUniformMessage

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/uniform-message/uniformMessage.send.html)

```go

import "github.com/llqgit/qqapp/v2"

sender := qqapp.UniformMsgSender{
    ToUser: "open-id",
    UniformqqappTmpMsg: qqapp.UniformqqappTmpMsg{
        TemplateID: "template-id",
        Page:       "page",
        FormID:     "form-id",
        Data: qqapp.UniformMsgData{
            "keyword": {Value: "value"},
        },
        EmphasisKeyword: "keyword.DATA",
    },
    UniformMpTmpMsg: qqapp.UniformMpTmpMsg{
        AppID:       "app-id",
        TemplateID:  "template-id",
        URL:         "url",
        Miniprogram: qqapp.UniformMsgMiniprogram{"miniprogram-app-id", "page-path"},
        Data: qqapp.UniformMsgData{
            "keyword": {"value", "color"},
        },
    },
}

_, err := sender.Send("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 动态消息

### createActivityId

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/updatable-message/updatableMessage.createActivityId.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.CreateActivityId("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### setUpdatableMsg

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/updatable-message/updatableMessage.setUpdatableMsg.html)

```go

import "github.com/llqgit/qqapp/v2"


setter := qqapp.UpdatableMsgSetter{
    "activity-id",
    UpdatableMsgJoining,
    UpdatableMsgTempInfo{
        []UpdatableMsgParameter{
            {UpdatableMsgParamMemberCount, "parameter-value-number"},
            {UpdatableMsgParamRoomLimit, "parameter-value-number"},
        },
    },
}

res, err := setter.Set("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 插件管理

### applyPlugin

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/plugin-management/pluginManager.applyPlugin.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.ApplyPlugin("access-token", "plugin-app-id", "reason")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### getPluginDevApplyList

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/plugin-management/pluginManager.getPluginDevApplyList.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetPluginDevApplyList("access-token", 1, 2)
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### getPluginList

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/plugin-management/pluginManager.getPluginList.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetPluginList("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### setDevPluginApplyStatus

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/plugin-management/pluginManager.setDevPluginApplyStatus.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.SetDevPluginApplyStatus("access-token", "plugin-app-id", "reason", qqapp.DevAgree)
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### unbindPlugin

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/plugin-management/pluginManager.unbindPlugin.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.UnbindPlugin("access-token", "plugin-app-id")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 附近的小程序

### addNearbyPoi

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/nearby-poi/nearbyPoi.add.html)

```go

import "github.com/llqgit/qqapp/v2"

poi := NearbyPoi{
    PicList: PicList{[]string{"first-picture-url", "second-picture-url", "third-picture-url"}},
    ServiceInfos: qqapp.ServiceInfos{[]qqapp.ServiceInfo{
        {1, 1, "name", "app-id", "path"},
    }},
    StoreName:         "store-name",
    Hour:              "11:11-12:12",
    Credential:        "credential",
    Address:           "address",                         // 地址 必填
    CompanyName:       "company-name",                    // 主体名字 必填
    QualificationList: "qualification-list",              // 证明材料 必填 如果company_name和该小程序主体不一致，需要填qualification_list，详细规则见附近的小程序使用指南-如何证明门店的经营主体跟公众号或小程序帐号主体相关http://kf.qq.com/faq/170401MbUnim17040122m2qY.html
    KFInfo:            qqapp.KFInfo{true, "kf-head-img", "kf-name"}, // 客服信息 选填，可自定义服务头像与昵称，具体填写字段见下方示例kf_info pic_list是字符串，内容是一个json！
    PoiID:             "poi-id",                          // 如果创建新的门店，poi_id字段为空 如果更新门店，poi_id参数则填对应门店的poi_id 选填
}

res, err := poi.Add("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

// 接收并处理异步结果
srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnAddNearbyPoi(func(mix *qqapp.AddNearbyPoiResult) {
    // 处理返回结果
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

### deleteNearbyPoi

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/nearby-poi/nearbyPoi.delete.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.DeleteNearbyPoi("access-token", "poi-id")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### getNearbyPoiList

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/nearby-poi/nearbyPoi.getList.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetNearbyPoiList("access-token", 1, 10)
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### setNearbyPoiShowStatus

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/nearby-poi/nearbyPoi.setShowStatus.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.SetNearbyPoiShowStatus("access-token", "poi-id", qqapp.ShowNearbyPoi)
// 或者
res, err := qqapp.SetNearbyPoiShowStatus("access-token", "poi-id", qqapp.HideNearbyPoi)
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 小程序码

### createQRCode

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/qr-code/wxacode.createQRCode.html)

```go

import (
    "ioutil"
    "github.com/llqgit/qqapp/v2"
)


creator := qqapp.QRCodeCreator{
    Path:  "mock/path",
    Width: 430,
}

resp, res, err := creator.Create("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}
defer resp.Body.Close()

content, err := ioutil.ReadAll(resp.Body)
// 处理图片内容

```

### get

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/qr-code/wxacode.get.html)

```go

import (
    "ioutil"
    "github.com/llqgit/qqapp/v2"
)


getter := qqapp.QRCode{
    Path:      "mock/path",
    Width:     430,
    AutoColor: true,
    LineColor: qqapp.Color{"r", "g", "b"},
    IsHyaline: true,
}

resp, res, err := getter.Get("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}
defer resp.Body.Close()

content, err := ioutil.ReadAll(resp.Body)
// 处理图片内容

```

### getUnlimited

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/qr-code/wxacode.getUnlimited.html)

```go

import (
    "ioutil"
    "github.com/llqgit/qqapp/v2"
)


getter :=  qqapp.UnlimitedQRCode{
    Scene:     "scene-data",
    Page:      "mock/page",
    Width:     430,
    AutoColor: true,
    LineColor: qqapp.Color{"r", "g", "b"},
    IsHyaline: true,
}

resp, res, err := getter.Get("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}
defer resp.Body.Close()

content, err := ioutil.ReadAll(resp.Body)
// 处理图片内容

```

---

## 内容安全

### imgSecCheck

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/sec-check/security.imgSecCheck.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.IMGSecCheck("access-token", "local-filename")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### mediaCheckAsync

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/sec-check/security.mediaCheckAsync.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.MediaCheckAsync("access-token", "image-url", qqapp.MediaTypeImage)
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

// 接收并处理异步结果
srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnMediaCheckAsync(func(mix *qqapp.MediaCheckAsyncResult) {
    // 处理返回结果
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

### msgSecCheck

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/sec-check/security.msgSecCheck.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.MSGSecCheck("access-token", "message-content")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 图像处理

### aiCrop

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/img/img.aiCrop.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.AICrop("access-token", "filename")
// 或者
res, err := qqapp.AICropByURL("access-token", "url")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### scanQRCode

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/img/img.scanQRCode.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.ScanQRCode("access-token", "file-path")
// 或者
res, err := qqapp.ScanQRCodeByURL("access-token", "qr-code-url")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### superResolution

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/img/img.superresolution.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.SuperResolution("access-token", "file-path")
// 或者
res, err := qqapp.SuperResolutionByURL("access-token", "img-url")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 及时配送

### 服务提供方使用

#### updateDeliveryOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.updateOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

mocker := qqapp.DeliveryOrderUpdater{
   // ...
}

res, err := mocker.Update("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### onAgentPosQuery

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.onAgentPosQuery.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnAgentPosQuery(func(mix *qqapp.AgentPosQueryResult) *qqapp.AgentPosQueryReturn {
    // 处理返回结果

    return &qqapp.AgentPosQueryReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onAuthInfoGet

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.onAuthInfoGet.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnAuthInfoGet(func(mix *qqapp.AuthInfoGetResult) *qqapp.AuthInfoGetReturn {
    // 处理返回结果

    return &qqapp.AuthInfoGetReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onCancelAuth

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.onCancelAuth.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnCancelAuth(func(mix *qqapp.CancelAuthResult) *qqapp.CancelAuthReturn {
    // 处理返回结果

    return &qqapp.CancelAuthReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onDeliveryOrderAdd

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.onOrderAdd.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnDeliveryOrderAdd(func(mix *qqapp.DeliveryOrderAddResult) *qqapp.DeliveryOrderAddReturn {
    // 处理返回结果

    return &qqapp.DeliveryOrderAddReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onDeliveryOrderAddTips

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.onOrderAddTips.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnDeliveryOrderAddTips(func(mix *qqapp.DeliveryOrderAddTipsResult) *qqapp.DeliveryOrderAddTipsReturn {
    // 处理返回结果

    return &qqapp.DeliveryOrderAddTipsReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onDeliveryOrderCancel

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.onOrderCancel.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnDeliveryOrderCancel(func(mix *qqapp.DeliveryOrderCancelResult) *qqapp.DeliveryOrderCancelReturn {
    // 处理返回结果

    return &qqapp.DeliveryOrderCancelReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onDeliveryOrderConfirmReturn

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.onOrderConfirmReturn.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnDeliveryOrderReturnConfirm(func(mix *qqapp.DeliveryOrderReturnConfirmResult) *qqapp.DeliveryOrderReturnConfirmReturn {
    // 处理返回结果

    return &qqapp.DeliveryOrderReturnConfirmReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onDeliveryOrderPreAdd

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.onOrderPreAdd.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnDeliveryOrderPreAdd(func(mix *qqapp.DeliveryOrderPreAddResult) *qqapp.DeliveryOrderPreAddReturn {
    // 处理返回结果

    return &qqapp.DeliveryOrderPreAddReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onDeliveryOrderPreCancel

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.onOrderPreCancel.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnDeliveryOrderPreCancel(func(mix *qqapp.DeliveryOrderPreCancelResult) *qqapp.DeliveryOrderPreCancelReturn {
    // 处理返回结果

    return &qqapp.DeliveryOrderPreCancelReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onDeliveryOrderQuery

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.onOrderQuery.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnDeliveryOrderQuery(func(mix *qqapp.DeliveryOrderQueryResult) *qqapp.DeliveryOrderQueryReturn {
    // 处理返回结果

    return &qqapp.DeliveryOrderQueryReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onDeliveryOrderReAdd

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.onOrderReAdd.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnDeliveryOrderReadd(func(mix *qqapp.DeliveryOrderReaddResult) *qqapp.DeliveryOrderReaddReturn {
    // 处理返回结果

    return &qqapp.DeliveryOrderReaddReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onPreAuthCodeGet

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.onPreAuthCodeGet.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnPreAuthCodeGet(func(mix *qqapp.PreAuthCodeGetResult) *qqapp.PreAuthCodeGetReturn {
    // 处理返回结果

    return &qqapp.PreAuthCodeGetReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onRiderScoreSet

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-provider/immediateDelivery.onRiderScoreSet.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnRiderScoreSet(func(mix *qqapp.RiderScoreSetResult) *qqapp.RiderScoreSetReturn {
    // 处理返回结果

    return &qqapp.PreAuthCodeGetReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

### 小程序使用

#### abnormalConfirm

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-business/immediateDelivery.abnormalConfirm.html)

```go

import "github.com/llqgit/qqapp/v2"

confirmer := qqapp.AbnormalConfirmer{
    ShopID:       "123456",
    ShopOrderID:  "123456",
    ShopNo:       "shop_no_111",
    WaybillID:    "123456",
    Remark:       "remark",
    DeliverySign: "123456",
}

res, err := confirmer.Confirm("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### addDeliveryOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-business/immediateDelivery.addOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

creator := qqapp.DeliveryOrderCreator{
   // ...
}

res, err := creator.Create("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### addDeliveryTip

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-business/immediateDelivery.addTip.html)

```go

import "github.com/llqgit/qqapp/v2"

adder := qqapp.DeliveryTipAdder{
   // ...
}

res, err := adder.Add("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### cancelDeliveryOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-business/immediateDelivery.cancelOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

canceler := qqapp.DeliveryOrderCanceler{
   // ...
}

res, err := canceler.Cancel("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### getAllImmediateDelivery

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-business/immediateDelivery.getAllImmeDelivery.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetAllImmediateDelivery("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### getBindAccount

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-business/immediateDelivery.getBindAccount.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetBindAccount("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### getDeliveryOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-business/immediateDelivery.getOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

getter := qqapp.DeliveryOrderGetter{
   // ...
}

res, err := getter.Get("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### mockUpdateDeliveryOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-business/immediateDelivery.mockUpdateOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

mocker := qqapp.UpdateDeliveryOrderMocker{
   // ...
}

res, err := mocker.Mock("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### onDeliveryOrderStatus

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-business/immediateDelivery.onOrderStatus.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnDeliveryOrderStatusUpdate(func(mix *qqapp.DeliveryOrderStatusUpdateResult) *qqapp.DeliveryOrderStatusUpdateReturn {
    // 处理返回结果

    return &qqapp.DeliveryOrderStatusUpdateReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### preAddDeliveryOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-business/immediateDelivery.preAddOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

creator := qqapp.DeliveryOrderCreator{
   // ...
}

res, err := creator.Prepare("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### preCancelDeliveryOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-business/immediateDelivery.preCancelOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

canceler := qqapp.DeliveryOrderCanceler{
   // ...
}

res, err := canceler.Prepare("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### reDeliveryOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/immediate-delivery/by-business/immediateDelivery.reOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

creator := qqapp.DeliveryOrderCreator{
   // ...
}

res, err := creator.Recreate("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 物流助手

### 小程序使用

#### addExpressOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-business/logistics.addOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

creator := qqapp.ExpressOrderCreator{
   // ...
}

res, err := creator.Create("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### cancelExpressOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-business/logistics.cancelOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

canceler := qqapp.ExpressOrderCanceler{
   // ...
}

res, err := canceler.cancel("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### getAllDelivery

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-business/logistics.getAllDelivery.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.getAllDelivery("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### getExpressOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-business/logistics.getOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

getter := qqapp.ExpressOrderGetter{
   // ...
}

res, err := getter.Get("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### getExpressPath

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-business/logistics.getPath.html)

```go

import "github.com/llqgit/qqapp/v2"

getter := qqapp.ExpressPathGetter{
   // ...
}

res, err := getter.Get("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### getExpressPrinter

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-business/logistics.getPrinter.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetPrinter("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### getExpressQuota

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-business/logistics.getQuota.html)

```go

import "github.com/llqgit/qqapp/v2"

getter := qqapp.QuotaGetter{
   // ...
}

res, err := getter.Get("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### onExpressPathUpdate

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-business/logistics.onPathUpdate.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnExpressPathUpdate(func(mix *qqapp.ExpressPathUpdateResult) {
    // 处理返回结果
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### testUpdateExpressOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-business/logistics.testUpdateOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

tester := qqapp.UpdateExpressOrderTester{
   // ...
}

res, err := tester.Test("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### updateExpressPrinter

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-business/logistics.updatePrinter.html)

```go

import "github.com/llqgit/qqapp/v2"

updater := qqapp.PrinterUpdater{
   // ...
}

res, err := updater.Update("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### 服务提供方使用

#### getExpressContact

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-provider/logistics.getContact.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.GetContact("access-token", "token", "wat-bill-id")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### onAddExpressOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-provider/logistics.onAddOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnAddExpressOrder(func(mix *qqapp.AddExpressOrderResult) *qqapp.AddExpressOrderReturn {
    // 处理返回结果

    return &qqapp.AddExpressOrderReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onCancelExpressOrder

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-provider/logistics.onCancelOrder.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnCancelExpressOrder(func(mix *qqapp.CancelExpressOrderResult) *qqapp.CancelExpressOrderReturn {
    // 处理返回结果

    return &qqapp.CancelExpressOrderReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onCheckExpressBusiness

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-provider/logistics.onCheckBusiness.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnCheckExpressBusiness(func(mix *qqapp.CheckExpressBusinessResult) *qqapp.CheckExpressBusinessReturn {
    // 处理返回结果

    return &qqapp.CheckExpressBusinessReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### onGetExpressQuota

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-provider/logistics.onGetQuota.html)

```go

import "github.com/llqgit/qqapp/v2"

srv, err := qqapp.NewServer("app-id", "access-token", "aes-key", "mch-id", "api-key", false)
if err != nil {
    // 处理微信返回错误信息
    return
}

srv.OnGetExpressQuota(func(mix *qqapp.GetExpressQuotaResult) *qqapp.GetExpressQuotaReturn {
    // 处理返回结果

    return &qqapp.GetExpressQuotaReturn{
        // ...
    }
})

if err := srv.Serve(http.ResponseWriter, *http.Request); err != nil {
    // 处理微信返回错误信息
    return
}

```

#### previewExpressTemplate

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-provider/logistics.previewTemplate.html)

```go

import "github.com/llqgit/qqapp/v2"

previewer := qqapp.ExpressTemplatePreviewer{
   // ...
}

res, err := previewer.Preview("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### updateExpressBusiness

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-provider/logistics.updateBusiness.html)

```go

import "github.com/llqgit/qqapp/v2"

updater := qqapp.BusinessUpdater{
   // ...
}

res, err := updater.Update("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

#### updateExpressPath

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/express/by-provider/logistics.updatePath.html)

```go

import "github.com/llqgit/qqapp/v2"

updater := qqapp.ExpressPathUpdater{
   // ...
}

res, err := updater.Update("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## OCR

### bankcard

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/ocr/ocr.bankcard.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.BankCard("access-token", "file-path", qqapp.RecognizeModeScan)
// 或者
res, err := qqapp.BankCardByURL("access-token", "card-url", qqapp.RecognizeModePhoto)
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### businessLicense

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/ocr/ocr.businessLicense.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.BusinessLicense("access-token", "file-path")
// 或者
res, err := qqapp.BusinessLicenseByURL("access-token", "card-url")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### driverLicense

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/ocr/ocr.driverLicense.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.DriverLicense("access-token", "file-path")
// 或者
res, err := qqapp.DriverLicenseByURL("access-token", "card-url")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### idcard

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/ocr/ocr.idcard.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.IDCardByURL("access-token", "card-url", qqapp.RecognizeModePhoto)
// 或者
res, err := qqapp.IDCard("access-token", "file-path", qqapp.RecognizeModeScan)
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### printedText

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/ocr/ocr.printedText.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.PrintedText("access-token", "file-path")
// 或者
res, err := qqapp.PrintedTextByURL("access-token", "card-url")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

### vehicleLicense

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/ocr/ocr.vehicleLicense.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.VehicleLicense("access-token", "file-path", qqapp.RecognizeModeScan)
// 或者
res, err := qqapp.VehicleLicenseByURL("access-token", "card-url", qqapp.RecognizeModePhoto)
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 生物认证

### verifySignature

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/soter/soter.verifySignature.html)

```go

import "github.com/llqgit/qqapp/v2"

res, err := qqapp.VerifySignature("access-token", "open-id", "data", "signature")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 订阅消息

### sendSubscribeMessage

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/subscribe-message/subscribeMessage.send.html)

```go

import "github.com/llqgit/qqapp/v2"

sender := qqapp.SubscribeMessage{
    ToUser:     mpOpenID,
    TemplateID: "template-id",
    Page:       "mock/page/path",
    Data: qqapp.SubscribeMessageData{
        "first-key": {
            Value: "value",
        },
        "second-key": {
            Value: "value",
        },
    },
}

_, err := sender.Send("access-token")
if err != nil {
    // 处理一般错误信息
    return
}

if err := res.GetResponseError(); err !=nil {
    // 处理微信返回错误信息
    return
}

fmt.Printf("返回结果: %#v", res)

```

---

## 解密

[官方文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/signature.html)

> ⚠️ 前端应当先完成[登录](#登录)流程再调用获取加密数据的相关接口。

### 解密手机号码

```go
import "github.com/llqgit/qqapp/v2"

res, err := qqapp.DecryptMobile("session-key", "encrypted-date", "iv" )
if err != nil {
    // 处理一般错误信息
    return
}

fmt.Printf("返回结果: %#v", res)
```

### 解密分享内容

```go
import "github.com/llqgit/qqapp/v2"

res, err := qqapp.DecryptShareInfo("session-key", "encrypted-date", "iv" )
if err != nil {
    // 处理一般错误信息
    return
}

fmt.Printf("返回结果: %#v", res)
```

### 解密用户信息

```go
import "github.com/llqgit/qqapp/v2"

res, err := qqapp.DecryptUserInfo( "session-key", "raw-data", "encrypted-date", "signature", "iv")
if err != nil {
    // 处理一般错误信息
    return
}

fmt.Printf("返回结果: %#v", res)
```

---
