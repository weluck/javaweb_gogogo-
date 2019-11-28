```
<!DOCTYPE html>
<html>

    <head>
        <meta charset="UTF-8">
        <title>AJAX</title>
        <meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no" />
        <style type="text/css">
            @CHARSET "UTF-8";
            * {
                margin: 0;
                padding: 0;
                font-family: microsoft yahei;
                font-size: 14px;
            }
            
            body {
                padding-top: 20px;
            }
            
            .main {
                width: 90%;
                margin: 0 auto;
                border: 1px solid #777;
                padding: 20px;
            }
            
            .main .title {
                font-size: 20px;
                font-weight: normal;
                border-bottom: 1px solid #ccc;
                margin-bottom: 15px;
                padding-bottom: 5px;
                color: blue;
            }
            
            .main .title span {
                display: inline-block;
                font-size: 20px;
                background: blue;
                color: #fff;
                padding: 0 8px;
                background: blue;
            }
            
            a {
                color: blue;
                text-decoration: none;
            }
            
            a:hover {
                color: orangered;
            }
            
            .tab td,
            .tab,
            .tab th {
                border: 1px solid #777;
                border-collapse: collapse;
            }
            
            .tab td,
            .tab th {
                line-height: 26px;
                height: 26px;
                padding-left: 5px;
            }
            
            .abtn {
                display: inline-block;
                height: 20px;
                line-height: 20px;
                background: blue;
                color: #fff;
                padding: 0 5px;
            }
            
            .btn {
                height: 20px;
                line-height: 20px;
                background: blue;
                color: #fff;
                padding: 0 8px;
                border: 0;
            }
            
            .abtn:hover,
            .btn:hover {
                background: orangered;
                color: #fff;
            }
            
            p {
                padding: 5px 0;
            }
            
            fieldset {
                border: 1px solid #ccc;
                padding: 5px 10px;
            }
            
            fieldset legend {
                margin-left: 10px;
                font-size: 16px;
            }
            
            .pic {
                height: 30px;
                width: auto;
            }
            #divFrom{
                display: none;
            }
        </style>
    </head>

    <body>

        <div class="main">
            <h2 class="title"><span>商品管理</span></h2>
            <table border="1" width="100%" class="tab" id="tabGoods">
                <tr>
                    <th>编号</th>
                    <th>图片</th>
                    <th>商品名</th>
                    <th>价格</th>
                    <th>详细</th>
                    <th>操作</th>
                </tr>
            </table>
            <p style="color: red" id="message"></p>
            <p>
                <a href="#" class="abtn" id="btnSave">添加</a>
                <input type="submit" value="删除选择项" class="btn" />
            </p>
            <div id="divFrom">
            <form id="formPdt">
                <fieldset>
                    <legend>添加商品</legend>
                    <p>
                        <label for="name">
                    名称：
                </label>
                        <input type="text" name="name" id="name" />
                    </p>
                    <p>
                        <label for="price">
                    价格：
                </label>
                        <input type="text" name="price" id="price" />
                    </p>
                    <p>
                        <label for="detail">
                    详细：
                      </label>
                        <textarea id="detail" name="detail" cols="60"></textarea>
                    </p>
                </fieldset>
            </form>
            </div>
        </div>

        <link rel="stylesheet" type="text/css" href="js/artDialog6/ui-dialog.css" />
        <script src="js/jQuery1.11.3/jquery-1.11.3.min.js" type="text/javascript" charset="utf-8"></script>
        <script src="js/artDialog6/dialog-min.js" type="text/javascript" charset="utf-8"></script>

        <!--[if (IE 8)|(IE 9)]>
        <script src="js/jquery.transport.xdr.min.js" type="text/javascript" charset="utf-8"></script>
        <![endif]-->
        <script type="text/javascript">
            var app = {
                url: "http://localhost:8087/JavaScript001/", //提供服务的域名
                add: function() {
                    var d = dialog({
                    title: '添加商品',
                    content: $('#divFrom').html(),
                    okValue: '添加',
                    modal:true,
                    backdropOpacity:0.3,
                    ok: function() {
                        var that = this;
                        $.ajax({
                        type: "post",
                        data: $(".ui-dialog #formPdt").serialize() + "&act=add",
                        success: function(data) {
                            if(data) {
                                app.log("添加成功!");
                                app.loadAll();
                                that.close();
                            } else {
                                app.log("添加失败!");
                            }
                        }
                    });
                    return false;
                    },
                    cancelValue: '关闭',
                    cancel: function() {
                        alert('你点了取消按钮')
                    },
                    onclose:function(){
                        alert("关闭了");
                    }
                });

                d.show();
                },
                del: function() {
                    //closest离当前元素最近的td父元素
                    id = $(this).closest("td").data("id");
                    var that = $(this);
                    $.ajax({
                        type: "get",
                        data: {
                            "id": id,
                            "act": "del"
                        },
                        success: function(data) {
                            if(data) {
                                that.closest("tr").remove();
                                app.log("删除成功!");
                            } else {
                                app.log("删除失败!");
                            }
                        }
                    });
                },
                loadAll: function() {
                    $.ajax({
                        type: "get",
                        data: {
                            "act": "getAllCORS"
                        },
                        success: function(data) {
                            $("#tabGoods tr:gt(0)").remove();
                            $.each(data, function(index, obj) {
                                var tr = $("<tr/>"); //行

                                $("<td/>").html(obj.id).appendTo(tr); //编号

                                var imgTd = $("<td/>");
                                $("<img/>", {
                                    "src": app.url + "images/" + obj.picture,
                                    "class": "pic"
                                }).appendTo(imgTd); //图片
                                imgTd.appendTo(tr);

                                $("<td/>").html(obj.name).appendTo(tr);
                                $("<td/>").html(Math.ceil(obj.price)).appendTo(tr);
                                $("<td/>").html(obj.detail).appendTo(tr);
                                $("<td/>").html("<a href='#' class='abtn del'>删除</a>").data("id", obj.id).appendTo(tr);
                                $("#tabGoods").append(tr);
                            });
                        }
                    });
                },
                init: function() {
                    /*动态绑定删除事件*/
                    $("#tabGoods").on("click", "a.del", {}, app.del);
                    /*绑定添加事件*/
                    $("#btnSave").click(app.add);
                    /*设置全局AJAX默认值*/
                    $.ajaxSetup({
                        dataType: "json",
                        url: app.url + "Product?type=meat-and-filler&format=json",
                        beforeSend: app.ajaxBefore,
                        complete: app.clearMsg,
                        error: function(xhr, textStatus, errorThrown) {
                            app.log("错误" + textStatus + errorThrown);
                        }
                    });
                    this.loadAll();
                },
                clearMsg: function() {
                    this.box.remove();
                },
                ajaxBefore: function() {
                    this.box=dialog({
                        modal:true
                    });
                    this.box.show();
                },
                log: function(msg) {
                    $("#message").html(msg);
                }
            };

            app.init();
        </script>
    </body>

</html>
```
![](https://github.com/weluck/javaweb_gogogo-/blob/master/%E5%89%8D%E7%AB%AF/%E5%9B%BE%E7%89%87/chuangkou.png)
