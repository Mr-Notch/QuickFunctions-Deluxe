# QuickFunctions Deluxe

**更卓越的 Minecraft 服务端扩展 Mod 兼守护程序**

**QuickFunctions Deluxe 适用于：**

- 各种基于 Fabric 的生电原版服
- 高版本 FabricMod 模组服



**感谢 Fallen-Breath 的 MCDReforged 与 HGR-Community 的 QuickFunctions**

- Fallen-Breath MCDR 直达站：[点击跳转](https://github.com/Fallen-Breath/MCDReforged "点击跳转")
- HGR-Community QF 直达站：[点击跳转](https://gitee.com/Mr_Notch/QuickFunctions "点击跳转")



## 说明索引目录

在使用 QuickFunctions Deluxe 之前，务必阅读完毕以下内容

[TOC]

## QuickFunctions Deluxe 的优点

> 为什么要选择 QuickFunctions Deluxe？（以下简称QFD）
>
> QFD 与 MCDR 的区别是什么？
>
> 使用 QFD 的好处是什么？

- **原版特征：**QuickFunctions Deluxe 基于 JavaSDK 编写，使用 FabricAPI 作为主类，并使用 Mixin 直接注入原版代码，没有任何干预原版进程，保证原汁原味的原版特性

- **MCDR 插件兼容性：**QuickFunctions Deluxe 兼容 80% 的 MCD 或 MCDR 插件，并且支持无缝将 MCDR 环境一键转换至 QFDP（QuickFunctions Deluxe PythonAPI） 环境
- **Scratch 编写：**QuickFunctions Deluxe 支持使用类似 Scratch 一样的积木式编程 UI 进行编写 QFD 脚本，让开发变得简单易懂，仅需简单鼠标拖拽即可实现大部分功能
- **全部可控式开关：**QuickFunctions Deluxe 将所有功能全部使用布尔值开关在 Config 文件中，使用者可以轻易地进行开关任何一个功能
- **GPL-3.0 开源协议：**QuickFunctions Deluxe 所有源代码全部在 GitHub 上开源，开发者可以直接修改源代码修改成适合自己服务器的 QFD 版本，无需向 QFD 开发组申请



## 构建方法、安装说明以及使用简要

> 如何构建 QFD？如何使用 QFD 的工具包？在安装完成后第一次使用需要注意什么？



### 如何在 GitHub 上构建 QuickFunctions Deluxe：

- Windows：使用 Git 构建工具直接从以下链接 Clone

- Linux：直接使用 git 指令从以下链接 Clone

  > https://github.com/Mr-Notch/QuickFunctions-Deluxe.git

  

### 如何给自己的服务端安装 QuickFunctions Deluxe：

在安装之前，需要注意以下事项：

1. 确保自己的服务端 API 为 FabricAPI
2. 确保自己的 FabricAPI 游戏版本在 1.15.2 及其以上
3. 确保自己已经安装 Fabric-Carpet

确认以上三点以后，您就应该可以进行安装 QuickFunctions Deluxe 了

**安装方法：**

- 直接将 fabric-qfd-version-snap.jar 文件粘贴到服务端目录下的 ./mods 文件夹内

- 启动一次服务端，此时应该会在 ./config 文件夹内看到 ./qfd 文件夹，并且该服务端不会成功启动

- 前往 ./config/qfd 文件夹，此时应该会看到类似以下的目录结构：

  ```
  ,/config/qfd
  ├─ functions/ -> 该目录下存放 QFD 的脚本文件
  │  ├─ xxx1-version-func.jar
  │  ├─ xxx2-version-func.jar
  │  └─ ...
  │
  ├─ mcdps/ -> 该目录下存放处于兼容模式运行的 MCDR 插件
  │  ├─ xxx1.py
  │  ├─ xxx2.py
  │  └─ ...
  │
  ├─ config/ -> 该目录下存放 QFD 的配置文件
  │  ├─ main.json
  │  ├─ switch.json
  │  ├─ functions.json
  │  ├─ methods.json
  │  ├─ events.json
  │  └─ messages/ -> 这是 QFD 的语言文件
  │     ├─ zh_cn.json
  │     ├─ en_us.json
  │     └─ ...
  │
  ├─ mixins/ -> 该目录下存放 QFD 的注入表
  │  ├─ lib-qfdfunc-snap.jar
  │  ├─ xxx-name-version.jar
  │  └─ ...
  │
  ├─ tools/ -> 该目录下存放 QFD 的开发者工具
  │  ├─ scratch-editor.jar
  │  ├─ version-changer.jar
  │  └─ ...
  │
  └─ readme.md
  ```



- 若确认 ./qfd 文件夹内的文件格式类似如上，那么可以进行下一步操作；

  若 ./qfd 文件夹为空或未找到，请核对上述 1-2 步骤（检查版本并确认服务端是否正常工作）

- 前往 ./config.json 文件夹，找到以下行，并根据宿主机物理环境进行填写

  > 原文件对照行

  ```
  # 这里为宿主机运行系统环境的填写，以便于 QFD 进行合理识别
  # Windows 或 DOS 内核的：0
  # Linux、macOS 等 UNIX 内核的：1
  
  os {
  	files {
  		backup=0
  		review=0
  		target=0
  		command=0
  	}
  	time {
  		format=0
  	}
  }
  ```

  

- 确认无误后使用快捷键 Ctrl+S 保存，并再次尝试启动 Minecraft 服务端

- 此时，在后台输出应该有类似代码片段：

  ```
  [16:51:28] [Server thread/INFO]: QuickFunctions Deluxe Loader
  [16:51:28] [Server thread/INFO]: *Successfully injected*
  [16:51:28] [Server thread/INFO]: Server Version: 1.16.2
  [16:51:28] [Server thread/INFO]: QFD Version: SNAP
  [16:51:28] [Server thread/INFO]: 
  [16:51:28] [Server thread/INFO]: QuickFunctions Deluxe Hooker
  [16:51:28] [Server thread/INFO]: Carpet Hooked!
  [16:51:28] [Server thread/INFO]: FabricAPI Hooked!
  [16:51:28] [Server thread/INFO]: Minecraft Mixin Hooked!
  [16:51:28] [Server thread/INFO]: 
  [16:51:28] [Server thread/INFO]: Now continue to start server...
  [16:51:28] [Server thread/INFO]: 
  ```

  

- 若有错误，一般为上一步步骤填写错误，请认真核对重新填写并重启服务端

- 确认无误后，使用 Minecraft 客户端（无需在客户端加入 QFD）进入服务端，并以 OP 权限运行指令：

  > /shoo

- 此时，在玩家窗口应该会弹出 完成挑战 “成功加载 QuickFunctions Deluxe”，并且会在聊天窗口反馈一些内容

- 这时，QuickFunctions Deluxe 已经正式初始化完毕



**我的服务端已经有 MCDR 了，我该怎么将兼容的 MCDR 插件加载到 QFD 里：**

- 前往服务端根目录 ./config/qfd/tools 文件夹，并寻找到 mcdr-hooker.jar 文件

- 双击该文件，Windows 或 macOS 会弹出 UI，而 Linux 等命令行则会弹出命令行光标界面

  **Windows 操作步骤：**

  - 将 MCDR 所在的目录填入第一个方框
  - 将 MCDR 与 Minecraft 版本填入第二个与第三个方框
  - 点击 “Hook Now” 按钮并等待 Hook Successfully 字样的出现

  **Linux 命令行操作步骤：**

  - 使用上下左右键移动光标高亮，同样地，将三个参数填入三个方框中
  - 使用光标瞄准按钮 “Hook Now” 并等待 Hook Successfully 字样的出现
  - 使用光标瞄准按钮 “Exit” 即可退出命令行界面



### 常用指令与函数方程式参数代入方法

使用 QFD，仅需要记住以下简单指令即可实现大部分操作

如需查询详细指令，请查看 commands.md 文件

- 获取帮助：

  > /qfd help

  此时会反馈一个含有详细指令操作的消息

  常用指令如下所示：

  - /qfd backup - 备份指令操作
  - /qfd func - 函数指令操作
  - /qfd player - 玩家指令操作
  - /qfd hooker - 与其他 Mod 的挂钩
  - /qfd server - 服务端指令操作
  - /qfd client - 客户端指令操作
  - /qfd mixins - 注入表
  - /qfd mcdrp - MCDR 插件操作（支持热重启）
  - /qfd reload - 重载指令操作

