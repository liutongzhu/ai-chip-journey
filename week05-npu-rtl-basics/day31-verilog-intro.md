# Day 31 - Verilog 入门语法速学
## 📘 Verilog 入门语法

### 常用结构
- `module` 定义模块
- `assign` 组合逻辑赋值
- `always` 时序逻辑块
- `if/case` 控制语句

### 学习任务
- 编写第一个 Verilog 模块：2 输入加法器
### 👶 小白也能懂：Verilog 是什么？
Verilog 就像是“计算电路的搭积木语言”。你告诉它要做一个“加法器”，它就帮你在芯片里真的搭出那个逻辑。

```verilog
module adder(input a, input b, output sum);
  assign sum = a + b;
endmodule
```
这段代码的意思就是：“我想要一个叫 adder 的模块，它有两个输入，一个输出，输出就是它们的和。”

就像给小机器人写说明书，告诉它怎么加法。