---

layout:     post
title:      复合式共轴高速直升机飞行控制策略研究
subtitle:   
date:       2021-03-6
author:     Zeyuan
header-img: img/https___blogs-images.forbes.com_lorenthompson_files_2017_09_Raider-1200x801.jpg
catalog: true
tags:
    - 配平策略
	- 优化
---
- 这里是一个目录
{:toc}
Welcome to the Compound-helicopter wiki!

This section will illustrate all information about my personal academic project: Investigation of flight control strategy of the compound coaxial high-speed helicopter. Pages are now under updating...

The helicopter model dimension is based on the Sikorsky X2 demonstrator and XH-59A demonstrator. 

The mathematic model is based on _Thomson, D., “Development of a Generic Helicopter Mathematical Model for Application to Inverse Simulation,” Internal Report No. 9216, Department of Aerospace Engineering, University of Glasgow, UK, 1992._

# Trimming result and analysis

This page illustrates the trimming results and analysis.
# Basic trimming

In basic trimming, we don't consider the propeller and any other redundant control variables. The trimmed variables are:
- $\theta_0$
- $\theta_{diff}$
- $\theta_{1c}$ : longitidunal cyclic pitch
- $\theta_{1s}$ : lateral cyclic pitch
- $\theta$
- $\phi$
- $v_{i1}$
- $v_{i2}$

Eight equations are used, among which 3 are force equilibrium, 3 are moment equilibrium, other 2 are for induced velocity calculation.
The Algorithm used to solve the problem is the Levenberg-Marquardt algorithm. (A variation of gradient descent)

Without the propeller, the CCH is nothing but a classical helicopter. So we can predict that the flight envelope cannot be too large. Although CCH can reach the speed of 150 m/s, considering the mathematical model is the modification based on the conventional helicopter, I finally limit the maximum trimming speed to 130 m/s. Actually, if one continues to trim beyond 130 m/s, the solution is going to be unrealistic, for instance, a cyclic pitch of 90 degrees, implicating that the linear aerodynamic model is not valid, so the solution is also meaningless. 

**Trimmed control variables:**
<img src="https://tva1.sinaimg.cn/large/e6c9d24ely1go7u4ifut1j21g20t0mys.jpg" style="zoom:50%" />

The red dash line is for a speed of 100m/s, which is the maximum speed for classical helicopters. Note that there is a slight decrease of the collective pitch as the speed increases from 0 to 50m/s, due to the forward flight velocity increase the relative speed of the advanced blade.  After 50 m/s, the rotor needs more thrust to provide the X direction forces for forwarding flight. Still, at the maximum speed of 130 m/s, the collective pitch is about 27 degrees. Technically speaking, linear aerodynamic modeling is not valid. Here 100 m/s limitation is like a model separation point, before which the model provides a high fidelity. We can find out that in the latter section after we add the propeller, the solution can be limited to a well-considered range where the linearization method works.

Lateral cyclic pitch is in a small range of variation, however, longitudinal cyclic pitch gradually increases to resist the longitudinal flapping and forces the rotor plane to turn forward to provide forwarding flight power.

The value of differential cyclic pitch mainly due to the different induced velocities of the upper rotor and lower rotor. At high speed, differential pitch converges to 0 so the corresponding induced velocity tends to be the same. This can be verified by the figure of induced velocity:

<img src="https://tva1.sinaimg.cn/large/008eGmZEly1go7vagtnydj30v40nc3z7.jpg" style="zoom:50%" />

Compared to the results in[], the above results show good consistency. 

**Trimmed state variables:**
<img src="https://tva1.sinaimg.cn/large/008eGmZEly1go7uukerqnj31k20tet9x.jpg" style="zoom:50%" />

The results show good consistency with real-life situations. The helicopter tends to be 'nose down' as it accelerates. The roll angle shows a little variation (within 1 degree) because CCH has no tail rotor so little side force. 

**Trimmed required power:**
<img src="https://tva1.sinaimg.cn/large/008eGmZEly1go7v07jvhsj313v0u0t9z.jpg" alt="U-power" style="zoom: 50%;" />



