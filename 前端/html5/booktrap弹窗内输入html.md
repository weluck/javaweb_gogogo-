```
$('[data-toggle="popover"]').popover({
      trigger: 'focus', // 这个是定义鼠标事件，等于data-trigger="focus"
      html: true // 关键在这里， 这样修改之后，我们的data-content里面就可以写html代码啦
 })
 ```
