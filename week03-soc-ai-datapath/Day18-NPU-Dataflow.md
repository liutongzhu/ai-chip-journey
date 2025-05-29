# Day 18: AI 数据通路建模（基础）

## 🎯 学习目标
- 掌握 NPU 数据流建模基本概念
- 用流程图描述典型卷积过程

## 一、卷积数据流流程图
```
Input Tensor
     ↓
On-Chip Buffer（IFMap）
     ↓
Matrix Multiply Unit (MMU)
     ↓
ReLU 激活函数
     ↓
On-Chip Buffer（OFMap）
     ↓
写回到内存
```

## 二、通路解释
- IFMap：输入特征图
- MMU：执行矩阵乘法
- ReLU：激活非线性操作
- OFMap：输出特征图存储

