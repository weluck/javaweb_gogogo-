## 解决方案

1. List<String> list = new Vector<>();
2. List<String> list = Collections. synchronizedList(new ArrayList<>());
3. List<String> list = new CopyOnWriteArrayList<> ();

**CopyOnWrite写入时复制
COW是计算机程序设计领域的一种优化策略;
多个线程调用的时候，list， 读取的时候，固定的，写入(覆盖)
在写入的时候避免覆盖，造成数据问题!
读写分离**

CopyOnWrite用的是Lock锁,List用的是sychronized,前者效率更高
