# NASSCOMM-VSD-Soc-Design-Program
Welcome to the Digital VLSI Soc Design and Planning Program conducted by VLSI SYSTEM DESIGN.This programs gives a overview of RTL to GDSII glow through rigorous lab exercises with hands on experience in physical design using Open Source EDA tools to students.

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

### Open-Source Digital ASIC Design Flow
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

  * Global Placement: It identifies the most efficient positions for all cells, though the initial placement may include overlaps or violations. The optimization is based on minimizing the half-perimeter wire 
    length (HPWL) to reduce overall routing complexity.
  * Detailed Placement: It adjusts the positions of cells after global placement to ensure they follow design rules and are legally placed without overlaps.
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Placement.png"/>
4.CTS - Insert buffers/inverters to distribute the clock signal uniformly so that there is clock skew.
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/CTS.png"/>
5.Routing - Connect all placed cells with metal wires while obeying design rules.

  * Global Routing: Global routing plans approximate wire paths between cells and blocks across routing tracks.
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Global%20Routing.png"/>

  * Detailed Routing: Detailed routing assigns exact metal layers and wire geometries to connect pins while meeting design rules.
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

**NOTE: In general ASIC design flow  pdn generation is done after floorplan but in OpenLANE ASIC design flow pdn generation is done after cts and before routing due to following reasons**

1.OpenLane uses automated flows (OpenROAD), which:

  * Insert clock buffers automatically.
  * Don’t fully account for pre-existing PDN early on.
    
2.If PDN is generated too early:
  * CTS might fail to insert buffers due to metal blockage.
  * Routing congestion or violations may happen.

### Tools demonstration from RTL to GDSII in linux
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

### FLOORPLANNNING AND PLACEMENT

`1.Utilization Factor & Aspect Ratio`  

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

`2.Pre placed cells`

The concept of pre-placing cells is nothing but reusing already designed blocks by not designing them again and again.Pre-placed cells are IPs comprising large combinational logic which once placed maintain a fixed position.Eg memory blocks,IP's 

`3.Decoupling Capacitors`

Generally these pre-placed blocks will be high-power draining blocks.Pre-placed cells must then be surrounded with decoupling capacitors (decaps).Decaps are huge capacitors charged to power supply voltage and placed close the logic circuit. Their role is to decouple the circuit from power supply by supplying the necessary amount of current to the circuit. They pervent crosstalk and enable local communication

`4.Power Planning`

Unlike pre-placed macros, individual blocks on the chip typically can't have dedicated decap cells. To maintain stable power delivery, effective power planning ensures that each block is equipped with its own VDD and VSS pads, which are tied into the chip’s horizontal and vertical power mesh.

`5.Pin Placement`

The netlist outlines how logic gates are connected. The area between the core and the die is used to place the chip’s pins. The connectivity described in Verilog or VHDL helps determine where the I/O pads for each pin should be located. After that, logical placement of pre-placed macros is carried out to distinguish their regions from the pin placement area.

#### FLOORPLAN IN EDA

Important files which are considered while doing floorplanning are 

1. ```floorplan.tcl``` 
2. ```conifg.tcl```
3. ```sky130A_sky130_fd_sc_hd_config.tcl```
   
Their priority order is also like this 1 with highest priority and 3 with lowest priority.Like clock port is declared in all the 3 files so clk port value which `floorplan.tcl` is having will be considered.

Now these files are shown in the toolbox

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20111808.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20111845.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20113828.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20114108.png"/>

Now these are floorplan switches which are defined in the `README.md file`

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20112117.png"/>

Now

`run_floorplan`


<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20112949.png"/>

Post the floorplan run, a .def file is created

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20114550.png"/>

For viewing floorplan magic is invoked with the help of following command in floorplan folder inside results directory

```magic -T /Desktop/work/tools/openlane_workshop_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged..lef def read picorv32a.floorplan.def &```

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20122405.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20122553.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20122842.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20123439.png"/>

#### PLACEMENT IN EDA

Now once your floorplan is completed do placememt.As you know placement will fill the defined floorplan with standard cells.

Now

```run_placemement```
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20140014.png"/>

For viewing placement magic is invoked with the help of following command in placement folder inside results directory

```magic -T /Desktop/work/tools/openlane_workshop_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged..lef def read picorv32a.placement.def &```

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20140029.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20140053.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-03%20140201.png"/>

### STANDARD CELL DESIGN FLOW
 
It involves three steps
1. Inputs: libraries, PDKs, user-defined specifications, DRC & LVS rules, SPICE models. 
2. Design steps: Circuit design, Layout design , Extraction of parasitics, Characterization .
3. Outputs: CDL (circuit description language), LEF, GDSII, extracted SPICE netlist (.cir), timing, noise and power .lib files

A SPICE DECK files includes model netlist,library files,load capcitances, how the components are connected and their values.

### STANDARD CELL LAYOUT OF INVERTER

Now our objective is to embedd a standard cell i.e inverter into our picorv32a design file

For this certain steps are fold

