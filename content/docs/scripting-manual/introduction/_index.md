---
title: 脚本编写简介
weight: 410
layout: single
---

这是一个快速信息表，可帮助你加快 FiveM 开发的速度。

# SCRT 是什么意思?
_ScRT_ 表示 _Scripting Runtime_ 或 _Script Runtime_。FiveM 有三种不同的脚本运行环境可用（Lua、C# 和 JavaScript），下面提到了它们。

# 我如何开始编写脚本？
可以在[此处](/docs/scripting-manual/)找到脚本手册，其中包含以下文章：

- [脚本资源介绍](/docs/scripting-manual/introduction/introduction-to-resources)
    - [创建你的第一个脚本](/docs/scripting-manual/introduction/creating-your-first-script)
- [脚本运行环境](/docs/scripting-manual/runtimes)
    - [在 Lua 中编写脚本](/docs/scripting-manual/runtimes/lua)
    - [在 JavaScript 中编写脚本](/docs/scripting-manual/runtimes/javascript)
    - [在 C# 中编写脚本](/docs/scripting-manual/runtimes/csharp)
- [从已弃用的方法迁移](/docs/scripting-manual/migrating-from-deprecated)
  - [Chat Messages](/docs/scripting-manual/migrating-from-deprecated/chat-messages)
- [处理事件](/docs/scripting-manual/working-with-events)
  - [监听事件](/docs/scripting-manual/working-with-events/listening-for-events)
  - [触发事件](/docs/scripting-manual/working-with-events/triggering-events)
- [NUI](/docs/scripting-manual/nui-development)
- [使用 Scaleform](/docs/scripting-manual/using-scaleform)

您可以参考上面提到的页面以查看完整的脚本编写手册。

# 原生函数
## 什么是原生函数？
简而言之，原生函数(Native)是游戏公开的函数，以便从脚本中调用并在游戏本身中执行给定操作或从中请求数据。例如，可以输入以下内容，从 Lua 脚本中获取本地玩家的角色(pet)，然后为该角色提供武器。

```lua
ped = GetPlayerPed(-1)
GiveWeaponToPed(ped, GetHashKey("WEAPON_PISTOL"), 100, false, false) -- 获得了一把手枪
```

## 原生函数可以在哪里看到？
[请点此查看全部原生函数](https://docs.fivem.net/natives/)。

# 开发者指令和游戏参考资料
## 所有的开发者指令在哪里查看？
[点此查看](/docs/client-manual/console-commands/#developer-commands)开发人员指令。

## 所有的标点、角色模型和其他东西在哪里？
这些内容被命名为 _游戏参考资料_，[请点此查看](/docs/game-references)。

# 性能
## 什么是故障警告(warnings)?
故障警告表明你的某个资源没有正常运行，你应该查看受影响的资源以找出原因，_使用探查器可以帮助诊断这一点_。诸如此类的事情有时可能是由于编写了需要很长时间才能执行的性能不佳的 SQL 查询，以及最终导致脚本执行停止的未优化循环。

## 调试分析器 (Profiler)
调试分析器可用于诊断资源执行时间 _为什么_ 过长，有一份[指南](/docs/scripting-manual/debugging/using-profiler) 解释了如何使用它，它可以在服务器和客户端上使用。

## 资源监视器 (Resmon)
资源监视器可用于客户端诊断哪个资源执行时间过长，它显示某些信息，例如每个资源的 cpu 使用情况（毫秒）和内存使用情况。

可以通过键入`resmon true`来启用它。你可能会看到一条消息，例如`Access denied for command resmon` (特别是在生产构建中运行时)，这意味着需要通过使用`+set moo 31337`参数启动 FiveM/RedM 客户端来启用开发者模式（例如，通过将其添加为快捷方式）。