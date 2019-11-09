在使用hr的时候很容易误解为border就是水平线，改变border就能改变水平线的颜色，然而事实并不是这样的，要想改变水平线的颜色，要从下面的i几个属性出发：

border：设置为none或者0px；

height：给定一个高度，在水平线中指的是水平线有多粗；

width：给定一个长度，即水平线大概有多长，占页面的多少；

background-color：设置水平线的颜色。

具体代码如下：

 <hr style="background-color:red;height: 1px;width:90%;border: none;"/>



注意：在使用border时，若设定值为border：1px solid red；则针对的是水平线的边，是4个边，而中间的颜色是空，即未改变水平线的实际颜色。

 <hr style="clear: both;background-color:red;height: 5px;width:90%;border: 5px solid green;"/>     
