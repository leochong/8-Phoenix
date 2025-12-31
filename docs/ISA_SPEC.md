# 8 Phoenix ISA Specification v0.1 (Draft)
# “八凤” 指令集架构规范 v0.1 (草案)

This document defines the core instructions for the 8 Phoenix 7nm Systolic Array.
本文档定义了“八凤” 7nm 脉动阵列的核心指令。

---

## 1. Memory Operations (内存操作)

### PX_LOAD_TILE [Dest_Reg], [HBM_Address]
* **English:** Loads a 16x16 matrix tile from HBM3 memory into the local SRAM buffer.
* **中文:** 将一个 16x16 的矩阵块从 HBM3 内存加载到本地 SRAM 缓冲区。

### PX_STORE_TILE [Src_Reg], [HBM_Address]
* **English:** Stores a result tile from SRAM back to the HBM3 memory.
* **中文:** 将 SRAM 中的结果块存储回 HBM3 内存。

---

## 2. Compute Operations (计算操作)

### PX_MATMUL [Reg_A], [Reg_B]
* **English:** Executes a deterministic matrix multiplication. This is the core operation for Transformers.
* **中文:** 执行确定性矩阵乘法。这是 Transformer 模型的核心运算。

### PX_RELU [Reg]
* **English:** Performs a rectified linear unit activation on the specified register.
* **中文:** 对指定寄存器执行 ReLU 激活函数。

---

## 3. Optical Interconnect (光互连)

### PX_SYNC_ALL
* **English:** Synchronizes all 8 chips in the tray. No chip proceeds until the optical "handshake" is complete.
* **中文:** 同步阵列中的所有 8 颗芯片。在光子“握手”完成前，所有芯片均不继续执行。

### PX_OPT_PUSH [Target_Chip_ID], [Reg]
* **English:** Pushes a data tile through the Silicon Photonics fabric to a specific neighbor chip.
* **中文:** 通过硅光子网络将数据块推送到特定的邻居芯片。