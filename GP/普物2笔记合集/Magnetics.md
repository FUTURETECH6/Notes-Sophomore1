## Magnet

[TOC]

> 新引入常量：$\mu_0 = 4\pi \times 10^{-7} T \cdot m \cdot A^{-1}$

### Ch29 Magnitude Force

==磁感应强度B != 磁场强度H==（但是并不重要因为H已经废弃，仅在磁介质的磁化问题中作为辅助量使用）

真空中有$B = \mu_0H$

$\mu_0$:Vacuum Permeability Constant 真空磁导率，值为$4\pi \times 10^{-7}\ T \cdot m \cdot A^{-1}$

#### 洛伦兹力与安培力

$$
\vec F_L = q \vec v \times \vec B\\
\vec F_A = i \vec L \times \vec B
$$

##### 通电导线

##### 通电线圈

<img src="普物2笔记.assets/image-20191027104948806.png" alt="image-20191027104948806" style="zoom: 50%;" />
$$
F_\tau = N i a B sin\theta\\
\tau = 2 F_\tau \frac b 2 =NiabBsin\theta = NiABsin\theta(\theta = <\vec n, \vec B>)\\
\vec \tau \parallel \hat n \times \vec B\\
$$

#### Magnitude Dipole

- **电偶极子**是两个分隔一段距离，[电量](https://zh.wikipedia.org/wiki/电量)相等，正负相反的[电荷](https://zh.wikipedia.org/wiki/電荷)。
- **磁偶极子**是一圈封闭循环的[电流](https://zh.wikipedia.org/wiki/電流)。例如一个有常定[电流](https://zh.wikipedia.org/wiki/電流)运行的线圈。

#### Magnetic dipole moment 磁矩μ(Loop Model)

> 由于没有发现单独存在的[磁单极子](https://baike.baidu.com/item/磁单极子/380283)，因此磁偶极子的物理模型不是两个[磁单极子](https://baike.baidu.com/item/磁单极子/380283)，而是一段封闭回路电流。

<img src="普物2笔记.assets/image-20191025161954395.png" alt="image-20191025161954395" style="zoom: 33%;" />
$$
\vec \mu = Ni \vec A
\\
\tau = \mu B sin\theta(\theta = <\vec \mu, \vec B>)
\\
\vec \tau = \vec \mu \times \vec B
\\
Energy\ U(\theta) = -\vec \mu \cdot \vec B
\\
For\ an\ orbiting\ electron,\ \mu_{orb} = iA = (\frac{e}{2\pi r/v})(\pi r^2) = \frac{evr}2,
\\
angular\ momentum(\vec L = \vec r \times \vec p):\ |\vec L_{orb}| = |m(\vec r \times \vec v)| = mrv
\\
\therefore \vec \mu_{orb} = -\frac e {2m}\vec L_{orb}
$$

### Ch30 Current – Produced Magnetic Fields 

#### Biot-Savart

$$
dB = \frac{\mu_0}{4\pi} \frac{i\ dl\ sin\theta}{r^2}
\\
d\vec B = \frac{\mu_0}{4\pi} \frac{i\ d\vec l \times \hat r}{r^2}
= \frac{\mu_0}{4\pi} \frac{i\ d\vec l \times \vec r}{r^3}
\\
\vec r：电流微元所在点到目标点(求B处)的位移矢量
$$

#### 电流生磁

##### Conclusion

\# THIS IS SCRIPT

$$
sin\theta = \frac R {\sqrt{R^2+L^2}}
\\
dB= A \frac{iRdl}{(R^2+L^2)^\frac 3 2}
\\
B = \int_a^b dB= \frac{i\mu_0R}{4\pi} \int_a^b \frac{dl}{(R^2+L^2)^\frac 3 2}
\\
(\int \frac{dl}{(R^2+L^2)^\frac 3 2} (L \triangleq \frac{Rsin\theta}{cos\theta})
= \int \frac{\frac{1}{cos^2\theta}Rd\theta}{R^3\frac 1 {cos^3\theta}}
=\frac 1 {R^2} \int cos\theta d\theta = \frac{sin(atan(\frac L R))}{R^2}+C = \frac{L}{R^2\sqrt{R^2+L^2}}+C)
\\
\therefore B = \frac{\mu_0i}{4\pi R} (\frac L {\sqrt{R^2+L^2}})|_{L=a}^{b}
$$

---

* **长直导线**：

$$
\left \{ \begin{array}{}
	中部：B = \frac{\mu_0i}{2 \pi R}\\
	一端：B = \frac{\mu_0i}{4 \pi R}?\\
\end{array} \right.\\
$$

* **弧形(单层单匝)导线圆心**：$B = \frac{\mu_0i\phi}{4\pi R} (\phi \leqslant 2\pi)$

* **距圆导线圆心L处**：$B= \frac{\mu_0 i R^2}{2(L^2 + R^2)^\frac 3 2} \\ (用dB = \frac{\mu_0}{4\pi} \frac{i\ ds\ sin\theta}{r^2}的定义而不是用圆环的结论-FMH's\ Page\ 27,\ WYW的没有)$


##### Conclusion2 coil

\* $[n] = \frac 1 m$ The number of turns per unit length 单位长度匝数

$$
螺线管coil：dB = \frac{(ndl)\mu_0iR^2}{2(l^2+R^2)^\frac 3 2}\\
(\frac{R/sin\beta}{dl} = sin\beta)\\
= \frac{\mu_0i(2\pi n)}{4\pi } (cos\beta_2 - cos\beta_1)[= (sin(\frac \pi 2-\beta_2) + sin(\beta_1 - \frac \pi 2))]\\
特殊的，当coil\ length \rightarrow \infty，有
\left \{ \begin{array}{}
	B_内 = n\mu_0i\\
	B_侧 = \frac 1 2 n\mu_0i\\
\end{array} \right.\\
$$

<img src="普物2笔记.assets/image-20191028125709888.png" alt="image-20191028125709888" style="zoom: 25%;" />

<img src="普物2笔记.assets/image-20191028194018555.png" alt="image-20191028194018555" style="zoom: 50%;" />

##### Conclusion3 parallel current

$$
F_{12}= F_{21} = \frac{\mu_0i_1i_2L}{2\pi d}\\
$$

#### 粒子生磁

$$
d\vec B = \frac{\mu_0}{4\pi} \frac{i\ d\vec s \times \hat r}{r^2}
= \frac{\mu_0}{4\pi} \frac{i\ d\vec s \times \vec r}{r^3}\\
i = \frac{dq}{dt}\\
id\vec s = \vec vdq,\ when\ there\ is\ only\ one\ particle\ carrying\ a\ single\ charge,\ dq = q\\
d\vec B = \frac{\mu_0}{4\pi} \frac{dq\ \vec v \times \hat r}{r^2} 
\therefore \vec B = \frac{\mu_0}{4\pi} \frac{q\ \vec v \times \hat r}{r^2}
$$

#### Ampere's Law(电生磁)

<img src="普物2笔记.assets/image-20191028200245926.png" alt="image-20191028200245926" style="zoom:33%;" />
$$
\mathop\oint_L \vec B \cdot d\vec l = \mu_0 \sum i(\forall surface\ binded\ by\ Amper\_Loop)
\\
右式正方向同\vec L(\vec n)
\\
若导线有限长，则必存在一曲面使得该面上净电流为0，因此安培定律不适用
$$

### Ch31 Self-Induction

#### Gauss's Law

$$
\left \{ \begin{array}{}
	\Phi_E = \oint \vec E \cdot d\vec A = \frac{q_i}{\epsilon_0}\\
	\Phi_B = \oint \vec B \cdot d\vec A = 0\\
\end{array} \right.
$$

#### Faraday’s Law(感应电动势)

$$
\epsilon = \oint \vec E \cdot d \vec s = -\frac{d\Phi _B}{dt} 【s为长度量】
$$

#### Inductance

$$
Def: L = \frac{N\Phi_B}{i},\Psi_B = N\Phi B=Li
\\
\frac L l = \mu_0n^2A(solenoid)
\\
Combine\ FL,\ \Phi_L = -\frac{d\Psi_B}{dt} = -L\frac{di}{dt}
$$

#### 动生电动势

$$
\Delta V = -\int \vec E \cdot d \vec l = \int (\vec v \times \vec B) \cdot d \vec l
$$

#### 动感混合

Ex.
$$
(使用矩形模型)
\\---1---\\
V_动 = v_\perp l_\perp B_{t_0};
\\
V_感 = A \frac{dB}{dt};
\\
V_合 = V_动+V_感;
\\---2(推荐使用此种，防止出现错误)---\\
\Phi = (B_{t_0} + \frac{dB}{dt}t)(A+vt \cdot l)
\\
V = |-\frac{d\Phi}{dt}| = \frac{d(AB_{t_0}+(vlB_{t_0}+A\frac{dB}{dt})t)+o(dt)}{dt}
= vlB_{t_0} + A \frac{dB}{dt};
$$