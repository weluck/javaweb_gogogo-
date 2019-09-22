语法格式一 : 无参数，无返回值<br>
`() -> System.out.println("Hello Lambda!");`

语法格式二 : 有一个参数，并且无返回值<br>
`(x) -> System.out.println(x)`

语法格式三 : 若只有一个参数，小括号可以省略不写<br>
 `x -> System.out.println(x)`
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
`Comparator<Integer> com = (x, y) -> Integer.compare(x, y);`

语法格式六 : Lambda 表达式的参数列表的数据类型可以省略不写，因为JVM编译器通过上下文推断出，数据类型，即“类型推断”<br>
`(Integer x, Integer y) -> Integer.compare(x, y);`

Lambda 表达式需要 “函数式接口” 的支持
函数式接口 : 接口中只有一个抽象方法的接口，称为函数式接口，可以通过 Lambda 表达式来创建该接口的对象 (若 Lambda表达式抛出一个受检异常，那么该异常需要在目标接口的抽象方法上进行声明) 可以使用注解 @FunctionalInterface 修饰可以检查是否是函数式接口，同时 javadoc 也会包含一条声明，说明这个接口是一个函数式接口。<br>
作为参数传递 Lambda 表达式 : 为了将 Lambda 表达式作为参数传递，接收Lambda 表达式的参数类型必须是与该 Lambda 表达式兼容的函数式接口的类型

需求 : 雇员对象如下，有一个包含许多员工信息的对象 employees，要求获取当前公司中员工年龄大于 35 的员工信息
```java
public class Employee {
    private String name;
    private int age;
    public Employee() {
    }
    public Employee(String name, int age) {
        this.name = name;
        this.age = age;
    }
    // ...
    @Override
    public String toString() {
        return "Employee{" + "name='" + name + '\'' + ", age=" + age + '}';
    }
}
```
最简单的方式是采用 foreach 循环遍历，以下是各种优化方式

优化方式一 : 策略设计模式
```java
@FunctionalInterface
public interface MyPredicate<T> {
    boolean test(T t);
}
public class FilterEmployeeByAge implements MyPredicate<Employee> {
    @Override
    public boolean test(Employee employee) {
        return employee.getAge() >= 35;
    }
}
public List<Employee> filterEmployees3(List<Employee> employees, MyPredicate<Employee> myPredicate) {
    List<Employee> emps = new ArrayList<>();
    for (Employee employee : employees) {
        if (myPredicate.test(employee)) {
            emps.add(employee);
        }
    }
    return emps;
}
```
```java
调用
List<Employee> emps = filterEmployees3(employees, new FilterEmployeeByAge());
for (Employee employee : emps) {
    System.out.println(employee.toString());
}
```
优化方式二 : 匿名内部类
```java
List<Employee> emps = filterEmployees3(employees, new MyPredicate<Employee>() {
    @Override
    public boolean test(Employee employee) {
        return employee.getAge() >= 35;
    }
});
for (Employee employee : emps) {
    System.out.println(employee.toString());
}
```
优化方式三 : Lambda
`filterEmployees3(employees, employee -> employee.getAge() >= 35).forEach(System.out::println);`

优化方式四 : Stream API
`employees.stream().filter((employee) -> employee.getAge() >= 35).limit(5).forEach(System.out::println);`

方法引用
-------
若 Lambda 体中的功能，已经有方法提供实现，可以使用方法引用 (可以将方法引用理解为 Lambda 表达式的另外一种表现形式)
1> 对象的引用 :: 实例方法名
2> 类名 :: 静态方法名
3> 类名 :: 实例方法名

`注 : 1> 方法引用所引用的方法的参数列表与返回值类型，需要与函数式接口中抽象方法的参数列表和返回值类型保持一致(就是函数签名和返回值一致)
       2> 若Lambda 的参数列表的第一个参数，是实例方法的调用者，第二个参数(或无参)是实例方法的参数时，格式 : ClassName::MethodName`
```java
PrintStream ps = System.out;
Consumer<String> con1 = (str) -> ps.println(str);
Consumer<String> con2 = ps::println;
Consumer<String> con3 = System.out::println;
```
对象的引用 :: 实例方法名
```java
Employee emp = new Employee(101, "张三", 18, 9999.99);
Supplier<String> sup = () -> emp.getName();
System.out.println(sup.get());
Supplier<String> sup2 = emp::getName;
System.out.println(sup2.get());
```
类名 :: 静态方法名
```java
Comparator<Integer> comparator1 = (x, y) -> Integer.compare(x, y);
Comparator<Integer> comparator2 = Integer::compare;

BiFunction<Double, Double, Double> fun = (x, y) -> Math.max(x, y);
System.out.println(fun.apply(1.5, 22.2));
BiFunction<Double, Double, Double> fun2 = Math::max;
System.out.println(fun2.apply(1.2, 1.5));
```
类名 :: 实例方法名
```java
BiPredicate<String, String> bp = (x, y) -> x.equals(y);
System.out.println(bp.test("abcde", "abcde"));
BiPredicate<String, String> bp2 = String::equals;
System.out.println(bp2.test("abc", "abc"));

Function<Employee, String> fun = (e) -> e.show();
System.out.println(fun.apply(new Employee()));
Function<Employee, String> fun2 = Employee::show;
System.out.println(fun2.apply(new Employee()));
```
`注 : 当需要引用方法的第一个参数是调用对象，并且第二个参数是需要引用方法的第二个参数 (或无参数) 时 :  ClassName::methodName`

构造器引用
---------
构造器的参数列表，需要与函数式接口中参数列表保持一致 (就是函数签名一致)
1> 类名 :: new
```java
Supplier<Employee> sup = () -> new Employee();
System.out.println(sup.get());
Supplier<Employee> sup2 = Employee::new;
System.out.println(sup2.get());

Function<String, Employee> fun = Employee::new;
BiFunction<String, Integer, Employee> fun2 = Employee::new;
```
数组引用<br>
1> 类型[] :: new
```java
Function<Integer, String[]> fun = (args) -> new String[args];
String[] strs = fun.apply(10);
System.out.println(strs.length);

Function<Integer, Employee[]> fun2 = Employee[]::new;
Employee[] emps = fun2.apply(20);
System.out.println(emps.length);
```

