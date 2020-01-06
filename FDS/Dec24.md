# Dec24



### Onpening Address

#### Quad

```c
Position  Find ( ElementType Key, HashTable H ) 
{   Position  CurrentPos; 
    int  CollisionNum; 
    CollisionNum = 0; 
    CurrentPos = Hash( Key, H->TableSize ); 
    while( H->TheCells[ CurrentPos ].Info != Empty && 
	H->TheCells[ CurrentPos ].Element != Key ) { 
	CurrentPos += 2 * ++CollisionNum - 1; 
	if ( CurrentPos >= H->TableSize )  CurrentPos -= H->TableSize; 
    } 
    return CurrentPos; 
}
```

$i^2 = (i-1)^2 +2(i-1)+1 = (i-1)^2+2i-1$

#### Double-hashing

$F(i) = i \times hash_2(X)$

将第二个散列函数应用到X并在 hash~2~(X), 2hash~2~(X), 3hash~2~(X), ...处进行探测，特殊的，若hash~2~(X) = 1，则为linear probing

常用的为 $hash_2(X) = R - (X\ mod\ R)$，其中R为TableSize

### 再散列

表快满之后换到一个新的表，时间复杂度是O(原表中元素个数 * 常数)

三种方式(平方查找)

* 到一半就再散列
* 插入失败了才再散列
* ※ 超过某一*装填因子*就进行再散列操作

