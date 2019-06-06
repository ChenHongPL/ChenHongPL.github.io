---
layout:   post
title:    "『转载』当下（2018 年）腾讯的技术建设是否处于落后同体量公司的状态？"
date:     2019-05-28
author:   "Eric"
catalog:  true
header-img: "img/post-bg-memory.jpg"
tags:
  - 腾讯
  - 技术建设
---
> 转载于知乎用户toughguy

现在是2018年9月25日，腾讯内部刚刚由总裁宣讲了形式一片大好，所有的困难都是暂时性，一切尽在把握中的鸡汤。与此同时，在 to C 端，抖音月活超过5亿，达到微信的一半；to B 端，腾讯云数据丢失风波刚过去不久，而云服务仍然没有独立作为事业群存在。

有趣的是，代表目前重点的微视和腾讯云，却一直挂在腾讯的社交事业部下面腾讯作为中国人寄托了太多感情和故事的公司，无论是恨腾讯还是喷游戏，不可否认，中国人在过去的20年中有太多的故事发生在 QQ/微信上面，相信没有一个中国人愿意看到腾讯de dao x。

然而，只有面对问题、面对困难，才能真正去帮助腾讯，不至于让他成为第二个联想，慢慢消失于人们的视野。在近期各种关于腾讯的公关文黑文中，本文只集中在两大问题：
- 技术体系：为什么说腾讯的技术体系是落后的?
- 管理体系：技术领袖为何会在腾讯消失？

以上述两点出发，从6个角度（**研发体系、高级人才的流失、人才招聘的误区、企业IT、香港帮以及马化腾自身**），用最直白没有任何花巧的语言，去直面腾讯的几大问题：

---
## 1. 研发体系：落伍一个时代
2018年4月，阿里发布“阿里技术参考图册”，将阿里的整体技术架构做了一遍梳理和介绍。

