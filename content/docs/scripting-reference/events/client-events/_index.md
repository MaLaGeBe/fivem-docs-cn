---
title: 客户端事件
weight: 541
layout: single
---

**可在脚本中使用的一些客户端事件列表。**

核心事件
-----------
这些事件是 FiveM 的一部分，不需要任何脚本资源。

{{% events "client" %}}

spawnmanager 事件
-------------------
这些事件是 [spawnmanager](/docs/resources/spawnmanager) 脚本资源的一部分。

- [playerSpawned](/docs/resources/spawnmanager/events/playerSpawned)

mapmanager 事件
-----------------
这些事件是 [mapmanager](/docs/resources/mapmanager) 脚本资源的一部分。

- [onClientMapStart](/docs/resources/mapmanager/events/onClientMapStart)
- [onClientGameTypeStart](/docs/resources/mapmanager/events/onClientGameTypeStart)
- [onClientMapStop](/docs/resources/mapmanager/events/onClientMapStop)
- [onClientGameTypeStop](/docs/resources/mapmanager/events/onClientGameTypeStop)
- [getMapDirectives](/docs/resources/mapmanager/events/getMapDirectives)

baseevents 事件
-----------------
这些事件是 [baseevents](/docs/resources/baseevents) 脚本资源的一部分。

- [onPlayerDied](/docs/resources/baseevents/events/onPlayerDied)
- [onPlayerKilled](/docs/resources/baseevents/events/onPlayerKilled)

sessionmanager 事件
---------------------
这些事件是 [sessionmanager](/docs/resources/sessionmanager) 脚本资源的一部分。

- [playerActivated](/docs/resources/sessionmanager/events/playerActivated)
- [sessionInitialized](/docs/resources/sessionmanager/events/sessionInitialized)

chat 事件
-----------
这些事件是 [chat](/docs/resources/chat) 脚本资源的一部分。

- [chatMessage](/docs/resources/chat/events/chatMessage)
- [chat:addMessage](/docs/resources/chat/events/chat-addMessage)
- [chat:addTemplate](/docs/resources/chat/events/chat-addTemplate)
- [chat:addSuggestion](/docs/resources/chat/events/chat-addSuggestion)
- [chat:removeSuggestion](/docs/resources/chat/events/chat-removeSuggestion)
- [chat:clear](/docs/resources/chat/events/chat-clear)
