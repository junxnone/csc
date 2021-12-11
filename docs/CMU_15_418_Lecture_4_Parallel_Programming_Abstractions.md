---
Title | CMU 15-418 Lecture 4 Parallel Programming Abstractions
-- | --
Create Date | `2021-09-29T02:00:07Z`
Update Date | `2021-12-11T08:17:13Z`
Edit link | [here](https://github.com/junxnone/csc/issues/7)

---
## Reference
- [ISPC](https://github.com/ispc/ispc) [[docs](https://ispc.github.io/)]

## Brief
- SPMD - `single program, multiple data` - `Programming model`
- ISPC - `Intel SPMD Program Compiler`
- Programming models
- **SMP** - `Symmetric multi-processor`
- **NUMA** - `Non-uniform memory access`


## SPMD & ISPC
- SPMD - `single program, multiple data` 
- ISPC - `Intel SPMD Program Compiler` 
  - 用于编译串行 `C code` 到 `SIMD implementation` 程序  - `xxx.ispc` --> `xxx.o`
- **Program Instance**:  同时运行的程序 `single program`
- **gang**:  一系列的 `Program Instance`
  - = N x `Program Instance` - N 取决于 `SIMD width` 
  - 用于 `one core` + SIMD
- **task**: 用于 multi-core 
  - 比 thread 更轻量 
- **ISPC supports parallelism**
  - **SPMD parallelism**: SIMD vector lanes on a single core  
  - **task parallelism**: multiple processor cores

Interleaved assignment | Blocked assignment
-- | --
![image](https://user-images.githubusercontent.com/2216970/139635445-4c75c251-82e2-4ea2-bf90-b8440b465968.png) | ![image](https://user-images.githubusercontent.com/2216970/139635947-6e721047-963c-405c-9337-0599eaffa91e.png)
![image](https://user-images.githubusercontent.com/2216970/139635773-285ee1fc-4b74-4bc5-a9d7-7cde348a855e.png) | ![image](https://user-images.githubusercontent.com/2216970/139636004-4a7d4128-1b2b-4fbd-9887-79a27ddb725a.png)
![image](https://user-images.githubusercontent.com/2216970/139636184-b9f009df-3e2e-44cb-b332-5db7c652fcfb.png) | ![image](https://user-images.githubusercontent.com/2216970/139636199-72654d6e-ef42-4560-86b9-8b8d085966d3.png)



## Programming models
- Thread Programming model
- ISPC Programming model

System Layers Interface & Implementation | ![image](https://user-images.githubusercontent.com/2216970/135245467-db9b76ba-76a8-456d-91a1-1c41b5b296dc.png) 
-- | --
Thread Programming model |  ![image](https://user-images.githubusercontent.com/2216970/135245886-c94c6523-4b95-4f45-b75c-e3fbe7de19ac.png) 
ISPC Programming model | ![image](https://user-images.githubusercontent.com/2216970/135245974-87a9145c-45ff-452d-8f3b-4d80875f9e23.png)


- 按照通信方式可以分为三种模型
- 实际使用中会混合使用编程模型 `Shared Address Space` + `Message Passing`

Model | Description
-- | --
**Shared address space** | - 共享变量<br> 非结构化数据<br> - 主动性更强？？
**Message passing** | - 发送/接收消息<br> - 结构化数据
**Data parallel** | - SIMD Vector Processor<br>- 通信受 iterations 限制



#### Shared Address Space Model

Shared address space | ![image](https://user-images.githubusercontent.com/2216970/135246760-0cde6b4e-dc3b-49f7-bab6-f4600bdf43d3.png) 
-- | --
**SMP** HW Implementation | ![image](https://user-images.githubusercontent.com/2216970/135250232-2b4e42d2-d82b-4d38-97e2-93e295cf7b17.png) 
**NUMA** HW Implementation | ![image](https://user-images.githubusercontent.com/2216970/139651287-47c6f557-cfa4-4039-b0b1-0d1dd8b6d0e0.png)

HW Arch |  Description
-- | --
SMP | - 处理器通过 Interconnect 直接访问所有处理器<br>- 对所有处理器而言, 访问 DRAM 时间相同
NUMA | - 每个处理器拥有自己的Memory<br>- 每个处理器可以通过 `Interconnect` 访问其他处理器的 Memory<br>- 对本地内存的访问是 `low lantency` + `high bandwidth`


- SMP - Symmetric(shared-memory) multi-processor
- NUMA - Non-uniform memory access
- Interconnect
  - Hyper-transport - AMD
  - QuickPath (QPI) - Intel

#### Message Passing Model
- MPI - `Message Passing Interface`
- 通常用于机器集群

Message passing | ![image](https://user-images.githubusercontent.com/2216970/135251375-cccae0d5-6229-4656-bbee-648ab29acc8a.png) 
-- | --


#### Data Parallel Model
- 一个函数处理大量的数据
- HW  support - Vector Processors -  SIMD
- SPMD Programming
- Stream Programming
- Languages - ISPC/OpenCL/CUDA

ISPC-> SPMD/SIMD | ![image](https://user-images.githubusercontent.com/2216970/135419585-ea69d459-36ed-407a-8d73-575261c74bb1.png) 
-- | --


#### Stream Programming
- Streams - Data
- Kernels - 处理函数 
- Gather/Scatter


Streams Programming | Description
-- | --
Benefits | - 函数独立<br>- data 已知, prefetching 优势<br>- Cache 优势, 可以减少读写 Memory
Drawbacks | Need library of operators to describe complex data flows ???




