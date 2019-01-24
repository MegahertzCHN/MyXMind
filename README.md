### MyXMind
最近看到了很多很好的博客，生成了自己的一些日常学习资料，以下是我整理XMind所借鉴的博客地址：
顺序：倒叙
软件：XMind Zen 

#### RAC文章总结：
最近一直在看RAC的文章，以下是我看的博客，给大家一些参考，难度依次升高。
参考链接是以前一篇巧神的博客：[ReactiveCocoa 讨论会](https://blog.devtang.com/2016/01/03/reactive-cocoa-discussion/),因为我主要是看了美团的技术博客，所以大部分总结的都是关于美团技术博客的文章，如果大家对我的学习路线不敢兴趣，可以坐[直通车](https://tech.meituan.com/tag/ReactiveCocoa)，直接学习。
以下是我觉得受益匪浅的博客地址：

1. [RACSignal的基本用法1](https://www.raywenderlich.com/2493-reactivecocoa-tutorial-the-definitive-introduction-part-1-2)  [RACSignal的基本用法2](https://www.raywenderlich.com/2490-reactivecocoa-tutorial-the-definitive-introduction-part-2-2)是两篇英文博客，但是非常的容易理解，即使是英语不好的我，也可以看个大概。实际上分为上下两篇，大家可以在Demo里面理解自己代码的意思，一步一步下来很有成就感。
2. [RACSignal的Subscription的深入研究](https://tech.meituan.com/RAC_Signal_Subscription.html)更进一步的分析了RACSignal原理，代码跟1紧密相连的所以1是需要大家仔细看一下的。
3. 了解了正常的RACSignal，我们就可以了解一下关于冷热信号的概念了。以下是美团总结的三个冷热信号的概念和详细解释了为什么需要了解冷热信号的区别，对于工程有哪些影响。3.1 [细说ReactiveCocoa的冷信号与热信号（一）](https://tech.meituan.com/talk_about_reactivecocoas_cold_signal_and_hot_signal_part_1.html)，3.2 [细说ReactiveCocoa的冷信号与热信号（二）](https://tech.meituan.com/talk_about_reactivecocoas_cold_signal_and_hot_signal_part_2.html)，3.3 [细说ReactiveCocoa的冷信号与热信号（三）](https://tech.meituan.com/talk_about_reactivecocoas_cold-signal_and_hot_signal_part_3.html) 看了一下，我好像3.3没有看，😓淡定淡定，秀儿坐下！！！
4. 巧神在博客中当时讨论了一下关于雷纯峰的技术博客，我看了几篇，其中：[ReactiveCocoa v2.5 源码解析之架构总览](http://blog.leichunfeng.com/blog/2015/12/25/reactivecocoa-v2-dot-5-yuan-ma-jie-xi-zhi-jia-gou-zong-lan/)，其实大家看了这些博客主要是学习MVVM架构，所以实践篇[MVVM With ReactiveCocoa](http://blog.leichunfeng.com/blog/2016/02/27/mvvm-with-reactivecocoa/)
5. 巧神的[ReactiveCocoa - iOS开发的新框架](http://blog.devtang.com/2014/02/11/reactivecocoa-introduction/)，我还没看，备注

总结一下，看了文章主要是了解了冷热信号对于项目的影响。（关于冷热信号的结论：1.RACSubject及其子类都是热信号。2.RACSignal除了RACSubject类外（当然也是除去他的子类的）都是冷信号。）大家所说的MVC是不便于测试的，不是纯函数的，代码抽离不方便的，MVVM几乎涵盖了所有的优势。其实大家接触多了以后就会发现很多Rx开头的都是以这种架构来进行解耦，所以很大程度都是一样的。在了解了一些RN的相关只是以后，你会觉得实际上Redux和Rx所干的事情都是一样的，大家都是基于纯函数的逻辑，保持这一个线程的干净程度，所以鄙人认为都是差不多的。大家保重身体，路漫漫兮修远兮...

### 埋点业务需求
1. 前段时间公司要求数据埋点所以研究了一下数据埋点的方法，看了一下美团无痕埋点的方式总结了一个XMind方面以后查看[美团点评前端无痕埋点实践](https://tech.meituan.com/mt_mobile_analytics_practice.html)

#### 博客里面主要有三种买点方式
1. 代码埋点，接口请求方式，服务端统计响应事件。代表：友盟
2. 可视化埋点，可视化动态配置统计时间，客户端动态解析，服务端统计。代表[Mixpanel](https://github.com/mixpanel)
3. “无埋点”，全部事件都进行统计，自己筛选自己想统计的事件。代表：[GrowingIO](https://www.growingio.com/)

#### 埋点做出得点思考---产品篇
埋点对于一个产品来说，是非常主要的。产品经理需要通过埋点信息拉统计自己想要的数据，这样数据就是最好的证明。一个产品经理怎样才能证明自己做的是很好的产品，拿数据说话。写代码经常说的一句话*Talking is Cheap, show me the code*，我觉得在产品上也应该有一句很适用的话*Talking is cheap, show me the data*。当然，这一切都是建立在我们都已经完成了项目功能。但是，这一切都做完了以后，你就可以看出来一个产品，到底是怎么样规划的好不好，一个产品经理在这方面是否合格。我觉得这是判断一个产品经理，到底是不是优秀的一个最基本的条件。
##### 埋点具体想要干那些事情，怎样做才是最好的
1. 所有的App，没有闪退性的Bug，才能证明其是一个成熟的商业项目
2. 事件统计务必做的精细，保证数据的精良，才不会出现决策上的误导。数据应该有一个准则，宁缺毋滥。（我可以容许你有小bug，但是你必须提出来，这个事件的统计我们在修改bug之前，不做统计）
3. 统计App的数据，产品必须要做的就是一个事件的转换概率。这是一个产品新建一个功能的时候必须统计的，一个用户是否欣赏这个功能就是在数据上说话的。数据上在没有bug的前提下，它是不会主动欺骗你的。这无论是自身规划以后的功能，还是当前功能测试都是很重要的。
4. 数据统计，对于第一个版本的App，相当于一个盲人摸象的过程，数据统计的越齐全，象就会越清楚。如果只是单纯的统计

### JSCore底层分析

1. 同样是美团的博客，说实话，最近美团一直在裁员，大家也一样在抱怨，但是从技术博客上来讲，我觉得写得都很不错，当然指的是iOS部分，我也不会其他的，[深入理解JSCore](https://tech.meituan.com/2018/08/23/deep-understanding-of-jscore.html)





