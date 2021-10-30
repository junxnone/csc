---
Title | CMU 15-418 Lecture 1 Why parallelism
-- | --
Create Date | `2021-09-26T02:51:50Z`
Update Date | `2021-10-30T03:24:33Z`
Edit link | [here](https://github.com/junxnone/csc/issues/3)

---
# Reference
- [Microprocessor Trend Data](https://github.com/karlrupp/microprocessor-trend-data)


# Brief
- **并行计算发展史:** `多处理器的计算机` --> `云计算`
- 处理器性能发展史
  - 4/8/16/32 --> 64 bit
  - 3.5 CPI --> 1.1 CPI
  - 10Mhz/200Mhz --> 3GHz
  - ILP: Superscalar & OoO
  - ...
- CPU 瓶颈 - `Power Density Wall`
  - 单处理器的性能到达瓶颈, 提升很慢

## Term

- **CPI** : Cycles Per Instruction
- **ILP**: instruction-level parallelism - 指令并行
- **OoO**: Out of order

## History of Parallel Computing

- 1970s 用于超级计算机进行科学计算
- 1990s 用于数据库/Web服务/交易
- 2004 CPU 频率升级到达技术瓶颈
- 2019 用于云计算


[Microprocessor Trend Data](https://github.com/karlrupp/microprocessor-trend-data) |
-- |
![image](https://user-images.githubusercontent.com/2216970/134624585-0f72cb55-a779-4615-ab14-3f5dfa8e3bf1.png)

## `SuperComputer` VS `Cloud System`(Data Center)

VS | SuperComputers | Cloud System(Data Center Clusters)
-- | -- | --
目标应用 | Few, Big tasks | Many small tasks
硬件 | - 定制化<br>- 高可靠性<br>- 低延迟连接 | - 消费级<br>- 低成本<br>- 吞吐量优化连接
Run-Time System | - Minimal<br>- 静态调度 | - 高可靠性<br>- 动态调度
Application Programming | - Low-level, processor-centric model<br>- Programmer manages resources | - High level, data-centric model<br>- Let run-time system manage resources



## 并行编程 4 个方向

- SIMD and multi-core parallelism
- CUDA programming on NVIDIA GPUs
- Parallel Programming via a Shared-Address Space Model
- Parallel Programming via a Message Passing Model
