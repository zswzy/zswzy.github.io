---
layout:     post
title:      第二章 飞机的飞行性能 
subtitle:   
date:       2020-07-06
author:     Zeyuan
header-img: img/767_sunset_takeoff.jpg
catalog: true
tags:
    - 航空飞行器飞行动力学
---
- 掌握飞机基本飞行性能(平飞、上 升、下滑、续航、起降)的性能指标

- 掌握基本飞行性能的工程计算原理和方法

- 典型飞行过程(如定直平飞、起降)的操纵原理

  

目录

{:toc}
# 第二章 飞机的飞行性能 

**飞行性能**： 飞机最基本的一些定 常或非定常的直线运动的性能。可将飞机视 为一个可控质点**,** 飞行性能包括平飞、上升下 滑、续航和起落四个方面的性能。

**定常直线运动：** 指运动参数不随时间而变化的运动。当运动 参数变化缓慢时，则称之为“准定常”运动。 定常运动:平飞、续航(基本性能)  非定常运动:上升、下滑、起落(速度变化较大)

**主要性能指标：**

- 平飞: 最大(最小)平飞速度;
- 上升:上升角、上升率、静升限、上升时间和距离;
- 下滑:下滑角、下滑时间和距离;
- 续航:航程(飞得多远?)、航时(飞得多久?)
- 起飞:起飞时间和距离、离地速度
- 着陆:着陆时间和距离、进场和接地速度

# 平飞性能

## 定常平飞的运动方程

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghp6arg94j30wi05474l.jpg" alt="image-20200706180329196" style="zoom:50%;" />

### 定常平飞需用推力及其计算方法

定义:指飞机在某一高度以一定速度进 行等速直线平飞所需的发动机推力,它随 飞机的飞行速度和高度的变化而变化。

1. 计算W重力
2. 给定H，得到大气密度，马赫数（根据速度）等
3. 根据速度，计算升力系数$C_L = \frac{2W}{\rho V^2 S} = \frac{2W}{\rho (aM)^2 S}$, 然后根据极曲线得到C~D~。 $K = \frac{C_L}{C_D} \Rightarrow thrust T_R = D = \frac{W}{K}$

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghpg4wixkj30y409ignj.jpg" alt="image-20200706181254746" style="zoom:50%;" />

### 平飞需用推力随飞行速度的变化规律

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghukdejm1j30vc0gmwh3.jpg" alt="image-20200706210959985" style="zoom:50%;" />

**飞行速度增大，零升阻力增大;诱导阻力减小**（A大致与M成正比）

- M<Mcr (亚音速范围) 呈”凹勺” 形变化!
  - A, C~D0~基本不变，D0～ M^2，Di～ 1/M^2. M = Mopt， D0 = Di， TR最小，K = Kmax
- Mlj <M<1.2~1.3(跨音速范围) 小展弦比、大后 掠角、薄翼型和 细长机身
  - CD0大幅增加，A增加～M， TR增大。此时，波阻为主(音障)，应采用低波阻构形。
- M > 1.2  ̅ 1.3(超音速范围)
  - Di可忽略，CD0～1/$\sqrt{M^2-1}$，D0～M. *T*R 与M等比例增加, 但较跨音速区缓慢.

平飞需用推力呈勺形，亚声段有一个最小推力速度;飞行速度大于最小推力速度后， 阻力单调增大。

最小推力即位升阻比最大点，D0 = Di，Kmax 有利状态（巡航）

### 平飞需用推力随飞行高度的变化规律

#### 有利飞行马赫数

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghuv1h14ij30xc0eqact.jpg" alt="image-20200706211959486" style="zoom:40%;" />

H增大，密度减小，D0减小Di增大。D0与Di的交点右移。**即在高空时，有利飞行马赫数要增大。**（CD0和CDi与高度关系？）

#### 最小平飞需用推力

亚音速范围 , Kmax =const ⇒ T = W/K = const(不随高度变化) Rmin max

一定H上可能出现Mopt >Mcr ,波阻使K~max~ ↓ ⇒T~R,min~↑

飞行高度增加，飞行速度应增大，最小平飞需用推力也增大,曲线稍微向 上移动。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghxmnguq2j30dg0bcmxa.jpg" alt="image-20200706225559087" style="zoom:33%;" />

高度增加，曲线变平缓<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghy0n2209j30wi0ikjv3.jpg" alt="image-20200706230925220" style="zoom:50%;" />

**飞机的飞行高度越大，有利飞行马赫数增大，民用运输机一般都在近升限高度 巡航飞行，经济性好;**

## 最大平飞速度

### 定常平飞基本关系

$L = W \Rightarrow $ 调整迎角 $\alpha \Leftarrow \alpha_{a,min} \leq \alpha \leq \alpha_{a,max}$

