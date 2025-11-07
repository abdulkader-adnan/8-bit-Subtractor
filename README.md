# 8-bit Adder/Subtractor Circuit

This is a digital logic design project for an 8-bit adder/subtractor circuit, completed as part of coursework for Misr International University.

**Authors:**
* Mohamed Sherif (2023/03849)
* Abdulkader Adnan (2023/07019)

## 📋 Project Overview

This circuit is capable of performing 8-bit binary addition and subtraction using a single control input (**M**).

* **Addition (M=0):** The circuit functions as a standard 8-bit ripple-carry adder.
* **Subtraction (M=1):** The circuit performs subtraction using the 2's complement method.

## ⚙️ How It Works

The functionality is controlled by a single switch, **M**. The circuit is built by cascading 8 full-adders.

### Subtraction (M=1)

When **M=1**, the circuit computes $A - B$ by converting the operation to $A + (\text{2's complement of } B)$.

1.  **1's Complement:** The circuit uses 8 XOR gates. One input for each XOR gate is a bit from $B$, and the other input is the control signal **M**.
    * When $M=1$, the XOR gate acts as an inverter (NOT gate), outputting $B'$. This step generates the 1's complement of B.
    * The logic is: $F(M=1, B) = (1)'B + (1)B' = (0)B + (1)B' = B'$

2.  **Adding One (2's Complement):** To complete the 2's complement ($B' + 1$), the control signal **M** (which is 1) is also fed into the initial carry-in ($C_{in}$) of the first full-adder.

3.  **Final Addition:** The 8 full-adders then add $A$ and the 2's complement of $B$. The final carry-out bit is ignored.

### Addition (M=0)

When **M=0**:
1.  The XOR gates output $B$ unchanged (since $F(M=0, B) = (0)'B + (0)B' = B$).
2.  The initial carry-in ($C_{in}$) is 0.
3.  The circuit performs a standard 8-bit addition: $A + B$.

## 🛠️ Components

### Logical Components
* **8 Full-Adders**: Each full-adder is built from:
    * 1 XOR gate (3-input) for the Sum ($S$)
    * 3 AND gates
    * 1 OR gate (3-input) for the Carry-out ($C_{out}$)
* **8 XOR Gates** (2-input): Used as controlled inverters to generate the 1's complement.

### Physical Implementation (ICs)
The document provides datasheets for implementing this circuit using standard ICs:
* **IC SN74LS83N (7483):** A 4-bit binary full-adder. (Two of these would be required for an 8-bit implementation).
* **IC SN74HC86N (7486):** Contains four 2-input XOR gates.

## 📄 Document Contents

This repository contains the project documentation, which includes:
* Truth tables for a half-adder and full-adder.
* Boolean expressions for $S$ and $C_{out}$.
* Circuit diagrams for half-adders, full-adders, and the complete 8-bit adder-subtractor.
* A step-by-step example of 8-bit subtraction using 2's complement.
* IC pinout diagrams for the 7483 and 7486 chips.