> [阿里技术：速度收藏！《阿里技术参考图册》发布，公开600页技术全景图](https://zhuanlan.zhihu.com/p/35819123)

当时在腾讯内网嘲讽者有之，忽视者有之，觉得应该模仿者有之，然而却没多少人在考虑一个问题：腾讯，你有这个能力吗？

如果腾讯一个 T3（高级工程师）的研发人员告诉你说他不习惯用git，不太会用。。。你会有什么感觉？

当你从其他公司加入腾讯，突然得知你不能从家里远程浏览代码并修改提交，必须通过一系列繁复的操作去远程登录到你办公室的机器，而这个远程登录只支持 windows，你会有什么感觉？

我们来说几个现象：
当你在腾讯准备召开一个三方远程会议，然后坐在那个看起来高大上的会议室里，却发现压根就没有白板给你绘制，同时内部视频分享的操作复杂度堪比神经网络，你会有什么感觉？

然后你慢慢发现开发人员不懂单元测试为何物，数据跟踪全靠猜，其它团队的代码你是永远无缘一见只能黑盒连调，任何功能开发你想找人讨论也没人负责，没人能说清楚一个部门的整体产品和技术架构。。。

对的，腾讯内部有 hive，有 hadoop，有 spark，有 GPU 集群，也有分布式的机器学习框架和大数据处理机制。然而，仅仅停留在某个特定业务中。

hive，就是存储数据，用起来慢？没有方便的工具或者可视化处理？sorry，那不是要考虑的问题，慢慢等就好了；

有内部 mysql 集群（这算最基础了吧），可是呢，必须从指定的远程跳板机用命令行处理，没有一个可用的客户端或者 web GUI，然后还强制不允许安装myphpadmin之类的开源，说是不安全；

数据监控，没有统一框架，各组自造轮子，视 ELK/Grafana 等等为无物，或者只是简单直接套用，套用了觉得效果没有预想好（根本没去深入了解）就开始自己做其实并不咋样的初级监控，一问到呢就说觉得自己开发更“轻量”，“更贴近业务”。

代码管理，自己山寨了一套模仿 gitlab 的系统，偏偏又不敢真的另外设计，只是在 UI 上去山寨，背后逻辑 bug 一大堆。

开发，单元测试是没有的，A/B 测试更是天方夜谭。举个例，大家看到微信前一阵推出了公众号搞成信息流，反响不好，只能更换新版本来验证。这典型的应该用 A/B测试或者 feature flag 控制的事情，在微信就是做不到，只能用频繁换版本这种大概五六年前的做法，而别家一个版本可以试验开关多个不同功能。

说到微信，微信可能是腾讯里面技术体系最接近现代公司的了，但可以看到其技术之薄弱。企业微信自称要和钉钉对抗，到现在也搞不好一个多设备同步问题，多人会议和 zoom 相比更是个 joke. 微信本身，这么多年了，克制是够克制，视频和图片都无法发高清图，都压缩的真的只适合手机看----你真以为这是克制，我认为其实是技术上支持不了。

绝大部分团队里压根没有任何人懂机器学习，也没有数据分析人员一直跟进，功能和数据 tracking 全靠 pm 猜，效果好不好靠蒙。。。

还有被人喷过无数次的内网隔离，入域问题，linux 不得入域，默认一切都是基于 windows。这尼玛是本人从业十多年来见过最奇葩的限制。这事情我会放到企业IT那部分去说。其它更多的细节就不多说了～～～～

所有这些，没有任何人出来对架构或者工具进行讨论和质疑，一切以把“业务完成”作为目标。从没人想过：如果加班加点也完成不了业务需求呢？去跳楼吗？-----而现在不是如果了，是真的加班加点砸钱也干不过抖音，干不过阿里（钉钉），人可能不用跳楼，反正股价是跳楼了。如果你是来自其它公司，你进入腾讯后会有极大的自由，自由到你无法意识到你是在一个庞大的世界前10市值的公司工作，自由到和十多个人的创业公司或者学校差不多（什么都要你自己造，从数据处理到 CI）

然而这有个奇特的现象啊：腾讯的一半工作人员都是研发相关，为什么反而如此忽略技术？

**这里其实有个分界点：2012年。**

2012 年的腾讯确立了“连接一切”的目标。照理说，要连接一切，背后更应该是极度灵活且稳定的底层架构服务，是每个工程师梦寐以求的目标。

在 2012 年以前的腾讯，这个目标是可能的。如果看“腾讯传”，会看到在与 msn 的战斗中，腾讯挖来不少微软的技术人才，后来又引来如 google 的吴军等人。在腾讯内网中，可以看到很多2012年以前对代码的规范，对统一数据平台的设计和执行等等。可以说，在提出“连接一切“这个口号前，腾讯的技术人才储备和实力，是位于中国前列，不亚于阿里巴巴，足以有底气提出这个伟大目标的。

然而奇葩的是在提出这个目标之后，我们突然看到腾讯萎靡了。先不谈人员的流失，就来看产品：从微信（诞生于 2011年）之后，腾讯在社交领域再无任何一款能拿出手的产品-----实际上整个公司从2012-2018 年就没有任何新品，除了游戏搞出王者荣耀。

在技术上，腾讯云的数据丢失已经让人看到极大的不足。而更直接的，是面对抖音的挑战时，腾讯无力的所谓“反击”，才让人惊讶地发现：原来这个巨人，已经不再能打了。在潘乱的“腾讯没有梦想”一文中，说到腾讯马放南山，刀枪入库。其实这倒不见得对，软件行业谈不上什么马放南山，如果对手还是新浪（微博），还是 360，还是网易，相信腾讯仍然能用雷霆万钧之势碾压对手。

然而，这是新一代的互联网公司。抖音，或者说头条的背后，是中国互联网 2012～2016 年全民创业的大成。技术上，数据驱动、基于 A/B 测试的快速迭代灰度发布、基于数据的技术运营等等，取代了靠产品经理拍脑瓜设计，靠疯狂发布新版本，数据全靠蒙的上一代做法；团队上，扁平化、敏捷化、数据挖掘机器学习成为团队标配，代替了繁重的层级审批和所谓“大佬带队”；运营商，来自于 O2O 的小团队分区域精细化运营取代了过去靠砸钱买广告没有可靠 metrics 的粗放做法。

腾讯意识到了危机，但当他真正拿起微视准备反击时，却发现自己还停留在坦克飞机大炮数量的比较时，对手已进入了空地一体化+电子干扰+全军信息化的世代。

年轻，必将战胜衰老-----20 岁的腾讯，在新一代互联网公司的面前，突然发现自己依赖的技术和“打法”，变得已经不再有效。

对于互联网公司来说，其实不应该存在发现技术和“打法”不再有效。因为互联网技术本就是一个不断发展的领域，没道理说有什么公司会突然一觉醒来发现世界全变了。实际上就像很多人说的，腾讯在 2017 年达到了市值高峰，一片赞歌，那么为什么在2018年突然到了谷底。如果说股价的变化因素很多，而技术体系这个问题，为什么在过去的五六年里没有这么多关注？

这里的核心问题就是：腾讯的技术困境，难道没有高级架构师来处理？

---
## 2. 技术领袖：2012～2014的出走

前面说到，在腾讯和 MSN 大战期间，从微软挖来不少人才。实际上在目前腾讯的组织架构中，残留有很重的微软（早期）特色：复杂而繁琐的测试部门和对应的千奇百怪的测试工具。

写出“浪潮之巅”来自 google 的吴军，也曾在腾讯负责 soso。

然而，这些人才，在 2012 之后，却一个一个地离开了,连CTO都走了，Why？

这个原因，恐怕没人能真正地回答。但从腾讯在 2012 之后业务的变化上，我们却非常能理解这些人员的离去。

腾讯在 2012 之后，砍掉了两个本来给予厚望的部门：搜索和电商。

从技术上来说，搜索是机器学习数据挖掘最早也是罪合适的落地点，对标的就是google/百度。

可以看到，对头条信息流最大的威胁不是腾讯，是百度的信息流。由此可见，在底层技术框架合适的前提下，业务方向的转换是能做到快速有效的。

而电商，阿里和 Amazon 都已经证明了，电商业务带动的就是云计算大数据的基础架构能力（也包括机器学习的推荐系统）。

而这些，都恰恰是腾讯在 2018 年的今天，突然发现自己的最大弱点：机器学习驱动、大数据驱动、云计算架构。

而回头一看，本来在腾讯已经步入中高层的这方面的技术领袖，却已经纷纷离职。

从 2012 之后发生了什么，我们不得而知，吴军在一次采访中隐晦地说到过腾讯没有搜索的基因，另一方面，在近期的一篇文章中，我们通过腾讯云的一角却隐约可以看到技术领袖和腾讯高管思维的冲突： 

> [腾讯正酝酿史上第三次组织架构变革](https://36kr.com/p/5153819.html)

文中提到，2010 年，拥有谷歌和微软背景的陈磊加入腾讯，并积极推动云计算的发展，但当时SNG（社交事业群）的负责人却认为要业务优先。2014 年，推动了腾讯云初期发展的陈磊离职。很有趣的是，上文中明显犯了战略错误，把业务放在并不成熟的云计算之前的高管，却并没有受到任何的指责，反而在文中提到可能会继续负责腾讯云服务。在战略上犯下大错后仍受重用，这在如战场一般的互联网公司是罕见的。

从另外一篇较早谈搜搜的可以看到，在 2010 前后，腾讯是真的下了力气挖业界顶级工程师，致力于往技术方向走的。

> [腾讯搜搜的没落之路：从拔苗助长到部门肢解裁员_科技_中国网](http://tech.china.com.cn/internet/20130917/54583.shtml)

很多人说，搜搜没做出啥来，所以高薪挖这些人是错误的，是不值得的。

实际上，一个大型企业做产品，80% 都会失败，但是为什么要去做？真的是一定要产品成功吗？其实不是的，做新产品一方面固然是希望产品本身成功，另一方面则是通过新产品来积累技术、把握技术动向，这样一来通过新产品可以带动兄弟团队和部门，二来可以保持和业界前沿接轨，不至于业务转向时措手不及。

我们可以看到，在挖来google大牛及在研发投入重注的 2010 之后，2011 年，诞生了微信。这中间有关系吗？没有关系吗？我们不能假设没有发生的事情，但现实就是，在这些牛人离开以后的 5、6 年，腾讯再无任何新品。

那么技术呢？这些牛人在技术上到底有什么帮助？

我们不妨反问一下：当年有这些牛人的时候，我想没人质疑过腾讯的技术水平（虽然那时候国内普遍较低）；然而没有这些牛人，腾讯的产品技术水平和业界（中国）前沿差了多少？

腾讯总裁刘某在最近的内部讲话中，把如今抖音的威胁和当年 3Q 大战做对比，说其实不如当年有威胁。作为一个总裁，说出这种背离现实的话，实在是让人失望。一则当年 3Q 大战不是技术之战，是运营、舆论和政策之战，这东西说白了是国家当时监管不严环境下的菜鸡互啄街头斗殴（不信的话，看看现在 360 是个啥角色，而腾讯当年就跟这个档次的打得“有声有色”）。现在和抖音是技术之战，是职业拳手在公开擂台对你挑战。而面对不缺钱不缺流量不缺运营的真正职业对手，技术上的落后，没有任何回旋的余地；二则，当年你有从微软谷歌挖来的各方高端人才助力（当时其实挖几个普通员工已经很牛逼了），而现在腾讯当年挖来的已经基本都离职，从gm一层开始基本上全部是土生土长的员工，兢兢业业，但无法在技术上提供太多帮助。与此同时，阿里这几年从西雅图从硅谷挖了多少高端人才？国外engineer一谈海归必说阿里，有几个人说腾讯？知道腾讯的岗位和级别要求？

哪怕是在 2010 前后，从微软谷歌挖来的人也帮腾讯铺垫了云计算和机器学习、大数据的一定基础，也拥有着超过类似汤道生这种“原生”员工的视野。然而，在随后的几年，这些人被一一排挤离开，到了今天，马化腾不得不承认腾讯在人才储备的不足。。。

那么，腾讯既然已经知道不足，那他是真的在开始弥补？我们不得不谈第三个问题：什么是高级人才？

---
## 3. 高级人才：发论文的就是高级？
不知道出于什么原因，腾讯对“研究人员”有特殊的偏好，从之前的吴军开始，就爱找研究人员来挑大梁。

问题是，什么时候学术研究和工业产品能混在一起了？一个精研算法的研究员，就能负责一个工程团队并在业务需求中合理取舍作出产品？

马化腾在近期谈AI的时候说腾讯在人才储备上不足，所以一直在弥补。然而，我们知道腾讯的 AI Lab 无非是招了一帮发论文的学术界 paper machine，不知道到底打算让他们出什么成果。

腾讯内部对技术嗤之以鼻，一谈技术就用“技术必须服务于业务”来搪塞。可悲的是，大部分腾讯员工连到底别人如何用技术去驱动业务的都没见过，就被所谓的业务优先洗脑了。

回避技术，回避细节，这是典型的缺乏技术领袖，从而缺乏技术自信的表现。大部分中层领导，因为自身已经多年脱离技术，对技术细节无法参与讨论，只能在业务细节上体现控制权。这本身可以理解，然而技术人才因为缺乏明确升职方向（除了做总监gm，还有啥 title 和高端职位？没了！你说T4、T5都是技术职级？来来，我们实打实的看产品代码仓库，t4、t5 提交了多少代码？实际上，有 T5 还在提交代码吗？），因此在腾讯自身并没有一个技术人才的发展通道（所谓 T4 大多也是看业务规模，不是看技术能力），最终，整个腾讯都没有一个对工程人才的正确评价体系和标准，也无人有能力去评价。相对来说，学术就好说了嘛，paper 发了多少引用了多少，这些正好是那什么 AI Lab 所习惯的一套。

而在太平洋一侧的硅谷，从微软到 google，研究院早已是过去式，专门供养一帮发paper的“研究人员”已被历史证明是错误的选择，没有哪家还在这么干。对产品团队配备专职机器学习专家(ML Scientist/Data Scientist)，让机器学习在业务组里落地应用，才是目前一线互联网企业的路线。即便在国内，我们看到达摩院、头条等公司，天天在叫着在ICML或CVPR或哪里发了多少论文吗？只有腾讯，每次腾讯 AI Lab 的论文又说发了多少，说实话都是啪啪打脸，意味着务虚的程度又深了一点。只有那些还处于创业阶段的公司，才天天拿着论文，搞个什么 xxxNet，什么比赛获奖了这些来宣传，而腾讯却在干同样的事情。

据我所知，腾讯在最近五六年，从来没有挖到过相当于在FLAGUAP等美国硅谷一线公司 senior engineering manager 以上的角色，也没有挖到过相当于 Google L7/Facebook E7 或以上的角色。而这些，才是真正的业界精英，能够推动技术架构和产品前进的。

悲伤的是，腾讯的HR部门，似乎对技术业界真牛人完全缺乏概念。在腾讯内部，HR对投资圈的简直是无脑膜拜，只要是美帝大学的 MBA ，那完全是必须破格录取，直接从实习生赐予中层管理岗位 titile，还说这是业界常规（当国内都是文盲吗？麦肯锡还是 BCG 会给一个刚毕业的MBA什么 title？还不都是 associate）。而对于 google/facebook/amazon/etc。这些一线互联网公司的工程师，则开始显示所谓的“架子”，让 google 的 L5 只去面试 T3.1 或 3.2，然后各种压包裹...例如有朋友说的真实案例：腾讯海外招聘：来挖狗5，面试左一轮右一轮，题也做了，“基础”也问了，项目细节也挖了，架构也做了。末了 hr 说可以给 3.1，3.2 要“争取”一下。。。请问这怎么挖？别人 40 万美元入门的年收入在乎你的3.2？挖一年能挖到半个人吗？当然鹅厂 HR 也可以说硅谷码农也没什么了不起的，不挖也罢（有趣的是这些 hr 挖些啥 facebook 东南亚或者 Google 什么大区的“市场经理”之类的很热情）。

其实，这又存在另一个问题：真正的工程专家到了腾讯，肯定是无法接受各种牵强无理的内部限制，比如繁琐到必须专人负责的 docker 环境和权限，毫无道理的内网分离等。。。对开发流程也必然提出各种修改意见，这一来未必能被中层接受（改变太大），二来，腾讯的锦衣卫企业IT所制定的荒谬内部限制，也必然无法接受高端工程专家的质疑，比如前文所说不允许在家远程提交修改代码之类的问题，企业IT压根就无法拿出可信理由，但他们要做的并不是去改进，而是压制其他人的反对。

---
## 4. 企业IT：锦衣卫要办的事，大将军又能如何
终于来到这个环节：企业IT

从技术和工程层面上来说，这是腾讯的最大毒瘤之一，具体细节可以参看这位的回答：

> [当下（2018 年）腾讯的技术建设是否处于落后同体量公司的状态？](https://www.zhihu.com/question/278473776/answer/492480937)

企业IT，在绝大公司内部，理论上是一个存在感比较弱的支撑部门，然而在腾讯，这不仅仅是关联到内部网络环境，不管什么项目，你必须按照企业IT的要求去安排你的开发、测试、部署和发布，而且没有商量。

腾讯的企业IT会在没有任何讨论的情况下告诉你你的网络协议不再被支持，是“不安全“的，是必须禁止的，并在禁止使用的内部黑名单上包括了例如 myphpadmin 这类的知名开源软件然后他们宣称自己的“安全”能力是世界第一。

在大部分互联网公司中，对开源的使用是有一定争议。然而无论什么公司，在禁止某些开源工具的同时，会提供对应的打过 patch 的对应定制版本或相似工具来满足需要。

然而腾讯的企业 IT 像极了锦衣卫和某些大家喜闻乐见的部门：只负责下令，只负责禁止，至于造成什么难题，是否提供可选方案，那是一律不管，也不听。

说直白点，企业IT是门槛最低的部门，其中所谓啥网络安全策略、网络隔离方案等等根本在其他人眼里是笑掉大牙，但这帮人却把控着莫大的权势。

我真的想x他大爷，这帮人真的可以，背后不知道是什么人在撑腰，一天拿着鸡毛当令箭。

真要讲技术的时候，比如心平气和给他们说其实可以用 public_key 认证，其实ssh本身比他们自己包的什么狗屁shell工具足够安全，他们听不懂，不再回复。

但是没辙，企业IT在腾讯内部不知道后台是什么人，反正可以一手遮天，不跟任何bg不跟任何其它技术人员讨论，一句公司不允许，就要求你停止服务。

为此我尝试从他们的角度想过很久，只能认为因为以前的网络开发部署，外网内网要求严格隔离，所以企业IT不允许任何对外网的服务和内网产生关联。也有小道消息说是因为早期腾讯内网被人入侵过，所以公司非常在意这个问题。

然而他们把内网又分成了三种网络，每种网络不能互通或者需要特别申请，企业IT认为这叫“安全”。。。这简直是滑天下之大稽。在这种滑稽的网络划分下，可以把腾讯企业IT的错误，尤其是严重影响内部技术框架的错误归纳如下：
- 不得从远程浏览提交代码（不可在家访问内部 git）
- Linux机器不可加入内网（真的，这是需要特别审批，不然不允许。这直接导致无数机器学习系统压根无法在内部真正接入数据做 online training）
- 内网服务不可使用除80/8080之外的端口（最近好像 8080 都禁止了）
- 不可自行组局域网（again，直接禁止内部尝试分布式集群）
- 内网分成三种网络，并实行物理隔断

可以说，企业IT是腾讯最大毒瘤，对腾讯的技术产品发展的罪恶罄竹难书！

我们不反对安全，不反对严格的规定，但是，一个部门，和其它部门没有任何沟通，没有任何公开讨论，如同皇帝圣旨一样下令，随意制定规矩，直接影响产品开发流程，等同于古代太监直接命令出战的军队，这是什么一回事？

或者说，企业IT确实是有圣旨。因为在咨询公司和投资公司里面，内部IT确实就是在做这些屁事。在这些投资公司里面，IT人员是上不了台面的，是disposable的。而，腾讯，在一些奇怪的思路和群体把持下，正好在把一个世界顶尖的互联网公司往三流投资公司转变！下面来说投资。

---
## 5. 投资问题

腾讯内部投资部门无数次用 google 用 amazon 用苹果来给自己辩解，说什么其它一线公司也大量投资。可惜，别人的投资，挖来了人才和技术，整合到自己的产品线，或者把人才融入到自己团队，例如 google 收购 deepmind，facebook 收购 intagram/parse 等等。而砸钱 600 多家公司，却只是像一个中国大妈一般去买股票成为股东罢了。

连接一切这个本应是具有无比技术挑战和吸引力的口号，在这里，却降格成了疯狂入股（买股票）。

关于这方面的错误，已有很多文章讲过，在这里不用我再废话。公司的方向，必然由公司高层决定，而腾讯作为一家上市公司，高层信息是公开的。24 名高管，去掉国外人士还有19名，其中香港商业背景的6名。可以说腾讯的高管团队印有强烈的“港味”。而其中大部分于 2004 左右入职，也就是腾讯上市前后。

从历史的眼光来看，2004 前后，不光是中国互联网开始成长，各种金融公司、投资公司也开始进入国内，而这些人是自带光环的，用复杂的金融概念忽悠了大把人，直到 2008 年的泡沫破灭。在当时这种氛围下，相信来自于香港的“高端投资人士”能够把腾讯从一个本地公司带到“世界级公司”，是可以理解的。可以想像，在 2004 年，成长于深圳大学计算机系的马化腾，接触到香港的投行买办时，会觉得对方如何的高大上。这一点，即便在今天，在很多大陆公司接触到麦肯锡/BCG等咨询公司时，也会被对方光鲜的外表和听上去 fancy 的复杂理论所迷惑，觉得对方能帮自己变得高大上，走入华尔街。。。

然而，历史过去了十多年，真正走向世界的，是土生土长的阿里，甚至是土生土长的抖音。

无论是腾讯的香港帮，还是香港金融投资本身，都被历史狠狠扇了一记耳光！

在有一篇叫“马化腾的七种武器”一文中用崇尚的语气这样说：“所以说，大公司最保守和安全的方式就是通过资本的方式，因为公司内部已经不可能有任何的驱动力了，只有通过投资来做。”

简直是放狗屁！Yahoo 做成了世界上有史以来恐怕最好的投资，结果呢？现在死到哪里去了？

对于香港背景的投行人士，一向就是华尔街的边缘，说直白点不过是西装革履的买办罢了。香港这么多年来，本来就没有什么创新和产品出现，而且本身就压根没啥世界一线的企业，有什么资格去谈大公司的驱动？互联网公司在成长后如何保持驱动能力，本来就是一个开放性难题，微软在遇到 google/facebook 后拼命挣扎，google 从大数据驱动到 mobile first 到 AI first 不断革新不断强化自己的开发人员，Amazon 从网上销售走到云计算走到 AI，阿里从淘宝到阿里云，哪家世界一线公司不是努力在自我革新自我驱动？

香港从未有人进入过世界一线公司的行列，就自以为能靠投资来驱动？香港买办连华尔街的边角都没沾到，也好意思谈这些？

然而，泡沫的虚高是金融投资的拿手好戏，一个本可以媲美 google 的公司，一个聚集了中国人情感的产品公司，被强行降格成为一个投资公司？

我们要清楚看到：在互联网时代初期，香港也曾有过互联网热潮，但是历史证明，香港为背景的企业高管，其视野、能力压根不适合经营一个世界顶级的科技企业，不可能带动腾讯去与 google/amazon 争雄-----这个工作，现在是阿里在努力。

身为程序员的腾讯员工更要意识到：如果你们和投资公司咨询公司接触过，就会知道其内部工程技术人员的地位几乎就是外包，连真正的内部年会都没资格参加，更遑论什么高额奖金。而有些人，正在努力把腾讯往那个方向转变！这不仅是个人的悲哀，也是中国的悲哀，把一个本是中国科技带头羊的公司，强行降格成为金融投资人士的垫脚石。对于这些人，他们的未来是可期的，在往着投资公司发展的道路上，他们不但会利用腾讯上万程序员的代码和加班去保障他们玩投资的资金来源（已投出腾讯半个市值的股票，美其名曰“护城河”，谁 tm 会在你不行的时候来“护”你？骗谁？），他们也会踩着真正创造了腾讯价值的鹅厂员工去达到他们的目标，买办从来就是做这些事情。危言耸听吗？恐怕不是。

企业IT的强势，恰恰在暗合投资/咨询公司的特点：内控重于一切，产品技术靠边，没人在意。一个市值曾进入世界前五的公司，对自己的定位是南山高盛？这算追求？

这不会是马云的追求，不会是李彦宏的追求，不会是王兴雷军任正非的追求，任何大陆的这一代互联网人，都不会在这个时代把自己局限于某个西方企业的模仿。

香港，和印度一样，他们是西方金融的殖民地，如果说印度人以踏入美国硅谷为荣，香港的“金融精英”则以能为华尔街公司的远东分部工作为耀。

要他们以超越西方一线企业为目标，从基因里就缺了这条弦。

---
## 6. pony：还在乎腾讯？

在“硅谷”一剧中，高层 CEO 热衷于心灵鸡汤、瑜伽，对实际业务视而不见。在QQ文档推出后，据说马化腾发了个朋友圈说提了8年的需求终于实现了。。。

这是高兴，还是可悲？

在这里，这一段就不再多写。一个人的格局可以很高，比如 Bill Gates，他的格局，绝对超越了微软 CEO，他已经在为人类而努力。然而，格局再高，跟能否把一个公司带回正轨是两码事。

ponyma，还对腾讯这家公司留有多少热情呢？

在当前大环境，ceo 去多做社会工作，打点更高层面的一些事情是合理和必须的，然而在这样做之前，公司能托付给投行出身的人吗？他们能真的懂得如何把控腾讯？

古代有买椟还珠的故事，而这帮香港买办正在上演这一幕。无视腾讯优秀的产品和曾经拥有的研发能力，一心只看到流量和资金，用他们狭隘的目光只聚焦在投资分成上。这帮香港买办的视野，并不比古惑仔好到哪里去，只知道收点保护费和小弟的簇拥，自以为声势浩大，其实在真正的强权到来时不堪一击。

**写在后面：**
本文纯属个人思考和部分联想，如很多朋友指出，有些地方太偏颇。但本文的目标只是从一些直接的角度激发思考，重在讨论，交流胜于一切。

腾讯纵有千般问题，但对言论的宽容，是我所见过仅有的。无论是内网社区还是对外，都能做到非常好的包容度。包括本文，在最初版本发出后，也只是客气地要求不要搞成人身攻击，这是非常合理的要求，因此做出部分调整。

正如文中所说，腾讯的最大特色就是自由度，我相信这在中国企业是罕见的。一个公司只要能保持这种自由和宽容，那就永远有希望。