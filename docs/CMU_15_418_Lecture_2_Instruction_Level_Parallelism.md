---
Title | CMU 15-418 Lecture 2 Instruction-Level Parallelism
-- | --
Create Date | `2021-09-26T03:27:07Z`
Update Date | `2021-10-30T05:53:10Z`
Edit link | [here](https://github.com/junxnone/csc/issues/4)

---
# Brief
- 多样的处理器 CPU/GPU/FPGA/VPU/...
- 不同处理器的并行方法
- ILP
  - Pipelining & Superscalar - 同时执行多条指令
  - Out of order execution - 动态调度执行指令
  - Speculation - 预测下条指令

## 各种处理器

Processors | 用途 | 并行方法 | 调度 | Cores | Hardware | 编程困难度
-- | -- | -- | -- | -- | -- | --
CPU | 序列化的 code | ILP | 硬件调度 | <100 | 昂贵复杂 | 容易
GPU | 很多独立的 task | 线程及数据并行| 软件调度 | > 1000 | 简单便宜 | 困难
FPGA | 信号处理/神经网络/... 
VPU | 神经网络


## CPU ILP - `instruction-level parallelism`

### Simple CPU Model

- **Fetch** – get the next instruction from memory
- **Decode** – figure out what to do & read inputs
- **Execute** – perform the necessary operations
- **Commit** – write the results back to registers / memory

![image](https://user-images.githubusercontent.com/2216970/139521653-abbc0bdb-5d4e-4b6e-8f18-680103b26877.png) |  ![InkedFoxitReader_BXqXJmKJV8_LI](https://user-images.githubusercontent.com/2216970/134797100-9067690d-c506-4d52-a52b-1b2a8e996499.jpg)
-- | --

### **Pipelining**
- 𝑁-stage pipeline gives up to 𝑁 × speedup
- `Fetch/Decode/Execute/Commit` - 4X Speedup
- 一些限制 Pipeling 并行的因素 - `Data Hazards/





![image](https://user-images.githubusercontent.com/2216970/139521736-2fa7e099-9653-4f7c-82fd-40ea97ce62f9.png) | ![Inkedchrome_k49UtilsYB_LI](https://user-images.githubusercontent.com/2216970/134641857-12563821-6c02-4628-986e-d656c8f76b82.jpg) 
-- | --

#### Data Hazards
- **Data hazards:** 并行需要是独立的任务, 而许多指令之间并不独立(寄存器读写依赖)
  - **example:** 前一条指令要写 `R3`, 后一条指令执行时要读 `R3`, 后一条指令执行时,前一条指令还没有 `commit`


![image](https://user-images.githubusercontent.com/2216970/139521888-154069d7-a378-4e5a-821c-632ff910dc2f.png) | ![Inkedchrome_lKvXLJsrqG_LI](https://user-images.githubusercontent.com/2216970/134646854-ac0014f9-d3e9-4263-a6a2-a0c652f192b3.jpg)
-- | --

- 解决方案: **Forwarding data** - CPU在一个时钟周期内，把一个单元的输出值内容拷贝到另一个单元的输入值中
  - Forwarding is expensive in deep pipelines

![image](https://user-images.githubusercontent.com/2216970/139522099-a4c262e8-e8f1-47d4-a01a-0c5f46cc2787.png) | ![image](https://user-images.githubusercontent.com/2216970/139522125-b8429f53-0b3d-4d6f-9c32-f7c5c5220e3c.png)
-- | --

####  Pipeline Flushes
- **Pipeline Flushes:** Fetch 到错误的指令，需要重新 Fetch 新的指令
  - Pipeline flushes are expensive in deep pipelines




- **Speculation:** CPU 猜测下一条要执行的指令 - 如果猜错, `rolling back`
- **Dataflow:** 根据寄存器依赖并行执行
  - Critical path limits maximum performance
- **Out-Of-Order(OoO):** 乱序执行 - `执行已经准备好的指令`
- **Structural hazard**: 浮点数/整数/Memory 特殊硬件资源有限
- **结论:** 
  - ILP & Pipeline 扩展性不好/动态调度 & OoO代价比较高
  - Multicore 更 Efficient


![InkedFoxitReader_BXqXJmKJV8_LI](https://user-images.githubusercontent.com/2216970/134797100-9067690d-c506-4d52-a52b-1b2a8e996499.jpg) | Simple CPU Model
-- | :--
![Inkedchrome_k49UtilsYB_LI](https://user-images.githubusercontent.com/2216970/134641857-12563821-6c02-4628-986e-d656c8f76b82.jpg) | Pipelining<br> 4X Speedup
![Inkedchrome_lKvXLJsrqG_LI](https://user-images.githubusercontent.com/2216970/134646854-ac0014f9-d3e9-4263-a6a2-a0c652f192b3.jpg) | **Data hazards** 当后一条指令需要用到前一条指令的寄存器时会填充 `NOP` 指令, 以等到前一条指令 `commit` <br> **解决方案**: Forwarding data(部分解决)
![InkedFoxitReader_VtCwFCBeQv_LI](https://user-images.githubusercontent.com/2216970/134799251-a9966841-0923-4adf-a5e7-5cfa216cd237.jpg) | Fetch 到错误的指令, 需要重新 Fetch
![image](https://user-images.githubusercontent.com/2216970/135018839-ab2c87e6-3183-435d-ae35-b14d0926b037.png) | Dataflow
![image](https://user-images.githubusercontent.com/2216970/135019570-42f01b5a-b3e9-4319-85ac-6a8848183d60.png) | OoO
![InkedFoxitReader_lUNIOkZCSc_LI](https://user-images.githubusercontent.com/2216970/135020663-6b36341d-bc37-4710-ae94-2a324e7605b5.jpg) | OoO 
![InkedFoxitReader_K5l8eERM5G_LI](https://user-images.githubusercontent.com/2216970/135027900-51413562-821e-4735-83a7-a62ad350430b.jpg) | Structural Hazards



