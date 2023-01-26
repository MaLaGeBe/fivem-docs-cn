---
title: 客户端问题手册
weight: 830
---

遇到游戏崩溃？无法运行FiveM？或者可能遇到一些更含糊的问题？在此处查找最常见的问题。

我在服务器上玩的时候游戏崩溃了
--------------------------------
崩溃通常与服务器特定问题有关。为了确保崩溃与特定服务器无关，建议加入[FiveM.net 测试服务器][testing-server]进行测试。如果这个服务器可以正常运行，我们建议你联系您遇到崩溃的服务器服主。否则，请继续阅读下面的内容。

我被服务器封禁了
----------------------------
FiveM不对你在服务器上所做的事情或服务器管理员对你所做的事情负责。如果你认为自己被误封了，请联系服主。FiveM不能也不会为此事提供支持。

我被所有FiveM服务器封禁了
------------------------------------
请参阅[本篇文章](/docs/support/ban-faq)。

找不到游戏可执行文件
------------------------------
<!-- https://media.discordapp.net/attachments/455024366091108352/479263072276578324/unknown.png -->
<!--<img src="/static/could-not-find-game-exec-error.png">-->
在你的[FiveM Application Data][where-is-fivem-installed]文件夹中找到`CitizenFX.ini`文件并确保它指向正确的路径。使用记事本等文本编辑器打开该文件，并在必要时编辑 GTA V 安装路径。

FiveM已经安装
--------------------------
<!-- https://media.discordapp.net/attachments/455024366091108352/479267390836834306/unknown.png -->
安装FiveM后，不需再使用同一个FiveM.exe文件。从 Windows 开始菜单使用快捷方式运行。按下任务栏上的“开始”按钮，然后在这里查找FiveM。

如果您通过删除快捷方式卸载FiveM，则可能需要正确[卸载FiveM][uninstalling]。

游戏缓存已过时(Game cache outdated)
-------------------
<!-- https://media.discordapp.net/attachments/455024366091108352/479268603510652946/unknown.png -->
<!-- https://vgy.me/JJJzfI.png -->
如果对话框询问`你要继续吗？(Do you wish to continue?)`，请按`是(Yes)`。如果你收到类似`DLC文件丢失(DLC files are missing)`的错误，请按照对话框中的提示确保你的游戏版本是最新的。此外，请确保您的`CitizenFX.ini`指向正确的GTA5安装目录。可以在[FiveM application data][where-is-fivem-installed]目录中找到这个文件。

Error generating ROS entitlement token
--------------------------------------
<!-- https://i.imgur.com/IAobS5M.png -->
Certain antivirus vendors are known to block FiveM for unknown reasons.
[Disable your antivirus][disabling-antivirus] and try again.

Error loading component xyz.dll
-------------------------------
Delete caches.xml from your [FiveM application data][where-is-fivem-installed] folder.
If there is no such file, delete the entire application data folder and run FiveM again. For `adhesive.dll` also see below.

Error loading component adhesive.dll
-------------------------------
Your Windows 10 installation is outdated. Please update it to at least version 1703. To check your current version, open command prompt and type `winver`.

Opening database (privcache:/) failed: IO error: could not lock file
------------------------------
Your privcache got corrupted. Please remove the "priv" folder from the cache folder located in your [FiveM application data][where-is-fivem-installed].

Entry Point Not Found
------------------------------
Delete `v8.dll`, `v8_libbase.dll`, `v8_libplatform.dll` if available in your `C:\Windows\system32` directory. These are (leftover) files from other applications that incorrectly use `system32` to place these files. FiveM loads dll's from `system32` first, resulting in these incorrect dll's being loaded.

Moving of xyz.exe failed (err = 32)
------------------------------
First check your taskmanager for existing fivem processes if you see them close them, if that doesn’t fix the issue try [disabling your antivirus][disabling-antivirus].

Stuck on 'We're getting there and it will be worth the wait'
------------------------------------------------------------
<!-- https://prnt.sc/kj02oo -->
Often caused by aggressive antivirus settings. [Disable your antivirus][disabling-antivirus] and try again.

Stuck on a rotating splash screen
---------------------------------
Delete `%appdata%\citizenfx\ros_id.dat` and `%localappdata%\digitalentitlements`.

