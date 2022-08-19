# makefile文件编写

第一步：新建名为makefile的文件，不加任何扩展名；

第二步：编写

```C
语法：目标文件：依赖文件
        
        <TAB键>指令
```          
例：
```C
test: test.c
        gcc test.c -o test
```

例：
```c
test: circle.o cube.o main.o
        gcc circle.o cube.o mian.o -o test
circle.o: circle.c
        gcc -c circle.c -o circle.o
cube.o: cube.c
        gcc -c cube.c -o cube.o
main.o: mian.c
        gcc -c main.c -o mian.o
clean:
        rm *.o main
```

变量 =(替换) +=(追加) :=(常量)

使用变量： $(变量名) 

例：
```c
TAR = test
OBJ = circle.o cube.o mian.o
CC := gcc

$(TAR): $(OBJ)
        $(CC) $(OBJ) -o $(TAR)
circle.o: circle.c
        $(CC) -c circle.c -o circle.o
cube.o: cube.c
        $(CC) -c cube.c -o cube.o
main.o: mian.c
        $(CC) -c main.c -o mian.o
clean:
        rm *.o main
```

隐含规则  %.c %.o任意的.c或者.o         *.c  *.o所有的.c .o 

例：
```c
TAR = test
OBJ = circle.o cube.o mian.o
CC := gcc

$(TAR): $(OBJ)
        $(CC) $(OBJ) -o $(TAR)
%.o: %.c
        $(CC) -c %.c -o %.o
clean:
        rm *.o main
```

通配符 $^所有的依赖文件  $@所有的目标文件  $<所有的依赖文件的第一个文件

例：
```c
TAR = test
OBJ = circle.o cube.o mian.o
CC := gcc

$(TAR): $(OBJ)
        $(CC) $^ -o $@
%.o: %.c
        $(CC) -c $^ -o $@
clean:
        rm *.o main
```
