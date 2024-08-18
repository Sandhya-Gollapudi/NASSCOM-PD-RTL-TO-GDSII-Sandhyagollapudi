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
Before running the floorplanning process in OpenLANE, you'll need to configure specific switches to tailor the floorplan according to your design requirements. Here's a step-by-step approach to preparing for floorplanning:

![floor1](https://github.com/user-attachments/assets/d68c6335-4178-4f3d-bcbd-c5adf52de9b4)

![floor2](https://github.com/user-attachments/assets/dc2f9add-845c-489c-95fe-b7df550539a0)

The default core utilization ratio is set to 50% and the aspect ratio is 1. However, these values are not fixed and should be adjusted according to the specific requirements of your design. You may need to modify these parameters to meet the design constraints and objectives.

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
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-07_10-25/results/floorplan/

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
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-07_10-25/results/placement/
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

##### To open and view your custom inverter layout in Magic, follow these commands:

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

##### To open your newly created inverter layout in Magic and check various port names and their values, follow these steps:

``` bash 
 # Command to save as
save sky130_vsdinv.mag

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_vsdinv.mag &
 ```
![4d3](https://github.com/user-attachments/assets/422d8840-4cf8-4405-bfd1-255a0af58d5a)

##### To generate a LEF (Library Exchange Format) file from your layout in Magic:

``` bash 
 # lef command
lef write
 ```
![4d4](https://github.com/user-attachments/assets/58946411-3628-461c-87ba-6ee392d3b692)

![4d5](https://github.com/user-attachments/assets/17ea4db4-0f3c-45dc-97bb-df3f3e2d22be)

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

![4d12](https://github.com/user-attachments/assets/b3e2aef5-c41c-4acf-b00a-15d824042b21)

![4d13](https://github.com/user-attachments/assets/704da716-4377-4500-b042-634effc5fbcc)

![4d14](https://github.com/user-attachments/assets/13feca44-1cf5-44ce-86e4-faa75a5ffdf6)

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
prep -design picorv32a -tag 29-07_10-25 -overwrite 

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
