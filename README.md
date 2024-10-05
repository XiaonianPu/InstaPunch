

# 基本介绍 - Introduction
InstaPunch® 是一款基于Python3开发的全生命周期定向运动多日赛成绩统计软件，主要由`InstaPunch® Reader`读卡客户端与`InstaPunch®`成绩统计客户端组成。

目前1.7.0-beta版本进行对外开放测试。该版本可以免授权直接使用`灰常越野`、`乐嘉体育`与`SPORTident`的计时器材。

![](/assets/about.png)
![](/assets/reader.png)


## 产品特点 - Highlights

### 跨平台
原生支持`MacOS`、`Linux`与`Windows`。MacOS版本已接入`Apple公证与签名服务`，未来将上架AppleStore。
![](/assets/macos.png)

### 通用性
定义了通用读卡数据传输协议（General Readout Transportation Protocol, GRTP），消除了不同品牌的硬件在表达、传输、存储上的差异，做到了大而全的兼容与良好的可拓展性。目前InstaPunch已支持 `SPORTident(SI)`、`华瑞建(ChinaHealth)`、`灰常越野(Huichang)一代与二代`、`乐嘉体育(Learnjoy)` 这四种定向运动计时器材。学会使用InstaPunch，你就能胜任这四种硬件的成绩统计工作。

### 内部安全性
使用读卡与成绩隔离的评估系统。读卡记录进入数据库后无法修改或删除，成绩通过对原始读卡记录进行评估得到。支持修改评估的成绩，但任何情况下都会保留并且可以还原为原始的读卡数据，有效避免成统侧未经授权的数据修改。

### 外部安全性

系统整体使用Sqlite3单文件数据库存储，备份赛事只需拷贝文件，即使在读卡过程中也可以随时增量备份数据库文件。

数据库使用SQLCipher3进行加密，同时使用主密码与用户密码，确保在多数情况下不会被窃取、修改成绩数据。

除了上面针对赛事数据库的安全性以外，InstaPunch在成统系统外部添加了多一层的数据备份：Reader在读卡时会对所有的读卡记录进行额外的dump备份，通过这些备份可以重放整个赛事的读卡过程。

## 主要功能 - Features

### 多日赛成统
支持多日赛成绩统计工作，团队项目支持配置棒次/人数，特别的，InstaPunch原生支持运动员单指卡的`多棒接力赛`。
![](/assets/basic.png)

### 通道与线路设计管理
支持通道与路线设计文档管理，使用OCAD的`IOF-XML 3.0`格式进行导入，支持路线编辑。您可以在软件内新建、修改、删除路线或者其使用的检查点，也能完全手工建立路线设计文档。
![](/assets/course_and_lane.png)


### 运动员名单管理
运动员名单提供灵活的管理操作界面，可以快速查看运动员在各个竞赛日的指卡、通道、路线等配置情况，支持CSV全量或增量导入，并且可以展示导入前后之差异。
![](/assets/competitor.png)


### 队伍管理
具有队伍管理页面与分配界面，支持简单修改、批量修改与其他快捷操作，支持数据快速导入导出，支持多种队伍/队员导入模式，支持接力赛/团队赛通道快捷匹配。

![](/assets/team.png)

### 出发批次管理
内建出发批次分配与管理，具有不同的出发批次生成与间隔策略，支持出发批次导入导出，支持快速编排。读卡评估时可以直接使用编排好的出发批次表作为出发时间。

![](/assets/startlist.png)

### 成统拓扑
支持复杂的分布式网络成统，包含`Standalone`/`Multiplex Standalone`/`Dedicated Server`三种基本的成统拓扑结构，允许任意组合的N台电脑使用M台主站，你甚至可以`混合多种不同的器材同时进行成统工作`。

### 读卡评估
灵活的读卡评估策略与可配置的读卡服务器，支持：
- 多个竞赛日按优先级依次录入成绩
- 支持重复读卡记录检测与拦截
- 重新评估成绩
- 打印数据转发模式配置
- 临时成绩打印

![](/assets/readout.png)


