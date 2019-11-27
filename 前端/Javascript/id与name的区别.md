<form name="form1"> 
    用户名：<input type=text name="username" id="username"> 
    密码：<input type=password name="password" id="pwd">
 </form> 
如果我要获得用户名和密码;
JS用name获得的话，就得写成document.form1.username.value; document.form1.password.value;
 用id获得： docuement.getElementById("username"); docuement.getElementById("pwd"); 
有时候name 可能会出现相同的名字，所以这时候我们用name获得就无法确定获得的是哪个值了。 document.getElemntsByName("username"); 这里得到的是一个数组。可以说几乎每个做过Web开发的人都问过，到底元素的ID和Name有什么区别阿？为什么有了ID还要有Name呢?! 而同样我们也可以得到最classical的答案：ID就像是一个人的身份证号码，而Name就像是他的名字，ID显然是唯一的，而Name是可以重复的。 name原来是为了标识之用，但是现在根据规范，都建议用id来标识元素。
一、以下只能用name： 
1. 表单（form）的控件名，提交的数据都用控件的name而不是id来控制。因为有许多name会同时对应多个控件，比如 checkbox和radio，而id必须是全文档中唯一的。此外浏览器会根据name来设定发送到服务器的request。因此如果用id，服务器是无 法得到数据的。 
2. frame和window的名字，用于在其他frame或window指定target。 
二、以下只能用id：
 1. label与form控件的关联， My Input
 for属性指定与label关联的元素的id，不可用name替代。
 2. CSS的元素选择机制，以#MyId的方式指定应用样式的元素，不能用name替代。 
 3. 脚本中获得对象： IE支持在脚本中直接以id（而不是name）引用该id标识的对象。例如上面的input，要在脚本中获得输入的内容，可以直接以 MyInput.value来获得。 如果用DOM的话，则用document.getElementByIdx_x("MyInput").value，如果要用name的话，通常先得到包含控件的form，例如 document.forms[0]，然后从form再引用name，注意这样得到的是经过计算后将发送给服务器的值。 name与id的其他区别是： id要符合标识的要求，比如大小写敏感，最好不要包含下划线（因为不兼容CSS）。而name基本上没有什么要求，甚至可以用数字 。 用CSS控制这个链接的停留样式， 可以这样写 #m_blog div.opt a:hover{color:#D57813} 或 #myLink:hover{color:#D57813} NAME主要应用在交互式网页，表单提交给某个服务器端脚本后接收变处理量使用。从源代码的规范性和兼容性角度出发，如在客户端 脚本里要索引某个对象，建议用document.getElementByIdx_x()方法，尽量不要直接使用NAME的值
