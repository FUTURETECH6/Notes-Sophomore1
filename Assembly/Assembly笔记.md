## 寄存器

#### ZF(zero)

* 标志寄存器
* 若执行完相关指令，结果为0，则zf=1，反之zf=0



#### PF

* 标志寄存器

* 若执行完相关指令，所有bits中1的个数为奇数(不是数本身的奇偶性)，则pf=1，反之pf=0



#### SF

* 标志寄存器

* 若执行完相关指令，结果为负，则sf=1，反之sf=0



#### CF(carry)

==书上说的不是很清楚，特别是表格==

~~仅最高位时作用还是任何运算都作用~~

* 标志寄存器

* 无符号数加法运算时，结果(无符号数)向最高有效位的更高一位(符号位)进位，则cf=1，反之cf=0

* 减法运算时记录借位值

* 实际上等价于cf存储的是更高位的取值，因为最高位不能存储数据

  | 位   | 8            | 7          | 6    | 5    | 4    | 3    | 2    | 1    |
  | ---- | ------------ | ---------- | ---- | ---- | ---- | ---- | ---- | ---- |
  | 数据 |              | 0          | 1    | 0    | 1    | 1    | 0    | 0    |
  |      | 假想的更高维 | 最高有效位 |      |      |      |      |      |      |

  所以实际上把进位产生的数据存入cf中



#### OF(overflow )

* 标志寄存器
* 若执行完相关指令发生溢出，则of=1，反之of=0



#### CF与OF

* CF针对无符号数(将寄存器中的操作数都看作是无符号数)
* OF针对有符号数(将寄存器中的操作数都看作是有符号数)



如图

<img src="https://img-blog.csdn.net/20170505193752326?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvQXBvbGxvbl9rcmo=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast">



## 操作符

#### offset

* 取得标号的偏移地址(标号后语句的第一个字节地址)



#### dup

* db 3 dup (0)  == db 0,0,0
* db 3 dup (0,1,2) == db 0,1,2,0,1,2,0,1,2
* db 3 dup ('abc','ABC') == db 'abcABCabcABCabcABC'



## 指令

#### 转移指令

##### [Intel x86 JUMP quick reference](http://www.unixwiz.net/techtips/x86-jumps.html)



#### jcxz

* 格式：jcxz 标号
* 相当于 if( (cx) == 0) jmp short 标号
* 短转移：修改IP介于-128~127



#### ret

* 格式：ret
* 实际执行：
  1. (IP)=((ss)\*16+(sp))
  2. (sp)=(sp)+2
* 相当于：pop ip



#### retf

* 格式：retf
* 实际执行：
  1. (IP)=((ss)\*16+(sp))
  2. (sp)=(sp)+2
  3. (CS)=((ss)\*16+(sp))
  4. (sp)=(sp)+2
* 相当于：pop ip    pop cs



#### call

###### 依据位移进行转移的(段内)

* 格式：call 标号
* 实际执行：
  1. (sp)=(sp)-2
  2. ((ss)\*16+(sp))=(ip)
  3. (ip)=(ip)+16位位移(标号处地址-call指令后第一个字节地址)
* 相当于：push ip    jmp near ptr 标号

###### 转移的目的地址在指令中的(段间)

* 格式：call far ptr 标号

* 实际执行
  1. (sp)=(sp)-2
  2. ((ss)\*16+(sp))=(cs)
  3. (sp)=(sp)-2
  4. ((ss)\*16+(sp))=(ip)
  5. (cs)=标号所在段的段地址
  6. (ip)=标号所在段中的偏移地址
* 相当于：push cs    push ip    jmp far ptr 标号

###### 转移地址在寄存器中的

* 格式：call 16位 reg
* 实际执行：
  1. (sp)=(sp)-2
  2. ((ss)\*16+(sp))=(ip)
  3. (ip)=(16位reg)
* 相当于 push ip    jmp 16位reg

###### 转移地址在内存中的

* push word ptr 内存地址 相当于 push ip    jmp word ptr 内存地址
* push dword ptr 内存地址 相当于 push cs    push ip    jmp dword ptr 内存地址



#### div

* 格式
  * div reg
  * div 内存单元
    * div byte ptr ds:[0]
    * div word ptr [bx+si+8]

* |  位数  |        除数8，被除数16         |              除数16，被除数32               | 64位除以32位得32位                                           |
  | :----: | :----------------------------: | :-----------------------------------------: | ------------------------------------------------------------ |
  | 运算数 | 除数在8位reg或内存，被除数在AX | 除数在16位reg或内存，被除数在DX(高)与AX(低) | edx:eax / 除数 = eax..edx                                    |
  |  结果  |       AL存商，AH存为余数       |              AX存商，DX存余数               | 假定要把一个32位整数如7FFFFFFFh转化成十进制格式<br/>则一定要采用(3)这种除法以防止发生除法溢出。 |




#### mul

* 格式
  * mul reg
  * mul 内存单元
    * mul byte ptr ds:[0]
    * mul word ptr [bx+si+8]

* | 乘数位数(相同) |        8        |         16         |
  | :------------: | :-------------: | :----------------: |
  |      乘数      | AL+8位reg或内存 |  AX+16位reg或内存  |
  |      结果      |       AX        | 低位在AX，高位在DX |




#### adc(sbb)

* 利用cf上的进位值实现带进位加法
* 格式：adc 操作对象1,操作对象2
* 功能：操作对象1=操作对象1+操作对象2+CF    Ex. adc ax,bx == (ax)=(ax)+(bx)+cf





#### cmp

