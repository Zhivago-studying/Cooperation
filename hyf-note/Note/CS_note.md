# 就是计算机系统咯

## 1. 神秘的gcc

* 四步编译
  1. gcc -E hello.c -o hello.i #预处理
  2. gcc -S hello.i -o hello.s #编译成汇编文件
  3. gcc -c hello.s -o hello.o #编译成目标文件（二进制）
  4. gcc hello.o -o hello #链接成可执行文件
* 选项  
  1. -wall #显示所有警告  
  2. -g #生成调试信息  
  3. -O3 #优化  
  4. -lm #链接库
* 多文件编译  
  1. gcc -g main.c func.c -o main #自己写的库要一块编译
* 库文件  
  1. gcc -shared -o mylibrary.so mylibrary.c
  2. 这是共享库（动态库），程序运行时链接
  3. gcc -c mylibrary.c
  4. ar rcs libmylibrary.a mylibrary.o
  5. 这是静态库，编译链接时就拿过来了
* 链接库
  1. gcc main.c -L. -lmylibrary -o main
  2. -L. #指定库文件路径，链接共享库
  3. gcc main.c libmylibrary.a -o main
  4. 链接静态库
   



## 2. 伟大的gdb调试
``` shell
gcc -g main.c -o main # -g 生成调试信息,才能用gdb调试
gdb main      # 启动gdb调试
b 行号/函数名  # 设置断点
b file.c:行号 # 在指定文件的指定行设置断点
b file.c:35 if i > 10 # 设置条件断点(循环)
info b         # 查看断点信息
disable 断点编号 # 禁用断点
enable 断点编号 # 启用断点

r             # 运行程序
l             # 列出代码,
l 0 10        # 列出第0到第10行代码,
l 0           #从头开始

p 变量名      # 打印变量值
display 变量名 # 跟踪显示变量值
undisplay 变量名 # 取消跟踪显示变量值
bt (backtrace)   # 打印调用栈
x/[数量][格式][单位] 地址 # 打印内存,例如 x/2xw &c # x/2xw &c表示从地址&c开始,十六进制打印2个32位的值
p $rip              # 打印rip寄存器值,gdb 规定的$
set var 变量名 = 值 # 设置变量值

n(next)          # 下一步,跳过函数调用
s(step)          # 下一步,进入函数调用

until 行号 # 指定位置跳转
finish           # 跳出当前函数
c(continue)      # 继续运行,跳转到下一断点

q(quit)          # 退出gdb调试

bt                # 查看栈堆的调用

layout  split / src          # 布局（同时显示汇编和源代码和命令行,或只有命令行）
fs cmd              # 关注（操作）命令行

```

## 3.objdump
``` shell
objdump -DxsS var > main.d    #一步到位
```
0100001110010011111111011010100010010010001011111001000111000100
