---
Title | OPT WHY
-- | --
Created @ | `2024-04-21T06:31:41Z`
Updated @| `2024-04-21T06:46:11Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/csc/issues/23)

---
#  1 程序性能优化的意义

- 计算系统(处理器架构/存储器)的发展渐缓，性能提升难度变大(受限于主频/存储器读写速度)

## 处理器架构的发展
- 单核 -> 多核 ->众核(GPU) -> 异构(CPU+XPU/...) -> 专用(TPU/NPU/..)
- 指令级并行: 指令流水/多发射/乱序执行
- 数据级并行: SIMD

## 存储器的发展
- 存储读写速度跟不上计算速度
- 数据的时间局部性和空间局部性 -> 缓存


## 编译器能力的局限性
- 编译器的优化能力
  - 自动向量化
  - 自动并行化
- 采用的程序静态分析技术能力有局限
- 采用保守性原则
- 通用性和高效性平衡
- 时间耗费考量


## 编程模型的局限性

- 底层隐藏