# Day 15: SoC 总体架构认知

## 🎯 学习目标
- 区分 SoC、CPU、MCU 的概念
- 理解 SoC 的模块组成及边缘 AI 芯片架构

## 一、SoC vs CPU vs MCU
| 类型 | 功能特点 | 应用领域 |
|------|----------|----------|
| CPU | 通用计算核心 | PC、服务器 |
| MCU | 内置 Flash、IO，适合控制类任务 | 传感器控制、电器 |
| SoC | 集成 CPU、NPU、DSP、IO 等所有模块 | 手机、AI 芯片 |

## 二、SoC 模块组成
- **CPU**：控制、计算核心
- **NPU**：AI 推理加速
- **DSP**：信号处理任务
- **Memory**：SRAM, DRAM, Cache 等
- **IO**：外设接口（UART, SPI, GPIO 等）
- **Power**：电源管理模块

## 三、典型 AI SoC 框图（示意）
```
+------------------------------+
|          SoC 芯片结构        |
| +---------+  +------------+ |
| |  CPU    |  |   NPU      | |
| +---------+  +------------+ |
| |  DSP    |  |   SRAM     | |
| +---------+  +------------+ |
| |  IO     |  | DRAM Ctrl  | |
| +--------------------------+|
+------------------------------+
```

