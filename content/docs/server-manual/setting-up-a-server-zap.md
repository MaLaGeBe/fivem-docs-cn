---
title: 通过 ZAP-Hosting 搭建服务器端
weight: 311
description: >
  关于通过 ZAP-Hosting 搭建 FXServer 的分步指南。
---

## ZAP-Hosting 设置步骤

1. 访问 [ZAP-Hosting 网站][zap-hosting-website] 并登录帐户，如果你还没有帐户，请注册一个。
2. 单击屏幕左上角（导航栏）的 [Rent a server][zap-rent-a-server]。
3. 将显示一个对话框，你可以在其中选择你的产品（`Choose your product`）。我们将使用云游戏服务器，依次点击`Gameserver`和`Cloud Gameserver`。
4. 将显示一个新页面，向下滚动直到找到`Search for games`然后输入`FiveM`。我们将选择`FIVE: FiveM Mod (Windows)`，因此请确保单击它。或者，你可以[单击此链接][zap-rent-a-windows-server]。
5. 选择服务器位置，我们将使用位于德国的服务器来举例说明。
6. 向下滚动并根据自己的喜好自定义服务器，请记住要使用超过48人同时加入游戏，你将需要 OneSync，它可以从 Patreon 获得，加入[FiveM 元素俱乐部银牌会员 💿][patreon-join]。
    - 如果你打算使用 OneSync 高级版，您应该使用与 patreon 会员相同的电子邮件地址注册你的服务器，随后它会由 ZAP-Hosting 自动配置。
7. 选择您喜欢的付款方式并同意条款，请记住按照`Step 1`中的详细信息登录。
8. 确认订单后，服务器将启动。服务器启动后，会显示`Initial installation will be required`对话框，然后点击`Install`。
9. 您现在应该能够访问显示 IP 地址的游戏面板，复制它以访问你的游戏服务器。
10. 复制 IP 并启动 FiveM。FiveM 打开后，按键盘上的 F8 调出控制台。输入`connect [你的服务器ip]`如果服务器正在运行，您应该能够连接。

该指南改编自[YouTube@ZAP-Hosting][zap-hosting-youtube-video]。


[zap-hosting-website]: https://zap-hosting.com
[zap-rent-a-server]: https://zap-hosting.com/en/gameserver-hosting/
[zap-rent-a-windows-server]: https://zap-hosting.com/en/shop/product/cloud-gameserver/fivem-mod-windows/
[zap-hosting-youtube-video]: https://www.youtube.com/watch?v=wJWICcBfA0I
[patreon-join]: https://www.patreon.com/join/fivem
