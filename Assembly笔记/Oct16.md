# Oct16

### 扩充 与 数据类型

扩充包括零扩充及符号扩充两种。
原变量为非符号数，补0；
原变量为符号数，补1；（由补码很好理解：保持值不变）



IEEE745标准中单精度小数(即float类型)的存储

8位指数(包括1位符号数)

1位符号数

23位尾数(1.尾数)

实际值：`1.尾数 << 指数(二进制位移运算)` 



```c
printf("%02X",  p[i]);  //两位16进制，不足补0
```



此段代码可改变f中最高一字节的值

```c
#include "stdio.h"

int main() {
	float f = 127.375;
	unsigned char *p;
	int i;
	p = (unsigned char *)&f;
	*(p + 3) = 1;
	for (i = 0; i < 4; i++)
		printf("%02X ",  p[i]);
}
```



### 双目四则运算

==小数的四则运算要另加f，如fdiv等==

#### add

* 操作数
  * add reg, reg
  
    * add ax, bh 会报错
  
  * add reg, const (如2)
  
  * add reg, var (如ds:[1000h])
  
  * add var, reg
  
  * add var, const 
  
    * add ==word ptr ds:[1000h]==, 2
  
      * ==word prt 用于申明数据类型为word==
  
      * Ex.
  
        ```assembly
        ;ds:[1000h]为FE，ds:[1001h]为01
        
        add word ptr ds:[1000h], 2
        ;变为0200h
        
        add byte ptr ds:[1000h], 2
        ;变为0100h(低位的溢出不影响到高位)
        ```
  
        
  
      * 类似还有 byte ptr, dword ptr
  
  * add var, var
  
  * ~~add var, var~~

#### sub

* 语法同add
* mov 语法也同 add

#### mul

* 

#### div

### 逻辑运算

|  &   |  \|  |  ^   |  ~   |  <<  |  >>  |    _rotl()    |    _rotr()    |
| :--: | :--: | :--: | :--: | :--: | :--: | :-----------: | :-----------: |
| and  |  or  | xor  | not  | shl  | shr  | rol//循环左移 | ror//循环右移 |



设AL=1011 0110
rol al, 1; 表示把AL循环左移1位
al = _rotl(al, 1); 表示把AL循环左移1位
结果AL=011 0110 1



Ex.

求 0111 1111 1111 1111的最高4位

```assembly
rol ax, 4
and ax, 000Fh
```



<center><b><font size = '6'>EAX是32位reg，AX是16位</font></b></center>



运用rol指令把32位整数转化成16进制格式输出:

v2h32.asm

```assembly
.386  ;表示cpu为386及以上，才支持32位寄存器
data segment use16
abc dd 2147483647
s db 8 dup(0),0Dh,0Ah,'$'
data ends
code segment use16
assume cs:code, ds:data
main:
   mov ax, data
   mov ds, ax
   mov eax, abc
   mov cx, 8
   mov di, 0   ; 目标数组的下标,可以引用s[di]
again:
   rol eax, 4  ; 386以上cpu中, 移位次数大于1时也可
               ; 使用常数
   push eax    ; 设eax=12345678h
   and eax, 0Fh; eax=00000008h, al=08h
               ; 这里位数不同为什么可以？
   cmp al, 10
   jb is_digit
is_alpha:
   sub al, 10
   add al, 'A'
   jmp finish_4bits
is_digit:
   add al, '0'
finish_4bits:
   mov s[di], al
   pop eax
   add di, 1
   sub cx, 1
   jnz again
   mov ah, 9
   mov dx, offset s
   int 21h
   mov ah, 4Ch
   int 21h
code ends
end main
```











