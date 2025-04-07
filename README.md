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
This image gives a overview that actually how software apps comunicate with hardware.There is a system software layer between app and hardware.The apps interface with system software and this layer converts them into a language which hardware can understand i.e binary language.

The System Software consists of different layers:

 1. O.S : Other than the general operations like Handling I.O operations, Allocating Memory, Low level System Functions the O.S converts the Application software to respected C,C++,Java etc.. codes.

 2. Compiler : The compiler takes output of O.S as input and converts the codes in C,C++,Java etc.. into Instruction set(.exe files). These instructions will be dependent on type of hardware used.

 3. Assembler : Assembler converts the .exe files into binary language and provides it to the hardware, and hardware performs the respective operations.

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Software%20Applications.png"/>

### Open-Source Digital ASIC Design
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Open%20Source%20ASIC.png"/>
Components required for Open-Source Digital ASIC Design are

1.RTL Design - In RTL design the behavior of a digital circuit is described using hardware description languages (HDLs) like Verilog or VHDL.

2.EDA Tools - Tools that help take your design from RTL all the way to GDSII (final layout),making chip ready for fabrication by verifying functionality at every stage.

3.PDK Data - The PDK contains technology-specific data provided by the foundry. This includes:
    
  * Design rules (minimum spacing, width, etc.)
  * Transistor models
  * Standard cell libraries
  * DRC/LVS rule decks
  * Layer information

### Simplified RTL to GDSII Flow
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Simplified%20RTL%20TO%20GDSII%20Flow.png"/>

1.Synthesis – Convert RTL to a gate-level netlist using standard cells.
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Synthesis.png"/>
2.Floorplanning and Powerplanning -
  * Floorplanning defines the chip's physical layout—core size, IO pin placement, and cell rows—ensuring logical blocks fit efficiently.
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Floorplanning.png"/>

  * Power planning builds power rings and metal straps to distribute VDD/VSS across the chip, ensuring reliable power delivery to all cells.
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Power%20Planning.png"/>
3.Placement - Place standard cells inside the defined floorplan.

  * Global Placement: for optimal position of cells
  * Detailed Placement: for legal positions
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Placement.png"/>
4.CTS - Insert buffers/inverters to distribute the clock signal uniformly so that there is clock skew.
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/CTS.png"/>
5.Routing - Connect all placed cells with metal wires while obeying design rules.

  * Global Routing - Global routing plans approximate wire paths between cells and blocks across routing tracks.
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Global%20Routing.png"/>

  * Detailed Routing - Detailed routing assigns exact metal layers and wire geometries to connect pins while meeting design rules.
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Detailed%20Routing.png"/>
6.Sign Off - Physical (DRC, LVS) and Timing verifications (STA).

### Open-source EDA tools
For step by step execution of OpenLANE ASIC flow various open-source EDA tools are used

| Column 1 | Column 2 |
|----------|----------|
| RTL synthesis and technology mapping | yosys,abc|
| Floorplan         |init_fp,io_placer,tap_decap_or          |
| Placement         |  RePLace        |
| STA         | OpenSTA         |
| CTS         | TritonCTS         |
| Routing         | TritonRoute         |
| DRC checks & GDSII generation         |magic,layout          |

###### NOTE: In general ASIC design flow  pdn generation is done after floorplan but in OpenLANE ASIC design flow pdn generation is done after cts and before routing due to following reasons
1.OpenLane uses automated flows (OpenROAD), which:

  * Insert clock buffers automatically.
  * Don’t fully account for pre-existing PDN early on.

2.If PDN is generated too early:
  * CTS might fail to insert buffers due to metal blockage.
  * Routing congestion or violations may happen.

#### Tools demonstration from RTL to GDSII in linux
The path of directory in which we will invoke our OpenLANE is

 ```
 vsduser@vsdsquadron:~/Desktop/work/tools/openlane_workshop_dir/openlane/
```
Now for invoking the OpenLANE and preparing the design use the followng commands
```
docker
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a
```
<img src = "https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20110042.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20110339.png"/>

After preparing design a runs folder will be created inside picorv32a folder
<img src = "https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20110518.png"/>

After design preparation is complete run synthesis

``` 
run_synthesis
```
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20111144.png"/>
Now once the synthesis is complete we will calculate flop ratio 
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20111051.png"/>

```
Flop ratio = Number of D Flip flops 
             ______________________
             Total Number of cells
```

```
dfxtp_4 = 1613,
Number of cells = 14876,
Flop ratio = 1613/14876 = 0.1084 = 10.84%
```

Now we can see synthesis results and reports

In synthesis results `.v` will be created which shows our design is converted into gate level netlist
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20111330.png"/>
Now these are synthesis reports
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20111418.png"/>
One such report we are looking is `1-yosys_4.stat.rpt`
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20111501.png"/>

## DAY 2
### FLOORPLANNNING AND PLACEMENT

1.Utilization Factor & Aspect Ratio  

While doing floorplanning we need to consider 2 parameters which will help us to decide about die,core of the chip

```
Utilisation Factor =  Area occupied by netlist
                     __________________________
                        Total area of core
```

```
Aspect Ratio =  Height
               ________
                Width
```

 Utilisation Factor of 1 signifies 100% utilisation of core and no other cell can be placed. However, practically, the Utilisation Factor is 0.5-0.6. 

Aspect ratio of 1 implies that the chip is square shaped as (h==w). Any value other than 1 implies rectanglular chip.

2.Pre placed cells

The concept of pre-placing cells is nothing but reusing already designed blocks by not designing them again and again.Pre-placed cells are IPs comprising large combinational logic which once placed maintain a fixed position.Eg memory blocks,IP's 

3.Decoupling Capacitors

Generally these pre-placed blocks will be high-power draining blocks.Pre-placed cells must then be surrounded with decoupling capacitors (decaps).Decaps are huge capacitors charged to power supply voltage and placed close the logic circuit. Their role is to decouple the circuit from power supply by supplying the necessary amount of current to the circuit. They pervent crosstalk and enable local communication

4.Power Planning

Unlike pre-placed macros, individual blocks on the chip typically can't have dedicated decap cells. To maintain stable power delivery, effective power planning ensures that each block is equipped with its own VDD and VSS pads, which are tied into the chip’s horizontal and vertical power mesh.

5.Pin Placement

The netlist outlines how logic gates are connected. The area between the core and the die is used to place the chip’s pins. The connectivity described in Verilog or VHDL helps determine where the I/O pads for each pin should be located. After that, logical placement of pre-placed macros is carried out to distinguish their regions from the pin placement area.

#### FLORPLAN IN EDA