Maybe the most important thing about the global performance of trimmed states is the required power. This figure illustrates a good tendency of the power required for different flight speeds. The helicopter needs more power to hover than forwarding flight(>0 - 60m/s) because when in hover states, the rotor needs more power to accelerate the flow, while in forwarding flight, more inflow is produced by the wind so the rotor needs to accelerate less flow. In other words, the induced velocity decreases as the speed increase. 

At high speed, the required power increases and this is mainly due to the resistance proportional to the square of the velocity, as well as the retreating blade stalls so more power and collective pitch are needed for the advancing blade.

# Representation of the system in matrix (linear) form

After trimming, the most important thing is to analyze the stability. To do this, we use the linear system theory to build the matrix representation of the system: dX/dt = AX+BU

![image-20210305222209852](https://tva1.sinaimg.cn/large/008eGmZEly1go9e91g5uvj30fe0hhac1.jpg)

![image-20210305222226221](https://tva1.sinaimg.cn/large/008eGmZEly1go9e92juyrj30770a3mxh.jpg)

![image-20210305222240211](https://tva1.sinaimg.cn/large/008eGmZEly1go9e8zafh9j30gd03pwep.jpg)

![image-20210305222247653](https://tva1.sinaimg.cn/large/008eGmZEly1go9e93ecykj306o02hq2x.jpg)

![image-20210305222255145](https://tva1.sinaimg.cn/large/008eGmZEly1go9e8y5fjsj307f02yglm.jpg)
$$
A = \left[
\begin{matrix}
X_{\Delta u}/m & X_{\Delta w}/m & X_q/m-w_0 & X_{\Delta \theta}/m & X_{\Delta v}/m & X_p/m & X_r/m+v_0 & X_{\Delta \phi}/m \\
Z_{\Delta u}/m & Z_{\Delta w}/m & Z_q/m+u_0 & Z_{\Delta \theta}/m & Z_{\Delta v}/m & Z_p/m-v_0 & Z_r/m & Z_{\Delta \phi}/m \\
M_{\Delta u}/I_y & M_{\Delta w}/I_y & M_q/I_y & M_{\Delta \theta}/I_y & M_{\Delta v}/I_y & M_p/I_y & M_r/I_y & M_{\Delta \phi}/I_y \\
0 & 0 & cos\phi_0 & 0 & 0 & 0 & -sin \phi_0 & 0   \\
Y_{\Delta u}/m & Y_{\Delta w}/m & Y_q/m & Y_{\Delta \theta}/m & Y_{\Delta v}/m & Y_p/m+w_0 & Y_r/m-u_0 & Y_{\Delta \phi}/m \\
\frac{I_zL_{\Delta u}+I_{xz}N_{\Delta u}}{I_xI_z-I_{xz}^2} & \frac{I_zL_{\Delta w}+I_{xz}N_{\Delta w}}{I_xI_z-I_{xz}^2} & \frac{I_zL_q+I_{xz}N_q}{I_xI_z-I_{xz}^2} & \frac{I_zL_{\Delta \theta}+I_{xz}N_{\Delta \theta}}{I_xI_z-I_{xz}^2} & \frac{I_zL_{\Delta v}+I_{xz}N_{\Delta v}}{I_xI_z-I_{xz}^2} & \frac{I_zL_p+I_{xz}N_p}{I_xI_z-I_{xz}^2} & \frac{I_zL_r+I_{xz}N_r}{I_xI_z-I_{xz}^2} & \frac{I_zL_{\Delta \phi}+I_{xz}N_{\Delta \phi}}{I_xI_z-I_{xz}^2}\\
\frac{I_{xz}L_{\Delta u}+I_xN_{\Delta u}}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_{\Delta w}+I_xN_{\Delta w}}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_q+I_xN_q}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_{\Delta \theta}+I_xN_{\Delta \theta}}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_{\Delta v}+I_xN_{\Delta v}}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_p+I_xN_p}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_r+I_xN_r}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_{\Delta \phi}+I_xN_{\Delta \phi}}{I_xI_z-I_{xz}^2}\\
 0 & 0 & sin\phi_0 tan\theta_0 & 0 & 0 & 1 & cos\phi_0 tan\theta_0 & 0  \\
\end{matrix}
\right ]
$$

