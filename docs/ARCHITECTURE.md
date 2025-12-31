# 8 Phoenix: Architectural Overview / 架构概览

## 1. The Core Philosophy (核心理念)
**English:** 8 Phoenix utilizes a "Deterministic Dataflow" architecture. Unlike traditional GPUs that use complex schedulers, 8 Phoenix relies on a compiler-driven approach to move data between HBM3 and the Systolic Array at precise clock cycles.
**中文:** “八凤”采用“确定性数据流”架构。与使用复杂调度器的传统 GPU 不同，“八凤”依赖编译器驱动的方法，在精确的时钟周期内实现 HBM3 与脉动阵列之间的数据传输。

---

## 2. The 8-Chip Optical Tray (8 芯片光互连阵列)
**English:** The system consists of 8 identical 7nm chiplets mounted on a specialized substrate.
* **Interconnect:** Silicon Photonics Mesh.
* **Coherence:** Unified Memory Space across 1TB of HBM3.
* **Latency:** < 100ns chip-to-chip jump.

**中文:** 系统由 8 个安装在专用基板上的相同 7nm 小芯片 (Chiplets) 组成。
* **互连技术:** 硅光子网格。
* **一致性:** 跨 1TB HBM3 的统一内存空间。
* **延迟:** 芯片间跳变延迟 < 100ns。

---

## 3. Floorplan Strategy (芯片布局策略)
| Module / 模块 | Description / 描述 |
| :--- | :--- |
| **8P-Core** | 512x512 INT8/FP16 Systolic Array (脉动阵列) |
| **L-Buffer** | 128MB On-chip SRAM (片上缓存) |
| **Opti-Bridge** | Silicon Photonics I/O (硅光子输入/输出) |
| **HBM-Ctrl** | Deterministic HBM3 Controller (确定性内存控制器) |

---

## 4. Scalability (可扩展性)
**English:** By using light instead of copper, 8 Phoenix avoids the "Thermal Wall." We can scale to rack-level (64+ chips) without the signal integrity degradation found in PCIe/NVLink systems.
**中文:** 通过使用光通信而非铜线，“八凤”避开了“热墙”效应。我们可以扩展到机架级（64+ 芯片），而不会出现 PCIe/NVLink 系统中常见的信号完整性衰减。