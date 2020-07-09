---
layout:     post
title:      第一章 飞行器质心运动方程
subtitle:   
date:       2020-07-05
author:     Zeyuan
header-img: img/418th_Flight_Test_Squadron_-_MC-130E.jpg
catalog: true
tags:
    - 航空飞行器飞行动力学
---
- 这里是一个目录
{:toc}
# 第一章 飞行器质心运动方程

研究飞机的飞行性能和飞行轨迹特性时，可将飞机视为一**可控的质点**来处理。

**质点运动**: 通过偏转操纵机构，使飞机的**合力矩为零**;研究飞机的飞行轨迹和飞行性能时可以把飞机视为质点运动。**力矩平衡作为运动的约束条件**。

# 作用在飞机上的外力

![image-20200705151635578](https://tva1.sinaimg.cn/large/007S8ZIlgy1gggeqckzshj30vs084wfn.jpg)

合外力F  = W + T +A  <u>一般不通过质心，它将引起绕质心转动的力矩</u>

- 重力 W = mg
- 推力 T(V, H, n)
- 空气动力 A = L+D+C 升+阻+侧
  - $L = \frac{1}{2}\rho V^2 S C_L$
  - $D = \frac{1}{2}\rho V^2 S C_D$
  - $C = \frac{1}{2}\rho V^2 S C_C$ ：通常考虑为0（假设无侧滑）
  - 升力和阻力系数（$C_L,C_D$）主要取决于马赫数(M)，雷诺数(Re)，迎角($\alpha$)，侧滑角($\beta$, 右侧滑为正，与$\psi$相反)以及飞机外形。
    - 马赫数M：指空气的压缩性效应;低速空气 流场不相互影响，高速时则前后相互影响。
    - 雷诺数Re：惯性力和粘性力的比值。一般飞机：1000万以上。

假设操纵面偏转可使力矩平衡，但将其最大 平衡能力作为约束。实际还常忽略操纵面偏转对力平衡的影响。

## 升阻特性

### 升力

升力部件：翼-身组合体，平尾

飞机上的空气动力的合力在飞机纵向对称平面上垂直于飞行速度方 向的分力。向上为正。$C_L$最大值约1.2-1.5。加增升装置可提高到2.2-3.0。

#### 升力系数小迎角范围 

$C_L = C_{L\alpha}(\alpha - \alpha _0) + C_{L\delta _e} \delta_e$ 第二项为升降舵偏转产生的升力，对于有尾飞行器，较小可忽略。

#### $C_{L\alpha}$: 升力线斜率

- 与翼型、机翼平面形状、 M数有关，即M，后掠角$\chi$，展弦比$\lambda$。取值0.05-0.09（单位deg）

- <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gggf8c0oy5j30b40fst9r.jpg" alt="image-20200705153355518" style="zoom:33%;" />
- <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gggfc5n1y0j30fu0cs0tx.jpg" alt="image-20200705153736053" style="zoom:50%;" />
- $C_{L\alpha}$ - M关系：亚声速 $C_{L\alpha} = \frac{C_{L\alpha,M=0}}{\sqrt{1-M^2}}[翼型]$ 。运输类飞机在高亚声速飞行时可获得高气动效率。超声速：$C_{L\alpha} = \frac{4}{\sqrt{M^2-1}}[翼型]$ 超声速飞机以略高声速巡航气动效率最高。
- 小后掠角，大展弦比飞机$C_{L\alpha}$越大

#### $\alpha _0$零升迎角

- 取决于机翼有效弯度和 M数,即～M，f。低速翼型-2- -4度，起降构型-6 - -10度。
  - <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghe6ci6bfj30gu0dw75b.jpg" alt="image-20200705214739077" style="zoom:50%;" />
  - 失速之前，飞行迎角增大，上下翼面的压差大，升力系数增大。

#### 典型升力系数

最大升力系数$C_{Lmax}$，失速升力系数$C_{Ls}$，限制升力系数（抖振）$C_{Lsh}$，最大允许升力系数$C_{La}$，操纵限制升力系数$C_{L\delta.max}$(保持飞机俯仰力矩平衡的限制。超声速时焦点后移，升降舵操纵效率下降。如果升力系数（迎角）太大，升降舵无法实现纵向力矩的平衡)

最大允许升力系数$C_{La}$。<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gggq7fqrm4j30lm0ki402.jpg" alt="image-20200705215335804" style="zoom:33%;" />

- 不同飞行速度飞机以不同构型获得好的气动特性。**巡航时设计基准状态。低速需要增升。**

### 阻力

摩擦阻力，压差阻力，粘性阻力，波阻，诱导阻力

**摩擦阻力**：浸润面积。 决定了飞机最大平飞速度。

#### 阻力系数（极曲线）

$C_D = C_{D0} + C_{Di} = C_{D0}+AC_L^2$

#### 零升阻力系数$C_{D0}$

与升力无关，取决于外形，M，Re。范围0.02-0.04

- 与构型关系：长细比增加，机翼薄，CD0越小。
- <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gggqgpeh6kj30es0dyjsd.jpg" alt="image-20200705220225903" style="zoom: 50%;" /> 

#### 升致阻力$C_{Di}$

诱导阻力。机翼翼梢产生翼梢绕流，后缘尾涡。产生诱导下洗流作用于机翼及其后区域。耗散能量。

- 升致阻力因子A取决于外形，M，Re。亚声速时，随展弦比增大而减小（对M基本不变）$A = \frac{1}{\pi \lambda}$ （这是对于椭圆形机翼，如果不是椭圆形需要在展弦比前乘自然常数e）。超声速时，随M增大，波阻和压差阻力增大。$A = \frac{1}{C_{L\alpha}}\approx\frac{\sqrt{M^2-1}}{4}$<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gggqnxgml0j30iq08w74u.jpg" alt="image-20200705220927103" style="zoom:50%;" />

#### 极曲线

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gggqwbxliyj30eu0co3z1.jpg" alt="image-20200705221731694" style="zoom:50%;" />

- **M数增大，极曲线右移**。M数<0.6时，空气压缩性 不变，升力(阻力)系数基 本与M数无关，极曲线重合;M数>1后，波阻增大，曲线右移，跨声速段更明显。
- **M数增大，极曲线会变弯**。A随M数增加而增大，大M数、大升力系数时，阻力系数增大，极曲线弯度增大。

#### 升力系数和阻力系数的典型数值

| 最大升力系数         | 1.2**—**1.5   |
| -------------------- | ------------- |
| 起降阶段最大升力系数 | 2.0**—**2.5   |
| 阻力系数             | 0.02**—**0.1  |
| 最大阻力系数         | <0.1          |
| 零升阻力系数         | 0.02**—**0.04 |

**阻力系数的计算和测量均非常困难!**

### 升阻比

$K = C_L/C_D$

飞机的升力和阻力会同时增加，因此需用升阻比来衡量飞机的气动特性

#### 最大升阻比，有利迎角，有利升力系数

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gggr3vsa15j30h00i6taf.jpg" alt="image-20200705222445835" style="zoom:50%;" /> $K_{max} = (C_L/C_D)_{max} = \frac{1}{2\sqrt{AC_{D0}}}$, CL取$\sqrt{\frac{C_{D0}}{A}}$, 对应$C_{Lopt}=\sqrt{\frac{C_{D0}}{A}},\alpha _{opt}=\sqrt{\frac{C_{D0}}{A}}/C_{L\alpha}+\alpha_0$, $C_{Di} = C_{D0},C_D = C_{Di}+C_{D0} = 2C_{D0}$

- 最大升阻比状态下,零升阻力系数等于升致阻力系数
- 升阻比大,巡航经济性**(航时最长)**和机动性好。
- 亚声速飞机最大升阻比为17-18;跨声速时约达12;超声速时可达6。飞翼布局（无全尾，全翼机）可达20以上。
- 民机采用M数与升阻比的乘积表示巡航效率**(航程最长)**。

# 发动机推力

- 空气喷气发动机**(**氧**+**燃料**)**
  - 涡喷：歼七、歼八
  - 涡扇：旅客机、F16、J10、 J11 J20
  - 涡桨：低空、低速军(民)运输机，运七、运八
- 火箭发动机（氧化剂+燃料）

### 涡轮喷气发动机

单个流道内靠喷管喷出高速燃气产生推力的燃气涡轮发动机。

### 涡轮风扇发动机

特点:压气机前装有风扇，由喷管排出燃气和风扇排出空气共同产生推力;内外二个涵道构成的燃 气涡轮发动机。

大涵道比(外涵道大)发动机排气速度低、推进 效率高 ;经济性好，适用于大型旅客机，因风扇迎风面积大，不宜超声速飞行;旅客机。

军用作战飞机采用小涵道比风扇发动机;F16。

### 涡轮螺旋桨发动机

特点:功率式发动机。由螺旋桨提供拉力，也靠喷气反作用(约10%，常被忽略)提供推力的燃气涡轮发动机，油耗低。

使用速度不超过800千米**/**小时。

### 推力产生原理

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gggrwl0u8yj30qq0ak74w.jpg" alt="image-20200705225222837" style="zoom:50%;" /> m':质量流量

### 涡轮喷气发动机的四个性能指标

1. **台架推力Ti** ：发动机在试车台上测得的推力，与转速n，飞行速度V，飞行高度H有关
2. **可用推力Ta** :发动机安装到飞机上后，真正的作用推力  $T_a=i\eta T_i$, $\eta$为推力损失系数。
3. **推重比$\gamma_{TW}$**：地面最大推力与结构重量之比，与设计材料和工艺水平有关。8-10。$\gamma_{TW} = T_a/W_e$.
4. **耗油率Cf**：单位时间产生单位推力所消耗的油量。～n, V, H **与m‘正比，T反比。**

### 涡轮喷气发动机典型油门状态

1. **加力状态:**开动加力燃烧室，对应于最大转速，推力较最大状态 增加**30-50%**，耗油率增加近一倍以上，连续工作时间限**5-10min**。**紧急情况使用。**
2. **最大状态**:对应于最大许用转速($n_{max}$) 状态 。推力为非加力时的最大值。只能连续工作**5-10min**，常用于起飞、短时加速、爬升、空中机动等。
3. **额定状态**:对应于最大转速**97%** ，推力为最大状态的**85-90%**，可较长时间工作**(半小时~1小时**)，用于平飞、爬升、远航飞行等。
4. **巡航状态**: **n~巡~≈90% n~额~，Ta~巡~ ≈ 80%Ta~额~**，耗油率最小，不限时， **用于巡航**。
5. **慢车状态**:**n~慢~ ≈ 30% n~额~**，推力很小，**Ta慢 ≈ 35%Tamax**，连续工作时间不允许超过**10-15min**，用于**下滑、着陆**。

### 涡轮喷气发动机特性

- 转速特性（油门特性） H，V一定，Ta，Cf和n关系
  - Ta～n^3^ <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghchyy1jfj30vk0fowh4.jpg" alt="image-20200706104451806" style="zoom:40%;" />

- 速度特性: H,n 一定，T和Cf与V（M）的关系：
  - <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghcjgf9nnj30v80kqwi8.jpg" alt="image-20200706104617133" style="zoom:40%;" />

- 高度特性：V，n一定，T，Cf与H关系
- <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghckt5rvdj30vk0is0wb.jpg" alt="image-20200706104735572" style="zoom:40%;" />

# 常用坐标轴及其转换

不同坐标系用于描述和处理不同的问题。

飞机的多个状态变量只能在不同的坐标系中描述。

军委你右手正交

## 地面轴系 Ox~g~y~g~z~g~ 惯性坐标系

Og为地面任意一点(如起飞点);

Oxg轴指向地平面某一任意方向(通常与飞行任务有关)

Ozg轴位于铅垂平面，垂直于纵轴Oxg，指向下方为正;

Oyg轴按右手法则确定。

由于地球作了静止和平面假设，所以该坐标系可视为惯性坐标系。**飞机的位置、姿态、地速(地加速度)等都是相对该坐标系来描述的。**

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghctlql8jj30g20jg0un.jpg" alt="image-20200706105603461" style="zoom:33%;" />

## 机体轴系Ox~b~y~b~z~b~ 动坐标系

 固联于飞机并随其一起运动的一种动坐标系.(**不垂直地面**)

Ob为飞机质心;

**Oxb纵轴 沿飞机结构纵轴(与机身轴线平行或者机翼平均气动弦线)，指向机头为正;**

Ozb竖轴 位于对称平面，垂直于纵轴Oxb，指向下方为正;

Oyb横轴 垂直于飞机对称面，指向右翼为正。

**飞机的发动机推力和三个气动力矩(滚转、偏航和俯仰 力矩)通常按该坐标系来定义。**

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghcw4zokpj30we0monaq.jpg" alt="image-20200706105830064" style="zoom:33%;" />

## 气流轴系Ox~a~y~a~z~a~ 动坐标系

表征气流速度矢量与飞机本体相联系的一种坐标系。**与机体轴系的区分为迎角和偏航。**

Oa为飞机质心;

**纵轴 Oxa沿气流速度矢量va (飞机的空速方向)， 指向机头为正;**

竖轴 Oza轴位于对称平面内，垂直于气流速度矢 量，指向下方为正;

横轴 Oya垂直于Oxaza平面，指向右为正。

**飞机的三个气动力(升力、阻力和侧力)通常按 该坐标系来定义。**

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghd0x04avj30lm0emn14.jpg" alt="image-20200706110225123" style="zoom:33%;" />

## 航迹轴系Ox~k~y~k~z~k~ 动坐标系

由飞机航迹速度矢量vk决定。与地轴系区分为：地轴系的Ox为任意方向。

Ok为飞机质心;

**纵轴 Oxk指向地速矢量vk方向，指向机头为正;**

竖轴 Ozk轴位于包含Oxk轴的铅垂平面内，垂直于Oxk轴，指向下方为正;

横轴 Oyk垂直于Oxkzk平面，指向右为正。

**航迹轴系相对于地轴系的关系即描述了飞机的运动航迹。**

## 坐标转换矩阵

### 平面坐标系转换

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghda91wzij30us0k8go5.jpg" alt="image-20200706111205825" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghdb8eq27j30r206mdgf.jpg" alt="image-20200706111302372" style="zoom:50%;" />

记法：p对q逆时针alpha，从p到q的变换

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghdc0opkaj30v80deq4m.jpg" alt="image-20200706111346153" style="zoom:50%;" />

### 空间坐标系转换

p到q系，欧拉角$\zeta,\eta,\xi$ : **先绕Oz转$\zeta$, 再绕Oy转$\eta$, 再绕Ox转$\xi$。****所以从p到q先偏航，再俯仰，最后滚转。**

$L_{qp} = L_x(\xi)L_y(\eta)L_z(\zeta)$ 特征与二维的相同

$$L_z =  \left[ \begin{matrix}   cos\alpha & sin\alpha & 0 \\   -sin\alpha & cos\alpha & 0 \\   0 & 0 & 1  \end{matrix}  \right]  $$

$$L_y =  \left[ \begin{matrix}   cos\alpha & 0 & -sin\alpha\\   0 & 1 & 0 \\   sin\alpha & 0 & cos\alpha  \end{matrix}  \right]  $$

$$L_x =  \left[ \begin{matrix}   1 & 0 & 0\\   0 & cos\alpha & sin\alpha \\   0 & -sin\alpha & cos\alpha  \end{matrix}  \right]  $$

角速度与欧拉角的关系：$$L_{rotate} = \left[ \begin{matrix} p\\q\\r \end{matrix} \right]   =\left[ \begin{matrix}   1 & 0 & -sin\theta \\   0 & cos\phi & sin\phi cos\theta \\   0 & -sin\phi & cos\phi cos\theta \end{matrix}  \right]\left[ \begin{matrix} \dot \phi \\ \dot \theta \\ \dot \psi \end{matrix}\right]  $$ **其中p，q，r是动坐标系下的角速度分量。**

#### 地面坐标系与机体坐标系

地速 = 空速 + 风速

飞行轨迹与地速有关;气动力与空速有关

机体坐标系相对于地面坐标系的方位(飞机在空中的姿 态)，常用三个欧拉角(姿态角)来表示

- **偏航角** $\psi$ :即机体轴Ox~b~ 在水平面Ox~g~y~g~上的投影与 Ox~g~ 轴 之间的夹角。当该投影线偏向 Ox~g~ 的右方时，偏航角为正; (右偏航)

- **俯仰角$\theta$**: 机体轴Ox~b~与水平面Ox~g~y~g~之间的夹角。纵轴偏向上方为正。（仰为正）

- **滚转角$\phi$:** 飞机对称平面Ox~b~z~b~ 与包括纵轴Ox~b~ 的铅垂平面之间的夹角。飞机右滚形成的角度为正。

**从地面到机体：$L_{bg} = L_x(\phi)L_y(\theta)L_z(\psi)$**

**从机体到地面：$L_{gb} = L_z(-\psi)L_y(-\theta)L_x(-\phi)$**

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghe5r6iiwj30xa0oujv9.jpg" alt="image-20200706114224109" style="zoom:33%;" />

#### 地面坐标系与航迹坐标系

航迹坐标系相对于地面坐标系的方位常用**二个欧拉角(航迹角)来表示**。它决定了飞机地速在空间的方向，即飞行航迹。

- **航迹偏角 χ** :航迹轴 Ox~k~ 在水平面 Ox~g~y~g~ 上的投影与纵轴 Ox~g~ 之间的夹角。航迹向右偏转时χ为正。又称为航向角。

- **航迹倾角$\gamma$:** 又称爬升角。航迹轴Ox~k~ 与水平面Ox~g~y~g~之间的夹角。航迹上倾为正。

**从地面到航迹：$L_{kg} = L_y(\gamma)L_z(\chi)$**

#### 航迹坐标系与气流坐标系

**航迹坐标系与气流坐标系在无风的情况下，只用一个角度即可确定。**

- **速度滚转角$\mu$ :** 飞机对称平面Ox~b~y~b~与含速度矢量V的铅锤平面之间的夹角。绕速度矢量V右滚转形成为正。

从航迹到气流：$L_{ak} = L_x(\mu)$

#### 气流坐标系与机体坐标系

此两系的Oz轴在相同平面。

- **飞行迎角$\alpha$**： 飞行速度在对称平面内投影与机体轴Oxb的夹角。投影在Oxb下为正迎角。
- **侧滑角$\beta$**: 飞行速度与对称平面之间的夹角。气流速度在对称平面右侧为正。**与偏航角相反。**

α和 β 在很大程度上决定了飞机产生的气动力和气动力矩。

**从机体到气流：$L_{ab} = L_z(\beta)L_y(-\alpha)$**

**从气流到机体：$L_{ba} = L_y(\alpha)L_z(-\beta)$**

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghf22t81aj30uw0j2q6d.jpg" alt="image-20200706121322095" style="zoom: 33%;" />

# 飞机质心运动方程

## 一般动坐标系中质心运动方程

$m\frac{d \vec V}{dt} = \vec F$ 只能在惯性系中用（也就是地面坐标系）。但在航迹坐标系中计算飞行性能很方便，故需建立在航迹坐标系中的质心运动方程。（是动坐标系）

动坐标系质心加速度 （在静坐标系下的表示）

$\frac{d\vec V}{dt} = \frac{\delta \vec V}{\delta t} + \vec \omega \times \vec V$

左边：地面看到的质心绝对加速度 右边：第一项为动系中观察的质心加速度。第二项为角速度引起的加速度。

$\frac{\delta \vec V}{\delta t} = \frac{dV_x}{dt}\vec i+\frac{dV_y}{dt}\vec j+\frac{dV_z}{dt}\vec k$

$\omega \times \vec V = ...$

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghfrocc3vj30x00lygqx.jpg" alt="image-20200706123801358" style="zoom:40%;" />

## 航迹坐标系中质心动力学方程

**该坐标系适用于飞行性能的计算**

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghfvclgbxj30wa0haju7.jpg" alt="image-20200706124136063" style="zoom:50%;" />

上式用角速度转换公式更加好：

$$ \omega_k = L_{rotate}(\phi = 0, \theta = \dot \gamma, \psi = \dot \chi) \left[ \begin{matrix} 0 \\ \dot \gamma \\ \dot \chi\end{matrix} \right]$$

$\vec \omega$ 的含义: 航迹坐标系**相对于惯性坐标系的角速度在航迹坐标系下的投影。**

- 发动机推力：<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghg77g488j30um076757.jpg" alt="image-20200706125300290" style="zoom:50%;" />

- 空气动力：<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghg7fy2ecj30q4084js1.jpg" alt="image-20200706125314650" style="zoom:50%;" />

- 重力： <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghg8cl3d3j30ik06odg5.jpg" alt="image-20200706125405677" style="zoom:50%;" />

质心运动方程：**最后是在航迹坐标系下写的** 三个方向：速度方向，侧向，垂直方向

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghg8uw8l8j30xi0aa3zy.jpg" alt="image-20200706125432445" style="zoom:50%;" />

总体思路：尝试在地面坐标系列出所有的量建立动力学方程，然后转换到动坐标系。

## 飞机质心运动学方程

速度由航迹坐标系转换到地面坐标系:<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghkd2sr3wj30du06q74e.jpg" alt="image-20200706151702313" style="zoom:33%;" />

标量形式：<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghkdpaag8j30hi0aa3z2.jpg" alt="image-20200706151738817" style="zoom:33%;" />可用来确定飞行轨迹

## 质心在铅垂平面内的运动方程

运动特征:飞机对称面与质心运动轨迹处于同 一铅垂面，即飞机**无倾斜、无侧滑。**

### 动力学方程 （俯冲，跃升和筋斗性能计算）

二自由度，不计质量变化

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghkgbi2kzj30us0eojui.jpg" alt="image-20200706152007939" style="zoom: 50%;" />

#### 直线飞行(直线上升、下降等)

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghkl75l06j30ui06gdge.jpg" alt="image-20200706152251275" style="zoom:50%;" />

#### 等速直线飞行(定常上升、定常下滑等)

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghklb334kj30u605uq3j.jpg" alt="image-20200706152419976" style="zoom:50%;" />

#### 水平直线飞行(平飞加减速等)

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghkl5z5waj30ls07yt8z.jpg" alt="image-20200706152331924" style="zoom:50%;" /> $\alpha$应该也是0

#### 等速水平直线飞行(等速直线平飞等)

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghkl83p4dj30t6068gly.jpg" alt="image-20200706152438704" style="zoom:50%;" />

### 运动学方程(铅垂平面飞行轨迹计算)

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghkm1po97j30ik0es0tm.jpg" alt="image-20200706152534632" style="zoom:50%;" />

## 质心在水平面内的运动方程

运动特征:飞机质心运动轨迹始终**平行于海平面。**

### 动力学方程(水平转弯和盘旋性能计算)

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghknj5865j30v60c6gn5.jpg" alt="image-20200706152703412" style="zoom:50%;" />

第三式表示飞机法向力始终平衡，即质 心在水平面内运动。

#### 无侧滑盘旋飞行

$\beta = 0, C = 0$, <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghl33v8u1j30gq08s0tl.jpg" alt="image-20200706154146308" style="zoom:33%;" />

#### 无侧滑等速盘旋飞行

$\beta = 0, C = 0, dV/dt = 0$, <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghl33dhkvj30gw0bcdgt.jpg" alt="image-20200706154156017" style="zoom:33%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghl3l6skgj30vc08yab9.jpg" alt="image-20200706154226008" style="zoom: 33%;" />

### 运动学方程(水平面飞行轨迹计算)

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghl491rw9j30xw0940tp.jpg" alt="image-20200706154306844" style="zoom:40%;" />

# 小结

- 气动特性参数及其随飞行状态和构型参数 的变化趋势
- 喷气式发动机性能参数以及其高度特性、 速度特性、转速特性、特定油门状态
- 常用坐标系的定义;坐标系间的夹角和相互转换
- 飞机质心在铅垂平面内和水平面的运动方程及其特殊运动状态下的简化

# 习题

1. **研究飞行器性能和飞行轨迹特性时，将飞行器视作可控质点来处理的基本前提是什么？**

   作用在飞行器上的力矩始终保持平衡。

2. **飞行器的最大允许升力系数主要受哪些因素的限制？**

   - 失速的限制，即最大允许升力系数CL.a，比失速升力系数CL.s小一些。此方面限制最大允许升力系数的主要因素有：高度、马赫数、飞行器的气动外形。
   - 操纵的限制，保持俯仰平衡所需的舵面极限偏角的限制。

3. **说明零升阻力系数CD0、升致阻力系数因子** A 随马赫数 Ma 的变化规律。**

   未完待续