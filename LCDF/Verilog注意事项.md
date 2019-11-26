阻塞与非阻塞

`<=`仅用在行为描述方式中(`initial`, `always`)给`reg`类型赋值，assign中只能用阻塞的

---

`initial`与`always`中仅有寄存器类型能被赋值

---

规约操作符

`&, ~&, |, ~|, ^, ~^`

---

连续赋值语句(assign)是并发执行的，也就是说各语句的执行顺序与其在描述中出现的顺序无关。

---

<S>自带模块也要表明引脚</S>

<S>`NOR4 XX(nQa, nQb, nQc, nQd, Rc);`能通过语法检测但无法实现功能，要写成`NOR4 XX (.I0(nQa), .I1(nQb), .I2(nQc), .I3(nQd), .O(Rc));`</S>

更正：

默认是先输出后输入，用`NOR4 XX(Rc, nQa, nQb, nQc, nQd);`就可以了

---

骚操作：`assign {count,sum} = a + b + cin;`（三位加法器，其中a、b是三位比特数）

---

`wire`与`reg`区别

- `wire`: Cannot "hold" value. Must be continuously assigned.
- `reg`:  Can "hold" value. Can be conditionaly assigned.

---

defparam

```verilog
FD FFDA (.C(clk),.D(Da),.Q(Qa));
defparam FFDA.INIT = 1'b0; //define initial value of the D type Flip-Flop
```

.INIT并非每个实例都有的，FD是有，拿基础门试了一下就没有

*这个初值是输入初值还是输出的？*

试一下发现是。。。

---

