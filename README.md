# 1.OVERVIEW
The 16-bit Arithmetic Logic Unit (ALU) is a fundamental component in digital systems designed to perform arithmetic and logic operations. This ALU accepts two 16-bit input operands, executes operations such as addition, subtraction, AND, OR, XOR, NOT, and shift operations, and provides a 16-bit output. It also generates status flags to indicate critical conditions such as carry-out, zero, negative, and overflow.

# 2.FUNCTIONALITY
The ALU performs the following basic arithmetic and logic operations:
ADD: Addition of two 16-bit numbers.
SUB: Subtraction of two 16-bit numbers.
AND: Bitwise AND between two 16-bit numbers.
OR: Bitwise OR between two 16-bit numbers.
XOR: Bitwise XOR between two 16-bit numbers.
NOT: Bitwise NOT on the first 16-bit number.
SLL: Shift left logical by one bit.
SRL: Shift right logical by one bit.
The ALU runs at a clock frequency of 100 MHz, ensuring high-speed computation in applications requiring efficient arithmetic and logic processing.

# 3.Block Diagram
The architecture of the ALU consists of several functional units connected together:
Input Unit: Accepts two 16-bit input operands (A and B) from the system.
Arithmetic Logic Unit: Carries out arithmetic and logic operations based on control signals.
Output Unit: Produces a 16-bit result based on the selected operation.
Status Flag Generator: Generates four status flags – Carry-Out (C), Zero (Z), Negative (N), and Overflow (V).
Control Unit: Decodes the operation based on control signals.
![image](https://github.com/user-attachments/assets/d998ae35-808b-47bd-8f77-ecfe30ad7895)

