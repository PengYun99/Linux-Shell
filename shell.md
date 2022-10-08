# 第一个shell脚本
#!/bin/bash  
echo "hello world!"  

# 交换式shell脚本
#!/bin/bash  
echo "please input name:"  
read name   
echo "your name:" $name  

#!/bin/bash  
read -p "input yoor age and height:" age height  
echo "your age=$age, your height=$height"

# shell脚本的数值计算
#!/bin/bash  
echo "please input two int nums:"    
read -p "first num:" first  
read -p "second num:" second  
total=$(($first+$second)) total与等号中间不能有空格  
echo "$first + $second = $total"  

# shell test命令
#!/bin/bash  
echo "please input file name:"  
read -p "file name:" filename  
test -e $filename && echo "$filename exist" || "$filename no exist" 检查文件是否存在  

#!/bin/bash  
echo "please input two strings:"  
read -p "first string:" firststr  
read -p "second string:" secondstr  
test $firststr == $secondstr && echo "firststr == secondstr" || "firststr != secondstr"

# 中括号判断符
#!/bin/bash  
echo "please input two strings:"  
read -p "first string:" firststr  
read -p "second string:" secondstr  
[ "$firststr" == "$secondstr" ]  && echo "firststr == secondstr" || "firststr != secondstr" 中括号与字符之间要打空格

# 默认变量
#!/bin/bash  
echo "file name:" $0 shell脚本的名字  
echo "total param num:" $# 有多少个参数  
echo "whole param:" $@ 整个参数的内容  
echo "first param:" $1  
echo "second param:" $2

# shell脚本条件判断
if-then  

#!/bin/bash  
read -p "please input (Y/N):" value  

if [ "$value" == "Y" ] || [ "$value" == "y" ]; then  
    echo "your input is y"  
    exit 0  
fi  
if [ "$value" == "N" ] || [ "$value" == "n" ]; then  
    echo "your input is n"  
    exit 0  
fi  

if-else  

#!/bin/bash  
read -p "please input (Y/N):" value  

if [ "$value" == "Y" ] || [ "$value" == "y" ]; then  
    echo "your input is y"  
    exit 0  
else  
    echo "your input is:$value"  
    exit 0  
fi  

if-elif-else    

#!/bin/bash  
read -p "please input (Y/N):" value 

if [ "$value" == "Y" ] || [ "$value" == "y" ]; then  
    echo "your input is y"  
    exit 0    
elif [ "$value" == "N" ] || [ "$value" == "n" ]; then  
    echo "your input is n"  
    exit 0  
else  
    echo "your input can't identify!"  
fi  

case语句  

#!/bin/bash  
case $1 in  
     "a")  
        echo "param is:a"  
        ;;  
     "b")  
        echo "param is:b"  
        ;;  
     *)  
        echo "cant't identify"  
        ;;  
esac

# shell 脚本函数
#!/bin/bash  
function help(){  
    echo "this is help cmd!"  
}  
function close(){  
    echo "this is close cmd!"  
}  
case $1 in  
    ".h")  
        help  
        ;;  
    ".c")  
        close  
        ;;  
esac  


# shell 循环
do-while  

#!/bin/bash  
while [ "$value" != "close" ]  
do  
    read -p "please input string:" value  
done  
echo "stop while!!"  

for循环  

#!/bin/bash   
for name in py py1 py2 py3  
do  
    echo "your name:$name"
done  

#!/bin/bash  
read -p "please input count:" count
total=0  
for((i=0; i<=count; i=i+1))  
do  
    total=$(($total+$i))  
done  
echo "1+2+.........+$count=$total"
