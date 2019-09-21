ArrayList 类似于 C++ 的 vector 模板。ArrayList 与 vector 都是泛型类型。 但 是 C++ 的 vector 模板为了便于访问元素重栽了 [ ] 运算符。由于 Java 没有运算符重载，所以必须调用显式的方法。此外，C++ 向量是值拷贝。如果 a 和 b 是两个向量， 賦值操作 a = b 将会构造一个与 b 长度相同的新向量 a, 并将所有的元素由 b 拷贝到 a, 而在Java 中， 这条赋值语句的操作结果是让 a 和 b 引用同一个数组列表。

•ArrayList<E> ( )
构造一个空数组列表。 <br>•ArrayList<E> (intinitialCapacity)
用指定容量构造一个空数组列表。
参数：initalCapacity 数组列表的最初容量<br>
•boolean add(E obj)
在数组列表的尾端添加一个元素。 永远返回 true。
参数：obj 添加的元素<br>
•int size( )
返回存储在数组列表中的当前元素数量。（这个值将小于或等于数组列表的容量。)<br> •void ensureCapacity(intcapacity)
确保数组列表在不重新分配存储空间的情况下就能够保存给定数量的元素。
参数：capacity 需要的存储容量<br>
•void trimToSize( )
将数组列表的存储容量削减到当前尺寸。
 • void set(int index，E obj)
设置数组列表指定位置的元素值， 这个操作将覆盖这个位置的原有内容。
参数： index 位置（必须介于 0 ~ size()-l 之间）<br>
obj 新的值
• E get(int index)
获得指定位置的元素值。
参数：index 获得的元素位置（必须介于 0 ~ size()-l 之间）<br> • void add(int index,E obj)
向后移动元素，以便插入元素。
参数：index 插入位置（必须介于 0 〜 size()-l 之间）<br>
obj 新元素<br>
• E removed nt index)
删除一个元素，并将后面的元素向前移动。被删除的元素由返回值返回。
参数：index 被删除的元素位置（必须介于 0 〜 size()-l 之间）<br>

java中的length属性是针对数组说的,比如说你声明了一个数组,想知道这个数组的长度则用到了length这个属性.<br>
java中的length()方法是针对字符串String说的,如果想看这个字符串的长度则用到length()这个方法.<br>
java中的size()方法是针对泛型集合说的,如果想看这个泛型有多少个元素,就调用此方法来查看!<br>
