Redis Cluster
-----

## 实验方法
通过Docker官方Redis实现，没有额外脚本


## 单个Master
这个是普通开发环境最简单的实现，一个Master下拖着2个Slave，通过AOF/RDB（类似MySQL的Binlog）方式复制到从机器
配置实现很简单，通过`slaveof xxx`实现即可

这种方案搭建简单，一般需要配合sentinal使用


## 多台Master
基于Hash的Slot分片