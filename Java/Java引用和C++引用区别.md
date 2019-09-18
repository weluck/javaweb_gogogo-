按值调用 （call by value) 表示方法接收的是调用者提供的值。而按引用调用 （ call by reference)
表示方法接收的是调用者提供的变量地址。一个方法可以修改传递引用所对应的变量值，而不能修改传递值调用所对应的变量值。

java的引用并不是引用，而是隐藏的指针！！！要把java的引用当作指针来看！！！而c++的引用才是真正的引用

java的引用只是能操作原内存，不能操作指向内存的指针，而c++的引用不仅是操作原内存，更是操作指向原内存的指针！

java类对象近似C++指针

java数组、类、接口按值传递的时候都是传递对象的地址，也是值传递

c++里对对象的引用相当于二级指针，而java里的引用只是一级指针

new 类名();创建对象
类名 xxx 创建对象的引用

JAVA的引用反应到c里准确有三点

类 string s = new string();

一、java的引用实际上是个一级指针，
在使用new的对象对其赋值时，new的对象省略了&，平时使用java的引用时省略了*即真实应该是string * s1 = new string(); string * s2 = new string();

二、在对象的引用之间互相赋值时，都是赋的各自存储的地址值，
即s1 = s2;也就说，java无法存在二阶指针，因为创建出来的实际上都是一级指针。而c++里一级指针的引用（当然实际上他是个二级指针），为 string * & s3 = s1;当*s3时可以修改s1所指向的内存，但引用的作用在于，他也可以修改s1所存储的地址，例s3 = new string();此时s1的地址也已经变化，总得来说

c++的引用时高阶指针向低阶指针，而java引用是同阶指针指向同阶指针，总得来说其实都是一阶指针，故其实都是自身存储的地址值在相互间的传递，而不是将自身地址值赋给其他的指针

故java中引用间互相传递可以更改所指向的共同内存，却无法更改各自所存储的地址值，即无法更改各自的引用所指向的方向

且java中只有值传递没有引用传递

以下程序证明：
public class Main{
     public static void main(String[] args){
          Foo f = new Foo("f");
          changeReference(f); // It won't change the reference!
          modifyReference(f); // It will modify the object that the reference variable "f" refers to!
     }
     public static void changeReference(Foo a){
          Foo b = new Foo("b");
          a = b;
     }
     public static void modifyReference(Foo c){
          c.setAttribute("c");
     }
}
①Foo f = new Foo(“f”);
![image1](https://img-blog.csdn.net/20170720153726843?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMzMwOTg3MA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

②public static void changeReference(Foo a)
![image2](https://img-blog.csdn.net/20170720153830742?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMzMwOTg3MA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

③changeReference(f);
![image3](https://img-blog.csdn.net/20170720153853192?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMzMwOTg3MA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

④Foo b = new Foo(“b”);
![image4](https://img-blog.csdn.net/20170720153935862?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMzMwOTg3MA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

⑤a = b
![image5](https://img-blog.csdn.net/20170720153959388?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMzMwOTg3MA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
![image6](https://img-blog.csdn.net/20170720154011425?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMzMwOTg3MA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

⑥c.setAttribute(“c”);
![image7](https://img-blog.csdn.net/20170720154028603?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdTAxMzMwOTg3MA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
