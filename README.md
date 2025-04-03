# NASSCOMM-VSD-Soc-Design-Program
Welcome to the Digital VLSI Soc Design and Planning Program conducted by VLSI SYSTEM DESIGN.This programs gives a overview of RTL to GDSII glow through rigorous lab exercises with hands on experience in physical design using Open Source EDA tools to students.

## DAY 1
### Overview of QFN-48 Chip,Pads,Core,Die and IP's
The QFN-48 (Quad Flat No-lead) package is a surface-mount integrated circuit (IC) package with 48 pins. It is commonly used for applications requiring a small form factor, excellent thermal performance, and efficient electrical connections.
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/QFN-48.png"/>

### Fundamental Terminologies related to structure and development of Integtaed Circuit
1.Core:
* The core of chip refers to functional logic of IC/chip.
* By functional logic I mean it includes combinational logic,sequental logic,memory,ALU and many more which help in data computation and processing.
* Core is typically surrounded by pads and clock distribution network.
  
2.Pads:
* Pads are metallic contact points which are used to connect die to the outside world and they are also located at periphery of die and interface with die.
* Types of pads
   * Power/Ground Pads-Supply power and ground to the chip
   * Signal Pads-Carry input/output signals
   * Test Pads-Used for debugging and testing

3.Die:
* The die is semiconductor piece cut from silicon wafer which consists of core,pads and other functional blocks and this die is fabricated using CMOS process
* The size of die depends on varios factors such as design complexity,technology node and requied functionality.
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Die%2CCore%2CIP's.png"/>

4.Intellectual Property:
  
* These are predesigned and reusable verified circuit blocks used in chip design.
* Types of IP:
    * Soft IP: RTL-based (e.g., Verilog/VHDL code) that can be synthesized.
   * Firm IP: Netlist-level IP with some degree of customization.
   * Hard IP: Fully placed and routed, ready for integration.
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/IP's%20Foundry.png"/>

### RISC-V Architecture
RISC-V is an open-source, modular, and extensible instruction set architecture (ISA) based on reduced instruction set computing (RISC) principles, allowing designers to create custom processors for various applications, from embedded systems to high-performance computing. RISC-V architecture allows designers to customize and build their processor in a way that's tailored to their target end applications.
An Instruction Set Architecture (ISA) is the interface between hardware (processor) and software (programs). It defines the set of instructions, registers, data types, memory access methods, and execution model that a processor can execute.
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/RISC-V.png"/>

### From Software Applications to Hardware
This image gives a overview that actually how software apps comunicate with hardware
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Software%20Applications.png"/>
