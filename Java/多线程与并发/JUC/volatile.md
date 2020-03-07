Volatile为Java虚拟机提供轻显级的同步机制
## 1. 保证可见性。
  ```java
  public class JMMDemo {
    // 不加 volatile 程序就会死循环！
    // 加 volatile 可以保证可见性
    private volatile static int num = 0;

    public static void main(String[] args) { // main

        new Thread(()->{ // 线程 1 对主内存的变化不知道的
            while (num==0){

            }
        }).start();

        try {
            TimeUnit.SECONDS.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        num = 1;
        System.out.println(num);

    }
  }
  ```
## 2. 不保证原子性。
  ```java
  package com.kuang.tvolatile;

import java.util.concurrent.atomic.AtomicInteger;

// volatile 不保证原子性
public class VDemo02 {

    // volatile 不保证原子性
    // 原子类的 Integer
    private volatile static AtomicInteger num = new AtomicInteger();

    public static void add(){
        // num++; // 不是一个原子性操作
        num.getAndIncrement(); // AtomicInteger + 1 方法， CAS
    }

    public static void main(String[] args) {

        //理论上num结果应该为 2 万
        for (int i = 1; i <= 20; i++) {
            new Thread(()->{
                for (int j = 0; j < 1000 ; j++) {
                    add();
                }
            }).start();
        }

        while (Thread.activeCount()>2){ // main  gc
            Thread.yield();
        }
        System.out.println(Thread.currentThread().getName() + " " + num);
    }
}
  ```
  可以不用sychronized, 使用原子类解决原子性问题，java.util.concurrent.atomic
## 3. 禁止指令重排。
指令重排:计算机并不一定按程序执行顺序去执行。<br>
源代码->编译器优化的重排->指令并行也可能会重排->内存系统也会重排-->执行
