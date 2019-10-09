# Oct9

**段地址+偏移地址不能写成[DS:BX]，而是DS:[BX]**

assume 帮助 编译器确定 用哪个寄存器代替 segment (类似于macro)，是字符串替换，无法校验是否逻辑正确

不能让变量的定义在code seg内定义并被执行到



8Bytes 的定义 `dq`(define quadruple)

dt(ten bytes) 定义10Bytes的数据 在c里是Long Double



小端规则：先存放低8位，后存放高8位的规则称为Little-Endian (小端规则)



~~~c
main()
{
   unsigned short int a = 0x1234;
   unsigned char *p;
   p = (unsigned char *)&a;
   printf("%X %X", p[0], p[1]);  //%x表示16进制整数
}
//0x34 0x12

/*截断*/
long int a = 0x12345678 
/* &a == 1000
 * 1000 0x78
 * 1001 0x56
 * 1002 0x34
 * 1003 0x12 */

char b;
b = a;  //b=0x78
b = *(char*)&a;  //b=0x78
~~~



```c
扩充包括零扩充及符号扩充两种。
原变量为非符号数，补0；
原变量为符号数，补1；
跟目标是否是符号数无关
char a = -1;  二进制=1111 1111B
short int b;
b = a;   b的二进制=1111 1111 1111 1111
char a = 127; 二进制=0111 1111B
short int b;
b = a;   b的二进制=0000 0000 0111 1111
```

