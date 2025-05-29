# Day 17: 存储子系统设计

## 🎯 学习目标
- 理解各类存储器特点
- 了解 DMA 控制与数据搬运路径

## 一、存储器对比

| 类型 | 带宽 | 延迟 | 功耗 | 适用 |
|------|------|------|------|------|
| SRAM | 高   | 低   | 高   | Cache |
| DRAM | 中   | 中   | 中   | 主存 |
| HBM  | 极高 | 中   | 高   | 高性能 AI |
| Flash| 低   | 高   | 低   | ROM |

## 二、DMA（Direct Memory Access）
- CPU 配置 DMA 后可将数据块搬运至 NPU 不占用 CPU

## 三、NPU 数据访问路径图
```
[DRAM] → [DMA] → [SRAM] → [NPU] → [SRAM] → [DRAM]
```

