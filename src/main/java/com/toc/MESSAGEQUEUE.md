<a name="index">**Index**</a>

<a href="#0">消息队列</a>  
&emsp;<a href="#1">1. 异步、削峰、解耦</a>  
&emsp;&emsp;<a href="#2">1.1. 异步</a>  
&emsp;&emsp;<a href="#3">1.2. 削峰</a>  
&emsp;&emsp;<a href="#4">1.3. 解耦</a>  
&emsp;<a href="#5">2. 系统复杂度</a>  
&emsp;&emsp;<a href="#6">2.1. 重复消费</a>  
&emsp;&emsp;&emsp;<a href="#7">2.1.1. 接口幂等性</a>  
&emsp;&emsp;<a href="#8">2.2. 顺序消费</a>  
&emsp;&emsp;<a href="#9">2.3. 保证消息不丢失</a>  
&emsp;&emsp;<a href="#10">2.4. 消息堆积</a>  
&emsp;&emsp;&emsp;<a href="#11">2.4.1. 原因及处理流程</a>  
&emsp;&emsp;&emsp;&emsp;<a href="#12">2.4.1.1. 典型原因</a>  
&emsp;&emsp;&emsp;&emsp;<a href="#13">2.4.1.2. 处理措施</a>  
&emsp;&emsp;<a href="#14">2.5. 数据一致性</a>  
&emsp;&emsp;<a href="#15">2.6. 可用性</a>  
&emsp;&emsp;<a href="#16">2.7. 分布式事务问题</a>  
&emsp;<a href="#17">3. 消息队列选型</a>  
&emsp;<a href="#18">4. 消息队列背后的设计思想</a>  
&emsp;&emsp;<a href="#19">4.1. 消息队列核心模型</a>  
&emsp;&emsp;<a href="#20">4.2. 获取数据的推、拉</a>  
&emsp;&emsp;<a href="#21">4.3. 消息队列模型</a>  
&emsp;&emsp;&emsp;<a href="#22">4.3.1. 队列模型</a>  
&emsp;&emsp;&emsp;<a href="#23">4.3.2. 发布订阅模型</a>  
&emsp;<a href="#24">5. 消息队列相关概念</a>  
&emsp;&emsp;<a href="#25">5.1. 优先级队列</a>  
&emsp;&emsp;<a href="#26">5.2. 延迟队列</a>  
&emsp;&emsp;<a href="#27">5.3. 死信队列</a>  
&emsp;&emsp;<a href="#28">5.4. 重试队列</a>  
&emsp;&emsp;<a href="#29">5.5. 消息回溯</a>  
&emsp;&emsp;<a href="#30">5.6. 其他概念</a>  
<a href="#31">Kafka</a>  
&emsp;<a href="#32">1. 基本概念</a>  
&emsp;<a href="#33">2. Kafka 高性能设计技术</a>  
&emsp;&emsp;<a href="#34">2.1. Producer发送端</a>  
&emsp;&emsp;<a href="#35">2.2. Broker存储消息</a>  
&emsp;&emsp;<a href="#36">2.3. Consumer消费端</a>  
&emsp;<a href="#37">3. 数据同步</a>  
&emsp;&emsp;<a href="#38">3.1. kafka replica</a>  
&emsp;&emsp;<a href="#39">3.2. ISR</a>  
&emsp;&emsp;<a href="#40">3.3. ACK机制</a>  
&emsp;&emsp;<a href="#41">3.4. 故障转移过程</a>  
&emsp;&emsp;<a href="#42">3.5. 其他</a>  
&emsp;<a href="#43">4. 消息消费细节</a>  
&emsp;&emsp;<a href="#44">4.1. 消费者组与Partition</a>  
&emsp;&emsp;<a href="#45">4.2. offset</a>  
&emsp;<a href="#46">5. 分布式的kafka解决节点宕机或者抖动问题</a>  
&emsp;<a href="#47">6. 与ZooKeeper的依赖</a>  
&emsp;&emsp;<a href="#48">6.1. Broker 注册 </a>  
&emsp;&emsp;<a href="#49">6.2. Topic 注册 </a>  
&emsp;&emsp;<a href="#50">6.3. 负载均衡 </a>  
&emsp;&emsp;<a href="#51">6.4. 消息 消费进度Offset 记录</a>  
&emsp;<a href="#52">7. 面试题</a>  
&emsp;&emsp;<a href="#53">7.1. Kafka 是什么？主要应用场景有哪些？</a>  
&emsp;&emsp;&emsp;<a href="#54">7.1.1. kafka优点</a>  
&emsp;&emsp;<a href="#55">7.2. kafka 为什么快</a>  
&emsp;&emsp;&emsp;<a href="#56">7.2.1. 顺序写磁盘</a>  
&emsp;&emsp;&emsp;<a href="#57">7.2.2. 大量使用内存页</a>  
&emsp;&emsp;&emsp;<a href="#58">7.2.3. 零拷贝技术</a>  
&emsp;&emsp;&emsp;<a href="#59">7.2.4. 消息压缩、批量发送</a>  
&emsp;&emsp;<a href="#60">7.3. Kafka 如何保证消息队列不丢失</a>  
&emsp;&emsp;<a href="#61">7.4. kafka 高可用是如何实现?</a>  
&emsp;&emsp;<a href="#62">7.5. kafka会存在数据丢失问题</a>  
&emsp;&emsp;<a href="#63">7.6. 想要保证消息（数据）是有序的，怎么做？</a>  
&emsp;&emsp;<a href="#64">7.7. 为什么在消息队列中重复消费了数据</a>  
<a href="#65">RocketMQ</a>  
&emsp;<a href="#66">1. 基本概念</a>  
&emsp;<a href="#67">2. 基本架构</a>  
&emsp;<a href="#68">3. 优缺点</a>  
&emsp;<a href="#69">4. 事务实现</a>  
# <a name="0">消息队列</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

