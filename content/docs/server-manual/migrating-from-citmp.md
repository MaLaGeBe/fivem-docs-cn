---
title: 从 CitizenMP.Server 迁移
weight: 360
description: >
  有一些旧版服务器端吗？这是一个迁移指南。
---

### 加载脚本

`require` 已弃用，任何脚本/库都应该使用资源清单中的 `server_script` 指令来加载。

示例：

``` lua
server_script "my_script.lua" -- load script
server_script "my_lib.net.dll" -- load a particular assembly into the .net appdomain
server_script "@resource_name/script.lua" -- load a script from another resource
```

要在运行时加载文件，可以使用 [LOAD\_RESOURCE\_FILE]({{% native "LOAD_RESOURCE_FILE" %}}) (`LoadResourceFile("resource_name", "file_name")`)，如果它是一个Lua文件，则可以使用。

``` lua
load(...)
```

加载 Lua 代码，示例如下：

``` lua
function loadLuaFile(resource, file)
    return load(LoadResourceFile(resource, file), file)()
end
```

### 拆分字符串 / String Splitting

`str:Split`已弃用，你应该为此使用正确的 Lua 函数。参考如下`stringsplit`函数。

``` lua
function stringsplit(inputstr, sep)
    if sep == nil then
        sep = "%s"
    end
    local t={} ; i=1
    for str in string.gmatch(inputstr, "([^"..sep.."]+)") do
        t[i] = str
        i = i + 1
    end
    return t
end
```

### 按位运算 / Bitwise Operations

Lua 5.3 弃用了`bit32`，CfxLua 运行时也不再运行它。与其他大多数编程语言一样，按位运算现在可以使用普通运算符(`&`, `|`, ...)。

### CLR

NeoLua 已弃用，因此 clr 命名空间不再存在。如果需要运行 C\# 代码，请使用普通的 .NET 运行环境进行服务器端导出。

### TempIDs

如果您在执行`playerConnecting`期间进行了任何特定的按位运算，则假设`source`值大于0x10000，那么在`playerConnecting`期间使用函数就不再需要了。
