### Redis的一些应用场景

- 利用 setnx 实现分布式锁

  setnx key value 当key不存在时,加入value,返回1

  当key存在时,直接返回0,由于redis使用的文件事件处理器是单线程的,能保证安全.

- 利用INCR命令生成分布式全局唯一ID

  Redis的INCR命令具备了"INCR AND GET"的原子操作

  redis是单线程架构,INCR命令不会出现ID重复

- 利用redis生成排行榜:例如新浪微博的热搜,视频按照发布时间排序等等.

- 计数器:页面浏览次数,视频播放次数,incr就好了

  