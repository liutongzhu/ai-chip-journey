# Day 32 - 数据通路设计基础
## 🔧 数据通路设计基础

### 基本模块
- 运算单元
- 寄存器
- 复用器
- 选择器

### 学习任务
- 构建一个执行乘法 + 累加的简化 MAC 单元（Verilog 实现）
### 👶 小白也能懂：数据怎么“走通道”？
数据通路就像是“食物加工流水线”：

- 运算单元 = 炒菜锅（负责算）
- 寄存器 = 放菜的盘子（存一下）
- 复用器/选择器 = 分菜的服务员（决定去哪）

我们搭建一条“乘法再加法”的流水线，比如：2×3→结果是6，然后6+1=7。