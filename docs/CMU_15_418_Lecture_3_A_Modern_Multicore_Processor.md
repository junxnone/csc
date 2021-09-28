---
Title | CMU 15-418 Lecture 3 A Modern Multicore Processor
-- | --
Create Date | `2021-09-28T11:22:39Z`
Update Date | `2021-09-28T11:22:39Z`
Edit link | [here](https://github.com/junxnone/csc/issues/5)

---
# Brief
- Multi-Core
  - Thread-level
  - 每个 core 执行不同的指令
- **SIMD Precessing**(Vector Program/Computing)
  - SIMD 并行化在编译时确定
  - Instruction-level/Data-Parallel
  - 每个 core->ALUs 执行 相同的指令
- Simultaneous Multi-Threading - **Hyperthreading**
  - Single core does the work of multiple cores 
- Interleaved multi-threading
- Memory
  - Latency(cycles/nsec)
  - Bandwidth (GB/s)
- **Stalls:** 运行下条指令时因为依赖不能运行
  - **Caches reduces stalls** 可以降低 memory access latency
  - **Prefetching reduces stalls:** Prefetching data into caches(prefetching 错误的话也会导致 performance 下降)
  - **Multi-Threading reduces stalls**


> prefetching, multi-threading is a latency hiding, not a latency reducing technique

![image](https://user-images.githubusercontent.com/2216970/135046400-d7da3152-78f7-4709-8ebd-075b66209c29.png) | SMD<br>Conditional execution<br>Not all ALUs  do useful work
-- | --
![image](https://user-images.githubusercontent.com/2216970/135049677-8ba6e874-d733-4c64-8632-4a0f896f1790.png) | Hyperthreading
![image](https://user-images.githubusercontent.com/2216970/135067136-aa5fba98-974e-4423-b3fc-11a2e1016d9e.png) | Hiding stalls with Multi-Threading

