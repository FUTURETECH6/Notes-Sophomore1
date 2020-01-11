# 



## Electric

[TOC]

> 引入常量：$\epsilon_0 = 8.854 \times 10^{-12} F \cdot m$
>
> $[\epsilon_0] = F \cdot m = $

### Ch22-2 Electric Field

**A Charged Electric Dipole**：The configuration of two equal and opposite charges ±*q* separated by a small distance *d*

#### Electric dipole moment $\vec p$ (电偶极矩)

The electric property of “electric dipole ” is described by the so-called electric dipole moment(电偶极矩): 

$\vec p=q\cdot \vec d\ (\vec d方向从-q到+q)$

##### 电偶极矩的电场

推导很麻烦，结论也不好记，看看就好吧能记尽量记

$\vec{E_p} = \frac1{4\pi\epsilon_0r^3}(-\vec p+3\frac{\vec r \cdot (\vec r \cdot \vec p)}{r^2})$($\vec r$为从dipole中心到该点的位移矢量)

#### Some conclusion


- 无限大带电平面：$E=\frac{\sigma}{2\epsilon_0}$
- 无限长带电棒：$E=\frac{\lambda}{2\pi\epsilon_0r}$
- 带电圆环：$E=\frac{1}{4\pi\epsilon_0}\frac{\lambda(2\pi R)z}{(R^2+z^2)^\frac{3}{2}}\hat k=\frac{1}{4\pi\epsilon_0}\frac{qz}{(R^2+z^2)^\frac{3}{2}}\hat k$
- 带电圆盘：$\frac{\sigma}{2\epsilon_0}(1-\frac{z}{\sqrt{z^2+R^2}})\hat k$
  * $当z\gg R，等效为点电荷，\frac{z}{\sqrt{z^2+R^2}}=[1+\frac{R^2}{z^2}]^{-\frac1 2}\approx 1-\frac 1 2\frac{R^2}{z^2}，代入得E=\frac{q}{4\pi \epsilon_0z^2}\hat k\\$
  * $当R\gg z，等效为无限面，E=\frac{\sigma}{2\epsilon_0}\hat k\\$
- 球、球壳均可等效为点电荷。


### Ch23 Gauss's Law

*Electeic Flux* 电通量
$$
Gauss'Law:\Phi=\oint_S \vec E \cdot d\vec A=\frac{1}{ε0}\sum_{inside\ S}q_i
$$

无论导体是否有cavity，cavity里是否有charge，导体的电荷仅在表面(内/外)上有，导体内部无电荷。

### Ch24 Electric Potential

**混合积公式**：$ \vec a \cdot(\vec b \times \vec c)=\vec b \cdot(\vec c \times \vec a)=\vec c \cdot(\vec a \times \vec b) $

#### 梯度散度旋度

