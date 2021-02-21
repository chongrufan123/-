# verilog

## 基本信息
### verilog的主要运用
- ASCI FPGA工程师编写可综合的RTL代码
- 高抽象级系统仿真进行系统结构开发
- 测试工程师用于编写各种层次的测试程序
- 用于ASIC和FPGA单元或更高层次的模块的模型开发

verilog适合系统级、算法级、寄存器传输级、逻辑、门级和电路开关级的设计

### ip核
#### 软核
有功能的描述，但是没有对应的工艺，只能调用

#### 硬核
有功能的描述，也有对应的工艺

### 自顶而下的设计流程
1. 用verilog设计文件
2. 进行HDL功能仿真
3. 综合
4. 进行电路的优化布局布线
5. 布线后进行实际的仿真，会考虑真正的门电路的延迟效果
6. 输出电路制造工艺文件

## 语法
### 电路抽象级别
> 电路可以进行不同级别的描述

1. 系统级：用高级语言实现设计模块的外部性能
2. 算法级：用高级语言结构实现设计算法的模型
3. RTL级（最常用）：描述数据在寄存器之间的流动和如何处理，控制这些数据流动的模型
4. 门级：描述逻辑门和逻辑门之间的连接
5. 开关级：三极管和存储节点和他们之间连接的模型

### 基本概念
以下为一个基本的verilog模块

    module 模块名(输入输出端口列表):
        parameter N = 8; #参数，表示数据位数
        output [N:1] out; #输入输出的外部特性
        input [N:1] in0, in1;
        input sel;      #一位表达式
        assign out = sel?in1:in0;   #逻辑功能描述-描述内部特征
    endmodule   #module开始，endmodule结束表示一个模块

> wire类型  导线类型，没有存储功能，只能参与到组合逻辑的设计中来
> reg类型    寄存器类型，有存储功能，可以参与到时序逻辑的运算
    
```
    # 以下module表示一个16位加法器
    module counter(q, cont, reset, cin, clk);
        parameter N = 4;
        output [N:1]q;
        output cont;
        input reset, cin, clk;
        reg [N:1]q;
        always @(posedge clk)   #posedge表示上升沿， negedge表示下降沿
            begin
                if (reset) q<=0;
                else
                    q<=q + cin;
            end
        assign cout= &q && cin;  #&q表示q的所有位相与，&&表示与
    endmodule
```    


