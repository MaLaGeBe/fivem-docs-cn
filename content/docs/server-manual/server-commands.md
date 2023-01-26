---
title: 服务器端指令
weight: 330
description: >
  在服务器控制台中运行的指令列表。
---

<!-- TODO: format this like client commands? -->

可以使用 RCon 工具直接从服务器控制台界面、服务器配置文件、服务器命令行或使用[ExecuteCommand]({{% native "EXECUTE_COMMAND" %}})函数（如果 ACL 允许该资源）执行控制台命令。

添加自定义 RCon 命令可以使用服务器上的 [RegisterCommand]({{% native "REGISTER_COMMAND" %}}) 函数或`rconCommand`事件（旧版）来完成。

## 脚本资源指令

### `start [脚本资源名称]`

如果未运行，则启动参数中指定的资源。也可以指定一个类别名称，例如`start [cars]`。

示例：

    start lambda-menu
    start [cars]

### `stop [脚本资源名称]`

停止参数中指定的资源（如果它已启动）。与 `start` 一样，也可以指定类别名称。

示例：

    stop mymode

### `ensure [脚本资源名称]`

Restarts the resource specified in the argument, if it was started. If it wasn't, starts the resource specified in the argument.

As with `start` and `stop`, one can also specify a category name.

示例：

    ensure my-testing-resource

### `restart [脚本资源名称]`

Restarts the resource specified in the argument, if it was started. Also supports category names.

示例：

    restart lambda-menu

### `refresh`

