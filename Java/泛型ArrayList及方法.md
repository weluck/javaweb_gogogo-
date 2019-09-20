ArrayList 类似于 C++ 的 vector 模板。ArrayList 与 vector 都是泛型类型。 但 是 C++ 的 vector 模板为了便于访问元素重栽了 [ ] 运算符。由于 Java 没有运算符重载，所以必须调用显式的方法。此外，C++ 向量是值拷贝。如果 a 和 b 是两个向量， 賦值操作 a = b 将会构造一个与 b 长度相同的新向量 a, 并将所有的元素由 b 拷贝到 a, 而在Java 中， 这条赋值语句的操作结果是让 a 和 b 引用同一个数组列表。

•A r r a y L i s t< E > ( )
构造一个空数组列表。 <br>•A r r a y L i s t < E > ( i n t i n i t i a l C a p a c i t y)
用指定容量构造一个空数组列表。
参数：initalCapacity 数组列表的最初容量<br>
•b o o l e a n a d d( E o b j )
在数组列表的尾端添加一个元素。 永远返回 true。
参数：obj 添加的元素<br>
•i n t s i z e( )
返回存储在数组列表中的当前元素数量。（这个值将小于或等于数组列表的容量。)<br> •v o i d e n s u r e C a p a c i t y( i n t c a p a c i t y)
确保数组列表在不重新分配存储空间的情况下就能够保存给定数量的元素。
参数：capacity 需要的存储容量<br>
•v o i d t r i m T o S i z e( )
将数组列表的存储容量削减到当前尺寸。

java中的length属性是针对数组说的,比如说你声明了一个数组,想知道这个数组的长度则用到了length这个属性.<br>
java中的length()方法是针对字符串String说的,如果想看这个字符串的长度则用到length()这个方法.<br>
java中的size()方法是针对泛型集合说的,如果想看这个泛型有多少个元素,就调用此方法来查看!<br>
