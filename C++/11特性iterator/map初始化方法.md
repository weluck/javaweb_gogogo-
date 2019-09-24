1.直接赋值法
-----------
```c++
map<string, int> m1;
m1[string("abc")] = 1;
m1["def"] = 2;
```
2.insert（）
-----------
```cpp
map<string, int> m2;
m2.insert({ "abc", 1 });    //使用这种就可以了
//其他形式和方式
m2.insert(make_pair(string("def"), 2));
m2.insert(pair<string, int>(string("ghi"), 3));
```
3.列表初始化
-----------
```cpp
map<string,int> m3 = {
{"string",1}, {"sec",2}, {"trd",3}
};
 
map<string,string> m4 = {
{"first","second"}, {"third","fourth"},
{"fifth","sixth"}, {"begin","end"}
};
```