参考资料：
- [消息队列背后的设计思想](https://mp.weixin.qq.com/s/k8sA6XPrp80JiNbuwKaVfgc)
- [Kafka 精妙的高性能设计（上篇）](https://mp.weixin.qq.com/s/kImrkVLE4dtpVnb-Yp479Q)
- [Kafka 精妙的高性能设计（下篇）](https://mp.weixin.qq.com/s/knn6gPUkG41ByJAxilDyoQ)
- [Kafka 概述：深入理解架构](https://juejin.cn/post/6844904050064883725#heading-8)

为什么使用消息队列？
- 异步、解耦、削峰、统一管理所有的消息
- 缺点：系统复杂度增加、消息队列存在消息发送的重复消费、消息丢失等问题。


消息队列适合哪些场景？\
消息队列：它主要用来**暂存生产者生产的消息**，**供后续其他消费者来消费**。它的功能主要有两个：**a.暂存(存储)、b.队列(有序：先进先出)**。其他大部分场景对数据的消费没有顺序要求，主要用它的暂存能力 。从目前互联网应用中使用消息队列的场景来看，主要有以下三个：
1. **异步处理数据**
2. **系统应用解耦**
3. **业务流量削峰**
> 消息队列主要适用于处理**对消息要求不是很实时，同时一份数据可能会多处使用的场景**。

## <a name="1">异步、削峰、解耦</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
### <a name="2">异步</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/async.png)
例子中我们把暂存快递的快递柜比作暂存数据的消息队列。当有了快递柜后，对于快递员而言，每次需要送快递时，只需要将快递投掷到快递柜，然后再通过短信或者电话通知收货人具体的快递信息即可。他就可以继续去派送下一单。而对于收获人而言，也可以根据具体方便的时间来取件。这样一来，二者完全异步了，不用相互等待了。
> 主要体现的消息队列的消息暂存的功能，使上下游的消息调用可以异步进行。

### <a name="3">削峰</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/cut-off.png)

对于大流量的请求，可以将请求放在消息队列。消息队列可以设置消息的效率频率，匹配服务器的服务能力，解决大流量请求发送服务器导致的服务器宕机问题。\
如常见的双11等活动，高峰值期间产生的订单消息等数据首先送入到消息队列中暂存，然后供下游系统根据自己的消费能力来逐步处理。同时**这类消息往往对时延的要求不是很高，比较适合采用消息队列暂存**。

### <a name="4">解耦</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/divorce.png)

上图最主流的推荐系统中内容的流转过程。在推荐系统中当创作者发布了一条内容后，该内容会首先经过安全部分的相关审核，通过审核后的内容，通常需要进行内容入库存储、送入模型进行特征的计算和生成。\
假如后期我们想提升推荐的效果，需要单独构建一份冷启动的推荐池，此时也需要用到这部分内容，那问题来了，在没有使用消息队列时，对于上游服务而言，需要通过扩展新的逻辑来实现该功能。在该场景里，会存在依赖三个下游服务，如果其中一个下游服务失败后，该如何处理，是重试还是返回失败等这些细节的处理。如果后期这部分数据还想在其他渠道分发，那又该如何对接。明显这种场景下面临着**系统紧耦合**的问题。\
如果引入了消息队列。当内容审核通过后，就直接将数据生产出来丢到消息队列中，下游的多个服务再从消息队列消费数据。当后续这一份数据需要扩展供其他系统使用时，也只要通过新的消费者来接入到消息队列消费就ok。上游生产消息的模块不要做任何的改动。

额外功能或业务的添加会导致业务流程处理的时间变长，虽然可以使用异步如线程、线程池来实现。但是使用线程实现的话，每个流程都要try catch去处理异常场景，**业务流程的耦合性太强**，而且系统中会杂糅进调用其他系统的代码。不利于维护。\
使用消息队列来实现，相当于流程操作完成，只要通知消息队列一个流程完成的消息就行了。其他业务流程订阅消息，接收到消息就会去处理对应的逻辑，降低整个流程的耦合性。

## <a name="5">系统复杂度</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
问题： 重复消费、消息丢失、顺序消费

### <a name="6">重复消费</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
接口幂等性：使用相同参数重复执行，并能获得相同结果。

#### <a name="7">接口幂等性</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
1. 使用唯一标识：如订单号+业务场景这样的唯一标识。执行操作前先根据这个全局唯一ID是否存在，判断是否执行。如果不存在则把全局ID，存储到存储系统中，比如数据库、redis等。如果存在则表示该方法已经执行。存储的时候加入过期时间，防止机器宕机后，全局ID锁死导致操作无法继续
2. 去重表：适用于在业务中有唯一标的插入场景中。如支付场景中，如果一个订单只会支付一次，所以订单ID可以作为唯一标识。这时，我们就可以建一张去重表（流水表），并且把唯一标识作为唯一索引，在我们实现时，把创建支付单据和写入去去重表，放在一个事务中，如果重复创建，数据库会抛出唯一约束异常，操作就会回滚。
3. 多版本控制：适合在更新的场景中，比如我们要更新商品的名字，这时我们就可以在更新的接口中增加一个版本号，来做幂等。
> `update goods set name=#{newName},version=#{version} where id=#{id} and version<${version}`


### <a name="8">顺序消费</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
针对顺序消费问题，只要发送者保证把消息发送到topic的相同队列中即可。
- 对于Kafka，生产者发送消息时可以指定固定Partition的topic下。
- 对于rocketmq，RocketMQ提供了MessageQueueSelector队列选择机制，Hash取模法将同一个操作的消息发送到同一个Queue里面。

同时消费者端也得保证顺序消费。如果多个消费者同时消费一个队列，一样可能出现顺序错乱的情况。

### <a name="9">保证消息不丢失</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
- 生产者端：不论是同步还是异步发送消息，同步和异步回调都需要做好try-catch，妥善的处理响应，如果Broker返回写入失败等错误消息，需要重试发送。当多次发送失败需要作报警，日志记录等。
- 消息队列端：存储消息阶段需要在消息刷盘之后再给生产者响应，防止突然宕机导致消息丢失。
    > 如果Broker是集群部署，有多副本机制，即消息不仅仅要写入当前Broker,还需要写入副本机中。那配置成至少写入两台机子后再给生产者响应。
- 消费端：消费者真正执行完业务逻辑之后，再发送给Broker消费成功

**消息可靠性增强了，性能就下降**

### <a name="10">消息堆积</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
主要原因 生产者的生产速度与消费者的消费速度不匹配
1. 先定位消费慢的原因，优化逻辑，如部分场景可以批量处理。
2. 增加Topic的队列数和消费者数量。

#### <a name="11">原因及处理流程</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

##### <a name="12">典型原因</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
1. 实时/消费任务挂掉
2. Kafka分区数设置的不合理（太少）和消费者"消费能力"不足
3. Kafka消息的**发送不均匀**，导致分区间数据不均衡。
    1. 在使用Kafka producer消息时，可以为消息指定key和分区。
    2. 若指定了分区，那么消息会发送指定分区。
    3. 如果未指定分区但是指定了key，那么就会使用key进行hash算法计算对应的分区。要求key要均匀，否则会出现Kafka分区间数据不均衡。
    4. 若key和分区均未指定，那么将会使用轮询发送的方式。
> `KafkaTemplate.send(ProducerRecord<K,V> record)`

##### <a name="13">处理措施</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
临时处理措施：同时增加kafka的服务器与消费者，**增加Partition，同时增加消费能力**。

上述典型原因处理方法：
1. 实时/消费任务挂掉
    1. 任务重新启动后直接消费最新的消息，对于"滞后"的历史数据采用离线程序进行"补漏"。
    2. 任务启动从上次提交offset处开始消费处理
2. Kafka分区数设置的不合理(TODO) :增加分区或者重新评估分区设置 
3. 消息发送不均匀，合理设置
    1. 在Kafka producer处，给key加随机后缀，使其均衡。 
    2. 评估顺序消费的能力。

### <a name="14">数据一致性</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
使用分布式事务解决消息发送后，一个消息被不同系统分别监听可能导致的 数据不一致问题。
> 如把下单，优惠券，积分。。。都放在一个事务里面一样，要成功一起成功，要失败一起失败。
  
### <a name="15">可用性</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
如何保证消息队列可用

### <a name="16">分布式事务问题</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
分布式事务就是指事务的参与者、支持事务的服务器、资源服务器以及事务管理器分别位于不同的分布式系统的不同节点之上。简单的说，就是一次大的操作由不同的小操作组成，这些小的操作分布在不同的服务器上，且属于不同的应用，分布式事务需要保证这些小操作要么全部成功，要么全部失败。本质上来说，分布式事务就是为了保证不同数据库的数据一致性。

在业务开发中，经常遇到更新服务数据库事务并且需要发送消息的场景，比如订单付款成功+发消息，用于给下游的积分系统给用户增加积分等等。\
实际上在开发中，很多人都会如此实现：
```
@Transactional
public void createOrder() {

    //1. 创建订单
    orderDAO.insert(orderDO);
    
    //2. 发消息
    kafkaProducer.send()
}
```
这段实现的问题：
1. 把中间件的通信放在事务中处理，如果中间件通信出现问题，可能导致事务过长。在并发量大的时候，可能会因为长事务占满数据库的连接，导致服务出现故障。
2. 下游服务，如果依赖于上游记录。可能在发送消息而事务还未提交时，下游服务回调上游服务，未找到对应的记录。
3. 如果发送消息成功，而本地事务提交失败，而出现了不一致的情况。

> **任何涉及到数据库和中间件之间的业务逻辑操作，都需要考虑二者之间的一致性。**

**本地消息表**

本地消息表这个方案最初是ebay提出的[ebay的完整方案](https://queue.acm.org/detail.cfm?id=1394128)

此方案的核心是将需要分布式处理的任务通过消息日志的方式来异步执行。消息日志可以存储到本地文本、数据库或消息队列，再通过业务规则自动或人工发起重试。人工重试更多的是应用于支付场景，通过对账系统对事后问题的处理。

![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/local-message-table.png)

本地消息表实现：
1. 在发送端建立一张用于发送消息专用的数据库表，在必须要发送事务的场景下，更新数据同时插入本地消息表，保证事务的一致性。
2. 通过定时job，扫描消息表发送队列消息，成功后更新消息表对应记录，来保证消息必定发送成功。
3. 发送消息与更新本地消息表同样数据分布式事务，会出现发送队列消息成功，而更新本地消息表失败的情况。因此消费端需要做好幂等的处理。
4. 消费端幂等的处理，可见本文重复消费的内容。
> 本地消息表实现的缺点：业务方需要单独设计消息表，以及需要定时发送消息的定时器，增加了与业务无关的开发负担

参考文章：
- [老生常谈——利用消息队列处理分布式事务 ](https://www.cnblogs.com/rjzheng/p/10115798.html)
- [分布式事务之本地消息表](https://www.cnblogs.com/FlyAway2013/p/10124283.html)
- [最终一致性之本地消息表、消息事务(三种常见错误场景)](https://blog.csdn.net/hosaos/article/details/108644527)

## <a name="17">消息队列选型</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
目前主要的消息队列有 ActiveMQ、RabbitMq、Kafka、RocketMq，用的比较多的是Kafka和RocketMq两个，主要这两个都支持10万级的高吞吐量，而且相应的开发社区活跃，遇到源码问题便于维护。

![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/compare.png)

1. ActiveMQ 和 RabbitMQ 二者属于同一量级，在吞吐量上比后面三者差一个量级；
2. 支持强一致性的有 RocketMQ 和 Pulsar，在对消息一致性要求比较高的场景可以采用这些产品。同时 kafka 虽然会有数据丢失的风险，但其吞吐量比较高同时社区非常活跃，在大数据的绝大部分场景里，都可以采用 kafka
3. kafka、RocketMQ、Pulsar 这几款是基于磁盘存储数据的，内存加速访问。而 ActiveMQ、RabbitMQ 采用内存存储数据，也支持数据持久化到磁盘。


## <a name="18">消息队列背后的设计思想</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
### <a name="19">消息队列核心模型</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/mq-structure.png)

对于一个消息队列而言，从数据流向的维度，可以拆解为三大部分：**生产者、消息队列集群、消费者**，数据是从生产者流向消息队列集群，最终再从消息队列集群流向消费者

**生产者**： 生产数据的服务，通常也称为数据的输入提供方，这里的数据通常指我们的业务数据。其次生产者通常会有多个，消息队列集群内部也会有多个分区队列，所以在生产者发送数据时，通常会存在负载均衡的一些策略，常见的有按 **key hash、轮询、随机等方式。其本质是一条数据，被消息队列封装后也被称为一条消息，该条消息只能发送到其消息队列集群内部的一个分区队列中。因此只需按照一定的策略从多个队列中选择一个队列即可**。
> 生产者通常是作为客户端的方式存在，但在支持事务消息的消息队列中，生产者也被设计为服务端，实现事务消息这一特性。\
> 业务场景例如推荐场景中用户对内容的点击数据、内容曝光数据、电商中的订单数据等等。

**消息队列集群**： 消息队列集群是消息队列这种组件实现中的核心中的核心，它的主要功能是存储消息、过滤消息、分发消息。
> 存储消息主要指生产者生产的数据需要存储到消息队列内部；存储消息可以说是消息队列的核心，一个消息队列吞吐量的高低、性能优劣都和它的存储模型脱不开关系。\
> 过滤消息只指消息队列可以通过一定的规则或者策略进行消息的过滤，该项能力通常也被称为消息路由；过滤消息属于高阶的特性功能，AMQP 协议对这些能力抽象的比较完备，部分消息队列可以选择性的实现该协议来达到该功能。\
> 分发消息是指消息队列通常需要将消息分发给处理同一逻辑的多个消费者处理或者处理不同逻辑的不同消费者处理。分发消息可以说和消费者模型相挂钩

**消费者**： 最终消息队列存储的消息会被消费者消费使用，消费者也可以看做消息队列中数据的输出方。消费者通常有两种方式从消息队列中获取数据：**推送(push)数据、拉取(pull)数据**


### <a name="20">获取数据的推、拉</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
消费者在从消息队列中获取数据时，主要有两种方案：
1. 等待推送数据
2. 主动拉取数据

![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/push-pull.png)

### <a name="21">消息队列模型</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
消息队列有两种模型：队列模型和发布/订阅模型。
![avatar](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/queue-core.png)

#### <a name="22">队列模型</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
消费者之间是竞争关系，即每条消息只能被一个消费者消费。
![avatar](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/queueModel.jpg)

#### <a name="23">发布订阅模型</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
解决一条消息能被多个消费者消费的问题，消息发往一个Topic主题中，所有订阅了这个 Topic 的订阅者都能消费这条消息。
![avatar](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/queueModel2.jpg)

消费者模型其实是一个`1:N:M` 的关系，一份数据被N个消费者组独立使用，每个消费者组中有M个消费者进行分摊消费\
其实这种模型也称为发布订阅模型，对于一条消息而言，**组间广播**、**组内单播**。一条消息只能被一个消费者组中的一个消费者使用。在消费者组内部也存在一些负载均衡的策略。常用的有：轮询、随机、hash、一致性 hash等方案。

**发布/订阅模型兼容队列模型，即只有一个消费者的情况下和队列模型基本一致**
> 对应的kafka一个topic可以仅指定一组消费组。

**RabbitMQ采用队列模型，RocketMQ和Kafka 采用发布/订阅模型**

## <a name="24">消息队列相关概念</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

### <a name="25">优先级队列</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

优先级队列不同于先进先出队列，优先级高的消息具备优先被消费的特权，这样可以为下游提供不同消息级别的保证。
> 不过这个优先级也是需要有一个前提的：如果消费者的消费速度大于生产者的速度，并且消息中间件服务器(一般简单的称之为Broker)中没有消息堆积，那么对于发送的消息设置优先级也就没有什么实质性的意义了，因为生产者刚发送完一条消息就被消费者消费了，那么就相当于Broker中至多只有一条消息，对于单条消息来说优先级是没有什么意义的。

### <a name="26">延迟队列</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
延迟队列存储的是对应的延迟消息，所谓“延迟消息”是指当消息被发送以后，并不想让消费者立刻拿到消息，而是等待特定时间后，消费者才能拿到这个消息进行消费。

延迟队列一般分为两种：
1. 基于消息的延迟和基于队列的延迟。
2. 基于消息的延迟是指为每条消息设置不同的延迟时间，那么每当队列中有新消息进入的时候就会重新根据延迟时间排序，当然这也会对性能造成极大的影响。
> 实际应用中大多采用基于队列的延迟，设置不同延迟级别的队列，比如5s、10s、30s、1min、5min、10min等，每个队列中消息的延迟时间都是相同的，这样免去了延迟排序所要承受的性能之苦，通过一定的扫描策略(比如定时)即可投递超时的消息。

### <a name="27">死信队列</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
**死信队列**用于处理无法被正常消费的消息，即死信消息。由于某些原因消息无法被正确的投递，为了确保消息不会被无故的丢弃，一般将其置于一个特殊角色的队列，这个队列一般称之为死信队列。这种正常情况下无法被消费的消息称为**死信消息**(Dead-Letter Message)
> 死信队列解决的问题是：如果消费者在消费时发生了异常，那么就不会对这一次消费进行确认(Ack),进而发生回滚消息的操作之后消息始终会放在队列的顶部，然后不断被处理和回滚，导致队列陷入死循环。\
> RocketMq的死信队列介绍：当一条消息初次消费失败，消息队列RocketMQ版会自动进行消息重试，达到最大重试次数后，若消费依然失败，则表明消费者在正常情况下无法正确地消费该消息。此时，消息队列RocketMQ版不会立刻将消息丢弃，而是将其发送到该消费者对应的特殊队列中。

RocketMq中支持导出死信消息以及在控制台上重新发送死信消息。
> 一条消息进入死信队列，意味着某些因素导致消费者无法正常消费该消息，因此，通常需要您对其进行特殊处理。排查可疑因素并解决问题后，可以在消息队列RocketMQ版控制台重新发送该消息，让消费者重新消费一次。

- [RocketMq死信队列](https://help.aliyun.com/document_detail/87277.html)

### <a name="28">重试队列</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
重试队列，具体指消费端消费消息失败时，为防止消息无故丢失而重新将消息回滚到Broker中。与回退队列不同的是重试队列一般分成多个重试等级，每个重试等级一般也会设置重新投递延时，重试次数越多投递延时就越大。
> 举个例子：消息第一次消费失败入重试队列Q1，Q1的重新投递延迟为5s，在5s过后重新投递该消息;如果消息再次消费失败则入重试队列Q2，Q2的重新投递延迟为10s，在10s过后再次投递该消息。\
> 重试越多次重新投递的时间就越久，为此需要设置一个上限，超过投递次数就入死信队列。重试队列与延迟队列有相同的地方，都是需要设置延迟级别，它们彼此的区别是：延迟队列动作由内部触发，重试队列动作由外部消费端触发;延迟队列作用一次，而重试队列的作用范围会向后传递。

### <a name="29">消息回溯</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
一般消息在消费完成之后就被处理了，之后再也不能消费到该条消息。消息回溯正好相反，是指消息在消费完成之后，还能消费到之前被消费掉的消息。
> 主要解决的问题是：对于消息而言，经常面临的问题是“消息丢失”，至于是真正由于消息中间件的缺陷丢失还是由于使用方的误用而丢失一般很难追查，如果消息中间件本身具备消息回溯功能的话，可以通过回溯消费复现“丢失的”消息进而查出问题的源头之所在。\
> 典型业务场景: 如consumer做订单分析，但是由于程序逻辑或者依赖的系统发生故障等原因，导致今天消费的消息全部无效，需要重新从昨天零点开始消费，那么以时间为起点的消息重放功能对于业务非常有帮助。

### <a name="30">其他概念</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

消息追踪/轨迹: 引入消息轨迹可以知道消息从生产者触发，经由broker等代理存储，再到消费者消费的整个过程，各个节点的状态、时间、地点等数据汇聚而成完整的链路信息。

消息过滤: 指按照既定的过滤规则为下游用户提供指定类别的消息。
> 以Kafka为例，可以通过客户端提供的ConsumerInterceptor接口或者Kafka Stream的filter功能进行消息过滤。对于rocketmq来说，支持Tag、SQL92和类过滤器(新版去除)等3种模式。

消息审计: 指在消息在生产、存储和消费的整个过程之间对消息个数及延迟的审计，以此来检测是否有数据丢失、是否有数据重复、端到端的延迟又是多少等。

消息路由: 将消息路由到指定的队列中，消费者消费队列里的消息。

# <a name="31">Kafka</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
## <a name="32">基本概念</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/kafka-structure.png)

1. 生产者`Producer`：生产者，负责创建消息，然后投递到 Kafka 集群中，投递时需要指定消息所属的 Topic，同时确定好发往哪个 Partition。
2. 消费者`Consumer`：消费者，会根据它所订阅的 Topic 以及所属的消费组，决定从哪些 Partition 中拉取消息。
    > 消费者可以通过设置消息位移（offset）来控制自己想要获取的数据，比如可以从头读取，最新数据读取，重读读取等功能
3. 话题`Topic`(具体的队列)： Kafka将消息种子(Feed)分门别类， 每一类的消息称之为话题(Topic).
4. 代理`Broker`：已发布的消息保存在一组服务器中，称之为Kafka集群。集群中的每一个服务器都是一个代理(Broker). 
5. 分区`Partition`：为了提高一个队列(topic)的吞吐量，Kafka会把topic进行分区(Partition)。Topic由一个或多个Partition（分区）组成，生产者的消息可以指定或者由系统根据算法分配到指定分区。
    > 使用分区的原因是：方便在集群中扩展，每个 `Partition` 可以通过调整以适应它所在的机器。第二个原因是多个`Partition`文件比单文件可以提升读写效率。\
    其中每个Partition中的消息是有序的，但相互之间的顺序就不能保证了，若Topic有多个Partition，生产者的消息可以指定或者由系统根据算法分配到指定分区，若需要所有消息都是有序的，那么最好只用一个分区。
6. `Zookeeper`：负责集群的元数据管理等功能，比如集群中有哪些 broker 节点以及 Topic，每个 Topic 又有哪些 Partition 等。
7. 消费组`Consumer Group`：一群消费者的集合，向Topic订阅消费消息的单位是Consumers。

## <a name="33">Kafka 高性能设计技术</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/kafka-advantage.png)

### <a name="34">Producer发送端</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
1. 批量发送消息。Kafka 采用了批量发送消息的方式，通过将多条消息按照分区进行分组，然后每次发送一个消息集合，从而大大减少了网络传输的`overhead`。
2. 消息压缩。消息压缩的目的是为了进一步减少网络传输带宽。
    > 其实压缩消息不仅仅减少了网络 IO，它还大大降低了磁盘 IO。因为批量消息在持久化到 Broker 中的磁盘时，仍然保持的是压缩状态，最终是在 Consumer 端做了解压缩操作。
3. 高效序列化。支持自定义类型，只需要提供相应的序列化和反序列化器。用户可以根据实际情况选用快速且紧凑的序列化方式（比如 ProtoBuf、Avro）来减少实际的网络传输量以及磁盘存储量，进一步提高吞吐量。
4. 内存池复用。
    > Producer 一上来就会占用一个固定大小的内存块，比如 64MB，然后将 64 MB 划分成 M 个小内存块（比如一个小内存块大小是 16KB）。当需要创建一个新的 Batch 时，直接从内存池中取出一个 16 KB 的内存块即可，然后往里面不断写入消息，但最大写入量就是 16 KB，接着将 Batch 发送给 Broker ，此时该内存块就可以还回到缓冲池中继续复用了，根本不涉及垃圾回收。
   ![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/kafka-producer.png)

### <a name="35">Broker存储消息</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
1. IO多路复用: kafka采用`Reactor`网络通信模型。
    > `Acceptor`线程，负责监听新的连接。`Processor`线程都有自己的`selector`，负责从`socket`中读写数据。`KafkaRequestHandler`业务处理线程，进行业务处理，然后生成`response`，再交由给`Processor`线程。
      ![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/kafka-broker-connect.png)
2. 磁盘顺序写。快速的存储消息。kafka本质上就是一个队列，是先进先出的，而且消息一旦生产了就不可变。这种有序性和不可变性使得Kafka完全可以「**顺序写**」日志文件。
    > 对于普通的机械磁盘，如果是随机写入，性能确实极差，也就是随便找到文件的某个位置来写数据。但如果是顺序写入，因为可大大节省磁盘寻道和盘片旋转的时间，因此性能提升了 3 个数量级。
3. `Page Cache`技术。利用了操作系统本身的缓存技术，在读写磁盘日志文件时，其实操作的都是内存，然后由操作系统决定什么时候将`Page Cache`里的数据真正刷入磁盘。
    > 大部分组件设计时，往往会选择一种主要介质来存储、另一种介质作为辅助使用。而`Page Cache`技术就是来内存来主力提升系统的性能。并且Kafka作为消息队列，消息先是顺序写入，而且立马又会被消费者读取到。
4. 分区分段结构。当面对海量消息时，单机的存储容量和读写性能有限，对数据进行分区存储，可以更好的利用不同机器的读写能力，应对海量数据的存储。
    > kafka通过水平拆分方案，对数据进行拆分，拆分后的数据子集叫做 Partition（分区），各个分区的数据合集即全量数据。每个`Partition`又被分成了多个`Segment`，引入`Segment`可以防止`Partition`过大。同时做历史消息删除时，常见的操作时需要将文件前面的内容删除，这有悖顺序写的设计。而`Segment`的引入，只需将旧的`Segment`文件删除即可，保证了每个`Segment`的顺序写。

### <a name="36">Consumer消费端</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
1. 稀疏索引。kafka查询的场景主要是能按照`offset`或者`timestamp`查到消息即可。Kafka消息的`offset`设计成有序的，将消息划分成若干个`block`，而稀疏索引记录每个`block`第一条消息的`offset`，查找的时候便可以便捷的使用二分查找高效定位。
    > 稀疏索引不会为**每个搜索关键字创建索引记录**。此处的索引记录包含搜索键和指向磁盘上数据的实际指针。搜索记录时，首先按索引记录进行操作，然后到达数据的实际位置。再进行顺序搜索，直到找到所需的数据为止。\
      B+树随着记录插入需要频繁的页分裂效率较低，而hash索引的常驻内存，若高达几百万的消息写入，会将内存撑爆。
2. mmap(memory mapped files)。kafka在**索引文件的读写**中用到了mmap。
    > mmap是一种内存映射文件的方法，即将一个文件或者其它对象映射到进程的地址空间，实现文件磁盘地址和进程虚拟地址空间中一段虚拟地址的一一对映关系。实现这样的映射关系后，进程就可以采用指针的方式读写操作这一段内存，而系统会自动回**写脏页面**到对应的文件磁盘上，即完成了对文件的操作而不必再调用read,write等系统调用函数。\
    kafka的log文件为什么不使用mmap？mmap 有多少字节可以映射到内存中与地址空间有关，32 位的体系结构只能处理 4GB 甚至更小的文件。Kafka 日志通常足够大，可能一次只能映射部分，因此读取它们将变得非常复杂。然而，索引文件是稀疏的，它们相对较小。将它们映射到内存中可以加快查找过程，这是内存映射文件提供的主要好处。
3. 零拷贝。零拷贝是指数据直接从磁盘文件复制到网卡设备，而无需经过应用程序，减少了内核和用户模式之间的上下文切换。
4. 批量拉取。和生产者批量发送消息类似，消息者也是批量拉取消息的，每次拉取一个消息集合，从而大大减少了网络传输的 overhead。


## <a name="37">数据同步</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

### <a name="38">kafka replica</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
1. 当某个topic的replication-factor为N且N大于1时，每个Partition都会有N个副本(Replica)。kafka的replica包含leader与follower。
2. Replica的个数小于等于Broker的个数，也就是说，对于每个Partition而言，每个Broker上最多只会有一个Replica，因此可以使用Broker id 指定Partition的Replica。
3. 所有Partition的Replica默认情况会均匀分布到所有Broker上。

### <a name="39">ISR</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
常见的同步方式：
- **同步复制**：只有所有的follower把数据拿过去后才commit，一致性好，可用性不高。
- **异步复制**：只要leader拿到数据立即commit，等follower慢慢去复制，可用性高，立即返回，一致性差一些。

Kafka的ISR(in-sync replica set)机制:
1. leader会维护一个与其基本保持同步的Replica列表，该列表称为ISR，每个Partition都会有一个ISR，而且是由leader动态维护。
2. 如果一个flower比一个leader落后太多，或者超过一定时间未发起数据复制请求，则leader将其重ISR中移除。
3. 当ISR中所有Replica都向Leader发送ACK时，leader才commit。
> 该时间阈值由replica.lag.time.max.ms参数设定。leader发生故障后，就会从ISR中选举出新的leader。

### <a name="40">ACK机制</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
ACK 机制：Kafka 采用的是至少一次`At least once`，消息不会丢，但是可能会重复传输。`acks`的默认值即为1，代表我们的消息被leader副本接收之后就算被成功发送。
> 可以配置 `acks = all` ，代表则所有副本都要接收到该消息之后该消息才算真正成功被发送。即保证消息不丢失的，设置消息持久化后再返回消息发送成功响应。对应Spring配置`spring.kafka.producer.acks=-1`

设置等待`acks`返回的机制，有三个值
- `0`：不等待返回的`ack`（可能会丢数据，因为发送消息没有了失败重试机制，但是这是最低延迟）
- `1`：消息发送给kafka分区中的leader后就返回（如果follower没有同步完成leader就宕机了，就会丢数据）
- `-1`（默认）：等待所有follower同步完消息后再发送（绝对不会丢数据）

| ack取值 | ack=0(At Most Once) | ack=1 | ack=-1(At Least Once) |
| --- | --- | --- | --- |
| 取值含义 |  leader接收到消息后，立即返回给生产者 | leader接收到消息记录完毕后，返回给生产者 | leader接收到消息并同步给ISR中的follower节点。等待follower节点都响应leader后才返回给生产者 |
| 特点 | 数据异步复制和存储，速度快、吞吐量高、可用性高、可靠性差 | Leader保存有完整数据，速度较快、吞吐量较高、可用性较高、可靠性较差 | Leader和ISR中的follower节点都保存有数据，同步较慢、可靠性较高 |
| 数据一致性 | 丢失数据风险最高、基本没有一致性 | 丢失数据风险较高 | 丢失数据的风险最低。极端情况(ISR列表为空)时也有丢失数据的风险 |

### <a name="41">故障转移过程</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/kafka-collapse.png)
> LEO：每个副本最大的 offset。\
  HW：消费者能见到的最大的 offset，ISR 队列中最小的 LEO。

**Follower 故障**\
follower 发生故障后会被临时踢出 ISR 集合，待该 follower 恢复后，follower 会 读取本地磁盘记录的上次的 HW，并将 log 文件高于 HW 的部分截取掉，从 HW 开始向 leader 进行同步数据操作。等该 follower 的 LEO 大于等于该 partition 的 HW，即 follower 追上 leader 后，就可以重新加入 ISR 了。

**Leader 故障**\
leader 发生故障后，会从 ISR 中选出一个新的 leader，之后，为保证多个副本之间的数据一致性，其余的 follower 会先将各自的 log 文件高于 HW 的部分截掉，然后从新的 leader 同步数据。
> 这只能保证副本之间的数据一致性，并不能保证数据不丢失或者不重复。

### <a name="42">其他</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
kafka 幂等功能：producer 不论向 server 发送多少重复数据，server 端都只会持久化一条。
> producer的参数中`enable.idompotence`设置为true即可。开启幂等性的producer在初始化时会被分配一个PID，发往同一partition的消息会附带Sequence Number。而broker端会对`<PID,Partition,SeqNumber>`做缓存，当具有相同主键的消息提交时，broker 只会持久化一条。
但是 PID 重启后就会变化，同时不同的partition也具有不同主键，所以幂等性无法保证跨分区会话的Exactly Once。

## <a name="43">消息消费细节</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
Kafka 使用`pull`的方式消费消息。通过建立`长轮询`的模式来拉取消费。
> pull模式不足之处是，如果Kafka没有数据，消费者可能会陷入循环中，一直返回空数据。解决方案是引入参数`timeout`\
> 消费者去Broker拉消息，定义了一个超时时间，也就是说消费者去请求消息，如果有的话马上返回消息，如果当前没有数据可供消费，consumer 会等待一段时间之后再返回，这段时长即为`timeout`，然后再次发起拉消息请求。

具体流程：消费者等待消息，当有消息的时候`Broker`会直接返回消息，如果没有消息都会采取延迟处理的策略，并且为了保证消息的及时性，在对应队列或者分区有新消息到来的时候都**会提醒消息来了**，及时返回消息。

拉取消费的方式的优势：
1. 为broker减压，减少broker的工作量。
2. 消费者端实现各式各样，使用拉取的方式，消费者端更灵活。
3. 匹配消费者端的消费效率，消费速度由消费端控制。

### <a name="44">消费者组与Partition</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
一个consumer group中有多个consumer，一个topic有多个partition，所以必然会涉及到partition的分配问题，即确定哪个partition由哪个consumer来消费。\
Kafka有两种分配策略，一个是RoundRobin，一个是Range，默认为range，当消费者组内消费者发生变化时，会触发分区分配策略（方法重新分配）。

消费者组与Partition关系
1. 假如所有消费者都在**同一个消费者组**中，那么它们将协同消费订阅Topic的部分消息(根据分区与消费者的数量分配)，保存负载均衡；
2. 假如所有消费者都在**不同的消费者组**中，并且订阅了同个Topic。消费者组中的消费者与`Partition`关系如下：
   > 1. 若消费者数小于`partiton`数，且消费者数为一个，那么它就消费所有`partiton`消息；
   > 2. 若消费者数小于`partiton`数，假设消费者数为N，`partiton`数为M，那么每个消费者能消费的分区数为`M/N`或`M/N+1`；
   > 3. 若消费者数等于`partiton`数，那么每个消费者都会均等分配到一个分区的消息；
   > 4. 若消费者数大于`partiton`数，则将会出现部分消费者得不到消息分区，出现空闲的情况；

![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/kafka-partition-consumer.png)

### <a name="45">offset</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
`offset`(消费进度):表示消费者的消费进度，offset在broker以内部`topic(__consumer_offsets)`的方式来保存起来。


## <a name="46">分布式的kafka解决节点宕机或者抖动问题</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

![image](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/kafkaStructure.jpg)
- 红色块的Partition代表的是主分区，紫色的Partition块代表的是备份分区。生产者往topic丢数据，是与主分区交互，消费者消费topic的数据，也是与主分区交互。
- 备份分区仅仅用作于备份，不做读写。如果某个Broker挂了，那就会选举出其他Broker的Partition来作为主分区，这就实现了高可用。

**Partition持久化**(解决宕机消息丢失)：Kafka是将Partition的数据写在磁盘的(消息日志)，不过Kafka只允许追加写入(顺序访问)，避免缓慢的随机 I/O 操作。写入时先缓存一部分，等到足够多数据量或等待一定的时间再批量写入(flush)。



## <a name="47">与ZooKeeper的依赖</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
- 探测broker和consumer的添加或移除。

- 负责维护所有Partition的领导者/从属者关系（主分区和备份分区），如果主分区挂了，需要选举出备份分区作为主分区。

- 维护topic、Partition等元配置信息


### <a name="48">Broker 注册 </a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
Broker是分布式部署并且相互之间相互独立，但是需要有一个注册系统能够将整个集群中的Broker管理起来

在 Zookeeper 上会有一个专门用来进行 **Broker 服务器列表记录的节点**。每个 Broker 在启动时，都会到 Zookeeper 上进行注册，即到/brokers/ids 下创建属于自己的节点。每个 Broker 就会将自己的 IP 地址和端口等信息记录到该节点中去

### <a name="49">Topic 注册 </a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
在 Kafka 中，同一个Topic 的消息会被分成多个分区并将其分布在多个 Broker 上，这些分区信息及与 Broker 的对应关系也都是由 Zookeeper 在维护。比如我创建了一个名字为 my-topic 的主题并且它有两个分区，对应到 zookeeper 中会创建这些文件夹：/brokers/topics/my-topic/Partitions/0、/brokers/topics/my-topic/Partitions/1

### <a name="50">负载均衡 </a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
Kafka 通过给特定 Topic 指定多个 Partition, 而各个 Partition 可以分布在不同的 Broker 上, 这样便能提供比较好的并发能力。 对于同一个 Topic 的不同 Partition，Kafka 会尽力将这些 Partition 分布到不同的 Broker 服务器上。当生产者产生消息后也会尽量投递到不同 Broker 的 Partition 里面。当 Consumer 消费的时候，Zookeeper 可以根据当前的 Partition 数量以及 Consumer 数量来实现动态负载均衡。

### <a name="51">消息 消费进度Offset 记录</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
在消费者对指定消息分区进行消息消费的过程中，需要定时地将分区消息的消费进度Offset记录到Zookeeper上，以便在该消费者进行重启或者其他消费者重新接管该消息分区的消息消费后，能够从之前的进度开始继续进行消息消费。Offset在Zookeeper中由一个专门节点进行记录，其节点路径为:

`/consumers/[group_id]/offsets/[topic]/[broker_id-partition_id]`

节点内容就是Offset的值。



## <a name="52">面试题</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

### <a name="53">Kafka 是什么？主要应用场景有哪些？</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
Kafka 是一个分布式流式处理平台。具有三个关键功能：
- 消息队列：发布和订阅消息流，这个功能类似于消息队列，这也是 Kafka 也被归类为消息队列的原因。
- 容错的持久方式存储记录消息流： Kafka 会把消息持久化到磁盘，有效避免了消息丢失的风险·。
- 流式处理平台： 在消息发布的时候进行处理，Kafka 提供了一个完整的流式处理类库。

Kafka 主要有两大应用场景：
- 消息队列：建立实时流数据管道，以可靠地在系统或应用程序之间获取数据。
- 数据处理： 构建实时的流数据处理程序来转换或处理数据流。

和其他消息队列相比,Kafka的优势在哪里？
- 极致的性能：基于 Scala 和 Java 语言开发，设计中大量使用了批量处理和异步的思想，最高可以每秒处理千万级别的消息。
- 生态系统兼容性无可匹敌：Kafka 与周边生态系统的兼容性是最好的没有之一，尤其在大数据和流计算领域。

#### <a name="54">kafka优点</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
1. Kafka操作的是序列文件I/O（序列文件的特征是按顺序写，按顺序读），为保证顺序，Kafka强制点对点的按顺序传递消息，这意味着，一个consumer在消息流（或分区）中只有一个位置。
2. Kafka不保存消息的状态，即消息是否被“消费”。一般的消息系统需要保存消息的状态，并且还需要以随机访问的形式更新消息的状态。而Kafka 的做法是保存Consumer在Topic分区中的位置offset，在offset之前的消息是已被“消费”的，在offset之后则为未“消费”的，并且offset是可以任意移动的，这样就消除了大部分的随机IO。
3. Kafka支持点对点的批量消息传递。
4. Kafka的消息存储在OS page Cache（页缓存，page cache的大小为一页，通常为4K，在Linux读写文件时，它用于缓存文件的逻辑内容，从而加快对磁盘上映像和数据的访问）。

### <a name="55">kafka 为什么快</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
顺序写磁盘、大量使用内存页 、零拷贝技术的使用、消息压缩及批量发送

#### <a name="56">顺序写磁盘</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
在顺序读写的情况下，磁盘的顺序读写速度和内存持平。因为硬盘是机械结构，每次读写都会寻址->写入，其中寻址是一个“机械动作”，它是最耗时的。而且 Linux 对于磁盘的读写优化也比较多，包括 read-ahead 和 write-behind，磁盘缓存等。

使用磁盘操作有以下几个好处：
- 磁盘顺序读写速度超过内存随机读写。
- JVM 的 GC 效率低，内存占用大。使用磁盘可以避免这一问题。
- 系统冷启动后，磁盘缓存依然可用。

为了避免磁盘被撑满的情况，Kakfa 提供了两种策略来删除数据：
- 「基于时间」 （默认七天）
- 「基于 Partition 文件大小」

#### <a name="57">大量使用内存页</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
mmap （Memory Mapped Files）直接利用操作系统的Page来实现文件到物理内存的映射，完成之后对物理内存的操作会直接同步到硬盘。mmf 通过内存映射的方式大大提高了IO速率，省去了用户空间到内核空间的复制。

#### <a name="58">零拷贝技术</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
传统 Read/Write 方式进行网络文件传输，在传输过程中，文件数据实际上是经过了四次 Copy 操作，其具体流程细节如下：

1. 调用 Read 函数，文件数据被 Copy 到内核缓冲区。
2. Read 函数返回，文件数据从内核缓冲区 Copy 到用户缓冲区
3. Write 函数调用，将文件数据从用户缓冲区 Copy 到内核与 Socket 相关的缓冲区。
4. 数据从 Socket 缓冲区 Copy 到相关协议引擎。
`硬盘—>内核 buf—>用户 buf—>Socket 相关缓冲区—>协议引擎`

Sendfile 系统调用则提供了一种减少以上多次 Copy，提升文件传输性能的方法。以简化网络上和两个本地文件之间的数据传输。

#### <a name="59">消息压缩、批量发送</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
批量发送：Kafka允许进行批量发送消息，producter发送消息的时候，可以将消息缓存在本地，等到了固定条件发送到 Kafka 。
数据压缩：，Producer可以通过GZIP或Snappy格式对消息集合进行压缩。压缩的好处就是减少传输的数据量，减轻对网络传输的压力。


### <a name="60">Kafka 如何保证消息队列不丢失</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

ACK 机制：Kafka 采用的是至少一次（At least once），消息不会丢，但是可能会重复传输。 acks 的默认值即为1，代表我们的消息被leader副本接收之后就算被成功发送。我们可以配置 acks = all ，代表则所有副本都要接收到该消息之后该消息才算真正成功被发送。
> 即保证消息不丢失的，设置消息持久化后再返回消息发送成功响应。
```
spring.kafka.producer.acks=-1
```

设置等待acks返回的机制，有三个值
- `0`：不等待返回的`ack`（可能会丢数据，因为发送消息没有了失败重试机制，但是这是最低延迟）
- `1`：消息发送给kafka分区中的leader后就返回（如果follower没有同步完成leader就宕机了，就会丢数据）
- `-1`（默认）：等待所有follower同步完消息后再发送（绝对不会丢数据）

| ack取值 | ack=0 | ack=1 | ack=-1(all) |
| --- | --- | --- | --- |
| 取值含义 |  leader接收到消息后，立即返回给生产者 | leader接收到消息记录完毕后，返回给生产者 | leader接收到消息并同步给ISR中的follower节点。等待follower节点都响应leader后才返回给生产者 |
| 特点 | 数据异步复制和存储，速度快、吞吐量高、可用性高、可靠性差 | Leader保存有完整数据，速度较快、吞吐量较高、可用性较高、可靠性较差 | Leader和ISR中的follower节点都保存有数据，同步较慢、可靠性较高 |
| 数据一致性 | 丢失数据风险最高、基本没有一致性 | 丢失数据风险较高 | 丢失数据的风险最低。极端情况(ISR列表为空)时也有丢失数据的风险 |


设置分区:为了保证 leader 副本能有 follower 副本能同步消息，我们一般会为 topic 设置 replication.factor >= 3。保证每个 分区(Partition) 至少有 3 个副本.

关闭 unclean leader 选举: leader 副本发生故障时， follower 副本与leader副本 同步程度不一致的副本不会加入选举。
> `unclean.leader.election.enable = false`

生产者端：
  1. 进行本地buffer，批量发送消息。设置`producer.type=async` 表示消息批量发送。默认为sync
  2. 设置至少写入到多个副本才算成功，也是提升数据持久性的一个参数，与acks配合使用。`min.insync.replicas> 1`
  
消费者端：Kafka consumer默认是自动提交位移的，设置` enable.auto.commit=false`关闭自动提交位移，在消息被完整处理之后再手动提交位移，保证消息不丢失。
```

// 自动提交offset
spring.kafka.consumer.enable-auto-commit=false
```

---
### <a name="61">kafka 高可用是如何实现?</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>


### <a name="62">kafka会存在数据丢失问题</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
> 数据在消息队列是如何持久化(磁盘？数据库？Redis？分布式文件系统？)

Kafka会将Partition以消息日志的方式(落磁盘)存储起来，通过 顺序访问IO和缓存(等到一定的量或时间)才真正把数据写到磁盘上，来提高速度。

### <a name="63">想要保证消息（数据）是有序的，怎么做？</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
Kafka会将数据写到Partition，单个Partition的写入是有顺序的。如果要保证全局有序，那只能写入一个Partition中。如果要消费也有序，消费者也只能有一个。

### <a name="64">为什么在消息队列中重复消费了数据</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
凡是分布式就无法避免网络抖动/机器宕机等问题的发生，很有可能消费者A读取了数据，还没来得及消费，就挂掉了。Zookeeper发现消费者A挂了，让消费者B去消费原本消费者A的分区，等消费者A重连的时候，发现已经重复消费同一条数据了。(各种各样的情况，消费者超时等等都有可能…)
  
如果业务上不允许重复消费的问题，最好消费者那端做业务上的校验（如果已经消费过了，就不消费了）
  
# <a name="65">RocketMQ</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

## <a name="66">基本概念</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
消息生产者（Producer）：负责生产消息，一般由业务系统负责生产消息。RocketMQ提供多种发送方式，同步发送、异步发送、顺序发送、单向发送。同步和异步方式均需要Broker返回确认信息，单向发送不需要。

消息消费者（Consumer）：负责消费消息，一般是后台系统负责异步消费。
  - 提供了两种消费形式：拉取式消费、推动式消费。
    - 拉取式消费：应用通常主动调用Consumer的拉消息方法从Broker服务器拉消息、主动权由应用控制。
    - 推动式消费：Broker收到数据后会主动推送给消费端，该消费模式一般实时性较高。
  - 提供两种消费模式：集群消费和广播消费
    - 集群消费模式下,相同Consumer Group的每个Consumer实例平均分摊消息。
    - 广播消费模式下，相同Consumer Group的每个Consumer实例都接收全量的消息。

主题（Topic）：表示一类消息的集合，每个主题包含若干条消息，每条消息只能属于一个主题，是RocketMQ进行消息订阅的基本单位。

代理服务器（Broker Server）：消息中转角色，负责存储消息、转发消息。代理服务器在RocketMQ系统中负责接收从生产者发送来的消息并存储、同时为消费者的拉取请求作准备。代理服务器也**存储消息相关的元数据，包括消费者组、消费进度偏移和主题和队列消息**等

名字服务（Name Server）：名称服务充当路由消息的提供者。生产者或消费者能够通过名字服务查找各主题相应的Broker IP列表。多个Namesrv实例组成集群，但相互独立，没有信息交换。

生产者组（Producer Group）：同一类Producer的集合，这类Producer发送同一类消息且发送逻辑一致。如果发送的是事务消息且原始生产者在发送之后崩溃，则Broker服务器会联系同一生产者组的其他生产者实例以提交或回溯消费。

消费者组（Consumer Group）：同一类Consumer的集合，这类Consumer通常消费同一类消息且消费逻辑一致。消费者组使得在消息消费方面，实现负载均衡和容错的目标变得非常容易。要注意的是，消费者组的消费者实例必须订阅完全相同的Topic。RocketMQ 支持两种消息模式：集群消费和广播消费。
- 标签（Tag）：为消息设置的标志，用于同一主题下区分不同类型的消息。来自同一业务单元的消息，可以根据不同业务目的在同一主题下设置不同标签。标签能够有效地保持代码的清晰度和连贯性，并优化RocketMQ提供的查询系统。

## <a name="67">基本架构</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
![avatar](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/rocketmqAC.jpg)
主要包含四部分Producer、Consumer、Broker、NameServer

- Producer与NameServer集群中的其中一个节点（随机选择）建立长连接，定期从NameServer获取Topic路由信息，并向**提供Topic 服务的Master建立长连接**，且定时向Master发送心跳。
- Consumer与NameServer集群中的其中一个节点（随机选择）建立长连接，定期从NameServer获取Topic路由信息，并向**提供Topic服务的Master、Slave建立长连接**，且定时向Master、Slave发送心跳。

## <a name="68">优缺点</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
- 单机吞吐量：十万级
- 可用性：非常高，分布式架构
- 支持10亿级别的消息堆积，不会因为堆积导致性能下降
- 源码是java，我们可以自己阅读源码，定制自己公司的MQ，可以掌控
- 天生为金融互联网领域而生，支持可靠性要求很高的场景，尤其是电商里面的订单扣款，以及业务削峰，在大量交易涌入时，后端可能无法及时处理的情况，经历阿里双十一考验。

缺点：
- 支持的客户端语言不多，目前是java及c++，其中c++不成熟
- 社区活跃度不是特别活跃那种
- 没有在 mq 核心中去实现JMS等接口，有些系统要迁移需要修改大量代码

## <a name="69">事务实现</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>
RocketMQ采用了2PC的思想来实现了提交事务消息，同时增加一个补偿逻辑来处理二阶段超时或者失败的消息。
![avatar](https://github.com/rbmonster/file-storage/blob/main/learning-note/other/middleware/rocketMqTransaction.jpg)

2pc主要缺点，协调者故障、阻塞、宕机，导致commit消息未全部发送完毕，参与者预提交事务消息请求阻塞。rocketmq引入参与者的回查补偿机制，解决该问题。

- 补偿流程：

(1) 对没有Commit/Rollback的事务消息（pending状态的消息），从服务端发起一次“回查”

(2) Producer收到回查消息，检查回查消息对应的本地事务的状态

(3) 根据本地事务状态，重新Commit或者Rollback

其中，补偿阶段用于解决消息Commit或者Rollback发生超时或者失败的情况。
