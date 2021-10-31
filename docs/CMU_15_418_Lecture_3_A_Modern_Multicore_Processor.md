---
Title | CMU 15-418 Lecture 3 A Modern Multicore Processor
-- | --
Create Date | `2021-09-28T07:47:05Z`
Update Date | `2021-10-31T05:23:02Z`
Edit link | [here](https://github.com/junxnone/csc/issues/5)

---
# Brief
- Multi-Core
- SIMD
- 

## Multi-Core
- Thread-level
- 每个 core 执行不同的指令


![image](https://user-images.githubusercontent.com/2216970/139568350-7b1d388a-7b0a-4c78-8979-dc7b18d85b8e.png)| ![image](https://user-images.githubusercontent.com/2216970/139568205-c5e17a32-8edc-4a08-b439-60d2fd63ab02.png)
-- | --

## SIMD
- **SIMD Precessing**(Vector Program/Computing)
- SIMD 并行化在编译时确定
- Instruction-level/Data-Parallel
- 每个 `core->ALUs` 执行 相同的指令
- AVX intrinsics 
  - SSE -> AVX -> AVX512
- 32 -->256(=32*8) ==> 同时处理 `8x` data 

![image](https://user-images.githubusercontent.com/2216970/139568239-41126d20-e497-43d6-9b49-f16db9d6f4db.png) | ![image](https://user-images.githubusercontent.com/2216970/139568266-f0a4f79e-06f6-40e5-a309-3cb2410216aa.png)
-- | --

### SIMD Conditional execution
- 当执行代码段存在条件判断时，不同的分支执行不同的指令, 会有一部分时间浪费掉
- 不好的 code 会严重影响 SIMD 效率
  - `Instruction stream coherence` - 指令流的连续性影响 SIMD 的效率
  - `Divergent/Divergence` - 发散执行, 指缺乏连续性

![image](https://user-images.githubusercontent.com/2216970/135046400-d7da3152-78f7-4709-8ebd-075b66209c29.png)

## Hyperthreading
- Simultaneous Multi-Threading - **Hyperthreading** - 超线程
  - Single core does the work of multiple cores 

![image](https://user-images.githubusercontent.com/2216970/139569166-44734064-21d2-4525-9440-e51d1101746f.png) | ![image](https://user-images.githubusercontent.com/2216970/135049677-8ba6e874-d733-4c64-8632-4a0f896f1790.png)  
-- | --


- Interleaved multi-threading
- Memory
  - Latency(cycles/nsec)
  - Bandwidth (GB/s)
- **Stalls:** 运行下条指令时因为依赖不能运行
  - **Caches reduces stalls** 可以降低 memory access latency
  - **Prefetching reduces stalls:** Prefetching data into caches(prefetching 错误的话也会导致 performance 下降)
  - **Multi-Threading reduces stalls**


> prefetching, multi-threading is a latency hiding, not a latency reducing technique



Hyperthreading
![image](https://user-images.githubusercontent.com/2216970/135067136-aa5fba98-974e-4423-b3fc-11a2e1016d9e.png) | Hiding stalls with Multi-Threading

