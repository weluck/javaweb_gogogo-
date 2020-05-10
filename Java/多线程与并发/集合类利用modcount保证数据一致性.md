1.什么是modcount?

modCount在AbstractList和HashMap中都有定义。这里以ArrayList为例，AbstractList被ArrayList类继承，注意！！HashSet集合的iterator方法由HashMap类负责实现，它本身没有modCount这个变量，而是存在于HashMap类中。

2.modCount的作用

简而言之：记录集合被修改的次数
详细解读：当集合（诸如ArrayList、HashMap对象）被修改（调用集合的add()方法或者remove()方法）时，modCount的值会自动+1。

3.什么是expectedModcount?
expectedModcount定义在AbstractList类的内部类Itr中

			public abstract class AbstractList<E> extends AbstractCollection<E> implements List<E> {
					.......
					private class Itr implements Iterator<E> {
							int expectedModCount = modCount;
					}
					
			}



并且Itr实现了Iterator接口

4.modCount如何与expectedModcount配合使得Iterator迭代器不可同时修改集合？

流程：首先当ArrayList对象调用iterator()方法时会返回一个Itr对象，注意！此时expectedModcount被初始化为modCount的值，记录了当前集合的修改次数。此时如果有另外一个ListIterator迭代器(可以执行add()方法，与iterator功能相似)调用了add（）方法修改了集合，注意！此时集合内部定义的modCount的值+1。如果现在前一个iterator迭代器准备访问集合，调用next()方法，就会抛出 ConcurrentModificationException异常。原因就是当迭代器调用next()方法时会检查定义在迭代器内部的expectedModCount的值是否等于定义在集合中的modcount。如果不相等就表明集合已经被修改过，然后抛出异常。

5.目的

防止iterator在遍历数据时数据是混乱的，例如，一个迭代器指向另一个迭代器刚刚删除的元素前面，现在这个迭代器就是无效的，并且不应该再使用。
