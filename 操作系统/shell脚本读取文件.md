1. 逐行输出所有行
```shell
#!/bin/sh  
#一次读文件一行,可以根据需要编辑改行的内容
num=0  
while read line  
do        
        echo $line
        echo "Do something..."  
        let num=num+1  
done < input.txt  
echo "$num" 
```
2. 使用Sed命令操作行
```shell
sed -n “3p” filename #输出文件的第3行
sed -n “2,5p“ filename #输出文件的第2到5行
sed ”/abc/d“ filename #删除包含“abc”的行
sed “2d” filename #删除第2行
sed ”$d“ filename #删除最后一行
```
3. 输出指定文件的特定行
```shell
#!/bin/sh
#deleteLine.sh
FILE=$1      
NUM=$2      
cat $1 | sed  -n "${NUM}p"
```
使用：./deleteLine.sh input.txt 3
