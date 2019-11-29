# Nov19



Negative road is not supported, but **negative-cost cycle** is not supported

四种：

* Unweighted 
* 

### Unweighted(无权最短路)

**Breadth-first Search Algorithm**

​	\- use Queue

​	\- If the T is initialized as as {∞}, then ∞ can be used as a mark for unvisited

​	\- T = T~Topological\ Sort~ = O(|V|+|E|)

```c
void Unweighted( Table T )
{	/* T is initialized with the source vertex S given */
	Queue  Q;
	Vertex  V, W;
	Q = CreateQueue (NumVertex );
    MakeEmpty( Q );
	Enqueue( S, Q ); /* Enqueue the source vertex */
	while ( !IsEmpty( Q ) ) {
		V = Dequeue( Q );
		T[ V ].Known = true; /* not really necessary */
        // 
		for ( each W adjacent to V )
			if ( T[ W ].Dist == Infinity ) {
				T[ W ].Dist = T[ V ].Dist + 1;
				T[ W ].Path = V;
				Enqueue( W, Q );
			} /* end-if Dist == Infinity */
	} /* end-while */
	DisposeQueue( Q ); /* free memory */
}
```

### Weighted

#### Dijkstra

​	\- [/ˈdaɪkstrə/](https://en.wikipedia.org/wiki/Help:IPA/English)

以下两种算法的区别在于寻找Unvisited的方式的不同

* **Implementation 1: For Dense Graph**
* Directly Scan to find the min One
  
* T = O(|V|^2^+|E|)
  
* **Implementation 2: For Sparse Graph**

  * Use a Priority Queue to store the distance data and call DeleteMin[costs O(log|V|)]

    [[最短路]使用优先队列优化的Dijkstra算法 - 童凌的技术博客 - CSDN博客](https://blog.csdn.net/tlonline/article/details/47398403)

    2 Methods: 

    * Method 1: Update $\Longrightarrow$ Decrease Key
      * T = O(|E|log|V| + |V|log|V|) = O(|E|log|V|)
    * Method 2: insert W with updated Dist into the priority queue(W为V所有邻接点)
      * 所有本来的W的node先deleteMin掉，再把新的插入进去
      * T = O(|E|log|V|) but requires |E| DeleteMin with |E| space
      * 比1好实现，但是复杂度高

  ```c
  void Dijkstra( Table T )
  {	/* T is initialized by Figure 9.30 on p.303 */
  	// All.Known = 0; All_Except_Source.Dist = ∞; All.Path = NULL;
  	Vertex  V, W;
  	for ( ; ; ) {
  		V = smallest unknown distance vertex;
  		if ( V == NotAVertex )
  			break;
  		T[ V ].Known = true;
  		for ( each W adjacent to V )  // O(|V|)
  			if ( !T[ W ].Known )
  				if ( T[ V ].Dist + Cvw < T[ W ].Dist ) {
  #if method1
  					Heap.DecreaseKey( T[ W ].Dist  to
  					                  T[ V ].Dist + Cvw );
  					// Change from (T[W].Dist) to (T[V].Dist + Cvw), will be percolate up
  #else
  					Heap.Insert( T[ V ].Dist + Cvw );
  #endif
  					T[ W ].Path = V;
  				} /* end-if update W */
  	} /* end-for( ; ; ) */
  }
  ```

  

* Other Improvements
  * Pairing Heap
  * Fibonacci Heap

- 算最短路个数

  ```c
  void ShortestDist( MGraph Graph, int dist[], int count[], Vertex S ) {
      _Bool hasVisited[MaxVertexNum] = {0};
      for (int i = 0; i < Graph->Nv; i++) {
          dist[i] = INFINITY;
          count[i] = 0;
      }
      dist[S] = 0;
      count[S] = 1;
      hasVisited[S] = 0;
      for (int i = 1; i < Graph->Nv; i++) {
          Vertex minUnV = 0;
          int minDist = INFINITY;
          for (int loopV = 0; loopV < Graph->Nv; loopV++)
              if (dist[loopV] < minDist && !hasVisited[loopV]) {
                  minUnV = loopV;
                  minDist = dist[loopV];
              }
          hasVisited[minUnV] = 1;
  
          for (int loopV = 0; loopV < Graph->Nv; loopV++) {
              if (Graph->G[minUnV][loopV] <= 0)
                  continue;
              if (minDist + Graph->G[minUnV][loopV] == dist[loopV] ) {
                  count[loopV] += count[minUnV];
              }
              if (minDist + Graph->G[minUnV][loopV] < dist[loopV]) {
                  dist[loopV] = minDist + Graph->G[minUnV][loopV];
                  count[loopV] = count[minUnV];
              }
          }
      }
      for (int i = 0; i < Graph->Nv; i++)
          if (dist[i] == INFINITY) {
              dist[i] = -1;
              count[i] = 0;
          }
  }
  ```

  