发动机可用推力$T_a = D \Rightarrow $ 调整转速 $n \Leftarrow n_{idle} \leq n \leq n_{max}$(加力/不加力)

发动机可用推力由某H、V 平飞重量、构形确定

-> 性能指标 -> V~max~, V~min~, H~max~, 平飞包线 -> 简单推力法求解

### 最大平飞速度Vmax ( Mmax )的定义和确定

在某高度能定直平飞的最大速度，称该高度最大平飞速度。

各高度Vmax最大者称为飞机的最大平飞速度。

### 图解确定Vmax：

满油门(最大状态、部分加力、 全加力)的Ta ~ M与TR ~M曲 线的右交点。

超声速飞机加力状态Vmax增大很多。<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghyg8f1igj30da0d6q3w.jpg" alt="image-20200706232422104" style="zoom:40%;" /> **注意该曲线的本质为推力 = 阻力， T= D**，可用的推力和马赫数也有关，推力越大马赫数越大。

### Vmax ～ H关系

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghyl15aebj30tc0cmac1.jpg" alt="image-20200706232903033" style="zoom:50%;" />

H增加，D(TR )曲线右移且变平坦， Ta 曲线下移

### 最大平飞速度 公式

$ V_{max} = \sqrt{\frac{2T_a}{C_D\rho S}}$ , ρ T~a~ C~D~ 都随高度变化

- 平流层中，音速不随高度而变化，因此同一速度 对应的 *M* 数不随高度变化，波阻系数就不随高度的增加而降低。另外由于 ρ 已经减小很多，为了保持 平飞需增加迎角，因而*C* ~D~增大。所以高度增加时*C*~D~ρ的减小变得缓慢，而此时发动机的推力剧烈下降，从而使得Vmax随高度的增加而减小。

- 对于跨音速飞机: 可用推力随高度的增加而降低，波阻系数增大，这样组合参数$T/C_D\rho$  随高度的增加而降低，因而随*V* max高度的增加一直减小;

- 对于超音速飞机:通常在对流层内 *V* max 随高度的增加而增大，在平流层中则随高度的增加而减小。原因:对流层中，音速降低，使同一速度所对应的*M* 数增大，在超音速区时，波阻系数随着 *M* 数的增大而减小，这样C~D~就减小。因此C~D~ρ的减小起主导作用，Vmax随高度的增加而增大。

其实这里说的很不严谨，没有指出三种飞机的本质区别。第一，不同类型飞机发动机不同，亚音速和跨音速的推力随高度降低明显，超音速较为不明显。第二，超音速的巡航速度范围与前两种有本质区别，阻力主要来源于零升阻力（随速度变化不大，且随高度增加减小）和波阻（随速度增加减小）。第三，跨音速飞机为何在11km以下Vmax变化不大？可能是因为C~D~增大，$\rho$ 减小，T减小，综合考虑变化不大。而有相同机理的亚音速飞机，CD变化不大，$\rho$减小更为主导。

另一种写法：$ V_{max} = \sqrt{\frac{2W}{C_L\rho S}}$ 但是这里的Cl并非最大值，也不一定是最小值，所以比较难确定。

## 最小平飞速度

在某高度能定直平飞的最小速度，称该高度最小 平飞速度。

### Vmin的确定

油门T~a~～M与T~R~ ～ M曲线的左交点，满足T~a~ = D => V~min,T~ (发动机推力限制)

升力系数的限制：L=W => V减小，CL增大 （同一高度）

C~L~ 的上限为C~L,a~，所以$V_{min} = V_{min,a} = \sqrt{\frac{2W}{C_{L,a}\rho S}} $ 

V~min~ = max{V~min,a~, V~min,T~} 受到最大允许升力系数和发动机推力的双重限制

### Vmin ～ H关系

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggijjfqaaij30g20aqdgh.jpg" alt="image-20200707113401516" style="zoom:33%;" /> H增加，TR右移，Ta下移，V~min,T~ 增加。密度下降，V~min,a~ 增加。 

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggijl1enh0j30ew0bcgma.jpg" alt="image-20200707113536100" style="zoom:33%;" /> H增加，Vmin增加，Mmin增加。

**低空受V~min,a~约束，高空受V~min,T~约束。**

**这些曲线的趋势都是实验得出来的？？**

起降的时候，构型变化大，C~L,a~ 大大增加，由最大允许升力系数得出的最小速度应该非常容易达到，但必须有一定的推力，因此是推力限制（不然克服不了空气阻力）？

### 确定Vmin的步骤

1. 在一定的高度上，根据$C_{L,R(request)} = \frac{2W}{\rho S a^2 M^2}$绘制 C~L,R~ ～M曲线，它和已知的C~L,a~曲线的绞线就是M~min,a~ (升力限制) （我们可以把CL,a理解为一系列CL~M曲线的上界）

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggijtbtcpxj30dg0g2dgt.jpg" alt="image-20200707114335927" style="zoom:50%;" />

