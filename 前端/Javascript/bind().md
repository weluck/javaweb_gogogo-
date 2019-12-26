bind()方法主要就是将函数绑定到某个对象，bind()会创建一个函数，函数体内的this对象的值会被绑定到传入bind()第一个参数的值，例如，f.bind(obj)，实际上可以理解为obj.f()，这时，f函数体内的this自然指向的是obj
```js
var a = {
    b : function(){
        var func = function(){
            console.log(this.c);
        }
        func();
    },
    c : 'Hello!'
}
a.b();
//undefined
注意：这里的this指向的是全局作用域，所以会返回undefined
var a = {
    b : function(){
        var that = this;
        var func = function(){
            console.log(that.c);
        }
        func();
    },
    c : 'Hello!'
}
a.b();
//Hello!
注意：可以通过赋值的方式将this赋值给that
var a = {
    b : function(){
        var func = function(){
            console.log(this.c);
        }.bind(this);
        func();
    },
    c : 'Hello!'
}
a.b();
//Hello!
 
var a = {
    b : function(){
        var func = function(){
            console.log(this.c);
        }
        func.bind(this)();
    },
    c : 'Hello!'
}
a.b();
//Hello!
```
