# 05 · 私网（Tailscale）：安装、登录本站控制服务器、选出口

> 网站版（更长、含繁体与英文）：https://7d24hrs.com/zh-CN/guides/tailscale-mesh

私网栏目用的是 Tailscale（基于 WireGuard 的组网工具），蓝盾自己运行控制服务器，你用**本站账号**登录，与 Tailscale 官方账号无关。登录一次就一直在线，出口地区在菜单里随时换。它和 VPN 的区别、适合谁，见 [网络指南 05](https://github.com/vipinus/network-guides/blob/main/03-private-network-vs-vpn.md)。

## 安装

| 平台 | 从哪装 |
|---|---|
| Windows / macOS / Linux / Android | [网站私网页面](https://7d24hrs.com/mesh)的下载区（本站直连，不用去官网） |
| iPhone / iPad | App Store，需要非中国区 Apple ID（见 [排障 03](https://github.com/vipinus/client-guides/blob/main/06-ios-app-store.md)） |

## 登录

1. **先退出官方账号**（登录过的话）：手机点头像 → Log Out；电脑执行 `tailscale logout`（Linux 前加 sudo）。不退干净，下一步的入口不出现。
2. **把登录指向本站**：
   - 手机：未登录界面右上角「⋯」→ Use custom server（部分版本叫 Use an alternate server），填网站私网页面给的地址，点 Log in。
   - Windows / Linux：在网站页面复制那条 `tailscale up --login-server=…` 命令，PowerShell / 终端里执行。
   - macOS：**按住 Option** 点菜单栏图标 → Debug → Custom Login Server → Add Account，填地址。
3. 浏览器自动打开本站登录页，用本站账号确认。回到客户端已经在线。

## 选出口

- 手机：菜单 → Exit Node，选一个地区，立即生效。
- 电脑：托盘 / 菜单栏图标 → Exit Node 子菜单；或 `tailscale set --exit-node=<地区名>`（`tailscale exit-node list` 看有哪些）。
- 不走出口选 None（命令行等号后留空）。同一时间只能一个出口。

## 到期与设备数

- 设备登录有效期跟账号到期日走，到期几分钟内离线；续费后重新点一次登录即可，不用重装。
- 5 台设备同时在线，与其他接入方式共用额度；超出时踢最久没上线的那台。

## 别这样用

- 同一台设备上还开着别的 VPN（公司 AnyConnect、其他组网软件）：会争 DNS 和路由，看国内视频提示版权、公司内网打不开都是这个原因。
- 校园网 / 公司网限制 UDP：WireGuard 走 UDP，只能靠中继，很慢；换 AnyConnect。

---
由 [蓝盾](https://7d24hrs.com) 团队整理 · 问题来 [Telegram 群](https://t.me/+NWJN_9yITj9kOWFh) · 注册领 24 小时免费试用，邀请朋友每位送 30 天，长期有效