2. 该高度下满油门T~a~ ～M曲线和T~R~～M曲线的左交点为M~min,T~
3. 取M~min~ = max(M~min,T~, M~min,a~)

## 平飞速度范围

### 理论飞行包线

在H~M(V)平面上， 定常平飞的M~max~~H与 M~min~~H线所勾划出的封闭曲线;

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggl3ev4zzaj30fk0bodg5.jpg" alt="image-20200707114738887" style="zoom:50%;" /> **其内飞机可定直平飞/等速爬升/加减速飞行等。其上可定直平飞。**

### 允许飞行包线

考虑实际使用限 制后得到的飞行包线。随H增加，包线的 速度范围收缩，直 至某高度收缩为一 点，**此为Hmax。**<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggik4jajzrj30gw0g8jtz.jpg" alt="image-20200707115421413" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggik56846dj30p20g8gnk.jpg" alt="image-20200707115458406" style="zoom:40%;" />

# 上升、下滑性能



<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gghg8uw8l8j30xi0aa3zy.jpg" alt="image-20200707115421413" style="zoom:50%;" />

## 定常直线上升运动方程

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggik8s6878j30xk0ae40a.jpg" alt="image-20200707115827293" style="zoom:40%;" />

这里方程的第二式其实是L = Wcosγ , γ为什么用小角度？？完全没道理。

飞机的上升一定是推力大于平飞时的气动阻力(相等时即为平飞运动)，飞机开始加速，当速度大到一定程度(大于最大平飞速度)，气动升力就大于重力，飞机就进入上升飞行。



## 定常直线上升运动性能

### 上升角 γ 最大上升角γ~max~

$sin\gamma = \frac{T_a-T_R}{W} =\frac {\Delta T}{W} \Rightarrow \gamma_{max} = sin^{-1}\frac{\Delta T_{max}}{W}$

**这是给定H,构形,W下的最大上升角**，**上升角的大小取决于发动机的剩余推力**

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggiln699g5j30o8024jrq.jpg" alt="image-20200707124638309" style="zoom:40%;" /> <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggl3eufws6j30c40b63z0.jpg" alt="image-20200707124649491" style="zoom:50%;" />

### 上升率Vv和最大上升率Vvmax

上升率V~v~:飞机在单位时间上升的高度。$V_v = \frac{dH}{dt}$

最大上升率V~vmax~ 

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggiolxu1vej30a80hamxx.jpg" alt="image-20200707142926054" style="zoom:40%;" />

给定高度、构形和W下可能 的最大上升率，**它取决于发动机的剩余功率。**

相应速度为快升速度 V~qc~(M~qc~)。

**注意，最陡上升速度是上升角最大，最大上升率是上升最快（但可能会用更远的距离），对应最短上升时间。**

上升率表明飞机空战获得高度的能力;由于剩余推力与飞行速度和高度有关， 故只能用图解法求解。p43

