## Sep11

#### OD快捷键

F2加断点

F8 step over 单步执行

F7 trace into 跟踪至call调用的指令(内部)

数据窗中 ctrl+g 可定位至数据所在地址并观察

alt+backspace可以撤回改过的指令



#### 指令

jbe: Jump short if below or equal (CF=1 or ZF=1)

test 判断ax是否为0

jnz: jump if not zero

nop: 机器码90h



#### 其他

##### 单向处理密文 md5



##### int main 有三个push

```assembly
00401237  |.  50            push    eax                              ; /Arg3 => 00410A30 ASCII "?,TAB,"A"
00401238  |.  FF35 F8664000 push    dword ptr [0x4066F8]             ; |Arg2 = 00410AB0
0040123E  |.  FF35 F4664000 push    dword ptr [0x4066F4]             ; |Arg1 = 00000001
00401244  |.  E8 B7FDFFFF   call    00401000                         ; \password.00401000


```

实际上是 

```c
int main(int argc, char *argv[], char *envp[]);
/*
其中argc是代表命令行的参数个数
argv[]存储命令参数，其中argv[0]通常代表该程序的程序名
envp[]代表系统的环境变量
*/
```



##### 暴力破解(去除跳转判断)

```assembly
00401030  |.  85C0          test    eax, eax
00401032  |.  75 0F         jnz     short 00401043
00401034  |.  68 54604000   push    00406054          ;  ASCII "Password is OK!"
00401039  |.  E8 F0000000   call    0040112E
```

用crtl+g 修改数据改为 nop后

```assembly
00401030  |.  85C0          test    eax, eax
00401032      90            nop
00401033      90            nop
00401034  |.  68 54604000   push    00406054          ;  ASCII "Password is OK!"
00401039  |.  E8 F0000000   call    0040112E
```

可绕过判断暴力破解密码。

但是只能在OD中运行有效，若要修改原.exe，需利用010ed



