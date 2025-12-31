# 8 Phoenix (八凤)
### 基于硅光子互连的开源 7nm AI 加速器

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Status](https://img.shields.io/badge/Status-开发中-yellow)](https://github.com/)
[![Language](https://img.shields.io/badge/Language-English%20%7C%20中文-red)](README.md)

8 Phoenix (八凤) 是一个硬件与软件协同设计的项目，旨在利用光通信解决 AI 的“内存墙”难题。通过将硅光子技术直接集成在 7nm 计算阵列中，我们实现了 8 颗芯片如同一颗统一的 1TB 处理器般协同工作。本项目完全开源，旨在为封闭的私有 AI 硬件提供高性能的替代方案

---

## 🚀 愿景：打破 AI 算力墙
当前的 AI 硬件被封闭在私有生态系统中，且“先进制程”的价格令人望而却步。“八凤”通过以下方式改变游戏规则：
1. **7nm 成熟制程：** 利用高良率、低成本的 7nm 节点，实现可持续的硬件制造。
2. **光子网络：** 使用光速硅光子技术取代功耗巨大的铜线，实现芯片间的高速通信。
3. **开源架构：** 为全球社区提供中英双语开源仓库，方便开发者审查、构建和扩展。

---

## 🛠 硬件规格 (目标参数)
| 特性 | 规格说明 |
| :--- | :--- |
| **工艺节点** | 7nm (FinFET) |
| **计算单元** | 8 芯片同步阵列 (8-Chip Tray) |
| **峰值算力** | 2.4 PetaFLOPS (FP16/BF16) |
| **统一显存** | 1,024 GB (1 TB) 通过 HBM3 实现 |
| **互连技术** | Phoenix-Link 光互连网格 (每枚芯片 3.2 TB/s) |
| **设计功耗 (TDP)** | 每单元 300W |

---

## 📂 项目结构
* `docs/`: 双语技术规范和 ISA 指令集手册。
* `hw/`: RTL 设计、平面布置图 (Floorplan) 和内存控制器逻辑。
* `sw/`: 编译器 (Phoenix-C)、功能仿真器和驱动栈。
* `examples/`: “Hello World” 矩阵运算及基础 AI 模型实现。

---

## 🏁 开始使用

### 1. 了解架构
阅读 [指令集架构 (ISA)](docs/ISA_SPEC.md) 手册，了解“八凤”如何通过确定性方式处理矩阵运算。

### 2. 运行功能仿真器
使用我们基于 Python 的仿真器测试 Phoenix-Matrix 指令的执行逻辑：
```bash
python sw/simulator/functional_model.py