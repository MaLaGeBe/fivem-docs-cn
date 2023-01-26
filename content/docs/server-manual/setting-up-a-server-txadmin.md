---
title: 使用 txAdmin 搭建服务器端
weight: 312
description: >
  通过txAdmin搭建FXServer服务器端的分步教程。
---

## 超级简单的搭建指南
![pic](/server-setup/header.png)
### Windows
#### 下载服务器端
1. [点击查看Windows版服务器端][windows-artifacts]。
2. 下载最新的推荐版本。<br>
   ![pic](/server-setup/windows-step-2.png)
3. 打开刚刚下载的`server.zip`。<br>
   ![pic](/server-setup/windows-step-3.png)
4. 将其解压缩到你要保存的位置。比如：`C:\FXServer\server`。<br>
   ![pic](/server-setup/windows-step-4a.png)<br>
   ![pic](/server-setup/windows-step-4b.png)
5. 打开刚刚解压的文件夹。它应该看起来像这样：<br>
   ![pic](/server-setup/windows-step-5.png)

#### 启动服务器端
1. 双击运行`FXServer.exe`。<br>
   ![pic](/server-setup/windows-step2-1.png)
2. 该网站应该会在你的浏览器中打开。确保已填写 PIN，然后单击 `Link Account`。<br>
   ![pic](/server-setup/windows-step2-2.png)
3. 在此页面登录你的[Cfx.re](https://forum.cfx.re/)账号然后单击`Yes, Allow`。<br>
   ![pic](/server-setup/windows-step2-3.png)
4. 设置密码以登录服务器的管理页面。<br>
   ![pic](/server-setup/windows-step2-4.png)
5. 点击“下一步(Next)”。<br>
   ![pic](/server-setup/windows-step2-5.png)
6. 为您的服务器输入一个名称，然后单击“下一步(Next)”。
7. 选择 'Popular Template'。<br>
   ![pic](/server-setup/windows-step2-7.png)
8. 暂时选择'CFX Default'模板。可能存在其他模板，但有些模板需要数据库服务器。<br>
   ![pic](/server-setup/windows-step2-8.png)
9. 单击“保存（SAve)”或选择其他路径。
10. 点击“Go to the Recipe Deployer”。<br>
   ![pic](/server-setup/windows-step2-10.png)
11. 继续点击“下一步(Next)”。<br>
  ![pic](/server-setup/windows-step2-11.png)
12. 输入你刚刚在 FiveM Keymaster 上创建的密钥，然后单击'Run Recipe'。<br>
   ![pic](/server-setup/windows-step2-12.png)
13. 如果输入无误，你可以再次单击“下一步(Next)”。<br>
   ![pic](/server-setup/windows-step2-13.png)
14. ...最后，单击 "Save & Run Server"，你的服务器端就搭建完成了！<br>
   ![pic](/server-setup/windows-step2-14.png)


[windows-artifacts]: https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/
[server-data]: https://github.com/citizenfx/cfx-server-data

[vcredist]: https://aka.ms/vs/16/release/VC_redist.x64.exe