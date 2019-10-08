1.利用set
---------
```cpp
int main()
{
    int myints[] = {1,2,3,1,1};
    int len = sizeof(myints)/sizeof(int);
    vector<int> vec(myints, myints + len);
    set<int>s(vec.begin(), vec.end());
    vec.assign(s.begin(), s.end());
}
```
2.利用sort()和unique()
------------------------
unique()函数将相邻且重复的元素放到vector的尾部 然后返回指向第一个重复元素的迭代器再用erase函数擦除从这个元素到最后元素的所有的元素。

所以可以先进行排序，这样重复元素就会堆一起了，调用unique()函数，再调用erase函数删除重复。代码见下：
```cpp
int main()
{
    int myints[] = {1,2,3,1,1};
    int len = sizeof(myints)/sizeof(int);
    vector<int> vec(myints, myints + len);
    sort(vec.begin(), vec.end());
    vec.erase(unique(vec.begin(), vec.end()), vec.end());
}
```