Rescans the *resources* folder and loads all resource manifests in them, also making new resources available to start using [start](#start-resourcename "wikilink").

示例：

    refresh

## 全局指令

### `exec [filename]`

Runs the commands specified in the filename, relative to the server data directory, or any resource name specified with `@`.

Commonly seen as `FXServer.exe +exec server.cfg`.

示例：

    exec server_nested.cfg
    exec @vMenu/config/permissions.cfg

### `quit`

Exits the server, sending a default quit message to all connected players.

### `quit [reason]`

Exits the server, also sending the specified reason to all connected players.

示例：

    quit "Restarting - will be back soon!"

## 管理指令

### `status`

{{% alert theme="info" %}}This is provided by the **rconlog** resource. {{% /alert %}}

Shows a list of players with their primary identifier, server ID, name, endpoint, and ping.

示例：

    status

### `clientkick [id] [reason]`

{{% alert theme="info" %}}This is provided by the **rconlog** resource. {{% /alert %}}

Kicks the client with the specified server ID (as seen in [status](#status "wikilink")) from the server, for the stated reason.

示例：

    clientkick 43 You're a superstitious idiot!

### `say [message]`

{{% alert theme="info" %}}This is provided by the **chat** resource. {{% /alert %}}

Sends a message in the chat as *console*.

示例：

    say Hi, everybody!

### `svgui`

Opens or closes the server debug GUI.

## 配置变量

### `gamename [game]`

Defines the game to run the server for.

示例：

    FXServer.exe +set gamename rdr3

#### 支持的游戏
| 名称 |   正式名称   |
| ---- | ------------------- |
| gta4 | LibertyM for GTA:NY |
| gta5 | FiveM for GTA:Five  |
| rdr3 | RedM for RDR3       |

### `onesync [on/off/legacy]`

Defines which mode of state awareness to use.

* **Off**: No state awareness at all, clients will use the standard GTA/RAGE P2P networking model, and the server will only function as a relay.
* **On**: Full state awareness and server-determined entity routing.
* **Legacy**: Compatibility mode for scripts that expect all players to exist on each client. Not recommended due to performance issues and graphical glitches.

### `sv_enforceGameBuild [build]`

Selects a game build for clients to use. This can only be specified at startup, and can not be changed at runtime.

示例：

    sv_enforceGameBuild h4
    sv_enforceGameBuild mptuner
    sv_enforceGameBuild 1355

Every build includes all content and changes from the builds before.

**FiveM builds**

| Number |               Aliases                |       Marketing name        |
| ------ | ------------------------------------ | --------------------------- |
| 1604   | xm18, christmas2018, mpchristmas2018 | Arena War                   |
| -      | -                                    | The Diamond Casino & Resort |
| -      | -                                    | Diamond Casino Heist        |
| 2060   | sum, mpsum                           | Los Santos Summer Special   |
| 2189   | h4, heist4, mpheist4                 | Cayo Perico Heist           |
| 2372   | tuner, mptuner                       | Los Santos Tuners           |
| 2545   | security, mpsecurity                 | The Contract                |
| 2612   | mpg9ec                               | -                           |
| 2699   | mpsum2                               | The Criminal Enterprises    |
| 2802   | mpchristmas3                         | Los Santos Drug Wars        |

**RedM builds**

| Number |                               Notes                               |
| ------ | ----------------------------------------------------------------- |
| 1311   | Mid 2020 update, not compatible with Red Dead Online licenses.    |
| 1355   | December 2020 update, works with newer game editions such as RDO. |
| 1436   | July 2021 update, includes new content from Blood Money DLC.      |
| 1491   | September 2022 update, limited content/changes.                   |

### `sv_maxClients [newValue]`

A variable that specifies the maximum amount of clients that the server can normally have, as an integer from 1 to 1024.

Values starting at 32 will require `onesync` to be set to `on` or `legacy`, and values above 64 will require `onesync` to be set to `on`.

### `sv_endpointPrivacy [newValue]`

A boolean variable that, if true, hides player IP addresses from public reports output by the server.

### `sets sv_projectName "project name"`

A string variable containing the name of your 'project', which would for example be the server's community. This should
be a name, not a list, nor should it contain tags.

Any non-compliant name will be cut off in the server list. <!-- Use our tool to check your name. -->

示例：

```bash
sets sv_projectName "Citizen Gaming"

# or if you are using a premium key, it can contain one color
sets sv_projectName "^6Citizen Gaming"
```

### `sets sv_projectDesc "project description"`

A string variable containing the description of your project. This should be written as a sentence.

示例：

```bash
sets sv_projectDesc "Your favorite drug deal simulation community!"
```

### `sv_hostname [newValue]`

A string variable that contains the server-specific host name. In addition to this, you may want to set `sv_projectName`
and `sv_projectDesc`.

### `sv_master1 [newValue]`

A string variable that can be used to set the server as "private", making it not possible to join by using the server browser UI (the server connect button will be disabled). In the past, this specific string variable dictated where heartbeats were sent and servers weren't listed if the address didn't point to FiveM's ingress address, this is no longer the case, the server will always post to the default server ingress on startup. In other words, this string variable **cannot be used to de-list a server from the master list.**

示例： 

```toml
sv_master1 ""
```

### `sv_authMaxVariance [newValue]`

**Variance** is how likely the user's id will change for a given provider (i.e. 'steam', 'ip', or 'license').

A console variable as an integer from 1-5 (default 5); from least to most likely to change.

### `sv_authMinTrust [newValue]`

**Trust** is how _unlikely_ it is for the user's identity to be spoofed by a malicious client.

A console variable as an integer from 1-5 (default 1); from least to most trustworthy (5 being a method such as external three-way authentication).

### `sv_filterRequestControl [mode]`

A console variable used to block `REQUEST_CONTROL_EVENT` routing based on a configurable policy.<br>
Supported modes for this variable are as follows:

- -1: Default, equivalent to 2 at this time, but will also warn in console.
- 0: Off. Also disables the routing bucket/entity lockdown-based policy.
- 1: Blocks control requests to entities controlled by players (currently, occupied vehicles only) that have existed for more than `sv_filterRequestControlSettleTimer` milliseconds (default `30000`) - hereafter referred to as 'settled'.
- 2: Blocks control requests to all entities controlled by players.
- 3: Blocks control requests to all entities controlled by players, and any 'settled' non-player entities.
- 4: Does not route `REQUEST_CONTROL_EVENT` whatsoever.

In addition, any mode but 'off' will have some additional checks as well:

- Control request events can't be routed across routing buckets.
- Control request events will always be blocked if the sender is in 'strict' entity lockdown mode, either by the global mode setting, or their routing bucket being set to such.

### `con_channelFilters`
The `con_channelFilters` command will list any active channel filters set to the end user.

A channel is the prefix of a console message, for 示例： `citizen-server-impl`, this channel will be displayed in brackets in the console followed by a message, i.e.

```
[citizen-server-impl] Found 44 resources.
```

Filters can be used to alter console output behavior.

Different actions exist to alter this behavior:

| Action  | Description |
| ------  | ---------------------------------------------------------- |
| noprint | Will stop anything from being printed at a trace listener level. |
| drop    | Will cause the output to be dropped at `Printfv`, so it won't reach any print listeners. |
| devonly | Will apply `drop` action behavior and will only drop the output if the [developer](/docs/client-manual/console-commands/#developer) command is set to `false`. |

Example output:
```
[cmd] forward:*/*: noprint
```

### `con_addChannelFilter [filter] [action]`
The `con_addChannelFilter` command will add a channel filter which can be used to filter console channel output. 

[Regex](https://en.wikipedia.org/wiki/Regular_expression) can be used for channel filters, this can be set through the `filter` command parameter.

Available actions are explained up [above](#con_channelFilters) (con_channelFilters command).

The example down below would stop any channel output coming from script names matching the given pattern.

So the following wouldn't show on the console: 

```
[script:gamemodePrefix-turfs]: Hello world!
[script:gamemodePrefix-derby]: This is a test.
```

示例： `con_addChannelFilter script:gamemodePrefix-* noprint`

### `con_removeChannelFilter [filter] [action]`
The `con_removeChannelFilter` command can be used to remove a channel filter, thus removing any previously applied actions (those applied via [con_addChannelFilter](#con_addChannelFilter)).

You can use [con_channelFilters](#con_channelFilters) to check for any active filters.

示例： `con_removeChannelFilter script:gamemodePrefix-* noprint`

### `sv_filterRequestControlSettleTimer [time]`

A console variable (default `30000` milliseconds) that allows you to set after how long (based on entity creation time in milliseconds) an entity should be blocked from a `REQUEST_CONTROL_EVENT`. This will only apply to filter request control modes [1 and 3](#svfilterrequestcontrol-mode), which are detailed under `sv_filterRequestControl` in this page.<br>

{{% alert color="warning" %}}
The **time** argument must be provided in milliseconds for this to work correctly.
{{% /alert %}}

### `sv_pureLevel [level]`

A console variable used to prevent users from using modified client files. There currently are two pure mode levels (1 and 2), an explanation for these levels can be found below:

- 1: Will block all modified client files except audio files and known graphics mods.
- 2: Will block all modified client files.

If modified files are installed in the FiveM folder, they will be ignored - if users however modified base game files, they will receive an error message telling them what file is modified.

### `load_server_icon [fileName.png]`

A console command which loads a specfied icon and sets it as the server icon. The icon needs to be a 96x96 PNG file.

示例：

```toml
load_server_icon "my-server.png"
```

### `rcon_password [password]`

Sets the RCon password. This being unset means RCon is disabled.

### `steam_webApiKey [key]`

Sets a [Steam Web API key](https://steamcommunity.com/dev/apikey), which is required to allow for Steam identifiers to be returned by the server.

## Access control commands

### `add_ace [principal] [object] [allow|deny]`

Adds an access control entry to the server's access control list.

示例：

```
add_ace group.admin command.potato allow
add_ace identifier.steam:110000112345678 command.apple deny
```

### `add_principal [child_principal] [parent_principal]`

Sets a principal to inherit from another principal.

示例：
```toml
# makes identifier.steam:110000112345678 inherit from group.admin
add_principal identifier.steam:110000112345678 group.admin
```

### `remove_ace [principal] [object] [allow|deny]`

Removes a specified ACE from the server's access control list.

示例：

```
remove_ace identifier.steam:110000112345678 command.apple deny
```

### `remove_principal [child_principal] [parent_principal]`

Removes a specified principal inheritance entry.

示例：
```
remove_principal identifier.steam:110000112345678 group.admin
```

### `test_ace [principal] [object]`
Tests if a principal is allowed or denied access to a given object.

示例： `test_ace group.admin command.adminstuff`
