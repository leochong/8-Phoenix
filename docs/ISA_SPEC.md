8 Phoenix ISA Specification v0.2
“八凤” 指令集架构规范 v0.2

1. Architectural State (架构状态)
Before executing instructions, the programmer must understand the register file: 在执行指令之前，程序员必须了解寄存器堆：

Tile Registers (T0 - T63): 64 registers, each holding a 16x16 FP16 matrix (512 bytes per register).

块寄存器 (T0 - T63): 64 个寄存器，每个寄存器存储一个 16x16 FP16 矩阵（每个寄存器 512 字节）。

Scalar Registers (S0 - S15): 16 registers for loop counters and memory addresses.

标量寄存器 (S0 - S15): 16 个用于循环计数和内存地址的寄存器。

2. Memory Operations (内存操作)
PX_LOAD_TILE [Dest_T], [Base_S], [Offset_S]
Description: Loads a 16x16 tile from HBM3 into Tile Register Dest_T.

描述: 从 HBM3 内存加载一个 16x16 矩阵块到块寄存器 Dest_T。

PX_STORE_TILE [Src_T], [Base_S], [Offset_S]
Description: Stores Tile Register Src_T to HBM3.

描述: 将块寄存器 Src_T 存储回 HBM3 内存。

3. Compute Operations (计算操作)
PX_MATMUL [T_Dest], [T_SrcA], [T_SrcB]
Operation: T_Dest = T_SrcA * T_SrcB + T_Dest (FMA - Fused Multiply Add).

操作: 执行乘累加运算。这是核心的脉动阵列运算。

PX_RELU [T_Dest]
Operation: element = max(0, element) for all elements in the tile.

操作: 对块中的所有元素执行 ReLU 激活函数。

4. Optical & Sync (光互连与同步 - The Missing Link)
PX_SYNC_BARRIER [Mask_S]
Description: Stops execution until all chips defined in the bitmask Mask_S reach this point via the Silicon Photonics link.

描述: 停止执行，直到比特掩码 Mask_S 中定义的所有芯片都通过硅光子链路到达此同步点。

PX_OPT_XCHG [T_Dest], [T_Src], [Target_Chip_ID]
Description: Non-blocking exchange of a tile with a neighbor chip.

描述: 与邻居芯片进行非阻塞式的矩阵块交换。

5. What was missing? (补充说明)
Tile Register Addressing: We didn't specify that we have 64 tiles. This is important for "unrolling" loops in AI models.

Base + Offset Memory: We added Base_S and Offset_S so the chip can handle large tensors in HBM3.

Sync Barrier: In an 8-chip system, you cannot move to the next layer of a neural network until all chips have finished their math. PX_SYNC_BARRIER is the "handshake" that makes this work.