![image-20200707144618172](https://tva1.sinaimg.cn/large/007S8ZIlgy1ggip3x6o7hj30n204cjsc.jpg)

![image-20200707144636260](https://tva1.sinaimg.cn/large/007S8ZIlgy1ggip3y0px3j30ok12mn7t.jpg)

![image-20200707144645918](https://tva1.sinaimg.cn/large/007S8ZIlgy1ggip3vpamlj30n204cjsc.jpg)

几个典型飞行速度的比较：

| 有利速度 | 升阻比最大的飞行速度                                         |
| -------- | ------------------------------------------------------------ |
| 陡升速度 | 剩余推力最大的飞行速度                                       |
| 快升速度 | 剩余功率(速度与剩余推力乘积） 最大的飞行速度（民机上升段飞行速度） 对应最短上升时间 |

### 理论静升限Hmax.a和实用静升限Hmax.s

H~max,a~ : 特定重量，构型，发动机加满油门（最大，加力，全加力）时，飞机能够定直平飞的最大高度。此时V~Vmax~ = 0

H~max,s~ : 对应飞机V~Vmax~ = 5m/s（超声速飞机）或者0.5m/s（亚音速飞机）的飞行高度。

### 最短上升时间 $t_{c,min}$

保持最快速度V~qc~ 以V~Vmax~ 上升，所需时间最短。飞机的快升速度Vqc随飞行高度增加而增大。意味着有加速度存在。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggipcle7wxj30sw08o0ty.jpg" alt="image-20200707145505889" style="zoom:50%;" />

### 上升所经过的水平距离Rc

从某一起始高度H1 ，上升至某一预定高度H2 ，所经过的水平距离。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggipezcr6uj30ts07it9f.jpg" alt="image-20200707145724182" style="zoom:50%;" />

注意，$\gamma = arctan\frac{\Delta T}{W}$, $\Delta T$随高度改变，所以$\gamma$也是飞行高度的函数。故水平距离只能用数值或 图解积分法;

## 非定常直线上升运动性能dV/dt != 0

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggipmmms2vj30ee066aac.jpg" alt="image-20200707150445650" style="zoom:50%;" />

 ### 上升率

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggipx7ylo1j31330u0jx2.jpg" alt="image-20200707151453860" style="zoom:50%;" />

非定常上升上升率$V_v = V_v^* \times \chi$, 第二项是在定常上升率基础上的修正系数。显然，如果加速上升，$\chi < 1$, 减速上升，$\chi >1$, 上升率更大。

（2.23）写成： <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggipzptyz3j30vq078dhj.jpg" alt="image-20200707151719285" style="zoom:40%;" />

- 加速上升时，发动机剩余功率部分转化为动能，实际上升率小于定常上升率;
- 减速上升时，发动机剩余功率部分转化为位能，实际上升率大于定常上升率;

### 上升时间

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggiq8t11joj30u40jo76t.jpg" alt="image-20200707152601292" style="zoom:50%;" />

### 最快上升轨迹的定义和计算

指从某一速度、高度上升到另一速度和高度的最快轨迹;

若上升过程中，均以 $V_{Vmax}^*$上升，则飞机上升最快;

分别绘出以高度和马赫数为函数的等能量高度曲线，和$V_{Vmax}^*$曲线族，两族曲线的**切点**所形成的轨迹即为最快上升轨迹。

## 定常下滑运动性能

飞机的飞行轨迹向下倾斜，但倾斜角不大的 直线飞行。如滑翔、无动力飞行，发动机慢 车，Ta≈0，定直下滑,倾斜角< 0。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggirsyraabj30xm0d4act.jpg" alt="image-20200707162000150" style="zoom:50%;" />

**滑翔角由极曲线决定，与飞机重量无关。 可通过滑翔飞行测量气动特 性参数K;**

**滑翔机: K较大(10~40)， ε不大，γ不大**

### 下滑距离 Rd

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggirz8gv92j30pk036aa6.jpg" alt="image-20200707162603105" style="zoom:50%;" />

亚音速飞机（极曲线基本不随马赫数变）

### 下滑速度Vd和下滑率Vv

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggis7dkh65j30te0883zs.jpg" alt="image-20200707163346342" style="zoom:50%;" />

### 下滑时间 $t_d$

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggiscdbginj30am02sq2v.jpg" alt="image-20200707163841053" style="zoom:50%;" />

注意，在最佳状态即K~max~, $C_{Lopt} = \sqrt {\frac{C_{D0}}{A}}, C_D = 2C_{D0} \Rightarrow C_R = \sqrt {4C_{D0}^2+\frac{C_{D0}}{A}}$, 二C~D0~ 取决于构型（和外形）和速度（Re），但在亚音速区基本不变。

下滑时间：$t_d = \frac{HK}{\sqrt{\frac{2W}{\sqrt{4C_{D0}^2+\frac{C_{D0}}{A}}\rho S}} cos\gamma}$, 

主要影响因子：

-  K（取决于飞机，马赫数（大马赫数变化大）），与$\gamma$ 同理
- C~D0~, 取决于构型和速度，主要在大马赫数变化大。零升阻力越大td越大。（下降速度慢）
- W重力，重力越大td越小下降越快
- 空气密度。密度越大相当于阻力增大，td越大。（下降速度慢）

# 续航性能

航程反映了民机的经济效益。航时反映飞的多久，预警机，侦察机指标之一。

准定常直线飞行，燃油逐渐消耗。

总航程中，巡航段约占90%

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggj5be2cr3j30w80migo5.jpg" alt="image-20200708000727276" style="zoom:50%;" />

## 航程和航时的基本关系式

### 航程D

飞机携载荷在平静大气中沿预定航向耗尽其可用燃油所经过的水平距离

D = D~el~ + D~cr~ + D~de~

### 航时t

飞机携载荷在平静大气中耗尽其可用燃油所能持续飞机的时间

t = t~el~ + t~cr~ + t~de~

续航性能取决于可用燃 油量和燃油消耗速度

### 可用燃油量和巡航段燃油量

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggj5e0ag5sj30qg0fsgoh.jpg" alt="image-20200708001002077" style="zoom:50%;" />

### 燃油消耗速度

#### 小时耗油量

飞机**飞行1小时**发动机所消耗的燃油质量(kg/h)。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggj5fb350kj30mu05yq3y.jpg" alt="image-20200708001116496" style="zoom:33%;" />

注意，Ti是在试车台的推力。实际上的推力$T_a = \eta i T_i$

#### 千米耗油量

飞机**相对于地面飞行1千米**所消耗的燃油质量(kg/km)

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggj5g75ohjj30oo04cwez.jpg" alt="image-20200708001202905" style="zoom:40%;" />

### 巡航段航程和航时的基本公式

设无风，V空速=地速。飞机质量变化只来源于耗油。dT时间内：

燃油消耗 $dm = -dQ_f = -c_{f,t}dt $

航时 $\Rightarrow dt = -\frac{dQ_f}{c_{f,t}} = -\frac{dW}{gc_{f,t}}$

航程 $dR  = Vdt = -\frac{VdW}{gc_{f,t}} = -\frac{dW}{gc_{f,R}}$

**飞机质量的变化(耗油量)除于小时耗油率就为航 时,若除于千米耗油量就为航程;**

巡航阶段重量从W1 变化到W2 （W1> W2)

则<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjoruvkwjj30vy07eabi.jpg" alt="image-20200708112023076" style="zoom:40%;" />

**为获得最大航程或最久航时,必须合适地选择飞机 的飞行状态和发动机工作状态;**

$c_{f,t} = c_fiT_i = \frac{c_fT_a}{\eta} = \frac{c_fW}{\eta K}$, $c_{f,r} = \frac{c_{f,t}}{V} = \frac{C_fT_a}{\eta V} = \frac{c_fW}{\eta V K}$

$\Rightarrow t_{cr}=-\int_{W_1}^{W_2} \frac{dW}{gc_{f,t}} = \int_{W_2}^{W_1} \frac{\eta K}{gc_f} \frac{dW}{W}$ **K与飞机气动特性有关。K越小航时越小。**

$\Rightarrow R_{cr} = -\int_{W_1}^{W_2} \frac{dW}{gc_{f,R}} = \int_{W_2}^{W_1} \frac{\eta V K}{gc_f} \frac{dW}{W}$ 与V，K有关。VK越大，航程越大。

上述航程和航时的计算,不能用解析法,通常要用 数值积分或图解积分法;

具体的航程和航时的计算需依据各种给定的飞行 任务,如侦察机应按预定的高度和速度执行任务;歼击机需按轰炸机的巡航高度和速度执行护航任务等。

## 等高等速巡航时的航程和航时

### 飞行特点

燃油持续消耗，飞机重量W减小，C~L~减小（迎角减小），C~D~减小（转速减小），飞行中需要逐渐推杆收油门

### 耗油特点

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjpigb7egj30qw05w0uj.jpg" alt="image-20200708114616610" style="zoom:50%;" />

可选最佳**V**、**H**组合使一定构形、重量下的耗油最少

### 图解积分法求解

基础方程：<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjpjvf2y5j30nq06wjs9.jpg" alt="image-20200708114739556" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjpk4ocu4j30u00au3z9.jpg" alt="image-20200708114755125" style="zoom:50%;" />

P60

![image-20200708121232080](https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjqacuobfj30qa0gcq8x.jpg)

![image-20200708121247101](https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjqabescwj30qe0vqti7.jpg)

![image-20200708121300276](https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjqacdgr4j30qe0vqti7.jpg)

## 久航速度和远航速度

**对应于(C~f,t~)~min~和（C~f,R~)~min~的飞行速度，分别称为某高度上的久航速度V~t,max~和远航速度V~R,max~** 

### 久航速度

给定H，不计cf，$\eta$随速度变化

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjtij4nbdj30xy07a0ty.jpg" alt="image-20200708140445439" style="zoom:50%;" />

**有利速度，最大升阻比**

### 远航速度

给定H，不计cf，$\eta$随速度变化

![image-20200708141337995](https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjts6qcwej30xc0h20v0.jpg)

**最大巡航效率速度(升阻 比与飞行速度的乘积最大)状态，民用飞机 (要求航程最远)的气动效率指标;**

**远航速度>久航速度。**

## 久航高度和远航高度

飞行高度不同，对应的tmax和Rmax也不同。在飞行包线内，等高等速飞行的**最大可能航程和航时称为最大航程**R~max，max~和最久航时t~max，max~。对应的飞行高度为远航高度H~R,max~和久航高度H~t,max~。

### 工程计算步骤

1. 给定一系列的飞行高度,计算每一高度的 Rmax和tmax
2. 画出Rmax - H 和tmax - H 的曲线<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjtr7lphlj30ay09i74w.jpg" alt="image-20200708141304617" style="zoom:60%;" />
3. 取对应最大值，对应久航/远航高度，最大航程/航时。

对于某些超声速飞机,由于 对应跨声速和超声速区的远 航速度飞行时,其千米耗油量 变化较大,如右图所示。<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjy9wntmcj30d60bat9b.jpg" alt="image-20200708164929154" style="zoom:50%;" />

要增大巡航段的航程，在某

跨声速支 超声速支

高度 H 以下，应以跨声速远航速度飞行，当超过该高度后，应采用超声速远航速度飞行。（与超声速飞机在超声速段的气动特性和发动机特性相关）

**低空以高亚声速飞行，高空以超声速飞行可获得最大航程**

## 飞机最佳续航性能概念

由于飞机巡航状态的飞行高度和飞行速度 选定后始终不变，因此，发动机的转速和飞 机升阻比等都将随飞机重量的变化而变化， 以满足飞机巡航飞行时的平衡条件。即其经 济效益受到限制，不能始终处于最佳状态。在巡航过程中，如果允许巡航飞行中的飞 行高度随重量而变化，同时选择最有利的飞 行速度和最有利的发动机工作状态，并且在 巡航过程中始终保持这种有利状态，则飞机 可获得更大的航程和航时，即最佳续航性能。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjybz6621j30v60l6403.jpg" alt="image-20200708165127734" style="zoom:50%;" />

## 最大活动半径

飞机由机场出发，飞到目标上空完成 一定任务后，再返回原机场所能达到的最远 距离 。它标志着飞机远航作战的能力。 

**不一定等于航程的一半**。飞机达到目标上空时 要执行任务(如空战、空投等），消耗部分燃油和质量，飞机重量减轻。<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjydrewzoj30ge0auwf0.jpg" alt="image-20200708165311677" style="zoom:50%;" />

## 风对续航性能的影响

作用在飞机上的空气动力和 推力只与空速有关，飞机的航迹只与地速有关。

- 风对飞机的**航时没有影响**
- **顺风飞机航程增大，反之减小**
- 风对现代飞机活动半径影响较小，且与风方向无关。

## 增加续航性能的途径

- 提高气动效率，增加K~max~ （气动设计）
- 减轻飞机结构重量 （结构设计）
- 增加可用燃油（合理设计内部储油空间，副油箱（但增加W和阻力），空中加油）
- 根据任务需要，选用合适的发动机，使推力要求匹配，且耗油率尽量小
- 设计最佳航路方案，包括考虑非标准使用条件的影响，如风
  - 风只会对航程有影响。

## 小结

| 续航性能指标   | R，t                                                     |
| -------------- | -------------------------------------------------------- |
| 决定因素       | K, H, V, C~f,R~, C~f,t~ 构型，飞机状态，动力特性         |
| 计算问题       | 给定飞机状态的巡航参数计算，确定给定高度的久航、远航速度 |
| 超声速飞机     | 可能会出现两个远航速度                                   |
| 增加R，t的途径 | 增加KV，增加K，减小C~f,R~,  减小C~f,t~                   |

# 	起落性能

特点：**非定常（速度改变快），安全裕度小，易失速，环境复杂（风切变，能见度，雨雪等）**

影响飞机使用经济性：滑跑距离决定机场的造价，离地（接地）速度决定起落架刚度，刹车等等

主要性能指标：

- 起飞滑跑距离，起飞距离，起飞时间，离地速度
- 着陆距离，滑跑距离，着陆时间，接地速度
- 距离越短，时间越少，离地/接地速度越低性能越好

## 运动及受力特点：

- 速度改变快，非定常运动
- 滑跑时：地面对飞机的支持力和摩擦力
- 地面效应：地面运动及近地飞行时的额外的气动力（升力系数增加，诱导阻力减小）
- 构型变化：起落架，襟翼等增升装置，减速板等

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjysv1m33j30y40p8wiz.jpg" alt="image-20200708170723864" style="zoom:40%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjysw4i3qj30yy0oin1j.jpg" alt="image-20200708170734302" style="zoom:40%;" />

## 起飞性能

起飞过程：飞机从起飞线开始滑跑，离地并上升到 机场上空的**安全高度**（机场周围障碍物决定。常用：25m，15m，10.7m，与飞机类型有关）

### 前三点飞机的起飞过程

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggjywn6zscj30xm0l8jww.jpg" alt="image-20200708171117912" style="zoom:50%;" />

**与空中飞行不同。需要放下襟翼，起飞通常5-8度，降落20-25 看不同飞机的操作手册。注意有地效存在。**

计算中，地面过程看作匀加速，上升过程用能量守恒计算。

### 地面滑跑距离d1和时间t1的计算

滑跑过程中的两主轮着地，假设推力与地面平行。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggk1y4i3uwj30wq0ao75j.jpg" alt="image-20200708185632797" style="zoom:50%;" />

 摩擦系数 f 干水泥：0.02-0.04 湿水泥：0.03-0.05 干硬土草地：0.07-0.10

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggl3ex4yhuj30jo0awt9y.jpg" alt="image-20200708185842167" style="zoom:50%;" />

因被积函数随运动速度而变，故只能用数值积分或图解积分求解。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggktma8accj30x408awfw.jpg" alt="image-20200709105352172" style="zoom:50%;" />

### 起飞滑跑性能的工程估算

假设匀加速，（但显然不是）

$\frac{dV}{dt} = a_{av} = const \Rightarrow \frac{W}{g}a_{av} = T_{av}-(D+F)_{av}$

T~av~ 由T~a~ - V	曲线取平均值，可取0.9T0 （T0是V=0时推力，起飞状态）

$(D+F)_{av} = \frac{1}{2}[(D+F)_{V=0} + (D+F)_{V = V_{lo}}] = \frac{1}{2}(fW+\frac{W}{K_{lo}}) = \frac{1}{2}W(f+\frac{1}{K_{lo}}) =(\Delta) Wf'$

定义 $f' = \frac{1}{2}(f+\frac{1}{K_{lo}})$

$\Rightarrow a_{av} = (\frac{T_{av}}{W}-f')g$

Klo:离地升阻比，由起飞极曲线确定

所以有

$t_1 = \frac{V_{lo}}{a_{av}} = \frac{1}{g}\frac{V_{lo}}{g(T_{av}/W)-f'}$

$d_1 = \frac{V^2_{lo}}{2a_{av}}=\frac{1}{2g}\frac{V^2_{lo}}{T_{av}/W-f'}$

对于T/W和W/S均较大的高速飞机， 可以忽略气动力的影响，进而推导出更简单的估算公式。

### 离地速度的确定

离地条件：<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggl3ewaognj30l2060wf9.jpg" alt="image-20200709115144843" style="zoom:40%;" /> <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggkvav6yxrj308m04kmx6.jpg" alt="image-20200709115211757" style="zoom:50%;" />

(略去推力矢量 的垂直分量) C~L,lo~: 离地升力系数，据 飞机近地面、起飞 襟翼构形的升力特 性和αlo确定。

限制条件：

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggkvc6zuhej30sc052ta6.jpg" alt="image-20200709115314167" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggkvc64ju6j30t007u0uf.jpg" alt="image-20200709115325827" style="zoom:50%;" />

### 空中段水平距离d2和时间t2的计算

指飞机离地开始加速上升至安全高度所经过的水平距离和时间。

**有地效到无地效，起落架收起， 升阻特性复杂。**

**能量法近似计算：**

假设1. $\gamma -> 0, cos\gamma \approx a$. 2. $\Delta T = T_a - D = \Delta T_{av}$

$\Rightarrow \frac{W}{2g}(V_H^2 - V_{lo}^2 )+ H_{H}W = \Delta T_{av}d_2$, 其中，$V_h = 1.3V_{lo}$

**空中段水平距离和时间：**

$d_2 = \frac{W}{\Delta T_{av}}(\frac{V_H^2-V_{lo}^2}{2g}+H), t_2 = \frac{d_2}{V_{av}}$

**$\Delta T_{av}, V_{av}$ 的确定方法：**取平均值 $\Delta T_{av} = \frac{1}{2}[(T-D)_{lo} + (T-D)_{V=V_H}], V_{av} = \frac{1}{2}(V_H+V_{lo})$

## 着陆性能

### 着陆过程

飞机从安全高度(15或25m处)下滑过渡到地面滑跑，直至完全停止运动的整个减速过程。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggkyd43ut2j30w20mcagn.jpg" alt="image-20200709133805347" style="zoom:50%;" />

### 进场速度和接地速度的确定

- **进场速度V~H~:**飞机下滑至安全高度**(25m)**处的瞬时速度。一般取C~L,H~ = (0.6 ~ 0.7 )C~L,td~ =>V~H~ = (1.2 ~ 1.3) V~td~
- **接地速度V~td~:**飞机主轮开始接触地面瞬间的速度(升力开始不能平衡重量)。$V_{td} = k_1 \sqrt{\frac{2W}{\rho S C_{L,td}}}$, 其中k~1~ 速度修正系数$C_{L,td} = min(C_{Lsh}, C_{L,pt})$ （抖升系数，护尾系数）计及地效、着陆形态。 

### 空中段水平距离d**3**和时间t**3**的计算

能量近似法

假设 1. $\gamma ->0, cos\gamma \approx 1$ 2. T~a~ 约为0. 3. D变化不大。

假设来源： 一般着陆形态飞机仰角5-10度（boeing），某些可能0度或0-5度。下滑角3度，$\gamma$ 应为3度，差不多是0. Ta在idle左右，但绝对会有力矩输出。

能量守恒: $\frac{W}{2g}V_H^2 + WH = \frac{W}{2g}V_{td}^2 + D_{av}d_3$
$$
\Rightarrow \left\{
\begin{array}{}
d_3 = \frac{W}{D_{av}}(\frac{V_H^2-V_{td}^2}{2g}+H) \approx K_{av}(\frac{V_H^2-V_{td}^2}{2g}+H)\\
t_3= \frac{d_3}{V_{av}} = \frac{d_3}{\frac{1}{2}(V_H+V_{av})}
\end{array}


\right .
$$


其中 $K_{av}= \frac{1}{2}(K_H+K_{td})$ 

分析： Kav减小会增加Vtd，减小d3. 但同时d4会增加，而d4刹车距离更加重要，所以要求Vtd越小越好。

### 着陆滑跑距离d4和时间t4的计算

假设：全刹车三点滑跑，匀减速<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggl2p2ggm9j30wu080myu.jpg" alt="image-20200709160800915" style="zoom:50%;" />
$$
\Rightarrow
\left\{ 
\begin{array}{}
t_4 = -\frac{V_{td}}{a_{av}} = \frac{2V_{td}}{g(f+\frac{1}{K_{td}})}\\
d_4 = -\frac{V_{td}^2}{2a_{av}} = \frac{V_{td}^2}{g(f+\frac{1}{K_{td}})}
\end{array} 
\right.
$$
分析：打开襟翼，减速板，升力系数和阻力系数大幅上升，V~td~，K~td~减小，刹车f增大，最后d4小，t4小。

## 起飞滑跑中单发停车的对策

飞机单发停车是继续起飞还是停止起飞，取决于当时飞机的速度和剩余跑道的长度。

### 中断起飞所需距离

指在起飞过程中,一台发动机停车,驾驶员中断起飞, 收油门并放减速机构,飞机从滑跑起点到完全停车所经过 的距离。

第一段：从速度为零加速滑跑至一台发动机停车瞬时速 度 V~ef~所经过的距离;

第二段：从一台发动机停车至驾驶员收油门、放减速装置中断起飞所经过的距离;规范定为**3秒**，飞行速度近似不变;

第三段：收油门，放减速装置至飞机完全停止运动所经过的距离。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggl349kcgwj30tc0eqq57.jpg" alt="image-20200709162040528" style="zoom:50%;" />

K~ef~是V~ef~时候的升阻比。V~ef~越大，所需要的d~at~越长。

### 继续起飞所需距离

指在起飞滑跑过程中,一台发动机停车后继续起飞时，飞机从滑跑起点到上升至安全高度所经过的水平距离。

第一段:所有发动机工作加速滑跑到V~ef~ ，一台 发动机停车，其余发动机工作加速滑跑到 V~lo~ 所经过的距离;

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggl34aej73j30xc0be776.jpg" alt="image-20200709162236173" style="zoom:50%;" />

第二段:从离地速度 开始至安全高度的加速上升距离;可参照起飞空中段的计算公式。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggl34uhkrjj30mc0dgwfn.jpg" alt="image-20200709162311655" style="zoom:50%;" />

### 决策速度和平衡场长

#### 决策速度 V1

多发飞机在起飞滑跑中一临界发动 机失效的某个速度，飞机无论继续起飞还是中断起 飞都需要同样的距离，该速度被定义为决策速度。它是继续起飞所需距离曲线与中断起飞所需距 离曲线相交点所对应的速度。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggl3cskbf8j30mi0doq3z.jpg" alt="image-20200709163045752" style="zoom:40%;" />

临界发动机：Critical engine means the engine whose failure would most adversely affect the performance and handling qualities of an aircraft.

#### 平衡场长 $L_{bf}$

**飞机继续起飞所需的距离等于中断起飞所需距离的场地长度。**<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggl3gulvjxj30pw0eygmw.jpg" alt="image-20200709163441916" style="zoom: 20%;" />

- 当实际场长等于平衡场长：<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggl3jr16r0j30pc0fmjsr.jpg" alt="image-20200709163728362" style="zoom:33%;" />
  - V1停车，可以继续起飞，也可中断起飞
  - 小于V1停车，继续起飞距离小于实际场长，只能中断起飞
  - 大于V1停车，只能继续起飞。
- 当实际场长小于平衡场长（飞机重量增加？）<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggl3k5hhk1j30wg0huacj.jpg" alt="image-20200709163752789" style="zoom:33%;" />
  - 在某一速度范围（图中两竖线之间），飞机继续起飞和中断起飞所需的距离均超出实际场长，危及飞行安全。

- 实际场长大于平衡场长(飞机重量减轻):<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ggl3ldvwmaj30vs0h4q51.jpg" alt="image-20200709163902976" style="zoom:33%;" />
  - 在某一速度范围，飞机继续起飞和中断起飞所需的距离均小于实际场长，但通常中断起飞。

