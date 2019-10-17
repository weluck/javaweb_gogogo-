```java
/**
          SimpleDateFormat函数语法：
        
          G 年代标志符
          y 年
          M 月
          d 日
          h 时 在上午或下午 (1~12)
          H 时 在一天中 (0~23)
          m 分
          s 秒
          S 毫秒
          E 星期
          D 一年中的第几天
          F 一月中第几个星期几
          w 一年中第几个星期
          W 一月中第几个星期
          a 上午 / 下午 标记符
          k 时 在一天中 (1~24)
          K 时 在上午或下午 (0~11)
          z 时区
         */
        
        SimpleDateFormat aDate=new SimpleDateFormat("yyyy-mm-dd  HH:mm:ss");
        SimpleDateFormat bDate=new SimpleDateFormat("yyyy-mmmmmm-dddddd");
        long now=System.currentTimeMillis();
        System.out.println(aDate.format(now));
        System.out.println(bDate.format(now));
        
         SimpleDateFormat myFmt=new SimpleDateFormat("yyyy年MM月dd日 HH时mm分ss秒");
            SimpleDateFormat myFmt1=new SimpleDateFormat("yy/MM/dd HH:mm");
            SimpleDateFormat myFmt2=new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");//等价于now.toLocaleString()
            SimpleDateFormat myFmt3=new SimpleDateFormat("yyyy年MM月dd日 HH时mm分ss秒 E ");
            SimpleDateFormat myFmt4=new SimpleDateFormat(
                    "一年中的第 D 天 一年中第w个星期 一月中第W个星期 在一天中k时 z时区");
         System.out.println(myFmt.format(now));
         System.out.println(myFmt1.format(now));
         System.out.println(myFmt2.format(now));
         System.out.println(myFmt3.format(now));
         System.out.println(myFmt4.format(now));
  ```       
运行结果：

2017-10-17  11:10:21<br>
2017-000010-000017<br>
2017年10月17日 11时10分21秒<br>
17/10/17 11:10<br>
2017-10-17 11:10:21<br>
2017年10月17日 11时10分21秒 星期二<br>
一年中的第 290 天 一年中第42个星期 一月中第3个星期 在一天中11时 CST时区<br>
