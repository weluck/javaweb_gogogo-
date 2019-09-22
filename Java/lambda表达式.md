语法格式一 : 无参数，无返回值<br>
    () -> System.out.println("Hello Lambda!");

语法格式二 : 有一个参数，并且无返回值<br>
    (x) -> System.out.println(x)

语法格式三 : 若只有一个参数，小括号可以省略不写<br>
    x -> System.out.println(x)
```java
Consumer<String> con = (x) -> System.out.println(x);
con.accept("啦啦啦，我是卖报的小行家");
```

语法格式四 : 有两个以上的参数，有返回值，并且 Lambda 体中有多条语句
```java
Comparator<Integer> com = (x, y) -> {
    System.out.println("函数式接口");
    return Integer.compare(x, y);
};
```

语法格式五 : 若 Lambda 体中只有一条语句， return 和 大括号都可以省略不写<br>
    Comparator<Integer> com = (x, y) -> Integer.compare(x, y);

语法格式六 : Lambda 表达式的参数列表的数据类型可以省略不写，因为JVM编译器通过上下文推断出，数据类型，即“类型推断”<br>
    (Integer x, Integer y) -> Integer.compare(x, y);
