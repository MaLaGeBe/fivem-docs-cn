---
title: 控制台指令
weight: 260
---

客户端命令列表，可用于开发服务器或调试资源问题。可以通过资源添加额外的命令，这些只是标准的 FiveM 命令。

这些命令可以与客户端控制台一起使用，您可以通过按 F8 打开它。如果愿意，你还可以安装其他工具，如[VConsole2][vconsole]。这使你可以在游戏外使用客户端控制台。

## 用户命令

任何人都可以在客户端控制台中使用用户命令，并且不需要启用或使用额外的开发人员模式设置。

### connect \<server\>
使用给定的IP地址、端口或URL连接到服务器。

示例： `connect 127.0.0.1:30120`, `connect "https://fivem.net/"`, `connect cfx.re/join/e23ywr`


### disconnect
将你与所连接的服务器断开连接并返回主菜单。

### bind
列出所有已配置的快捷指令。

### bind \<mapper> \<input> \<command>
绑定[快捷指令](/docs/game-references/input-mapper-parameter-ids/)以在游戏中按下时执行指定的指令。
绑定输入以在游戏中按下时执行指定的命令。

示例： `bind keyboard F9 "say hi; wait 250; say bye"`

### rbind \<resource> \<mapper> \<input> \<command>
同上，但仅当指定的脚本资源在服务器端正在使用时才会运行。

### unbind \<mapper> \<input>
取消绑定所有已绑定到键盘映射输入的指令。

示例： `unbind keyboard F9`

### cl_drawfps \<bool\>
在屏幕角落启用或禁用FPS显示。

示例： `cl_drawfps <true|false>`

### cl_drawperf \<bool\>
启用或禁用在屏幕角落显示性能指数：

| 名称（单位）   |                                描述                                        |
| ------------- | -------------------------------------------------------------------------- |
| FPS           | *帧率：* 每秒在屏幕上绘制多少帧。                                             |
| Ping (ms)     | 从服务器获得响应需要多长时间（往返时间）。                                     |
| PL (%)        | *丢包：* 有多少数据包未能及时到达。                                           |
| CPU Usage (%) | CPU利用率。                                                                 |
| GPU Usage (%) | 显卡利用率。                                                                |
| GPU Temp (°C) | 显卡的摄氏温度。                                                            |

示例： `cl_drawperf <true|false>`

### quit
将强制客户端立即关闭。

### quit [reason]
将强制客户端立即关闭，向服务器指定退出原因。

### loadlevel \<level_name>
<!-- TODO: Needs an reference on how to use and/or setup the loadlevel command -->
从提供的名称开始本地游戏加载关卡（或通常称为地图）。

示例： `loadlevel gta5`, `loadlevel rdr3`, `loadlevel blank-map`.

### storymode
启动 FiveM 故事模式。

### profile_sfxVolume \<0-10+>
为游戏设置音效音量。该值没有上限，但下限为0，100%音量对应10。

### profile_musicVolume \<0-10+>
设置单人游戏模式下游戏的音乐音量。

### profile_musicVolumeInMp \<0-10+>
连接到网络游戏时设置游戏的音乐音量。

## Developer commands

开发人员指令要求客户端在开发人员模式下运行，否则它们将显示错误，例如`Access denied for command resmon`或者`Command strdbg is disabled in production mode`。

可以通过以下几种方式启用开发者模式：

1. 在任意版本上通过使用`+set moo 31337`参数启用FiveM&RedM客户端，比如将其添加为快捷方式。
2. 在非生产环境更新通道（例如 Beta 或 Latest）上运行客户端。请注意，其他更新渠道可能会不稳定并导致游戏无法启动等问题。

### cmdlist
`cmdlist`指令将列出在客户端（或服务器端）上注册的所有指令。它还会输出使用`set`、`sets`和`seta`指令设置的变量。

### con_miniconChannels
你可以使用`con_miniconChannels`指令在屏幕上显示控制台消息，而不需要打开客户端控制台。

频道名称是控制台消息旁边彩色框中的文本。消息过滤器对频道名称执行模式的*完全匹配*，这意味着它必须在开头或结尾没有任何额外字符的情况下匹配。
星号 (*) 可用于指定部分频道名称，作为0或more字符的占位符。多个模式可以使用空格或加号 (`+`) 组合。

示例： `con_miniconChannels <pattern>`

默认：`minicon:*`

示例模式：
- 所有消息：`*`
- 源自任意脚本资源的消息：`script:*`
- 来自`banking`和`racing`脚本资源的消息：`script:banking script:racing`

### developer
为开发人员启用一些附加的日志记录。通常对普通用户没有用。

示例： `developer <true|false>`

### devgui_cmd \<path> \<command>
向控制台上方显示的开发人员 GUI 添加指令。

示例： `devgui_cmd "Launch/MP/Disconnect" "disconnect"`

### devgui_convar \<path> \<variable>
向控制台上方显示的开发人员 GUI 添加一个 convar。

示例： `devgui_convar "Game/SFX Volume" profile_sfxVolume`

