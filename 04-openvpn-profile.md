# 04 · OpenVPN：下载 .ovpn 配置导入即连

OpenVPN 是老牌开源协议，客户端遍地都是，Linux、路由器、老设备上最省事。蓝盾的配置文件已经带好账号密码，导入就能连。

## 三步

1. 在[网站专网页面](https://7d24hrs.com/openvpn)的表里装你系统的客户端（各平台都有官方 OpenVPN Connect）。
2. 登录后**点地区国旗**下载该地区的 .ovpn 配置文件。
3. 在客户端里打开这个文件，连接。

## 平台差异

| 平台 | 说明 |
|---|---|
| Windows / macOS / Android / iOS | 配置已内置账号密码，导入即连 |
| Linux | 从系统的 VPN 设置里导入 .ovpn，首次连接时填网站邮箱与密码 |
| 路由器 | 见 [router-guides](https://github.com/vipinus/router-guides)，预装固件不需要手动导入 |

## 要知道的

- 一份配置对应一个地区，多地区就多下几份，客户端里切换。
- 改密码后配置里的密码就旧了，重新下载。
- 到期后连不上，续费后原配置继续用。
- 网络环境差、丢包多时，sing-box 往往更快；同一账号可以随时换，见 [02](02-singbox-subscription-links.md)。

---
由 [蓝盾](https://7d24hrs.com) 团队整理 · 问题来 [Telegram 群](https://t.me/+NWJN_9yITj9kOWFh) · 注册领 24 小时免费试用，邀请朋友每位送 30 天，长期有效
