# 04 · OpenVPN：下载 .ovpn 配置导入即连，路由器、NAS、Linux 都能用

> 网站版（更长、含繁体与英文）：https://7d24hrs.com/zh-CN/guides/openvpn-setup

OpenVPN 是老牌开源协议，几乎所有系统、路由器固件、NAS 都自带客户端。蓝盾的配置文件已经带好账号密码和加密材料，导入就能连。手机电脑日常用 AnyConnect 或 sing-box 更省事；OpenVPN 的价值在**只认 OpenVPN 的地方**：OpenWrt 路由器、群晖 / 威联通 NAS、Linux 服务器、老设备。

## 三步

1. 在[网站专网页面](https://7d24hrs.com/openvpn)的表里装你系统的客户端（各平台都有官方 OpenVPN Connect；Windows 也可用 OpenVPN GUI，macOS 可用 Tunnelblick）。
2. 登录后**点地区国旗**下载该地区的 .ovpn。一个地区一个文件。
3. 客户端里打开这个文件，连接。

| 平台 | 说明 |
|---|---|
| Windows / macOS / Android / iOS | 配置已内置账号密码，导入即连 |
| Linux | 系统 VPN 设置 → 从文件导入，首次连接填网站邮箱与密码；命令行 `openvpn --config 文件`；开机自启放 `/etc/openvpn/client/` |
| OpenWrt 路由器 | 装 luci-app-openvpn，上传 .ovpn 启用；预装本站固件的不需要 |
| 群晖 NAS | 控制面板 → 网络 → 网络界面 → 新增 → VPN → OpenVPN（导入 .ovpn）；要让 NAS 出站走线路就勾「使用默认网关」 |
| 威联通 NAS | QVPN → VPN 客户端 → 添加 → OpenVPN，导入 |

## 国内用户：国内网站直连

连上后国内网站会绕远。网站提供「国内直连工具」，双击运行，国内 IP 直连、其余走线路，思科和专网通用。海外用户别用它。

## 连不上按顺序查

| 日志关键词 / 表现 | 原因 | 做法 |
|---|---|---|
| AUTH_FAILED | 账号密码错或到期 | 登录网站看有效期；改过密码要重新下载配置 |
| TLS handshake failed / key negotiation failed | 到服务器的 UDP 不通 | 换地区、换网络；校园网限 UDP 就改用 AnyConnect |
| 导入报错 | 客户端太旧（OpenVPN 2.5 以前） | 更新客户端 |
| 连着突然断 | 账号到期，服务器断开 | 续费后重连，配置不用换 |

## 安全

配置文件里带账号密码，等于账号本身，别外传；泄露了在网站改密码，旧文件立刻失效。线路的握手本身也加了密，没有配置里的密钥连握手都发不起，服务器对扫描器不可见。

---
由 [蓝盾](https://7d24hrs.com) 团队整理 · 问题来 [Telegram 群](https://t.me/+NWJN_9yITj9kOWFh) · 注册领 24 小时免费试用，邀请朋友每位送 30 天，长期有效
