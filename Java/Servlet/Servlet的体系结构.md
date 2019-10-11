Servlet -- 接口
>>
GenerucServlet -- 抽象类
>>
HttpServlet -- 抽象类

    GenericServlet:将Servlet接口中其他的方法做了默认空实现，只将service()方法做为抽象
    * 将来定义Servlet类时,可以继承GenericServlet,实现Service()方法即可
    
    HttpServlet:对Http协议的一种封装,简化操作
    * 定义类继承HttpServlet
    * 复写doGet/doPOst方法
    
