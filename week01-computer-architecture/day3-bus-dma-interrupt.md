# Day3: 总线结构与 I/O 设备通信 | Bus Architecture & I/O Communication

## 🎯 学习目标 | Learning Objectives

- 理解数据总线、地址总线、控制总线的作用和协作
- 掌握 DMA（直接内存访问）和中断的基本原理
- 能用伪代码描述中断处理流程

---

## 📚 核心知识点 | Key Concepts

### 1. 总线结构简介 (Bus Architecture)

在一个计算机系统中，**总线** 是连接各个部件（CPU、内存、I/O 设备）的通信通道。总线通常包括三种类型：

- **数据总线（Data Bus）**：传输实际的数据。
- **地址总线（Address Bus）**：传输内存或设备的地址。
- **控制总线（Control Bus）**：传输控制信号，如读写信号、中断请求等。

### 2. DMA（Direct Memory Access）

**DMA 是一种让 I/O 设备在不占用 CPU 的情况下直接访问内存的机制。**

#### DMA 工作流程：

1. CPU 配置 DMA 控制器（源地址、目标地址、数据长度）
2. DMA 控制器开始传输数据（无需 CPU 干预）
3. DMA 完成后，向 CPU 发出中断通知

### 3. 中断机制（Interrupt）

**中断是 I/O 设备主动通知 CPU 某一事件已发生的一种机制**，可打断 CPU 正在进行的程序。

#### 中断流程简述：

1. 设备触发中断信号（IRQ）
2. CPU 当前指令完成后响应中断
3. 保存上下文（PC、寄存器）
4. 跳转到中断服务程序（ISR）
5. ISR 执行完成后恢复上下文，继续主程序

---

## 🔧 示例伪代码：中断处理流程

```c
// 假设我们有一个简化的嵌入式系统中断伪代码
void main() {
    enable_interrupts();  // 允许中断
    while (true) {
        do_normal_work();  // 执行主程序
    }
}

// 中断服务程序（ISR）
void interrupt_handler() {
    save_context();              // 保存 CPU 状态
    if (interrupt_source == IO_DEVICE) {
        handle_io_device_event();  // 处理中断来源
    }
    clear_interrupt_flag();     // 清除中断标志
    restore_context();          // 恢复 CPU 状态
    return_from_interrupt();    // 返回中断前的位置
}
```

---

## ✍️ 作业建议 | Suggested Practice

- 手绘一张总线结构图（标出数据/地址/控制总线的方向）
- 对比轮询 vs 中断的 I/O 方式的优缺点
- 写出一段你理解的 DMA 工作过程

---

## 📖 推荐阅读 | Recommended Reading

- 《深入理解计算机系统》第 6 章：I/O 系统
- 《Computer Organization and Design》by Patterson & Hennessy