1. We wiil clone a repository `vsdstdcelldesign` in our `openlane` directory

```
git clone https://github.com/nickson-jose/vsdstdcelldesign
```

Now we want to see the layout of the inverter so we will open magic inside vsdstdcelldesign directory which we cloned

`magic -T sky130A.tech sky130_inv.mag &`

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-04%20233306.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-04%20233330.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-04%20234409.png"/>

We need a spice file so we need to extract it using following commands

```
extract all
ext2spice cthresh 0 rethresh 0
ext2spice
```

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-04%20235927.png"/>

Now the spice file is shown below
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-05%20002508.png"/>

Now we need to see the transition graph se wee need to run simulation by using ngpice in terminal

```
ngspice sky130_inv.spice
```
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-05%20003540.png"/>

Now for charcterizing standard cell design 4 parameters are taken into consideration

1.Rise transition: Time taken for the output to rise from 20% of max value to 80% of max value

2.Fall transition- Time taken for the output to fall from 80% of max value to 20% of max value

3.Cell rise delay = time(50% output rise) - time(50% input fall)

4.Cell fall delay = time(50% output fall) - time(50% input rise)

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-05%20003924.png"/>

According to my calculation 

 1.Rise Time =0.0638ns
 
 2.Fall Time=0.04277ns
 
 3.Cell Rise Delay=0.06092ns
 
 4.Cell Fall Delay=0.02713ns

 Now we need to see layout for that we need `.magicrc` file we need to download a folder `drc_tests.gz`

 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-05%20120754.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-05%20120816.png"/>

 this is `.magicrc file`
 
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-05%20121234.png"/>

 Now fixing poly,difusion and DRC errors
 
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-05%20121700.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-05%20134032.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-05%20134118.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-05%20134130.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-05%20135708.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-05%20140644.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20002339.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20002838.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20010559.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20011440.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20012311.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20012654.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20014117.png"/>
 <img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20014533.png"/>

 ### PRE LAYOUT TIMING ANALYSIS/POST SYNTHESIS TIMING ANALYSIS

In this section we need a LEF file from magic layout file 

First convert track.info file to grid.info

This is a track file we can see this in this location

```
cd openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130_fd_sc_hd/less tracks.info
```

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20122729.png"/>

Now open magic layout window inside vsdstdcelldesign directory

```
magic -T sky130A.tech sky130_inv.mag &
```

A requirement for ports as specified in tracks.info is that they should be at intersection of horizontal and vertical tracks.To ensure they are at intersection use this command

```
grid 0.46um 0.34um 0.23um 0.17um
```

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20123447.png"/>
Now save file as sky130vsdinv.img

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20125254.png"/>
Now write lef file in tkcon window.As you can see lef file is created
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20125841.png"/>
This is the lef file containing all information
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20130038.png"/>
Now we have new cell inverter we have to include this in our synthesis.So first we need to integrate it in picorv32 design and for that we need to copy the lef file and all the timing libraries required for analysis in our src folder
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20131040.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20131751.png"/>
Now go inside the picorv32 open `config.tcl` file.Update this file
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20132946.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20141043.png"/>

Now start again from scratch in OpenLANE so that we can whether our cell is included in our design

Use these commands 

```
docker

flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a -tag 23-03_10-48 -overwrite

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]

add_lefs -src $lefs

run_synthesis
```

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20141112.png"/>
Now we can see vsdinv is include in our design when we completed the synthesis stage and there is a huge value of total negative slack and worst negative slack
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20141728.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20141802.png"/>

So to improve timing performance we will change certain parameters and start agai using these commands

```
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 24-03_10-03 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to display current value of variable SYNTH_STRATEGY
echo $::env(SYNTH_STRATEGY)

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to display current value of variable SYNTH_BUFFERING to check whether it's enabled
echo $::env(SYNTH_BUFFERING)

# Command to display current value of variable SYNTH_SIZING
echo $::env(SYNTH_SIZING)

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

```

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20154454.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20155739.png"/>

Now run floorplan
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20160452.png"/>
Placememt
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20160630.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20161230.png"/>
We can see an instance of inv in figur below
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20161918.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20162016.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20162111.png"/>

Now doing post synthesis timing analysis
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20223445.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20224608.png"/>
We can see there is no timing violation
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-06%20233052.png"/>

### CTS

The purpose of building a clock tree is to ensure the clock signal reaches all sequential elements uniformly, minimizing clock skew. The H-tree is a commonly used methodology in Clock Tree Synthesis (CTS). 
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20001210.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20001820.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20001940.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20002951.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20010311.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20010430.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20010454.png"/>

### PDN GENERATION

for pdn generation use command `gen_pdn`

<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20013542.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20013853.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20013906.png"/>

# ROUTING AND FINAL GDSII generation
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20014538.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20020707.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20020720.png"/>

These are final chip tapeout files sent to foundry for fabrication
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20022810.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20022850.png"/>
<img src="https://github.com/Rajveer-1234/NASSCOMM-VSD-Soc-Design-Program/blob/main/Images/Screenshot%202025-04-07%20023043.png"/>