[如何直观形象的理解梯度，散度，旋度？ - 知乎](https://www.zhihu.com/question/24074028) ([第一个回答](https://www.zhihu.com/question/24074028/answer/26657334)较浅显，[第二个回答](https://www.zhihu.com/question/24074028/answer/31526009)较清晰)

[4.6: Gradient, Divergence, Curl, and Laplacian - Mathematics LibreTexts](https://math.libretexts.org/Bookshelves/Calculus/Book%3A_Vector_Calculus_(Corral)/4%3A_Line_and_Surface_Integrals/4.6%3A_Gradient%2C_Divergence%2C_Curl%2C_and_Laplacian)
$$
\nabla=\frac{d}{d\vec n}\hat{e_n}
=\frac{\partial}{\partial x}\hat i+\frac{\partial}{\partial y}\hat j+\frac{\partial}{\partial z}\hat k\\
$$

##### 梯度

$$
计算标量场中f的变化速率，包括该点变化率最大的大小及方向\\
标量\Longrightarrow向量\\
grad f=\nabla f
=\frac{\partial f}{\partial x}\hat i+\frac{\partial f}{\partial y}\hat j+\frac{\partial f}{\partial z}\hat k\\
$$

##### 散度

$$
计算向量场\\
向量\Longrightarrow标量\\
div f=\nabla\cdot f=\frac{\partial f}{\partial x}+\frac{\partial f}{\partial y}+\frac{\partial f}{\partial z}\\
\left \{ \begin{array}{}
	divf>0 & 该点有散发通量的正源(发散源/source)\\
	divf<0 & 该点有吸收通量的负源(洞或汇/sink)\\
	divf=0 & 该点无源\\
\end{array}\right.\\
(若是单位体积不包含该电荷，那么毫无疑问，有多少电场线进入就有多少电场线出，散度为0；\\
但若选取的单位体积内包含了一个正点电荷，则电场线只出不进，因而散度不为零)
$$

##### 旋度

[旋度 - 维基百科，自由的百科全书](https://zh.wikipedia.org/zh-hans/旋度)

$$
向量\Longrightarrow向量\\
curlf=\nabla\times f= 
\left[ \begin{array}{}
	\frac{\partial}{\partial x} \\
	\frac{\partial}{\partial y} \\
	\frac{\partial}{\partial z}
\end{array}\right]
\times
\left[ \begin{array}{}
	f_x\\f_y\\f_z
\end{array}\right]
=\left[ \begin{array}{} 
	\frac{\partial z}{\partial y}-\frac{\partial y}{\partial z}\\
	\frac{\partial x}{\partial z}-\frac{\partial z}{\partial x}\\
	\frac{\partial y}{\partial x}-\frac{\partial x}{\partial y}
\end{array}\right]\\
= (\frac{\partial z}{\partial y}-\frac{\partial y}{\partial z})\hat i+
	(\frac{\partial x}{\partial z}-\frac{\partial z}{\partial x})\hat j+
	(\frac{\partial y}{\partial x}-\frac{\partial x}{\partial y})\hat k\\
$$

##### Ex. 场

* 电场是有源无旋场
* 磁场是无源有旋场

#### 电势

$$
从点电荷出发，V_i(r_i)=\int_r^\infty\frac{q_i}{4\pi\epsilon_0{r_i}^2}dr=\frac{q_i}{4\pi\epsilon_0r_i}，因此V=\Sigma V_i(r_i)=\frac 1{4\pi\epsilon_0}\Sigma\frac{q_i}{r_i}；\\
从电场出发，V=\int_r^\infty \vec E\cdot d\vec l\\
$$

#### 电势差

$$
从功能角度：dW_{Electric\ Field\ on\ charge}=q_0\vec E\cdot d\vec l，W=\int_i^fq_0\vec E\cdot d\vec l，\\
又\because W=-\Delta U=-q\Delta V=-q(V_f -V_i)，\therefore \Delta V=-\int_i^f\vec E\cdot d\vec l\\
从电场：\Delta V=(\int_f^\infty-\int_i^\infty)(\vec E\cdot d\vec l)=-\int_i^f\vec E\cdot d\vec l
$$

#### 电势与电压

$$
E_\vec l=-\frac{\partial V}{\partial\vec l}=-\nabla V
$$

#### ==自能与互能==

$$
U_互=\frac1 2\Sigma q_i V_{其他q在q_i处}=\frac1 2\int_? Vdq\\
U_自=\int_0^QV_{体系中已有的电荷在dq处}dq
$$

[自能与互能(百度百科)](https://baike.baidu.com/item/静电能)

[静电势能中的自能和互能有什么区别？还有就是电势能和静电势能的区别？ - FUTURETECH6的回答 - 知乎](https://www.zhihu.com/question/303819123/answer/843921203)

> 所谓“自能”就是将一个带电体看成无穷个带电微元，将这些无穷多个带电体微元从无限分散状态聚集成该带电体，外力所做功的大小。所谓“互能”则是将带电体系统中，各带电体从现在位置彼此分开至无穷远时，它们之间的静电力所做的功。
>
> 静电能包括自能和互能。点电荷的自能是无穷大，一般在静电学问题中都不考虑点电荷的自能。

互能算两次有1/2 自能无1/2

**Ex.半径R带电Q的球体能量计算**

<u>注意：仅在表面有电荷</u>
$$
U = 
\left \{ \begin{array}{}
	互能：\frac 1 2\int \frac{Q}{4\pi \epsilon_0 R}dq = \frac{Q}{8\pi \epsilon_0 R} \int dq
	\\
	自能：\int_0^Q \frac{q}{4\pi \epsilon_0 R}dq
	\\
	电容：\frac{Q^2}{2C} = \frac{Q^2}{2(4\pi \epsilon_0 R)}
\end{array} \right \}
= \frac{Q^2}{8 \pi \epsilon_0 R}
$$

*第三种算法中$C = 4\pi \epsilon_0 (\frac{\infty R}{\infty - R})$。因为仅球壳外表面(外侧)带电，因此可视作由外表面到无穷远的电容器，也可算$V = \frac{Q}{4 \pi \epsilon_0 R}, C = \frac Q V$。*

### Ch25 Conductors

#### 等势体

##### Ex.

$$
两个相距无限远的导电圆球，总电量为Q，用导线将两者表面相连，求电荷分布\\
\frac{q_1}{4\pi\epsilon_0R_1}=\frac{q_2}{4\pi\epsilon_0R_2}\\
\Longrightarrow \frac {q_1} {q_2}= \frac {R_1} {R_2}
$$

### Ch26-1 Capacitance

#### 计算方式

$$
设电量为q，利用\Delta V=V_+-V_-=\int_+^-(-\nabla V)\cdot d\vec l=\int_+^-\vec E\cdot d\vec l\\
可以获得\Delta V=(...)\cdot q
$$

#### Conclusion

- **Parallel-Plate Capacitor**

$$
E=\frac \sigma {\epsilon_0}(G's\ Law)\\
C=\frac{\epsilon_0A}d\\
$$

- **Cylindrical Capacitor**

$$
C=2\pi\epsilon_0\frac L{ln(R)-ln(r)}\\
$$

- **Spherical Capacitor**

$$
C=\frac{4\pi\epsilon_0}{\frac1r-\frac1R}
=4\pi\epsilon_0(\frac{Rr}{R-r})
$$

**单个平行板电容器，仅在向对面有电荷，外面不带电荷**

==注意，平行板电容器的电场是$\frac \sigma {\epsilon_0}$。因为两板都有电荷，因此高斯定律得分成两部分计算==

#### 串并联

- Series Connection, 串联，q相同，$\frac 1 C = \Sigma \frac 1 C_i$
- Parallel Connection, 并联，V相同，$C = \Sigma C_i$


##### 应用

<u>将导体插入平行板中，$C'=\frac{\epsilon_0A}{d-t}$(视作串联即可)</u>

#### 能量

$$
U =
\left \{ \begin{array}{}
	\frac{q^2}{2C}
	\\
	\frac{q \Delta V}{2}
	\\
	\frac{\epsilon_0 E^2 \Omega}{2}
\end{array} \right.
$$

##### 能量计算

$$
微分中，\left|\Delta V'\right|=\frac {q'}c，dU=dq'\left|\Delta V'\right|=\frac{q'dq'}C\\
若全程，则U=\int_0^UdU=\int_0^q\frac{q'}Cdq'
\\
=\frac{q^2}{2C}\\
=\frac{q\Delta V}2\\
(q'和\Delta V'都表示过程量)
$$

##### 能量密度

$$
(只针对平行板电容器)(似乎)\\
U=\frac{q^2}{2C}=\frac{q^2d}{2\epsilon_0A}=\frac{\epsilon_0}2(\frac q{\epsilon_0A})^2(Ad)=\frac{\epsilon_0}2E^2\Omega\\
u=\frac U \Omega=\frac{\epsilon_0E^2}2\\
$$

---

### Ch26-2 Dielectrics

Q一定时，X表示插入电介质后的量值，X~0~表示真空时的量值
$$
\left \{ \begin{array}{}
	C=\kappa_eC_0\\
	\Delta V=\frac Q C=\frac Q{\kappa_eC_0}=\frac {\Delta V_0}{\kappa_e}\\
	E = \frac{\Delta V} d = \frac{E_0} {\kappa_e}\\
\end{array} \right.
\\
另外有，\\
\because \frac{Q}{\epsilon_0A}
= \frac {(Q_0 - Q')}{\epsilon_0A}
\xlongequal[始终成立]{GaussLaw} E
= \frac {E_0}{\kappa_e}
= \frac {Q_0} {\kappa_e \epsilon_0 A}
\\
\therefore Q_0
= \kappa_e (Q_0 - Q') \longrightarrow Q'
= (1-\frac 1 {\epsilon_e})Q_0
$$

==不要忘了最基本的这几个==

==本质上$\frac{E_0}{\kappa_e} = \frac{E}{1} = \frac{E'}{\kappa_e-1}$==

#### 分子角度解释

取向极化(Alignment polarization)与位移极化(Displacement polarization)

> 取向不能完全与电场线平行的原因：Because the molecules are continuously jostling each other as a result of their random thermal motion, this alignment is not complete

#### Polarization (极化强度矢量P(大写))

$$
\vec P = \frac{\sum\vec {p_i}}{\Delta V}\\
此处\Delta V表示体积\\
dQ'=qdN=qndV=qnlcos\theta dA=PdAcos\theta=\vec P\cdot d\vec A\\
\therefore \sigma' = \frac {dQ'}{dA}=Pcos\theta =\vec P \cdot \vec n = P_{\vec n}\\
$$

**一个重要结论**
$$
\mathop\oiint_s\vec P \cdot d \vec A = - \sum_{(ins)}q'_i
$$

#### Depolarization field E’ (退极化场)

$$
\vec E = \vec {E_0} + \vec {E'}
$$

#### Polarization law of dielectrics (电介质的极化规律)

$$
\vec P \Longrightarrow \sigma' \Longrightarrow \vec E' \Longrightarrow \vec E\\
$$

####  Polarization coefficient $\chi_e$ (极化率)

for general isotropic(各向同性) materials
$$
\vec P = \chi_e \epsilon_0 \vec E\\
其中，\chi_e = \kappa_e - 1
$$

#### Electric displacement vector $\vec D$ (电位移矢量)

$\vec D = \epsilon_0 \vec E + \vec P\\ = \epsilon_0 \vec E + \chi_e \epsilon_0 \vec E = (\kappa_e \epsilon_0) \vec E$

**产生原因**：
$$
In\ Dielectric,\ \vec E \neq 0\\
\vec {E_0} \longrightarrow \vec P \longrightarrow \sigma_e' \longrightarrow \vec{E'} \longrightarrow \vec E = \vec {E_0} + \vec {E'}\\
$$
##### 定理：环积分等于原电量

$\oiint \vec D \cdot d \vec A= \Sigma_{i}q_0$

**Proof**:
$$
在某电介质中，有带电+Q_0的球\\
\oiint \vec P \cdot d \vec A = - \sum_{ins} q'？？？
(\sigma' = P，然后负号是因为定义d\vec A方向向外而\vec P是向内的？)
\\取一个包住内表面的高斯面\\
\therefore \epsilon_0 \oiint \vec E \cdot d \vec A
\xlongequal{Gauss} \sum_{ins} (q_0 + q')
\xlongequal{上式} \sum_{ins}q_0 - \oiint \vec P \cdot d \vec A\\
\therefore \oiint (\epsilon_0 \vec E + \vec P) \cdot d \vec A
= \sum_{ins}q_0\\
\vec D \overset {\triangle} {=} \epsilon_0 \vec E + \vec P\\
\therefore \oiint \vec D \cdot d \vec A
= \sum_{i}q_0\\
$$
Also
$$
\vec D = \epsilon_0 \vec E + \vec P\\
= \epsilon_0 \vec E + \chi_e \epsilon_0 \vec E\\
= (1+\chi_e)\epsilon_0 \vec E\\
= \kappa_e \epsilon_0 \vec E
$$

(非正规地写成：$\vec D = \epsilon_0 \vec E_0$)

证明用图：<img src="普物2笔记.assets/image-20191013182554314.png" alt="image-20191013182554314" style="zoom:35%;" />

#### 多种介电质(Dielectrics)

##### PP

<img src="普物2笔记.assets/page40image3039776.jpg" alt="page40image3039776.jpg" style="zoom: 25%;" />
$$
同并联，C=\frac {\epsilon_0A}{d}(\kappa_1+\kappa_2)
$$

若上下两种电介质

$$
C_i = \frac{\kappa _i \epsilon_0 A}{d_i}\\
$$

##### 复杂一点：Sepherical

<img src="普物2笔记.assets/page41image3052000.jpg" alt="page41image3052000.jpg" style="zoom: 50%;" />
$$
\because C=4\pi\epsilon_e(\frac{Rr}{R-r})\\
\frac1C=\frac1{4\pi\epsilon_0\kappa_1(\frac{ba}{b-a})}
+\frac1{4\pi\epsilon_0\kappa_1(\frac{ba}{b-a})}\\
\Longrightarrow C=\frac{4\pi\epsilon_0\kappa_1\kappa_2 abc}{\kappa_1a(c-b)+\kappa_2c(b-a)}
$$

### Ch27 Ohm's Law

Electric Density (电流密度)
$$
j = \frac {di}{dS_{\bot}} = \frac {dq}{dtdS_\bot}
$$
Drift Velocity $v_d$ (漂移速度)

载流子移动速度
$$
i = -e \cdot n \cdot (Av_d)\\
j = \frac i A = -nev_d
$$

### Ch28 Circuit Theory

#### Kirchhoff's Law

- **First Law: Junction Rule**

  At any junction in an electric circuit, the total current entering the junction must be the same as the total current leaving the junction.

- **Second Law: Loop Rule**

   The algebraic sum of all differences in potential around a complete circuit loop($\forall$ loop) must be zero.

**Ex.** Problem 12

$\epsilon_1=10V,\epsilon_2=5V,R_1=R_2=R_3=4\Omega$

<img src="普物2笔记.assets/image-20191107184215773.png" alt="image-20191107184215773" style="zoom: 50%;" />
$$
假设i_1向右，i_2向右，i_3向下
\\
\left \{ \begin{array}{}
	i_1 = i_2 + i_3\\
	\epsilon_1-i_1R_1-i_3R_3 = 0\\
	-i_2R_2-\epsilon_2+i_3R_3 = 0\\
\end{array} \right.
\\\Longrightarrow i_1 = 1.25A, i_2 = 0
$$
==注意：方向应先假设，求出是负的再反向即可==

#### RC Circuit(串联RC)

##### 充电

$$
\epsilon - iR - \frac q C = 0 \Longrightarrow 
i = \frac{dq}{dt} = \frac{C\epsilon-q}{RC}
\\
\therefore \frac{dt}{RC} = \frac{dq}{C\epsilon-q}
\\
解微分方程得：
\\
q(t) \xlongequal{\tau \triangleq RC} C\epsilon(1-e^{-\frac t \tau})
\\
V(t) = \frac q C = \epsilon(1-e^{-\frac t \tau})
\\
i(t) = \frac{dq}{dt} = \frac \epsilon Re^{-\frac t \tau}
$$

##### 放电

$$
q = q_0 e^\frac t \tau
\\
i = \frac \epsilon Re^{-\frac t \tau}
$$