$$
B = \left[
\begin{matrix}
X_{\Delta \theta_0}/m & X_{\Delta \theta_{diff}}/m & X_{\Delta \theta_{1c}}/m & X_{\Delta \theta_{1s}}/m & X_{\Delta \theta_{prop}}/m & X_{\Delta \theta_e}/m & X_{\Delta \theta_r}/m & X_{\Delta \theta_{1cdiff}}/m & X_{\Delta \theta_{1sdiff}}/m \\
Z_{\Delta \theta_0}/m & Z_{\Delta \theta_{diff}}/m & Z_{\Delta \theta_{1c}}/m & Z_{\Delta \theta_{1s}}/m & Z_{\Delta \theta_{prop}}/m & Z_{\Delta \theta_e}/m & Z_{\Delta \theta_r}/m & Z_{\Delta \theta_{1cdiff}}/m & Z_{\Delta \theta_{1sdiff}}/m \\
M_{\Delta \theta_0}/I_y & M_{\Delta \theta_{diff}}/I_y & M_{\Delta \theta_{1c}}/I_y & M_{\Delta \theta_{1s}}/I_y & M_{\Delta \theta_{prop}}/I_y & M_{\Delta \theta_e}/I_y & M_{\Delta \theta_r}/I_y & M_{\Delta \theta_{1cdiff}}/I_y & M_{\Delta \theta_{1sdiff}}/I_y \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
Y_{\Delta \theta_0}/m & Y_{\Delta \theta_{diff}}/m & Y_{\Delta \theta_{1c}}/m & Y_{\Delta \theta_{1s}}/m & Y_{\Delta \theta_{prop}}/m & Y_{\Delta \theta_e}/m & Y_{\Delta \theta_r}/m & Y_{\Delta \theta_{1cdiff}}/m & Y_{\Delta \theta_{1sdiff}}/m \\
\frac{I_zL_{\Delta \theta_0}+I_{xz}N_{\Delta \theta_0}}{I_xI_z-I_{xz}^2} & \frac{I_zL_{\Delta \theta_{diff}}+I_{xz}N_{\Delta \theta_{diff}}}{I_xI_z-I_{xz}^2} & \frac{I_zL_{\Delta \theta_{1c}}+I_{xz}N_{\Delta \theta_{1c}}}{I_xI_z-I_{xz}^2} & \frac{I_zL_{\Delta \theta_{1s}}+I_{xz}N_{\Delta \theta_{1s}}}{I_xI_z-I_{xz}^2} & \frac{I_zL_{\Delta \theta_{prop}}+I_{xz}N_{\Delta \theta_{prop}}}{I_xI_z-I_{xz}^2} & \frac{I_zL_{\Delta \theta_e}+I_{xz}N_{\Delta \theta_e}}{I_xI_z-I_{xz}^2} & \frac{I_zL_{\Delta \theta_r}+I_{xz}N_{\Delta \theta_r}}{I_xI_z-I_{xz}^2} & \frac{I_zL_{\Delta \theta_{1cdiff}}+I_{xz}N_{\Delta \theta_{1cdiff}}}{I_xI_z-I_{xz}^2} & \frac{I_zL_{\Delta \theta_{1sdiff}}+I_{xz}N_{\Delta \theta_{1sdiff}}}{I_xI_z-I_{xz}^2} \\
\frac{I_{xz}L_{\Delta \theta_0}+I_xN_{\Delta \theta_0}}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_{\Delta \theta_{diff}}+I_xN_{\Delta \theta_{diff}}}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_{\Delta \theta_{1c}}+I_xN_{\Delta \theta_{1c}}}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_{\Delta \theta_{1s}}+I_xN_{\Delta \theta_{1s}}}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_{\Delta \theta_{prop}}+I_xN_{\Delta \theta_{prop}}}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_{\Delta \theta_e}+I_xN_{\Delta \theta_e}}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_{\Delta \theta_r}+I_xN_{\Delta \theta_r}}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_{\Delta \theta_{1cdiff}}+I_xN_{\Delta \theta_{1cdiff}}}{I_xI_z-I_{xz}^2} & \frac{I_{xz}L_{\Delta \theta_{1sdiff}}+I_xN_{\Delta \theta_{1sdiff}}}{I_xI_z-I_{xz}^2} \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 
\end{matrix} 
\right ]
$$