### 赛事看板
通过赛事看板，可以全览各个竞赛日的出发与返回情况，包括总出发人数、实际出发人数、返回人数、超时未返回人数，可以筛选出未返回的，或者超时仍未返回的运动员名单，支持对运动员标记未出发。
![](/assets/blackboard.png)

### 成绩导出
动态的成绩生成控制，支持即时排序与`不分组、组别、性别、通道、路线`这五种分组方式，支持单人、团体成绩修改，支持多场赛事总成绩排名计算。
![](/assets/result.png)

## 使用须知 - Notice
- 该软件`不是`一款傻瓜式成统软件。它定位于解决`复杂赛事`成绩统计工作，因此具有`较为陡峭的学习曲线以及较高的学习门槛`。
- 该软件为本人日常业余时间进行开发与维护的共享软件，包括客户端软件、Web后端、Web前端等所有环节只有本人一人进行维护，因此具有功能实现排期不确定的缺点。在正式版本(release)发布前请不要直接用于大型赛事，建议先从小活动上手。
- 软件大多数功能都是免费的，但一些特别设计的高级功能只针对部分硬件与用户开放。
- 目前软件处于beta阶段，功能迭代是主要工作内容，不排除有较多隐藏的bug，相关文档的补充会比较慢，如有问题请联系开发者。

## 潜在的反病毒误报 - Windows antivirus issues

由于软件使用`Nuitka`进行打包，其部分压缩特征与释放型木马程序类似，部分反病毒引擎会对InstaPunch报毒，包括Microsoft/Google/AVG等境外反病毒引擎。
![](/assets/anti-virus.png)
这些误报似乎是由于Nuitka在国内几乎无人使用，但境外则有较多的木马程序使用这一软件进行打包分发所致。我们认为短时间内无法解决境外引擎误报的问题，如要使用请记得添加白名单。如果您确实不信任该软件或开发者，请不要使用该软件。

# 文档与教程 - Documentation
最新文档可以访问InstaPunch的官方文档页面 [InstaPunch Docs](https://docs.xnorienteering.club)。
# 软件发布与授权获取 - Release & Licence

软件版本发布请见 [release page](https://github.com/XiaonianPu/InstaPunch/releases)。

如需申请华瑞健读卡支持请发邮件到`sserxiaonian@gmail.com` 。

# 各版本主要开发内容 - Road Map
当前正在进行中的版本
## 2.0.0-GA (2024.12) (当前状态)
- 路段取消支持
- 其他bug修复
## 1.9.0-Stable (2024.11) (当前状态)
- 团体总分计算
- 分区积分赛模式（快速测向）
- 其他bug修复

## 1.8.0-RC (2024.06)
- 成绩并列
- 高级读卡路由与可视化界面
- Reader连接管理与可视化界面
- 更加现代的UI设计
## 1.7.0-beta (2024.02)
- UI设计V4
- Sqlalchemy全部ORM操作转CORE，大幅提示数据库读写性能
- 全局数据缓冲区，优化内存使用
- MacOS版本公证与签名支持
## 1.6.0-beta (2023.09)
- 数据库与数据存储模型解耦
- 多棒接力赛支持
- 读卡ID与转发策略支持
## 1.5.0-beta (2023.06)
- 支持MacOS (Apple Silicon)
## 1.4.0-beta (2023.04)
- UI设计V3
## 1.3.0-beta (2023.03)
- 分布式成统支持
## 1.2.0-beta (2023.02)
- 出发批次支持
## 1.1.0-beta (2023.01)
- Websockets通信协议定稿
- UI设计V2
## 1.0.0-beta (2022.12)
- 离线授权与激活系统
- UI设计V2
## 0.9.0-alpha (2022.10)
- 确定基本框架与技术路线
- 基本功能完成
- UI设计V1

# 版权以及其他说明 - Copyright & Statements
- 本软件版权归蒲小年(danielxnpu)所有。
- 如果您对小谷围高校定向联盟的故事感兴趣，可以访问 [这里](https://xnorienteering.club)




