使用时应注意表格单元大小,假如单元大小小于pan设置大小,那该单元显示无法占据该大小,看实验下例子进行理解。
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>实验八</title>
        <style 
            type="text/css">div{ 
            background:#009933; 
            width:660px; 
            height:260px; 
            margin:0px auto;
            border:2px dotted #ff3300; 
            color:white; 
        }
            form{ margin:0 auto;} 
            table{margin:0 auto;font-weight:bold;} 
            h2{font-size:28px;text-align:center;} 
        </style>
    </head>
    <body>
        <div>
        <h2>福利彩票投注助手</h2>
        <form>
        <table >
            <tbody>
                <tr>
                    <td><input id="bet1" value="机选1注" onclick="selectnumber(1)" type="button" style="width: 100%;height: 35px;"></td>
                    <td rowspan="8" colspan="12"><select id="text" size="8" style="width: 380px; height: 150px;"></select></td>
                    <td><input id="bet1" value="删除" onclick="delSelect()" type="button" style="width: 100%;height: 35px;"></td>
                </tr>
                <tr>
                    <td><input id="bet2" value="机选5注" onclick="selectnumber(5)" type="button" style="width: 100%;height: 35px;"></td>
                </tr>
                <tr>
                    <td><input id="bet3" value="机选10注" onclick="selectnumber(10)" type="button" style="width: 100%;height: 35px;"></td>
                    <td><input id="bet3" value="全部删除" onclick="delSelectAll()" type="button" style="width: 100%;height: 35px;"></td>
                </tr>
            </t>
        </table>
        </form>
        </div>
</body>
</html>
```
如果将每行“机选”rowspan设为2,“机选5注”会因为没有空间而进入最右边表格
