# 06 · iOS 装不了应用怎么办

iPhone 上搜不到 Hiddify、Tailscale、Telegram，或者提示「此项目在您所在的国家或地区不可用」——不是应用没了，是 App Store 按 Apple ID 的地区分商店，中国区商店没上架大多数网络类应用。苹果不允许侧载，所以没有安装包可以绕过去，本站也不提供。解法只有换一个地区的 Apple ID，推荐新注册一个而不是改现有账号；下面是步骤、「付款方式选无」的窍门，以及为什么绝不能用别人分享的账号。

## 为什么会这样

App Store 按 Apple ID 的地区分商店，不同地区上架的应用不同。中国区商店没有 Hiddify 和 Tailscale，Telegram、Discord 也时有时无；Cisco Secure Client、OpenVPN Connect 在多数地区都有。这是上架差异，不是应用的问题，换个地区的账号就能装。

本站的音乐盒（sing-box）和私网（Tailscale）在 iPhone 上都要走 App Store，所以这一步绕不开；安卓、Windows、macOS 的安装包本站直接提供，不受影响。

## 方案一（推荐）：新注册一个非中国区 Apple ID

1. 退出当前 App Store 的账号：设置 → 顶部头像 → 媒体与购买项目 → 退出登录。只退 App Store，不退 iCloud，你的照片、备份、通讯录都不受影响。
2. 在 App Store 里找一个免费应用，点「获取」，按提示「创建新 Apple ID」。地区选美国、香港、日本、新加坡任一，付款方式选「无 / None」——这个「无」只在「下载免费应用时顺带注册」的路径里出现，直接在网页上注册往往没有这个选项。
3. 用新账号登录 App Store，搜 Hiddify、Tailscale、Telegram 下载。
4. 装完可以切回原来的账号，已经装好的应用照常使用和更新。以后要装新应用再切一次。

## 方案二：把现有账号改地区

在 account.apple.com 登录后修改国家或地区。要先取消所有订阅、把余额用完、有些还要绑当地的付款方式，改回来也一样麻烦。不推荐，除非你本来就要长期换区。

## 绝不要做的事

- 不要用别人分享的 Apple ID，包括群里、网上「共享账号」。账号所有者可以远程锁定你的设备，被锁的 iPhone 只能找对方解；开启双重认证后无法关闭，风险和纠纷都在你身上。本站客服也不会提供任何共享账号。
- 不要装来路不明的描述文件或「企业证书签名」的安装包，那是绕过商店的常见手段，也是植入证书、劫持流量的入口。

## 装好之后

Hiddify：回本站音乐盒页面扫码或复制导入链接。Tailscale：先退出官方账号再按私网页面的步骤填本站的控制服务器地址。Telegram、Discord：进本站联络页扫码进群。

## 常见问题

**换区注册要信用卡吗？** 不要。按方案一的路径（下载免费应用时顺带注册）付款方式可以选「无」。

**新账号会影响我的 iCloud 和照片吗？** 不会。只在 App Store 里切换账号，iCloud 仍是原来的账号。

**iPad 也一样吗？** 一样，iPadOS 用同一套 App Store 规则。

**安卓手机也有这个问题吗？** 没有。安卓、Windows、macOS、Linux 的安装包本站直接分发，不依赖应用商店。

## 延伸阅读

- [联络页：客户端下载卡与三个群](https://7d24hrs.com/zh-CN/contact)
- [音乐盒 sing-box：扫码导入](https://7d24hrs.com/zh-CN/singbox)
- [私网 Tailscale：登录步骤](https://7d24hrs.com/zh-CN/mesh)
- [怎么联系我们、怎么不失联](https://7d24hrs.com/zh-CN/guides/stay-in-touch)

本文网站版（含繁体与英文）：https://7d24hrs.com/zh-CN/guides/ios-app-store

---
由 [蓝盾](https://7d24hrs.com) 团队整理 · 问题来 [Telegram 群](https://t.me/+NWJN_9yITj9kOWFh) · 注册领 24 小时免费试用，邀请朋友每位送 30 天，长期有效
