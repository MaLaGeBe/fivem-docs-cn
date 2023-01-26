---
title: 使用 FXServer 搭建服务器端
weight: 313
description: >
    FXServer分步搭建指南
---


## 服务器端分步搭建教程

### Windows

#### 先决条件
1. 如果你想按照推荐的方式 _克隆_ 基础服务器端数据，请使用 [Git][git-scm]。

#### 安装
1. 创建一个新目录（例如 `C:\FXServer\server`），这将用于服务器端程序文件。
2. 从[Windows服务器端构建列表][windows-artifacts]下载当前推荐的 Windows master 分支构建程序。
3. 将下载的文件解压缩到先前创建的目录中。
    * 3b. 使用任意第三方解压缩工具（例如 WinRAR 或 7-Zip）打开 `.7z` 文件。
4. 将 [cfx-server-data][server-data] Clone 到服务器端程序文件夹之外的新文件夹中，例如 `C:\FXServer\server-data`。
    * 4b. `git clone https://github.com/citizenfx/cfx-server-data.git server-data` *（要输入此命令，你需要打开命令提示符，按 `Win + R`，在弹出的运行对话框中输入`cmd`然后按回车键，请记住通过键入 `cd C:\FXServer` 将目录切换到你计划clone的目录。）*
5. 在你的`server-data`文件夹中创建一个**server.cfg**文件（将以下[示例 server.cfg](#servercfg)文件复制到该文件中）。
6. 使用`sv_licenseKey "licenseKeyGoesHere"`在server.cfg 中设置许可证密钥。
7. 从 `server-data` 文件夹运行服务器。例如，在命令提示符 (cmd.exe) 窗口中运行： 
    ```dos
    cd /d C:\FXServer\server-data
    C:\FXServer\server\FXServer.exe +exec server.cfg
    ```

    （仅当将目录更改为不同驱动器上的某个路径时才需要添加 `/d` 指令）

---

### Linux
{{% alert theme="info" %}}请注意，由于有关 Linux 发行版兼容性和本机 C++ 代码诊断工具可用性的问题，FXServer 的 Linux 版本仅作为免费端口提供。
如果你遇到任何问题，还请使用 Windows 版本，则更有可能看到你遇到的问题都已得到修复。
{{% /alert %}}

#### 先决条件
1. 如果你想按照推荐的方式 _克隆_ 基础服务器端数据，请使用 [Git][git-scm]。
2. 安装 `xz` 或 `xz-utils` 包。 

#### 安装
1. 创建一个新文件夹（例如 `mkdir -p ~/FXServer/server`），这将用于保存服务器端程序文件。
2. 从[Linux服务器端构建列表][linux-artifacts]下载当前推荐的 Linux master 分支构建程序（复制推荐服务器端版本 URL 并使用 `wget <url>` 下载它）
3. 使用 `cd ~/FXServer/server && tar xf fx.tar.xz` 将下载的文件解压缩到之前创建的目录（你需要安装 `xz`，在 Debian/Ubuntu 上在 `xz-utils` 包中）。
4. 将 [cfx-server-data][server-data] Clone 到服务器端程序文件夹之外的新文件夹中。<br>
   示例：`git clone https://github.com/citizenfx/cfx-server-data.git ~/FXServer/server-data`
5. 在你的`server-data`文件夹中创建一个**server.cfg**文件（将以下[示例 server.cfg](#servercfg)文件复制到该文件中）。
6. 使用`sv_licenseKey "licenseKeyGoesHere"`在server.cfg 中设置许可证密钥。
7. 从 `server-data` 文件夹运行服务器端。<br>
   `cd ~/FXServer/server-data && bash ~/FXServer/server/run.sh +exec server.cfg`

---

<a name="servercfgexample"></a>

## server.cfg

下面是一个`server.cfg`的示例文件。

{{%  code file="/static/examples/config/server.cfg" language="sh"  %}}

---

### 常见问题

- 如果提示`resources found`并且显示`Failed to start resource`则说明你没有`cd`到正确的文件夹路径。
- 如果没有提示`resources get started`而且你也无法连接服务器(如`timed out`/`connection refused`)，那么你没有添加`+exec`指令。
- 如果提示`no license key was specified`则可能出现上述两个问题之一。

[windows-artifacts]: https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/
[linux-artifacts]: https://runtime.fivem.net/artifacts/fivem/build_proot_linux/master/
[server-data]: https://github.com/citizenfx/cfx-server-data

[vcredist]: https://aka.ms/vs/16/release/VC_redist.x64.exe
[winrar]: https://www.rarlab.com/download.htm
[7zip]: https://www.7-zip.org/download.html
[git-scm]: https://git-scm.com/download/win

