# Dec24



### Onpening Address



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

$=(i-1)^+2(i-1)+1=(i-1)^2+2i-1$

