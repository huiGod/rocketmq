1. 新建ROCKETMQ_HOME目录，目录下创建conf、logs、store 目录
2. 拷贝 rocketmq/distribution/conf 下的broker.conf、logback_broker.xml、logback_namesrv.xml 到 ROCKETMQ_HOME 目录下的 conf 中
3. log 文件中的${user.home}全部替换为你的rocketmq运行目录
4. 修改broker.conf文件
```$xslt
brokerClusterName = DefaultCluster
brokerName = broker-a
brokerId = 0
# 这是nameserver的地址
namesrvAddr=127.0.0.1:9876
deleteWhen = 04
fileReservedTime = 48
brokerRole = ASYNC_MASTER
flushDiskType = ASYNC_FLUSH
# 这是存储路径，你设置为你的rocketmq运行目录的store子目录
storePathRootDir=你的rocketmq运行目录的store子目录
# 这是commitLog的存储路径
storePathCommitLog=你的rocketmq运行目录的store子目录/commitlog
# consume queue文件的存储路径
storePathConsumeQueue=你的rocketmq运行目录的store子目录/consumequeue
# 消息索引文件的存储路径
storePathIndex=你的rocketmq运行目录的store子目录/index
# checkpoint文件的存储路径
storeCheckpoint=你的rocketmq运行目录的store子目录/checkpoint
# abort文件的存储路径
abortFile=你的rocketmq运行目录/abort
```
5. BrokerStartup启动
启动参数：-c /Users/huigod/Documents/rocketMQ/conf/broker.conf
环境变量：ROCKETMQ_HOME=/Users/huigod/Documents/rocketMQ
6. NamesrvStartup
环境变量：ROCKETMQ_HOME=/Users/huigod/Documents/rocketMQ
7. 启动 RocketMQ控制台
git clone https://github.com/apache/rocketmq-externals.git
cd rocketmq-externals/rocketmq-console
mvn package -DskipTests
java -jar rocketmq-console-ng-1.0.1.jar --server.port=8080 --rocketmq.config.namesrvAddr=127.0.0.1:9876