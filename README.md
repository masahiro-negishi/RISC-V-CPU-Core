# RISC-V CPU Core
## About
This project implements CPU Core which can execute all the instructions of base RISC-V instruction set (RV32I). This core executes each instruction in a single clock. 

## Diagram
```mermaid
graph LR
  PC --> D-FF
  D-FF --> +1 & IMem & Adder1[Add] & Adder2[Add]
  +1 --> PC
  IMem --> Dec
  Dec --$rs1--> RF
  Dec --$rs2--> RF
  Dec --$rd--> RF
  Dec --$imm--> MX1[MX] & Adder1
  Adder1 & Adder2 --> PC
  RF --> MX1 & Adder2
  RF --$op2--> ALU & DMem
  MX1 --$op1--> ALU
  ALU --> DMem & MX2[MX]
  DMem --> MX2
  MX2 --> RF
```

## Reference
This project is based on a edX course [Building a RISC-V CPU Core](https://learning.edx.org/course/course-v1:LinuxFoundationX+LFD111x+1T2021/home) served by the Linux foundation.
