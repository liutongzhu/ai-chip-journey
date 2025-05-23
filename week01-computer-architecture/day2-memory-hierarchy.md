# 📘 Day 2: 存储层级结构与 Cache 原理 (Memory Hierarchy and Cache)

## 🎯 学习目标

- 理解计算机的存储系统是分层结构
- 掌握 Cache（缓存）的作用与类型（L1、L2、L3）
- 学会分析访问延迟、容量、局部性原理等关键特性
- 绘制存储层级金字塔图

---

## 🧠 知识要点

### 🔹 存储层级结构

从速度快到慢，容量小到大，成本高到低，依次是：

- 寄存器（Register）
- 一级缓存（L1 Cache）
- 二级缓存（L2 Cache）
- 三级缓存（L3 Cache）
- 主存（DRAM）
- 固态硬盘（SSD）
- 磁盘（HDD）
- 远程存储（如云存储）

### 🔹 延迟示意（估算）

| 存储层级 | 访问延迟（cycles） | 容量（示意） |
|----------|--------------------|---------------|
| Register | 1                  | 几十 B        |
| L1 Cache | 4~5                | 32KB ~ 128KB  |
| L2 Cache | 10~20              | 256KB ~ 1MB   |
| L3 Cache | 30~50              | 几 MB         |
| DRAM     | 100~300            | 几 GB         |
| SSD      | 上千               | 数百 GB       |
| HDD      | 上万               | TB 级别       |

### 🔹 局部性原理

- 时间局部性：最近访问的数据可能很快再次访问
- 空间局部性：访问某地址的数据，附近的数据也可能被访问

---

## 📝 作业任务

### ✅ 绘制存储层级金字塔图

```
       +-------------+
       |  Register   |
       +-------------+
             ↑
       +-------------+
       |   L1 Cache  |
       +-------------+
             ↑
       +-------------+
       |   L2 Cache  |
       +-------------+
             ↑
       +-------------+
       |   L3 Cache  |
       +-------------+
             ↑
       +-------------+
       |    DRAM     |
       +-------------+
             ↑
       +-------------+
       |    SSD/HDD  |
       +-------------+
```

- 在图中注明每层的大致延迟与容量对比。
- 思考：为什么把缓存层次结构做得复杂是有必要的？

---

## 📚 推荐资料

- 《深入理解计算机系统》第 6 章
- [Cache Memory - GeeksforGeeks](https://www.geeksforgeeks.org/cache-memory-in-computer-organization/)
- [YouTube: Computer Memory Hierarchy Explained](https://www.youtube.com/results?search_query=computer+memory+hierarchy)