Stuck on a black screen
-----------------------
This is a common issue with certain NVIDIA drivers. Stay patient, it takes a minute to load. This often
happens to other games too.

Stuck on a colored background but no menu
------------------------------
This happens on specific older AMD laptop GPUs. Unfortunately, this is caused by CEF and not by FiveM. Once the issue has been fixed in CEF, FiveM will be updated too. A forum moderator has created a topic that could potentially rectify this issue. [Click here][discrete-gpu] for more info.

FiveM uninstalls itself after running it!
-----------------------------------------
This is most likely your antivirus software removing FiveM. Unfortunately some antivirus vendors falsely flag FiveM,
and remove some (or even all) FiveM files as a precaution. You can safely ignore any warnings about this.<br />
[Click here][disabling-antivirus] for more info on how to disable your antivirus.

My game is dropping frames and I have decent hardware
----------------------------
If you believe your game is dropping frames for whatever reason, you may want to take what's called
a 'trace'. A trace can be used to capture game function calls and allows developers to see where an application is taking longer than expected to execute, causing performance drops.

ETW can be downloaded from here:
https://github.com/google/UIforETW/releases

Download the `etwpackage` zip file from the `Assets` section and extract it, optionally, you can click [here](https://github.com/google/UIforETW/releases/download/v1.56/etwpackage1.56.zip) to download it. Make sure you are downloading the zip file that contains the binaries and not the source code.

After extracting the zip file:
- Navigate to the etwpackage folder
- Navigate to the bin folder
- Execute `UIforETW.exe` by double clicking it.

You will see a couple options there (to the right, in the checkbox section), leave them as is and follow the next steps: 
- Wait for the game/application to drop frames. 
- Once your game begins to drop frames click on ‘Start Tracing’. 
- Let it run for a minute.
- Click on `Save Trace Buffers` after that. Remember to upload the trace afterwards.

Traces will most likely end up saved under `C:\Users\xxxx\Documents\etwtraces`. In UI For ETW's window there's a list of saved traces, you can click on. Click on the trace with the most recent date and proceed by clicking on 'Browse Folder' afterwards.

You can use services such as Google drive to upload your trace.

I have an NVIDIA GPU and FiveM hanged
-----------------------------------------
FiveM hangs when using NVIDIA GPUs as of recently are not uncommon (especially on most recent drivers), efforts were made, trying to contact NVIDIA, but no clear response was given. As of now, we're trying to figure out a way to resolve hangs for this specific GPU vendor, but we need your help on this, and here's how you can help us:

Once the NVIDIA 'crash' dialog is shown, follow these steps:
1. Hold `WinKey + R` and type `taskmgr` followed by enter, it's important that you don't close the process while following this guide.
2. Once `Task Manager` opens, go into the `Details` tab.
3. Find `FiveM_GTAProcess.exe`, right click it and click on `Create dump file`.
4. Wait until the process is dumped, it will be created in the following directory: `C:\Users\xxxx\AppData\Local\Temp\FiveM_GTAProcess.DMP`
5. Click `Open File Location` and zip up the following file: `FiveM_GTAProcess.DMP`, you can zip up a file by right clicking it, followed by clicking `Send To -> Compressed (zipped) folder` on the context menu.
6. Contact [CFX Support][email] or one of the elements on our [Discord][discord] once you have the process dump ready to send.

Additionally, you may still enjoy FiveM by rolling back to older drivers such as 471, but we encourage you to send these reports, prior to doing this!

Help! I can't find my issue here!
---------------------------------
We are more than happy to help you out! If you're running into crashes or freezes, please post your issue
on our [forums][forum]. Provide as much detail as you can, that will make it easier for everyone to help you.
For all other issues, you are more than welcome to join our [Discord][discord] and have a chat with us.

[where-is-fivem-installed]: /docs/support/client-faq#where-is-fivem-installed
[disabling-antivirus]: /docs/client-manual/disabling-antivirus
[email]: mailto:support@fivem.net
[forum]: https://forum.cfx.re
[discord]: https://discord.gg/fivem
[testing-server]: https://cfx.re/join/jm85gm
[uninstalling]: /docs/client-manual/installing-fivem#uninstalling
[discrete-gpu]: https://forum.cfx.re/t/217731
