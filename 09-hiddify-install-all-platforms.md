# 09 · 伪装（Hiddify）各平台安装：Windows、macOS、Linux、安卓、iOS

伪装（流量伪装）用的客户端是开源的 Hiddify，自带 sing-box 内核，装完不用再配别的。五个平台用同一个 App，但各平台装好之后第一次运行要过的关不一样：Windows 可能被杀毒软件拦或删，Mac 可能提示「已损坏」还要给网络扩展授权，Linux 要执行一条授权命令才能开 VPN 模式，iPhone 在国区商店搜不到。这篇把每个平台从哪下载、怎么装、第一次运行要做什么一次讲完，最后给导入订阅并连上的最短步骤。

## 从哪里下载

| 平台 | 安装包 | 从哪装 |
|---|---|---|
| Windows | 安装程序（.exe），只有 x64 | 伪装页下载区 |
| macOS | .dmg，Apple 芯片和 Intel 通用一个包 | 伪装页下载区 |
| Linux | .deb（Debian / Ubuntu 系），只有 x64 | 伪装页下载区 |
| 安卓 | .apk，分 ARM64 和 x86-64 两个 | 伪装页下载区，或 Google Play |
| iPhone / iPad | App Store 的 Hiddify Proxy & VPN | App Store，需要非中国区 Apple ID |

伪装页的下载区会按你当前的系统自动推荐对应的包，其他系统的包也列在下面。每一行旁边还有「官方网站」图标，指向 Hiddify 官方发布页，可以对照版本。桌面三个系统（Windows、macOS、Linux）还有视频教程。

