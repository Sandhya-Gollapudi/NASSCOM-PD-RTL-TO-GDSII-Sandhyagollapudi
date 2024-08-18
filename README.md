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
#### The `config.tcl` file in OpenLane holds all the specifications for the design environment. It defines the configuration settings, constraints, and tool parameters that tailor the synthesis and layout processes to meet the requirements of your specific design.

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
