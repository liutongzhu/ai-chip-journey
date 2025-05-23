# Day 6: CPU 五级流水线原理  
## 📚 学习目标

- 掌握五级流水线各阶段（IF/ID/EX/MEM/WB）的核心功能
- 理解流水线冒险问题的成因与解决方案
- 能绘制 5 指令的流水线执行时间图（甘特图）

---

## 🧠 五级流水线阶段详解

| 阶段 | 英文全称 | 功能 |
|------|----------|------|
| **IF** | Instruction Fetch | 从内存中取指令到指令寄存器 |
| **ID** | Instruction Decode | 译码指令并读取寄存器操作数 |
| **EX** | Execute | 执行算术/逻辑运算或地址计算 |
| **MEM** | Memory Access | 读写内存（如`LDR/STR`指令） |
| **WB** | Write Back | 将运算结果写回目标寄存器 |


---

## ⚠️ 流水线冒险（Hazard）问题

### 1️⃣ **结构冒险**
- **成因**：硬件资源冲突（如同时读写内存）
- **解决**：哈佛架构（指令/数据内存分离）或插入等待周期

### 2️⃣ **数据冒险**
- **成因**：数据依赖导致未就绪（如`ADD R1,R2,R3`后接`SUB R4,R1,R5`）
- **解决**：前递（Forwarding）或插入空操作（NOP）

### 3️⃣ **控制冒险**
- **成因**：分支跳转导致预取错误指令（如`BEQ`后指令无效）
- **解决**：分支预测或延迟槽技术

---

## 🛠️ 流水线时间图（5 指令甘特图）

### 假设指令序列：  
`I1: ADD R0,R1,R2`  
`I2: SUB R3,R0,R4`（依赖I1结果）  
`I3: LDR R5, [R6]`  
`I4: BEQ label`（分支跳转）  
`I5: AND R7,R8,R9`

### 理想流水线时序（无冒险）：
```plaintext
时钟周期 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9  
---------|---|---|---|---|---|---|---|---|---
I1      |IF |ID |EX |MEM|WB |   |   |   |  
I2      |   |IF |ID |EX |MEM|WB |   |   |  
I3      |   |   |IF |ID |EX |MEM|WB |   |  
I4      |   |   |   |IF |ID |EX |MEM|WB |  
I5      |   |   |   |   |IF |ID |EX |MEM|WB  
```

---
## ✅ 今日小结
- 流水线通过指令级并行提升吞吐率
- IF-ID-EX-MEM-WB 是经典五级划分
- 冒险问题会显著降低流水线效率
- 前递/预测/缓存等技术可缓解冒险

---
## 🔍 拓展阅读
- 《计算机体系结构：量化研究方法》第3章
- MIPS 流水线冒险处理机制
- RISC-V 流水线设计白皮书
