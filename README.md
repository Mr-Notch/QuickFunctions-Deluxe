# QuickFunctions
一个基于Forge的多功能基础系统MOD —— A useful, powerful mod by Forge

搭配HGRCarpet使用更佳
这是一个基于Forge的多功能基础系统MOD。集成定点备份、请求传送、格式化聊天栏、placeholderAPI变量、@以及更多实用的指令与功能

该MOD的配置文件在config/quickfunc/conf.json内，配置文件内容请等待第一个Beta版本。

下面是对于每一种功能的详细介绍以及教程：

#1. 定点备份与回档：
（备份目录在config/quickfunc/backup文件夹内）

  #/qf backup make <slot> <locate> <zipped> —— 立即执行备份操作。
   <slot>栏目可以为备份后的文件/文件夹名称 不填则以当前时间来命名（例如2020_3_16_13_35.zip）
   <locate>栏目可以指定备份哪一个文件/文件夹，其根路径为服务端根目录，不填为全局备份（备份根目录下所有文件，除该MOD的备份文件夹）
   <zipped>栏目只能填布尔值（true/false），意为是否以.zip格式压缩 不填则默认true
  #/qf backup repo <slot> <restarted> —— 立即执行回滚操作。
   <slot>栏目是/qf backup make <slot>中所写入的值。可以在任意一个执行了上一条指令后备份的文件内进行回滚
   <restarted>栏目只能填布尔值（true/false），意为在回滚完成后是否执行重启操作（如果填写false则回滚需在手动重启后方可生效）不填默认true
  #/qf backup confirm —— 确认执行备份/回滚操作。
  /qf backup list <page> —— 列出当前备份目录所有的备份节点。
   <page>栏目是当list内容过多时翻页的，页数取决于备份目录中备份节点的数量
  #/qf backup auto <time> <locate> <zipped> —— 启动定时备份功能。
   <time>栏目是规定间隔多长时间备份一次，单位为游戏刻（GameTick, gt），其余参数与/qb backup make相同（不包含<slot>. 自动备份下的文件/文件夹将强制以时间进行命名，例如2020_3_16_13_35.zip）
  #/qf backup stopauto —— 停止自动备份。
  #/qf backup delete <slot> —— 删除备份文件夹内的某个备份。
   <slot>栏目为备份后的文件/文件夹名称
  #/qf backup diskprotect <bool_value> <value>—— 是否开启硬盘保护功能。 
   <bool_value> 只能为布尔值（true/false），意为是否开启该功能，当值位于false时，后面的所有参数将无效
   <value>栏目只能为单位字节（例如5GB、5KB、10MB等），意为当硬盘空间小于此值时触发保护功能
   硬盘保护意为防止备份项目过多导致磁盘爆满。当磁盘空间小于<value>规定的大小时，自动备份将停止，手动备份会提示“是否删除最早的备份以此来空出该备份所需的磁盘空间”并会让执行指令的终端进行/qf backup confirm确认操作
  
#2. 请求传送、接受传送与拒绝传送：
 
  #/qf tpafunc <bool_value> —— 是否开启请求传送功能
   <bool_value> 只能为布尔值（true/false），当值位于false时，以下所有指令全部无效
  #/tpa <player> —— 向该玩家发送一个传送请求。
   <player>栏目只能为玩家实体。控制台、命令方块发出的该指令无效
  #/tpaccept —— 接受传送请求。
  #/tpadeny —— 拒绝传送请求。

#3. 格式化聊天栏与@<player>：
  （该功能的详细配置在config文件内可以找到）
  
  #/qf chatfunc <bool_value> —— 是否开启格式化聊天
   <bool_value> 只能为布尔值（true/false），当值位于false时，客户端会遵循Minecraft的聊天格式而不是QuickFunctions的格式
  #/qf mute <bool_value> —— 是否开启全局禁言
   <bool_value> 只能为布尔值（true/false），当值位于true时，玩家发送除指令外所有的内容将全部屏蔽（在客户端表现为发送文字后聊天栏无任何反应），但玩家依然可以使用/say、/tell(raw)、/title等指令来说话（如果他有这些指令使用权限的话）
  <chat>@<player> <chat> —— 在聊天栏内@一位玩家
   <chat>栏目是玩家要发送的上下文（包含空格、无字符。在@<player>结束后必须加一个空格才能接着剩下的语句。否则MOD将无法识别@内容）
   <player>栏目只能为玩家实体。
   当MOD成功识别后，被@的玩家会有一个“note_pling”的提示音，并在聊天栏内会看到@部分呈翠绿色的高亮（&a格式）
  
#4. placeholderAPI支持（暂未更新）：
  （该功能暂且未在beta版本中加入）
  
