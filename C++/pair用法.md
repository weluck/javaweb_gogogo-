1. 初始化
```cpp
pair<string, string> author("James","Joy");    // 创建一个author对象，两个元素类型分别为string类型，并默认初始值为James和Joy。
pair<string, int> name_age("Tom", "18");
pair<string, int> name_age2(name_age);    // 拷贝构造初始化
```
2. 利用first和second对对象进行访问
3. make_pair生成新的对象
```cpp
 pair<int, double> p1;
 p1 = make_pair(1, 1.2);
cout << p1.first << p1.second << endl;
 
//output: 1 1.2
 
int a = 8;
 
string m = "James";
 
pair<int, string> newone;
 
newone = make_pair(a, m);
cout << newone.first << newone.second << endl;
```
5. 通过tie获取pair元素值
```cpp
std::pair<std::string, int> getPreson() {
    return std::make_pair("Sven", 25);
}
 
int main(int argc, char **argv) {
    std::string name;
    int ages;
 
    std::tie(name, ages) = getPreson();
 
    std::cout << "name: " << name << ", ages: " << ages << std::endl;
 
    return 0;
```
