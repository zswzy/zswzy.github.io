---
layout:     post
title:      Summary-chapter2
subtitle:   
date:       2020-05-26
author:     Zeyuan
header-img: img/ibmpower9supercomputer.jpg
catalog: true
tags:
    - ST7
---
- 这里是一
个目录
{:toc}
# Summary Chapter2

## Lecture1 - MPI principle, point-to-point communication

### Principles of message passing and MPI

### **Basic MPI instructions**

- Importing MPI module:

  - ```python
    from mpi4py import MPI
    ```

- To know the number of run MPI processes (of the application):

  - ```python
    comm = MPI.COMM_WORLD
    NbP = comm.Get_size()
    ```

- To know the process Id (from *0* up to *NbP-1*):

  - ```python
    Me = comm.Get_rank()
    ```

**No assumption about message printing order!**

### Point-to-Point communications

![image-20200524164135209](https://tva1.sinaimg.cn/large/007S8ZIlgy1gf3x5t1a23j30ya0lwq81.jpg)

#### Buffered & blocking comm.: Bsend/Recv

- Non-blocking send, buffered send
- Blocking recv

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf686juaixj30u803yt99.jpg" alt="image-20200524164734631" style="zoom:50%;" />

**Bsend**: 先把数据拷贝到buffer再发送，拷贝完毕后return。原始数据可以被重写。

**Recv**: 请求数据交换，等到整个数据接收

```python
bsend(self, obj, int dest, int tag=0)
# tag: Only send and recv with identical tag can match
Bsend(self, buf, int dest, int tag=0)
obj = recv(self, int source=ANY_SOURCE,
							int tag=ANY_TAG, Status status=None)
Recv(self, buf, int source=ANY_SOURCE, int tag=ANY_TAG, 									Status status=None)
```

```python
//One process code
...
Bsend(Tab,...,Me+1,...);
Recv(Tab,...,Me-1,...);
...
```

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf686l6kjij30qk07ygmq.jpg" alt="image-20200524165117725" style="zoom:50%;" />



#### Synchronous & blocking comm.: Ssend/Recv

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf686xnfvvj30gw0bwq4g.jpg" alt="image-20200524165152561" style="zoom:50%;" />

Communications are *appointments (***Rendez- Vous)** between processes。

分为两步：

- 第一步，Tab->buffer,**Ssend**: 请求数据交换，等待整个数据发送。不能被重写目的地的原始数据。（放在buffer里）
- 第二步，Tab->Tab,**Recv**: 请求数据交换并等到整个数据接收。接收完毕后return。

奇数process：先Ssend再Recv，偶数：先Recv再Ssend再交换 permute

会比Bsend/Recv执行时间长

```python
ssend(self, obj, int dest, int tag=0)
Ssend(self, buf, int dest, int tag=0)

obj = recv(self, int source=ANY_SOURCE,int tag=ANY_TAG, 								Status status=None)
Recv(self, buf, int source=ANY_SOURCE, int tag=ANY_TAG, 								Status status=None)
```

```python
if (processId %2 == 0):
	Ssend(Tab,...,Me+1,...)
  Recv(Tab,...,Me-1,...)
else:
  Recv(buffer,...,Me-1,...);
  Ssend(Tab,...,Me+1,...);
	permut(buffer,Tab);
```

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf68754ngej30n408sgmt.jpg" alt="image-20200524170359072" style="zoom:50%;" />

- 注意如果不分奇偶的话会有deadlock

#### « Standard & Blocking » comm.: Send/Recv

**Send**: Allows constructors to implement optimizations function of their architecture. Not a portable communication mechanism。 比如，信息规模较小时，会像Bsend，较大时，会像Ssend。Behavior is not guagranteed.

**Recv**:不变。正常。请求数据交换，等到所有数据接收，接收后返回。

- 由于可移植性portability，PC cluster不应该用这种 stantard-blocking comm。
- 由于comm的efficiency，SuperComputer应该用这种。会附带一个标准协议的文档说明。

#### Combined & Blocking comm.: Sendrecv

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf3y1ht2vwj30vg03it8y.jpg" alt="image-20200524171200005" style="zoom:50%;" />

**Sendrecv**:1 send & 1recv, 1 operation.

```python
recvobj = sendrecv(self, sendobj, int dest, int sendtag=0, 									int source=ANY_SOURCE, int recvtag=ANY_TAG,
								Status status=None)

Sendrecv(self, sendbuf, int dest, int sendtag=0,
								recvbuf=None, int source=ANY_SOURCE, int 										recvtag=ANY_TAG, Status status=None)liang zo
```

两种scheme：

- 奇数和邻居交换数据，然后偶数和邻居交换数据。<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf3y4ansu1j30vq06uq3v.jpg" alt="image-20200524171440874" style="zoom:50%;" />
- <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf3y4f7yauj30wk06qgmi.jpg" alt="image-20200524171450902" style="zoom:50%;" />

#### Combined & Blocking: Sendrecv_replace - **only for numpy**

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf3yu6caw2j30pq05qjs6.jpg" alt="image-20200524173932813" style="zoom:50%;" />

**Sendrecv_replace**: 1 send, 1recv, 1 buffer

```python
Sendrecv_replace(self, buf, int dest, int sendtag=0,
					int source=ANY_SOURCE, int recvtag=ANY_TAG,
					Status status=None)
```

**No need for a fine schedule: just follow the circulation scheme. Easy to use** & **very efficient** communications!

#### Data circulation on a ring of processes

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf3z01rj61j30tq0l80yb.jpg" alt="image-20200524174508386" style="zoom:50%;" />

#### Asynchronous point-to-point comms.

**Non-blocking** Send and Recv operations

**Isend**: 运行一个send线程，然后返回

**Irecv**：运行一个receiv线程，然后返回

- 可能在通信和计算上会有重叠
- 但在send操作结束前，或者下一个计算之前，不回重写data MyTab
- 用一个data buffer otherTab去接收数据

**Wait(...)**:重新同步计算和通信，等待他们结束，这样就可以重写MyTab

```python
// local computations
reqs = comm.isend(myTab,dest); // launch a thread
reqr = comm.irecv(otherTab,src);// launch a thread
next_calcul(...)
reqs.Wait(); reqr.Wait(); //remaining inactive up to the Wait(...) operation !No overlap!
// end of computations
```

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf48ws4m7vj30wu0cm41v.jpg" alt="image-20200524232803576" style="zoom:50%;" />

### **Example: dense matrix product on a ring**

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf48xbtjh4j30vk05kaan.jpg" alt="image-20200524232839082" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf48ycg0g7j30us0howj5.jpg" alt="image-20200524232933800" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf498a8isij30va06st9l.jpg" alt="image-20200524233907355" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf49b8rzfcj30wk0jqdjf.jpg" alt="image-20200524234158324" style="zoom:50%;" />

```python
import numpy as np
comm = MPI.COMM_WORLD
LOCAL_SIZE = SIZE//NbP
#double A_slice[LOCAL_SIZE][SIZE];
data = np.empty(LOCAL_SIZE*SIZE, dtype=float)

#Loop computation-circulation
def ComputationAndCirculation:
  for step in range(NbP):
		LocalSliceProduct(step)
    comm.Sendrecv_replace(data,(Me-1)%NbP,source=(Me+1)%NbP)
    ...
```



---

## Lecture2 Multithreading with OpenMP- Parallelized code on one node - Multithreading thread是比process更小的单位

### Principesd’OpenMP

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf52qkoltxj31280mqjuj.jpg" alt="image-20200525163959823" style="zoom:50%;" />

#### Ctrl du parallélisme par directives

![image-20200525164040888](https://tva1.sinaimg.cn/large/007S8ZIlgy1gf52r9y7j6j311w0ngte0.jpg)

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf687oetmxj311c0nmdl2.jpg" alt="image-20200525164527444" style="zoom:50%;" />

### Exemples de parallélisation

Parallélisation de la relaxation de Jacobi

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf52zh0z4tj311q0mgn1c.jpg" alt="image-20200525164835638" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf52zozcahj311s0nm0zu.jpg" alt="image-20200525164850513" style="zoom:50%;" />



Parallélisation du bubble-sort

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf687wx46aj31140lewir.jpg" alt="image-20200525164900869" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf5301ocq6j311o0nudkt.jpg" alt="image-20200525164910690" style="zoom:50%;" />



---

## Lecture3 - MPI application deployment

### Déploiement sur cluster de multicoeurs et mécanismes de MPI

结构：node - socket - core

**Ressources matérielles:**<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf53vi8iy6j30p009gwfc.jpg" alt="image-20200525171925755" style="zoom:50%;" />

**Topologie des processus (ex : anneau)**: <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf53vs37d6j30pk05awez.jpg" alt="image-20200525171941036" style="zoom:50%;" />

```python
mpirun –np #P –machinefile machines.txt
			-map-by ppr:N: <node|socket|core...>
			-rank-by <node|socket|core...>
			-bind-to <none|socket|core...>
```

**-map-by**:topologie virtuelle sur les rsrcs matérielles ?

**-rank-by**: processus MPI sur la topologie matérielle

**-bind-to**:process sur les rsrcs matérielles locales 实际上limité à un socket

**ppr:N**: Nbr de processus par ressource

#### Sol 1 : un processus MPI par nœud 一个node一个process

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf541e90jnj30og08o75d.jpg" alt="image-20200525172503199" style="zoom:50%;" />

每个process对应一个node，按node的序号排列process，每个process的实际存储在一个node/socket里面（的内存）。P个process至少需要P个node/machine

```python
mpirun –np #P –machinefile machines.txt
			-map-by ppr:1:node
			-rank-by node
			-bind-to none|socket
```



#### Sol 2 : un processus MPI par cœur en « mode compact »

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf543sur56j30o406w40j.jpg" alt="image-20200525172721998" style="zoom:50%;" />

每个process对应一个core，按core的序号排列，并且实际上也是在core里面跑。如果一个node有C个core的话，至少需要P/C个node。

```python
mpirun –np #P –machinefile machines.txt
			-map-by ppr:1:core #或者ppr:#C:node
			-rank-by core
      -bind-to core .........
```

#### Sol 3 : un processus MPI par cœur en « round robin »

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf548ylqslj30pm0a8tbn.jpg" alt="image-20200525173220838" style="zoom:50%;" />

每个process对应一个core，**但是按node的序号排列**，实际上也是在core里面跑。如果一个node有C个core的话，至少需要P/C个node。

- 所有的通讯需要跨越node，Pas le plus efficace!!

```python
mpirun –np #P –machinefile machines.txt
			-map-by ppr:1:core
			-rank-by node 		
      -bind-to core .........
```

#### Sol 4 : un processus MPI par node et C threads/process

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf688acrtzj30oa07gjsx.jpg" alt="image-20200525233309800" style="zoom:50%;" />

```python
mpirun –np #P –machinefile machines.txt
				-map-by ppr:1:node
      -rank-by node
      -bind-to none #Refuse parfois de binder sur le nœud entier : threads sur un seul socket !
```

#### **Sol 4’ : un processus MPI par** socket **et C**s threads/process

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf5epl5wwkj30pe084jtg.jpg" alt="image-20200525233420464" style="zoom:50%;" />

```python
mpirun –np #P –machinefile machines.txt
				-map-by ppr:1:socket
      -rank-by socket
      -bind-to socket
```

**Solution plus efficace sur nœuds NUMA (nœuds modernes)**

#### Options de binding de MPI

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf688eta6vj30sy07gjs3.jpg" alt="image-20200525233550500" style="zoom:50%;" />

#### Meilleur déploiement ?
- L’occupation des ressources de calcul disponibles
  - *Déployer une tâche (processus ou thread) par ressource :*
    - au moins une tâche par cœur physique
    - ou une tâche par cœur logique (selon le noyau de calcul utilisé)

- Le schéma de communication obtenu
  - Minimiser les communications inter-nœuds

- Le respect de l’architecture NUMA des nœuds
  - Au moins un processus par sous-nœud NUMA (en général par socket)

在一个cluster上的最优配置也仅限于这个cluster

### EX

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf5ey40o9rj30yi0m4djo.jpg" alt="image-20200525234224836" style="zoom: 50%;" />

-nt 代表每个process分几个thread

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf5ezv5djgj30wo0faq5b.jpg" alt="image-20200525234411418" style="zoom:50%;" />

### Modélisation de performances

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf5ffb06jxj30xw0naq6s.jpg" alt="image-20200525235902502" style="zoom:50%;" />

#### Modélisation des communications

- 在同一个node里面，$t_{comm} = 0$,迅速
- 在不同node间，<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf688m57ovj30qc048gm1.jpg" alt="image-20200526124425376" style="zoom:50%;" /> 一个起始时间，加上与信息量成正比的时间，比较慢

#### Volume des comms. du déploiement

一共三种：

N~node~ x N~socket~ x N~core~ = N~n~ x N~s~ x N~c~

- **一个node一个process，每个process有N~s~ x N~c~ 个thread。** rank-by node<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf61xdea1aj307w04amx9.jpg" alt="image-20200526125735953" style="zoom:50%;" />
  - 对于矩阵乘法，需要进行N~n~次轮换（计算步骤）。
  - 矩阵A的colume d'une tranche ： Q~s~ = Q~A~/N~n~
  - 每一etape，每个process（每一个node）发送Q~s~ 信息到另一个(process)node.
  - **穿越整个reseau的数据量：N~n~x(N~n~xQ~s~) = N~n~xQ~A~**
  - **每个信息的数据量：Q~s~= Q~A~/N~n~**
- **一个socket一个process，每个process有 N~c~ 个thread。**rank-by socket<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf61wy9pxyj3086042q34.jpg" alt="image-20200526125710502" style="zoom:50%;" />
  - 对于矩阵乘法，需要进行N~n~xN~s~次轮换（计算步骤）。
  - 矩阵A的colume d'une tranche ： Q~s~ = Q~A~/(N~n~xN~s~) 比上一个更小
  - 每一etape，每个process（每一个socket）发送Q~s~ 信息到另一个(process)socket，每一个node也是发送Qs到另一个node
  - **穿越整个reseau的数据量：N~n~N~s~x(N~n~xQ~s~) = N~n~xQ~A~**
  - **每个信息的数据量：Q~s~= Q~A~/(N~n~xN~s~)**
  - 信息总量是一定的，但单次发送信息量更少了
- **一个socket一个process，每个process有 N~c~ 个thread。**rank-by node<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf61xjuc2kj308w04caa9.jpg" alt="image-20200526125746718" style="zoom:50%;" />
  - 对于矩阵乘法，需要进行N~n~xN~s~次轮换（计算步骤）。
  - 矩阵A的colume d'une tranche ： Q~s~ = Q~A~/(N~n~xN~s~)
  - 每一etape，每个process（每一个socket）发送Q~s~ 信息到另一个(process)socket，但是每一个node发送QsxN~s~到另一个node
  - **穿越整个reseau的数据量：N~n~N~s~x(N~n~xQ~s~xN~s~) = N~n~xQ~A~xN~s~**
  - **每个信息的数据量：Q~s~= Q~A~/(N~n~xN~s~)**
  - 虽然每次的数据量较小，但总量很大，所以很慢

#### temps d’exécution pour un déploiement donné

部署：一个node一个process，每个process创建C个thread

P个node，每个node有C个core。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf621vrpevj30oi082wg1.jpg" alt="image-20200526130154709" style="zoom:50%;" />

假设矩阵的大小为$\sqrt{N}*\sqrt{N}$，计算C = AxB.

- 非并行：矩阵计算，每计算一个对应元素，就要用A的一行和B的一列，也就是要算根号N次，并且求和根号N次(实际上是根号N-1次)，也就是2倍根号N次。C中一共有N个元素要计算。
  
  - <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf62c5o2nej30b0048t8y.jpg" alt="image-20200526131143091" style="zoom: 33%;" /> *tflop* *tient compte du multithreading sur C coeurs*
- 并行计算：每一个node只需要计算C中的某一列，这一列一共有N/P个元素。而每一轮，只需要计算这一列中的1/P个元素，也就是N/P^2个元素。node之间的通信，数据量为轮换A的一行，也就是N/P个元素。t~s~起始时间可以忽略略不计
  - <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf62jypj4uj30fw0bs757.jpg" alt="image-20200526131916950" style="zoom:33%;" />modele: t~comm~ = t~s~ + qt~w~
  - 一共要算P次：<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf688tj3q0j30co0583yv.jpg" alt="image-20200526132017743" style="zoom:33%;" />
- Speed-up:<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf62lejudyj30d805sq38.jpg" alt="image-20200526132040589" style="zoom:33%;" />

- 计算数据和通信之间的复杂度：计算复杂度>通信，也就是说在N较大的时候，计算复杂度为主导，而这个复杂度是比单核计算要小一些的。

  - <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf62nh8l9hj30rm096q48.jpg" alt="image-20200526132238085" style="zoom:50%;" />当N较大时，可以忽略通信的复杂度，以计算时间为主导。

  <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf62oaw1nyj30nm0543yv.jpg" alt="image-20200526132323271" style="zoom: 33%;" />Speed up的上界为P：增快P倍。<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf62or42cyj304w03qglg.jpg" alt="image-20200526132353594" style="zoom:50%;" />



---

## Lecture4 - Collective communication

### Main available operation

| Blocking           |                        | Non-blocking (since MPI 3.0) |
| ------------------ | ---------------------- | ---------------------------- |
| NumPy arrays       | Generic Python objects | NumPy arrays                 |
| MPI.Comm.Bcast     | MPI.Comm.bcast         | MPI.Comm.Ibcast              |
| MPI.Comm.Gather    | MPI.Comm.gather        | MPI.Comm.Igather             |
| MPI.Comm.Reduce    | MPI.Comm.reduce        | MPI.Comm.Ireduce             |
| MPI.Comm.Scatter   | MPI.Comm.scatter       | MPI.Comm.Iscatter            |
| MPI.Comm.Allgather | MPI.Comm.allgather     | MPI.Comm.Iallgather          |
| MPI.Comm.Allreduce | MPI.Comm.allreduce     | MPI.Comm.Iallreduce          |
| MPI.Comm.Alltoall  | MPI.Comm.alltoall      | MPI.Comm.Ialltoall           |

https://www.mpi-forum.org/docs/

[https://www.mpi-forum.org/docs/mpi-3.1/mpi31-report/mpi31-report.html](https://www.mpi-forum.org/docs/mpi-3.1/mpi31-report/mpi31-report.html)

### Detailed interface

https://mpitutorial.com/tutorials/mpi-scatter-gather-and-allgather/zh_cn/

#### Broadcasting operation

**One process sends same data to all processes (of the group)**

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63hg2wa5j30gm08yaau.jpg" alt="image-20200526135130105" style="zoom:50%;" />

C:

```C
int MPI_Bcast(void *buffer, int count, MPI_Datatype datatype, int root, MPI_Comm comm)
int MPI_Ibcast(void* buffer, int count, MPI_Datatype datatype, int root, MPI_Comm comm, MPI_Request *request)
```

python:

```python
object = MPI.Comm.bcast(object, root) #一般的python对象
MPI.Comm.Bcast(buffer, root) #numpy
request = MPI.Comm.Ibcast(buffer, root)#numpy
```

#### Scattering operation

**One process sends different data to all processes** 把一个数组中的元素分出去

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63hocp7uj30h8094q3s.jpg" alt="image-20200526135140000" style="zoom:50%;" />

C：

```C
int MPI_Scatter(const void* sendbuf, int sendcount, MPI_Datatype sendtype, void* recvbuf, int recvcount, MPI_Datatype recvtype, int root, MPI_Comm comm)
int MPI_Iscatter(const void* sendbuf, int sendcount, MPI_Datatype sendtype, void* recvbuf, int recvcount, MPI_Datatype recvtype, int root, MPI_Comm comm, MPI_Request *request)
```

python:

```python
recvobj = MPI.Comm.scatter(sendobj, root)
MPI.Comm.Scatter(sendbuf, recvbuf, root)#numpy
request = MPI.Comm.Iscatter(sendbuf, recvbuf, root)#numpy
```

#### Gathering operation

**One process receives different data from all processes** 会返回一个数组

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63h6fzwaj30ge08gwfa.jpg" alt="image-20200526135113058" style="zoom:50%;" />

https://pythonprogramming.net/mpi-gather-command-mpi4py-python/

C:

```C
int MPI_Gather(const void* sendbuf, int sendcount, MPI_Datatype sendtype, void* recvbuf, int recvcount, MPI_Datatype recvtype, int root, MPI_Comm comm)
int MPI_Igather(const void* sendbuf, int sendcount, MPI_Datatype sendtype, void* recvbuf, int recvcount, MPI_Datatype recvtype, int root, MPI_Comm comm, MPI_Request *request)
```

python:

```python
recvobj = MPI.Comm.gather(sendobj, root)
MPI.Comm.Gather(sendbuf, recvbuf, root) #numpy
request = MPI.Comm.Igather(sendbuf, recvbuf, root)#numpy
```

#### Reducing operation

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63jcr3mej30rw0bw764.jpg" alt="image-20200526135318359" style="zoom:50%;" />

**One process deduces unique data from all processes**

C:

```C
int MPI_Reduce(const void* sendbuf, void* recvbuf, int count, MPI_Datatype datatype, MPI_Op op, int root, MPI_Comm comm)
int MPI_Ireduce(const void* sendbuf, void* recvbuf, int count, MPI_Datatype datatype, MPI_Op op, int root, MPI_Comm comm, MPI_Request *request)
```

python:

```python
recvobj = MPI.Comm.reduce(sendobj, op, root)
MPI.Comm.Reduce(sendbuf, recvbuf, op, root) #numpy
request = MPI.Comm.Ireduce(sendbuf, recvbuf, op, root)#numpy
```

op: MPI_MAX, MPI_MIN, MPI_SUM, MPI_PROD, MPI_LAND, MPI_LOR, ...

op: MPI.MAX, MPI.MIN, ...

#### Allreduce: Reduce + Bcast

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63jk5hrjj30s00c4767.jpg" alt="image-20200526135331686" style="zoom:50%;" />

#### Allgather：Gather+Bcast

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63i9pyeoj30co09uq3v.jpg" alt="image-20200526135214621" style="zoom:50%;" />

### Examples

点乘和矩阵乘法，好像写的不是很严谨，没有rank什么的

```python
from mpi4py import MPI
import numpy

def dotprod(comm, x, y, xy) :
	xy[0] = numpy.dot(x, y)
  comm.Allreduce(MPI.IN_PLACE, xy, op=MPI.SUM) 		
  return

def matvecprod(comm, A, x, Ax) :
  n = A.shape[0] #行数
	m = A.shape[1] #列数
	x_glob = numpy.empty(m, dtype=x.dtype)
  req = comm.Iallgather(x,x_glob)
	Ax[:] = numpy.dot(A[:,0:n], x)
	req.Wait()
	Ax[:] += numpy.dot(A[:,n:m], x_glob[n:m])
return
```



---

## Lecture5 - Distributed algorithms on multi-dimensional topologies

### Dense matrix product on a 1D ring

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63oubasqj30vc0iwdkh.jpg" alt="image-20200526135833336" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63p5agybj30we0bo75p.jpg" alt="image-20200526135854066" style="zoom:50%;" />

**Performance**:

在第三课已经详细分析过了，这里不多赘述

非并行模式：<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63rdf8xdj30d402ejrd.jpg" alt="image-20200526140057894" style="zoom: 50%;" />

并行模式：<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63rolw3mj30do02mgln.jpg" alt="image-20200526140118370" style="zoom: 50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63s7vb59j30tk04cq3j.jpg" alt="image-20200526140147150" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63shqmokj30wg0bgjtg.jpg" alt="image-20200526140206764" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63sqxkazj30hu04g3yx.jpg" alt="image-20200526140220047" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63t0l1ewj30u408kdhc.jpg" alt="image-20200526140233793" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63t7ottoj30kw0860tj.jpg" alt="image-20200526140246976" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63tsk6qwj30um0j2whh.jpg" alt="image-20200526140316979" style="zoom:50%;" />

### Dense matrix product on a 2D torus

#### Parallelisation scheme

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63vvsstyj30my0c8gob.jpg" alt="image-20200526140519785" style="zoom:50%;" />

partition：

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63wqwlrej30xc0eejta.jpg" alt="image-20200526140611532" style="zoom:50%;" />

**Only one partitioning** for A, B and C
Data circulation principle:

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63zhkuk1j30am0eaglw.jpg" alt="image-20200526140847948" style="zoom:50%;" />

- **A** blocks: require a **circulation on the row** of processes
- **B** blocks: require a **circulation on the colums** of processes

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf63zp041kj30ec0ey74y.jpg" alt="image-20200526140900974" style="zoom:50%;" />

问题：process P~I,J~ 需要同时A~I,K~和B~K,J~中的元素。起始时刻，实际上只有P~I,I~process可以计算。<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf643205j1j30f20emt9g.jpg" alt="image-20200526141213703" style="zoom:50%;" />

改变initial partition：就可以相乘了

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf644m89huj30g00dwgmr.jpg" alt="image-20200526141344967" style="zoom:50%;" />

- **Row** **I** **has been** **pre-shifted** **of** **I** **steps to the left**
- **Column** **J** **has been** **pre-shifted** **of** **J** **steps to the top**

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf64bolkkyj30y40gqq6n.jpg" alt="image-20200526142031933" style="zoom:50%;" />

#### Performance：

第一种：**Implementation with blocking communications** (no overlapping)

Hypothese:

- All computations are load balanced, are identical
- All communications of one matrix shift are achieved in parallel
- All communications cross the same « network » (depends on the deployment !)

preshift:有点像初始化分配矩阵的感觉

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf64gjbl34j30jk02m0st.jpg" alt="image-20200526142511937" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf64go4eznj30ci032aa1.jpg" alt="image-20200526142521753" style="zoom:50%;" />

computation: <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf64idyutgj30p203e0t4.jpg" alt="image-20200526142700735" style="zoom:50%;" />

circulation: <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf64inr5c6j30hu034wer.jpg" alt="image-20200526142715881" style="zoom:50%;" />

post-shift: 最后把矩阵计算的结果收集起来

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf64k4hx6aj30by0260sp.jpg" alt="image-20200526142729246" style="zoom:50%;" />

complete: <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf64ksrm0vj30r00583z4.jpg" alt="image-20200526142918372" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf64l0eroej30ks074t9b.jpg" alt="image-20200526142930721" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf64l6hqjfj30jc02amxd.jpg" alt="image-20200526142941338" style="zoom:50%;" />

Speed-up:<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf64ln1r52j30ts0ca0uk.jpg" alt="image-20200526143007766" style="zoom:50%;" />

第二种：**Implementation with** **non-**blocking communications
<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf650pe1cfj30vc0ioq5y.jpg" alt="image-20200526144420842" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf650qim88j30r80detak.jpg" alt="image-20200526144435313" style="zoom:50%;" />

#### Comparison 1D Ring / 2D Torus solutions:
<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf68a619nuj30xq0h2gnv.jpg" alt="image-20200526144501648" style="zoom:50%;" />

### Hyper-quicksort on a kD hypercube

#### Principe séquentiel

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf65l3f32gj30xk0j0dis.jpg" alt="image-20200526150410392" style="zoom:50%;" />

#### Parallélisation naïve不太懂

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf65lnub2tj30wi0fq768.jpg" alt="image-20200526150443720" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf65nebhgkj30y40jswhi.jpg" alt="image-20200526150623569" style="zoom:50%;" />

#### Hyper-cubes

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf65pd6zbrj30wg06gdgo.jpg" alt="image-20200526150817240" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf65phfboxj30xe0b4dgq.jpg" alt="image-20200526150824167" style="zoom:50%;" />

**Décomposition**:

1 hypercube de dimension n coupé par un hyper-plan donne 2 sous-hypercubes de dimension n-1 :

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf65r4vicij30x00cggmp.jpg" alt="image-20200526150959796" style="zoom:50%;" />

**Distance entre nœuds :**

Le nombre de bits différents dans les adresses de deux nœuds donne leur distance (si la numérotation a suivi la construction récursive)

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf65q5lfchj30sy08gjs8.jpg" alt="image-20200526150903624" style="zoom:50%;" />

Les algorithmes de routages seront à base de calculs simples (et rapides)

#### Principe de parallélisation sur Hyper-Cube不懂

objective:

- **Tous les processeurs doivent travailler tout le temps !**
- S’inspirer d’un tri séquentiel rapide (*O(N.log(N))*) : quick-sort

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf66y9o35cj30y60bo0ug.jpg" alt="image-20200526155101183" style="zoom:50%;" />

**Init :** Chaque nœud charge N/P données en local

**Etape 0 :**

- Choix de 2^0^ pivots pour les 2^0^ hypercubes de dimension d-0
- Séparation selon le pivot sur chaque nœud de l’hypercube
- Echange des listes inférieures et supérieures en dimension d-0
- Fusions locales des listes conservées et des listes reçues

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf670vxbwyj30vo0buae1.jpg" alt="image-20200526155352656" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf671lbgtdj30xw0k077y.jpg" alt="image-20200526155433913" style="zoom:50%;" />

**Etape 1 :**

- Choix de 2^1^ pivots pour les 2^1^ hypercubes de dimension d-1
- Séparation selon un pivot sur chaque nœud des 2^1^ hypercubes
- Echange des listes inférieures et supérieures en dimension d-1
- Fusions locales des listes conservées et des listes reçues

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf676q8k0tj30xs0d4gpy.jpg" alt="image-20200526155932753" style="zoom:50%;" />

**Etape 2 :**

- Choix de 2^2^ pivots pour les 2^2^ hypercubes de dimension d-2
- Séparation selon un pivot sur chaque nœud des 2^2^ hypercubes
- Echange des listes inférieures et supérieures en dimension d-2
- Fusions locales des listes conservées et des listes reçues

![image-20200526155924047](https://tva1.sinaimg.cn/large/007S8ZIlgy1gf676r0x0nj30u40d8q4n.jpg)

**Etape finale :**

- Chaque processeur tri en local sa liste finale

  - ex : quick-sort local et séquentiel sur chaque processeur

  <img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf675lvjalj30wo0d6n06.jpg" alt="image-20200526155829036" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf675uj67ij30x80jgwip.jpg" alt="image-20200526155844023" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf67bdxjd5j30ve0kgwiv.jpg" alt="image-20200526160402697" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf67bne86bj30xi0k0416.jpg" alt="image-20200526160420578" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf67c6l89aj30yo0kodme.jpg" alt="image-20200526160444443" style="zoom:50%;" />

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf67cas767j30xq0o279k.jpg" alt="image-20200526160457663" style="zoom:50%;" />



---

## Lecture6 - Serial optimizations and vectorization

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf67dx44fqj30z00lutwk.jpg" alt="image-20200526160621950" style="zoom:50%;" />

### Three important issues to get optimized code on one CPU core

#### Compile with optimization options
