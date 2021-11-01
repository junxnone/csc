---
Title | CMU 15-418 Lecture 4 Parallel Programming Abstractions
-- | --
Create Date | `2021-11-01T05:59:02Z`
Update Date | `2021-11-01T05:59:02Z`
Edit link | [here](https://github.com/junxnone/csc/issues/7)

---
# Reference
- [ISPC](https://github.com/ispc/ispc) [[docs](https://ispc.github.io/)]

# Brief
- SPMD - `single program, multiple data`
- ISPC - `Intel SPMD Program Compiler`
  - 用于编译 `C code` 到 `SIMD implementation` - `xxx.ispc` --> `xxx.o`
  - **Program Instance**: 
  - **gang**: The group of running program instances
- **ISPC supports parallelism**
  - **SPMD parallelism**: SIMD vector lanes on a single core  
  - **task parallelism**: multiple processor cores
- **Three parallel Programming models**
  - **Shared address space**
  - **Message passing**
  - **Data parallel**
- **SMP** - `Symmetric multi-processor`
- **NUMA** - `Non-uniform memory access`


![image](https://user-images.githubusercontent.com/2216970/135419585-ea69d459-36ed-407a-8d73-575261c74bb1.png) | Program Instances/gang
-- | --
![image](https://user-images.githubusercontent.com/2216970/135245467-db9b76ba-76a8-456d-91a1-1c41b5b296dc.png) | System Layers
![image](https://user-images.githubusercontent.com/2216970/135245886-c94c6523-4b95-4f45-b75c-e3fbe7de19ac.png) | Thread Programming model
![image](https://user-images.githubusercontent.com/2216970/135245974-87a9145c-45ff-452d-8f3b-4d80875f9e23.png) | ISPC Programming model
![image](https://user-images.githubusercontent.com/2216970/135246760-0cde6b4e-dc3b-49f7-bab6-f4600bdf43d3.png) | Shared address space
![image](https://user-images.githubusercontent.com/2216970/135250232-2b4e42d2-d82b-4d38-97e2-93e295cf7b17.png) | HW implementation of a shared address space
![image](https://user-images.githubusercontent.com/2216970/135251375-cccae0d5-6229-4656-bbee-648ab29acc8a.png) | Message passing model

