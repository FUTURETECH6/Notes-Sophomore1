# Nov26

一些在Nov19中提及

#### Acyclic Graphs(无圈图)



### Application of Graphs

#### Network Flow

##### Solution 1

* **Gf**: Flow Graph
  * Maintain the biggest Flow when ended
* **Gr**: Residual Graph
  * 表示对于每条边还能添加上多少流，即 Gr = G - Gf

**Step**

1. Find any path s $\rightarrow$ t in Gr (Augmenting Path)
2. Take the minimum edge on this path as the amount of flow and add to Gf
3. Update Gr and remove the 0 flow edges
4. if (there is a path s $\rightarrow$ t in Gr ) {Goto Step 1;} else {end;}

##### Solution 2: Ford–Fulkerson, Undo-able Greedy

找到的最大的若不连通则需要找第二大，以此类推直到有能连通的，或找不到了就退出

```c
    if (maxVal > 0) {
        int tmp = find_AgPath(iMaxNext, __min(curFlow, G[iCurSat][iMaxNext]));
        if (tmp > 0) {
            G[iCurSat][iMaxNext] -= tmp;
            G[iMaxNext][iCurSat] += tmp;
            return tmp;
        }
        if (tmp == 0)
            goto findLessMax;
    }
```



#### 连通分支

* Kosaraju
* Tarjan