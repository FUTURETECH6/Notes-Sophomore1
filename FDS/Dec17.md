# Dec17

## QSort

### m3算法课件版

m3的时候把pivot存到[right-1]，三个中最大值存在[right]

然后快排的时候

```c
for(;;) {
	while ( A[ + +i ] < Pivot ) { }  /* scan from left */
	while ( A[ – –j ] > Pivot ) { }  /* scan from right */
    if ( i < j ) 
		Swap( &A[ i ], &A[ j ] );  /* adjust partition */
	else
        break;  /* partition done */
}
Swap( &A[ i ], &A[ Right - 1 ] );
```

最后一个比pivot大的和pivot交换位置

