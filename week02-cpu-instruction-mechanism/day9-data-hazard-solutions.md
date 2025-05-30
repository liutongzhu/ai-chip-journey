# Day 9：数据冒险与解决策略（Data Hazards & Solutions）

本节将深入讲解 **CPU 流水线中的数据冒险（Data Hazard）**，并介绍三种常用的解决方案：

- 前递（Forwarding）
- 冒险检测单元（Hazard Detection Unit）
- 停顿插入（Stall / Bubble）

---

## 🚧 什么是数据冒险？

当一条指令依赖于前面指令的执行结果，但前面的指令还没完成时，就会产生数据冒险。

### 举例说明：

假设有以下三条 MIPS 指令：

```assembly
1: ADD R1, R2, R3   ; R1 = R2 + R3
2: SUB R4, R1, R5   ; R4 = R1 - R5
3: AND R6, R1, R7   ; R6 = R1 & R7
```

第二、三条指令都依赖第一条指令的结果 R1。但 R1 只有在 EX/MEM 阶段才产生结果。

如果没有处理好这个依赖关系，就可能在 ID 阶段使用了还没写入的旧值，导致计算出错。

---

## 🛠️ 解决方法一：前递（Forwarding）

**前递** 通过增加数据通路，把 ALU 的输出直接“转发”到需要使用结果的下一条指令。

### 前递路径：

```text
EX/MEM.ALUResult ────────────┐
                             ▼
                         Forwarding MUX ─→ ALU（下一条指令用）
```

### 前递逻辑示意：

```verilog
if (EX/MEM.RegWrite && (EX/MEM.Rd != 0) && (EX/MEM.Rd == ID/EX.Rs)) {
    ForwardA = 10; // 使用前递结果代替寄存器读取
}
```

---

## 🧠 解决方法二：冒险检测单元

当 ID 阶段检测到后续指令依赖前面的 load 指令时，无法通过前递解决（load 结果在 MEM 阶段产生），就需要 **插入冒险检测逻辑**，主动停顿流水线。

### 示例：

```assembly
1: LW R1, 0(R2)
2: ADD R3, R1, R4   ; 冒险！R1 还未准备好
```

### 插入停顿：

```text
1: LW   R1, 0(R2)
2: NOP               ← 插入一条空指令（Bubble）
3: ADD  R3, R1, R4
```

---

## 🚥 解决方法三：插入停顿（Stall）

在无法前递的情况下，通过暂停部分流水级并插入 Bubble（气泡）来让上游指令“等一等”。

这种方式虽然保证了正确性，但会牺牲指令吞吐率。

---

## ✅ 小结

| 解决方式     | 是否牺牲性能 | 适用场景                     |
|--------------|--------------|------------------------------|
| 前递         | 否           | 计算类指令依赖               |
| 冒险检测单元 | 否           | 自动插入停顿，更智能         |
| 手动插入停顿 | 是           | 特殊指令场景，软件处理       |

---

## 📌 练习：尝试识别以下代码中的数据冒险并画出依赖图

```assembly
LW R1, 0(R2)
ADD R3, R1, R4
SUB R5, R3, R6
```

- 哪些冒险可以前递解决？
- 哪些需要停顿？

---
