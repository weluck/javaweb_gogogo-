c++中map的一些方法:

* begin() 返回指向map头部的迭代器
* clear() 删除所有元素
* count() 返回指定元素出现的次数
* empty() 如果map为空则返回true
* end()   返回指向map末尾的迭代器
* erase() 删除一个元素
* find()  查找一个元素
* insert()插入元素
* max_size()返回可以容纳的最大元素个数
* size()  返回map中元素的个数
* swap()  交换两个map
* containsKey()  是否存在键
* get_allocator()  返回map的配置器
* key_comp()       返回比较元素key的函数
* lower_bound()    返回键值>=给定元素的第一个位置
* max_size()       返回可以容纳的最大元素个数
* rbegin()         返回一个指向map尾部的逆向迭代器
* rend()           返回一个指向map头部的逆向迭代器
* upper_bound()     返回键值>给定元素的第一个位置
    
求键用->first,值->second.
