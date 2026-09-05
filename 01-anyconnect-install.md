# 01 · 思科 AnyConnect：各平台安装、连接与更新

> 网站版（更长、含繁体与英文）：https://7d24hrs.com/zh-CN/guides/anyconnect-china

AnyConnect 是思科的企业 VPN 客户端，现在的正式名字叫 **Cisco Secure Client**，用法没变。不需要证书文件、不需要导入配置，填地址和账号密码就能连。它在中国能不能用、连不上怎么换，见 [出海指南 02](https://github.com/vipinus/chuhai-guides/blob/main/02-anyconnect-in-china.md)。

## 安装

| 平台 | 装哪个 | 从哪装 |
|---|---|---|
| Windows 10 及以上 | Cisco Secure Client 5.x | [网站思科页面](https://7d24hrs.com/anyconnect) |
| Windows 7 / 8 | AnyConnect 4.9（最后支持它们的版本，不再更新） | 同上 |
| macOS | Cisco Secure Client 5.x | 同上 |
| iOS | Cisco Secure Client | App Store；商店搜不到就装开源的 OpenConnect，协议相同 |
| Android | Cisco Secure Client | Google Play，或网站页面的 APK |
| Linux | 网站页面的安装包，或发行版仓库里的 openconnect | 同上 |

Windows 上还有开源的 OpenConnect-GUI 可选，账号通用。

## 连接四步

1. 打开客户端，地址栏填服务器地址。蓝盾用户在网站上**点地区国旗**即可复制该地区的地址。
2. 填账号（注册邮箱）和密码。
3. 看到「已连接」后，打开一个查 IP 的网页确认出口在你选的地区。
4. 换地区就换一个地址，客户端会记住用过的地址，下次下拉选。

## 更新

不用先卸载：直接安装新版本覆盖，保存的地址会保留。手机在应用商店更新。系统大版本升级后先更新客户端再排查连接问题。

## 常见提示

| 提示 | 含义 |
|---|---|
| Login failed | 账号密码错，或账号到期 |
| Untrusted server certificate | 多半是系统时间不对，或当前网络在拦截加密连接；换网络再试 |
| Connection attempt has failed | 这个地址暂时不可达，换地区 |

---
由 [蓝盾](https://7d24hrs.com) 团队整理 · 问题来 [Telegram 群](https://t.me/+NWJN_9yITj9kOWFh) · 注册领 24 小时免费试用，邀请朋友每位送 30 天，长期有效
