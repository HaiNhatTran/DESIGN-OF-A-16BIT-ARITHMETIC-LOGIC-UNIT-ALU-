# 1.OVERVIEW
The 16-bit Arithmetic Logic Unit (ALU) is a fundamental component in digital systems designed to perform arithmetic and logic operations. This ALU accepts two 16-bit input operands, executes operations such as addition, subtraction, AND, OR, XOR, NOT, and shift operations, and provides a 16-bit output. It also generates status flags to indicate critical conditions such as carry-out, zero, negative, and overflow.

# 2.FUNCTIONALITY
The ALU performs the following basic arithmetic and logic operations:
- ADD: Addition of two 16-bit numbers.
- SUB: Subtraction of two 16-bit numbers.
- AND: Bitwise AND between two 16-bit numbers.
- OR: Bitwise OR between two 16-bit numbers.
- XOR: Bitwise XOR between two 16-bit numbers.
- NOT: Bitwise NOT on the first 16-bit number.
- SLL: Shift left logical by one bit.
- SRL: Shift right logical by one bit.
The ALU runs at a clock frequency of 100 MHz, ensuring high-speed computation in applications requiring efficient arithmetic and logic processing.

# 3.Block Diagram
The architecture of the ALU consists of several functional units connected together:
- Input Unit: Accepts two 16-bit input operands (A and B) from the system.
- Arithmetic Logic Unit: Carries out arithmetic and logic operations based on control signals.
- Output Unit: Produces a 16-bit result based on the selected operation.
- Status Flag Generator: Generates four status flags – Carry-Out (C), Zero (Z), Negative (N), and Overflow (V).
- Control Unit: Decodes the operation based on control signals.
![image](https://github.com/user-attachments/assets/d998ae35-808b-47bd-8f77-ecfe30ad7895)

# 4.I/O Interfaces
Input I/O:
- A[15:0]: 16-bit operand input A.
- B[15:0]: 16-bit operand input B.
- OP_SEL[2:0]: 3-bit control input to select the operation (0-7).
Output I/O:
- RESULT[15:0]: 16-bit result from ALU.
- C: Carry-Out flag.
- Z: Zero flag.
- N: Negative flag.
- V: Overflow flag.

 # 5.Detailed Functional Description
ADD Operation:
- The ALU adds operand A and operand B, and outputs the result in RESULT. The status flags are updated based on the arithmetic addition (Carry-Out, Zero, Negative, Overflow).
SUB Operation:
- The ALU performs subtraction of operand A from operand B, producing the result in RESULT. The status flags reflect the subtraction (Carry-Out, Zero, Negative, Overflow).
AND Operation:
- The ALU performs bitwise AND between operand A and operand B, with the result in RESULT.
OR Operation:
- The ALU performs bitwise OR between operand A and operand B, with the result in RESULT.
XOR Operation:
- The ALU performs bitwise XOR between operand A and operand B, with the result in RESULT.
NOT Operation:
- The ALU performs bitwise NOT on operand A, with the result in RESULT.
SLL Operation:
- The ALU shifts operand A left by one bit, with the result in RESULT.
SRL Operation:
- The ALU shifts operand A right by one bit, with the result in RESULT.
  
Status Flag Generation:
- Carry-Out (C): Indicates if there was a carry-out from the most significant bit after the operation.
- Zero (Z): Indicates if the result is zero.
- Negative (N): Indicates if the result is negative.
- Overflow (O): Indicates if there was an arithmetic overflow.

# 6.Explanation of Flag Functionality in the 16-bit ALU Design
1. carry_out (Carry-Out Flag):
   
Purpose: The carry_out flag checks whether there is a carry (or borrow) generated during addition or subtraction.

For addition (ADD), carry_out represents the 17th bit (most significant bit) of the addition result.

For subtraction (SUB), it indicates if the subtraction resulted in a borrow.

The calculation includes the carry/borrow in the 17th bit (carry_out), while the lower 16 bits are stored in result.

2. zero (Zero Flag):
Purpose: The zero flag checks if the result of the operation is zero.

If result == 16'b0, the zero flag is set to 1.

Otherwise, it remains 0.

It compares all 16 bits of result with zero. If all bits are 0, the zero flag is activated.

3. negative (Negative Flag):
Purpose: The negative flag determines the sign of the result based on the most significant bit (MSB).

If result[15] == 1, the result is negative in 2's complement representation.

Otherwise, the result is positive.

Implementation in the design:

This simply checks the MSB (15th bit) of result.

4. overflow (Overflow Flag):

Purpose: The overflow flag detects arithmetic overflow during addition or subtraction.

For addition (ADD): Overflow occurs when two numbers with the same sign are added, and the result has a different sign.

if ((a[15] == b[15]) && (result[15] != a[15])) begin
    
    overflow = 1;

end

a[15] == b[15]: Ensures the two numbers have the same sign.

result[15] != a[15]: The result has a different sign from the inputs.

For subtraction (SUB): Overflow occurs when subtracting a positive number from a negative number (or vice versa), and the result goes out of range for 16-bit representation.

if ((a[15] != b[15]) && (result[15] != a[15])) begin
    
    overflow = 1;

end

a[15] != b[15]: Ensures the two numbers have different signs.

result[15] != a[15]: The result does not have the expected sign based on a.
