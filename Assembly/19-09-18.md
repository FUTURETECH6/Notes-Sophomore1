## Sep18

### 快捷键

代码窗中ctrl+g：地址或函数名(必须是内核的API函数名，库函数不可，区分大小写)



Winmain 的输出输出使用消息循环而不是掉用函数

reg.exe在弹窗时会调用内核函数(API, app prog interface) MessageBoxA()

策略：

1. 在messagebox设断点找出调用方



401301 将eax中得到的输入与0x1999AA98 XOR，

若等于ecx中的用户信息码，则正确，则不弹窗$\Rightarrow$ 00401101 $\Rightarrow$ MessageBoxA() 77d507ea

因此注册码为0x22686299(bhh的电脑的用户信息码577...) ^ 0x1999AA98 转为十进制



```asm
.386
.model flat, stdcall
option casemap :none

include include\windows.inc
include include\kernel32.inc
include include\user32.inc

includelib lib\kernel32.lib
includelib lib\user32.lib

.data
result db 100 dup(0); dup:duplicate重复
;char result[100]={0};
format db "%d",0; db:define byte字节类型
; char format[3]="%d";
prompt db "The result",0

.code
main:         ; 标号
    mov eax, 0; eax:extended ax
    mov ebx, 1
again:
    add eax, ebx; eax=0+1+2+3
    add ebx, 1  ; ebx=4
    cmp ebx, 100; cmp:compare
    jbe again   ; jbe:jump if below or equal
invoke wsprintf, offset result, offset format, eax  ;wsprintf是MS的内核函数
;C里是wsprintf(result, format, eax);
invoke MessageBox,0,offset result,offset prompt,0
;    第一个0表示父窗口编号即handle(句柄)，0表示无父窗口   最后这个0表示弹框的式样
;    用处：连动两者，一起拖动或删除
    ret
end main; 指定程序的起始执行点
         ; end后面的标号决定了程序刚开始
         ; 运行时的eip的值。

```



invoke并非指令而是macro 在编译时会转换为call指令，参数会被转换为push指令(从右往左push)

```asm
invoke wsprintf, offset result, offset format, eax  ;
```

```asm
00401014  |.  50            push    eax                              ; /<%d>
00401015  |.  68 64304000   push    00403064                         ; |Format = "%d"
0040101A  |.  68 00304000   push    00403000                         ; |s = SUM.00403000
0040101F  |.  E8 18000000   call    <jmp.&user32.wsprintfA>          ; \wsprintfA
```



### **==汇编里"与'没有区别==**



dup的嵌套



s db 3 dup(2 dup (1))

111111

