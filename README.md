# NASSCOM-PD-RTL-TO-GDSII-Sandhyagollapudi
I attended a two-week workshop by VSD and NASSCOM, focused on converting RTL to GDSII using OpenLane and open-source tools. The course, which I found via Kunal Ghosh on LinkedIn, covered Digital SoC and Physical Design. We worked with the SkyWater 130 open-source PDK throughout the program.

## Day 1 - Inception of open-source EDA OpenLANE and sky130 PDK
### D1 SK1 How To Talk to Computers
## D1-SKY L1 Introduction to QFN-48 Package chip pads core die and IPs

![image1](https://github.com/user-attachments/assets/5c751d8a-6753-4a83-af6a-b1e60253cc59)
#### Arduino Board

This is an Arduino microcontroller board, with the encircled section showing the microprocessor, which connects to other board components. The chip's design, from concept to fabrication, follows the RTL to GDSII process. Arduino comprises a physical programmable board and an IDE that enables writing and uploading code to the board.

#### RISC-V SOC
![image2](https://github.com/user-attachments/assets/ad004bed-6c41-4931-8e3e-133a720195f0)

RISC-V SoCs incorporate various components like SRAM, ADC, DAC, and SPI, which are known as foundry IPs. These elements are fabricated in foundries using processes such as deposition and lithography. The modular nature of the RISC-V architecture allows for the integration of these components into a single chip, enabling a wide range of applications from embedded systems to high-performance computing.

#### INSIDE A MICROCONTROLLER BOARD
![3](https://github.com/user-attachments/assets/81447c34-5ea3-4c47-9a77-13f83ee66b33)

![4](https://github.com/user-attachments/assets/e5cb0c77-4289-4ff8-b998-b2c5578daf48)

### Microcontroller and SoC Components Overview:

- **Core**: The CPU of the microcontroller that executes instructions, such as ARM Cortex-M or RISC-V cores.
- **Die**: The physical silicon chip where the microcontroller’s circuitry is fabricated.
- **Pad**: The physical connection points on the chip where external components are connected.
- **GPIO (General-Purpose Input/Output)**: Programmable pins used for interfacing external devices, configured to handle input or output signals.
- **Bank**: Groups I/O pins or memory segments for organizational purposes, often referring to a set of GPIO pins.
- **Foundries**: Manufacturing facilities like TSMC or Intel, where microcontroller chips are fabricated using deposition and lithography techniques.
- **IPs (Intellectual Properties)**: Pre-designed logic blocks like UART, SPI, and I2C, integrated into the microcontroller for specialized functions.
- **SRAM & DRAM**: Volatile memory used for temporary data storage, with SRAM being faster but more power-consuming than DRAM.
- **ADC & DAC**: Analog-to-digital and digital-to-analog converters that facilitate the processing of analog signals by the microcontroller.
- **RISC-V SoC (System on Chip)**: An integrated chip with a RISC-V core and components like memory, peripherals, and communication interfaces.
- **Macros**: Predefined code or hardware configurations that automate repetitive tasks in programming or hardware design.

### Integration:
All components work together within a microcontroller or SoC, starting with the **Core** executing instructions on the **Die**, which connects to external components via **Pads**. External devices interface through **GPIO** pins, organized by **Banks** and configured using **Macros**. The microcontroller, built in **Foundries**, incorporates **IPs**, **SRAM**, **DRAM**, **ADC**, and **DAC** to store data and handle analog and digital signal processing. This seamless integration enables the microcontroller to perform complex tasks while interacting with the external world.

## D1-SKY L2 Introduction to RISC-V

![image](https://github.com/user-attachments/assets/fe71ebf9-cb1c-4c0d-9267-46ddc6e7dc50)

### Overview of RISC-V CPU Design and Implementation

- **RISC-V Assembly Code (Left)**: This section displays a snippet of assembly code specific to the RISC-V architecture. Each line demonstrates the basic instructions the CPU processes.

- **Implementation in Hardware Description Language (Bottom)**: This part illustrates the **picorv32** CPU core's design using a Hardware Description Language, such as Verilog or SystemVerilog. It shows how assembly instructions are converted into logical operations and register movements within the CPU, including configuration settings for features like counters or cache.

- **Physical Layout (Right)**: Here, the actual physical layout of the **picorv32** CPU core is visualized with tools like **qflow**. It displays various circuit elements, such as logic gates (e.g., AND2X2), flip-flops (e.g., DFFPOSx1), and their connections, illustrating the arrangement of transistors and wiring on the silicon chip.

### Key Takeaways:
The image highlights the connection between software and hardware in CPU design. It shows the transition from high-level assembly code through hardware description languages to the final physical layout of the chip, providing insight into the different stages of CPU design and how design decisions translate into the chip's physical implementation.

## D1-SKY L3 From software applications to Hardware

![image](https://github.com/user-attachments/assets/828ca683-7a19-487f-9a86-8e0e86e1b2b5)

![image](https://github.com/user-attachments/assets/5a5c0f28-776f-4edf-8cbf-f16432979f14)

### Overview of Software to Hardware Translation

- **Application Software (Top Left)**: We start with everyday software applications, developed in languages such as C++, Java, or Python. These applications interact with the system through a predefined set of instructions.

- **System Software and Compilation (Top)**: The Operating System (OS) manages system resources and provides an interface for applications to communicate with the hardware. Compilers convert high-level code (e.g., C++) into assembly language instructions tailored for the specific CPU architecture.

- **Assembly and Machine Code (Middle)**: The assembler translates assembly code into binary machine code (0s and 1s), which the hardware can directly interpret and execute. The **Instruction Set Architecture (ISA)** defines the set of instructions that a processor can execute, serving as the abstract interface between software and hardware.

- **Hardware Implementation (Bottom)**:
  - **Register Transfer Level (RTL)**: Describes hardware behavior using a Hardware Description Language (HDL) such as Verilog or VHDL, defining how data flows between registers and the logical operations performed.
  - **Netlist Synthesis**: Converts the RTL description into a netlist, a detailed representation of the circuit’s interconnected components, including gates and flip-flops.
  - **Physical Design**: Guides the physical placement and routing of transistors and wires on the silicon die, creating the tangible hardware that executes the software instructions.

### Key Takeaways:
This diagram illustrates the multi-layered process of translating software into hardware. It highlights the critical roles of compilers, assemblers, and hardware design tools in transforming abstract instructions into physical circuits, offering insight into the relationship between software, hardware, and computer architecture.

### D1 SK2 SOC Design and OPENLANE
## D1-SKY2 L1 Introduction to all components of an open-source digital ASIC design

![image](https://github.com/user-attachments/assets/89bf2b10-c41e-4788-bb0d-b38d3f6d4810)

### Introduction to Digital ASIC Design Components

- **RTL Design (Register Transfer Level Design)**:
  - **Definition**: Represents the logic and behavior of a digital circuit using registers and the data transfers between them.
  - **Purpose**: Specifies the functionality and operations of the circuit at a high level of abstraction.

- **EDA Tools (Electronic Design Automation Tools)**:
  - **Definition**: Software applications used for designing, simulating, and verifying electronic systems and integrated circuits.
  - **Purpose**: Automate the chip-making process, improving efficiency and reducing time-to-market.

- **Open-Source Tools**:
  - **QROad**: Specializes in routing within digital ASIC designs.
  - **OpenROAD**: Offers a comprehensive suite for placement, routing, and design rule checking.
  - **OpenLane**: Provides an end-to-end RTL-to-GDSII flow, integrating with other open-source tools.

- **PDK (Process Design Kit)**:
  - **Definition**: A collection of files and information from semiconductor foundries that describe the manufacturing process and design rules.
  - **Purpose**: Ensures designs are manufacturable and provides parameters for accurate simulation.
  
- **Google SkyWater 130nm PDK**:
  - **Definition**: An open-source PDK for the SkyWater 130nm process technology.
  - **Features**: Includes libraries, design rules, and models specific to the 130nm technology node.

### Integration and Accessibility

PDKs, or Process Design Kits, consist of model files provided by foundries that adhere to fabrication rules, bridging the gap between semiconductor fabrication engineers and circuit designers. While many designs, tools, and PDKs come with licenses and limited access, a number of open-source options are available. We will leverage these open-source tools and PDKs to design and generate CPU cores effectively.

## D1-SKY2 L2 simplified RTL TO GDSII MODEL

![image](https://github.com/user-attachments/assets/0fcedb11-7b60-4f97-8dd9-d72091903ef2)

![image](https://github.com/user-attachments/assets/5441c715-6bd4-4c83-a28d-463d16012d44)

### RTL-to-GDSII Design Flow Overview

1. **RTL Design**: The circuit's functionality is described using a Hardware Description Language (HDL) like Verilog or VHDL to create a high-level digital design. *(Tool: EDA Playground)*

2. **RTL Synthesis**: The RTL code is converted into a gate-level netlist, mapping the design to a library of standard cells while optimizing for area, power, and timing. *(Tool: yosys/abc)*

3. **Floorplanning and Power Planning**: The chip's die, core, and I/O pad areas are defined, with preplaced cells arranged and power distribution networks planned. *(Tools: init_fp, ioplace, tapcell, pdngen)*

4. **Placement**: Gate-level cells are assigned physical locations on the chip, minimizing wire length and signal delays while adhering to design rules. *(Tools: RePlace, Resizer, OpenDP, Magic Layout)*

5. **Clock Tree Synthesis**: A clock distribution network is constructed, ensuring minimal clock skew and proper timing. *(Tool: TritonCTS)*

6. **Routing**: Connections between gates and interconnects are made based on placement data, ensuring proper signal routing while avoiding congestion. *(Tools: FastRoute, TritonRoute)*

7. **Static Timing Analysis**: Timing constraints are analyzed, performing setup and hold checks to ensure the design meets required performance standards. *(Tool: OpenSTA)*

8. **Signoff**: Final design checks, including DRC (Design Rule Checks), LVS (Layout vs. Schematic), and ERC (Electrical Rule Checks), confirm that the design is ready for fabrication. *(Tools: Magic, KLayout, Netgen, CVC)*

9. **GDSII File Generation**: The final physical layout is generated as a GDSII file, containing all geometric data, layers, and mask information needed for manufacturing. *(Tool: Magic)*

This streamlined process ensures the transition from high-level RTL design to a fully verified chip layout ready for fabrication, with tools automating each stage for efficiency and precision.


![image](https://github.com/user-attachments/assets/b0f80b99-2b11-4ce6-869a-3553d6df09be)

### Netlist Modifications and Antenna Rule Violations in Chip Design

- **Netlist Modifications and Verification**: Whenever the netlist is modified—such as during Clock Tree Synthesis (CTS) or post-placement optimizations—verification is required to ensure the functionality remains unchanged. This is done using a formal verification tool like **LCE (yosys)** to confirm that the circuit's function is preserved after netlist modifications.

- **Antenna Rule Violations**: During fabrication, long metal wire segments can behave like antennas, accumulating charge that can damage transistor gates. To prevent this:
  - **Router's Role**: The router typically limits wire length to avoid antenna effects. If it fails, two solutions are commonly employed:
    1. **Bridging**: Introduces a higher metal layer to act as an intermediary.
    2. **Antenna Diode Cells**: These cells drain excess charges, protecting the gates. Antenna diodes are typically provided by the standard cell library (SCL).

- **Preventive Approach with OpenLANE**: OpenLANE adopts a proactive strategy by placing fake antenna diode cells next to every input pin after placement. Once routing is completed, an antenna checker is run. If violations are found on a specific cell's input pin, the fake diode cell is replaced with a real one, ensuring protection against antenna effects.

This method ensures robustness during fabrication, protecting transistors from potential damage caused by antenna effects while maintaining design integrity throughout netlist modifications.
## D1 SK3 Get Familiar with Open Source EDA Tools

### Calculate FLOP Ratio and Percentage after synthesis

#### FLOP Ratio= 
Total Number of D Flip-Flops/Number of Cells
#### Percentage=
FLOP Ratio×100

### Commands to Start OpenLane Using Docker and Run Synthesis

``` bash 
 cd Desktop/work/tools/openlane_working_dir/openlane
docker
 ```
``` bash 
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
 ```
![1](https://github.com/user-attachments/assets/39fe8205-442c-4c92-94c8-74625af96843)

![2](https://github.com/user-attachments/assets/60f6e373-813c-422b-aac1-a2078cf72af9)

![3](https://github.com/user-attachments/assets/0e58099c-1772-4ba8-9846-f44e12ed20c8)

![4](https://github.com/user-attachments/assets/aaa58527-fff8-4086-91d9-538fd3a7c54b)

#### The `config.tcl` file in OpenLane holds all the specifications for the design environment. It defines the configuration settings, constraints, and tool parameters that tailor the synthesis and layout processes to meet the requirements of our specific design.

![6](https://github.com/user-attachments/assets/4b726efa-1c84-48c7-a98c-37e32a9834af)

![7](https://github.com/user-attachments/assets/4f257183-902f-4030-9f51-d7a1a7ed7edb)

![8](https://github.com/user-attachments/assets/402d94ca-fee7-4a34-af23-a3edd859a5a2)

![9](https://github.com/user-attachments/assets/68e22322-1a94-48d1-8f28-38d4fb50b14b)

#### After synthesis is completed, the results can be viewed both in the Docker terminal window and in the OpenLane directory under the `results/synthesis` folder. This folder contains detailed synthesis reports, including gate-level netlists and performance metrics.

![5](https://github.com/user-attachments/assets/6cf1f1b2-abb2-4bd6-8788-42de1873ba3f)

### RESULTS
- FLOP RATIO = 1613/14876=0.1084
- Percentage = 0.1084×100=10.84

![10](https://github.com/user-attachments/assets/a5a53481-ddd8-4fae-8b9e-ab0771dbeedc)

![11](https://github.com/user-attachments/assets/8860dc86-e954-412d-8048-c783c9cc4e9f)

![13](https://github.com/user-attachments/assets/5ed9657f-fe97-465a-96cf-e8d0d3864e2b)

![14](https://github.com/user-attachments/assets/1a86c550-d5fb-467a-abb4-3e8cc2a5f187)

#### At the end of the synthesis process, you will observe that the synthesis results displayed in the Docker terminal window match those found in the `results/synthesis` directory within the OpenLane project. Both contain the same data, such as the gate-level netlist and synthesis reports, ensuring consistency between the logs and output files.

## Day 2 Good floorplan vs bad floorplan and introduction to library cells
### D2 SK1 Chip floor planning considerations

![image](https://github.com/user-attachments/assets/5301c52e-7087-44e3-8461-857669ba15aa)

![image](https://github.com/user-attachments/assets/4b713164-f3c7-41ee-a06b-df83eb5b9085)

![image](https://github.com/user-attachments/assets/ed6af0c1-539a-4287-b42e-4c2bbfb6e43f)

![image](https://github.com/user-attachments/assets/30d87f8b-9bde-4185-b175-87df3c44607a)

![image](https://github.com/user-attachments/assets/df5209a0-2708-45cd-b1ec-dd18df0a5f11)

### Core and Die in Chip Design, Utilization Factor, and Aspect Ratio

In this section, we explore how to calculate the dimensions of the Core and Die of a chip during physical design. Starting with a simple netlist that includes two flip-flops and some combinational logic, the netlist represents the connectivity of an electronic circuit. The goal is to convert logical components, such as AND and OR gates, into physical dimensions while ignoring wire lengths. We focus solely on the Core and Die areas of the chip.

Assume each standard cell, including logic gates and flip-flops, has a dimension of **1 unit × 1 unit**, giving each an area of **1 square unit**. Using this, we can estimate the area occupied by the netlist on the silicon wafer. After placing all flip-flops and logic gates together, the combined width and height of the occupied area would be **2 units each**, resulting in a total area of **4 square units**. This is the minimum space required to fit the netlist.

### Core and Die:
- **Die**: The portion of a silicon wafer that holds the core logic. It is a small semiconductor piece on which the circuit is fabricated.
- **Core**: The section of the Die where the fundamental logic of the design is placed.

### Utilization Factor:
The utilization factor measures how much of the core area is being used by the logic. A utilization factor of **1** means the core is fully utilized with no empty space left. For a larger chip with a dimension of **4 × 4 square units**, the utilization factor could be **0.25**, indicating that only 25% of the chip area is used by the netlist, leaving 75% available for routing and additional cells.

### Aspect Ratio:
The aspect ratio is calculated by dividing the height by the width of the core. When the aspect ratio equals **1**, the chip is square-shaped. If the aspect ratio differs from 1, the chip takes on a rectangular shape. For example, with dimensions of **2 units × 2 units**, the aspect ratio is **1**, indicating a square chip.

In summary:
- **Utilization Factor**: Indicates how efficiently the core area is used.
- **Aspect Ratio**: Describes the shape of the chip (square or rectangular).

![image](https://github.com/user-attachments/assets/cdf506c8-9f1f-4e83-9cf4-6b6e7a476df2)

![image](https://github.com/user-attachments/assets/6a6979e4-355b-4951-8b9b-c030b6de19c6)

![image](https://github.com/user-attachments/assets/cd818b2e-4589-4802-9bb0-76ccf444042f)

### Preplaced Cells in Chip Design

Consider a large combinational logic circuit composed of numerous logic gates. To manage its complexity, we divide the circuit into smaller sections by cutting it into two blocks. Each block is then treated separately, with extended input/output pins. These blocks are isolated and "black-boxed," meaning their internal logic becomes invisible to the main netlist and external viewers. 

Once black-boxed, these blocks can be treated as independent IPs (intellectual properties) or modules. The advantage of this approach is that these IPs can be reused multiple times across different designs after being implemented once. Examples of such reusable IPs include memory, clock-gating cells, comparators, and multiplexers (MUX), which all integrate into the top-level netlist to perform specific functions. Although these cells receive signals and generate outputs, their functionality is defined just once.

The process of arranging these IPs within a chip is known as **floorplanning**. When these IPs are assigned specific locations in the chip prior to the automated placement and routing stage, they are referred to as **preplaced cells**. This manual placement ensures that critical components are located optimally within the design, enhancing performance and efficiency.


![image](https://github.com/user-attachments/assets/e3867775-5bee-41ca-aa28-6a32fe783245)

![image](https://github.com/user-attachments/assets/f5d305bf-d699-4c7e-b46e-8a4d3913091f)

![image](https://github.com/user-attachments/assets/af9557a9-5476-4183-bea4-1ee20b358775)

![image](https://github.com/user-attachments/assets/d8f35617-4bf4-45cc-b038-ad65bbfe41f7)

![image](https://github.com/user-attachments/assets/bd6faff4-f98b-4a0b-92b5-79ba37fd496e)

![image](https://github.com/user-attachments/assets/40a4f886-53a3-442a-a602-94fe7a453a0f)

![image](https://github.com/user-attachments/assets/d482b8fc-ff5c-4549-ad7e-73bd6dd6e3c2)

![image](https://github.com/user-attachments/assets/070091d0-3ae1-4e65-9c6c-392b96ba013d)

![image](https://github.com/user-attachments/assets/caedb9d3-2ec3-437e-adf3-663f086275af)

### De-Coupling Capacitors and Power Planning

Consider the same circuit discussed earlier, now part of a larger block. When a logic gate, like an AND gate, switches between 0 and 1, it requires a certain amount of current to charge or discharge its internal capacitance, representing logic levels. Due to resistances and inductances in the power supply path (Rdd and Ldd), a voltage drop occurs, leading to a slightly lower voltage at node 'A' than the ideal Vdd, such as 0.97V instead of 1V. This can result in unreliable logic levels, leading to potential errors in the circuit.

To address this, a **decoupling capacitor** is placed in parallel with the circuit. During switching events, the decoupling capacitor supplies the needed current, while the RL network replenishes the charge. In chip design, decoupling capacitors are strategically placed between different blocks to ensure stable power supply and reduce fluctuations in local voltage levels. This helps maintain reliable communication between blocks and ensures consistent performance across the circuit.

### Power Planning

Once local decoupling is established, power planning extends to the entire chip. Signals transmitted from drivers to loads, such as across a 16-bit bus, need sufficient power to maintain consistent logic levels. However, placing decoupling capacitors everywhere is impractical, especially for larger buses. Voltage drops inevitably occur when the power supply is far from the bus.

For example, if a 16-bit bus is connected to an inverter, the capacitors will charge and discharge as the signals flip between logic 0 and 1. If all capacitors share the same ground or Vdd tap points, ground bounce (voltage spikes in the ground line) and voltage dips at the Vdd tap can occur, potentially causing the circuit to enter an undefined state, leading to unpredictable behavior.

To mitigate these issues, **multiple power supplies** are used across the chip, allowing each block to draw power from the nearest supply and discharge to the closest ground. This **power mesh** design helps reduce voltage drops and ground bounces, ensuring more stable and reliable circuit operation throughout the chip.

![image](https://github.com/user-attachments/assets/64927106-752f-4bed-8b6a-a06bcef2c8be)

![image](https://github.com/user-attachments/assets/b0e7dd5f-b970-4935-99e3-e86892042ee1)

### Pin Placement and Logical Placement Blockage

In complex digital circuits, understanding the timing analysis between different clock domains is crucial. Consider a design with 6 input ports and 5 output ports. The connectivity between these gates is described using VHDL/Verilog, resulting in a **netlist** that defines the relationships between components.

Now, when placing this netlist into the core of the chip, we need to fill the empty area between the core and die with the necessary pin information. The **frontend team** defines the netlist and its input/output connectivity, while the **backend team** handles the physical **pin placements** on the chip.

To optimize performance, pin placements must be strategically made by locating **preplaced blocks** as close as possible to the corresponding input and output pins. This reduces signal delay and enhances the overall timing performance of the circuit, ensuring that the paths between blocks are as efficient as possible.

### Section 2 Tasks

1. **Run 'picorv32a' Design Floorplan:**
   - Using OpenLANE, execute the flow for the **'picorv32a'** design to generate the necessary outputs, specifically the floorplan.
   - Ensure that all configurations are set correctly in `config.tcl` to match the design requirements.

2. **Calculate Die Area in Microns:**
   - Once the floorplan is generated, extract the **die width** and **die height** from the floorplan DEF (Design Exchange Format) file.
   - Calculate the **die area** using the formula:
     \[
     \text{Die Area} = \text{Die Width} \times \text{Die Height}
     \]
     - Ensure units are consistent, and the result is in square microns.

3. **Explore Floorplan in Magic Tool:**
   - Load the generated **floorplan DEF** into the **Magic tool** to visualize and explore the layout.
   - Inspect the placement of macros, pins, and ensure that all components are optimally placed.

4. **Run 'picorv32a' Design Congestion Aware Placement:**
   - Rerun the OpenLANE flow, this time with **congestion-aware placement** enabled for the 'picorv32a' design.
   - Ensure placement is optimized to prevent routing congestion in critical areas of the design.

5. **Explore Placement in Magic Tool:**
   - Load the generated **placement DEF** file into the Magic tool.
   - Explore the placement of the cells, observe the optimized layout, and ensure congestion is minimized.

6. **Revisit Die Area:**
   - After placement, verify if the die area has changed based on the final placement DEF.
   - Recalculate the die area if necessary.

This process ensures that the **'picorv32a'** design undergoes proper floorplanning and placement steps, producing a die area that can be verified using the Magic tool for visualization and further analysis.

``` bash 
 run_floorplan
 ```
Before running the floorplanning process in OpenLANE, you'll need to configure specific switches to tailor the floorplan according to our design requirements. Here's a step-by-step approach to preparing for floorplanning:

![floor1](https://github.com/user-attachments/assets/d68c6335-4178-4f3d-bcbd-c5adf52de9b4)

![floor2](https://github.com/user-attachments/assets/dc2f9add-845c-489c-95fe-b7df550539a0)

The default core utilization ratio is set to 50% and the aspect ratio is 1. However, these values are not fixed and should be adjusted according to the specific requirements of our design. You may need to modify these parameters to meet the design constraints and objectives.

![floor3](https://github.com/user-attachments/assets/c65fe48e-450f-4c41-9cbf-c3b3e90ddacd)

In OpenLANE, the FP_PDN files configure the power distribution network and are applied by default during the floorplanning stage. The FP_IO_MODE value of 1 or 0 indicates that pin positioning is randomized but spaced evenly.

The priority for configuration settings follows this order: system defaults in `floorplanning.tcl` are applied first, followed by settings in `config.tcl`, and finally, the PDK variant settings in `sky130A_sky130_fd_sc_hd_config.tcl`.

Next, we will execute the floorplan process with these settings to observe the resulting configuration.

![floor4](https://github.com/user-attachments/assets/de60ebf9-27e7-46d0-8d57-9089adc6a614)

![floor5](https://github.com/user-attachments/assets/be0be710-cb4c-42f0-b398-818f13c1dda5)

![floor6](https://github.com/user-attachments/assets/df7b87fa-9309-4e0e-9f15-f91ea00c19be)

#### Calculate the die are in microns

- 100 unit distance = 1 micron

- Die width in unit distance = 660,685

- Die height in unit distance = 671,405

- Distance in micron = Value in unit distance/1000

- Die width in micron = 660,685/1000

- Die height in micron=671,405/10,000

Area of die in micron = (660.685 \times 671.405 = 443,587.212425) square microns  

#### RUNNING floorplan.def in Magic layout in another terminal

``` bash 
 # Change directory to path containing generated floorplan def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/14-08_02-48/results/floorplan/

# Command to load the floorplan def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
 ```

![floor7](https://github.com/user-attachments/assets/138a3178-a886-4a22-b274-3fe1b13f3722)

![floor8](https://github.com/user-attachments/assets/1679f6e2-b4a5-4e7d-97d5-b1f3f535e8ee)

![floor9](https://github.com/user-attachments/assets/69146bb1-1eb5-4fea-a856-81adb73b6189)

![floor10](https://github.com/user-attachments/assets/08e468ff-6230-473a-8748-cba1ec8cc173)

### D2 SK2 Library binding and placement

![image](https://github.com/user-attachments/assets/17ad611b-9bae-4ff0-b6d1-e4ddeb518b78)

![image](https://github.com/user-attachments/assets/1c187295-0b57-4eaf-ad0f-cc70f59ce4d2)

### Netlist Binding and Initial Placement Design

1. **Build Netlist with Physical Cells:**
   The netlist includes gates and their functional representations, such as a NOT gate depicted as a triangle in a schematic but actually a box with specific physical dimensions. Similarly, AND gates and flip-flops are represented as boxes with defined width and height. In reality, these gates and flip-flops do not have geometric shapes like triangles or boxes; instead, they are physical components with set dimensions. 

2. **Library Definition:**
   The netlist components—gates, flip-flops, and blocks—are assigned physical shapes and dimensions. These components are stored in a library, which acts like a bookshelf where you can find different gates and flip-flops. The library contains timing information for each cell, such as gate delays, and is divided into two sub-libraries: one for shape and size and another for delay information. 

3. **Library Usage:**
   The library provides various versions of each cell, allowing for choices based on timing requirements and available space on the floorplan. Larger cells have lower resistance paths, which typically result in faster operation and reduced delays. Designers select cells based on these factors to meet timing conditions and spatial constraints on the floorplan.

![image](https://github.com/user-attachments/assets/c8e897c3-9535-4d19-a427-58caece425e2)

![image](https://github.com/user-attachments/assets/810dff2a-5ab6-429e-8f68-cdda538d29ca)

### Placement

Once each gate has been assigned a specific shape and size, the next step is to position these physical representations on the floorplan. Here's how the placement process works:

1. **Floorplan and Netlist Preparation:**
   We start with a floorplan that includes input and output ports and a netlist with specified sizes for each component. The netlist provides the connectivity information and logical layout, while the floorplan outlines where the components will be placed.

2. **Maintaining Pre-Placed Cells:**
   During placement, pre-placed cells (cells that were assigned fixed positions in earlier steps) are preserved. The placement process ensures that these pre-placed cells remain in their designated locations and that no new cells are positioned over them.

3. **Placement Execution:**
   The physical representations of the netlist components are placed onto the floorplan, following the connectivity information provided by the netlist. The goal is to ensure that the logical connections between components are maintained and that the circuit interacts correctly with its input and output ports.

4. **Timing and Delay Considerations:**
   Proper placement helps maintain minimal timing delays by ensuring efficient routing between components. The placement aims to keep the circuit's performance optimal, minimizing the distance and delay between interconnected gates and ports. 

Overall, the placement process involves strategically positioning the netlist components on the floorplan to achieve both functional connectivity and optimal performance.

![image](https://github.com/user-attachments/assets/3469c3bc-043c-44cf-abce-2716dde9dd39)

![image](https://github.com/user-attachments/assets/57e7bcaf-bd67-4d9c-af19-cc1577878ff9)

### Optimize Placement Using Estimated Wirelength and Capacitance

Optimizing placement focuses on addressing issues related to wirelength and capacitance to improve signal integrity and performance. Here's a detailed look at the process:

1. **Estimating Capacitance and Wirelength:**
   Before routing the design, it is essential to estimate the capacitance associated with the connections between components. For instance, if there is a long wire from `Din2` to `FF1`, it results in high capacitance and resistance due to the extended length. This can affect the signal quality and make it challenging for `FF1` to accurately capture the input.

2. **Introducing Repeaters:**
   To mitigate the problem of high capacitance and long wirelength, intermediate steps are introduced. These intermediate steps are called **repeaters**. Repeaters act as buffers that recondition and amplify the signal, ensuring that it maintains its integrity over long distances. Each repeater replicates the original signal, sending it forward until it reaches the intended component, such as `FF1`.

3. **Balancing Signal Integrity and Area:**
   While repeaters help maintain signal integrity, they also consume additional area on the floorplan. The trade-off between improving signal quality and the increased area usage due to repeaters must be carefully managed.

4. **Timing Analysis:**
   After optimizing the placement with repeaters, it's crucial to perform a timing analysis. This involves assessing the design with ideal clock signals to ensure that the placement achieves the desired timing performance. The analysis will verify if the optimizations have been successful and whether the placement meets the design requirements.

Overall, optimizing placement involves strategically managing wirelength, capacitance, and the use of repeaters to ensure signal integrity while balancing the available floorplan area. Timing analysis then confirms the effectiveness of these optimizations.

**Need for Libraries and Characterization:**

1. **Logic Synthesis:** Converts RTL code into a gate-level netlist representing the circuit’s functionality.
2. **Floorplanning:** Uses the synthesized netlist to define the core and die size for the chip layout.
3. **Placement:** Positions logic cells on the chip to optimize initial timing and area.
4. **Clock Tree Synthesis (CTS):** Ensures the clock signal reaches all parts of the chip evenly with equal rise and fall times.
5. **Routing:** Connects cells according to design rules, relying on cell characterization for accurate signal paths.
6. **Static Timing Analysis (STA):** Evaluates timing characteristics such as setup time, hold time, and circuit frequency.
7. **Libraries:** Provide essential cells with physical dimensions, timing information, and performance attributes.
8. **Characterization:** Defines cell performance parameters to ensure accurate timing analysis and optimization.
9. **Integration:** Libraries and characterization are integral for accurate design and performance across all IC design stages.
10. **Common Element:** Throughout the design flow, cells and gates are central to each step, from synthesis to final timing analysis.
#### To run congestion-aware placement for the picorv32a design using OpenLANE,

``` bash 
 run_placement
 ```
![floor12](https://github.com/user-attachments/assets/576a0fbd-1da3-4533-a9ff-11ee28f1ae21)

``` bash  
# Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/14-08_02-48/results/placement/
# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
``` 
![floor14](https://github.com/user-attachments/assets/b0018322-17d1-46de-8fbf-6ebf414982b2)

![floor15](https://github.com/user-attachments/assets/058c81b2-9c0d-4015-87e3-a2c8a8ad2ff6)

### D2 SK3 Cell design and characterization flows
### Inputs, Design Steps, and Outputs for Cell Design Flow

**Inputs:** Define the standard cell’s functionality, design rules, technology node, library requirements, and electrical characteristics, and include simulation tools and layout constraints.

**Design Steps:** Involve schematic design, cell layout creation, electrical characterization, verification, integration into the library, and documentation.

**Outputs:** Include cell layout and schematic files, characterization data, library files, verification reports, and comprehensive documentation.

This process ensures that standard cells are effectively designed, characterized, and integrated into the library for use in larger designs.

![image](https://github.com/user-attachments/assets/9f7c4429-9697-4dd9-8779-33e0b150e09f)

![image](https://github.com/user-attachments/assets/3223034b-c4d2-453c-88d9-4e44d2c79cdd)

![image](https://github.com/user-attachments/assets/75097f87-7b49-443f-8db1-f2057da061a9)

### Circuit Design Steps

1. **Function Implementation:** Design the circuit functionality using PMOS and NMOS transistors.
2. **Model Transistors:** Ensure PMOS and NMOS transistors meet the specifications of the library.

**Outputs:** Typically include CDL (Circuit Description Language) files, GDSII layout files, LEF (Library Exchange Format) files, and extracted SPICE netlists (.cir).

![image](https://github.com/user-attachments/assets/2e045f0c-2c2f-405c-9126-18f77a3f577f)

### Layout Design Steps

1. **Implement Function:** Create the layout with PMOS and NMOS transistors.
2. **Generate Network Graphs:** Derive PMOS and NMOS network graphs from the implemented design.
3. **Determine Euler's Path:** Identify the Eulerian path, which is a path that traces each edge exactly once.
4. 
![image](https://github.com/user-attachments/assets/58e8d3d4-1462-4fa0-81da-6ef9ec70c429)

![image](https://github.com/user-attachments/assets/389c1787-10dd-462a-b95c-abb050fe9273)

![image](https://github.com/user-attachments/assets/ff4452df-e505-4fb8-bbcf-b700a533cb1e)

 Next step is to draw stick diagram based on the Euler's path. This stick diagram is derived out of the circuit

![image](https://github.com/user-attachments/assets/09608fb5-c357-4439-b085-487f260c7a61)

The next step involves converting the stick diagram into a detailed layout, incorporating proper rules and specifications. This layout will provide information on cell width, length, drain current, pin locations, and other critical parameters.

Finally, extract the parasitics from the layout and characterize them in terms of timing. The output from the layout design will be in GDSII format. With the extracted SPICE netlist, you can then perform characterization to obtain timing, noise, and power information.

![image](https://github.com/user-attachments/assets/6366d881-d5c8-4305-8af7-dad4b8f0e9d4)

1. **Read the Model**: Begin by importing the model.
2. **Read the Extracted SPICE Netlist**: Load the extracted SPICE netlist.
3. **Define the Buffer Behavior**: Recognize and define the behavior of the buffer.
4. **Read Subcircuits of the Inverter**: Import and examine the subcircuits of the inverter.
5. **Attach Power Supplies**: Connect the necessary power supplies.
6. **Apply Stimulus**: Apply the required stimulus to the circuit.
7. **Provide Output Capacitance**: Specify the necessary output capacitance.
8. **Simulation Command**: Use appropriate simulation commands (e.g., `.tran` for transient simulation, `.dc` for DC simulation).

Finally, compile all these inputs into a configuration file for the characterization software, such as "GUNA."

### D2 SK4 General timing characterization

![image](https://github.com/user-attachments/assets/49ffc7f9-bb63-4642-a71f-39116e498edd)

![image](https://github.com/user-attachments/assets/e640b30a-8cec-4868-965c-06d8cf884a04)

![image](https://github.com/user-attachments/assets/ae33d8af-b89a-432c-ae32-6e7f4f2c26a4)


| **Concept**          | **Definition**                                                | **Formula**                                                |
|----------------------|----------------------------------------------------------------|------------------------------------------------------------|
| **Rise Time**        | The time required for the output signal to increase from 20% to 80% of Vdd. | `time(slew_high_rise_thr) - time(slew_low_rise_thr)`      |
| **Fall Time**        | The time required for the output signal to decrease from 80% to 20% of Vdd. | `time(slew_high_fall_thr) - time(slew_low_fall_thr)`      |
| **Propagation Delay**| The time difference between when the input reaches 50% Vdd and when the output reaches 50% Vdd. | `time(out_thr) - time(in_thr)`                            |
## Day 3 Design library cells using magic layout and ngspice characterization
### D3 SK1 Labs for CMOS Inverter and ngspice simulation

So far, we have completed the floor planning and placement stages. If we want to modify the floor planning, such as changing the pin placements from being equally spaced, we can do this using the Set command.

First, check the switches in the configuration file. For example, if the current syntax is `env(FP_IO_MODE) 1`, change it to `env(FP_IO_MODE) 2`. Then, rerun the floor planning.

Afterward, verify the changes in pin locations using the Magic tool with the `-T` option.

![day32](https://github.com/user-attachments/assets/1571b0ab-3fc7-4419-9e37-e85abfd6a354)

![day33](https://github.com/user-attachments/assets/e6c316c5-07f8-435a-b719-be9816632839)

![day35](https://github.com/user-attachments/assets/c8757aca-cbde-4571-bacf-8eb92404d270)

![day34](https://github.com/user-attachments/assets/4610fc81-7d82-4e51-85f4-fd2e33d79cb4)

### SPICE DECK FOR CMOS INVERTER

![image](https://github.com/user-attachments/assets/abe7299a-a51b-4146-8b81-532853f2c60b)

**Component Connectivity:**  
This involves defining the connectivity of the substrate pin, which adjusts the threshold voltage of the PMOS and NMOS transistors.

**Component Values:**  
Specify the values for PMOS and NMOS transistors, typically using the same size for both to maintain consistency.

**Identify the Nodes:**  
Nodes are the points between which components are connected. Identifying these nodes is crucial for defining the netlist.

**Name the Nodes:**  
Assign names to these nodes for clarity: Vin, Vss, Vdd, and out.

**Connections:**

- For M1 MOSFET:  
  - **Drain** is connected to the **out** node.  
  - **Gate** is connected to the **in** node.  
  - **Source** and **Substrate** are connected to the **Vdd** node.

- For M2 MOSFET:  
  - **Drain** is connected to the **out** node.  
  - **Gate** is connected to the **in** node.  
  - **Source** and **Substrate** are connected to **0**.

- **CLOAD** is connected between the **out** node and **0** with a value of 10 fF.

- **Supply Voltage (Vdd)** is connected between **Vdd** and **0** with a value of 2.5 V.

- **Input Voltage (Vin)** is connected between **Vin** and **0** with a value of 2.5 V.

**Simulation Commands:**  
Set up the simulation to sweep Vin from 0 to 2.5 V in steps of 0.05 V to observe how Vout changes with Vin.

**Final Modeling:**  
Complete the modeling by creating files that provide a comprehensive description of the NMOS and PMOS transistors, including their electrical characteristics and connectivity.

![image](https://github.com/user-attachments/assets/58347f56-730a-4859-9d19-6d04f06d8720)

![image](https://github.com/user-attachments/assets/137281aa-7d24-475d-8630-d8d2e8c16f73)

**Switching Threshold (Vm):**  
The switching threshold, or Vm, is a key parameter that defines the robustness of an inverter. It represents the point at which the input voltage (\( V_{in} \)) equals the output voltage (\( V_{out} \)). At this threshold, the inverter transitions between its high and low states, making it crucial for determining the device's performance and reliability.

![image](https://github.com/user-attachments/assets/29aa8fb0-8ae0-40da-8de7-72107fb03aec)

![image](https://github.com/user-attachments/assets/29498881-fc29-40c7-8a6f-fdf1d66af1db)

![image](https://github.com/user-attachments/assets/f019979d-e332-44f7-9c83-e64f890235d4)

In dynamic simulation, we analyze the rise and fall delays of a CMOS inverter as they vary with \( V_{out} \). During this simulation, the input is a pulse, while all other conditions remain constant. The simulation command used is `.tran` for transient analysis.

A **Time vs. Voltage** graph is plotted to observe the changes. From this graph, we can determine the rise time (time taken for \( V_{out} \) to rise from 20% to 80% of \( V_{dd} \)) and the fall time (time taken for \( V_{out} \) to fall from 80% to 20% of \( V_{dd} \)).

**Section 3 Tasks Description:**

1. **Clone Custom Inverter Standard Cell Design:** Begin by cloning the standard cell design for a custom inverter from the GitHub repository to obtain the design files.

2. **Load and Explore Layout in Magic:** Open the custom inverter layout in the Magic tool to review and explore the design, ensuring it aligns with specifications.

3. **Spice Extraction of Inverter:** Use Magic to extract the SPICE netlist from the layout, which will be used for simulation and analysis.

4. **Edit Spice Model File:** Modify the extracted SPICE model file to incorporate any necessary changes for accurate simulation analysis.

5. **Post-Layout Ngspice Simulations:** Conduct post-layout simulations using Ngspice with the updated SPICE model file to evaluate the inverter’s performance.

6. **Fix DRC Issues in Old Magic Tech File:** Identify and correct problems in the Design Rule Check (DRC) section of the old Magic tech file for the Skywater process to ensure compliance with design rules.

``` bash 
 # Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Clone the repository with custom inverter design
git clone https://github.com/nickson-jose/vsdstdcelldesign

# Change into repository directory
cd vsdstdcelldesign

# Copy magic tech file to the repo directory for easy access
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .

# Check contents whether everything is present
ls

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &
 ```
![day36](https://github.com/user-attachments/assets/201ee014-ff9a-4338-823b-b53f203ecb8e)

![day37](https://github.com/user-attachments/assets/2568d3c5-1bf3-4853-a965-e6bc303e267b)

![day38](https://github.com/user-attachments/assets/d0dba619-3fab-4228-b268-bc8641db9fd9)

![day39](https://github.com/user-attachments/assets/a204ce58-b783-4301-a846-e25c6214b29d)

### D3 SK2 Inception of layout and CMOS fabrication process
##### Steps to do Spice extraction of inverter in magic

``` bash 
# Check current directory
pwd

# Extraction command to extract to .ext format
extract all

# Before converting ext to spice this command enable the parasitic extraction also
ext2spice cthresh 0 rthresh 0

# Converting to ext to spice
ext2spice
 ```
![day311](https://github.com/user-attachments/assets/9d9d3b24-4916-42e7-95b3-826209a629fe)

![dat12](https://github.com/user-attachments/assets/eea380a8-98cb-4985-a4ad-c533fc4c91b6)

##### create spice file and necessary modifications to be made according to our spice deck
![day314](https://github.com/user-attachments/assets/8a696c46-bd16-4f34-ae18-fdeefaff2992)

![day315](https://github.com/user-attachments/assets/b0e42d0a-2173-4d08-a8e9-41fac212f244)

![day310](https://github.com/user-attachments/assets/e0708367-18f3-433c-b4bc-fbe79f668081)

![day313](https://github.com/user-attachments/assets/4ad331b4-8370-4213-b257-7ae2193daa8f)

![day316](https://github.com/user-attachments/assets/51074316-0b44-4b26-81d5-b593db7ab779)

#### post-layout ngspice simulation Steps:
``` bash 
# Command to directly load spice file for simulation to ngspice
ngspice sky130_inv.spice

# Now that we have entered ngspice with the simulation spice file loaded we just have to load the plot
plot y vs time a
 ```
![s1](https://github.com/user-attachments/assets/55d4b1d3-08f0-4f51-a982-bf9be32e8863)

Rise time It is time taken to the output waveform to 20% value to 80% value.

![s2](https://github.com/user-attachments/assets/7a5b43a9-5ef3-42ed-80d1-e2e7b27ac052)

so, rise time= (2.24569 - 2.18217)e-09 = 63.52 psec.
Fall time
it is the time take by output for transition from 80% to 20%

![s3](https://github.com/user-attachments/assets/e7fb500f-6b96-4667-9ad7-f1acc05a8e8d)

so, fall time= (4.09641 - 4.04758)e-09 = 48.83 psec
Propagation delay
it is the time difference between the 50% of input and 50% of the output.

![s4](https://github.com/user-attachments/assets/ccce5dfd-080b-4d7f-be0c-18a5ff76e670)

so, propogation delay =(2.21106 - 2.15144)e-09 = 59.62 psec.
Cell rise delay
Time taken by output to rise to 50% and input to fall to 50%

![s5](https://github.com/user-attachments/assets/43a3d7a6-3437-475b-bbde-ffff8cd0a395)

so,cell fall delay=(4.08482-4.04771)e-09=37.11psec

### D3 SK3 Sky130 Tech File labs
##### To find and fix problems in the DRC (Design Rule Check) section of the old Magic tech file for the Skywater process:we can go to the website:-The Magic Technology File Manual - DRC Section
Link to Google_Skywaters Design Rules: - SkyWater PDK Documentation - Periphery Rules
For reference , we can use the github repo of Google-Skywater:SkyWater PDK GitHub Repository
##### Use below Commands:

``` bash 
# Change to home directory
cd

# Command to download the lab files
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

# Since lab file is compressed command to extract it
tar xfz drc_tests.tgz

# Change directory into the lab folder
cd drc_tests

# List all files and directories present in the current directory
ls -al

# Command to view .magicrc file
gvim .magicrc

# Command to open magic tool in better graphics
magic -d XR &
 ```
``` bash 
 #IN TKCON WINODW Form a seperate box
paint v2
cif see VIA2
 ```
![drc1](https://github.com/user-attachments/assets/ef24cc94-1f1e-4417-b489-c63529227606)

![drc2](https://github.com/user-attachments/assets/b45d2571-dc21-4c23-b5bc-4dac4a0aec52)

![drc3](https://github.com/user-attachments/assets/779e34dd-2e74-48a9-9f7a-3565bd458ca9)

![drc4](https://github.com/user-attachments/assets/e8e5d604-101e-4ff1-9dbf-9432b9cf3825)

![drc5](https://github.com/user-attachments/assets/abd426f8-3a85-4c74-a5fa-643239eab197)

##### Incorrectly implemented poly.9
![drc6](https://github.com/user-attachments/assets/d598afcf-f3c4-4c15-bba9-0bd8932834aa)

![Screenshot from 2024-08-15 08-02-21](https://github.com/user-attachments/assets/4d4564d8-6ef1-4a60-943c-5caa1161f77c)

##### update in sky130a.tech
``` bash 
vim sky130A.tech
 ```
![drc7](https://github.com/user-attachments/assets/88c6e7ab-add6-49c8-bd9f-2247cb5112ff)

![drc8](https://github.com/user-attachments/assets/123d90fe-2ddd-4d47-a25f-6a7f0814da64)

##### Type below Commands in tkcon

``` bash 
 # Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
 ```
![drc9](https://github.com/user-attachments/assets/9c225a36-735f-4a56-9685-6fa274612e5f)

![drc10](https://github.com/user-attachments/assets/ebedebe3-c824-4b56-a9ad-781258f4bc99)

##### Incorrectly implemented difftap2.rule
![drc11](https://github.com/user-attachments/assets/88310738-c120-40ea-9e69-18d27ff27bda)

##### update in sky130a.tech
``` bash 
vim sky130A.tech
 ```
![drc13](https://github.com/user-attachments/assets/9b840d3d-6393-41c4-8914-3c6fd24cb0d0)

##### Type below Commands in tkcon
``` bash 
# Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
 ```
![drc12](https://github.com/user-attachments/assets/fe442945-1cee-465f-927d-b06531b55b09)

##### Incorrect implementation of nwell.4 rule
![drc14](https://github.com/user-attachments/assets/7570d195-e74c-4170-be3b-6d5154b1fdab)
##### update in sky130a.tech
``` bash 
vim sky130A.tech
 ```
![drc15](https://github.com/user-attachments/assets/dc715299-dd1c-449c-ba62-91bd87dcb864)

![drc16](https://github.com/user-attachments/assets/f643cc76-b4e4-4c52-9e96-1f863aeaeafe)

##### Type below Commands in tkcon
``` bash 
# Loading updated tech file
tech load sky130A.tech

# Change drc style to drc full
drc style drc(full)

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
 ```
![drc17](https://github.com/user-attachments/assets/5b6edfdb-980e-42fa-bffd-2262806df23d)

## DAY 4 Prelayout timing analysis and importance of good clock tree
### D4 SK1 Timing modelling using delay tables

### Lab Task for Day 4

1. **Fix DRC Errors:**
   - Resolve any small Design Rule Check (DRC) errors identified in the layout.
   - Verify that the layout meets all required design rules and is ready for integration.

2. **Save and Open Layout:**
   - Save the finalized layout with a custom name.
   - Open the saved layout to ensure it is correctly saved and accessible.

3. **Generate LEF File:**
   - Generate the LEF (Library Exchange Format) file from the updated layout.
   - This file will describe the physical properties of the custom inverter cell.

4. **Update Design Files:**
   - Copy the newly generated LEF file and any associated library files to the `picorv32a` design’s `src` directory.
   - Edit the `config.tcl` file to include the new LEF file and update the library files for the OpenLANE flow.

5. **Run OpenLANE Flow:**
   - Perform synthesis using OpenLANE with the newly inserted custom inverter cell.
   - Address any new violations introduced by the custom inverter cell by modifying design parameters.

6. **Verify Floorplan and Placement:**
   - Run floorplan and placement to ensure the custom inverter cell is correctly integrated into the Place and Route (PnR) flow.

7. **Post-Synthesis Timing Analysis:**
   - Perform timing analysis using the OpenSTA tool to check for timing violations.
   - Make necessary timing ECO (Engineering Change Order) fixes to address any timing issues.

8. **Update Netlist:**
   - Replace the old netlist with the updated netlist generated after timing ECO fixes.
   - Reimplement the floorplan, placement, and Clock Tree Synthesis (CTS) based on the new netlist.

9. **Post-CTS Timing Analysis:**
   - Conduct timing analysis using OpenROAD after CTS to verify that timing requirements are met.

10. **Explore Timing Analysis:**
    - Modify the `CTS_CLK_BUFFER_LIST` variable by removing the `sky130_fd_sc_hd__clkbuf_1` cell from the clock buffer list.
    - Explore the impact of this change on the post-CTS timing analysis.

### LEF and DEF Files

- **LEF (Library Exchange Format):** Describes the physical properties of standard cells, macros, and other library elements. It does not include placement details but provides necessary information for placing and routing designs.
  
- **DEF (Design Exchange Format):** Contains detailed information about the actual placement and routing of cells in the design, including cell positions and interconnections.

### Condition for Standard Cell

- **Ports:** Input and output ports should be aligned with the intersection of vertical and horizontal tracks.
- **Dimensions:**
  - Width: Should be an odd multiple of the horizontal track pitch.
  - Height: Should be an even multiple of the vertical track pitch.
- **Track Information:** Open the track file from `pdk/sky130/libs.tech/openlane/sky130_fd_sc_hd/track.info` to verify track pitches.

![4d1](https://github.com/user-attachments/assets/731c63b4-b97f-46c4-b2a2-a03f537d0250)

![4d2](https://github.com/user-attachments/assets/b701e32a-36f8-4aaf-b546-3e0eb4d62fcd)

##### To open and view our custom inverter layout in Magic, follow these commands:

``` bash 
 # Change directory to vsdstdcelldesign
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &
# Get syntax for grid command
help grid

# Set grid values accordingly
grid 0.46um 0.34um 0.23um 0.17um
 ```
![4d1](https://github.com/user-attachments/assets/28326618-27a7-4b7f-b0ce-d55c8cb3220a)

![4d2](https://github.com/user-attachments/assets/acd9697a-3e90-4c4a-aa1e-02ce338946b3)

##### To open our newly created inverter layout in Magic and check various port names and their values, follow these steps:

``` bash 
 # Command to save as
save sky130_vsdinv.mag

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_vsdinv.mag &
 ```
![4d3](https://github.com/user-attachments/assets/422d8840-4cf8-4405-bfd1-255a0af58d5a)

![4d3](https://github.com/user-attachments/assets/b0b13894-d22d-4516-8847-8fb48e0d7c91)

![4d4](https://github.com/user-attachments/assets/ca52f7ea-5006-4a02-9ff2-0b3751084223)


##### To generate a LEF (Library Exchange Format) file from our layout in Magic:

``` bash 
 # lef command
lef write
 ```
![4d5](https://github.com/user-attachments/assets/200af362-5acc-4f7d-8ff0-b11dfe8434d7)

![4d6](https://github.com/user-attachments/assets/631829a9-27e0-4b31-bc6c-6ebdafcf97d3)

##### To copy the newly generated LEF file and associated required lib files to the picorv32a design src directory follow these steps:

``` bash 
# Copy lef file
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# Copy lib files
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
 ```

![4d6](https://github.com/user-attachments/assets/14212563-e348-4b36-8f59-f966d48f2de4)

![4d7](https://github.com/user-attachments/assets/cc37d15b-17e0-4c74-948d-4b049bdc13b4)

![4d8](https://github.com/user-attachments/assets/c67212a5-c134-4bb2-80b5-5ffd52997c53)

![4d9](https://github.com/user-attachments/assets/faf96a9c-2048-4108-91a2-909bff480b05)

##### Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow
##### Commands to be added in config.tcl

``` bash 
 set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
 ```
![4d10](https://github.com/user-attachments/assets/5dbdfc5f-7d8f-481c-bee9-5cc1ff7d4e2d)

![4d11](https://github.com/user-attachments/assets/5c04d08a-4c64-4ea3-a344-83febeb75fdc)

##### To run the OpenLane flow synthesis with the newly inserted custom inverter cell, follow these steps:

``` bash 
 # Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane
docker
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
 ```
![4d11](https://github.com/user-attachments/assets/f32aac58-b72b-46b1-a6cb-98f41a2de1ee)

![4d12](https://github.com/user-attachments/assets/b813c95d-02a7-467f-a229-06daaa800529)

![4d13](https://github.com/user-attachments/assets/17ea6dd6-9a6b-46c9-baf2-104ba4bcda31)

![4d14](https://github.com/user-attachments/assets/205ff76a-6751-465f-9159-3b8484b4a391)

![4d15](https://github.com/user-attachments/assets/37e025c8-b9a6-4661-914d-7bdda316d737)

### Delay Tables:

**Power-Aware CTS**: Power-aware clock tree synthesis involves techniques to reduce power consumption in clock trees by controlling the propagation of the clock signal. For example, if the enable pin of an AND gate is set to logic '1', the clock signal will propagate. If the enable pin is set to logic '0', the clock will be blocked. Similarly, with an OR gate, setting the enable pin to logic '0' allows clock propagation, while setting it to logic '1' blocks the clock. This blocking mechanism can significantly reduce power consumption in the clock tree.

### Understanding Delay Tables

![image](https://github.com/user-attachments/assets/6ede5618-27e9-48d3-8f5c-3888f1d16f56)

**What Are Delay Tables?**
Delay tables are data structures used in digital circuit design to model the timing delays of various components such as gates, interconnects, and cells. They provide detailed information about how long it takes for a signal to pass through a component under different operating conditions.

**Need for Delay Tables:**
- **Accurate Timing Analysis:** Delay tables allow precise timing predictions for digital circuits, helping designers ensure that the circuit meets timing requirements.
- **Performance Optimization:** By understanding delay characteristics, designers can optimize the circuit for speed and reduce critical path delays.
- **Design Verification:** Delay tables assist in verifying that the design meets required timing constraints, preventing errors due to timing violations.
- **Library Characterization:** Standard cell libraries use delay tables to characterize cell delay under various conditions such as load, input slew, voltage, and temperature.

**Components of Delay Tables:**
- **Input Slew Rate:** The rate at which the input signal transitions between logic levels.
- **Output Load:** The capacitance the output of a cell or gate must drive.
- **Voltage and Temperature:** Delay tables often account for variations in voltage and temperature.
- **Transition Time (Slew):** The time it takes for a signal to transition from one logic level to another.
- **Propagation Delay:** The time for a signal to travel from input to output of a cell.

**Usage of Delay Tables:**
- **Static Timing Analysis (STA):** STA tools use delay tables to calculate path delays in a circuit, ensuring signals meet timing constraints.
- **Timing Closure:** Delay tables are used during place-and-route to minimize delays and achieve timing closure.
- **Simulation:** Delay tables support accurate timing simulations, predicting circuit behavior and ensuring reliable operation under different conditions.
- **Library Development**:  
In standard cell library development, delay tables are generated for each cell to capture its behavior under various conditions such as different input slew rates, output loads, operating voltages, and temperatures. These delay tables are essential for Electronic Design Automation (EDA) tools, which use them for accurate timing analysis, performance optimization, and ensuring that the circuit meets all timing requirements during design and verification processes.

![image](https://github.com/user-attachments/assets/3de8d5f5-5300-4d2f-9c57-415d14fcdfa1)

![image](https://github.com/user-attachments/assets/d3826ccd-2192-42ba-8fef-3ac20e52a39f)

##### To run OpenLANE synthesis with modified commands to improve timing, follow these steps:

``` bash 
 
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane


docker
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# overwrite the design
prep -design picorv32a -tag 19-08_02-39 -overwrite 

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
# Command to display current value of variable SYNTH_STRATEGY
echo $::env(SYNTH_STRATEGY)

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) 1

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
# Run_floorplan
run_floorplan
# Run_placement
run_placement
 ```
##### if Floorplan is failed the run these steps:

``` bash 
 # If floorplan fails
init_floorplan
place_io
tap_decap_or
 ```
![4d16](https://github.com/user-attachments/assets/176c52b1-b26d-474a-bfb5-0923ee271042)

![4d17](https://github.com/user-attachments/assets/681b875e-7eb4-4242-b7c0-750204d8c181)

Even after changing the command, the WNS (Worst Negative Slack) remains at -23.89 and the TNS (Total Negative Slack) at -711.59. To reduce these values, a more aggressive approach can be used by setting `set ::env(SYNTH_STRATEGY) "DELAY 3"`. Although the slack hasn't decreased yet, it is expected to improve after the clock tree synthesis (CTS) and routing stages are completed.
![4d18](https://github.com/user-attachments/assets/5732d6ef-d2b8-4f00-8e20-e0d0c42817bd)

![4d20](https://github.com/user-attachments/assets/da73f526-cc02-4f7e-b18e-d3f8a841b7cb)

![4d19](https://github.com/user-attachments/assets/2dba8bd5-9fb6-42b3-b2f2-91f98b80db21)

We observed that both TNS (Total Negative Slack) and WNS (Worst Negative Slack) have reduced, but this has come at the cost of increased chip area. The previous chip area was 147712.918400. To manage this trade-off, we can use `set ::env(SYNTH_STRATEGY) 1` to run floorplan and placement, then address the reduction of TNS and WNS in later stages.

![4d20](https://github.com/user-attachments/assets/98de3311-6423-4e61-8a15-d2be8d385df7)

![4d21](https://github.com/user-attachments/assets/9a039536-432a-4c79-acb4-44026afa63c0)

![4d22](https://github.com/user-attachments/assets/2531596e-a1de-405e-9585-b43b04c709d5)

![4d24](https://github.com/user-attachments/assets/05fde656-7827-4b4f-b326-a4615a6275d0)

![4d25](https://github.com/user-attachments/assets/c8ee6394-efed-49f3-9ae1-2c170cec1370)

#### Commands to open magic terminal

``` bash 
 # Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/19-08_02-39/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
 ```
![4d26](https://github.com/user-attachments/assets/a795edf2-e1ab-41fc-9a83-ee11978fc88d)

![4d27](https://github.com/user-attachments/assets/e7f65b61-fac3-4db4-90e5-10995d417d28)

### D4 SK2 Timing analysis using ideal clock using openSTA
##### Setup Timing Analysis
![image](https://github.com/user-attachments/assets/13a7817d-8a5e-47b2-ad9a-ddde7be46631)

In setup timing analysis with an ideal clock (single clock), we start with a clock frequency of 1 GHz, which gives a clock period of 1 ns. We perform the analysis over one clock period, from 0 to 1 ns. At the 0 clock period, the edge reaches the launch flop, and by T = 1 ns, the second edge reaches the capture flop.

Let's assume the combinational delay between the launch and capture flip-flops is represented by θ. For the system to function correctly, the setup timing analysis requires this combinational delay to be less than the clock period (T). Inside the capture flip-flop, several MOSFETs, logic gates, resistances, and capacitances influence the timing.

The delay within the flip-flop, particularly through MUX1 and MUX2, affects the combinational delay requirement. The time needed for the input 'D' to stabilize before the clock edge is known as setup time (S). Therefore, the input 'D' must settle a finite amount of time (S) before the clock edge to ensure proper operation.

Thus, the combinational delay requirement is updated from θ < T to θ < (T - S), accounting for the setup time.

##### clock jitter and uncertainity

![image](https://github.com/user-attachments/assets/242c1431-4f60-4247-be36-4890c61eef5c)

In a system where the clock is generated by a PLL (phase-locked loop), the clock signal is ideally expected to arrive at precise intervals like 0, T, 2T, etc. However, due to inherent variations in the clock source, the signal may not always be generated exactly at these times. This variation is known as jitter, which refers to the temporary deviation in the clock pulse.

Taking jitter into account, we introduce an uncertainty time (US) into our timing equation. The timing condition now becomes θ < (T - S - US), where 'S' is the setup time, and 'US' accounts for jitter. Assuming a setup time (S) of 0.01 ns and an uncertainty (US) of 0.09 ns, we can evaluate the timing path in our circuit, focusing on stages 1 and 3, both operating under a single clock.

To identify the combinational path delay for both logic stages and perform post-synthesis timing analysis using OpenSTA, follow these steps:

#### Post-Synthesis Timing Analysis with OpenSTA:

``` bash 
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane
docker

# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
 ```
![4d28](https://github.com/user-attachments/assets/67b6380f-146c-42f6-a8e8-baf6b48dfb95)

Newly created pre_sta.conf for STA analysis in openlane directory

![good](https://github.com/user-attachments/assets/61bf2349-ed39-452e-8512-a005ba9240a3)

To create a custom my_base.sdc file for STA analysis in the openlane/designs/picorv32a/src directory, base it on the default openlane/scripts/base.sdc and modify it according to our design needs.

![4d30](https://github.com/user-attachments/assets/200e6eb3-d35a-426f-9f40-0698effb3025)

``` bash 
 # Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
 ```
![sta1](https://github.com/user-attachments/assets/89a2e1f7-72e3-4bfb-8af8-20b5d34a7248)

![sta2](https://github.com/user-attachments/assets/104ca169-dabd-4811-bcc2-6d37ee489ea0)

Since high fanout is causing more delay, we can reduce the fanout during synthesis by adjusting the fanout parameter in OpenLane. Here's how I can modify the synthesis process to control fanout and potentially reduce the delays:

##### Commands to include new lef and perform synthesis:

``` bash 
# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a -tag 19-08_02-39 -overwrite

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to set new value for SYNTH_MAX_FANOUT
set ::env(SYNTH_MAX_FANOUT) 4

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
 ```
![sta4](https://github.com/user-attachments/assets/95173e3b-0a77-4ba6-8487-39968c6b6d1d)

![sta5](https://github.com/user-attachments/assets/2b6ca1b7-bc74-449d-aa3f-030a8493cb43)

![sta6](https://github.com/user-attachments/assets/14d81d16-b404-40d6-91dd-aeeabb6f2889)

![sta7](https://github.com/user-attachments/assets/76b6b4d6-addd-4b99-a951-2234cfc94fdc)

To address timing violations related to fanout in the design, especially when an OR gate with driving strength 2 is driving 4 fanouts, we need to make Timing ECO (Engineering Change Order) fixes. Here’s how I can approach this:

![sta8](https://github.com/user-attachments/assets/c85943fc-b906-4dd1-a551-2b813b74402c)

To optimize timing by replacing an OR gate with a higher drive strength (e.g., drive strength 4), follow these commands and steps in our design flow. This process involves updating the cell in our netlist, adjusting the design, and re-running synthesis and place & route:

``` bash 
 # Reports all the connections to a net
report_net -connections _11668_

# Replacing cell
replace_cell _14506_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
 ```

![sta9](https://github.com/user-attachments/assets/d80d263e-b6b6-46e4-a327-dbc2b4183c3b)

![sta10](https://github.com/user-attachments/assets/7cb134f1-5466-4540-8f3b-cf9cd907748f)

Slack Violation after many attempts of changing cells and strategies :
Slack Met:

![sat17](https://github.com/user-attachments/assets/54b1a838-6c9c-4d28-bc0a-9c29aee2595a)

![sta12](https://github.com/user-attachments/assets/c9d2db35-7760-4cc2-a4d5-f0a84ed0f242)

![sta13](https://github.com/user-attachments/assets/105b75cc-6128-4974-bcc0-88e047c82023)
##### We see that the overall slack is reduced

### D4 SK3 Clock Tree Synthesis TritonCTS and signal integrity
#### Clock Tree routing and buffering Using H-tree algorithm

![image](https://github.com/user-attachments/assets/620b492b-c712-4758-af53-248637f25171)

![image](https://github.com/user-attachments/assets/92d59a24-ea62-4b43-abd1-924f576416ff)

![image](https://github.com/user-attachments/assets/c1975476-ef5b-441d-9cb4-c36ed7cee6a6)

### Clock Tree Synthesis Overview

In clock tree synthesis, we connect `clk1` to `FF1` and `FF2` in stage 1, `FF1` in stage 3, and `FF2` in stage 4 using physical wires. This setup introduces a problem due to varying distances from the clock source to each flip-flop, causing clock skew where `t2 > t1`.

**Clock Skew:** Defined as the difference between the arrival times of the clock signal at different flip-flops. Ideally, skew should be 0 ps. In the previous setup, the clock tree was poorly designed. To improve, we'll modify the design to position the clock distribution more centrally so that the clock reaches all flip-flops at nearly the same time.

**Clock Tree Synthesis and Buffering:**
- **Issue:** Due to varying wire lengths and RC networks in the clock path, the waveform at the output differs from the input waveform.
- **Solution:** Use repeaters to mitigate this issue. Clock repeaters are designed to maintain equal rise and fall times.

**Steps:**
1. **Remove Existing Clock Route:** Disconnect the previous clock route.
2. **Place Repeaters:** Add two repeaters along the clock path to help maintain signal integrity.
3. **Clock Propagation:** Allow the clock signal to pass through these repeaters. The repeaters ensure that the waveform remains consistent and reaches the output effectively.

By employing these techniques, we enhance the clock tree’s performance and achieve more reliable timing across the design.

### Crosstalk and Clock Net Shielding

**Clock Net Shielding:** 
Clock net shielding is a technique used in IC design to protect the clock signal from interference and noise. The clock signal's integrity is crucial for the proper operation of digital circuits. Shielding involves placing dedicated shielding layers or routes between the clock net and other signals to prevent noise and crosstalk from affecting the clock signal. This ensures that the clock remains stable and reliable, minimizing disruptions in the circuit's timing.

**Crosstalk:**
Crosstalk occurs when an unwanted signal from one circuit or wire affects an adjacent circuit or wire. In ICs, crosstalk typically results from capacitive or inductive coupling between neighboring nets. This interference can cause noise and degrade signal quality, impacting the overall performance and reliability of the circuit. Managing crosstalk is essential for maintaining signal integrity and ensuring accurate circuit operation.

![image](https://github.com/user-attachments/assets/04fa89dc-c6a7-46d6-9d99-f5a8580f10e4)

![image](https://github.com/user-attachments/assets/187b496b-f589-4665-bac1-9e92eeeed0a3)

### Lab Steps to Run CTS Using Triton

1. **Replace the Old Netlist:** Replace the existing netlist with the updated netlist generated after applying timing ECO fixes.

2. **Implement the Floorplan and Placement:** Reapply the floorplan and placement based on the updated netlist to reflect the changes in the design.

3. **Run Clock Tree Synthesis (CTS) Using Triton:** Execute the CTS process with Triton to optimize the clock distribution network and ensure proper synchronization across the design.

``` bash 
# Change from home directory to synthesis results directory
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/19-08_02-39/results/synthesis/

# List contents of the directory
ls

# Copy and rename the netlist
cp picorv32a.synthesis.v picorv32a.synthesis_old.v

# List contents of the directory
ls
 ```
![sta14](https://github.com/user-attachments/assets/965a66f1-f7f3-482a-b4ae-1d4205d05fc7)

##### Command to write verilog

``` bash 
 
# Check syntax
help write_verilog

# Overwriting current synthesis netlist
write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/19-08_02-39/results/synthesis/picorv32a.synthesis.v

# Exit from OpenSTA since timing analysis is done
exit
 ```
![sta15](https://github.com/user-attachments/assets/7349fff5-67de-46a6-b986-a09caad04080)

Verifiy that the netlist is overwritten by checking that instance _14506_ is replaced with sky130_fd_sc_hd__or4_4

To proceed with the design and ensure to follow up on the clean design with no violations, use the following commands to load the design and run the necessary stages:

``` bash 
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 19-08_02-39 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts
 ```
![sta16](https://github.com/user-attachments/assets/0f6b3722-799a-449e-ace7-09996cfe88fe)

![ssta17](https://github.com/user-attachments/assets/a3de64c1-d29c-4f34-b987-973a0c694a4c)

![sta17](https://github.com/user-attachments/assets/ce1e452a-a9c0-40bb-ac4e-ca04ef11752f)

### D4 SK4 Timing analysis with real clocks using openSTA

##### Setup analysis with real clock

![image](https://github.com/user-attachments/assets/de4b7f8d-7a30-47b4-9dc8-845466277b0a)

##### Hold analysis

![image](https://github.com/user-attachments/assets/7aabb791-a083-4942-af5c-2112d947ce53)

### Key Concepts of Clock Tree Synthesis (CTS):

Clock Tree Synthesis (CTS) is a crucial step in digital design that ensures all cells receive the clock signal nearly simultaneously. Key aspects of CTS include:

- **Quality Checks:** CTS involves several quality checks such as slew rate, pulse width, latency, duty cycle, and signal integrity.
- **Algorithms:** Techniques like the H-tree are commonly used for effective clock signal distribution across large chip areas. This hierarchical structure helps to minimize clock skew and optimize power consumption.
- **Crosstalk:** Crosstalk can be a significant issue, especially at smaller nodes due to the high density of components. Proper shielding of the clock network is essential to protect it from glitches and hazards.

##### Post-CTS OpenROAD Timing Analysis

``` bash 
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/19-08_02-39/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/19-08_02-39/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/19-08_02-39/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Check syntax of 'report_checks' command
help report_checks

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
 ```
![sta18](https://github.com/user-attachments/assets/30e7cbf5-5a13-4f39-b6f7-01a131ff5a76)

![sta19](https://github.com/user-attachments/assets/cc483e18-da42-45f9-b77b-6d132b43fbd2)

![sta20](https://github.com/user-attachments/assets/ee04b3ac-77a1-4eb8-94cd-e5af1ec5eedd)

##### Exploring Post-CTS OpenROAD Timing Analysis by Removing a Clock Buffer 'sky130_fd_sc_hd__clkbuf_1'

``` bash 
# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Removing 'sky130_fd_sc_hd__clkbuf_1' from the list
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Checking current value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Setting def as placement def
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/19-08_02-39/results/placement/picorv32a.placement.def

# Run CTS again
run_cts

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/19-08_02-39/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/19-08_02-39/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts1.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/19-08_02-39/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Report hold skew
report_clock_skew -hold

# Report setup skew
report_clock_skew -setup

# Exit to OpenLANE flow
exit

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)
 ```
![sta21](https://github.com/user-attachments/assets/bdfa9185-ce09-4254-988e-1408c622bcaf)

![sta22](https://github.com/user-attachments/assets/368d9858-5050-43dd-b675-b5fd49d3cc51)

### DAY 5 Final steps for RTL2GDS using Tritronroute and openSTA
#### D5 SK1 Routing and design rule check
### Introduction to Maze Routing (Lee's Algorithm)

**Routing**: The process of finding the optimal path between two endpoints, with minimal twists and turns, to ensure a shortest and most efficient connection. 

**Maze Routing (Lee's Algorithm)**: This algorithm avoids zig-zag connections by favoring more straightforward paths, such as L-shaped or Z-shaped routes. Here's a summary of how it works:

1. **Grid Creation**: The algorithm begins by setting up a routing grid with specific dimensions. 

2. **Labeling Grids**: Starting from the 'Source' point, the algorithm labels adjacent horizontal and vertical grids (but not diagonals). It assigns labels incrementally until it reaches the 'Target' point. 

3. **Finding the Path**: Once all possible paths are labeled, the algorithm identifies the shortest path from the source to the target. The goal is to minimize turns and avoid zig-zag routes, ideally opting for L-shaped connections.

By systematically labeling grids and selecting the shortest, most direct path, Lee's Algorithm efficiently finds the optimal route through the maze of connections.

![image](https://github.com/user-attachments/assets/91b4a4f2-b754-4393-85ab-b9f56ef78a9b)

### Design Rule Check (DRC)

**DRC Cleaning**: To perform a Design Rule Check (DRC), follow these steps to ensure that our design adheres to the required specifications:

1. **Identify Design Rules**: Understand the design rules that apply to our layout. These rules specify the minimum distances and other constraints between various components, such as wires, transistors, and other elements.

2. **Example Setup**: Consider a circuit with two parallel wires. According to DRC rules, there should be a minimum spacing between these two wires to prevent electrical interference and ensure reliable operation.

3. **Apply Rules**: Verify that the layout adheres to these spacing requirements. Use DRC tools to check if the distances between wires meet the specified minimum values.

4. **Correct Violations**: If the tool detects violations (e.g., wires that are too close together), adjust the layout to increase the spacing between the wires or make other necessary modifications to resolve the issues.

5. **Recheck and Verify**: After making adjustments, re-run the DRC tool to ensure that all violations have been resolved and that the design now complies with the design rules.

By following these steps, you can ensure that our design meets the required standards and operates correctly.

![image](https://github.com/user-attachments/assets/21adfd3b-13ee-4b62-b604-64d9ab05c03f)

### Design Rule Check (DRC) Rules

1. **Wire Width**: The width of each wire must meet the minimum requirement derived from the optical wavelength of the lithography technique used. This ensures that the wires are wide enough to be accurately patterned and reliable.

2. **Wire Pitch**: The minimum distance between two adjacent wires, known as the pitch, must adhere to specified limits to avoid interference and maintain signal integrity.

3. **Wire Spacing**: The spacing between wires should conform to defined standards to prevent signal shorting and ensure proper isolation between different signal paths. If two wires are too close, they might cause shorting issues.

   **Solution for Signal Short Problems**: To address potential shorting issues, place one of the wires on a different metal layer. Typically, the upper metal layer is wider than the lower layers, providing better separation and reducing the risk of short circuits.

4. **Check Via Width and Spacing**: Ensure that the via width and spacing between vias (used for connecting different metal layers) meet design rules to avoid issues in vertical connections.

5. **Parasitic Extraction**: After routing and DRC, perform parasitic extraction to determine the resistance and capacitance associated with each wire. This information is crucial for accurate timing analysis and further optimization of the design.

### Day 5 Lab Implementation

1. **Generate the Power Distribution Network (PDN)**
2. **Detailed Routing with TritonRoute**
3. **Post-Route Parasitic Extraction**
4. **Post-Route Timing Analysis with OpenSTA**

### D5 SK2 Power distribution network and routing

``` bash 
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane


docker
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Following commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts

# Now that CTS is done we can do power distribution network
gen_pdn
 ```
![5d1](https://github.com/user-attachments/assets/a290f316-a0a8-4fe6-93c0-24ded2aea4f6)

![5d2](https://github.com/user-attachments/assets/135eeeac-4708-4e12-bd36-1b16036e4a53)

![5d3](https://github.com/user-attachments/assets/583f15e2-e229-43ef-ab4e-c09d76b8578d)

``` bash 
# Change directory to path containing generated PDN def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-08_04-22/tmp/floorplan/

# Command to load the PDN def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &
 ```
![image](https://github.com/user-attachments/assets/5c20f4f4-35aa-4655-8800-51d0ceb70d4b)

In the image, the green area represents the chip, while the yellow, red, and blue boxes indicate the I/O pins, power pads, and ground pads, respectively.

Power is transferred from the pads to the rings through the black dots shown at the intersection points of the rings and pads.

The vertical and horizontal tracks, represented by red and blue lines, ensure that power is effectively distributed from the ring to the chip. This illustrates how power planning is implemented in the physical design of a device.

To perform detailed routing using TritonRoute and explore the routed layout, follow these steps:

``` bash 
# Check value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Check value of 'ROUTING_STRATEGY'
echo $::env(ROUTING_STRATEGY)

# Command for detailed route using TritonRoute
run_routing
Screenshots of routing run
 ```

![5d5](https://github.com/user-attachments/assets/477d6605-f164-4c1d-94e5-2a2501857aec)

##### Commands to load routed def in magic

``` bash 
# Change directory to path containing routed def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-08_04-22/results/routing/

# Command to load the routed def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
 ```
![5d6](https://github.com/user-attachments/assets/14f29fd4-2799-4a3b-ad71-f5fb006f4fcb)

![5d7](https://github.com/user-attachments/assets/5ab08cf9-7920-4b1d-ae25-46fdfdc6ca43)

### D5 SK3 Tritron route features

![image](https://github.com/user-attachments/assets/8472b03c-880d-4b99-90a3-388727138027)

![image](https://github.com/user-attachments/assets/1885d6a2-c2a7-4ce8-8750-816697a5b119)

![image](https://github.com/user-attachments/assets/10229418-3c0b-4fbc-bc8a-50907337e5fc)

![image](https://github.com/user-attachments/assets/aa2d0058-359d-4b79-9f8b-c720590bfe21)

![image](https://github.com/user-attachments/assets/2b83f356-048a-4777-b417-ca19ce9d4647)

TritonRoute is an advanced detailed routing tool for IC physical design, particularly effective for complex and advanced technology nodes. It uses preprocessed route guides from the global routing stage to streamline the detailed routing process. The tool optimizes both intra-layer and inter-layer routing, ensuring efficient connections across different metal layers with minimal interference. It employs parallel routing within layers and sequential routing between layers, improving routing speed and accuracy. TritonRoute also features sophisticated algorithms for managing connectivity access points and access point clusters, which helps reduce congestion and ensures reliable connections throughout the design.

| **Feature**             | **Fast Routing (Global Routing)**                    | **Detailed Routing**                                          |
|-------------------------|--------------------------------------------------------|--------------------------------------------------------------|
| **Purpose**              | Provides an initial, approximate routing plan           | Finalizes the exact routing paths adhering to all constraints |
| **Speed**                | Fast and less computationally intensive                 | Slower and computationally demanding                          |
| **Accuracy**             | Provides a coarse estimate; not fully accurate          | Highly accurate, ensuring manufacturability and performance   |
| **Design Rule Compliance** | Limited consideration of design rules                   | Full adherence to design rules and constraints                |
| **Use Case**             | Early-stage congestion analysis and layer assignment    | Final routing step before tape-out                            |
| **Output**               | Approximate paths and layer assignments                 | Final, optimized, and DRC-compliant layout                    |

To perform post-route timing analysis using OpenSTA with the extracted parasitics, follow these steps:

``` bash 
 # Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/20-08_04-22/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/20-08_04-22/results/routing/picorv32a.def

# Creating an OpenROAD database to work with
write_db pico_route.db

# Loading the created database in OpenROAD
read_db pico_route.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/20-08_04-22/results/synthesis/picorv32a.synthesis_preroute.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Read SPEF
read_spef /openLANE_flow/designs/picorv32a/runs/20-08_04-22/results/routing/picorv32a.spef

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
 ```
![5d8](https://github.com/user-attachments/assets/82c9f084-0541-4e6f-9517-e43d9f635a12)

![5d9](https://github.com/user-attachments/assets/2e96c18b-69cb-4087-897c-a18768a18d2a)

In OpenLANE, since SPEF extraction is not natively supported, the process of extracting parasitics and performing post-route timing analysis needs to be done using external tools

![5d10](https://github.com/user-attachments/assets/f1d1856c-95e5-478d-a53a-a18ab7adfaae)

# Acknowledgements
I would like to express my gratitude to Mr. Kunal Ghosh for sharing this insightful workshop, and I would also like to extend my thanks to the GitHub OpenLane community for their invaluable contributions.

# References

- https://github.com/The-OpenROAD-Project/OpenLane
- https://github.com/nickson-jose/vsdstdcelldesign
- https://github.com/AnupriyaKrishnamoorthy/NASSCOM-PD-ANU/tree/main
