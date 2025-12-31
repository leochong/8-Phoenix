# 8 Phoenix (八凤)
### Open-Source 7nm AI Accelerator with Silicon Photonics Interconnect

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Status](https://img.shields.io/badge/Status-In--Development-yellow)](https://github.com/)
[![Language](https://img.shields.io/badge/Language-English%20%7C%20中文-red)](README_CN.md)

8 Phoenix is a hardware-software co-design project aiming to solve the AI "memory wall" using light. By integrating silicon photonics directly onto a 7nm compute tray, we enable 8 chips to act as a single, unified 1TB processor. Open-sourced to provide a high-performance alternative to proprietary AI hardware.

---

## 🚀 Vision: Breaking the AI Wall
Current AI hardware is locked behind proprietary ecosystems and "leading-edge" price tags. 8 Phoenix changes the game by:
1. **7nm Maturity:** Utilizing the high-yield, lower-cost 7nm node for sustainable manufacturing.
2. **Optical Fabric:** Replacing power-hungry copper with light-speed Silicon Photonics for chip-to-chip communication.
3. **Open Architecture:** Providing a bilingual (English/Chinese) open-source repository for the global community to inspect, build, and scale.

---

## 🛠 Hardware Specifications (Target)
| Feature | Specification |
| :--- | :--- |
| **Process Node** | 7nm (FinFET) |
| **Compute Units** | 8-Chip Synchronous Tray |
| **Peak Performance** | 2.4 PetaFLOPS (FP16/BF16) |
| **Unified RAM** | 1,024 GB (1 TB) via HBM3 |
| **Interconnect** | Phoenix-Link Optical Mesh (3.2 TB/s per chip) |
| **TDP** | 300W per Unit |

---

## 📂 Project Structure
* `docs/`: Bilingual technical specifications and ISA manuals.
* `hw/`: RTL designs, floorplans, and memory controller logic.
* `sw/`: Compiler (Phoenix-C), functional simulators, and driver stacks.
* `examples/`: "Hello World" matrix math and basic AI model implementation.

---

## 🏁 Getting Started

### 1. Explore the Architecture
Read the [Instruction Set Architecture (ISA)](docs/ISA_SPEC.md) to understand how 8 Phoenix processes matrix operations deterministically.

### 2. Run the Functional Simulator
Test the execution logic of the Phoenix-Matrix instructions using our Python-based simulator:
```bash
python sw/simulator/functional_model.py