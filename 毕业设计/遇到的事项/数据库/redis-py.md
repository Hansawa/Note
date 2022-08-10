## 类

1. Redis: 
2. StrictRedis: 会用传入的 host 与 port 等参数构造一个 ConnectionPool，因此不需要对连接进行手动管理
3. ConnectionPool

## 方法

1. zadd(name, mapping): 3.0后，使用有序集合名字与要添加的数据，数据的类型为字典，字典中键为 member，值为 score
1. zscan(name, cursor=0, count=None): 选择名字为 name 的有序集合，返回从 cursor 开始的 count 行元素，返回类型为 list。注意，count 只是一个给数据库的暗示（hint），返回的个数可多可少，而且当有序集合的元素个数少于 redis.windows-service.conf 文件中的有序集合最大压缩列表条目数（zset-max-ziplist-entries = 128）或有序集合最大压缩列表值的长度（zset-max-ziplist-value = 64）时，程序会将全部的元素返回，而不是返回 count 个。

创建连接后 redis 自动把连接交给连接池管理，因此不需要手动关闭连接

要使从 redis 获取的值为字符串，要在创建连接（实例化 StrictRedis 的时候）将参数 decode_response 的值设置为 True