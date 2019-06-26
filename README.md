# TTC-hmily-demo
解决方案之--补偿事务TCC框架Hmily

1.分布式事务基础理论

  ①CAS定理

  ②BASE理论

2.分布式事务解决方案

  ①基于XA协议的两段式提交（2PC），事务在数据库处理，数据库压力大

  ②TCC（try confirm cancel），分布式事务分成了三个阶段，尝试、确认、取消

      

阶段
职责
尝试	对业务系统做检测及资源预留
确认	对业务系统做确认提交
取消	在业务执行错误，需要回滚的状态下执行的业务取消，预留资源释放


3.MQ事务消息

    第一阶段Prepared消息，会拿到消息的地址。

    第二阶段执行本地事务，

    第三阶段通过第一阶段拿到的地址去访问消息，并修改状态。

4.TCC案例分享–hmily分布式事务框架

    框架特性：

支持嵌套事务(Nested transaction support).
采用disruptor框架进行事务日志的异步读写，与RPC框架的性能毫无差别。
支持SpringBoot-starter 项目启动，使用简单。
 RPC框架支持 : dubbo,motan,springcloud。
本地事务存储支持 : redis,mongodb,zookeeper,file,mysql。
事务日志序列化支持 ：java，hessian，kryo，protostuff。
 采用Aspect AOP 切面思想与Spring无缝集成，天然支持集群。
 RPC事务恢复，超时异常恢复等。