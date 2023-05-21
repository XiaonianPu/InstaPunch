# InstaPunch

InstaPunch™ 是一款基于 PySide6 图形化界面设计的全生命周期定向运动多日赛成绩统计软件，主要有**InstaPunch Reader**读卡软件与**InstaPunch**成绩统计客户端组成。

## 介绍

该成统软件的主要特性有：

- InstaPunch凭借灵活的读卡数据接口、合理的数据库与实体结构设计，抹平了不同硬件在读卡记录上的表达、存储差异，使得不同的硬件器材能够以相同的形式展示在软件中。目前InstaPunch已包括 **SPORTident(SI)、华瑞建(ChinaHealth)、灰常越野(Huichang)、乐嘉体育(Learnjoy)** 这四种定向运动计时器材。学会使用InstaPunch，您就可以掌握上述四种硬件的成绩统计工作。
- 支持**路线设计文档管理**，支持IOX-XML 3.0格式进行导入，支持成统内对路线设计文档进行修改。您可以在软件内新建、修改、删除路线或者其使用的检查点，并将修改应用到过往的读卡数据中。
- 运动员名单具有强大且灵活的管理操作界面，使用CSV进行导入，支持增量与差异化导入，具有一定的字段识别能力。
- 团体项目具备良好的队员分配界面，支持多种队伍、队员导入模式，支持接力赛、团队赛路线自动匹配。
- 具有不同的出发批次生成与间隔策略，支持出发批次导入导出，评估时可以直接使用出发时间。
- 采用读卡与成绩隔离的评估系统。读卡记录进入数据库后无法修改、删除，成绩通过对原始读卡记录进行**评估**得到。软件支持修改评估的成绩，任何情况下**都会保留并且可以还原为**原始的读卡数据，有效避免成统侧未经授权的数据修改。
- 具有较高的数据安全特性，数据使用Sqlite3单文件数据库存储，备份赛事只需拷贝文件（读卡过程中也可以随时备份）。数据库实现了基于HMAC-512的SQLCipher3加密库，同时使用主密码与用户密码，即使我这个开发者也无法在不知道用户密码的情况下解密数据库，确保在多数情况下数据库无法在外部被访问。

列举了那么多特性，同时也需要指出的是：

- 该软件并**不是**一款傻瓜式成统软件。它定位于解决**复杂赛事**成绩统计工作，以赛事数据与成绩安全为主要保障目标，结合对应的Web平台，提供安全、稳定、强大的成绩统计支撑。因此具有**较为陡峭的学习曲线以及较高的学习门槛**。
- 该软件为本人日常业余时间进行开发与维护的共享软件，包括客户端软件、Web后端、Web前端等所有环节只有本人一人进行维护，因此具有功能实现排期不确定的演员，请不要直接用于大型赛事，建议先从小活动上手。
- 软件大多数功能都是免费的，但一些特别设计的高级功能只针对部分硬件与用户开放。
- 目前软件处于beta阶段，功能迭代是主要工作内容，不排除有较多隐藏的bug，相关文档的补充会比较慢，如有问题请联系开发者。

软件版本发布请见 [release page](https://github.com/XiaonianPu/InstaPunch/releases)，如需授权体验请发邮件 sserxiaonian@gmail.com 。

本软件版权归蒲小年(danielxnpu)所有，侵权必究？否，不必究，👴不在乎。

如果您对小谷围的故事感兴趣，可以访问 [这里](https://xnorienteering.club)
