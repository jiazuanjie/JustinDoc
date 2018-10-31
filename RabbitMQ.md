## 什么是消息队列
消息是指在应用间传送的数据。它可以是一个字符串，也可以是一个对象。

消息队列则是一种应用间的通信方式，消息发送后可以立即返回，由消息系统来确保消息的可靠传递。消息的生产者（Publisher）只管把消息发布到MQ中而不用管谁来消费，消息的消费者（Consumer)只管从MQ中获取消息而不管是谁发布的

## RabbitMQ

#### 队列（Queue）、生产者（Publisher）、消费者（Consumer）

> 队列是RabbitMQ的内部对象，用户存储消息。生产者生产消息放到队列中，消费者则可以从队列中获取消息并消费

![队列](https://upload-images.jianshu.io/upload_images/5015984-066ff248d5ff8eed.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/401/format/webp)

> 多个消费者可以订阅同一个队列，这时队列中的消息就会被平均分摊给多个消费者进行处理，而不是每个消费者都收到所有的消息处理

![多消费者队列](https://img-blog.csdn.net/20170828201853982?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvZHJlYW1jaGFzZXJpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

#### 交换器（Exchange）、绑定（Binding）

> 当然，消息从生产到消费不是简单的队列直达，实际上生产者需要将消息发送到Exchange上，再通过Binding将Exchange和Queue关联起来。
Binding可以理解成是将Exchange和Queue连接起来的路由规则，Exchange也可以理解成由路由规则构成的路由表

![路由](https://img-blog.csdn.net/20170828202419941?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvZHJlYW1jaGFzZXJpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

> RabbitMQ结构图

![](https://img-blog.csdn.net/20170828204522460?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvZHJlYW1jaGFzZXJpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

#### 消息确认机制

> 如果消息被某个消费者<b style='color:red;font-size:1.5rem'>正确</b>的接收到了，那么该消息就会从队列中移除。  
那么怎么定义正确收到？通过ack。每个消息都要被acknowledged（确认）。  
如果一个消息没有被确认，那么它就会被发送给下一个消费者。

## 参考资料

* amqplib：<a href='http://www.squaremobius.net/amqp.node/channel_api.html#overview'>点我达</a>  
* RabbitMQ：<a href='https://www.rabbitmq.com/'>点我达</a>
* 安装配置教程：<a href='https://www.jianshu.com/p/79ca08116d57'>点我达</a>  
