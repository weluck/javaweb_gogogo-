传统方式操作资源 ：通过不同的参数来实现不同的效果！方法单一，post 和 get

* http://127.0.0.1/item/queryItem.action?id=1 查询,GET
* http://127.0.0.1/item/saveItem.action 新增,POST
* http://127.0.0.1/item/updateItem.action 更新,POST
* http://127.0.0.1/item/deleteItem.action?id=1 删除,GET或POST

使用RESTful操作资源 ： 可以通过不同的请求方式来实现不同的效果！如下：请求地址一样，但是功能可以不同！

* http://127.0.0.1/item/1 查询,GET
* http://127.0.0.1/item 新增,POST
* http://127.0.0.1/item 更新,PUT
* http://127.0.0.1/item/1 删除,DELETE

实现:
```java
@Controller
public class RestFulController {

    //映射访问路径
    @RequestMapping("/commit/{p1}/{p2}")
    public String index(@PathVariable int p1, @PathVariable int p2, Model model){
        
        int result = p1+p2;
        //Spring MVC会自动实例化一个Model对象用于向视图中传值
        model.addAttribute("msg", "结果："+result);
        //返回视图位置
        return "test";
        
    }
    
}
```

使用method属性指定请求类型
```java
//映射访问路径,必须是Get请求         //浏览器地址栏默认放为GET请求,其他请求会报405
@RequestMapping(value = "/hello",method = {RequestMethod.GET})
public String index2(Model model){
    model.addAttribute("msg", "hello!");
    return "test";
}
```

注解设置请求类型:
* @GetMapping
* @PostMapping
* @PutMapping
* @DeletMapping
* @PatchMapping