#5. 快速发送bossbar、actionbar、subtitle等位置的文字：
  #/qf bossbarmsg <msg> <time> <barcolor> —— 发送一个BOSS血条消息
   <msg>栏目是想要发送的文字，支持&转义符、JSON格式（当系统检测到JSON格式中有time规定的值时，<time>栏目将失效）。
   <time>栏目为BOSS血条持续的时间，单位为游戏刻（GameTick, gt）
   <barcolor>栏目为血条颜色，只能为JSON格式
  #/qf actionbarmsg <msg> —— 发送一个唱片条消息
   <msg>栏目是想要发送的文字，支持&转义符、JSON格式。
  #/qf subtitlemsg <msg>
   <msg>栏目是想要发送的文字，支持&转义符、JSON格式。若不规定渐变时间、持续时间，系统默认会以“10 20 10”的格式放送。
  
#6. 快速寻找史莱姆区块、生物群系：
  #/qf slimefinder <radius> —— 以玩家为中心寻找史莱姆区块
   <radius>栏目意为半径，规定一个圆，圆心为玩家中心。半径为单位格（一个方块长度=1）
  #/qf biomefinder <biome> <radius> —— 以玩家为中心寻找规定的生物群系
   <biome>栏目只能输入生物群系名称，输入其他则无效
   <radius>栏目意为半径，规定一个圆，圆心为玩家中心。半径为单位格（一个方块长度=1）
   若该范围内存在两个或两个以上生物群系，MOD将自动选择一个离玩家最近的生物群系进行输出坐标
  
#7. 模糊指令：
  （该部分请参考config文件fuzzycommands部分，在这里不做过多赘述）

#8. 服务器指标查询：
  #/qf healthreport —— 发送一个服务器健康报告。
   详细内容请参考config中的healthreport部分
  
#9. 在游戏内控制服务器后台、查询服务端根目录文件（暂未更新）：
  （该功能暂且未在beta版本中加入）
  
  #/qf panelmode <player> —— 将某个玩家切换至控制台模式
   <player>栏目只能为玩家实体，若留空将给操作者本身开启控制台模式。
  #/qf exitpanel <player> —— 退出控制台模式
   <player>栏目只能为玩家实体，若留空将给操作者本身退出控制台模式。
  #/qf lookupfile <page> —— 列举服务器根目录所有文件
   <page>栏目是当list内容过多时翻页的，页数取决于根目录文件的数量
  #/qf file open <locate> —— 打开某个文件
   <locate>为文件名称，打开文件需要带后缀（例如config/quickfunc/conf.json）
  #/qf file backspace <locate> —— 回退至某个路径
   <locate>为文件夹路径，需填写局部路径（从服务端根目录开始），留空代表本目录
  #/qf file cd <locate> —— 前往某个文件夹
   <locate>为文件夹路径，需填写局部路径（从服务端根目录开始），留空代表本目录
  #/qf file ls <locate> —— 列举某个路径内的文件/文件夹
   <locate>为文件夹路径，需填写局部路径（从服务端根目录开始），留空代表本目录
  #/qf file zip <locate> <value> —— 处理一个.zip格式的压缩包
   <locate>为文件路径，需填写局部路径（从服务端根目录开始），留空无效
   <value>遵循Linux加解压缩参数，具体请自己CSDN
  #/qf file tar <locate> <value> —— 处理一个.tar(.gz)格式的压缩包
   详细内容与上一条指令相同，故此不做过多赘述
  #/qf file delete <locate> —— 删除一个文件/文件夹
   <locate>为文件夹路径，需填写局部路径（从服务端根目录开始），留空无效
   是否有回收站需要根据服务端宿主系统决定
   删除内容属于敏感指令，需要使用/qf file confirm确认操作
  #/qf file confirm —— 确认执行
  
#10. LOG日志与监测系统：
  （日志文件在config/quickfunc/logs内可以找到，命名格式为时间_格式，例如2020_3_16_15_09_all.txt）

  #/qf log <bool_value> —— 是否开启日志记录模式
   <bool_value> 只能为布尔值（true/false），当值位于false时，以下所有关于日志的指令均无效
  #/qf log <mode> —— 规定记录模式
   <mode>栏目有：all, debug, develop, server, player。默认情况下是all
   all模式：该模式会记录除debug之外的所有事件。
   debug模式：会记录所有Minecraft、Forge以及Netty的事件，其他事件不记录
   develop模式：相当于debug的升级版。除了记录debug内的东西之外，还会记录聊天、指令、命令方块、datapacks、functions的执行操作，包含此MOD的任务
   server模式：与根目录的logs记录方法相同，遵循Minecraft的日志写法
   player模式：仅记录玩家的聊天、指令，与方块的交互以及登入登出、IP地址信息
  
#11. 自动重启：
  #/qf autorestart <time> <msgswitch> —— 规定自动重启间隔
   <time>栏目是规定间隔多长时间重启一次，单位为游戏刻（GameTick, gt）
   <msgswitch> 只能为布尔值（true/false），意为是否开启重启倒计时警告系统
   倒计时警告文字与计时器可以在config文件autorestart部分找到
  #/qf stopautorestart —— 停止自动重启
  
...更多功能 敬请期待...
与HGRCarpet搭配更佳
目前仅开发1.13.2Forge版本，预计未来会开发1.14+的Fabric版本。
 
