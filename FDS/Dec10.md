# Dec10

## ShellSort

### Hibbard’s Increment Sequence:

h~k~ = 2^k^-1  

Worst case is $\Theta(N^{1.5})$

Average case is $O(N^{1.25})$

### Sedgewick’s best sequence 

9\*4^i^ – 9\*2^i^ + 1 or 4^i^ – 3\*2^i^ + 1

Worst case is $O(N^{\frac43})$

Average case is $O(N^{\frac76})$

## HeapSort

算法一：如果直接deleteMin需要额外O(N)的空间

算法二：

Heapsort data start from position 0.

