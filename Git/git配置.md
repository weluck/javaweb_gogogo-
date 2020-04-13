```bash
#查看系统config
git config --system --1ist
并查看当前用户(g1oba1) 配置
git config --g1oba1 --1ist
```

Git相关的配置文件:

1 )、Git\mingw64letc'gitconfig : Git安装目录下的gitconfig   -system系统级

2)、C:\Users\Administrator\ .gitconfig只适用于当前登录用户的配置   -global 全局, 这里可以直接编辑配置文件,通过命令设置后会响应到这里。

> 设置用户名和邮箱

当你安装Git后首先要做的事情是设置你的用户名称和e-mail地址。这是非常重要的,因为每次Git提交都会使用该信息。它被永远的嵌入到了你的提交中: 

```bash
git config --g1oba1 user . name "kuangshen" #名称
git config --g1oba1 user .emai 123@qq.com #邮箱
```

只需要做一-次这 个设置,如果你传递了-global选项,因为Git将总是会使用该信息来处理你在系统中所做的- -切操作。如果你希望在一个特定的项目中使用不同的名称或e-mail地址,你可以在该项目中运行该命令而不要-global选项。总之-global为全局配置，不加为某个项目的特定配置。
