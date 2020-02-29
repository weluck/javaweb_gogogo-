Semaphore(int permits) 
创建一个 Semaphore与给定数量的许可证和非公平公平设置。  
Semaphore(int permits, boolean fair) 
创建一个 Semaphore与给定数量的许可证和给定的公平设置。  
void acquire() 
从该信号量获取许可证，阻止直到可用，或线程为 interrupted 。  
void acquire(int permits) 
从该信号量获取给定数量的许可证，阻止直到所有可用，否则线程为 interrupted 。  
void acquireUninterruptibly() 
从这个信号灯获取许可证，阻止一个可用的。  
void acquireUninterruptibly(int permits) 
从该信号量获取给定数量的许可证，阻止直到所有可用。  
int availablePermits() 
返回此信号量中当前可用的许可数。  
int drainPermits() 
获取并返回所有可立即获得的许可证。  
protected Collection<Thread> getQueuedThreads() 
返回一个包含可能正在等待获取的线程的集合。  
int getQueueLength() 
返回等待获取的线程数的估计。  
boolean hasQueuedThreads() 
查询任何线程是否等待获取。  
boolean isFair() 
如果此信号量的公平设置为真，则返回 true 。  
protected void reducePermits(int reduction) 
缩小可用许可证的数量。  
void release() 
释放许可证，将其返回到信号量。  
void release(int permits) 
释放给定数量的许可证，将其返回到信号量。  
String toString() 
返回一个标识此信号量的字符串及其状态。  
boolean tryAcquire() 
从这个信号量获得许可证，只有在调用时可以使用该许可证。  
boolean tryAcquire(int permits) 
从这个信号量获取给定数量的许可证，只有在调用时全部可用。  
boolean tryAcquire(int permits, long timeout, TimeUnit unit) 
从该信号量获取给定数量的许可证，如果在给定的等待时间内全部可用，并且当前线程尚未 interrupted 。  
boolean tryAcquire(long timeout, TimeUnit unit) 
如果在给定的等待时间内可用，并且当前线程尚未 到达 interrupted，则从该信号量获取许可。  