### invoke-levelload
`loadlevel`的别名，详见[loadlevel](#loadlevel)指令。

### list_aces
<!-- TODO: probably needs a reference to an explanation for ACL stuff -->
列出控制台中的所有 ace（访问控制项）。它创建一个主体和对象之间关系的列表，以及是否允许或不允许使用它。 示例输出：

```
builtin.everyone -> command.freecam = ALLOW
group.admin -> command.testbed = DENY
<rest of the aces...>
```

### list_principals
<!-- TODO: probably needs a reference to an explanation for ACL stuff -->
列出系统中所有的principal，它会打印出哪些principals被其他人继承的列表。 示例输出：

```
identifier.steam:110000111111111 <- group.admin
identifier.steam:110000111111112 <- group.moderator
<child> <- <parent>
```

左侧是属于右侧父节点的子节点。

### localGame \<name>
<!-- DOCTODO: document this concept -->
在单人模式中从`usermaps:/resources/[name]`加载本地资源。

### localRestart
重新启动本地游戏资源。

### modelviewer
允许你通过图形界面加载 TXD 和可绘制对象。

示例： `modelviewer <true|false>`

### net_maxPackets
一个配置标志，告诉客户端它应该至少每秒发送多少个数据包。

默认值为 50，最小值为 1，最大值为每秒 200。

示例： `net_maxPackets <number_of_packets>`

### net_printOwner \<objectID>
打印网络对象标识的所有者。

### net_showCommands
内部开发工具。 除非要求运行，否则对普通用户无用。

### net_showDrilldown
内部开发工具。 除非要求运行，否则对普通用户无用。

### net_showTime
内部开发工具。 除非记录状态感知数据，否则对普通用户无用。

### netEventLog
启用一个工具来显示所有网络流量事件。

此指令将显示所有传入/传出流量事件。它显示了事件的方向（例如服务器端 -> 客户端）、事件名称和发送数据的大小（例如 2 bytes）。

示例： `neteventlog <true|false>`

### net_statsFile
`net_statsFile` 是存储 FiveM 客户端网络使用/行为指标的命令。

它应该跟踪诸如 ping、接收的数据包和字节、发送的数据包和字节以及路由包的数量等指标。所有这些信息都将使用 CSV 格式存储在一个文件中。

示例： `net_statsFile <file_name>`

示例： `net_statsFile metrics.csv` - this will create a CSV file called `metrics.csv` in your
FiveM [application data directory][faq-data].

### netgraph
`netgraph`命令将为你提供关于 FiveM 客户端网络使用情况的实时指标。
netgraph 由一个图表和关于网络的基本信息组成：

| 字段名称     |                             描述                                      |
| ----------- | --------------------------------------------------------------------- |
| ping        | 从服务器获得响应需要多长时间（往返时间）                                  |
| in          | 我们每秒接收了多少数据包。                                               |
| in (bytes)  | 我们每秒接收了多少字节。                                                 |
| out         | 我们每秒发送了多少数据包。                                               |
| out (bytes) | 我们每秒发送了多少字节。                                                 |
| rt          | 路由接收/发送的数据包。                                                  |
| rd          | 路由数据包 **延迟**。                                                   |

该图表示已发送或接收了多少特定类型的数据包。

示例： `netgraph <true|false>`

### netobjviewer
当启用游戏状态感知时，显示当前通过网络同步的对象和节点列表。

示例： `netobjviewer <true|false>`

### netobjviewer_syncLog
用于诊断书面游戏状态的差异。 对普通用户没有用。

### nui_devtools
从游戏进程中打开 NUI 开发工具窗口。

### onesync_logFile \<filename>
用于从游戏状态感知子系统中保存客户端日志。这些文件会变得很大，因此应谨慎使用此命令。

示例： `onesync_logFile "1s_today.log"; wait 5000; onesync_logfile ""`

### r_disableRendering
用于支持内部模具。对普通用户没有用，也不能在运行时切换。

### resmon
resmon 命令将打开资源监视器。资源监视器监视每个资源的 CPU 使用率和内存使用率，并在概览中显示。当你在游戏过程中遇到性能问题时会派上用场。

示例： `resmon <true|false>`

### save_gta_cache
<!-- TODO: reference a guide on GTA cache and using it in a resource -->
将指定资源的缓存数据保存到AppData中的CitizenFX目录。这将用于具有大量碰撞或地图文件的资源，以加速玩家的初始加载。

示例： `save_gta_cache <resource name>`

### se_debug
`se_debug`命令启用安全功能（如 ACL）的详细日志记录。

示例： `se_debug <true|false>`

有助于了解为什么有些人可以或不能访问某些命令，示例输出：
```
TEST ACL [system.console -> command.resmon] ACE [system.console command] -> ALLOW
TEST ACL [system.console -> command.resmon] -> ALLOW
```

### set
在客户端设置一个变量。

示例： `set <key> <value>`

示例：
```
set animal snail

animal
  "animal" is "snail"
  default: ""
  type: string
```

### seta
在客户端上设置存档变量。
变量保存在`%AppData%\CitizenFX\fivem.cfg`和`%AppData%\CitizenFX\redm.cfg`中。

示例： `seta <key> <value>`

示例：
```
seta food escargot

food
  "food" is "escargot"
  default: ""
  type: string
```

### strdbg
`strdbg`可用于查看 GTA 流媒体中当前正在加载的内容，以潜在地发现与流式传输某些项目有关的任何问题，例如当世界停止加载时。

示例： `strdbg <true|false>`

### strlist
`strlist` 是一个图形界面，显示 GTA 流媒体中注册的条目及其当前状态。

Usage `strlist <true|false>`

### strmem
显示特定流媒体资源使用的流媒体内存列表，以及全局概览。

示例： `strmem <true|false>`

### test_ace
测试是否允许或拒绝主体访问给定对象。

示例： `test_ace <principal> <object>`

示例： `test_ace group.admin command.adminstuff`

[faq-data]: /docs/support/client-faq#where-is-fivem-installed
[vconsole]: https://forum.cfx.re/t/20005
