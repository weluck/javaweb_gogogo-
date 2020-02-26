Condition因素出Object监视器方法（ wait ， notify和notifyAll ）成不同的对象，以得到具有多个等待集的每个对象，通过将它们与使用任意的组合的效果Lock个实现。 Lock替换synchronized方法和语句的使用， Condition取代了对象监视器方法的使用。 
条件（也称为条件队列或条件变量 ）为一个线程暂停执行（“等待”）提供了一种方法，直到另一个线程通知某些状态现在可能为真。 因为访问此共享状态信息发生在不同的线程中，所以它必须被保护，因此某种形式的锁与该条件相关联。 等待条件的关键属性是它原子地释放相关的锁并挂起当前线程，就像Object.wait 。 

一个Condition实例本质上绑定到一个锁。 要获得特定Condition实例的Condition实例，请使用其newCondition()方法。 

例如，假设我们有一个有限的缓冲区，它支持put和take方法。 如果在一个空的缓冲区尝试一个take ，则线程将阻塞直到一个项目可用; 如果put试图在一个完整的缓冲区，那么线程将阻塞，直到空间变得可用。 我们希望在单独的等待集中等待put线程和take线程，以便我们可以在缓冲区中的项目或空间可用的时候使用仅通知单个线程的优化。 这可以使用两个Condition实例来实现。 
```
  class BoundedBuffer {
   final Lock lock = new ReentrantLock();
   final Condition notFull  = lock.newCondition(); 
   final Condition notEmpty = lock.newCondition(); 

   final Object[] items = new Object[100];
   int putptr, takeptr, count;

   public void put(Object x) throws InterruptedException {
     lock.lock(); try {
       while (count == items.length)
         notFull.await();
       items[putptr] = x;
       if (++putptr == items.length) putptr = 0;
       ++count;
       notEmpty.signal();
     } finally { lock.unlock(); }
   }

   public Object take() throws InterruptedException {
     lock.lock(); try {
       while (count == 0)
         notEmpty.await();
       Object x = items[takeptr];
       if (++takeptr == items.length) takeptr = 0;
       --count;
       notFull.signal();
       return x;
     } finally { lock.unlock(); }
   }
 } （ ArrayBlockingQueue类提供此功能，因此没有理由实现此示例使用类。） 
 ```
Condition实现可以提供Object监视器方法的行为和语义，例如有保证的通知顺序，或者在执行通知时不需要锁定。 如果一个实现提供了这样的专门的语义，那么实现必须记录这些语义。 

需要注意的是Condition实例只是普通的对象，其本身作为一个目标synchronized语句，可以有自己的监视器wait和notification个方法调用。 获取Condition实例的监视器锁或使用其监视方法与获取与该Condition相关联的Condition或使用其waiting和signalling方法没有特定关系。 建议为避免混淆，您永远不会以这种方式使用Condition实例，除了可能在自己的实现之内。 

除非另有说明，传递任何参数的null值将导致NullPointerException被抛出。 

      Condition好处在于可以指定唤醒目标。