桌面安装包是 Hiddify 官方发布包的原样镜像，不改动、不重新打包。放行之前可以先自己核对：把安装包上传 VirusTotal 看看，方法见 [排障 06](https://github.com/vipinus/troubleshooting-guides/blob/main/06-antivirus-false-positive.md)。

## Windows

1. 从伪装页下载区下载安装程序，双击安装。（目前实测 Windows 安全中心不会报毒；万一你装的杀毒软件报了，见 [排障 06](https://github.com/vipinus/troubleshooting-guides/blob/main/06-antivirus-false-positive.md) 最后的常见问题。）

## macOS

1. 从伪装页下载区下载 .dmg，打开后把 Hiddify 拖进「应用程序」。
2. 在「访达」→「应用程序」里按住 Control 点 Hiddify 图标，选「打开」，在对话框里再点一次「打开」。
3. 还是打不开：「系统设置」→「隐私与安全性」，在「安全性」一栏点「仍要打开」，输入密码确认。
4. 提示「已损坏，无法打开」：文件并没有坏，是系统在拦没有签名的 App。打开「终端」，执行下面这条命令，回车后输入登录密码，再打开 Hiddify：

```bash
sudo xattr -dr com.apple.quarantine /Applications/Hiddify.app
```

这条命令只移除下载来源的隔离标记，只对这一个 App 生效。**不要**用 `sudo spctl --master-disable` 整机关掉 Gatekeeper。

装好后第一次点连接，系统还会要求给「网络扩展」授权，不做这步图标会一直转圈、连不上：

- **macOS 15 Sequoia 及更新**：「系统设置」→「通用」→「登录项与扩展」，拉到底部的「扩展」，显示方式切成「按类别」，点「网络扩展」旁边的 ⓘ，打开 Hiddify 的开关，按提示输入密码或验证指纹。
- **macOS 13 Ventura / 14 Sonoma**：先启动 Hiddify 并点一次连接，会弹出「系统扩展已被阻止」；然后「系统设置」→「隐私与安全性」，往下找到「来自开发者 … 的系统软件已被阻止载入」，点「允许」并输入密码。

公司配发的 Mac 如果这些按钮是灰的，是设备管理策略锁住了，找 IT，或者改用已签名的思科、专网、私网客户端。

## Linux

1. 从伪装页下载区下载 .deb，双击用软件中心安装，或在下载目录打开终端执行（Debian、Ubuntu 及其衍生版）：

```bash
sudo apt install ./下载的文件名.deb
```

2. 装完直接连接会报「operation not permitted」，开不了 VPN 模式——官方 deb 装好后没有这项权限。打开终端执行下面这条命令给 Hiddify 授权，然后重新打开 Hiddify：

```bash
echo /usr/share/hiddify/lib | sudo tee /etc/ld.so.conf.d/hiddify.conf && sudo ldconfig && sudo setcap cap_net_admin,cap_net_raw+ep /usr/share/hiddify/hiddify
```

3. **每次升级 Hiddify 后要再执行一次**：授权挂在程序文件上，升级换了文件，授权就没了。

只提供 x64 的 deb。ARM 的 Linux 设备没有对应的包，可以用专网（OpenVPN）。

## 安卓

1. 从伪装页下载区下载 .apk。页面会按你的手机自动推荐架构，绝大多数手机是 ARM64。能用 Google Play 的也可以直接在商店装。
2. 安装时提示「未知来源」或安全软件提醒，允许即可。
3. 第一次点连接时系统会申请 VPN 权限，点允许。

## iPhone / iPad

1. 在 App Store 搜「Hiddify」安装，免费。
2. 搜不到、或提示「此项目在您所在的国家或地区不可用」：Hiddify 没在中国区商店上架（美国、香港、台湾、日本、新加坡都有）。苹果不允许侧载，没有安装包可以绕过，只能换一个非中国区的 Apple ID。推荐新注册一个：在 App Store 里对任意免费应用点「获取」→「创建新 Apple ID」，地区选香港、美国等，付款方式选「无」。只在 App Store 里切换账号，不影响 iCloud。完整步骤见 [06 · iOS 装不了应用怎么办](https://github.com/vipinus/client-guides/blob/main/06-ios-app-store.md)。
3. 第一次点连接时系统会申请 VPN 权限，点允许。

**不要**用别人分享的 Apple ID，对方能远程锁你的设备。

## 装好后：导入订阅并连接

1. 登录网站，打开伪装页。
2. 点想用的地区国旗，弹出二维码；或点页面上方的「导入所有自动选择」，一次导入境外全部地区、由客户端自动选。**它不包含中国区**：回国看视频、登网银要单独点中国国旗导入。
3. 手机：点「复制导入链接」后切到 Hiddify 按提示添加，或用另一台设备上的 Hiddify 扫码。电脑：点「复制配置地址（粘贴用）」，在 Hiddify 里点「+」→「从剪贴板添加」。
4. 点连接。

三种链接的区别、其他客户端怎么导入、订阅会不会过期，见 [02 · Hiddify 订阅链接](https://github.com/vipinus/client-guides/blob/main/02-singbox-subscription-links.md)。导入了连不上，见 [排障 04](https://github.com/vipinus/troubleshooting-guides/blob/main/04-singbox-import-not-connecting.md)。

## 常见问题

**安装包是你们改过的吗？** 不是。桌面安装包是 Hiddify 官方发布包的原样镜像，伪装页每一行都有指向官方发布页的链接，可以自己对照版本，也可以上传 VirusTotal 复核。


**Mac 上已经执行了 xattr 命令，还是连不上？** 多半是「网络扩展」没授权，按上面 macOS 那一节去系统设置里打开 Hiddify 的开关。

**Linux 升级 Hiddify 后又开不了 VPN 模式了？** 正常现象，升级后重新执行一次授权命令。

**ARM 的 Windows 或 Linux 电脑能用吗？** 目前没有这两种桌面包，可以换用专网（OpenVPN）等其他接入方式，账号通用。

**不想折腾放行步骤？** 思科（Cisco Secure Client）、专网（OpenVPN Connect）、私网（Tailscale）都是厂商签名的客户端，不会被报毒，Mac 上也不会提示「已损坏」，账号是同一个。

## 延伸阅读

- [伪装页：客户端下载与各地区二维码](https://7d24hrs.com/zh-CN/singbox)
- [Hiddify 订阅链接怎么导入](https://7d24hrs.com/zh-CN/guides/singbox-subscription)
- [客户端被报毒 / Mac 提示已损坏：先验证，再放行](https://7d24hrs.com/zh-CN/guides/antivirus-false-positive)
- [macOS「网络扩展」授权是什么、怎么放行](https://7d24hrs.com/zh-CN/guides/macos-network-extension)
- [iOS 装不了应用怎么办](https://7d24hrs.com/zh-CN/guides/ios-app-store)

---
由 [蓝盾](https://7d24hrs.com) 团队整理 · 问题来 [Telegram 群](https://t.me/+NWJN_9yITj9kOWFh) · 注册领 24 小时免费试用，邀请朋友每位送 30 天，长期有效
