## jquery的.css方法
```javascript
$("span").css("css属性名","属性值")

如  $("span").css("color","red") 将标签为span的字体都设为红色的
```
## addclass
```javascript
<style type="text/css">
   .aa {
        border:1px solid red;
    }
  </style>



$("#txtName").addClass("aa");
 <input id="txtName"type="text"value="请输入你的姓名"/>
```

## 对css样式操作
```
1、.css("样式")：获得样式值，比如$("input").css("color")  获得input中字体的颜色

2、.css("样式","value"):为样式赋值，如$("input").css("color","red");

3、.addClass("样式类1,样式类2,样式类3"):可以添加多个定义好的样式类

4、.hasClass("样式类类")：判断是否存在该样式

5、.toggleClass("样式类")：如果存在(不存在)就切换(删除)样式

6、.toggleClass("样式类",swith):如果swith为false，则删除样式，如果swith为true，则切换成该类

7、removeClass("样式类")：移除样式类

8、.css({样式名:"value",样式名:"value",样式名:"value"}):可以多次添加样式
```

## 对内置属性进行加删
```js
function fun(){
		var t = document.getElementById('t').value;
		console.log(t);
		if(t == 1){
			document.getElementById("btn").disabled=false;
		} else{
			document.getElementById("btn").disabled=true;
		}	
	}
```
